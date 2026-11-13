---
name: auto-kho-drive
description: "Tự động đẩy bài Khám kênh/Định hướng (.html) lên stu.fedu.vn & kho.fedu.vn kèm phá cache ?v=<sha8>, và tự động đánh số phiên bản (v01, v02...) đẩy video AI lên Google Drive."
---

# KỸ NĂNG TỰ ĐỘNG HÓA KÉP: PHÂN TÍCH KÊNH LÊN KHO & ĐÁNH SỐ PHIÊN BẢN VIDEO AI LÊN GOOGLE DRIVE (`auto-kho-drive`)

Kỹ năng này vận hành **tự động 100% (Zero-Prompt)** ở tầng hạ tầng cho 2 nhu cầu cốt lõi của anh Việt mà không cần anh Việt phải nhắc lại ở từng phiên làm việc:

---

## 🏛️ TRỤ CỘT 1: TỰ ĐỘNG ĐẨY & CẬP NHẬT PHÂN TÍCH KÊNH / KHÁM KÊNH / HỌC VIÊN LÊN KHO (`STU ↔ KHO`)

### 1. Nguyên lý vận hành (Hội thảo cùng CLAUDE2 Opus 5.5)
- **Single Source of Truth:** Mọi file `.html` khám kênh, phân tích logic kênh, hệ quy chiếu, định hướng học viên hoặc kịch bản tư vấn đều được lưu chuẩn hóa tại `[đường-dẫn-Mac]` và đăng ký trong `[đường-dẫn-Mac] gia/data/audit_registry.json` + `students_master.json`.
- **Thẻ định danh tự động (`<script id="audit-meta">`):** Mỗi file HTML đều được tự động nhúng `<script type="application/json" id="audit-meta">` chứa `student_id`, `loai_tai_lieu`, `content_sha8`, `canonical_url`.
- **Tự động phát hiện sửa đổi HTML & Phá Cache Iframe (`?v=<sha8>`):**
  - Khi bất kỳ file phân tích `.html` nào (dù nằm ở `stu.fedu.vn/audits/`, `course_repo/`, hay `k/`) được chỉnh sửa hoặc cập nhật, `sync_kho_audits.py` tự động tính mã băm `SHA256` chuẩn hóa (`content_sha8`).
  - Nếu nội dung thay đổi: tự động copy bản mới nhất về `stu.fedu.vn/audits/`, tự động bóc lại `<title>` & dàn ý `H2/H3` mới nhất vào bài viết Markdown trên `kho.fedu.vn`, và gắn tham số `?v=<content_sha8>` vào `nguon_url` để khung **`🖥️ Trang thiết kế gốc`** trên `kho.fedu.vn` lập tức hiển thị bản mới nhất (không bao giờ bị dính cache Cloudflare).
- **Cascade Hook 1 Chiều trong `ship.py`:**
  - Khi chạy `ship.py --site stu --auto-commit`, hệ thống tự động chạy `sync_kho_audits.py --json-status`. Sau khi `stu.fedu.vn` deploy thành công (HTTP 200), nếu có file phân tích mới hoặc vừa được sửa, `ship.py` **tự động kích hoạt deploy `kho.fedu.vn` luôn**!

### 2. Lệnh 1-Chạm khi Tạo Mới hoặc Cập Nhật File Phân Tích HTML bất kỳ
Khi anh Việt yêu cầu **phân tích kênh, khám kênh, lập hệ quy chiếu, viết định hướng học viên**, hoặc **sửa/update một file phân tích HTML**, sau khi tạo/sửa file `.html`, chỉ cần chạy **1 lệnh duy nhất**:

> _(lệnh chạy trên Mac — đã lược khi lên Web)_
*(Nếu chỉ sửa trực tiếp các file HTML đã có sẵn trong `stu.fedu.vn/audits/`, `course_repo/` hoặc `k/`, chỉ cần chạy `python3 "[đường-dẫn-Mac] gia/sync_kho_audits.py" --ship` hoặc `python3 "[đường-dẫn-Mac] gia/ship.py" --site stu --auto-commit` — hệ thống sẽ tự động phát hiện file nào vừa sửa và cập nhật lên Kho).*

---

## 🎬 TRỤ CỘT 2: TỰ ĐỘNG ĐẨY VIDEO CHỈNH SỬA AI LÊN GOOGLE DRIVE KÈM ĐÁNH SỐ PHIÊN BẢN (`v01`, `v02`, `v03`...)

### 1. Nguyên lý vận hành (`video_vault.py` + Hook `telegram_notify.py`)
- **Kích hoạt tự động 100% qua Cổng Telegram:**
  - Mọi kỹ năng làm video AI (`ai-hook`, `auto-edit-video`, `spa-edit`, `before-after-video`, `motion`, `so-do-motion`, `google-flow`, `render-v3`) khi xuất xong file `.mp4` / `.mov` đều đi qua `telegram_notify.py --video "<file.mp4>"`.
  - `telegram_notify.py` đã được gắn hook trực tiếp gọi `video_vault.register_and_spawn_upload(...)`:
    1. **Cấp số phiên bản tức thì (`< 0.1s`):** Tự động gom nhóm về đúng `project_slug` (cắt bỏ các hậu tố `_v1`, `_final`, `_fix_seam`, `_edit`, `_20261029`...; nếu tên file chung chung như `output_final.mp4` thì tự động gom theo thư mục cha hoặc `cid` của cuộc trò chuyện).
    2. **Chống trùng bằng `SHA256`:** Nếu sửa và render lại (kể cả ghi đè lên cùng tên file `output_final.mp4`) $\rightarrow$ `SHA256` mới $\rightarrow$ tự động tăng lên **`v02`**, **`v03`**, **`v04`**... Nếu gửi lại đúng file cũ (trùng `SHA256`) $\rightarrow$ giữ nguyên số phiên bản cũ, không upload thừa.
    3. **Đẩy ngầm lên Google Drive:** Tự động tải lên thư mục tập trung `gdrive:AI_EDITED_VIDEOS/<project_slug>/<project_slug>_vXX_<YYYYMMDD-HHMM>.mp4` kèm cập nhật bảng lịch sử `_LICH_SU_PHIEN_BAN.md` (ghi rõ từng bản sửa lúc mấy giờ, thời lượng, dung lượng, ghi chú thay đổi) và bảng tổng hợp `_BANG_THEO_DOI_PHIEN_BAN.md`.

### 2. Lệnh CLI Độc Lập (Khi muốn đẩy hoặc tra cứu phiên bản video ngoài luồng)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_