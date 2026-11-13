---
name: html
description: "Xuất HTML Content-Adaptive 3 Mode (Article/Dialogue/Reference), bố cục 2 cột Sticky TOC, hỗ trợ Hybrid UI."
tier: A
---

> **CHẾ ĐỘ GEMINI WEB (Tầng A)** — Đây là bản Web của kỹ năng `html` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Làm trọn đầu ra ngay trên Web (kịch bản, bài viết, phân tích, HTML 1 file).
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).


# KỸ NĂNG INKDOC: XUẤT BẢN TÀI LIỆU NGHIÊN CỨU & TRA CỨU (SKILL: INKDOC)

Định dạng HTML chuyên sâu (Hybrid GitBook + Substack + Wikipedia) tối ưu cho việc **đọc liên tục (long-form), tra cứu wiki, và lưu trữ hội thoại**. Thiết kế loại bỏ hoàn toàn các hiệu ứng animation (Zero-Animation) và khối màn hình để tập trung 100% vào Typographical Hierarchy.

> [!IMPORTANT]
> Đặc tính "Mềm dẻo" (Flexibility): Hệ thống này không đóng băng cứng nhắc. Tùy theo lượng dữ liệu kỹ thuật hay văn xuôi, AI được quyền kết hợp các Module giao diện (Như Reading Mode + Spec Badges) để tối ưu hóa *Trạng thái nhận thức* của người đọc.

---

## 🎯 1. BẢNG MANTRA KÍCH HOẠT

1. **`HTML : [Nội dung / Từ khóa]`** hoặc **`html`**
2. **`INKDOC : [Nội dung / Từ khóa]`**
3. **`XUẤT BẢN HTML`** *(Tự động chuyển hóa nội dung ở lượt chat gần nhất)*

---

## 🤖 2. CƠ CHẾ CONTENT-ADAPTIVE 3 MODE (AI TỰ QUYẾT ĐỊNH)

Khi xuất bản, AI tự động chọn Mode layout phù hợp nhất:

### 📖 MODE 1: ARTICLE (Văn Bản Đọc Dài / Nghiên Cứu)
* **Kích hoạt**: Bài blog, phân tích, tự sự.
* **Layout**: TOC trái, Nội dung cột phải hẹp (max-width 680px - 720px) chuẩn Substack.
* **Đặc điểm**: Đọc liền mạch, không chia cắt. Dùng Tiempos Text 18-19px, line-height 1.7+.

### 💬 MODE 2: DIALOGUE (Hội Thoại / Q&A)
* **Kích hoạt**: Có dạng đối thoại, hỏi-đáp.
* **Layout**: Danh sách lượt chat bên trái để click jump.
* **Đặc điểm**: Câu hỏi (User/Host) nằm trong box nền xám ấm (Slate-100) hoặc dùng `<details><summary>`, câu trả lời bung toàn bộ bằng Tiempos Text.

### 📚 MODE 3: REFERENCE & HYBRID (Wiki / Cẩm Nang / Kịch Bản Kỹ Thuật)
* **Kích hoạt**: Tài liệu tra cứu, kịch bản (Shot-list), danh sách quy tắc chứa nhiều thông số kỹ thuật.
* **Layout Hybrid (Tách Não)**: 
  - **Phần Bối cảnh (Context)**: Trình bày dạng văn xuôi (Serif) thoáng đãng như Mode 1 để đọc hiểu.
  - **Phần Thực thi (Execution / Specs)**: Chuyển sang định dạng bảng, lưới (Grid) hoặc danh sách khối lượng cao với font không chân (Sans-serif). Sử dụng hệ thống **Apple HIG Badge** (xem mục 3.3). Giúp mắt quét dữ liệu (scan) dưới 1 giây.

---

## 🎨 3. UI/UX & CẤU TRÚC HIỂN THỊ

### 3.1. Mục lục (Navigation & Semantic TOC)
* **Nested TOC (Phân tầng ngữ nghĩa)**: Bắt buộc tạo cấu trúc phân tầng (`<ul>/<li>` lồng nhau). Không làm phẳng mục lục.
* **Auto Slugify**: Mọi thẻ Heading (H2, H3, H4) bắt buộc phải có `id` tự sinh từ text (vd: `id="gioi-thieu"`).
* **Instant Snap**: Bấm vào link TOC phải nhảy ngay lập tức (`scroll-behavior: auto;`). KHÔNG dùng `smooth`.
* **ScrollSpy**: Đổi style link TOC đang active khi cuộn, không dùng animation lòe loẹt.

### 3.2. Typography & Hệ thống Màu
* **Nền tảng Monochome Slate**: Trắng (`#ffffff`), xám nhạt (`#f8fafc` đến `#e2e8f0`), và chữ đen đậm (`#0f172a`). Không dùng nền sặc sỡ.
* **Phân cấp Font**:
  - Tiêu đề ngắn/Tên bài: `FD Aeonik Extended` 700 (IN HOA).
  - Tiêu đề mục (H2/H3): `FD Aeonik` 600.
  - Văn bản đọc (Narrative): `Tiempos Text` 18-19px, line-height 1.7.
  - Thông số/Kỹ thuật (Specs): Sans-serif system font 16px hoặc `JetBrains Mono` 13-14px.

### 3.3. Cấu trúc Spec-Block & Micro-Badges (Quy tắc trình bày dữ liệu)
* **Phá bỏ Tường Văn Bản (No Wall of Text)**: Mọi thông số (Góc, Action, Thời lượng) KHÔNG ĐƯỢC để dạng gạch đầu dòng thô. Chuyển thành lưới Flexbox 2 cột (Spec-block):
  - **Cột trái (Label)**: Dùng **Apple HIG Badge** (nền `slate-100`, chữ in hoa `text-[11px]`, viền siêu mỏng, bóng đổ nhẹ). Đóng vai trò mỏ neo thị giác.
  - **Cột phải (Value)**: Căn thẳng hàng, dùng font Sans-serif `text-[16px]`.
* **Căn chỉnh Tuyệt đối (Pixel-Perfect Alignment)**: Mọi Micro-Badge chèn vào giữa text (`[ECU]`, mốc thời gian) bắt buộc phải có CSS `relative -top-[1px] align-baseline` (hoặc `align-middle`) để đường cơ sở (baseline) của huy hiệu phẳng hoàn toàn so với văn bản, tuyệt đối không được trồi lên lệch dòng.

---

## ⚙️ 4. QUY TRÌNH THỰC THI, KIỂM ĐỊNH & XUẤT BẢN (BẮT BUỘC ĐỌC)

* **Template chuẩn 2 cột Sticky TOC (`scroll-behavior: auto`):** `[đường-dẫn-Mac]`
* **Compiler & Deterministic Verifier:** `[đường-dẫn-Mac]`

**BƯỚC 1: NẠP NGUYÊN LIỆU BỘ NÃO THỨ 2 (KHI VIẾT BÀI MỚI) & XÁC ĐỊNH MODE + DỰNG TOC**
- Nếu người dùng yêu cầu viết bài nghiên cứu / cẩm nang mới từ từ khóa hoặc chủ đề (`HTML : [Từ khóa]`), chạy `python3 "[đường-dẫn-Mac] gia/brain.py" "<chủ đề>" --mode write` để nạp sẵn Thơ Lục Bát (`tho`), Lật bản chất (`doilap`) và Luận điểm (`cotloi`) của anh Việt trước khi viết.
- Đọc nội dung -> Chọn Mode (1/2/3) -> Parse toàn bộ Heading để lập cây Semantic Nested TOC.

**BƯỚC 2: RÁP TEMPLATE (`[đường-dẫn-Mac]`) & CHỐNG LỖI DOM**
Khi xử lý văn bản hoặc dùng `[đường-dẫn-Mac]`, luôn ghi nhớ các bài học kỹ thuật:
1. **Lỗi Markdown List (Bị gộp dòng)**: Khi dịch file `.md`, nếu danh sách (`- item`) đứng liền sát đoạn văn trước mà không có dòng trắng, bộ parser dễ gộp thành Text thường (`<p>`). **GIẢI PHÁP:** Luôn chạy Regex chèn thêm `\n\n` trước `- ` nếu nó không ở đầu dòng trước khi convert.
2. **Lỗi Nuốt Chữ khi DOM Manipulation (Live List Iteration Bug)**: Khi dùng `BeautifulSoup` đổi cấu trúc DOM (ví dụ: bọc Text vào các Div 2 cột), tuyệt đối KHÔNG dùng vòng lặp `for child in soup.contents` trực tiếp. Việc move/append phần tử sẽ làm thay đổi mảng gốc `contents`, gây ra lỗi nhảy cóc (skipping elements) và âm thầm xóa vĩnh viễn nội dung chữ (text nodes) của người dùng. **GIẢI PHÁP:** Luôn ép sang mảng tĩnh `for child in list(soup.contents):`.

**BƯỚC 3: KIỂM ĐỊNH TẤT ĐỊNH (`compile_and_verify_inkdoc.py`) TRƯỚC KHI PUSH GIT**
Bắt buộc chạy Verifier để đảm bảo `scroll-behavior: auto`, đủ bố cục 2 cột Sticky TOC, không sót raw Markdown (`**...**`, `### `), bảo toàn $\ge 95\%$ số từ so với bản gốc và sạch từ cấm qua `verify_voice.py`:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

**BƯỚC 4: XUẤT BẢN VÀ PUSH GIT**
* Lưu file `.html` (Kebab-case) tại kho `k`.
* **Favicon Tự động**: Gen bằng SVG Data URI. Nền near-black (`#07090E`), bo góc app icon (`rx="16"`). Monogram 2 chữ in hoa theo tên bài. Màu monogram tùy ngữ cảnh (Tâm lý: `#10B981`, Marketing: `#FB923C`, Code: `#38BDF8`).
* Tự động push GitHub (`git add`, `git commit`, `git push`) và báo cáo URL cho user.


## Quy Chuẩn Nhúng Trực Tiếp Kho 743 Webfont CDN (Không Cần Cài Đặt Font)
- **Chỉ mục tra cứu cho AI:** `[đường-dẫn-Mac]` (743 họ font phân loại theo `k4_role`, `category`, `mood`, `use_case`).
- **Quy tắc nhúng vào `<head>` mọi bản HTML Online / Slide / Banner:**
  - Khai báo biến gốc `FONT_CDN` (trỏ về `https://font.fedu.vn`) và nhúng kèm `crossorigin="anonymous"` để tương thích 100% với cả thiết bị di động chưa cài font lẫn công cụ chụp ảnh DOM (`html-to-image` / Playwright):
    - **Gói 21 Font Chủ Lực (`core.css`):** `<link rel="stylesheet" href="https://font.fedu.vn/cdn/core.css" crossorigin="anonymous">` (gồm `FD Aeonik`, `FD Gilroy`, `GR Sectra`, `GR Pantheon`, `GR Walsheim`, `GR America`, `FD Tiempos`, `FD Acta`, `FD Moranga`, `FD Druk Wide`, `FD Söhne`, `FD Suisse Int'l`, `FD Domaine`, `FD National 2`, `FD Altform`, `FD Ambit`, `GR Alpina`, `GR Super`, `GR Ultra`, `FD Aeonik Mono`, `FD Editorial Old`).
    - **Nhúng lẻ từng bộ (Multiple Fonts):** `<link rel="stylesheet" href="https://font.fedu.vn/cdn/f/<id>.css" crossorigin="anonymous">`.
