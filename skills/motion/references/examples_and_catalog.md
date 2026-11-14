# motion — Thư viện 10 Archetypes, Luật Vật Lý Chuyển Động V3 & Chi Tiết 6 Khuôn .TSX

> Tài liệu tham chiếu chuẩn hóa cho `SKILL.md` (Đã nâng cấp lên chuẩn **2.5D Spatial Camera Engine V3** theo chẩn đoán của **CLAUDE2 Opus 5.5** — Xóa bỏ hoàn toàn công thức `Math.sin` camera cũ).

---

### 2.2. Phương Án Về Bố Cục UI/UX (5 Quy Luật Attention Budgeting — Chuẩn Motion 05 & 06)
Khắc phục triệt để căn bệnh "tham chi tiết / quá tải thông tin / đè lớp chữ":
1. **Single Focal Point (1 Tiêu Điểm Duy Nhất):** Tại bất kỳ frame nào, mắt người xem chỉ được phép nhìn vào **1 cụm tiêu điểm duy nhất** ở tâm thị giác.
2. **$\ge 85\%$ Negative Space (Không Gian Thở Tối Đa):** Giữ tối thiểu 85% diện tích khung hình là nền sạch (`#042016` Deep Emerald, `#07080A` Obsidian, `#F4FCE3` Mint Cream, `#F5F2EB` Ivory hoặc `#F3ECDD` Risograph).
3. **Zero Redundant HUD (0% Rác Giao Diện):** **CẤM** đặt Header cố định, thanh Subtitle chạy song song ở đáy, Timecode giả hay nhãn `SEMANTIC_CORE` lặp lại chữ đang có ở giữa màn hình.
4. **Self-Cleaning Pre-Cue (Mồi Cảnh Tự Thu Dọn):** Hạt mồi dẫn mắt xuất hiện trước điểm cắt `10–14 frames`, nhưng **phải tự thu nhỏ/biến mất hoặc đậu gọn vào góc trang trí ngay khi chữ chính bung ra** (cấm đè lên dòng chữ đầu tiên của cảnh mới).
5. **Clean Stage Separation & Full-Bleed Geometry:**
   - Mỗi cảnh mới phải dọn sạch cảnh cũ thông qua **1 diễn viên chung (Shared Actor Relay)** hoặc **cửa chéo SVG `<polygon>` tọa độ đỉnh thật** phủ kín 100% 4 góc `(0,0) → (1080,1920)` (tuyệt đối không dùng `div` xoay góc gây hở mép trái).
   - Phân tầng `zIndex` nghiêm ngặt: Nền (`zIndex: 1`) $\rightarrow$ Viên thuốc/Hộp trang trí (`zIndex: 10`) $\rightarrow$ Chữ Hero chính (`zIndex: 30`) $\rightarrow$ Diễn viên dẫn mắt (`zIndex: 60`).

---

### 2.3. Phương Án Về Vật Lý Chuyển Động & Quỹ Đạo Camera 2.5D (`spatialCameraEngine.ts`)
1. **Cấm Tuyệt Đối `Math.sin(frame...)` Trên Camera & Blur:**
   - **LỖI CŨ ĐÃ BỊ XÓA BỎ:** Trước đây việc dùng `1 + 0.008 * Math.sin(frame / 28)` làm camera nhấp nhô tại chỗ lặp đi lặp lại 19 chu kỳ.
   - **CHUẨN MỚI BẮT BUỘC:** Mọi camera phải nội suy qua mảng `Waypoint[]` bằng `computeSpatialCamera(frame, track, PROFILES[style], fps)` trong `src/components/motion/spatialCameraEngine.ts`.
2. **Đồ Thị Vận Tốc 2 Pha (Two-Phase Speed Graph):**
   - **Pha 1 — Snap Impulse (`10–18 frames`):** Đi `82%` quãng đường bằng `Easing.bezier(0.16, 1, 0.3, 1)` hoặc `spring({ damping: 14, stiffness: 190 })`.
   - **Pha 2 — Continuous Micro-Drift:** Trôi tuyến tính `18%` quãng đường còn lại về hướng waypoint kế tiếp.
3. **Diễn Xuất So Le 4 Tầng (Staggered Choreography):**
   - Tầng 1 (`f0 → f28`): Cửa chéo SVG `<polygon>` hoặc Background Wipe mở khung hình.
   - Tầng 2 (`f18 → f34`): Cụm từ khóa Hero bung từng từ qua hộp mặt nạ 3D (`overflow: 'hidden'`, `paddingTop/Bottom: '0.14em'` giữ nguyên dấu tiếng Việt `Ấ, Ể, Ữ, Ộ`).
   - Tầng 3 (`f28 → f45`): Viên thuốc phụ / Thẻ số liệu trượt vào khóa lò xo.
   - Tầng 4 (`endFrame - 12f`): Diễn viên dẫn mắt (`GuideFlower`, `Caret`, `Pipe`, `Iris`) khởi động dẫn sang cảnh kế tiếp.
4. **True Velocity-Derived Motion Blur (`blur = 0px` trong `READ_WINDOWS`):**
   - Tính bán kính blur từ đạo hàm vận tốc thật `velocityBlur(frame, track, profile)` giữa frame $f$ và $f-1$.
   - Trong toàn bộ `readWindows` (lúc người xem đọc chữ hoặc bảng số liệu Bento), **`blur` bắt buộc bằng `0px` tuyệt đối** (`Laplacian.var() >= 120`, mục tiêu `>= 150`).

---

### 3. Chi Tiết 6 Khuôn Thiết Kế Gốc (`.TSX`) & Cách Thay Thế `Math.sin` Cũ Bằng Engine Mới

1. **Khuôn #1 — `VietCleanV3_10s.tsx` (`PROFILES.cleanV3` • Chuẩn Motion 05 Ultra-Clean):**
   - **Phù hợp nhất cho:** Video Hook tư duy, giải thích khái niệm sắc bén, đối lập Cũ vs Mới.
   - **Chuẩn hóa Camera V3:** Bỏ `breathScale = 1 + Math.sin(...)` và blur cố định theo frame. Dùng `PROFILES.cleanV3` (push-in nhẹ `z: 0 → 0.04`, `rz = 0°` giữ chữ thẳng tuyệt đối, whip-pan ngang `Δx = 28%` trong `8 frames` khi chuyển stage).
2. **Khuôn #2 — `VietClaudeMotionRiso10s.tsx` (`PROFILES.riso` • Chuẩn Motion 03 Hybrid Risograph):**
   - **Phù hợp nhất cho:** Video chuyên gia nói chuyện cần giữ gương mặt thật của anh Việt đan xen đồ họa Editorial Risograph ấm áp.
   - **Chuẩn hóa Camera V3:** Tách **2 Rig độc lập**:
     - *Rig Mặt người thật:* Chỉ push-in tuyến tính `1.00 → 1.035`, tuyệt đối không lắc.
     - *Rig Đồ họa Risograph:* Dùng `PROFILES.riso` (`spring damping: 18, stiffness: 140`, lia ngang `±5%` như lật trang tạp chí). Bỏ `jitterX = sin(...)`, thay bằng lệch khuôn in đứng yên theo bậc 4 frames: `random('riso-' + Math.floor(frame / 4)) * 0.6`.
3. **Khuôn #3 — `PinterestViet9x16.tsx` (`PROFILES.pinterest` • Editorial Kinetic 2.5D Matt Loui) & `VietBrandPinterestGold.tsx` (`PROFILES.gold` • 3D Bento Gold):**
   - **Phù hợp nhất cho:** Video giải thích triết lý xây kênh (`kenh.fedu.vn`), hệ sinh thái công cụ, Bento Dashboard 3D, dải lụa SVG `<textPath>` và chuyển cảnh đa tầng.
   - **Chuẩn hóa Camera V3:** Nội suy 9 phân cảnh qua `PROFILES.pinterest` (`Snap 82% + Drift 18%`), nghiêng 3D `rx = 8°, rz = -2.2°` tại Bento Dashboard với `readWindows: [[745, 920]]` giữ độ nét `Laplacian = 215.7` (`0px` blur). Với `Gold`, thay `blobPulse` hàm sin bằng xung tắt dần khớp điểm nổ SFX: `Math.exp(-(frame - cueFrame) / 10)`.
4. **Khuôn #4 — `VietMasterClassPower10s.tsx` (`PROFILES.masterclass` • Acid-Lime Brutalist Kinetic Text):**
   - **Phù hợp nhất cho:** Video vị thế chuyên gia / quyền lực mềm theo phong cách trailer MasterClass trên nền Acid Chartreuse `#E0EE70`.
   - **Chuẩn hóa Camera V3:** Dùng `PROFILES.masterclass` (`move: 'step'`, `spring damping: 26, stiffness: 320`, `drift: 0.06`, `rot = 0°` tuyệt đối). Camera đi như **nước cờ vua** theo bội số lưới `11%`, kết hợp cột trụ đen làm diễn viên chung quét sạch màn hình.
5. **Khuôn #5 — `VietScientificAtlas.tsx` (`PROFILES.atlas` • Scientific Atlas Motion V4 Full-Canvas `1080x1920`):**
   - **Phù hợp nhất cho:** Video giải thích cơ chế khoa học, y khoa, da liễu, nha khoa trên nền giấy `#F5F2EB`.
   - **Chuẩn hóa Camera V3:** Camera `PROFILES.atlas` (`move: 'glide'`, `blur = 0px` toàn thời gian) **chỉ tác động lên khung mô học (`Y=250..960`)**, dịch tâm mượt về tọa độ `(nx, ny)` của Callout đang sáng. Header, Callout và Voice Card khóa tĩnh. Sóng âm 5 cột lấy từ biên độ thật của `voice.wav` (không dùng hàm sin).
6. **Khuôn #6 — `VietSuiPlayLaunch20s.tsx` (`PROFILES.suiplay` • 3D Device Portal & Rapid Match-Cut):**
   - **Phù hợp nhất cho:** Trailer công nghệ tốc độ cao, xuyên tâm qua 14 lớp thiết bị 3D và cắt 16 khe video theo nhịp trống.
   - **Chuẩn hóa Camera V3:** Bỏ `1 + 0.006 * Math.sin(frame / 28)`. Dùng `PROFILES.suiplay` (`move: 'portal'` tăng tốc mũ vào tâm thiết bị, cắt đúng lúc vận tốc đạt đỉnh, cảnh kế tiếp vào bằng `snap 6–8f` cùng vận tốc để tạo cú Match-Cut liền mạch).
7. **Khuôn #7 — `PaageOffline0711_30fps.tsx` (`PAAGE_UI_SHOWCASE_70S` • Paage UI Showcase `70.37s`, `1920x1080 @ 30fps`):**
   - **Phù hợp nhất cho:** Video quảng cáo/giới thiệu Khóa học Offline, Dịch vụ Spa/Thẩm mỹ, Nha khoa, Phòng khám, SaaS hoặc Sản phẩm chủ lực cần dẫn dắt đầy đủ 11 chương (Hook 3 câu -> Đại tự Hero trên B-Roll -> Nhập nỗi đau khách hàng -> Kéo thả B-Roll thực chứng -> Giao diện Split-View + Popup 3 Đánh giá -> Quả cầu xử lý 3 bước + 3 Giải pháp -> 3 Khung B-Roll + Cam kết bảo hành -> Xuất Video & MacBook 3D -> Biên tập Trước/Sau + Chọn tệp khách mục tiêu -> Bộ đếm số liệu + 4 Nhóm khách hàng -> Đại tự Ngày/Thương hiệu + Click CTA).
   - **Tài liệu & Preset:** Xem [`templates/paage_ui_showcase_70s/TEMPLATE.md`](file://[đường-dẫn-Mac]), [`schema.json`](file://[đường-dẫn-Mac]) và script [`render_paage_template.py`](file://[đường-dẫn-Mac]).

---

### 4. Bảng 11 Archetypes Hiệu Ứng Tinh Tuyển (`pin_00` $\rightarrow$ `paage_11`)

| Mã Mẫu | Tên Cơ Chế Chuyển Động | Khi Nào Sử Dụng (Semantic Routing) | Nguồn Tham Chiếu (`motion00.html`) |
|---|---|---|---|
| **`pin_00`** | **Radial Orbit 12 Icons & Comet Trail** | Mở ra Kỷ nguyên mới, Hệ sinh thái đa công cụ, Tầm nhìn tổng quan | `#REF-01` (`PinterestViet9x16.tsx`) |
| **`pin_01`** | **Vertical Slot-Machine Wheel Picker & 3-Sphere Blend** | Phủ định danh xưng cũ (cuộn & gạch bỏ) hoặc Giao thoa 3 yếu tố | `#REF-02` (`pin_01_[số-tk].mp4`) |
| **`pin_02`** | **Radial Tick-Mark Dial & Cascading File Tree** | Giải thích thuật toán, Phân nhánh cấu trúc từ gốc đến ngọn | `#REF-03` (`pin_02_[số-tk].mp4`) |
| **`pin_03`** | **3D Glass Rolodex Stack & Isometric Grid Tilt** | Đóng gói quy trình, Xếp lớp thẻ kiến thức theo trục sâu Z | `#REF-04` (`pin_03_[số-tk].mp4`) |
| **`pin_04`** | **Backlit Aura, Cursor Typing & Hard Invert** | Câu Hook phá vỡ niềm tin cũ, Đảo nền Đen $\leftrightarrow$ Trắng/Đỏ trong 1 frame | `#REF-05` (`pin_04_[số-tk].mp4`) |
| **`pin_05`** | **Oblique Cylindrical Text Drum (`-8°`) & Mechanical Snap `0°`** | Vô hiệu hóa chỉ số ảo, Xoay trụ chữ tốc độ cao rồi khóa lẫy tại tâm | `#REF-06` (`pin_05_[số-tk].mp4`) |
| **`pin_06`** | **Frosted Glass Pill $\rightarrow$ 3D Growth Card & Rack Focus** | Chuyển hóa thành kết quả/doanh thu, Lấy nét tiêu cự hoàn tất trước khi đọc | `#REF-07` (`pin_06_[số-tk].mp4`) |
| **`pin_07`** | **Circle-Expand Wipe, Full-Bleed Diagonal `<polygon>` & Lead-Char Seed** | Mồi cảnh tối giản: Chấm tròn bung nền, Cửa chéo SVG `<polygon>`, Chữ cái đầu rơi | `#REF-08` (`pin_07_[số-tk].mp4`) |
| **`pin_08`** | **Figma 4-Corner Selection Box, 6 Cursors & Elastic Split** | Khung chọn 4 góc kéo mở từ khóa, Con trỏ bầy đàn tụ hội, Tách dòng đàn hồi | `#REF-09` (`pin_08_[số-tk].mp4`) |
| **`riso_09`** | **Claude Motion Editorial Risograph + Hybrid Cut** | Phong cách tạp chí giấy kem `#F3ECDD`, cam `#E2683A`, xanh `#1E5A64`, đan xen Cận mặt | `#PROD-10` (`VietClaudeMotionRiso10s.tsx`) |
| **`mc_power_10`** | **MasterClass Acid-Lime Brutalist Kinetic Text** | Nền vàng chanh `#E0EE70` + Đen `#060606` + Đỏ `#C8232C`: Bàn cờ vua Step-Move, Cột trụ đen | `#PROD-11` (`VietMasterClassPower10s.tsx`) |
| **`paage_11`** | **Paage UI Showcase 70s (28 Beats + 6 B-Roll + 4-Phase Cursor)** | Quảng cáo Khóa học/Spa/Nha khoa/SaaS 11 chương khớp 1:1 nhịp trống & click chuột | `#PROD-12` (`PaageOffline0711_30fps.tsx`) |