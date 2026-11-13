---
name: analyze-video
description: "Link video Reels/TikTok/Shorts/FB → phân tích phân cảnh, mổ xẻ kịch bản."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `analyze-video` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).
>
> **LUỒNG WEB ⇄ MAC (ưu tiên):** Mac đã tải video, cắt shot, đẩy ảnh lên R2 và đưa YouTube. Khi anh gõ `PHÂN TÍCH VIDEO <mã>`: mở Docs `AGY_VIDEO_<mã>` trong Drive `AGY_BRIDGE/video_jobs` → xem video (link YouTube, hoặc anh đính kèm `<mã>.mp4` từ Drive) → soi từng shot theo mốc giờ → in báo cáo 4 phần ra chat → `CHỐT PHIÊN` đúng 2 FILE `video/<folder>/shots.json` + `video/<folder>/sync.json` như yêu cầu trong Docs. KHÔNG tự cắt ảnh, KHÔNG đổi số shot. Link ảnh .webp và @Drive mp4 em KHÔNG nhìn được → bắt buộc có mp4 đính kèm trong chat; không thấy hình thì KHÔNG CHỐT PHIÊN. sync.json phải có `"nguon_hinh": "video"`.

> Tài liệu kèm: `references/broll-and-storyboard-pipeline.md`, `references/carousel-yt-upgrade.md`, `references/examples_and_catalog.md`, `references/youtube-token-troubleshoot.md`


# KỸ NĂNG PHÂN TÍCH & BÓC TÁCH VIDEO THỰC CHIẾN (ANALYZE VIDEO SKILL)

## 📌 NGUYÊN TẮC VÀNG VỀ TÍNH NHẤT QUÁN (THE 1:1 CONSISTENCY LAW)

1. **ĐỒNG BỘ 1:1 GIỮA CHAT VÀ BÁO CÁO WEB (CLOSED-LOOP VISION SYNC)**:
   - Báo cáo trong Chat và Báo cáo Web HTML trên `ytuong.fedu.vn` **BẮT BUỘC PHẢI KHỚP NHAU 100% VỀ MẶT NỘI DUNG**.
   - **CẤM TUYỆT ĐỐI**: Để file HTML báo cáo tồn tại văn mẫu heuristic của OpenCV (*"Cận Cảnh Chi Tiết Cảm Xúc..."* hay phân loại sai thành Talking Head/Kiến trúc do bắt nhầm từ khóa).
   - Mọi phân tích chuyên sâu mà Mắt Thần AI (Vision) nhìn thấy từ ảnh chụp đều phải được ghi đè ngược vào `shot_info.json` và render lại vào file HTML trước khi hoàn tất nhiệm vụ.

2. **ƯU TIÊN TRẢ KẾT QUẢ VÀO CHAT NGAY (ZERO LATENCY)**:
   - Khi có link video, trích xuất khung hình và soi ảnh bằng `view_file`.
   - Xuất bản ngay báo cáo theo chuẩn **Gạch Đầu Dòng Tối Giản (5 ý/shot)** vào chat.

3. **NGUYÊN TẮC MEDIA — CHỈ YOUTUBE, KHÔNG R2 CHO VIDEO CHÍNH**:
   - **BẮT BUỘC YouTube**: Mọi video phân tích đều phải upload lên YouTube kênh Sabakiz (chế độ Unlisted, playlist "Phân tích video") và nhúng `<iframe>` YouTube vào báo cáo HTML. Iframe bắt buộc có `enablejsapi=1` để điều khiển phân cảnh bằng postMessage.
   - **CẤM TUYỆT ĐỐI `<video>` từ R2 làm player chính**: R2 (`media.fedu.vn`) CHỈ lưu trữ ảnh keyframes (`.webp`, `.jpg`) làm thumbnail. KHÔNG BAO GIỜ dùng thẻ `<video src="media.fedu.vn/videos/...">` làm trình phát chính — đây là nguyên nhân gốc rễ gây lỗi 404 cache, ORB block, và Format error trên trình duyệt.
   - **Chống xung đột Player**: Script `loadVideoCandidate()` trong JS BẮT BUỘC có guard `if (player.tagName === 'IFRAME') return;` để không ghi đè src lên iframe YouTube.
   - **Lưu trữ backup Google Drive**: Video gốc luôn được upload song song lên Google Drive.

4. **TIẾN TRÌNH HẠ TẦNG & ĐỒNG BỘ NGẦM**:
   - Tải video, render webp, upload YouTube Sabakiz + Google Drive, upload ảnh lên R2, và tái tạo file HTML chạy ngầm bằng script tự động.
   - Luôn tự động commit & push git theo quy tắc hệ thống.

---

## 📌 NGUỒN VIDEO HỖ TRỢ
Instagram Reels, TikTok, YouTube/Shorts, Facebook (qua `yt-dlp`), Lazada & Shopee (Playwright headless: `fetch_lazada_meta` / `fetch_shopee_meta`). Bảng nền tảng, quy tắc E-Commerce và cơ chế scrape Lazada mới: `references/examples_and_catalog.md`.

## 📌 QUY TRÌNH THỰC THI 4 BƯỚC KHÉP VÒNG (4-STEP CLOSED-LOOP)

### BƯỚC 1: KIỂM TRA TRÙNG LẶP (PRE-CHECK DUPLICATION)
Trước khi tải hay bóc tách, kiểm tra xem video này đã có trong `scene.html` chưa:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- **NẾU ĐÃ CÓ (`exists: true`)**:
  - Dừng ngay việc tải lại hay tạo thư mục mới.
  - Báo ngay cho người dùng link báo cáo Web và Drive, tóm tắt 3 dòng nội dung cốt lõi và kết thúc.
- **NẾU CHƯA CÓ (`exists: false`)**:
  - Chuyển sang Bước 2.

---

### BƯỚC 2: BÓC TÁCH TƯ LIỆU THÔ BẰNG SCRIPT
Chạy script phân tích và trích xuất khung hình:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
Script sẽ tự động:
1. Tải video master về local (`[đường-dẫn-Mac] gia/output_packages/<folder_name>/`).
2. Băm nhỏ các shot, trích xuất ảnh `.jpg` và `.webp` vào thư mục `extracted_shots/`.
3. Tải video lên YouTube kênh Sabakiz (playlist 'Phân tích video', Unlisted) để nhúng iframe trực tiếp, đồng thời upload keyframe lên Cloudflare R2 CDN và Google Drive.

**Lưu ý đặc biệt cho Shopee/Lazada**: Script tự nhận diện domain và gọi hàm `fetch_shopee_meta()` hoặc `fetch_lazada_meta()` bằng Playwright headless để cạo video URL từ trang sản phẩm.

---

### BƯỚC 3: MẮT THẦN AI SOI ẢNH & XUẤT BẢN TRONG CHAT
AI gọi công cụ `view_file` mở trực tiếp các file ảnh `shot_XX_mid.jpg` để thực sự **NHÌN THẤY** bối cảnh, chữ text trên video, đồ vật, hành vi của nhân vật.
**CẢNH BÁO TỐI CAO:** AI TUYỆT ĐỐI KHÔNG ĐƯỢC BỎ QUA BƯỚC NÀY. BẮT BUỘC PHẢI IN TOÀN BỘ BÁO CÁO PHÂN TÍCH RA CHAT THEO ĐÚNG 4 PHẦN DƯỚI ĐÂY TRƯỚC KHI GỌI `sync_ai_analysis.py`.

Toàn bộ báo cáo trong chat tuân thủ đúng 4 phần:
1. **TIÊU ĐỀ & LIÊN KẾT ĐIỀU HƯỚNG:**
   Mẫu markdown tiêu đề (Tên đòn bẩy, Nguồn @creator, Mạch ý tưởng, Trục kịch bản 3 nhịp): `references/examples_and_catalog.md`.
2. **MỔ BĂNG TỪNG SHOT (ĐÚNG 5 GẠCH ĐẦU DÒNG):**
   Mỗi shot có tiêu đề rõ `[Hành động mấu chốt + Vì sao đắt]`:
   - **🎬 Diễn biến:** 1-2 gạch đầu dòng chỉ rõ Ai làm gì, ở đâu (chuẩn xác theo ảnh thật).
   - **✅ Điểm sáng:** 1 gạch đầu dòng chốt hạ lý do khung hình hiệu quả.
   - **⚠️ Điểm yếu:** 1 gạch đầu dòng chỉ ra điểm gợn hoặc điểm cần khắc phục.
   - **💡 Bài học:** 1 gạch đầu dòng chốt kinh nghiệm thực chiến.
   - **⚙️ Kỹ thuật (3 Hệ Quy Chiếu Bắt Buộc):** Đánh giá sắc bén 3 yếu tố:
     1. `Góc máy`: Có thay đổi >30 độ so với shot trước để chống Jump Cut không?
     2. `Nhịp độ`: Shot này có < 3s không? Nếu >3s thì có chuyển động nội tại cứu vớt không?
     3. `Cỡ cảnh & Nhịp thở`: Không ép đổi cỡ cảnh luân phiên. Đánh giá xem shot này đang làm nhiệm vụ *Breathe-In (Cận liên tiếp bơm cảm giác)* hay *Breathe-Out (Toàn/Trung để nhả không gian)*.
3. **MEGA PROMPT ÁNH XẠ 1-CHẠM:**
3. **MEGA PROMPT ÁNH XẠ 1-CHẠM** (`### ⚡ MEGA PROMPT ÁNH XẠ 1-CHẠM (ZERO-FRICTION STORYBOARD)`): mẫu nguyên văn trong `references/examples_and_catalog.md`.
4. **KHỐI LIÊN KẾT TƯ LIỆU DƯỚI ĐÁY:**
   Thư mục máy, Video gốc, Google Drive, Xem Báo Cáo Web.

---

### BƯỚC 4: ĐỒNG BỘ NGƯỢC (REVERSE SYNC) & AI-NATIVE V2 ĐẢM BẢO 100% NHẤT QUÁN
Trước khi phân loại, BẮT BUỘC đọc `[đường-dẫn-Mac]` và nạp Few-Shot Rules từ chỉnh sửa của anh Việt: `python3 "[đường-dẫn-Mac]" --print-fewshot-prompt`.
Sau khi đồng bộ xong, chạy tiếp `python3 "[đường-dẫn-Mac]"` để tự động tính toán 5 trục AI-Native V2.
Ngay sau khi phân tích xong bằng Mắt Thần, AI **BẮT BUỘC** gọi script đồng bộ ngược để ghi đè phân tích thị giác thật vào file dữ liệu và HTML:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
**🚨 QUAN TRỌNG: TRƯỚC KHI CHẠY SCRIPT TRÊN, AI BẮT BUỘC PHẢI DÙNG TOOL GHI ĐÈ KẾT QUẢ PHÂN TÍCH CHI TIẾT TỪNG SHOT VÀO FILE `shot_info.json` CỦA THƯ MỤC DỰ ÁN.** Nếu AI bỏ qua bước sửa file JSON này, báo cáo HTML xuất ra sẽ bị kẹt lại dữ liệu rác (văn mẫu OpenCV) của Bước 2.

Script tự động: ghi `shot_info.json`, tạo lại HTML Light Theme, đồng bộ `vietndj.github.io/reports/` + `ytuong-fedu-vn/reports/`, cập nhật `master_classifications.json`, rebuild `build_ideas_bank.py`, deploy Cloudflare Pages, `git commit` + `git push` cả hai kho (chi tiết từng bước: `references/examples_and_catalog.md`).

---

## 📌 QUY TẮC BẢO VỆ DUNG LƯỢNG & CLOUDFLARE DEPLOY (<25MB)
1. Cấm base64 trong HTML (HTML 50-80KB); 2. Cấm Vercel — chỉ Cloudflare Pages; 3. Cập nhật `dist/` qua `build_ideas_bank.py` rồi deploy `npx wrangler pages deploy dist --project-name ytuong-fedu-vn-pages` (token Cloudflare đặt trong biến môi trường `CLOUDFLARE_API_TOKEN`; lệnh đầy đủ: `references/examples_and_catalog.md`).

---

## 📌 GIAO DIỆN BÁO CÁO HTML & NHÚNG YOUTUBE SABAKIZ
Shot card tối giản (headline + 1 câu insight, metadata trong `<details>`), Light Theme, template tại `[đường-dẫn-Mac]`; mọi JS player BẮT BUỘC kiểm tra `player.tagName === 'IFRAME'` + `postMessage`. Chi tiết: `references/examples_and_catalog.md`.

---

## 📚 TÀI LIỆU THAM CHIẾU (ĐỌC KHI CẦN)

> Các workflow phụ trợ được tách riêng để tiết kiệm context. Khi trigger tương ứng, đọc file trước khi thực thi.

| Workflow | Trigger | File |
|---|---|---|
| **Carousel → YouTube Upgrade** | Sửa/nâng cấp ≥2 báo cáo carousel | `references/carousel-yt-upgrade.md` |
| **B-Roll Bank Pipeline** | `UP BROLL`, `BROLL BANK`, `brollbank` | `references/broll-and-storyboard-pipeline.md` |
| **Storyboard Studio** | Tạo bảng phân cảnh, `/storyboard` | `references/broll-and-storyboard-pipeline.md` |

| **YouTube Token & Troubleshooting** | Lỗi upload kênh, quota, khung hình ngang | `references/youtube-token-troubleshoot.md` |

---

## 📌 KIẾN TRÚC CHỐNG LỖI 12 CHỐT CHẶN & HEALTH CHECK
Chi tiết 12 chốt chặn: `references/examples_and_catalog.md`. Sau khi sửa pipeline/đồng bộ hàng loạt, BẮT BUỘC chạy `python3 [đường-dẫn-Mac]` và đạt **OVERALL HEALTH CHECK: PASS (100%)** trước khi bàn giao.

