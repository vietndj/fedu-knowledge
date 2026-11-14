---
name: spa-pa2
description: "Mantra: SPA PA2 / EDIT SPA PA2 / PHUONG AN 2 / EDIT VIDEO NAY THEO SPA PA2. Dựng video chuyên gia Spa PA2-V9.4 đa học viên (cắt vấp ẩn, giữ phụ đề nguyên bản, khóa thuật ngữ, poster theo từ neo, ngân sách đồ họa ≤20%, B-Roll thật chống trùng). SPA PA2 không kèm tên học viên → dùng skill này; riêng Hằng/Alice → dùng skill edit-hang."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `spa-pa2` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).


# 🎬 KỸ NĂNG EDIT VIDEO SPA PA2-V9.4 (`SPA-PA2` — HỆ CỔNG V9.4 CHUẨN EDITOR NGƯỜI THẬT)

> ⚡ **KỶ LUẬT SIÊU TIẾT KIỆM TOKEN & ĐỊNH TUYẾN HỌC VIÊN (`--who` & `--hook`):**
> 1. **CẤM TUYỆT ĐỐI** dùng `read_file` đọc mã nguồn trong `scripts/` hoặc đọc file kỹ thuật `plan.json`.
> 2. **CHỈ ĐỌC/SỬA** duy nhất file `<work_dir>/content.json` và luôn truyền cờ `--quiet-json`.
> 3. Truyền `--who "<tên học viên>"` để tự nạp Logo, Outro `Silk Ivory Atelier` + nút CTA riêng và nhớ Hook (`H0..H5`).

## 🚫 7 QUY TẮC SẮT ĐÁ KHI TỰ BIÊN TẬP `content.json` (`A6, T1, S1-S2, H1, P3, G7, B3`)
1. **BẢO TOÀN CẶP SỐ THỨ TỰ LIỆT KÊ (`A6 ENUM_INTEGRITY` & `S4 LIST_SECTION_ATOMIC`):**
   - Nếu trong bài người nói có câu *"Thứ hai..."* (VD: `T45`), bắt buộc trước đó trong `selected_take_ids` phải có câu chứa *"Thứ nhất..."* (VD: `T37`). **CẤM** cắt mất vế *"Thứ nhất"*.
   - **GIỮ NGUYÊN MỐC `start/end` CỦA `sections`:** Engine đã tự động căn ranh giới `Section 04` bắt đầu ngay tại câu dẫn nhập trước *"thứ nhất"* (VD: `31.52s`) để cả *"thứ nhất"* và *"thứ hai"* nằm trọn trong 1 chương mục. Chỉ sửa `title` của `sections`, **CẤM** sửa `start/end` làm cắt đôi danh sách liệt kê.
2. **KHÓA THUẬT NGỮ NGUYÊN BẢN & CHỐNG BỊA CHỮ HOA MỸ (`T1 TERM_LOCK` & `G7_DESC_GROUNDED`):**
   - Dùng đúng 100% thuật ngữ chuyên môn người nói phát âm trong bài (VD: người nói nói *"chân mày sợi"* và *"phun tan viền"* thì **TUYỆT ĐỐI CẤM** tự đổi thành *"điêu khắc sợi"* hay rút gọn sai nghĩa thành *"mặt nét"*).
   - **CẤM TỰ BỊA TỪ HOA MỸ TRÊN POSTER (`G7_DESC_GROUNDED`):** Mọi dòng `title`, `desc`, `detail`, `takeaway` trên `P1, P2, P3` bắt buộc lấy từ vựng có thật trong lời nói của nhân vật tại đúng đoạn đó. **TUYỆT ĐỐI CẤM** tự bịa các cụm từ sáo rỗng không có trong lời nói như *"thần thái"*, *"chiều sâu thanh thoát"*, *"tỷ lệ vàng"*, *"phong thủy"*, *"quý phái"*.
3. **PHỤ ĐỀ NGUYÊN BẢN, CHUẨN DẤU CÂU & CHỐNG RỚT 1 CHỮ MỒ CÔI (`S1 SUB_VERBATIM`, `S2 SUB_POLISH` & `SUB_ORPHAN`):**
   - Phụ đề `subs` (`l1, l2`) phải khớp $\ge 90\%$ từng từ với lời nói thật (`raw`). Chỉ sửa lỗi nhận diện ASR (như *"nữ nhân nè mà"* $\rightarrow$ *"nữ nhân nào mà"*, *"hơi, nhạt nhòa"* $\rightarrow$ *"hơi nhạt nhòa"*, thêm dấu phẩy ở mệnh đề phụ *"kinh nghiệm của Dung,"*, *"có tâm, có gu,"*). **CẤM** viết lại hay tóm tắt câu nói.
   - **CHỐNG RỚT 1 CHỮ (`SUB_ORPHAN`):** Khi câu phụ đề có $\ge 3$ từ, dòng 2 (`l2`) bắt buộc phải có $\ge 2$ từ. **TUYỆT ĐỐI CẤM** để 1 từ đơn lẻ (như *"ha"*, *"hơn"*, *"nhé"*) nằm trơ trọi ở dòng 2.
4. **ĐỒNG BỘ CHỮ IN HOA TRÊN HOOK (`H1 HOOK_CASE`):** Cả `h1_line1` và `h1_line2` (cùng `highlight`, `l1`, `kicker`) trong `hook` bắt buộc viết **IN HOA 100%** (VD: `h1_line1: "NÊN CHỌN CHÂN MÀY SỢI"`, `h1_line2: "HAY PHUN TAN VIỀN?"`). **CẤM** viết chữ thường ở `h1_line2`.
5. **CHỐNG LẶP NỘI DUNG GIỮA HAI POSTER & ĐẶT TIÊU ĐỀ BAO QUÁT (`P3 POSTER_NO_REPEAT`):** Hai Poster liên tiếp (`P1` và `P2`) phải có độ trùng từ khóa $< 55\%$:
   - **`P1` (`kind: "versus"`, `layout_mode: "fullscreen"`):** Đặt tại phần phân loại 2 nhóm gương mặt (VD: Khuôn mặt hơi nhạt nhòa $\rightarrow$ Phun tan viền tạo điểm nhấn sắc độ chuyển màu vs Khuôn mặt đã sắc nét $\rightarrow$ Chân mày sợi giúp đường nét hài hòa, tự nhiên hơn).
   - **`P2` (`kind: "criteria"`, `layout_mode: "split_aroll"`):** Đặt tại phần nguyên tắc thẩm mỹ kế tiếp (`24.5–31.5s`), chỉ tóm tắt đúng 3 ý của đoạn này (`01 MỌI ĐƯỜNG NÉT CẦN TƯƠNG TRỢ`, `02 CÁI GÌ QUÁ CŨNG KHÔNG ĐẸP`, `03 SỰ BỔ TRỢ VỪA ĐỦ RẤT HỢP LÝ`), **TUYỆT ĐỐI KHÔNG** lặp lại 2 ý phân loại mặt nhạt nhòa / mặt sắc nét của `P1` và không lấy trước ý của đoạn sau (`39s`).
   - **`P3` (`kind: "criteria"`, `layout_mode: "fullscreen"`):** Tiêu đề `title` phải bao quát cả 3 mục (VD: `"3 YẾU TỐ ĐỂ CÓ DÁNG MÀY ĐẸP"`, **CẤM** đặt là *"3 TIÊU CHÍ CHỌN NƠI UY TÍN"* khi mục 02 nói về sở thích cá nhân mỗi ngày nhìn gương). Ba mục: `01 ĐÚNG CHUẨN NÉT TỪNG PHƯƠNG PHÁP`, `02 ĐÚNG SỞ THÍCH MỖI NGÀY NHÌN GƯƠNG`, `03 CHỌN NGƯỜI CÓ TÂM, CÓ GU & BẢO HÀNH`.
6. **NHÃN B-ROLL TRUNG THỰC & KHÔNG LẶP TỪ (`B2 BROLL_DEDUP`, `B3 BROLL_LABEL_TRUTH` & `B3_NO_DUP_WORD`):**
   - Giữ nguyên `media_path` của các tư liệu B-Roll thật đã được Engine lọc chống trùng (`dHash >= 14`).
   - Trên các khe B-Roll thật (`B1, B2`), đặt `kicker: "TƯ LIỆU CẬN CẢNH"` và `headline: "CHI TIẾT ĐƯỜNG NÉT MÀY"` (không lặp từ `"THỰC TẾ"` hay `"CẬN CẢNH"` giữa `kicker` và `headline`, và **CẤM** lấy tiêu đề chương mục quản lý/cam kết đè lên cảnh cận cảnh).

## 🔄 QUY TRÌNH BẮT BUỘC 4 BƯỚC CHO MỌI VIDEO QUAY THÔ CỦA HỌC VIÊN

1. **Bước 1 — Tách sóng âm `A1..A6`, Quét đạo cụ mép `V3`, Lọc B-Roll chống trùng `B2` (`extract`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

2. **Bước 2 — Đọc `subs` trong `<work_dir>/content.json` & Tự Biên Tập Nội Dung (`hook, sections, posters, timeline_nodes, broll`):**
   - Đọc `<work_dir>/content.json`, dựa trực tiếp vào lời thoại `subs` để tự biên tập nội dung sắc nét, chuẩn chuyên môn cho:
     - `hook` (`h1_line1`, `h1_line2` IN HOA 100%, đặt câu hỏi/luận điểm mở bài đúng lời nói).
     - `sections` (4 tiêu đề chương mục ngắn gọn 4–6 chữ, đúng thuật ngữ `T1`, giữ nguyên `start/end` nguyên khối của Engine).
     - `posters` (`P1` versus fullscreen, `P2` criteria split_aroll khai thác ý 24.5–31.5s không lặp `P1`, `P3` criteria fullscreen tiêu đề bao quát đủ 3 yếu tố; chỉ dùng từ vựng có trong lời nói `G7_DESC_GROUNDED`; giữ nguyên `anchor_phrase`).
     - `timeline_nodes` (4 mốc tổng kết có `title` và `desc` trọn nghĩa 8–12 chữ).
     - `broll` (`B1, B2` giữ nguyên `media_path` thật, đặt `kicker: "TƯ LIỆU CẬN CẢNH"`, `headline: "CHI TIẾT ĐƯỜNG NÉT MÀY"`).

3. **Bước 3 — Chạy Cổng Kiểm Toán Tất Định (`audit`) Trước Khi Render:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
   Bắt buộc cả `v82_9_gates_pass: true` (`0` lỗi thị giác/cắt lề `L1`) và `v9_gates_pass: true` (`0` lỗi nội dung `A6, T1, S1, S2_SUB_ORPHAN, S4_LIST_SECTION_ATOMIC, H1, P2, P3, G7_DESC_GROUNDED, B1, B2, B3, V1`). Nếu có bất kỳ lỗi nào, sửa ngay trong `content.json` và chạy lại `audit` tới khi đạt `true`.

4. **Bước 4 — Kết xuất Video & Storyboard 12 Khung Hình (`render`):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
   Kiểm tra ảnh `<out>_preview_12frames.jpg` để nghiệm thu.

---
## ⚡ Chuẩn Chuyển Động 12 Nguyên Lý Tự Động (Motion Core V8)
- **Động cơ vật lý dùng chung:** Mọi chuyển động thẻ, chữ, huy hiệu, biểu đồ, nút CTA và Outro bắt buộc dùng `_vendor.motion_core` (đồng bộ từ `[đường-dẫn-Mac]`, hồ sơ `spa_atelier`: có lấy đà ngược chiều, lò xo 1 nhịp nảy, nén giãn `sx*sy=1`, lệch pha Cha–Con và thoát cảnh `9 frames`; cấm viết hàm easing bậc 3 đơn điệu cục bộ).
- **Hậu kiểm tự động (Chế độ Cảnh báo `--mode warn`):** Sau khi xuất `.mp4`, hệ thống tự chạy `[đường-dẫn-Mac] --video <out.mp4> --profile spa_atelier --mode warn` (exit `0` không chặn render, ghi chỉ số 12 nguyên lý vào `motion/self_learning_ledger.jsonl`).
