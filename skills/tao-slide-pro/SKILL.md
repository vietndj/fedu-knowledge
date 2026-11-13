---
name: tao-slide-pro
description: "Slide Figma/PPTX, bridge server helper.py, 6 kiểu layout chuẩn & Hệ thống 6 Khuôn Sơ Đồ Vector Tổng Quát (diagram_engine.js)."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `tao-slide-pro` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).

> Tài liệu kèm: `references/examples_and_catalog.md`


# Kỹ Năng Thiết Kế Slide, Sơ Đồ & Biên Tập Figma/FigJam (`tao-slide-pro`) - On-Demand Mode

Kỹ năng biến AI thành Co-pilot thiết kế & biên tập thực chiến của **anh Việt**, giao tiếp 2 chiều theo thời gian thực với **Figma Design, Figma Slides và FigJam** theo cơ chế **On-Demand (`0 MB RAM` khi nghỉ)** hoặc xuất file **PowerPoint (`.pptx`)** đồng bộ Google Drive.
*(Mẫu JSON bộ slide đầy đủ, payload FigJam và thông số tọa độ/font Design System 2.0 xem tại `references/examples_and_catalog.md`).*

---

## ⌨️ 5 Cách Gọi / Ra Lệnh Chắc Chắn Kích Hoạt Kỹ Năng

| STT | Mục đích sử dụng | Câu lệnh gọi chắc chắn kích hoạt | Hành vi AI thực hiện tự động |
| :--- | :--- | :--- | :--- |
| **1** | **Tạo slide bài giảng / chia sẻ** | **"Tạo slide figma về [chủ đề]"** *(hoặc "Lên slide figma đối chiếu...")* | Áp dụng chuẩn **Cover Kiểu 01 (Slide 85)** cho slide đầu và **Kiểu 03 (2 Cột Đối Chiếu)** / **Kiểu 02 (3 Cột)** cho các slide sau, đẩy thẳng lên Figma. |
| **2** | **Bật kết nối & Kiểm tra** | **"Bật figma slide"** *(hoặc "Kết nối figma")* | Đánh thức Bridge Server On-Demand (`0.2s`), kiểm tra kết nối Plugin Figma Slides. |
| **3** | **Nhân bản slide kèm Sơ đồ (`clone`)** | **"Clone slide figma với nội dung [text/JSON]"** | Nhân bản từ slide mẫu (`anchorId`), điền số Stencil, tiêu đề song tấu, phụ đề, câu hỏi mở và tự dựng **6 Khuôn Sơ Đồ Vector (`diagram`)** trực tiếp trên slide. |
| **4** | **Sửa văn bản trực tiếp** | **"Sửa figma slide đang chọn"** | Lấy vùng chọn trên Figma, viết lại ngắn gọn và cập nhật ngược vào layer. |
| **5** | **Vẽ Sơ đồ tư duy / Flowchart** | **"Vẽ mindmap figma về [chủ đề]"** *(hoặc "Tạo flowchart trên figjam")* | Tự dựng sơ đồ phân nhánh hoặc flowchart có mũi tên liên kết trên FigJam / Figma. |

---

## 1. Cơ Chế On-Demand & Bộ Lệnh CLI (`helper.py`)

* **Bước 0 trước khi soạn nội dung Slide mới (`brain.py` — ~450 tokens):** Khi tạo slide bài giảng/đối chiếu theo chủ đề, tự động gọi:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
  để lấy sẵn Thơ Lục Bát (`poemText`), câu Lật bản chất 2 cột (`Kiểu 03`) và Khẩu quyết (`Kiểu 06`) đúng chất anh Việt.
* **Khi bình thường:** Tiến trình tắt hoàn toàn (`0 MB RAM, 0% CPU`). Khi có lệnh: tự đánh thức trong `0.2s`. Khi xong: `helper.py stop`.

### 🔹 Các lệnh CLI thực thi chính:
1. **Đọc Selection trực tiếp từ Figma / FigJam:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
2. **⚡ Nhân bản Slide mẫu kèm 6 Khuôn Sơ Đồ Tổng Quát (`clone` — ƯU TIÊN SỐ 1 khi đã có slide mẫu):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
3. **Tạo Bộ Slide Mới từ đầu (`create` — BẮT BUỘC gộp vào 1 file JSON khi tạo $\ge 2$ slide, cấm gọi lẻ liên tiếp):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
4. **Sửa văn bản đang chọn / Cập nhật Tiêu đề & Phụ đề:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
5. **Tạo Mindmap, Sticky Notes, Flowchart trên FigJam & Tắt Server:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

---

## 2. Hệ Thống 6 Khuôn Sơ Đồ Vector Tổng Quát Trên Slide (`diagram_engine.js`)

Khi nhân bản từ Slide mẫu Stencil (`1920 × 1080`, ví dụ `anchorId: "1:451"`), mỗi phần tử slide trong mảng `slides` có thể khai báo thuộc tính `diagram` để tự động dựng sơ đồ tóm tắt bằng Native Figma Nodes + Vector SVG ngay tại vùng sân khấu `x = 120..1800, y = 405..855`:

### 🔹 Khung tọa độ & Typography chuẩn (`1920 × 1080`):
- **Số Stencil lớn:** `FD Monument Extended Regular` `316px`.
- **Nhãn khuôn (`diagram.tag` ≤ 16 ký tự):** `x = 1400, y = 168, w = 400, h = 28` (`SVN-Aeonik Medium 22px`, căn phải, `#58524A`).
- **Tiêu đề song tấu (`Frame 4` tại `y = 235`, căn giữa theo trục `960`):**
  * `titleLine1`: `FD Freight Display Medium Italic 89px`.
  * `titleLine2`: `SVN-Aeonik Medium 77px`, viết **Sentence case** (chữ thường tự nhiên, viết hoa chữ cái đầu), đặt tại `x = w1 + 30` (tự động thu tỷ lệ đồng đều nếu tổng rộng `> 1680px`).
- **Phụ đề (`subtitle` ≤ 100 ký tự):** `x = 260, y = 342, w = 1400` (`SVN-Aeonik Regular 28px`, căn giữa, `#58524A`).
- **Sân khấu Sơ đồ (`Diagram / {kind}`):** `x = 120, y = 405, w = 1680, h = 450`.
- **Câu hỏi tương tác (`questionText` ≤ 120 ký tự):** `x = 120, y = 875, w = 1680, h = 55` (`FD Freight Display Medium Italic 30px`, căn giữa, `#58524A`).
- **Bảng màu tạp chí nền sáng:** Chữ chính `#16181C`, chữ phụ `#58524A`, điểm nhấn `#B45309`, nền hộp chốt `#FDF2D4`, nền thẻ `#FBF8F1`, viền `#DED5BE`, số lớn trong sơ đồ dùng `FD Ivar Fine SemiBold`.

### 🔹 Bảng Đặc Tả & Giới Hạn Ký Tự 6 Khuôn Sơ Đồ (`diagram.kind`):

| Mã `diagram.kind` | Nhãn `tag` gợi ý | Bố cục & Cấu trúc trường JSON (`diagram`) | Giới hạn ký tự (`validate_diagram`) |
| :--- | :--- | :--- | :--- |
| **`compare_strip`** | `"So sánh"` | Bảng đối chiếu 2 cột ngang (`x=460, w=642` vs `x=1158, w=642`) kèm nhãn tiêu chí trái (`x=120, w=320`), vòng tròn nối `joiner` (`d=48`) và thanh `takeaway` đáy (`y=769, h=86`). | `left_head`, `right_head` ≤ 28 · `joiner` ≤ 6 (mặc định `"hay"`) · `rows` (2–3 hàng): `label` ≤ 24, `left` ≤ 44, `right` ≤ 44 · `takeaway` ≤ 80. |
| **`proportion_svg`** | `"Tỷ lệ"` | Biểu đồ tỷ lệ Vector SVG bên trái + Thẻ giải nghĩa số `64px` bên phải:<br>• `mode: "dots"`: Lưới 10×10 (100 chấm `d=30`).<br>• `mode: "donut"`: Vòng cung tròn SVG `d=360`.<br>• `mode: "bar"`: Thanh tỷ lệ ngang `h=72`. | `mode`: `"dots" \| "donut" \| "bar"` (với `"dots"` tổng `value` = 100) · `parts` (2–4 phần): `value` (số), `label` ≤ 36, `desc` ≤ 60 · `source` ≤ 70. |
| **`roadmap_flow`** | `"Các bước"` | Chuỗi 3 bước (`w=522`) hoặc 4 bước (`w=378`) nối tiếp bằng mũi tên SVG `40×24` + thanh `takeaway` đáy. | `steps` (3–4 bước): `label` ≤ 14, `head` ≤ 18, `desc` ≤ 56 · `takeaway` ≤ 80. |
| **`anatomy_visual`** | `"Cơ chế"` | Hình vẽ Vector 2D `520×450` bên trái (`x=120, y=405`) + 3 thẻ chú thích bên phải (`x=720, w=1080, h=138`) nối bằng đường dẫn ngang `1.5px` bắt đầu từ `anchorX`. | `svg` (`520×450`, cấm chứa `<text>`) · `callouts` (đúng 3 mục): `anchorX` (`20..510`), `head` ≤ 32, `desc` ≤ 60. |
| **`ledger_checklist`** | `"Ghi nhớ"` | Khung sổ biên lai 3–4 hàng ngang (`x=120, w=1680`): Số `01..04` (`64px`) + vạch dọc `x=260` + `head` (`34px`) + `desc` (`28px`). | `rows` (3–4 hàng): `head` ≤ 34, `desc` ≤ 52. |
| **`poem_sanctuary`** | `"Khoảng lặng"` | Tự động xóa tiêu đề & phụ đề; đặt ký họa SVG `120×120` tại `x=900, y=356` và 4 câu thơ lục bát (`46px`, dòng cao `68px`) tại `x=360, y=512`. | `lines` (đúng 4 dòng): mỗi dòng ≤ 48 · `svg` (`120×120`). |

---

## 3. Bảng Menu 6 Kiểu Layout Tạo Mới Từ Đầu (`create`)

| Mã Kiểu | Tên Layout | Thuộc tính JSON | Bố cục cốt lõi |
| :--- | :--- | :--- | :--- |
| **Kiểu 01** | **Editorial Giant Anchor Number (Slide 85)** | `layout: "cover"`, `number: "0"` | Số khổng lồ `1636px` (`#3C3C3C`) tràn mép trái + Tiêu đề song tấu + `subtitle` 28px + Header/Footer chuẩn. |
| **Kiểu 02** | **3-Column Breakdown (3 Tầng)** | `layout: "3_columns"`, `cards: [3]` | 3 cột song song (`w = 570px`): `badge` cyan + `title` 28px + Hairline + `desc` 22px + `takeaway` đáy. |
| **Kiểu 03** | **Luxury Comparison 2 Columns (Slide 10)** | `layout: "2_columns"`, `cards: [2]` | 2 khối đối chiếu (`w = 868px`): Trái cảnh báo vs Phải chuẩn chỉ. |
| **Kiểu 04** | **Prompt & Code Jet Dark** | `layout: "code"`, `code_lines: [...]` | Cột trái giải thích logic; Cột phải hộp IDE Dark Jet `#0F172A` chứa code/prompt. |
| **Kiểu 05** | **4-Grid Matrix** | `layout: "4_grid"`, `cards: [4]` | 4 cột song song / ma trận với badge số `01, 02, 03, 04`. |
| **Kiểu 06** | **Big Quote / Takeaway** | `layout: "quote"`, `quote: "..."` | Câu khẩu quyết lớn `40px` giữa màn hình + thẻ `takeaway` ở đáy. |


## Quy Chuẩn Nhúng Trực Tiếp Kho 743 Webfont CDN (Không Cần Cài Đặt Font)
- **Chỉ mục tra cứu cho AI:** `[đường-dẫn-Mac]` (743 họ font phân loại theo `k4_role`, `category`, `mood`, `use_case`).
- **Quy tắc nhúng vào `<head>` mọi bản HTML Online / Slide / Banner:**
  - Khai báo biến gốc `FONT_CDN` (trỏ về `https://font.fedu.vn`) và nhúng kèm `crossorigin="anonymous"` để tương thích 100% với cả thiết bị di động chưa cài font lẫn công cụ chụp ảnh DOM (`html-to-image` / Playwright):
    - **Gói 21 Font Chủ Lực (`core.css`):** `<link rel="stylesheet" href="https://font.fedu.vn/cdn/core.css" crossorigin="anonymous">` (gồm `FD Aeonik`, `FD Gilroy`, `GR Sectra`, `GR Pantheon`, `GR Walsheim`, `GR America`, `FD Tiempos`, `FD Acta`, `FD Moranga`, `FD Druk Wide`, `FD Söhne`, `FD Suisse Int'l`, `FD Domaine`, `FD National 2`, `FD Altform`, `FD Ambit`, `GR Alpina`, `GR Super`, `GR Ultra`, `FD Aeonik Mono`, `FD Editorial Old`).
    - **Nhúng lẻ từng bộ (Multiple Fonts):** `<link rel="stylesheet" href="https://font.fedu.vn/cdn/f/<id>.css" crossorigin="anonymous">`.
