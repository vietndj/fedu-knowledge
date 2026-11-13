---
name: banner-k4
description: "Mantra: BANNER K4 / LAM BANNER / CHECK BANNER / SUA BANNER / BO CHON CHU BANNER. Tự động thiết kế, hiệu chỉnh theo font (LAW_09), kiểm toán UI/UX 14 cổng (uiux_auditor.py V4.0) + cold-reviewer và tự học cho Banner Facebook 4:5 (1080x1350)."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `banner-k4` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).


# Hệ Thống Tự Động Thiết Kế, Kiểm Toán UI/UX 14 Cổng (`V4.0`) + `cold-reviewer` & Tự Học Banner Quảng Cáo (`banner-k4`)

Kích hoạt ngay khi anh Việt gọi một trong các từ khóa:
- **`LÀM BANNER KB_XX`** / **`BANNER K4`** / **`TIẾP TỤC BANNER`** / **`BỘ CHỌN CHỮ BANNER`**
- **`CHECK BANNER`** / **`KIỂM TOÁN BANNER`** / **`UI UX AUDITOR`**
- **`SỬA BANNER: ...`** *(kèm nhận xét của anh Việt)*

---

## 1. Kiến Trúc Cốt Lõi & Các File Thực Thi

| Thành phần | Đường dẫn | Vai trò |
|---|---|---|
| **Sổ Cái Tự Học (`Self-Learning Ledger`)** | `[đường-dẫn-Mac]` | Lưu trữ toàn bộ các Luật Vàng đúc kết từ mỗi lần anh Việt sửa/duyệt (`LAW_01` → `LAW_09`+) và bảng thông số `per_font_optical_leading_table` cho 21 họ font Serif. **Bắt buộc đọc ở Bước 0.** |
| **Bộ Chấm Tự Động 14 Cổng (`UI/UX Auditor V4.0`)** | `[đường-dẫn-Mac]` | Chấm tự động 14 cổng thực chiến (`G1` → `G14`) trong `0.8s`: bắt lỗi 2 size chữ lệch nhau, lỗi leading lỏng (`W > 1.36`) hoặc chạm dấu 2D (`min_2d_ink_gap_px < 6px`), lỗi chạm vai áo (`shoulder_clearance < 22px`), lỗi đường gạch `::after` đè chữ, lỗi lệch tâm dọc (`G14`). |
| **Kiểm Toán Viên Thị Giác Độc Lập (`cold-reviewer`)** | Subagent `cold-reviewer` (`Model: "inherit"`, Read-Only, ~15s) | Soi trực tiếp ảnh `.jpg` đã xuất bằng mắt độc lập (0 thiên kiến xác nhận), phát hiện lỗi thẩm mỹ tinh tế trước khi báo cáo anh Việt. |
| **Cố Vấn Kiến Trúc & Luật UI/UX (`CLAUDE2`)** | MCP `claude-delegate` (`run_task_pro`, `model="opus"`) | Tham gia khi thiết kế kiểu trình bày mới hoặc thiết lập công thức toán học/luật mới cho `banner_laws.json` (lưu ý bơm đủ dữ liệu vào `context` và dặn không gọi tool đọc file để trả lời nhanh trong ~25–35s). |
| **Kệ Duyệt & Bộ Chọn Chữ (`HTML Local & Web`)** | `[đường-dẫn-Mac]` & `banner2.html` | Trang giao diện trình bày trực tiếp trên Google Chrome Local (load 0ms từ file `.jpg` local). |
| **Kho 50 Kiểu Phong Cách & 13 Khuôn Q (`Natural Language Resolver`)** | `[đường-dẫn-Mac]` & `build_banner.py` | Chuẩn hóa 50 Kiểu Phôi Phong Cách (`Kiểu 1` → `Kiểu 50`, chia 7 Nhóm Tinh Thần) + 13 Khuôn Quảng Cáo (`Q1` → `Q13`). Hỗ trợ tra cứu tự nhiên qua `python3 [đường-dẫn-Mac] --resolve "<câu nói>"`. |

---

## 1B. Cơ Chế Gọi Tên Tự Nhiên & Phân Loại 50 Kiểu Phong Cách + 13 Khuôn Quảng Cáo (`Q1–Q13`)

Khi anh Việt yêu cầu thiết kế banner theo **Số kiểu (`Kiểu 1..50`)**, **Mã Khuôn (`Q1..Q13`)**, **Tên ngắn tiếng Việt**, hoặc **mô tả tự nhiên**, bắt buộc chạy lệnh tra cứu ở Bước 0:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

### Quy Tắc Bất Biến Khi Ánh Xạ Câu Lệnh Tự Nhiên:
1. **Tách riêng Phôi Phong Cách (`Kiểu 1..50`) và Khuôn Bố Cục Quảng Cáo (`Q1..Q13`):**
   - `Kiểu 1..50`: Quy định bối cảnh, ánh sáng, góc máy và thần thái nhân vật.
   - `Khuôn Q1..Q13`: Quy định cấu trúc đóng khung chữ / sơ đồ chẩn đoán đè lên phôi ảnh (`Q1` Tờ Lịch Studio · `Q2` Tờ Lịch Đen Trắng · `Q3` Ghép Lớp Học Thật · `Q4` Ghép 3 Học Viên · `Q5` Giải Phẫu 3 Khúc · `Q6` Trục 3 Nấc · `Q7` Thang 3 Bậc · `Q8` Đối Chiếu 2 Cột `×/✓` · `Q9` Mặt Cắt Thân Rỗng · `Q10` Tảng Băng Chìm 90-9-1 · `Q11` Khung Trước–Sau · `Q12` Lộ Trình 3 Bước · `Q13` Thanh 90 Người Xem Thầm).
2. **Thứ tự ưu tiên khớp lệnh (`Resolver Priority`):**
   - **Ưu tiên 1 (Khớp số/mã trực tiếp):** `"kiểu 16"`, `"kiểu 33"`, `"khuôn Q10"` $\rightarrow$ Lấy chính xác card tương ứng. Nếu có hậu tố biến thể góc chụp (`"kiểu 9 rộng"`, `"kiểu 16 trắng đen"`, `"kiểu 17 rộng"`, `"kiểu 34 phân thân"`, `"kiểu 35 rộng"`), chọn đúng nhánh ảnh đó.
   - **Ưu tiên 2 (Khớp tên ngắn hoặc từ khóa `aliases`):** Ví dụ `"bàn gỗ đèn giấy"` $\rightarrow$ `Kiểu 16`; `"sofa da CEO"` $\rightarrow$ `Kiểu 33`; `"cầm mic hồng tím"` $\rightarrow$ `Kiểu 5`; `"bờ kè trời xanh"` $\rightarrow$ `Kiểu 34`; `"tuxedo dạ tiệc"` $\rightarrow$ `Kiểu 38`; `"phơi sáng kép"` $\rightarrow$ `Kiểu 19`.
   - **Ưu tiên 3 (Nói chung chung theo bối cảnh/nhóm):** Nếu anh Việt chỉ nói từ khóa chung có nhiều kiểu gần nhau (ví dụ chỉ nói `"ngồi ghế sofa"` thì có `Kiểu 33 Sofa Da Phòng Gỗ CEO` và `Kiểu 49 Sofa Da Nâu Góc Rộng`), gợi ý nhanh 2–3 kiểu khớp nhất kèm số thứ tự để anh Việt chốt hoặc chọn kiểu có điểm `score` cao nhất.
   - **Ưu tiên 4 (Ghi đè trang phục / tỷ lệ):** Mọi chỉ dẫn bổ sung trong câu nói (ví dụ `"lấy kiểu 43 sân bay nhưng mặc vest xanh navy"`, `"tỷ lệ ngang 16:9"`) sẽ ghi đè lên trang phục/tỷ lệ mặc định của kiểu đó.

### Bảng Tóm Tắt 7 Nhóm Tinh Thần (50 Kiểu Phong Cách):
- **① Sân Khấu · Thuyết Trình & Podcast (9 kiểu):** `1` Neon Phòng Máy Chủ · `2` Cầm Máy Thuyết Trình · `5` Diễn Giả Hồng Tím · `10` Sân Khấu Màn LED Lớn · `13` Thuyết Trình Siêu Xe Đỏ · `22` Ghế Đối Thoại Podcast (2 Người) · `26` Showroom Trắng Cầm Máy · `36` Bục Gỗ Phát Biểu Nền Đỏ · `50` Podcast Rèm Tối Mic Thu.
- **② Quyền Lực · Sang Trọng Nền Tối (10 kiểu):** `8` Phòng Khách Tân Cổ Điển · `14` Tuxedo Hoàng Hôn Venice · `21` Biểu Đồ Chữ Vàng (Cook Era) · `23` Studio Tối Bìa Tạp Chí · `31` Quý Ông Nền Đen Tuyền · `33` Sofa Da Phòng Gỗ CEO · `35` Bàn Đá Đen Vân Vàng · `38` Tuxedo Nơ Đen Dạ Tiệc · `45` Blazer Trắng Đèn Chùm Đêm · `49` Sofa Da Nâu Góc Rộng.
- **③ Studio Phông Sáng & Chân Dung Tối Giản (5 kiểu):** `6` Blazer Be Phông Xanh · `15` Phông Xám Doanh Nhân · `27` Vẫy Chào Tường Kem · `39` Nụ Cười Sảnh Tiệc Ấm · `46` Áo Cổ Lọ Đen Kiểu Jobs.
- **④ Bàn Làm Việc · Chuyên Gia & Tư Duy (5 kiểu):** `9` Bàn Họp Tech Startup · `16` Bàn Gỗ Đèn Giấy · `17` Phòng Tối Đèn Giấy Cao · `28` Chuyên Gia Soi Thiết Bị · `29` Trầm Tư Phóng Sự.
- **⑤ Ngoài Trời Ban Ngày · Resort & Thiên Nhiên (9 kiểu):** `3` Quý Ông Hồ Đồi Chè · `4` Nắng Ấm Hiên Gỗ · `7` Vệt Nắng Tường Trắng · `11` Cafe Sáng Đọc Báo · `12` Tường Đá Cổ Châu Âu · `30` Suit Xanh Trước Tòa Tháp · `32` Sơ Mi Trắng Núi Đồi Xanh · `34` Bờ Kè Biển Trời Xanh · `37` Song Hành Tàu Ngầm Cam.
- **⑥ Phố Đêm · Sân Bay & Di Chuyển (4 kiểu):** `41` Phố Đêm Dưới Mái Vòm · `42` Cầu Đi Bộ Đêm Thành Phố · `43` Sải Bước Sảnh Sân Bay · `44` Tựa Lan Can Đô Thị Đêm.
- **⑦ Đồ Họa · Đen Trắng & Hiệu Ứng Đặc Biệt (8 kiểu):** `18` Sóng Ngọc Khoanh Tay · `19` Phơi Sáng Kép Kiến Trúc · `20` Đen Trắng Nền Trắng Chữ To · `24` Vòng Ngọc Diễn Giả · `25` Bộ Ba Góc Mặt Ngang · `40` Góc Nghiêng Vũ Trụ Xanh · `47` Đồ Họa Chéo Đỏ Đen · `48` Đồ Họa Vòng Xoáy Đỏ MC.

---

## 2. Quy Trình "Zero-Friction" (Ít Ma Sát & Tự Động 100%)

Mỗi khi thiết kế hoặc sửa Banner, hệ thống chạy tự động khép kín theo 4 bước (không để Gemini Main tự làm tự khen):

1. **Bước 1 — Tự Động Đo & Khóa Thông Số Theo Từng Font (`Auto-Calibrate / Auto-Heal < 1s`):**
   - Với mỗi bộ font Serif, tự động đo `xH` (`x-height / fontSize`) và biên dạng mực 2D (`2D column-wise ink profile` có `letter-spacing` thật) trên Canvas 2D:
     - **Đồng nhất 1 cỡ chữ duy nhất (`delta_fs = 0px`)** cho cả 3 dòng tiêu đề sao cho `max_line_width <= 548px` (cách vai áo nhân vật `>= 37px`).
     - **Khóa `Optical Leading` riêng cho từng font (`LAW_09`):** $L_{\text{target}} = \max(2.18 \times xH,\ L_{\text{2D}})$ để tỷ lệ khoảng trắng quang học $W = \frac{L - xH}{xH}$ luôn nằm trong vùng đầm chắc **`1.11 – 1.32`** mà khe mực 2D giữa chân chữ dòng trên (`p, g, ộ`) và dấu dòng dưới (`ă, à, ỗ`) vẫn `>= 10px`.
     - **Căn tâm dọc (`G14 Optical Vertical Center`):** Độ lệch khoảng trống đỉnh – đáy `vertical_balance_err <= 0.14`.
2. **Bước 2 — Xuất Ảnh Local & Bung Google Chrome Tức Thì (`0ms` chờ đợi):**
   - Xuất thẳng `.jpg` vào thư mục local và reload ngay tab Google Chrome đang mở (`bo-chon-chu-banner.html` hoặc `banner2.html`) bằng AppleScript `set URL of t` (không dùng `execute javascript` để tránh treo).
3. **Bước 3 — Chạy Máy Đo `uiux_auditor.py V4.0` (`14/14 Cổng`, ~0.8s):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
   - Nếu bất kỳ cổng nào trong `G1..G14` báo `false`, tự động điều chỉnh thông số và re-render ngay lập tức trước khi báo cáo.
4. **Bước 4 — Hậu Kiểm Độc Lập Bằng Subagent `cold-reviewer` (~15s):**
   - Gọi `invoke_subagent` (`TypeName: "cold-reviewer"`, `Model: "inherit"`) truyền trực tiếp đường dẫn ảnh `.jpg` + tiêu chí gốc (không kèm lời tự khen). Nếu `cold-reviewer` phát hiện lỗi thị giác (`P0/P1`), tự động sửa dứt điểm ngay.

---

## 3. Cơ Chế Tự Học Sau Mỗi Lần Anh Việt Sửa (`Self-Learning Loop`)

Mỗi khi anh Việt đưa ra bất kỳ nhận xét sửa đổi nào:
1. **Sửa ngay trên Local + Reload Chrome tức thì** cho anh Việt xem.
2. **Ghi ngay bài học mới vào `banner_laws.json`** và nâng cấp điều kiện kiểm tra tương ứng trong `uiux_auditor.py` để lỗi đó vĩnh viễn không bao giờ lặp lại.

---

## 4. Bộ Định Tuyến Tự Động 4 Cấp (`Auto-Router` — `banner_fast_engine.py` `0.20s/ảnh`) & Quy Chuẩn 4 Phương Án Hook (`LAW_27`)

Khi anh Việt yêu cầu sửa chữ, đổi phương án Hook, đổi kiểu chữ hoặc làm banner khóa mới, hệ thống tự động gọi `[đường-dẫn-Mac]` để phân luồng thông minh:

| Cấp độ | Tên luồng | Khi nào tự động kích hoạt | Tốc độ thực tế & Cổng kiểm tra |
| :--- | :--- | :--- | :--- |
| **L1** | **`FAST_TEXT`** | Chỉ đổi chữ tiêu đề (`hook`), từ khóa màu (`hl`), chữ khung bé (`sub_old/new`) hoặc đổi Phương án `1..4` (`--variant 1..4`) | **`0.20s / ảnh ấm`** (`3.6s` cho 54 ảnh · `7.8s` cho 140 ảnh với 4 workers). Đọc tọa độ mặt từ `face_box_cache.json` + kiểm tra `fast_bbox_gate` (`< 2ms`). |
| **L2** | **`STYLE_SWAP`** | Đổi mã kiểu chữ `H01..H40 × K01..K50 × S01..S35 × M01..M06` | **`0.22s / ảnh ấm`**. Giữ nguyên phôi nền và cache mặt, tính lại `LAW_09` và bắt buộc qua `fast_bbox_gate`. |
| **L3** | **`CAMPAIGN_SYNC`** | Đổi thông tin khóa học (`07–08/11`, địa điểm, học phí `4.000.000đ`) trong `campaign_config.json` | **`7.8s / 140 ảnh`**. Tự động cập nhật Lớp 4 cho toàn bộ 140 bài và kiểm tra `fast_bbox_gate`. |
| **L4** | **`FULL_PLATE`** | Khi hash ảnh nền (`color_bg_sha16`) thay đổi hoặc thêm KB mới chưa có phôi nền | **`2.5s / ảnh`**. Tự động chạy tạo nền Zero-Blur + `audit_v3_banner` 25/25 cổng rồi ghi đè `face_box_cache.json`. |

### Cú pháp chạy nhanh (`0.20s/ảnh`) & Mở Chrome Local xem trước:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- **Quy chuẩn `LAW_27` (Zero-Context Clarity & 4 Phương Án / KB):**
  - Mỗi câu Hook trên Banner bắt buộc là **1 câu tiếng Việt hoàn chỉnh, liền mạch 3 dòng (`3–4 từ/dòng = 13–17 ký tự/dòng`, tổng `10–12 từ`)**, tự thân dễ hiểu trong 1 giây, cấm cắt từ ghép, cấm ẩn dụ cụt, cấm để `sub_old/sub_new` rỗng.
  - Mỗi KB trong `banner2_cards/KB_XX.json` lưu đủ **4 Phương Án Hook** (`PA1` & `PA2` của Gemini + `PA3` & `PA4` của Thư ký `CLAUDE2`): `PA1` kết xuất lên mặt ảnh chính, còn **3 Phương án còn lại hiển thị dạng chữ bên dưới mỗi thẻ trên `banner2.html`** để anh Việt cần đổi phương án nào là bấm/gọi lệnh `0.20s` ra ảnh ngay.


## Quy Chuẩn Nhúng Trực Tiếp Kho 743 Webfont CDN (Không Cần Cài Đặt Font)
- **Chỉ mục tra cứu cho AI:** `[đường-dẫn-Mac]` (743 họ font phân loại theo `k4_role`, `category`, `mood`, `use_case`).
- **Quy tắc nhúng vào `<head>` mọi bản HTML Online / Slide / Banner:**
  - Khai báo biến gốc `FONT_CDN` (trỏ về `https://font.fedu.vn`) và nhúng kèm `crossorigin="anonymous"` để tương thích 100% với cả thiết bị di động chưa cài font lẫn công cụ chụp ảnh DOM (`html-to-image` / Playwright):
    - **Gói 21 Font Chủ Lực (`core.css`):** `<link rel="stylesheet" href="https://font.fedu.vn/cdn/core.css" crossorigin="anonymous">` (gồm `FD Aeonik`, `FD Gilroy`, `GR Sectra`, `GR Pantheon`, `GR Walsheim`, `GR America`, `FD Tiempos`, `FD Acta`, `FD Moranga`, `FD Druk Wide`, `FD Söhne`, `FD Suisse Int'l`, `FD Domaine`, `FD National 2`, `FD Altform`, `FD Ambit`, `GR Alpina`, `GR Super`, `GR Ultra`, `FD Aeonik Mono`, `FD Editorial Old`).
    - **Nhúng lẻ từng bộ (Multiple Fonts):** `<link rel="stylesheet" href="https://font.fedu.vn/cdn/f/<id>.css" crossorigin="anonymous">`.
