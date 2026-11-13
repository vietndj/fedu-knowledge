# audit-viet-lai — Chi tiết Bước 0, 5 Phép Thử Cutter, Mẫu Đầu Ra & 11 Chốt Chặn Toán Học

> Phần tham chiếu tách từ `SKILL.md` (nội dung gốc giữ nguyên 100%).

<!-- gốc: SKILL.md dòng 30-37 -->
### BƯỚC 0: KIỂM KÊ CHẤT LIỆU & DỰNG KHUÔN ÂM BẢN (NEGATIVE MOLD)
1. **Mục tiêu & Người đọc:** Xác định người đọc là ai, đang hoài nghi điều gì. *(Nếu văn bản dưới 25 chữ hoặc đã đủ sắc: báo thẳng điểm tốt và chỉ đề xuất 1 chỉnh sửa nhỏ).*
2. **Chọn lọc 2–3 chi tiết đắt nhất (Chống nhồi số):**
   - Chỉ giữ lại **2–3 chi tiết/con số tạo lực thuyết phục mạnh nhất** từ bản gốc; **mỗi câu tối đa 3 con số**.
   - **Cắt thẳng tay thông tin hồ sơ khách hàng** (quy mô nhân sự, doanh thu, ngành nghề...) vì người đọc đã biết rõ về công ty của chính mình.
   - **Giữ nguyên nghĩa của con số gốc:** Con số dùng lại phải gắn đúng với sự việc trong bản gốc (cấm lấy số "3 tuần bỏ phần mềm" đổi nghĩa thành "3 tuần chuẩn hóa").
   - **Cấm tuyệt đối tự bịa số liệu hay thuật ngữ giải pháp:** Phần thao tác giải pháp hoặc số liệu còn thiếu trong bản gốc bắt buộc để thẻ `[CẦN BỔ SUNG: ...]` hoặc `[SỐ LIỆU: ...]`.
3. **Khuôn Âm Bản (Banality Baseline):** Liệt kê nhanh **3 ý hiển nhiên** mà ai nghe chủ đề cũng đoán được + **1 câu văn mẫu AI** dễ viết nhất. Mọi luận điểm ở bước sau trùng với Khuôn Âm Bản này bị loại ngay lập tức.

<!-- gốc: SKILL.md dòng 49-60 -->
### BƯỚC 3: CUTTER (GỌT 30–40% CHỮ THỪA) & ĐẤU LOẠI 5 PHÉP THỬ
Thực hiện một lượt **Subtractive Editing (Chỉ Xóa, Không Thêm Ý)**:
- Cắt 30–40% chữ thừa; xóa câu dạo đầu; xóa chữ đệm (*thực chất, chính vì vậy, về cơ bản*); xóa từ rào đón mơ hồ (*có thể nói, dường như, phần nào, tương đối, khá là, nhìn chung*); xóa sạch cấu trúc AI Punchy (*Sự thật là, Đây chính là, Không phải X mà là/do Y, Không chỉ... mà còn*, câu cụt $\le 5$ từ liên hoàn).
- Sát hạch qua **5 Phép Thử**:
  1. **So-What Test:** Người trong nghề đọc câu này có thấy thông tin/cơ chế mới không?
  2. **Brand-Swap Test (Áp thẳng vào câu mô tả giải pháp):** Câu nói về việc mình làm có chỉ rõ *ai làm gì, lúc nào* không? Nếu chung chung hoặc bản gốc chưa có $\rightarrow$ bắt buộc gắn `[CẦN BỔ SUNG: thao tác cụ thể]`.
  3. **Scroll-Stop Test:** Câu mở đầu có đi thẳng vào kết quả hoặc chi tiết đắt nhất (không nhồi số hồ sơ) không?
  4. **Anti-Hedge Red Team:** Rào đón đúng 1 lần bằng **điều kiện cụ thể** (*"Điều kiện là..."*), không dùng từ giảm nhẹ mơ hồ.
  5. **Read-Aloud Test (Đọc to lúc uống cà phê):** Đọc thành tiếng từng câu; câu nào ngượng miệng hoặc ghép từ sai ngữ pháp (kiểu *"đội ngũ doanh thu..."*) phải viết lại ngay.
- **Tổng hợp 2 Phương Án (Jaccard Bigram Overlap $\le 0.38$, cùng Core Claim):**
  - **Phương án 1 (Bản Chính — Điềm tĩnh & Sắc bén):** Mở từ chi tiết thật $\rightarrow$ Giải thích cơ chế vòng lặp khiến cách cũ thất bại $\rightarrow$ Chốt điều kiện & bước tiếp theo.
  - **Phương án 2 (Bản Táo Bạo — Cái giá rơi thẳng vào người đọc):** Đặt **cái giá phải trả / kỷ luật đánh đổi lên chính người đọc** (không đẩy sang nhân viên hay bên thứ ba) $\rightarrow$ Chốt bước tiếp theo.

<!-- gốc: SKILL.md dòng 64-108 -->
## 📋 ĐỊNH DẠNG ĐẦU RA TIÊU CHUẨN

```markdown
### 1. CHẨN ĐOÁN CỐT LÕI & KHUÔN ÂM BẢN
* **Mục tiêu & Người đọc:** [1 dòng ngắn gọn]
* **Khuôn Âm Bản đã loại bỏ:** [3 ý hiển nhiên + 1 câu văn mẫu AI đã chủ động tránh]
* **Điểm chết nặng nhất (Bệnh tư duy):** [Chỉ rõ bệnh tư duy + Trích dẫn nguyên văn: "..."]
* **Luận điểm sắc nhất (Core Claim):** "[1 câu ≤ 25 từ, cụ thể, có thể phản bác được]"
* **Ý phụ đã chủ động cắt bỏ (≥3 ý):** [Liệt kê ≥3 ý phụ / thông tin hồ sơ khách hàng đã bỏ]

---

### 2. HAI PHƯƠNG ÁN VIẾT LẠI (ĐÃ QUA CUTTER)

#### 🔹 Phương án 1: Bản Chính — Điềm tĩnh & Sắc bén (Theo cơ chế thật)
> "[Nội dung viết lại — giữ 2-3 chi tiết đắt nhất, ≤3 số/câu, bảo vệ đúng Core Claim, có bước tiếp theo]"
* **Điểm giữ lực & Hóa giải phản bác:** [1 dòng giải thích cơ chế + điều kiện biên đã cài vào câu]

#### 🔹 Phương án 2: Bản Táo Bạo — Cái giá rơi thẳng vào người đọc
> "[Nội dung viết lại — cùng Core Claim với Bản 1 nhưng đặt thẳng cái giá/kỷ luật đánh đổi lên chính người đọc]"
* **Điểm giữ lực & Hóa giải phản bác:** [1 dòng giải thích cái giá đánh đổi đã chỉ thẳng]

---

### 3. KHUYẾN NGHỊ CHỌN & ĐÁNH ĐỔI
* **Đề xuất dùng:** Phương án [1 hoặc 2]
* **Lý do & Cái giá đánh đổi:** [Khi nào dùng Bản 1, khi nào dùng Bản 2]
```

---

## 🛡️ CỔNG KIỂM ĐỊNH TẤT ĐỊNH v3.1 (11 CHỐT CHẶN TOÁN HỌC)

Trước khi xuất kết quả, bắt buộc chạy `[đường-dẫn-Mac]` để kiểm tra tự động:
1. **Quote thật 100%** trong bản gốc.
2. **Core Claim $\le 25$ từ**.
3. **Không phạt từ nối nhân quả** (*vì, do, nên, nhưng, nếu, khi*) và **không cộng điểm mật độ cho chữ số** (triệt tiêu động cơ nhồi số).
4. **Chống bịa số liệu & Cảnh báo số đổi nghĩa:** Mọi con số digit (ngoài thẻ `[SỐ LIỆU: ...]`) phải có trong bản gốc và giữ đúng đơn vị đi kèm.
5. **Chống nhồi số (`max_numbers_per_sentence <= 3`):** Mỗi câu tối đa 3 con số/khoảng số.
6. **0 cấu trúc AI Punchy** (*Sự thật là, Không phải [do/vì/là]... mà [là/do/vì], Không chỉ... mà còn*, $\ge 3$ câu cụt $\le 5$ từ liên tiếp).
7. **Kiểm soát từ rào đón (`HEDGE_WORDS`):** Mật độ $\le 1.5/100$ từ và không vượt quá bản gốc.
8. **0 từ sáo rỗng & chữ đệm (`FLUFF_PHRASES` = 0, gồm cả *"thực chất"*, *"chính vì vậy"*, *"về cơ bản"*)**.
9. **Độ phân kỳ phương án:** Jaccard Bigram Overlap $\le 0.38$ (trên cùng 1 luận điểm).
10. **Bảo toàn 2–3 chi tiết đắt nhất** hoặc sử dụng thẻ `[CẦN BỔ SUNG: ...]`.
11. **0 vi phạm Sổ Đen từ cấm** (`verify_voice.py`).