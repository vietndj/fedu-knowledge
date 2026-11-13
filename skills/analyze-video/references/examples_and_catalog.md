# analyze-video — Nền tảng hỗ trợ, scrape Lazada, UI báo cáo & 12 chốt chặn

> Phần tham chiếu tách từ `SKILL.md` (nội dung gốc giữ nguyên 100%).

<!-- gốc: SKILL.md dòng 150-155 -->
1. **CẤM BASE64 TRONG HTML**: Tuyệt đối không nhúng video hoặc ảnh base64 vào file HTML. File báo cáo HTML chỉ chứa URL CDN và iframe YouTube, dung lượng giữ mức 50-80KB để không vượt ngưỡng 25MB của Cloudflare Pages.
2. **CẤM TUYỆT ĐỐI VERCEL**: Đã khai tử Vercel trên toàn hệ thống. Mọi website phát sóng trực tiếp qua Cloudflare Pages.
3. **ĐÓNG GÓI & DEPLOY CHUẨN**:
   - Luôn cập nhật thư mục `dist/` qua `build_ideas_bank.py`.
   - Deploy lệnh chuẩn (tự nạp token từ `cloudflare_credentials.json`): `CLOUDFLARE_API_TOKEN="$(jq -r .api_token [đường-dẫn-Mac])" npx wrangler pages deploy dist --project-name ytuong-fedu-vn-pages`.

<!-- gốc: SKILL.md dòng 138-145 -->
Script sẽ tự động:
1. Ghi nhận dữ liệu phân tích chuẩn vào `shot_info.json`.
2. Tạo lại file HTML báo cáo **Light Theme chuẩn 30ngayviral** (compact shot cards, clickable links).
3. Đồng bộ sang `vietndj.github.io/reports/` và `ytuong-fedu-vn/reports/`.
4. Cập nhật `master_classifications.json` đúng ngành nghề, kiểu quay, tags.
5. Rebuild YTUONG ideas bank (`build_ideas_bank.py`) đóng gói vào `dist/`.
6. Tự động deploy Cloudflare Pages: `CLOUDFLARE_API_TOKEN="$(jq -r .api_token [đường-dẫn-Mac])" npx wrangler pages deploy dist --project-name ytuong-fedu-vn-pages`.
7. Tự động `git commit` và `git push` lên cả hai kho mã nguồn.

<!-- gốc: SKILL.md dòng 116-119 -->
   ```markdown
   ### ⚡ MEGA PROMPT ÁNH XẠ 1-CHẠM (ZERO-FRICTION STORYBOARD)
   📸 **Thả 1 tấm ảnh chỗ bạn định quay vào đây, hoặc gõ nhanh 3 từ khóa (Ví dụ: Spa - Khách - Lọ Serum / Quán Ăn - Bếp - Món Nóng)**. Tôi sẽ nội suy đồ vật và đẻ ra thẳng Bảng Phân Cảnh (Storyboard) áp dụng ngay công thức này cho bạn quay ngay!
   ```

<!-- gốc: SKILL.md dòng 97-104 -->
   ```markdown
   # [Tên Đòn Bẩy Thị Giác / Kỹ Thuật Đắt Giá Nhất Của Video]
   **Nguồn:** [@Tên_Creator](Link_Gốc_Instagram_Hoặc_TikTok)  
   **Mạch ý tưởng:** [Chủ Đề 1](https://ytuong.fedu.vn/?q=chu-de-1) • [Chủ Đề 2](https://ytuong.fedu.vn/?q=chu-de-2)

   **TRỤC KỊCH BẢN 3 NHỊP**  
   [Nhịp 1: Mồi mắt/Hook] ➔ [Nhịp 2: Thân bài/Cú đấm thị giác] ➔ [Nhịp 3: Chốt hạ/CTA]
   ```

<!-- gốc: SKILL.md dòng 193-219 -->
## 📌 KIẾN TRÚC CHỐNG LỖI 12 CHỐT CHẶN (OPUS HARDENED)

Toàn bộ pipeline `analyze_video_daemon.py` → `analyze_and_upload.py` → `sync_ai_analysis.py` → `build_ideas_bank.py` áp dụng 12 chốt chặn kỹ thuật bắt buộc:

1. **Khóa File Liên Tiến Trình & Atomic Write (`#1`, `#5`, `#7`)**:
   - Mọi thao tác đọc/ghi `analyze_video_queue.json`, `video_tasks_queue.json`, và `master_classifications.json` đều bọc trong `threading.RLock()` + `fcntl.flock` và ghi qua file tạm `.tmp` + `os.replace` để chống race condition giữa Daemon, Worker và Agent.
2. **Bảo Toàn Whisper Transcript & Multi-Video Carousel (`#2`)**:
   - `analyze_and_upload.py` xuất `speech.json` (chứa `speech_data`, `all_vids`, `source_url`, `youtube_url`, `youtube_id`) và lưu `all_vids` ngay vào `shot_info.json`. Khi `sync_ai_analysis.py` chạy lại sẽ tự động nạp `speech.json` + `all_vids` để không bao giờ làm mất lời thoại hay carousel.
3. **Khai Tử Fallback Chết & Bảo Toàn Link YouTube (`#3`, `#4`)**:
   - Tuyệt đối không dùng fallback chết `https://media.fedu.vn/videos/{shortcode}.mp4`. Link YouTube được lưu dự phòng ở cả `youtube.json`, `shot_info.json`, `speech.json` và `master_classifications.json`.
   - Mọi trình phát (`<iframe>` YouTube hoặc `<video>`/carousel) đều có `id="mainPlayer"`, `enablejsapi=1` và hàm `playShot()` kiểm tra `player.tagName === 'IFRAME'` dùng `postMessage`.
4. **Dọn Hàng Đợi Tự Động & Đóng Vòng Đời `VISION_PENDING` (`#6`, `#8`, `#10`)**:
   - `sync_ai_analysis.py` sau khi xuất báo cáo sẽ tự động chuyển trạng thái task từ `VISION_PENDING` sang `COMPLETED` trong queue.
   - `housekeep_tasks()` trong daemon tự động đóng các task `VISION_PENDING` treo quá 30 phút và giới hạn file queue tối đa 200 task gần nhất; `MAX_RETRY = 3` chống lặp vô tận.
5. **Chuẩn Hóa Bắt `RESULT_JSON:` & Git Rebase (`#5`, `#9`)**:
   - `analyze_and_upload.py` in `RESULT_JSON:` ở dòng cuối cùng để `parse_result_json()` trong daemon bắt chính xác `folder_name`, `shortcode`, `report_file`, `youtube_url`.
   - `rebuild_and_push()` luôn chạy `git pull --rebase` trước khi push.
6. **Chống Crash `StopIteration` & Đồng Bộ 1:1 `dist/reports` (`#11`, `#12`)**:
   - Mọi lệnh `next(...)` tra cứu `COUNTRIES` / `INDUSTRIES` trong `build_ideas_bank.py` đều có default value an toàn, đồng thời tự động dọn file thừa trong `dist/reports/` để khớp 1:1 với `reports/`.
   - Các file nhạy cảm (`client_secrets.json`, `youtube_token.json`, `cookies.txt`, `*.tar.gz`, `.DS_Store`) luôn nằm trong `.gitignore`.

### 🔍 Kiểm Định Sức Khỏe Toàn Hệ Thống (Health Check Verifier)
Sau khi sửa đổi pipeline hoặc đồng bộ báo cáo hàng loạt, chạy lệnh kiểm định tự động:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
Script kiểm tra 5 hạng mục (Queue JSON & Zombie `VISION_PENDING`, Dung lượng HTML < 1MB & Zero Base64, Chuẩn `mainPlayer` + `IFRAME` + `enablejsapi=1`, Đồng bộ `master_classifications.json` & `dist/reports/`, và `.gitignore`) — bắt buộc đạt **OVERALL HEALTH CHECK: PASS (100%)** trước khi bàn giao.

<!-- gốc: SKILL.md dòng 159-175 -->
## 📌 QUY TẮC VỀ GIAO DIỆN BÁO CÁO HTML (COMPACT SHOT CARD)

1. **Shot card tối giản**: Mỗi cảnh chỉ hiển thị **headline + 1 câu key insight** (logic/tinh thần cảnh). Metadata kỹ thuật (góc máy, ánh sáng, chuyển cảnh, bối cảnh) **ẩn trong accordion** `<details>`.
2. **Clickable links**: Tiêu đề → link reel gốc. Tên creator → link IG profile. KHÔNG hiển thị "Tệp:" hay "Trực quan: 9:16 Vertical HD".
3. **Light Theme**: Kế thừa design system 30ngayviral.fedu.vn (nền trắng, FD Aeonik + Tiempos Text, SVG icons thay emoji).
4. **Template tách riêng**: HTML template nằm tại `[đường-dẫn-Mac]`, Python chỉ bơm data vào template.

---

## 📌 QUY TẮC NHÚNG VIDEO YOUTUBE SABAKIZ (BẮT BUỘC)

Mọi video phân tích đều BẮT BUỘC upload lên YouTube kênh Sabakiz (playlist "Phân tích video" / "Ý tưởng", chế độ Unlisted):
- Script `sync_ai_analysis.py` tự động phát hiện và upload lên YouTube nếu chưa có link YouTube.
- Nhúng `<iframe>` YouTube trực tiếp vào báo cáo HTML (`mainPlayer`) và đồng bộ `youtube_embed`, `youtube_id` vào `master_classifications.json` cũng như `ytuong.fedu.vn`.
- KHÔNG dùng thẻ `<video>` trực tiếp từ R2 để phát video chính. R2 chỉ lưu trữ keyframe và video backup.
- Mọi hàm JS trong report (`playShot`, `setSpeed`, `stepFrame`, `toggleMute`) BẮT BUỘC kiểm tra `player.tagName === 'IFRAME'` và dùng `postMessage` thay vì gọi trực tiếp thuộc tính HTML5 Video.

<!-- gốc: SKILL.md dòng 31-60 -->
## 📌 NGUỒN VIDEO HỖ TRỢ (SUPPORTED PLATFORMS)

Script `analyze_and_upload.py` hỗ trợ tải và phân tích video từ **tất cả các nền tảng sau**:

| Nền tảng | Ví dụ link | Cơ chế tải |
|---|---|---|
| **Instagram Reels** | `https://www.instagram.com/reel/DcgEuvwx47P/` | `yt-dlp --cookies-from-browser chrome` |
| **TikTok** | `https://www.tiktok.com/@user/video/123` | `yt-dlp` hoặc TikTok API |
| **YouTube / Shorts** | `https://youtu.be/C3ZQYhluv4o` | `yt-dlp` |
| **Facebook Video** | `https://fb.watch/...` | `yt-dlp` |
| **Lazada** | `https://s.lazada.vn/s.oU2DB?c=w` | Playwright headless cạo video URL từ trang sản phẩm (`fetch_lazada_meta`) |
| **Shopee** | `https://shopee.vn/product/...` hoặc link rút gọn Shopee | Playwright headless cạo video URL từ trang sản phẩm (`fetch_shopee_meta`) |

### Quy tắc tải video quảng cáo E-Commerce (Shopee & Lazada):
1. Script dùng **Playwright headless** mở trang sản phẩm, đợi video player render, trích xuất URL video gốc (`.mp4`).
2. Sau khi tải, video được upload lên **YouTube Sabakiz (Unlisted)** với tiêu đề chuẩn `[ECOM] Tên_Sản_Phẩm - @Tên_Shop`.
3. Phân loại tự động: tag `UGC`, `quang-cao`, ngành `cong-nghe` / `thoi-trang` / `gia-dung` tùy nội dung.
4. Thumbnail keyframe upload lên R2 (`media.fedu.vn/images/`).

### 🔧 CƠ CHẾ SCRAPE VIDEO LAZADA (ĐÃ CẬP NHẬT — Tháng 9/2026)

> **KHÔNG dùng Network Response Listener để bắt link `.mp4`** — Lazada đã đổi cơ chế, link video KHÔNG còn xuất hiện trong XHR/Fetch responses khi headless. Script cũ trả về `None`, gây lỗi `OpenCV: Couldn't read video stream from file ".../video.mp4"`.

**Cơ chế mới (đã sửa trong `fetch_lazada_meta()` tại `analyze_and_upload.py`):**
1. Vẫn gắn `page.on('response', ...)` làm **fallback dự phòng** nhưng không phụ thuộc chính.
2. Dùng `page.evaluate()` tiêm JS trực tiếp → cưỡng ép click nút Play `.gallery-preview-panel-v2__video-player`.
3. Trong vòng lặp 15 lần, sau mỗi click → `page.evaluate()` quét `document.querySelectorAll('video')` → lấy `src` attribute trực tiếp từ thẻ HTML `<video>`.
4. Ngay khi `video.src` có giá trị `http...` → thoát vòng lặp, gán `video_url`.

---
