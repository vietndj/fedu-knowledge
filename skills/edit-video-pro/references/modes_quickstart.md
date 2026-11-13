# Chi tiết Chế độ 2 Cam, Vlog Tự Sự & 6 Luật Curation B-Roll (`R1..R6`)

## 1. Chế độ 2 Cam (`dualcam_engine.py` · V3.9)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- **Chặng 1:** Tự động tách `Cam A` (Master Audio), `Cam Z` (Góc 2 tắt tiếng) & `Local B-Roll` bằng `Multi-Window FFT Lag Consistency >= 3/4 cửa sổ ±5ms`; giữ 100% màu gốc `bt709` (`REC709_SDR`/`HDR_HLG_PQ`/`CAMERA_LOG`, tắt LUT CapCut), cắt câu lặp/meta-talk, khóa mắt `(621px, 640px)`.
- **Chặng 2:** Đầu video có `Hero Hook PA1`, phụ đề 2 tầng hộp đen mờ Vàng Kim (`FD Orbikular` + `FD Tiempos Fine Italic`), giữa bài đặt Màn hình đen chữ tóm tắt 2 tầng (`Retrospective Sharp Summary` `1.291s`, đổi góc qua màn đen, `Gate 10 Anti-Parrot` & `Gate 8A` `t1_size >= 15.0`) + Nhạc `4-Diamond` (`-20dB -> 0dB -> 0dB -> -20dB`), và **khung hình cuối BẮT BUỘC là Màn hình `CTA Outro` V3.9** (Huy hiệu Monogram + Tên thương hiệu + Định vị + Nút bấm viên thuốc `CTA Pill Button`).
- **Luật tự quyết định thương hiệu & CTA:** Nếu người dùng không cung cấp tên thương hiệu / câu CTA, tự đọc bối cảnh thư mục & lời thoại để quyết định `--brand-name`, `--brand-tagline` và `--cta-text` sát chủ đề (bài giảng K4/FEDU của anh Việt → `"NGUYỄN VIỆT · FEDU"` · học viên K4 → tên thương hiệu học viên).

## 2. Chế độ `VLOG TỰ SỰ` (`vlog`)
Dành cho Vlog cá nhân/đời thường đã tự cắt cảnh sẵn `>= 8` cảnh montage, không chèn thẻ Bento khoa học, chỉ thêm chữ đầu nhẹ nhàng + tách hạ nhạc nền `-18.5 dB` + 1 cú hòa cảnh mềm cuối `0.40s` + CTA cá nhân giản dị `SĐT + Facebook`:
- **3 Tổ hợp Phong Cách (`--style`):** `nhat_ky` (**Nhật Ký Đời Thường** = `V2 + T3`, mặc định ⭐) · `dien_anh` (**Điện Ảnh Tinh Khôi** = `V1 + T1`) · `lua_moc` (**Lụa Mộc Thanh Lịch** = `V3 + T2`).
- **3 Style Khung Đầu (`--head-style`):** `V1` (**Điện Ảnh Tối Giản**) · `V2` (**Nhật Ký Viết Tay** ⭐) · `V3` (**Nhãn Giấy Lụa Mộc**).
- **3 Style Khung Cuối (`--tail-style`, 0% bán hàng/BĐS):** `T1` (**Trong Suốt Tinh Khôi**) · `T2` (**Danh Thiếp Lụa Mờ**) · `T3` (**Chữ Ký Cuối Trang** ⭐).
- **Lệnh chạy (`--preview-6` nếu cần duyệt 6 ảnh trước):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

## 3. Chi tiết 6 Luật Curation Chuỗi B-Roll (`R1..R6`)
Tạo `<WORK_DIR>/sequence_curation.json` có mảng `"takes"` giữ thứ tự `T01..Tnn` (`take`, `see`, `angle_id`, `scale` `["ECU","CU","MS","OTS","WS"]`, `action`, `prev_link`, `phase_in` `1..5`, `phase_out` `1..5`, `decision`, `defect`, `trim_window`, `seam_to_next`):
- **R1 (Đổi Góc / Đổi Cỡ Cảnh / Tiền Cảnh = `"KEEP"`):** Hướng nhìn mới (`OTS`, qua cửa/tán cây) hoặc đổi `WS <-> MS <-> CU <-> ECU` → cấp `angle_id`/`scale` mới, `"decision": "KEEP"`.
- **R2 (Loại Bản Quay Lại Lỗi — `"DROP_RETAKE_OF_Txx"`):** Hai take liền kề (`<= 3` takes, `retake_cand_of`) cùng góc & cỡ cảnh → giữ 1 bản sạch (`"KEEP"`), bản lỗi đánh `"DROP_RETAKE_OF_Txx"` kèm `"defect"` (`"STRANGER"` khi `bg_intruder_hint: true`, hoặc `"EXIT_EARLY"` / `"FLUB"` / `"SHAKE"` / `"DUP_ACTION"`).
- **R3 (Nối Sát Động Tác `Seam Handover Lx-Fy` — CẤM LẶP 2 LẦN):** Các take khác góc nối tiếp 1 hành động → `"KEEP"` tất cả, chọn `"seam_to_next": "Lx-Fy"` (từ `seam_candidates`) để cảnh sau vào sát phần cuối động tác cảnh trước, `phase_in`/`phase_out` tăng đơn điệu (`1->2->3..5`).
- **R4 (Mắt Xích Nhân Quả & Sự Kiện UI = `"KEEP"`):** Cảnh màn hình phản hồi thao tác → `"prev_link": "CAUSE_EFFECT_OF_Txx"`, `"decision": "KEEP"`, giữ `suggested_window_s` (cấm `DROP_UNUSABLE`).
- **R5 (Chốt Rời Khung `exit_t`):** Nếu `exit_t != null` → `trim_window[1] <= exit_t + 0.10`.
- **R6 (Ưu Tiên Chân Máy Đứng Yên):** Luôn ưu tiên `suggested_window_s`.