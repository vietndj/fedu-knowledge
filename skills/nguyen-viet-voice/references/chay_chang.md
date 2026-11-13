## ⚡ TẦNG 5: CƠ CHẾ `CHẠY CHẶNG` TẤT ĐỊNH (`chay_chang_helper.py` — CHỐNG BÃO HÒA ATTENTION & CHỐNG LẶP Ý GIỮA CÁC CHẶNG)

Khi viết kịch bản / bài viết đòi hỏi nhiều ràng buộc đan xen, nếu ép mô hình xuất $\ge 4$ bài trong cùng 1 bước thì từ bài thứ 4 trở đi *Attention Budget* bị bão hòa, dễ trôi về văn mẫu hoặc lặp lại cảnh mở đầu/phép so sánh của bài trước.

Ngay sau khi anh Việt đã duyệt ổn định 1–2 mẫu đầu tiên và hô Mantra **`CHẠY CHẶNG`** hoặc **`CHẠY CHẶNG TIẾP`** (giọng nói: *"chạy chặng"*, *"chạy theo chặng"*, *"chạy chặn"*, *"chạy trặng"*, *"chia chặng"*, *"lặp chặng"*, *"chốt khuôn chạy chặng"*, *"chạy chặng tiếp"*):
1. **Khởi tạo Sổ Cái (`init`):** Lưu tại `[đường-dẫn-Mac]` (không lưu `/tmp/` để `renhanh_capsule.py` tự động kế thừa khi sang trang):
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
2. **Lặp từng chặng (`next` $\rightarrow$ Viết `bai/<id>.md` $\rightarrow$ `check`):**
   - `chay_chang_helper.py next` tự động in lại **Khuôn Nén Recency ($\le 6$ dòng)** + danh sách **cảnh mở đầu & phép so sánh đã dùng** + tạo **biên nhận Bước 0 riêng (`receipts/<id>.json`)** cho từng bài (gỡ lỗi `RECEIPT_TOPIC_MISMATCH` khi chạy 10 bài khác chủ đề).
   - `chay_chang_helper.py check` kiểm định từng bài độc lập qua 4 tầng (`verify_voice.py`, `verify_3tang.py`, luật riêng của luồng, và chống trùng lặp `3-gram Jaccard >= 0.50`).
   - **Cầu chì Cache Cliff 195k:** Không dừng hỏi duyệt giữa các cặp; chỉ dừng duy nhất khi `check` báo chạm ngưỡng **YELLOW ($\ge 195\text{k}$)** để anh Việt nói `CHẠY CHẶNG TIẾP` sang trang mới chạy nốt.
3. **Gộp đích bằng script (`merge`):** Chạy `chay_chang_helper.py merge` để ghép các file `bai/<id>.md` đã PASS (cấm LLM gõ lại gây lệch chữ) và `git push` **1 lần duy nhất** ở cuối lượt.