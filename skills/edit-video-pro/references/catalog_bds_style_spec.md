# Kho tham chiếu edit-video-pro (tách từ SKILL.md 10/11/2026 để SKILL.md ≤ 21KB)

### 1.3. Bộ 4 Chế Độ Animation Bất Động Sản 3D & Kho Phong Cách V3.7 (`PA1..PA5`, `G1..C9+F0`, `O1..O6`)
- **4 Chế Độ Animation BĐS 3D (`scripts/`):**
  1. **`edit pro vòng cung` / `vòng cung map` (`M12`):** `scripts/bds_vong_cung_3d_engine.py` (Vệ tinh 3D Vòng Cung Giao Thông & Phễu Tọa Độ + Màn đen giới thiệu `4.5s`).
  2. **`edit pro bản đồ orbit` / `đường vàng bản đồ` (`M13`):** `scripts/bds_orbit_3d_engine.py` & `scripts/verify_m13.py` (Tô Sông/Sân bay + Đường vàng + Orbit Tòa tháp 3D + Flycam khoanh lô).
  3. **`edit pro google earth` / `zoom vũ trụ bđs`:** `scripts/bds_earth_zoom_engine.py` (Phễu vệ tinh Google Earth 3D xuyên mây xuống tâm dự án).
  4. **`edit pro flycam 3d` / `3d với flycam`:** `scripts/bds_flycam_3d_tracking_engine.py` & `scripts/verify_flycam_3d_gates.py` (Lưới tòa tháp 3D bám Flycam thật `< 2.0px`).
- **Kho 5 Hook (`PA1..PA5`), 9+1 Style Ngành (`content_style_router.py`) & 6 Kết Bài CTA (`outro_vault.py` V3.8):**
  * **Hook:** `PA1` (Editorial Frameless), `PA2` (Top Glass Card), `PA3` (Paper Header), `PA4` (Lower-Third Kinetic Badge), `PA5` (Split Headline Banner).
  * **Style (`--palette`):** `tech_blueprint_hud`, `bio_dermal_atlas`, `arch_wealth_matrix`, `ledger_trust_doc`, `culinary_warm`, `edu_grid_mindmap`, `botanic_organic`, `retail_bold_tag`, `kinetic_sport`, `finpath_dark_highlight`.
  * **Outro (`CTA Outro` V3.9):** `O4_split_glass_card` (Mặc định: rõ mặt diễn giả ở nửa trên + Thẻ kính CTA 4 tầng gồm Huy hiệu Monogram + Tên thương hiệu + Định vị + Tiêu đề `FD Tiempos Fine Italic` + 2 ý cốt lõi + Nút bấm `CTA Pill Button` kèm mũi tên `→`), `O2_editorial_digest`, `O1_executive_seal`, `O3_blueprint_grid`, `O5_action_roadmap`, `O6_minimal_quote_sig`. Nếu người dùng không nhập tên thương hiệu hay câu CTA, AI và `outro_vault.py` tự động suy luận & quyết định tên thương hiệu + câu nút CTA sát chủ đề bài nói (0% chữ hệ thống cũ).
- **Kho Phong Cách `VLOG TỰ SỰ` (`scripts/vlog_tusu_engine.py` — Cho Vlog đời thường đã cắt cảnh sẵn):**
  * **3 Tổ hợp Phong Cách (`--style`):**
    1. `nhat_ky` — **Nhật Ký Đời Thường** (`V2 + T3`, Mặc định ⭐): Chữ viết tay hiện nét bút ở đầu + Chữ ký viết tay & lời nhắn thân tình ở cuối.
    2. `dien_anh` — **Điện Ảnh Tinh Khôi** (`V1 + T1`): Chữ Serif nghiêng dưới ngực + Thông tin cá nhân trong suốt không khung hộp.
    3. `lua_moc` — **Lụa Mộc Thanh Lịch** (`V3 + T2`): Thẻ giấy kem lụa mờ ở đầu + Danh thiếp kính mờ màu trà rêu trầm ở cuối.
  * **3 Style Khung Đầu (`--head-style`):** `V1` (*Điện Ảnh Tối Giản*) · `V2` (*Nhật Ký Viết Tay*) · `V3` (*Nhãn Giấy Lụa Mộc*).
  * **3 Style Khung Cuối CTA Cá Nhân (`--tail-style` — 0% nhắc BĐS/bán hàng, chỉ Cá nhân + Điện thoại + Facebook):** `T1` (*Trong Suốt Tinh Khôi*) · `T2` (*Danh Thiếp Lụa Mờ*) · `T3` (*Chữ Ký Cuối Trang*).
  * **Chuẩn chuyển cảnh & âm thanh Vlog:** Giữ nguyên 100% nhát cắt gốc trong thân bài, đặt 1 cú Hòa cảnh mềm `0.40s` (`C2 Cross-Dissolve`) khi sang cảnh cuối, kéo giãn mượt đoạn kết bằng Optical Flow (`+2.6s`), tách giọng AI `Open-Unmix HQ` + hạ nhạc nền `-18.5 dB` dưới giọng đọc, kiểm định 8 cổng `VL1..VL8`.

## 0B & 0C. CHUẨN DỰNG V3.5 (42 CỔNG) & CHỈ MỤC NÂNG CẤP NHANH FULL STUDIO V3.2
> Chi tiết đầy đủ 6 trụ cột V3.5 (`perform_roughcut_on_aroll`, `OpticalArollFramer`, B-Roll `broll_clip` 9:16, Poster `<= 20` âm tiết `4.5–5.0s`, Style `C10 · Báo Đen Bôi Sáng` `--palette finpath_dark`, 42 cổng `edit_video_pro_verifier.py`) xem tại [`references/v3_spec_and_upgrade_index.md`](file://[đường-dẫn-Mac]).
- **Chỉ mục nâng cấp nhanh ("Muốn sửa X -> Mở đúng 1 file Y", cấm đọc tràn lan):**
  1. Thông số Màn đen chữ (`MOI, AEO, TIEMPO`), Y, trễ `+0.358s`, ngưỡng 2 Cam, dB `4-Diamond`, Hook/Outro: `presets/dualcam_viet_style.json`.
  2. Thuật toán 2 Cam vs B-Roll (`Multi-Window FFT`), Màn đen chữ, Nhạc `4-Diamond`, CapCut 2 Chế độ: `scripts/dualcam_v3_upgrade.py`.
  3. Tăng tốc Full Studio (`fastcopy` APFS `cp -c`, Skeleton `~18KB`, Hash Cache, 2-Worker): `scripts/studio_accelerator.py`.
  4. Điều phối 2 Cam & Kết xuất biến thể Studio: `scripts/dualcam_engine.py`.


## Nguyên Lý Gốc V4.1 (bản đầy đủ)

> **Nguyên Lý Gốc V4.1 (`smart_guards.py` — Giúp cả Gemini 3.8 Flash trên máy khách đạt chuẩn Gemini 4):** Engine tự động xử lý tất định 100% các bài toán đo đếm được: (1) Rough-cut `A1..A6` bắt cả câu nói lại nguyên câu khác chữ, vấp âm học `<200ms`, bảo vệ mệnh đề Nhân-Quả (`A3`) & bảo toàn cặp liệt kê `"Thứ nhất / Thứ hai"` (`A6`); (2) Quét giơ sổ/đọc kịch bản `V1` (kèm cầu dao `G1_DETECTOR_SANITY <= 20%` chống báo nhầm tường sáng) để xuất `must_cover_spans` cho cảnh trám tự che; (3) Ngắt dòng Quy Hoạch Động `COMPOUND_SAFE_WRAP_ALL` + `SUB_ORPHAN` bảo vệ `>110` từ ghép tiếng Việt đa ngành và triệt tiêu từ mồ côi 1 chữ trên mọi lớp chữ; (4) Khóa `G7_DESC_GROUNDED` & `P3_POSTER_NO_REPEAT` chống bịa số `%` và chống lặp ý giữa các thẻ.