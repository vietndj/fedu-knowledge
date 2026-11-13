---
name: edit-hang
description: "Mantra: EDIT VIDEO THEO KIỂU CỦA HẰNG / EDIT THEO KIỂU HẰNG / LÀM VIDEO THEO KIỂU CỦA HẰNG / DỰNG VIDEO THEO KIỂU HẰNG / EDIT CHO HẰNG / EDIT HẰNG / EDIT HANG / EDIT ALICE / SPA PA2 / XEM HOOK HẰNG / ĐỔI HOOK HẰNG / CẬP NHẬT EDIT HẰNG. Kỹ năng dựng video chuyên biệt chuẩn PA2-V9.4.0 dành riêng cho MASTER ALICE THANH HẰNG (ALICE BEAUTY & ACADEMY): chỉ cần gọi kèm tên video, tự động quét & đọc nội dung các video/ảnh xung quanh (có hoặc không có thư mục broll) để làm cảnh trám, tự gắn Logo ALICE cánh lá đỏ, tự nhớ phương án Hook H0..H5, và luôn có màn hình kết Silk Ivory Atelier kèm nút cta đỏ."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `edit-hang` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).


# 🎬 KỸ NĂNG DỰNG VIDEO RIÊNG — MASTER ALICE THANH HẰNG (`EDIT-HANG` · PA2-V9.4.0)

> ⚡ **KỶ LUẬT SIÊU TIẾT KIỆM TOKEN & TỰ ĐỘNG HÓA 100%:**
> 1. **CẤM TUYỆT ĐỐI** dùng `read_file` đọc mã nguồn trong `scripts/` hoặc đọc file kỹ thuật `plan.json`.
> 2. **CHỈ ĐỌC/SỬA** file nội dung chữ `content.json` (và xem bảng ảnh `<work_dir>/broll_contact_sheet.jpg` nếu có cảnh trám xung quanh) và luôn truyền cờ `--quiet-json`.
> 3. **Mặc định 100% video xuất ra đều tự động có:**
>    - **Chỉ cần gọi kèm tên video (`<tên_video.mp4>`) — Tự động quét & đọc nội dung các video/ảnh xung quanh làm cảnh trám:** Nếu có thư mục `broll/` (`tram/`, `anh/`...) thì quét thư mục đó; **nếu KHÔNG có thư mục `broll/`**, tự động quét toàn bộ các video & ảnh nằm ngay cạnh video đó và trong các thư mục con xung quanh, tự loại bỏ các video đứng nói (A-Roll) khác, đọc nội dung thị giác từng video/ảnh (`broll_contact_sheet.jpg` + `broll_catalog_readonly`) và ghép khớp ngữ nghĩa vào đúng câu nói!
>    - **Logo ALICE cánh lá đỏ** trên góc phải các bảng Motion Graphic.
>    - **Màn hình kết `Silk Ivory Atelier`** có ảnh đại diện tròn + Logo thương hiệu + Địa chỉ + **Nút CTA đỏ: `"NHẮN HẰNG XEM NỀN MÔI & TƯ VẤN 1:1   →"`**.
>    - **Tự động nhớ phương án Hook mở đầu (`H0..H5`)** từ lần chọn cuối cùng trên máy (`~/.fedu/alice_thanh_hang/state.json`).

## 🗣️ 1. CÁCH GỌI TỰ NHIÊN TRÊN MÁY (0 MA SÁT)

| Mong muốn của chị | Câu gõ tự nhiên vào ô chat | Lệnh Agent thực thi (`spa_pa2_engine.py`) |
| :--- | :--- | :--- |
| **1. Dựng video chuẩn có sẵn CTA & tự quét cảnh trám xung quanh** | *"Edit video theo kiểu của Hằng `<tên_video.mp4>`"*<br/>*"Làm video theo kiểu của Hằng `<tên_video.mp4>`"* | Gọi `extract --video "<tên_video>"` -> Xem `broll_contact_sheet.jpg` + biên tập `content.json` -> Gọi `audit` -> Gọi `render`. Tự động tìm & đọc nội dung video/ảnh xung quanh làm cảnh trám, dùng Hook đã nhớ và gắn Outro + nút cta đỏ. |
| **2. Xem bảng 6 mẫu Hook mở đầu (`H0..H5`)** | *"Xem mẫu hook"* / *"Có mấy kiểu hook"* | Chạy `hooks --brand alice_thanh_hang --quiet-json` và hiển thị ảnh `hook_sheet.jpg` (`H0..H5`) cho chị chọn. |
| **3. Đổi kiểu Hook mở đầu (và tự nhớ cho các lần sau)** | *"Làm video này với hook H2 (hoặc hook poster)"*<br/>*"Đổi sang hook H0 (không khung)"* | Truyền thêm cờ `--hook H2` (hoặc `H0..H5`). Nếu chị nói *"lần này thôi"* thì thêm `--once`. |
| **4. Đổi chữ trên nút kêu gọi hành động (CTA)** | *"Đổi nút CTA cuối video thành: NHẮN HẰNG TƯ VẤN 1:1"* | Chạy `hooks --brand alice_thanh_hang --set-cta "NHẮN HẰNG..." --quiet-json` (lưu vĩnh viễn vào `~/.fedu/alice_thanh_hang/brand.local.json`). |
| **5. Cập nhật phiên bản mới tự động** | *"Cập nhật edit pro"* / *"Cập nhật edit"* | Chạy `update --brand alice_thanh_hang --quiet-json` (giữ nguyên 100% CTA và Hook đã nhớ). Nếu cần quay lui: thêm `--rollback`. |

## 🔄 2. QUY TRÌNH BẮT BUỘC 4 BƯỚC CHO MỌI VIDEO MỚI (`PA2-V9.4.0`)

1. **Bước 1 — Bóc băng Whisper từ-nhịp & Tự động quét + đọc nội dung video/ảnh xung quanh (`extract`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
   *(Lưu ý: Chỉ cần truyền tên video hoặc đường dẫn vào `--video`, Engine tự tìm file, bóc băng Whisper và tự động quét mọi video/ảnh xung quanh — dù có hay không có thư mục `broll/` — đọc nội dung thị giác từng file, xuất `<work_dir>/broll_contact_sheet.jpg` và khớp ngữ nghĩa vào `B1..B4`!)*
2. **Bước 2 — Đọc nội dung cảnh trám xung quanh (`broll_contact_sheet.jpg`) & Biên tập `content.json` (`PA2-V9.4.0`):**
   - Dùng `read_file` đọc `<work_dir>/content.json` VÀ **nếu có `<work_dir>/broll_contact_sheet.jpg` thì dùng `read_file` xem trực tiếp bảng ảnh thu nhỏ các video/ảnh xung quanh**.
   - **Phụ đề `subs` (`S1 SUB_VERBATIM`):** Giữ nguyên `start`, `end`, `id`, `take_id` và **giữ nguyên `>= 90%` từ vựng lời nói thật** của chị Hằng (chỉ sửa lỗi chính tả nếu có và ngắt 2 dòng `l1`, `l2` tròn nghĩa, cấm kết thúc dòng bằng từ treo như *"một, những, các, cho, của, là, mà"*).
   - **Cảnh trám `broll` (`B1..B5`):** Đối chiếu hình ảnh thật trên `broll_contact_sheet.jpg` (hoặc `broll_catalog_readonly`) với câu nói tại vị trí đó. Giữ hoặc hoán đổi `media_path` giữa các khe `B1..B4` sao cho hình ảnh video/ảnh xung quanh khớp 100% với lời chị Hằng đang nói, và đặt `headline` riêng biệt không trùng nhau mô tả đúng cảnh thực tế trong hình (`<= 28` ký tự). Với khe `macro_quote` (nếu có), viết `quote` là 1 câu nhận định đắt giá trích từ lời nói tại thời điểm đó (`8-14` từ).
   - **Hook, Chương mục `sections` (`01..04`), `timeline_nodes` & `posters` (`P1..P3`):**
     - Trong `hook`: `h1_line1` và `h1_line2` bắt buộc viết **100% IN HOA**.
     - Trong `posters` (`P1`, `P2`, `P3`): Biên tập nội dung `P1` (`versus` hoặc `layers`), `P2` (`criteria` ở chế độ `split_aroll` nửa trên đồ họa / nửa dưới mặt chị Hằng), `P3` (`criteria` hoặc `compare`) bám sát đúng các mốc lời nói trong video. **CẤM bịa số `%`** không có trong lời nói thật.
3. **Bước 3 — Kiểm toán tất định 22 cổng trước khi xuất (`audit`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
   *(Đảm bảo `v82_9_gates_pass: true` và `v9_gates_pass: true` — nếu báo lỗi ở cổng nào thì sửa ngay trường đó trong `content.json`).*
4. **Bước 4 — Kết xuất kèm Logo ALICE cánh lá đỏ, Hook đã nhớ & Màn hình kết CTA (`render`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
