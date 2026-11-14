# YouTube Upload: Xử Lý Sự Cố & Kiến Trúc Multi-Token

## 🛠 XỬ LÝ SỰ CỐ: TẢI NHẦM KÊNH YOUTUBE
Nếu video bị tự động upload nhầm sang kênh cá nhân (ví dụ: "Nguyễn Đức Việt") thay vì "Sabakiz", nguyên nhân là do file token OAuth (`token_sabakiz.pickle`) lưu sai phiên đăng nhập. 
- **Cách sửa nhanh:** Chạy lệnh `python3 [đường-dẫn-Mac]`, trình duyệt mở ra BẮT BUỘC phải chọn tài khoản Google sở hữu kênh Sabakiz để ghi đè lại file token chuẩn.

## 🔑 KIẾN TRÚC MULTI-PROJECT & MULTI-TOKEN POOL

Hệ thống lưu trữ **SONG SONG 4 Dự án Google Cloud & nhiều Token** tại `[đường-dẫn-Mac]`:

| File Credentials | Dự án Google Cloud | Token file tương ứng | Kênh kết nối |
|---|---|---|---|
| `client_secrets.json` | `vietndj-git-cms` ([số-tk]) | `token_sabakiz.pickle` | **Sabakiz** (Kênh chính) |
| `client_secrets.json` | `vietndj-git-cms` ([số-tk]) | `token_full.pickle` | **Nguyễn Đức Việt** (Cá nhân) |
| `client_secrets_2.json` | `apiutu` ([số-tk]) | `token_sabakiz_2.pickle` | **Sabakiz** (Dự phòng P2) |
| `client_secrets_2.json` | `apiutu` ([số-tk]) | `token_kqc.pickle` | **KQC** (Gánh tải trần kênh) |
| `client_secrets_3.json` | `edumall-1308` ([số-tk]) | `token_meditation.pickle` | **Meditation Book** |
| `client_secrets_4.json` | `upyoutub004` ([số-tk]) | `token_project_4.pickle` | **Dự Án 4** (Dự phòng mở rộng) |

**Cơ chế hoạt động:**
- Script `extract_storyboard_02.py` tự động thử lần lượt các token trong `TOKEN_CANDIDATES`.
- Nếu kênh chính chạm trần hạn ngạch ngày (`429 Quota Exceeded` hoặc `uploadLimitExceeded`), script **tự động nhảy sang token tiếp theo trong Pool** (như KQC, Project 4).
- Mọi video upload từ bất kỳ kênh nào đều được tự động gom về chung Playlist `Phân tích video` (`PLI7jGRLNGsvY` và `PLONsbnGDa39A`) trên Sabakiz.

## 🛠 XỬ LÝ SỰ CỐ: TỶ LỆ KHUNG HÌNH YOUTUBE BỊ NGANG
- **Tình trạng:** Video tải từ IG/TikTok về đôi lúc là video ngang (VD: 1916x1078) do creator up gốc là ngang. Khi up lên YouTube sẽ bị chèn viền đen trên dưới (letterbox).
- **Cách xử lý:** Hệ thống tải tự động (`extract_storyboard_02.py`) ĐÃ ĐƯỢC CẬP NHẬT để tự động bắt diện `width > height`. Khi đó nó sẽ tự động chạy `ffmpeg` padding dải đen (chuẩn kích thước dọc 1080x1920) TRƯỚC KHI đẩy lên YouTube. AI sau này tuyệt đối KHÔNG cần can thiệp code tải nữa, tính năng đã tự động.

## 🛠 XỬ LÝ SỰ CỐ: QUÉT SÓT VIDEO KHI SỬA LỖI HÀNG LOẠT
- Khi anh yêu cầu kiểm tra/sửa lỗi cho "tất cả các bài sáng nay", AI BẮT BUỘC phải quét toàn bộ thư mục `output_packages` bằng vòng lặp tự động (tham chiếu ngày `newermt`), KHÔNG ĐƯỢC quét thủ công vài bài rồi dừng.
- Script kiểm tra phải duyệt qua từng key trong `master_classifications.json` (cả folder_name lẫn shortcode) để đảm bảo không sót.