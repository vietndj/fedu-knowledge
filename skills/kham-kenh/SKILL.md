---
name: kham-kenh
description: "Mantra: KHAM KENH / AUDIT KENH. Tự động đọc kênh FB/TikTok học viên, chụp màn hình, tải video, bóc lời thoại, chấm điểm qua 4 Định dạng & Vòng gửi xe 3s (Hộp nhung × Nhẫn vàng) và xuất Báo Cáo Khám Kênh 3 Tầng V2.0. (Kèm: DAY KHO STU)."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `kham-kenh` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).

> Tài liệu kèm: `references/auto-kho-drive.md`, `references/examples_and_catalog.md`


# KỸ NĂNG KHÁM KÊNH & GIẢI PHẪU VIDEO HỌC VIÊN (`kham-kenh` V2.0)

Kỹ năng vận hành theo **Kiến trúc Hybrid 1-Chạm V2.0**: kết hợp **MCP `viet-tools:kham_kenh` + Lăng kính 4 Định dạng & Logic Kênh (`05-dinh-dang-2.0.html`, `cu/index.html`, `logickenh-xaykenh.html`) + Cơ chế Giả thuyết hỏi lại chính chủ + Verifier tất định 12 cổng `verify_channel_audit.py`**.
*(Mẫu HTML V2.0, bảng chấm `.score-table`, thẻ 3 dòng `.video-audit-card`, khối `KENH_META` và nhánh Benchmark xem tại [`references/examples_and_catalog.md`](file://[đường-dẫn-Mac])).*

## 🧭 PHÂN VAI RẠCH RÒI GIỮA `kham-kenh` V2.0 VÀ `dinh-huong-kenh` V2.0
| Tiêu chí | `kham-kenh` (V2.0 — Giải phẫu hiện trường kênh) | `dinh-huong-kenh` (V2.0 — Giải phẫu dòng tiền & 5 mắt xích) |
| :--- | :--- | :--- |
| **Câu hỏi cốt lõi** | **Kênh đang làm gì trên từng thước phim và lệch chuẩn ở đâu?** (Có ảnh `strip.jpg` + lời thoại làm bằng chứng vật lý). | **Vì sao khách mua hàng giá cao, dòng tiền và niềm tin 7 giờ chảy qua 5 mắt xích thế nào?** |
| **Cách dùng Logic Kênh** | Không giảng lý thuyết dài dòng; biến thành **4 nhãn chấm tất định (`data-*`)** gắn trực tiếp lên từng video. | Phân tích sâu 3 Bức tường (420 phút), Bảng tâm lý 4 tầng, Chuỗi 11 điểm chạm Lurker → Dark Social. |
| **Độ dài & Hình thức** | **Nén sắc bén:** Chữ bình luận **$\le 3.000$ từ** (toàn trang $\le 6.000$ từ). **100% `h1`, `h2` là Tiêu đề dạng Câu hỏi (`?...`)** $\le 18$ từ. | Bản `.md` + `.html` thảo luận 5 mắt xích (`MX1..MX5`), kiểm định qua `verify_logic_kenh.py`. |
| **Cầu nối dữ liệu** | Sinh khối `<!-- KENH_META ... -->` + `3–6` câu hỏi xác minh chính chủ (`.question-block`) từ điểm bất thường trên kênh. | Kế thừa trực tiếp `KENH_META` và câu trả lời của chính chủ từ bài khám kênh. |

---

> **⚠️ QUY TẮC VĂN PHONG & CHỐNG GIÁO ĐIỀU BẮT BUỘC 100% (`nguyen-viet-voice` + `K10/K11`):**
> - Tuân thủ 100% [`nguyen-viet-voice/SKILL.md`](file://[đường-dẫn-Mac]) & danh sách từ cấm tại [`resources/blacklist.md`](file://[đường-dẫn-Mac]). Tâm thế người làm nghề ngồi xem từng thước phim cùng chủ kênh.
> - **CẤM TUYỆT ĐỐI:** (1) Toàn bộ từ sáo rỗng, kịch tính hóa, phán xét trong `blacklist.md` (dùng *"người làm nghề"* hoặc *"người thạo việc"*, *"chỗ khách giấu"*, *"bảng đối chiếu 4 định dạng"*); (2) Chữ `"FEDU"` và từ `"xô"` (dùng *"dòng nội dung"* / *"nhóm bài"*); (3) **Title Case** trên `h1..h4` (bắt buộc dùng **Sentence case**); (4) Chép nguyên văn từ `cu/index.html` hoặc `logickenh-xaykenh.html` ($\le 2$ cụm 10 từ trùng; mỗi nguyên lý gốc chỉ nhắc tối đa 1 câu).

## ⌨️ CÚ PHÁP KÍCH HOẠT (TRIGGER) & CỔNG PHÂN LOẠI (`student` vs `benchmark`)
| Mantra / Trigger | Phân loại vai trò | Đích xuất bản |
| :--- | :--- | :--- |
| `KHAM KENH : [Link FB/TikTok]` | `role = "student"`: Học viên có trong `students_master.json` (hoặc anh Việt xác nhận là học viên/lead mới) | `stu.fedu.vn` (`stu_profiles` + `/audits/<student_id>.html`) |
| `KHAM KENH MAU : [Link]` *(hoặc kênh lạ)* | `role = "benchmark"`: Kênh mẫu tham khảo (**CẤM** tạo thẻ trong `students_master.json`/`stu_profiles`) | `kho.fedu.vn` (`kenhmau-<slug>`, `pillar: "case-study"`, `type: "kenh-mau"`) |

---

## 🔄 CÁCH LÀM 5 BƯỚC V2.0 (NGẮN GỌN – SẮC BÉN – HỆ THỐNG HÓA)

### BƯỚC 1: PHÂN LOẠI VAI TRÒ (`student` | `benchmark`) & THU THẬP DỮ LIỆU
1. **Tra cứu bắt buộc trong Student Hub trước khi chạy:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
2. **Thu thập dữ liệu kênh** qua MCP `viet-tools:kham_kenh` hoặc CLI:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

### BƯỚC 2: SOI ẢNH THẬT & XUẤT BÁO CÁO `report.html` THEO KHUNG CÂU HỎI V2.0
0. **Nạp Nguyên Liệu Bộ Não Thứ 2 (`brain.py` — ~450 tokens):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
1. **Soi ảnh thật (`view_file`)**: Xem trực tiếp ảnh giao diện kênh (`screenshots/timeline_01.jpg`, `about_01.jpg`, `reels_grid_01.jpg`) và toàn bộ `strip.jpg` kết hợp đọc `transcript` trong `channel_raw_data.json`.
2. **Khai báo khối `<!-- KENH_META ... -->` ngay đầu `report.html`** (đủ 8 khóa: `san_pham`, `gia`, `chu_ky_suy_nghi`, `ap_dung_7h`, `giay_xem_tb`, `nguoi_thu_hai`, `kenh_rieng`, `gio_quay_tuan` — ghi rõ `[số liệu kênh]` hoặc `[giả định — cần hỏi chính chủ]`).
3. **Cấu trúc 3 Tầng V2.0 — 100% Tiêu đề `h1`, `h2` là Câu hỏi (`?...`, $\le 18$ từ) & Chữ bình luận $\le 3.000$ từ:**

   - **🏷️ Tiêu đề `H1` (Dạng câu hỏi $\le 18$ từ):**
     *Ví dụ: `Kênh của chị X đang bán bằng lượt xem giải trí hay bán bằng niềm tin làm nghề?`*

   - **🩺 TẦNG 1 ($\le 700$ từ) — Chẩn đoán hệ thống qua 3 câu hỏi lớn:**
     1. **`H2`: Kênh đang chiều lòng 1% người bình luận ồn ào hay nuôi 90% người xem thầm lặng?**
        - 3 dòng kết luận sắc gọn từ số liệu thật trên kênh + 1 câu kết luận về việc người mua thật nằm ở nhóm xem thầm lặng (90-9-1) và lưu bài/gửi riêng qua Zalo, Messenger (Dark Social).
     2. **`H2`: Nhìn vào 4 định dạng và 3 dòng nội dung, kênh đang lệch về đâu và bỏ trống chỗ nào?**
        - Bảng đối chiếu **4 Định dạng Video 2.0** ([05-dinh-dang-2.0.html](file://[đường-dẫn-Mac])):
          - `1. Voice-Over & Thao tác tay` (`voice-over` — 0% lộ mặt, cảnh trám 3 lớp Mồi–Băm–Nối chứng minh tay nghề).
          - `2. Walk & Talk` (`walk-talk` — 50–70% lộ mặt, 3 trục 45°, băm 3 pha Mồi–Chính–Nối tạo sự gần gũi).
          - `3. Talking Head` (`talking-head` — 30% lộ mặt, Mặt để tin – Cảnh để hiểu – Nhịp để xem hết, 2 góc 0°/45°).
          - `4. Storytelling 2.5` (`story-25` — Lát cắt 5 giây T2 + Tráng men thể diện T2.5 để khách có cớ đàng hoàng mua hàng).
        - Chỉ rõ kênh đang dồn bao nhiêu video vào định dạng nào, thiếu định dạng nào trong **3 dòng nội dung** (`Kết nối sâu` – `Đời sống 4 tầng` – `Khoe khéo dịch vụ / 31 Vỏ bọc`).
     3. **`H2`: Có những giả thuyết nào từ số liệu kênh cần hỏi lại chính chủ trước khi sửa?**
        - Đặt `2–3` cụm khối tương tác (`.analysis-block` `🔍 Giả thuyết từ điểm bất thường trên kênh` + `.question-block` `❓ Câu hỏi cần xác minh lại chính chủ` kèm `🔀 Nếu A → ... / Nếu B → ...`).

   - **🎬 TẦNG 2 ($\le 1.400$ từ bình luận) — Bảng chấm 12 video & 4–6 Thẻ giải phẫu đại diện (Cấm lặp lỗi):**
     1. **`H2`: 12 video trên kênh vượt qua vòng gửi xe 3 giây (Hộp nhung × Nhẫn vàng) ra sao?**
        - **Bảng Chấm Tổng Thể (`.score-table`, $\ge 5$ đến $12$ dòng `tr[data-format]`)**: Mỗi dòng chấm 1 video với đủ 5 thuộc tính `data-*`:
          - `data-format` & `data-format-next` $\in$ `{voice-over, walk-talk, talking-head, story-25, khac}`
          - `data-hop-nhung` (Thỏa mãn Thị giác / Chiếc hộp nhung: ánh sáng, bố cục, chuyển cảnh, âm thanh) $\in$ `{dat, rot, mot-phan}`
          - `data-nhan-vang` (Thỏa mãn Trí tuệ / Chiếc nhẫn vàng: mô tả đúng bệnh vi mô trong 3 giây đầu) $\in$ `{dat, rot, mot-phan}`
          - `data-dich` (Đích người xem) $\in$ `{1pct, 90pct}`
     2. **`H2`: Đâu là 4–6 kiểu lỗi đại diện trên kênh và sửa một lần thế nào cho cả nhóm?**
        - Thay vì viết 12 thẻ lặp lại cùng một lỗi, chỉ chọn **4–6 Thẻ Giải Phẫu Đại Diện (`.video-audit-card`)** — mỗi thẻ đại diện cho **1 kiểu bệnh hoặc 1 định dạng**.
        - Mỗi `.video-audit-card` gắn đủ `data-format`, `data-format-next`, `data-hop-nhung`, `data-nhan-vang`, `data-dich`, có ảnh `strip.jpg`, hộp `transcript` 3 nhịp **đặt gọn trong thẻ `<details>`**, và phần nhận xét **nén $\le 130$ từ** gồm đúng 3 dòng:
          1. **Vòng gửi xe 3 giây (Hộp nhung × Nhẫn vàng):** Khung hình 3s đầu có gì tốt giữ lại, câu mở đầu đang rớt ở đâu?
          2. **Lỗi kỹ thuật theo chuẩn 4 Định dạng:** Chiếu theo chuẩn định dạng đó đang thiếu gì (thiếu cảnh trám 3 lớp, góc máy chết 1 chỗ, hay thiếu lát cắt vi mô)?
          3. **Gọt lại ngay:** Viết thẳng 1 câu mở đầu mới + 1 nhịp cảnh trám cụ thể.
        - Nếu video có lượt xem vọt cao hoặc chìm bất thường, gắn ngay 1 khối `.question-block` (`❓ Hỏi lại chính chủ` + `🔀 Nếu A / Nếu B`).

   - **🧭 TẦNG 3 ($\le 900$ từ bình luận + 4 kịch bản) — Lộ trình 4 Định dạng, 4 Kịch bản mẫu & Bảng xác minh chính chủ:**
     1. **`H2`: Tuần này chính chủ nên bấm máy định dạng nào trước để khớp quỹ thời gian?**
        - Cách sửa lời giới thiệu đầu trang, 3 góc máy cố định, phối hợp **3 dòng nội dung** (`Kết nối sâu` – `Đời sống 4 tầng` – `Khoe khéo dịch vụ / 31 Vỏ bọc` — **bỏ tỷ lệ 40-40-20 cũ**), và lộ trình nâng cấp theo **4 Định dạng** khớp với `gio_quay_tuan`.
     2. **`H2`: Bốn kịch bản mẫu đại diện cho 4 định dạng viết sẵn từng câu trông thế nào?**
        - Xuất **đúng 4 thẻ `.script-card`** gắn thuộc tính `data-format` phủ đủ 4 định dạng:
          - Thẻ 1 (`data-format="voice-over"`): Kịch bản **Voice-Over & Thao tác tay** (thu âm trước, quay cảnh trám 3 lớp Mồi – Băm – Nối).
          - Thẻ 2 (`data-format="walk-talk"`): Kịch bản **Walk & Talk** (quy tắc 3 trục 45°, băm 3 pha Mồi – Chính – Nối).
          - Thẻ 3 (`data-format="talking-head"`): Kịch bản **Talking Head** (2 góc máy 0° & 45°, Mặt để tin – Cảnh để hiểu – Nhịp để xem hết).
          - Thẻ 4 (`data-format="story-25"`): Kịch bản **Storytelling 2.5** (Lát cắt 5s T2 + Tráng men thể diện T2.5 — **bắt buộc có 1 câu trong ngoặc kép `“...”` khách dùng để nói với `nguoi_thu_hai` khi gửi link qua Zalo/Messenger**).
     3. **`H2`: Còn những điểm mù dữ liệu nào cần hỏi lại chính chủ trước khi chốt hướng đi?**
        - Bảng tổng hợp các điểm mù dữ liệu còn thiếu (bắt buộc có `giay_xem_tb`, `nguoi_thu_hai`, `gio_quay_tuan` kèm phân nhánh `Nếu Phương án A → ...` / `Nếu Phương án B → ...`).
        - Khối `<div class="note-block" contenteditable="true">` (`💡 Ghi chú xác minh cùng chính chủ` — tự lưu `localStorage` và có nút Copy biên bản).

### BƯỚC 3: KIỂM ĐỊNH TẤT ĐỊNH 12 CỔNG QUA `verify_channel_audit.py` V2.0
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Bắt buộc đạt `"pass": true, "issues_count": 0` qua đủ **12 Cổng `K0..K11`** (Dữ liệu thô thật không fallback giả `K0`; Trần chữ bình luận $\le 3.000$ từ & mỗi thẻ $\le 130$ từ `K1`; 100% `h1/h2` là câu hỏi $\le 18$ từ `K2`; Đủ nhãn 4 Định dạng `K3`; Đủ nhãn Vòng gửi xe Hộp nhung × Nhẫn vàng `K4`; Đích 1% vs 90% Lurker/Dark Social `K5`; 3–6 khối Giả thuyết & Câu hỏi xác minh chính chủ `K6`; Đủ `KENH_META` & Bảng điểm mù `K7`; Ô ghi chú `localStorage` `K8`; Đúng 4 kịch bản cho 4 định dạng `K9`; Chống chép giáo điều `K10`; 0 từ cấm `nguyen-viet-voice` + 0 chữ `"FEDU"`/`"xô"` + UI Sáng Responsive `K11`).

### BƯỚC 4: UPLOAD ONLINE (CDN R2 `media.fedu.vn` & YOUTUBE `Sabakiz`)
1. **Đẩy ảnh, video `.mp4` và `report.html` lên CDN R2 (`https://media.fedu.vn/stu-audits/<student_id>/`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
2. **Đẩy video phân tích lên YouTube `Sabakiz`**: Dùng `[đường-dẫn-Mac] BANK/youtube_batch_upload.py` (tự xoay vòng `token_project_1..12.json` trong `[đường-dẫn-Mac] BANK/` — nếu thiếu token thì báo cần OAuth lại), tạo/lấy Playlist `<Tên Học Viên> K3`, upload chế độ `unlisted`.

### BƯỚC 5: XUẤT BẢN ĐÚNG ĐÍCH THEO VAI TRÒ & ĐỒNG BỘ TỰ ĐỘNG 1 NGUỒN (`STU ↔ KHO`)
- **Nhánh A (`role == "student"` $\rightarrow$ `stu.fedu.vn` + tự động đồng bộ sang `kho.fedu.vn/kham-kenh`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- **Nhánh B (`role == "benchmark"` $\rightarrow$ `kho.fedu.vn`):** Copy HTML vào `kho-fedu-vn/docs/public/audits/kenhmau-<slug>.html` & `k/kenhmau-<slug>.html`, tạo 3 chương Markdown + đăng ký `semantic_map.json` & `BENCHMARK_CHANNEL_MAP`, rồi chạy `build_related.py`, `build_fedu_graph.py` và `ship.py --site kho --auto-commit`.

### BƯỚC 6: BÁO CÁO KẾT LUẬN THUYẾT PHỤC ANH VIỆT TRÊN CHAT (CẤM CHUỖI TIN NHẮN MẪU)
- **TUYỆT ĐỐI CẤM** tự động xuất "Chuỗi tin nhắn tư vấn Zalo/Messenger mẫu" để mớm lời gửi học viên (anh Việt tự trò chuyện với học viên bằng giọng thật của anh; chỉ soạn tin nhắn khi anh Việt yêu cầu rõ *"soạn tin nhắn"*).
- Phản hồi cuối trên Chat chỉ gồm **Link bấm 1 chạm** + **Khối Kết Luận Bảo Vệ Phương Án ($\le 220$ từ, 4 mũi đinh)** để thuyết phục anh Việt:
  1. **Luận điểm chốt hạ:** Mũi nhọn duy nhất cần đánh cho ca này là gì và vì sao bác bỏ các hướng khác?
  2. **Bằng chứng số liệu đối chứng:** Cặp số liệu thực tế nào trên kênh chứng minh cơ chế đó đúng?
  3. **Tử huyệt cảnh báo:** Học viên đang hiểu lầm ở đâu — nếu chiều theo ý họ mà không nắn lại sẽ gãy kênh thế nào?
  4. **2 Biến số cần kiểm chứng:** Đúng 2 điểm mù thực địa anh Việt cần xác nhận khi gặp học viên.


---
## 🛰️ Nhánh Kỹ Năng Hợp Nhất (Giữ Nguyên Đường Dẫn Scripts)

| Mantra / Tác vụ | Tài liệu chi tiết (chỉ đọc khi gọi đúng nhánh) | Thư mục Scripts gốc (không đổi) |
|---|---|---|
| **DAY KHO STU / AUTO KHO DRIVE** — Đẩy bài Khám kênh/Định hướng (.html) lên stu.fedu.vn & kho.fedu.vn + video AI lên Drive | [`references/auto-kho-drive.md`](file://[đường-dẫn-Mac]) | `[đường-dẫn-Mac]` |
