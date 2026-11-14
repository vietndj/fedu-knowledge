# Chi Tiết 16 Cổng Kiểm Định Tất Định (`verify_logic_kenh.py` V2.0)

> _(lệnh chạy trên Mac — đã lược khi lên Web)_

- `G0_bai_toan_goc`: Có mức giá/quy mô + ngưỡng tin cậy + khai báo `ap_dung_7h` (phân định bán bằng view vs bán bằng niềm tin 7 giờ).
- `G1_du_lieu_hoac_tuyen_bo_thieu`: Có bảng số liệu thật HOẶC ghi rõ `"Chưa có dữ liệu kênh"` (chống bịa số liệu).
- `G2_nghich_ly_va_co_che`: Có lật nghịch lý + mật độ liên từ nhân quả thực chất $\ge 6.0 / 1.000$ từ (không đếm nhầm từ khuyên bảo `"nên"` đứng lẻ).
- `G3_giai_phau_kep_loi_ich_va_tam_ly`: Đạt đồng thời $\ge 2$ điểm chạm lý tính (lợi ích, dòng tiền, chi phí, phép so sánh) VÀ $\ge 2$ điểm chạm tâm lý 4 tầng (nỗi sợ gốc Tiền/Tình/Sự công nhận, lát cắt vi mô, thể diện).
- `G4_it_nhat_5_gia_thuyet`: Có $\ge 5$ giả thuyết tường minh gắn với bài toán gốc và 5 mắt xích.
- `G5_cau_hoi_kiem_chung_va_phan_nhanh`: Có $\ge 5$ câu hỏi kiểm chứng + $\ge 5$ cấu trúc phân nhánh (`Nếu ... thì ...`).
- `G6_ghi_nhan_du_lieu_con_thieu`: Có $\ge 3$ vị trí chỉ rõ dữ liệu còn thiếu / chưa biết.
- `G7_nguyen_viet_voice_zero_blacklist`: Gọi trực tiếp `verify_voice.py --mode giaima --no-receipt`, bắt buộc **0 từ cấm**.
- `G8_html_interactive_discussion_ui` *(chỉ cho `.html`)*: Đảm bảo đủ 3 khối `.analysis-block`, `.question-block`, `.note-block` (`contenteditable`).
- `G9_nam_mat_xich_niem_tin`: Đảm bảo ánh xạ đủ **5 Mắt Xích (`MX1..MX5` / `data-mx="1..5"`)** và mỗi mắt xích đều có Giả thuyết + Câu hỏi kiểm chứng + Phân nhánh.
- `G10_dien_bien_lurker_dark_social`: Trong `MX5` (hoặc toàn bài) có phân tích **90% Người xem thầm lặng (Lurker)** + chuỗi diễn biến nhiều chạm (`→` / `Chạm 1..5` / `video thứ`) + hành động **Dark Social** gửi riêng qua `kenh_rieng` cho `nguoi_thu_hai` kèm **câu nhắn nguyên văn trong ngoặc kép**.
- `G11_bai_toan_7_gio_va_3_buc_tuong`: (Khi `ap_dung_7h: co`) Có bài toán tích lũy **7 giờ (`420 phút` / `7-11-4`)**, phép tính thời lượng xem có gắn nhãn nguồn (`[số liệu kênh]` hoặc `[giả định]`), và đủ **3 Bức tường** (Toán học, Tâm lý chuyển khoản, Sức bền sản xuất).
- `G12_hai_truc_thi_giac_tri_tue_vong_gui_xe`: Có phân tích **Vòng gửi xe 3 giây** qua 2 trục **Thỏa mãn Thị giác (Chiếc hộp nhung)** × **Thỏa mãn Trí tuệ (Chiếc nhẫn vàng / Hook nhân hiệu mô tả vi mô trong ngoặc kép)**.
- `G13_tang_25_the_dien_costly_signaling_3_dau_ra`: Có đủ (1) **Tầng 2.5 Tráng men thể diện** kèm câu tự nói trong ngoặc kép, (2) **Costly Signaling (Tín hiệu đắt giá)** đối lập với Cheap Talk, (3) Đóng gói **3 Đầu ra** (`Thời gian`, `Tiền bạc`, `Thể diện`).
- `G14_chong_chep_ly_thuyet_giao_dieu`: Chặn chép nguyên văn từ `logickenh-xaykenh.html` và `cu/index.html` ($\le 3$ cụm 10 từ trùng), giới hạn nhắc tên `Nielsen`/`RadiumOne` ($\le 1$ lần), và bắt buộc mỗi mắt xích phải gắn với dữ liệu cụ thể của học viên (`san_pham`, `gia`, `nguoi_thu_hai`).
- `G15_zero_fedu_va_xo`: 0 lần xuất hiện chữ `"FEDU"` trong văn bản hiển thị và 0 lần dùng từ `"xô"` để chỉ nhóm nội dung.

---

## Chi Tiết Đầy Đủ Ví Dụ Minh Họa 5 Mắt Xích (`MX1`..`MX5`)

### Bước B1 — Mắt xích 1 (`MX1`): Tư duy nền tảng — Giải phẫu Tâm lý Gộp (Lợi ích/Dòng tiền × 4 Tầng Tâm lý) + 3 Đầu ra JTBD + Tín hiệu đắt giá (`Cổng G3 & G13`)
1. **Bảng Giải Phẫu Tâm Lý & Lợi Ích Hợp Nhất (Gộp 4 tầng tâm lý và bài toán lợi ích/dòng tiền vào 1 bảng duy nhất để không trùng lặp):**

| Tầng nhận thức & tính toán của khách | Nội dung giải phẫu cụ thể trong ngành của học viên |
|:---|:---|
| **1. Tầng 1 — Lời nói đãi bôi bề mặt** | Câu khách thường nói xã giao ngoài miệng hoặc câu quảng cáo văn mẫu đối thủ hay rao (ví dụ: *"Để anh chị tham khảo thêm"*, *"Cam kết chất lượng số 1"*). |
| **2. Tầng 2 — Lát cắt hành vi vi mô (3 giây thật)** | Một hành động vật lý cụ thể, nhỏ nhưng thật 100% mà khách làm khi đang loay hoay với vấn đề (ví dụ: *23h đêm zoom bản đồ quy hoạch*, *mở ngăn kéo giấu hợp đồng*, *ngồi nhìn cốc nước đá tan hết*). |
| **3. Tầng 3 — Nỗi sợ gốc rễ (`Tiền` / `Tình` / `Sự công nhận`) & Phép so sánh lợi ích/dòng tiền** | • **Nỗi sợ vô thức:** Sợ mất tiền tích cóp, sợ bị người nhà đánh giá, sợ hớ.<br/>• **Bài toán lợi ích / dòng tiền / phép so sánh ngầm:** Cùng số tiền đó (`gia`), khách đang ngầm đặt lên bàn cân so với lựa chọn nào (gửi tiết kiệm, mua hàng Shopee rẻ hơn 1/5, hay làm ở đối thủ)? |
| **4. Tầng 2.5 — Tráng men thể diện (Chiếc cớ đàng hoàng để mua không ngượng)** | Lý do khoa học / tài chính / trách nhiệm gia đình mà người bán cần trao cho khách để khách tự thuyết phục mình và nói với người nhà. **Bắt buộc viết nguyên văn 1 câu trong ngoặc kép `“...”`** mà khách sẽ dùng để nói với vợ/chồng/đồng nghiệp. |
| **5. Bằng chứng cần thấy & Chỗ vướng cuối cùng** | Con số thực địa, sổ ghi chép, phép thử vật lý hoặc cam kết thanh khoản/bảo hành nào tháo chốt cuối cùng trước khi ký/chuyển khoản? |


---

## PHỤ LỤC CHI TIẾT PHẦN C & ĐỊNH DẠNG ĐẦU RA
### PHẦN C — KHUNG KỊCH BẢN THỰC ĐỊA & BẢNG ĐIỂM MÙ DỮ LIỆU

#### Bước C1: 3 Khung kịch bản theo đầu vào thật (Không viết lời thoại văn mẫu)
- Đưa ra 3 khung kịch bản gắn với 3 dòng nội dung ở `MX4`, dựa trên **đầu vào có thật của học viên**:
  1. **Kịch bản 1 (Costly Signaling / Thao tác kiểm định thật):** 1 phép đo thực địa, 1 tờ bảng tính dòng tiền, hoặc 1 ca từ chối/can khách mua sai.
  2. **Kịch bản 2 (Storytelling 4 tầng & Tầng 2.5 Thể diện):** Lấy trực tiếp lát cắt hành vi vi mô và câu nói Tầng 2.5 ở `MX1`.
  3. **Kịch bản 3 (31 Vỏ Bọc / Giải đáp câu hỏi Dark Social):** Từ 1 câu hỏi thật khách hay nhắn Zalo lúc nửa đêm.
- Trình bày gọn 3 nhịp: `Mở đầu 3 giây (Thị giác + Câu Hook Nhân Hiệu)` → `Triển khai bằng chứng` → `Kết câu điềm tĩnh giữ thể diện cho khách`.

#### Bước C2: Bảng kê Điểm Chưa Biết & Dữ Liệu Còn Thiếu (`Cổng G6 — Tự nhận thức giới hạn`)
- Lập bảng tổng hợp **tất cả các dữ liệu mà mô hình hiện chưa biết** (chỉ người làm nghề thực tế mới có).
- **Bắt buộc có mặt 3 biến số thực địa** (nếu đầu vào chưa cung cấp): (1) Thời lượng xem trung bình thực tế (`giay_xem_tb`), (2) Người thứ hai nhận link trong Dark Social (`nguoi_thu_hai`), (3) Số giờ bấm máy mỗi tuần của học viên (`gio_quay_tuan`), cùng các điểm mù đặc thù của ngành.
- Cột bắt buộc: `STT` | `Dữ liệu đang thiếu / Câu hỏi cần kiểm chứng` | `Nếu thực tế là Phương án A → Hướng đi` | `Nếu thực tế là Phương án B → Đổi hướng thế nào`.

---

## 3. HAI ĐỊNH DẠNG ĐẦU RA BẮT BUỘC

1. **File 1 — Bản Phân Tích Logic (`.md`) dành riêng cho anh Việt:**
   - Có khối `<!-- KENH_META ... -->` ở đầu file.
   - Đầy đủ Phần A (`A1..A3`), Phần B (`MX1..MX5`), Phần C (`C1..C2`).
   - **CẤM TUYỆT ĐỐI** viết đoạn *"Câu anh Việt sẽ nói với học viên..."* hoặc *"Chuỗi tin nhắn Zalo mẫu gửi học viên"* trong cả file `.md` lẫn phản hồi trên khung Chat (anh Việt tự biết cách nói chuyện).
   - **CẤM TUYỆT ĐỐI** dùng các từ trong sổ đen `nguyen-viet-voice`, cấm từ `"FEDU"`, cấm gọi là `"xô"`.
   - **Trên khung Chat báo cáo anh Việt:** Thay toàn bộ chuỗi tin nhắn mẫu bằng **Tóm tắt hướng làm ($\le 220$ từ, 4 ý mộc mạc)**: (1) Giữ hướng nào & vì sao bỏ hướng khác; (2) Số thật trên kênh và bài vừa làm; (3) Chỗ dễ nản hoặc dễ vấp nhất nếu quay về thói quen cũ; (4) 2 việc cần xem tiếp ở mấy bài tới.

2. **File 2 — Bản Thảo Luận Tương Tác Trên Web (`.html`) dành cho anh Việt & Học viên cùng bàn:**
   - Xuất ra `[đường-dẫn-Mac]` và đồng bộ lên `stu.fedu.vn`.
   - Giao diện sáng chuẩn InkDoc (`#F8FAFC`), có khối `<!-- KENH_META ... -->` ở đầu HTML, và chia các section bao phủ đủ 5 mắt xích (`data-mx="1"` đến `data-mx="5"`).
   - Mỗi chủ đề bắt buộc có 3 khối class chuẩn để qua cổng `G8`:
     - `<div class="analysis-block">` (`🔍 Góc nhìn từ dữ liệu & giả thuyết logic`)
     - `<div class="question-block">` (`❓ Câu hỏi kiểm chứng thực tế cùng học viên` — kèm phân nhánh Nếu A / Nếu B)
     - `<div class="note-block" contenteditable="true">` (`💡 Ghi chú chốt tại buổi thảo luận` — tự động lưu `localStorage` trên trình duyệt và có nút **Copy toàn bộ biên bản thảo luận**).