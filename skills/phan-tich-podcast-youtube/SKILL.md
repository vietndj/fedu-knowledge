---
name: phan-tich-podcast-youtube
description: "Link YouTube / mantra PODCAST. Bóc transcript, phân tích 8 insight, HTML repo k."
tier: A
---

> **CHẾ ĐỘ GEMINI WEB (Tầng A)** — Đây là bản Web của kỹ năng `phan-tich-podcast-youtube` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Làm trọn đầu ra ngay trên Web (kịch bản, bài viết, phân tích, HTML 1 file).
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).


# KỸ NĂNG PHÂN TÍCH PODCAST YOUTUBE HỆ THỐNG (SYSTEM ARCHITECT PODCAST ANALYZER)

## 📌 QUY TẮC ĐỊNH TUYẾN LINK TỰ ĐỘNG (SMART URL ROUTING)
- Bất cứ khi nào người dùng gửi đường link **YouTube** (`youtube.com/watch?v=...`, `youtu.be/...`, `youtube.com/live/...`, `youtube.com/shorts/...`):
  - **MẶC ĐỊNH 100%** kích hoạt kỹ năng **`phan-tich-podcast-youtube`** (không bắt buộc gõ thêm chữ `PODCAST`).
  - **TUYỆT ĐỐI KHÔNG** dùng `analyze-video` (chỉ dành cho video ngắn Instagram/TikTok/FB).

---

## QUY TRÌNH THỰC THI TỰ ĐỘNG HÓA 5 BƯỚC KHÉP KÍN

### 1. TẢI & LÀM SẠCH TRANSCRIPT + METADATA (`ingest_youtube_podcast.py`)
- Gọi trực tiếp script chuẩn để tải metadata (`upload_date` chuẩn `DD/MM/YYYY`, `duration_string`) và làm sạch phụ đề `.vtt`/`.srt` (khử thẻ `<c>`, inline timestamp `<00:00:00.000>`, khử dòng lặp liên tiếp của YouTube auto-sub, gom đoạn mỗi 45s giúp giảm ~80% token rác):
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- **Quy chuẩn ngày phát hành (Publish Date Standard)**: BẮT BUỘC lấy ngày phát hành chính xác từ `upload_date` của YouTube (`DD/MM/YYYY` cho giao diện và `YYYY-MM-DD` cho `<meta property="article:published_time">`).

---

### 2. PHÂN TÍCH THEO PROMPT 'KIẾN TRÚC SƯ TRÍ TUỆ HỆ THỐNG'
- **Bước 2.0 — Nạp Nguyên Liệu Bộ Não Thứ 2 (`brain.py` — ~450 tokens):** Trước khi biên soạn 8 Insights, gọi:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
  để đối chiếu các cặp Thơ Lục Bát (`tho`), câu Lật bản chất (`doilap`) và Luận điểm (`cotloi`) sẵn có của anh Việt cùng chủ đề.
- **Văn phong ("Chất Nguyễn Việt × Độ Sắc Claude" — Chế độ `giaima`)**:
  - Sắc bén, chuyên nghiệp, trực diện, CẤM biệt ngữ vĩ mô, CẤM thuật ngữ khoa học/hàn lâm, CẤM self-help sáo rỗng, tuân thủ 100% Sổ Đen `nguyen-viet-voice`. 100% TIẾNG VIỆT.
  - **Kết luận đặt ngay đầu mỗi Insight**: Mở bằng thơ Lục Bát vật lý mỏ neo + câu định nghĩa trực diện `**Không phải A... mà là B**` (vượt qua phép thử hoán đổi: vế A là cách hiểu thông thường của số đông, vế B chỉ đúng cơ chế chạy ngầm thật sự).
  - **Giải mã theo chuỗi nhân quả**: Trình bày cơ chế theo chuỗi `Bước 1 -> Bước 2 -> Bước 3` bằng vật thật, việc thật đời thường (bàn làm việc, sổ bán hàng, quán ăn, xưởng may...).
- **Quy chuẩn Tiêu đề & Thẻ `<title>`**:
  - Dịch thoát ý tiêu đề sang tiếng Việt đanh thép, phản ánh đúng bản chất bài học.
  - Công thức bắt buộc: `<title>{Tên_Diễn_Giả}: {Tiêu_Đề_Tiếng_Việt}</title>`.
  - **CẤM TUYỆT ĐỐI** để tiêu đề tiếng Anh hoặc chèn hậu tố thừa (`| Chuẩn Đọc & Bố Cục FEDU`, `| Kiến Trúc Sư...`, `| System Intelligence...`, `| fedu.vn...`).
- **Cấu trúc 5 phần bắt buộc**:
  - **0. [THÔNG TIN BẢN GỐC]**: Hiển thị đủ 5 thông số `.meta-item` (`Khách mời`, `Vai trò`, `Phát hành` chuẩn `DD/MM/YYYY`, `Thời lượng gốc`, `Thời lượng đọc`) kèm Link YouTube gốc (`target="_blank"`) và đoạn tóm tắt bối cảnh thực địa.
  - **1. [BÓC TRẦN LẦM TƯỞNG]**: *2 câu lục bát in nghiêng*. 2 câu blockquote (`>`) sắc lạnh đập tan ảo tưởng đám đông.
  - **2. [NGUYÊN LÝ GỐC RỄ]**: *2 câu lục bát in nghiêng*. Quét toàn bộ video, **TỐI THIỂU 8 Insights** rải đều. Mỗi Insight bắt buộc có:
    - `### 📌 Insight [Số]: [Tóm tắt kết luận 1 câu đặt ngay đầu]`
    - `> 📜 Lục bát mỏ neo:` 2 câu thơ lục bát vật lý in nghiêng + câu định nghĩa `**Không phải A... mà là B**`.
    - `> 🎙️ Dữ kiện gốc:` Trích câu chuyện/số liệu/nghiên cứu thực tế.
    - `- 👁️ Hiện tượng bề mặt:` Đám đông làm sai thế nào.
    - `- 🔬 Giải mã bản chất:` Giải thích bình dân, trực diện theo chuỗi `Bước 1 -> Bước 2 -> Bước 3`.
    - `- ⚙️ Cách làm thực chiến:` Cách thiết kế môi trường vật lý / các bước làm tại bàn.
  - **3. [THIẾT KẾ KHÔNG GIAN]**: *2 câu lục bát in nghiêng*. Hướng dẫn bài trí môi trường vật lý, loại bỏ ma sát.
  - **4. [BẢO TOÀN CẢM XÚC]**: *2 câu lục bát in nghiêng*. Khách quan hóa rủi ro thành dữ liệu thực nghiệm.

---

### 3. DỰNG & KIỂM ĐỊNH HTML SWISS MONOCHROME (`build_and_verify_podcast_html.py`)
- **Triết lý Swiss Monochrome (30NGAYVIRAL Reading Flow Light Theme)**:
  - Chỉ dùng đậm–nhạt, in hoa–thường và khoảng cách trên nền trắng `#ffffff`, chữ thân bài `Tiempos Text` (`16.5px`, `line-height: 1.82`, màu mực `#0f172a` chuẩn WCAG AAA), tiêu đề `FD Aeonik` (`#090d16`). CẤM dùng màu mè hay chấm tròn macOS.
  - Mỗi Insight đặt trong `.code-box` tối giản có nút `Sao chép` 1-chạm góc trên phải.
  - `.top-nav__meta` hiển thị `📅 DD/MM/YYYY | 0% ĐÃ ĐỌC`.
- **Dựng HTML từ JSON hoặc Kiểm định file HTML bắt buộc**:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Chỉ khi script trả về `"status": "PASS"` (exit code `0`) mới được chuyển sang Bước 4.

---

### 4. ĐỒNG BỘ CHỈ MỤC & ĐẨY LÊN REPO `vietndj/k`
- File HTML lưu tại: `[đường-dẫn-Mac]].html` (nạp font tương đối từ `./fonts/`).
- Chạy `python3 build_feed.py` tại `[đường-dẫn-Mac]` để tái lập chỉ mục tìm kiếm và `posts-manifest.json`.
- Thực hiện `git add`, `git commit` và `git push` lên repo `vietndj/k`:
  - GitHub Pages: `https://vietndj.github.io/k/[slug-bai-viet].html`
  - Custom domain: `https://fedu.vn/k/[slug-bai-viet].html`

---

### 5. BÁO CÁO KẾT QUẢ (TELEGRAM CHỈ GỬI KHI CÓ YÊU CẦU)
- **Mặc định 100% KHÔNG tự ý bắn Telegram.** Trả kết quả trực tiếp trong khung chat Antigravity.
- Chỉ khi anh Việt yêu cầu rõ việc gửi Telegram mới gọi:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
