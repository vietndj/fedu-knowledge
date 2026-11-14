# tao-slide-pro — Mẫu JSON Bộ Slide, FigJam Payloads & Thông số Design System 2.0

> Phần tham chiếu tách từ `SKILL.md` (nội dung gốc giữ nguyên 100%).

<!-- gốc: SKILL.md dòng 54-119 -->
4. **Cấu trúc JSON Chuẩn Cho Bộ Slide:**
   ```json
   [
     {
       "layout": "cover",
       "number": "0",
       "title_part1": "Làm thế nào",
       "title_part2": "Video đẹp ?",
       "subtitle": "Khi đã biết cách dùng capcut & quay bằng đt rất nét rồi"
     },
     {
       "layout": "2_columns",
       "section": "ĐỐI CHIẾU 01 • MỤC TIÊU & TÂM LÝ",
       "title": "CHUYỂN HOÁ NHẬN THỨC VS THÚC ÉP MUA HÀNG",
       "subtitle": "sự khác biệt gốc rễ giữa nuôi dưỡng niềm tin và săn bắt doanh số tức thì",
       "cards": [
         {
           "badge": "❌ 01 • VIDEO ADS (QUẢNG CÁO RA ĐƠN)",
           "title": "SĂN BẮT DOANH SỐ & KHÁCH LƯỚT QUA",
           "desc": "• Mục tiêu cốt lõi: Bán hàng ngay lập tức (Hard Sell), gom data nóng, ép khách bấm mua trên từng đồng chi phí.\n\n• Tâm lý người xem: Cảm thấy đang bị chào bán. Thấy dè chừng, phán xét và lướt qua ngay nếu chưa có nhu cầu cấp bách.",
           "takeaway": "Ads giải quyết dòng tiền ngắn hạn nhưng khiến tệp khách hàng cảnh giác."
         },
         {
           "badge": "✅ 02 • VIDEO MARKETING (ĐÓNG GÓI GIÁ TRỊ)",
           "title": "GIEO HẠT NHẬN THỨC & TỰ NGUYỆN TÌM MUA",
           "desc": "• Mục tiêu cốt lõi: Xây dựng uy tín, niềm tin (Trust), cho thấy tay nghề thật và thay đổi góc nhìn lâu dài.\n\n• Tâm lý người xem: Cảm thấy được nhận giá trị, mở mang tư duy. Người xem biết ơn, tự nguyện follow và chủ động tìm mua.",
           "takeaway": "Marketing nuôi dưỡng lòng tin để khách hàng tự chốt đơn mà không cần ép mua."
         }
       ]
     },
     {
       "layout": "3_columns",
       "section": "KỊCH BẢN THỰC CHIẾN",
       "title": "3 TẦNG ĐÀO SÂU TỰ SỰ VIRAL",
       "subtitle": "công thức gọi đúng điều ai cũng biết nhưng ngại nói",
       "cards": [
         {
           "badge": "TẦNG 1 • SAFE",
           "title": "Bề nổi ai cũng thấy",
           "desc": "Gọi đúng vấn đề khách đang gặp hoặc tình huống đời thường quen thuộc. Giữ mắt người xem ngay 3 giây đầu.",
           "takeaway": "Mở khoá chú ý"
         },
         {
           "badge": "TẦNG 2 • REAL",
           "title": "Lý do thực sự bên trong",
           "desc": "Đặt câu hỏi 'Tại sao' 2 lần. Nói thẳng chỗ khó nói mà số đông hay né tránh.",
           "takeaway": "Nói trúng tim đen"
         },
         {
           "badge": "TẦNG 3 • RAW",
           "title": "Đóng gói giải pháp cốt lõi",
           "desc": "Đưa ra công thức dứt điểm vấn đề. Biến chiêm nghiệm thành hành động cụ thể.",
           "takeaway": "Tạo niềm tin tuyệt đối"
         }
       ]
     },
     {
       "layout": "quote",
       "section": "BÀI HỌC ĐÚC KẾT",
       "title": "CÔNG THỨC KẾT HỢP MARKETING & ADS",
       "subtitle": "marketing đi trước tạo niềm tin, ads tiếp sức bùng nổ",
       "quote": "Đừng bao giờ chạy Ads khi kênh chưa có Video Marketing tạo dựng niềm tin. Hãy dùng Video Marketing để xây 'đập giữ nước' trước, rồi mới dùng Ads để 'mở van xả nước' mang doanh thu bùng nổ.",
       "takeaway": "🎯 80% Năng lượng chia sẻ tay nghề thật (Organic) + 20% Ngân sách chạy Ads bài ra đơn nhiều nhất."
     }
   ]
   ```

<!-- gốc: SKILL.md dòng 129-155 -->
7. **Tạo Sơ đồ tư duy (Mindmap phân nhánh) trên FigJam:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
8. **Tạo cụm Sticky Notes trên FigJam:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
9. **Tạo Sơ đồ quy trình / Flowchart trên FigJam:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

<!-- gốc: SKILL.md dòng 163-193 -->
## 2. Bảng Menu 6 Kiểu Layout Chuẩn Hóa Slide (Design Presets)

| Mã Kiểu | Tên Layout | Thuộc tính JSON nhận diện | Bố cục & Tiêu chuẩn chi tiết |
| :--- | :--- | :--- | :--- |
| **Kiểu 01** | **Editorial Giant Anchor Number (Slide 85 Master Standard)** | `layout: "cover"`, `number: "0"`, `watermark: "0"` | **Slide Mở Đầu (Bắt buộc cho slide 1):** Số khổng lồ `1636px` (`#3C3C3C`, opacity 0.99) tràn mép trái (`x = -178, y = -401`) + Cụm tiêu đề song tấu tại `x = 899, y = 418` (Vế 1 Serif Nghiêng `SVN-Freight Display Medium Italic` 89px & Vế 2 Sans `SVN-Aeonik Medium` 77px) + Subtitle 28px (`x = 899, y = 540`) + Top Header `2026` & `imess/zalo : [sđt]` + Hairline đáy `y = 955` + Mentor Footer Signature (`x = 1590, y = 1000`). |
| **Kiểu 02** | **3-Column Breakdown (3 Tầng)** | `layout: "3_columns"` hoặc `cards: [3 phần tử]` | 3 Cột lớn song song (`w = 570px`): Header badge cyan + Tiêu đề thẻ `28px` + Hairline phân tách + Body text `22px` (`lineHeight 160%`) + Hộp Takeaway xanh ngọc ở đáy. |
| **Kiểu 03** | **Luxury Comparison 2 Columns (Slide 10 Master Standard)** | `layout: "2_columns"` hoặc `cards: [2 phần tử]` | **2 Khối Đối Chiếu Sang Trọng (`w = 868px`):**<br>• Cột Trái (Cảnh báo/Ads): Viền đỏ `#FCA5A5` 1.5px, Badge `❌ 01 • ...` (`SVN-Aeonik Bold 20px`, đỏ `#DC2626`), Tiêu đề thẻ `32px` (`FD Aeonik Extended Bold`), Hairline phân cách 1px `#E2E8F0`, Body `25px` (`lineHeight 155%`) phân đoạn `\n\n`, Hộp Takeaway bo góc 10px.<br>• Cột Phải (Chuẩn chỉ/Marketing): Viền xanh ngọc `#6EE7B7` 1.5px, Badge `✅ 02 • ...` (`SVN-Aeonik Bold 20px`, xanh `#059669`), Tiêu đề thẻ `32px`, Hairline phân cách 1px, Body `25px`, Hộp Takeaway bo góc 10px. |
| **Kiểu 04** | **Prompt & Code Jet Dark** | `layout: "code"` hoặc `code_lines: [...]` | Cột trái giải thích logic; Cột phải là hộp IDE Dark Jet `#0F172A` có 3 nút tròn Mac OS đỏ-vàng-xanh chứa code/prompt XML chuẩn chỉ. |
| **Kiểu 05** | **4-Grid Matrix** | `layout: "4_grid"` hoặc `cards: [4 phần tử]` | 4 cột song song / ma trận với badge số `01, 02, 03, 04`. |
| **Kiểu 06** | **Big Quote / Takeaway** | `layout: "quote"` hoặc `quote: "..."` | 1 Câu khẩu quyết cốt lõi cỡ lớn `40px` (`SVN-Freight Display Medium Italic`) ở giữa màn hình + Thẻ đúc kết hành động thực chiến ở đáy. |

---

## 3. Hệ Thống Tiêu Chuẩn Thiết Kế Slide Mới (Design System 2.0)

> [!IMPORTANT]
> **3 NGUYÊN TẮC BẤT DI BẤT DỊCH CỦA ANH VIỆT:**
> 1. **SLIDE TIÊU ĐỀ ĐẦU TIÊN (COVER) LUÔN DÙNG KIỂU 01 (GIANT ANCHOR NUMBER 0):**
>    - Số khổng lồ `1636px` (`SVN-Aeonik Black`, màu `#3C3C3C`, tràn viền mép trái `x = -178px, y = -401px`) để neo giữ thị giác trong 0.2s đầu tiên.
>    - Mặc định đánh số `0` (người dùng sẽ đổi số 1, 2, 3... sau tùy ý).
>    - Cụm tiêu đề song tấu: Serif nghiêng (`SVN-Freight Display Medium Italic` 89px) + Sans dứt khoát (`SVN-Aeonik Medium` 77px) + Subtag 28px (`SVN-Aeonik Regular`).
>    - Nền trắng tinh khiết `#FFFFFF`, Top Header `2026` & `imess/zalo : [sđt]`, Hairline đáy `y = 955px`, Mentor Footer Signature `x = 1590, y = 1000`.
> 2. **TẤT CẢ SLIDE NỘI DUNG TIẾP THEO (SLIDES 2+):**
>    - Dùng chuẩn **NỀN TRẮNG TINH KHIẾT `#FFFFFF`** với chữ than chì đậm `#0F172A` / `#334155` sắc nét, thẻ Container `#F8FAFC`, Viền `#E2E8F0`, Takeaway trắng/xanh ngọc.
>    - Header Top dàn đều 2 đầu (`SPACE_BETWEEN`): `2026  •  TÊN CHUYÊN MỤC` ở trái và `imess/zalo : [sđt]` ở phải.
>    - Footer Bar dàn đều 2 đầu: Mentor Profile (Avatar + `Mentor : Nguyễn Đức Việt` / `[sđt]`) ở trái và `[email]` ở phải.
> 3. **CẤU TRÚC THẺ ĐỐI CHIẾU 2 CỘT (KIỂU 03):**
>    - **BẮT BUỘC** có Cụm Header Thẻ riêng: Badge phân loại màu + Tiêu đề thẻ lớn `32px` (`FD Aeonik Extended Bold`).
>    - **BẮT BUỘC** có đường kẻ Hairline 1px `#E2E8F0` ngăn cách tiêu đề và nội dung bên dưới.
>    - Nội dung body phải có khoảng cách dòng thông thoáng (`lineHeight: 155%`) và ngắt đoạn `\n\n`.