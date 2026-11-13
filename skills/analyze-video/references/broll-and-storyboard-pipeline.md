# auto-broll-bank (B-Roll Automation Pipeline)

Kích hoạt khi người dùng gõ một trong các mantra sau hoặc yêu cầu phân tích video B-roll:
1. `UP BROLL : [đường_dẫn_hoặc_link]` hoặc `BROLL BANK : [đường_dẫn]`
2. `brollbank` hoặc `tìm trong brollbank` hoặc `broll bank`
3. Yêu cầu phân tích/cắt phân cảnh đắt cho video B-roll.

---

## 1. QUY TRÌNH TRA CỨU KHO (Khi gọi `brollbank`)
- Ngay lập tức hiểu yêu cầu là tìm kiếm video/cảnh trám B-roll.
- Truy cập vào file cơ sở dữ liệu: `[đường-dẫn-Mac]`.
- Đọc nội dung JSON, lọc các video phù hợp theo keyword/archetype/tag.
- Trả về danh sách kết quả trực tiếp (kèm link xem YouTube và mã số).

---

## 2. QUY TRÌNH TỰ ĐỘNG HÓA TOÀN TRÌNH (ALL-IN-ONE PIPELINE)

Khi thêm mới hoặc phân tích video B-roll, AI BẮT BUỘC thực thi trọn vẹn **6 bước khép kín** sau đây (chạy qua Master Runner hoặc các module tương ứng, không dừng dở chừng):

> _(lệnh chạy trên Mac — đã lược khi lên Web)_

### BƯỚC 1: Phân Tích & Cắt Phân Cảnh Đắt (Golden Clips)
- Tự động quét file video và SRT phụ đề tương ứng.
- Nhận diện các khoảnh khắc đắt giá (Insight cốt lõi, bước ngoặt tâm lý, kỹ thuật nghề).
- Dùng `ffmpeg -ss <start> -to <end> -c copy -avoid_negative_ts make_zero` cắt trực tiếp thành các file `.mp4` 4K chất lượng gốc (Lossless, tốc độ >100x).
- Xuất file `.srt` phụ đề con độc lập cho từng clip (đồng bộ về mốc `00:00:00,000`) để kéo thẳng vào CapCut / Premiere dựng ngay.
- Thư mục lưu trữ: `<thư_mục_video>/phan_canh_dat/`.

### BƯỚC 2: Tạo YouTube Chapter Markers & Description
- Tự động sinh danh sách mốc thời gian YouTube Chapters bắt đầu từ `00:00`.
- Tạo file `desc.txt` chứa tiêu đề, tóm tắt nội dung và toàn bộ mốc Chapters.

### BƯỚC 3: Upload YouTube Chế Độ Unlisted
- Gọi script:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Cơ chế upload: Chunk 20MB (`resumable=True`), tự động retry chống đứt gãy kết nối mạng cho video dung lượng lớn (4K hàng chục GB).

### BƯỚC 4: Nghiệm Thu Link YouTube & Thêm Vào Playlist
- **Nghiệm thu bắt buộc:** Tự động gọi API `youtube.videos().list(part='snippet,status', id=video_id)` để kiểm tra trạng thái video (`uploaded` / `processed`).
- Trích xuất link chính thức: `https://www.youtube.com/watch?v=<video_id>` và short link `https://youtu.be/<video_id>`.
- Tự động add video vào Playlist B-Roll Bank chính thức: `PLPs82ezbs9Lo`.

### BƯỚC 5: Cập Nhật Database Chuẩn 100% Schema & Rebuild HTML
- Gọi script:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Script tự động đọc `ffprobe` để nạp đầy đủ: `orientation` (`vertical` / `horizontal`), `resolution`, `duration`, `size_mb`, `category_badge`, `thumbnail`.
- Cập nhật cả 2 cơ sở dữ liệu:
  - `[đường-dẫn-Mac] BANK/broll_bank_master.json`
  - `[đường-dẫn-Mac]`
- Chạy `build_brollbank_html.py` kết xuất lại giao diện.

### BƯỚC 6: Auto Git Push Deploy Live Website
- Chạy lệnh commit và push tự động tại repo GitHub Pages:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Xác nhận trang web đã cập nhật tại: `https://brollbank.fedu.vn`.

---

## 3. BÁO CÁO NGHIỆM THU
Sau khi kết thúc luồng, AI xuất bảng báo cáo ngắn gọn, trực diện:
1. Link YouTube nghiệm thu (Unlisted) & Playlist.
2. Link Website live `https://brollbank.fedu.vn`.
3. Bảng danh sách các phân cảnh đắt đã cắt kèm thời lượng, file `.mp4` và `.srt` con.

---

# Kỹ Năng: Tạo Bảng Phân Cảnh Điện Ảnh Tự Động (AI Storyboard Studio)

Kỹ năng này tự động hóa 100% quy trình chuyển đổi **Kịch bản nói (lời thoại + mô tả cảnh)** và **Ảnh bối cảnh gốc** thành **Bảng Phân Cảnh Điện Ảnh 9:16** tương tác đa tầng chuẩn Studio.

---

## 🎯 1. NGUYÊN TẮC CỐT LÕI & CHUẨN ĐẦU RA

1. **Cơ chế phân cảnh 3 nhịp (3-Beat Rhythm):** Mỗi cảnh BẮT BUỘC được băm nhỏ thành 3 khung hình:
   - 🔰 **Đầu cảnh (In-point):** Thiết lập không gian, vị thế nhân vật và điểm chạm mở màn.
   - 🔥 **Chi tiết / Cao trào (Main Action):** Hành động trọng tâm, biểu cảm và cận cảnh nội dung.
   - 🔄 **Cuối cảnh / Mồi chuyển (Out-point Lead):** Động tác kết thúc / ngắt nhịp làm mồi nối mượt sang cảnh kế tiếp (*Match-cut*).
2. **Nhân Vật Mặc Định Tuyệt Đối Là Anh Việt:** Mọi khung hình visual storyboard có nhân vật nam đều MẶC ĐỊNH lấy theo nhân diện anh Việt (khai thác bộ mỏ neo tại `[đường-dẫn-Mac] gia/assets/ava` và `anh_viet_face_catalog.json`).
3. **Đồng Nhất 100% Trang Phục (Wardrobe Continuity):** Toàn bộ 15 micro-beats trong cùng một bảng phân cảnh BẮT BUỘC phải mặc CÙNG MỘT BỘ TRANG PHỤC duy nhất. Tuyệt đối không để AI tự đổi trang phục giữa các cảnh làm gãy nhịp raccord điện ảnh.
4. **Khối Tin Nhắn Gốc (Original Input Context):** Hiển thị nổi bật ở trên cùng file HTML (gồm text kịch bản gốc và ảnh bối cảnh nhận được qua Telegram hoặc Chat).
5. **Giao Diện Sạch (No AI Prompt Box):** Loại bỏ hoàn toàn các box prompt AI lý thuyết, tập trung 100% vào thông số đạo diễn (Cỡ cảnh, Góc máy, Động tác máy, Bố cục, Ghi chú đạo diễn và Lời thoại).
6. **Lưu trữ Cloudflare R2:** Mọi hình ảnh phân cảnh và bối cảnh tham chiếu được lưu trữ vĩnh viễn trên Cloudflare R2 CDN (`https://media.fedu.vn/storyboards/`).
7. **Xuất bản GitHub Pages:** Tự động đồng bộ và xuất bản web HTML tương tác trực tuyến tại `https://vietndj.github.io/offline02/`.
8. **Định Dạng Tin Nhắn Telegram Siêu Tinh Gọn:** Khi gửi kết quả qua Telegram cho anh Việt (@viet_vni_bot), BẮT BUỘC chỉ gửi **Tiêu đề kịch bản** và **Link HTML online**.
   * *Mẫu chuẩn:*
     ```text
     🎬 Bảng Phân Cảnh: [Tiêu đề kịch bản]
     🔗 https://vietndj.github.io/offline02/[ten_file].html
     ```

---

## 🗣️ 2. CÁCH GỌI TỰ NHIÊN

### A. 5 Cách Gọi Trong Chat:
1. *"Lên bảng phân cảnh cho kịch bản này giúp tôi, kèm ảnh bối cảnh..."*
2. *"Tạo storyboard 5 cảnh cho video bán hàng này..."*
3. *"Băm nhỏ kịch bản này thành các phân cảnh 3 nhịp (đầu, chi tiết, mồi chuyển)..."*
4. *"Lập visual storyboard 9:16 và xuất ra web html..."*
5. *"Phân cảnh kịch bản này và đẩy ảnh lên R2 + GitHub Pages..."*

### B. 5 Cách Gọi Qua Telegram Bot (@viet_vni_bot):
1. **Gửi 1-3 ảnh bối cảnh** kèm Caption là nội dung kịch bản thoại.
2. **Gõ lệnh nhanh:** `/storyboard [dán nội dung kịch bản hoặc link online]`
3. **Nhắn tự nhiên:** `Phân cảnh kịch bản này giúp tôi: Cảnh 1... Cảnh 2...`
4. **Nhắn theo tiền tố:** `Bảng phân cảnh: [dán kịch bản 5 cảnh]`
5. **Nhắn yêu cầu:** `Lên phân cảnh video 30s từ kịch bản này...`

---

## ⚙️ 3. QUY TRÌNH THỰC THI

1. **Bóc tách kịch bản (Text / Link Online):** Tự động đọc text hoặc cào ngầm nội dung từ URL (Google Docs, Google Sheets, Web) không cần cấp quyền browser.
2. **Khớp bối cảnh tham chiếu:** Sử dụng ảnh người dùng gửi hoặc ảnh mẫu AI làm seed gốc.
3. **Sinh & Đồng bộ ảnh lên R2:** Lưu trữ ảnh vào `r2:vietndjmedia/storyboards/[slug]/assets/`.
4. **Render HTML Studio & Cập nhật Master Hub:**
   - Biên dịch file HTML kịch bản chi tiết (gồm khối tin nhắn gốc, 15 beats, dải filmstrip, không box AI prompt).
   - Tự động cập nhật thẻ kịch bản mới vào Master Hub `index.html`.
5. **Deploy GitHub Pages & Gửi Tin Nhắn Telegram:**
   - Push lên repo `vietndj/offline02`.
   - Gửi tin nhắn siêu ngắn gọn về Telegram cho anh Việt gồm Tiêu đề và Link trực tuyến.

---

## 📁 4. VỊ TRÍ MÃ NGUỒN & TÀI NGUYÊN MASTER

* **Thư mục Repo GitHub:** `[đường-dẫn-Mac]`
* **Script Pipeline Chính:** `[đường-dẫn-Mac]`
* **Master Hub Index Builder:** `[đường-dẫn-Mac]`
* **Link Master Hub:** `https://vietndj.github.io/offline02/`
* **Cloudflare R2 Base:** `https://media.fedu.vn/storyboards/`