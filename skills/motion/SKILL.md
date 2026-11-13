---
name: motion
description: "Mantra: MOTION / MOTION CORE / MOTION V8 / MOTION MAU / MOTION MOI / MOTION SUA / MOTION CHECK / MOTION 60 / MAU 01..03 MOTION GRAPHIC (Paage 70s, Adwave 61s, Higgsfield 45s). Động Cơ Vật Lý 12 Nguyên Lý & Micro-12P Silk Editorial V8.3 Toàn Hệ Sinh Thái (tự động cấp phát cho mọi kỹ năng làm Video & Animation Python/Remotion) + 3 Template 30fps Đa Tỷ Lệ (16:9 & 9:16) & kiểm định T0..T3."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `motion` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).

> Tài liệu kèm: `references/LEGACY_60FPS.md`, `references/architecture_8.md`, `references/before-after-video.md`, `references/examples_and_catalog.md`, `references/so-do-motion.md`, `references/templates_3.md`


# KỸ NĂNG MOTION V8.3 — ĐỘNG CƠ MICRO-12P SILK EDITORIAL & 12 NGUYÊN LÝ TOÀN HỆ SINH THÁI (`MAU 01..03`)

## 0. LÕI VẬT LÝ CHUNG TOÀN HỆ SINH THÁI (`MOTION CORE V8.3` — MICRO-12P CHO CHỮ ĐỌC vs SHOWCASE)
- **Nguồn sự thật duy nhất (Single Source of Truth):**
  - Token vật lý `v8.3.0` & 7 Hồ sơ thể loại chia làm **2 Chế Độ Kiểm Toán (`audit_mode`)**:
    + **`reading_editorial`** (`spa_atelier`, `talking_head`, `before_after`): **Micro-12P Silk Editorial** — đủ 12 nguyên lý ở liều thấp sang trọng, chữ đọc khóa `scale = 1.000` sắc nét tuyệt đối.
    + **`kinetic_showcase`** (`ad_showcase`, `explainer_diagram`, `real_estate_3d`, `hook_transition`): Bung năng lượng 12 Nguyên Lý kiểm soát bảo toàn diện tích `sx * sy = 1`.
    + File gốc: [`core/motion_tokens.json`](file://[đường-dẫn-Mac])
  - Động cơ Python V8.3 + Multi-Pass Clean Sprite Rig (`surface_sheet_rgba` + `text_layer_rgba` + `accent_layer_rgba`, `0%` bóng ma): [`core/motion_core.py`](file://[đường-dẫn-Mac])
  - Bộ đồng bộ tự động sang Remotion (`motionTokens.ts` / `motionPhysics12P.ts`) & vendoring khóa SHA-256 (`_vendor/motion_core.py`) cho 12 đích Python: `python3 [đường-dẫn-Mac]`
  - Sổ cái tự học hợp nhất toàn hệ thống: [`self_learning_ledger.jsonl`](file://[đường-dẫn-Mac])
- **Luật Ranh Giới Cứng V8.3 (`MICRO-12P SILK EDITORIAL` vs `ACCENT` vs `KINETIC`):**
  1. **Tách Lớp Sạch Từ Renderer cho Thẻ Đọc (`editorialSurface` + `editorialText`):**
     - **Nền A-Roll (`Anticipation & Staging`):** Làm dịu `0 -> 8%` trong `3f` trước khi thẻ xuất hiện, trả về trong `4f` khi thoát.
     - **Tấm nền thẻ (`editorialSurface`):** Spring từ trạng thái đứng yên (`zeta = 0.82, omega = 13.0`, frame 1 chỉ đi `~8.1%` tạo Slow-In mượt như nhung, tránh cú giật `42%` của `quintic_out`), `ΔY = +26px -> 0`, `scale = 0.985 -> 1.000` (không vượt), bóng đổ độ sâu (`Solid Drawing`), thoát `8f` (`+2px` lấy đà 2f đầu -> `-18px` `cubic_in` 6f sau).
     - **Lớp chữ đọc (`editorialText` / `READ`):** **Khóa cứng `scale = 1.000`** (`0%` nhòe/lấp lánh do lấy mẫu lại, `0°` xoay/skew), đi trễ **`+40ms`** sau tấm nền thẻ (`ΔY = +16px -> 0`) tạo Follow-Through mềm mại, khóa tĩnh `<= 0.48s`; chỉ đổi sang `static_sheet_rgba` khi `max_abs_diff <= 2/255`.
     - **Bỏ Sheen trên Poster đọc** (chỉ giữ Sheen trên nút CTA Outro); đường tiến độ vẽ dần `0 -> 100%` trong `0.48s` sau `+0.15s` (`Secondary Action`).
  2. **`editorialBadge` & `editorialPill` (Tách trên `accent_layer_rgba` trong suốt, `0%` bóng ma):**
     - **Huy hiệu `01/02/03` (`editorialBadge`):** Trễ `+2f (+67ms)`, spring `zeta = 0.50, omega = 18.0`, `scale 0.85 -> 1.024 -> 1.000`, `2%` Squash & Stretch bảo toàn diện tích (`sx * sy = 1`) trong `0.12s` đầu, vào theo cung cong nhẹ `Arc (+6, +14)px`.
     - **Pill nhãn (`editorialPill`):** Trễ `+3f (+100ms)`, spring `zeta = 0.70, omega = 15.0`, trượt ngang `ΔX = -10px -> 0`, `scale = 1.000`.
  3. **`HERO` (Đại tự ngắn $\le 3$ từ ở Hook mở đầu) & `KINETIC` (Thẻ UI quảng cáo `Mau01..03`, Sơ đồ động không chứa đoạn văn dài):**
     - `HERO` tiết chế sang trọng (`stretch <= 4.5%`, `skew <= 1.2°`, khóa phẳng `0%` méo ngay khi vào pha HOLD); `KINETIC` áp đủ 4 nhịp 12 Nguyên Lý (`Anticipation -> Spring Overshoot -> Hold -> Exit 9f`).
  4. **Tự động hậu kiểm cảnh báo Đa Chế Độ (`Advisory Warn`):** Mọi video xuất ra đều tự chạy [`motion_audit.py`](file://[đường-dẫn-Mac]) `--mode warn` (tự chọn thang `reading_editorial` hoặc `kinetic_showcase` + khoanh đúng `Per-Segment ROI` tách mặt người nói ở Split-Top Poster). Đặt `FEDU_MOTION_V8=0` nếu cần quay lui chế độ tĩnh cũ.

---

## 1. BA LUẬT VÀNG, BẢNG 3 TEMPLATE & QUY TẮC ĐỊNH TUYẾN TỶ LỆ

### Ba Luật Vàng Tối Thượng (Thứ tự ưu tiên: `LIEN MACH > DE DOC > STAGING > VAT LY`)
1. **`MOT CANH – MOT VAT CHINH`:** Mỗi lúc chỉ 1 vật chuyển động chính; vật khác đứng yên/dịu xuống. Ưu tiên tuyệt đối Màn Hình Điểm Chính Dừng Nhạc `1.60s` `<ZeroNoisePillarScreen30 />` thay vì xếp chữ tiêu đề lớn cạnh video đang chạy.
2. **`LUN TRUOC – BAT SAU – NGHI DE DOC – LAY DA VUT THOAT`:** Vào có lấy đà $\rightarrow$ Bật dứt khoát $\rightarrow$ Khóa tĩnh đọc chữ $\rightarrow$ Trước khi chữ/cảnh sau vào, chữ/cảnh trước bắt buộc có pha OUT 9 frames (`3f` lấy đà + `6f` tăng tốc bậc ba vút thoát).
3. **`KHONG DE CHU – KHONG CAT MAT BROLL – KHONG ZOOM CAN MAT HOC VIEN – KHONG LECH CON TRO`:** Dùng `<FlexRelayRow30>` chống đè chữ 100%, dùng khung vuông `cardAspect <= 1.45` hoặc `<MultiSquareBrollStrip30 />` kết hợp `broll_crop_manifest.json` bảo toàn khuôn mặt & cắt sạch trần nhà/biển EXIT, **`0%` zoom cận mặt học viên (`safeScale = 1.0`, giữ khung nhỏ đủ tỷ lệ, chọn frame mắt mở tươi tắn)**, đặt `<HandCursor30 />` ở Root Stage và neo tọa độ bằng `anchorToRect30` ngoài khuôn mặt.

### Hệ Thống 3 Template Đóng Gói (`templates/registry.json` & `scripts/render_template.py`)
- **`mau01` (Paage `70s`):** `Mau01Paage30fps` (`16:9`) / `Mau01Paage9x16-30fps` (`9:16`), `kb1`/`kb2`.
- **`mau02` (Adwave `61.2s`):** `AdwaveShowcase61s-30fps` (`16:9`) / `AdwaveShowcase61s9x16-30fps` (`9:16`).
- **`mau03` (Higgsfield `44.8s`):** `Mau02Higgsfield30fps` (`16:9`) / `Mau02Higgsfield9x16-30fps` (`9:16`), mặc định `kb2`.
- **Lệnh CLI điều phối:** `python3 [đường-dẫn-Mac] --template [mau01|mau02|mau03] --aspect [16:9|9:16|both] --variant [kb1|kb2]`
- **Định tuyến tỷ lệ tự động:** Không nói tỷ lệ $\rightarrow$ mặc định **`16:9` (`1920×1080`)**; có từ `"dọc"` / `"9:16"` / `"TikTok"` / `"Reels"` $\rightarrow$ **`9:16` (`1080×1920`)**; nói `"cả hai"` $\rightarrow$ **`both`**.
- **Chi tiết bảng 3 Template & 8 Lệnh Gọi (`MOTION MAU`, `MOTION MOI`, `MOTION SUA`, `MOTION CHECK`, `MOTION 60`):** Đọc [`references/templates_3.md`](file://[đường-dẫn-Mac]) (pipeline 60fps cũ xem [`references/LEGACY_60FPS.md`](file://[đường-dẫn-Mac])).

---

## 2. CHECKLIST 8 CHUẨN KIẾN TRÚC BẮT BUỘC CỦA MOTION ENGINE V7.1
*(Chi tiết kỹ thuật từng chuẩn xem tại [`references/architecture_8.md`](file://[đường-dẫn-Mac]) — bắt buộc đọc khi viết mới hoặc sửa component `.tsx`):*
1. **Ma Trận Biến Dạng 4 Cấp (`KineticDeformClass30`):** `KINETIC_READABLE_30` (chữ $\ge 3$ từ: `0%` méo, `0°` skew), `KINETIC_HERO_30` ($\le 2.5\%$), `KINETIC_RIGID_30` (B-Roll/mặt người/UI: `0%` méo), `ELASTIC` (nút/con trỏ: `6%–14%`).
2. **Pha OUT 9 Frames (`exitCurve30` + `<SceneExitWrapper30 />`):** `3f` lấy đà ngược (`-12%`) + `6f` gia tốc bậc ba vút thoát (Gate B9).
3. **Hàng Chữ Tiếp Sức (`<FlexRelayRow30 />`):** Cấm `position: 'absolute'` cho $\ge 2$ cụm chữ cùng hàng và cấm `marginLeft <= -15px` (Gate B8).
4. **Giàn Camera 3D Thật (`<Camera3DRig30 />`):** Cấm xoay phẳng 2D giả 3D; cấm đặt `overflow: 'hidden'`/`filter`/`opacity < 1` trực tiếp trên node `preserve-3d` (Gate B10).
5. **Con Trỏ 4 Pha Ở Root Stage (`<HandCursor30 />` + `anchorToRect30`):** Đặt trực tiếp dưới `<AbsoluteFill>`, chạm tâm nút `\Delta \le 18\text{px}`, cấm đè mặt B-Roll (Gate B19).
6. **Khung B-Roll Vuông & `0%` Zoom Mặt Học Viên (`cardAspect <= 1.45` + `<MultiSquareBrollStrip30 />`):** Vùng ngang rộng `w/h > 1.45` bắt buộc chia 2–3 ô vuông; khóa `safeScale = 1.0` cho học viên dọc (`R_B20d`); tự cắt biển `EXIT`/trần nhà qua `broll_crop_manifest.json` (Gate B20).
7. **Dừng Nhạc `1.60s` (`48f`) Mở `<ZeroNoisePillarScreen30 />` (`R_B12c`):** Cấu trúc 3 Nội Dung Chính ($\le 10$ tiếng/dòng) + kết bài `<PillarSummaryBoard30 />` (Gate B12..B18).
8. **Phân Tầng Cơ Học Nhún (`L0..L3` — Gate B17):** `L0` (`0%` nhún cho Container lớn), `L1` (`overshoot <= 2%`), `L2` (`pressPx: 3`), `L3` (`pressPx: 7` tối đa 3 nút CTA).

---

## 3. CHU TRÌNH KIỂM ĐỊNH 4 MỐC (`T0 -> T1 -> T2 -> T3`) & GIAO HÀNG TELEGRAM TỰ ĐỘNG

1. **Mốc `T0` (`Asset Ingest` — khi thêm/cập nhật B-Roll):**
   `python3 [đường-dẫn-Mac]`
2. **Mốc `T1` (`Pre-Flight` — trước khi code):** Đọc dòng cuối [`scripts/self_learning_ledger.jsonl`](file://[đường-dẫn-Mac]) và xác lập 3 Điểm Chính + mốc dừng nhạc.
3. **Mốc `T2` (`Pre-Render AST Gatekeeper < 0.3s` — BẮT BUỘC chạy trước `npx remotion render`):**
   `python3 [đường-dẫn-Mac] --tsx "<thư_mục_template>"` (Phải đạt `overall=PASS` mới được render).
4. **Mốc `T3` (`Post-Render Pixel & Blueprint Audit` — ngay sau khi xuất `.mp4`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
   Kiểm tra ảnh Bản Thiết Kế 12 Nhịp `/tmp/qa_layout_blueprint_<stem>.jpg`, ghi vào `self_learning_ledger.jsonl`, và **MẶC ĐỊNH 100% TỰ ĐỘNG GỬI VIDEO KẾT QUẢ VÀO TELEGRAM** (`telegram_notify.py`). *(Lưu ý: `check_motion.py` FAIL lần thứ 2 trên cùng scene $\rightarrow$ bắt buộc giao subagent `motion-debugger`).*


---
## 🛰️ Nhánh Kỹ Năng Hợp Nhất (Giữ Nguyên Đường Dẫn Scripts)

| Mantra / Tác vụ | Tài liệu chi tiết (chỉ đọc khi gọi đúng nhánh) | Thư mục Scripts gốc (không đổi) |
|---|---|---|
| **VIDEO TRUOC SAU / SIDE BY SIDE** — Tạo Video So Sánh Trước–Sau 1080x1920 (10 Nền, 35 Chữ, 6 Khuôn Motion) | [`references/before-after-video.md`](file://[đường-dẫn-Mac]) | `[đường-dẫn-Mac]` |
| **SO DO MOTION** — Tạo Video Sơ Đồ Chuyển Động 60fps 1080x1920 kèm Phụ đề 5B, SFX & Lồng tiếng | [`references/so-do-motion.md`](file://[đường-dẫn-Mac]) | `[đường-dẫn-Mac]` |
