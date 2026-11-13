# Template ARC — Xuất HTML Thảo Luận Logic Kênh (`dinh-huong-kenh` V2.0)

## Hướng dẫn sử dụng

Khi cần xuất file `.md` phân tích logic kênh thành HTML bản thảo luận tương tác chuẩn 16 cổng (`G0..G15`), thay thế các biến trong template dưới rồi ghi vào `/tmp/arc_html_logickenh.md` và chạy:

> _(lệnh chạy trên Mac — đã lược khi lên Web)_

## Biến cần thay thế

| Biến | Ví dụ |
|:---|:---|
| `{TÊN_HỌC_VIÊN}` | Bùi Thị Hiền |
| `{NGÀNH}` | BĐS Hạ Long Xanh |
| `{ĐƯỜNG_DẪN_FILE_MD}` | `/tmp/logickenh_hien.md` |
| `{SLUG}` | `bui_thi_hien` |
| `{LED_ID}` | `3347` |
| `{ĐƯỜNG_DẪN_OUTPUT}` | `[đường-dẫn-Mac]` |

## Cấu trúc bắt buộc của HTML Bản Thảo Luận V2.0 (Đạt 16/16 Cổng)

1. **Khối Metadata `<!-- KENH_META ... -->` ở ngay sau `<!DOCTYPE html>`:**
   Sao chép nguyên vẹn khối `<!-- KENH_META ... -->` từ đầu file `.md` sang file `.html` (`san_pham`, `gia`, `chu_ky_suy_nghi`, `ap_dung_7h`, `giay_xem_tb`, `nguoi_thu_hai`, `kenh_rieng`, `gio_quay_tuan`).
2. **Đủ 3 Phần & 5 Mắt Xích Niềm Tin (`data-mx="1"` đến `data-mx="5"`):**
   - Phần A: Bài toán gốc, Số liệu kênh & 3 Bức tường của bài toán 7 Giờ (`420 phút`).
   - Phần B: 5 Section tương ứng với 5 Mắt Xích, gắn thuộc tính `data-mx="1"`, `data-mx="2"`, `data-mx="3"`, `data-mx="4"`, `data-mx="5"` trên thẻ `<section>` hoặc `<div class="section-card">`:
     - `data-mx="1"`: MX1 — Tư duy nền tảng (Bảng Tâm lý Gộp 4 tầng & Tầng 2.5 Thể diện + 3 Đầu ra Thời gian/Tiền bạc/Thể diện + Cheap Talk vs Costly Signaling).
     - `data-mx="2"`: MX2 — Vòng gửi xe 3 giây (2 trục Thỏa mãn Thị giác × Thỏa mãn Trí tuệ + Câu Hook Nhân hiệu mô tả vi mô trong ngoặc kép).
     - `data-mx="3"`: MX3 — Tích lũy giờ bay (Lộ trình 4 định dạng theo độ thoải mái của học viên).
     - `data-mx="4"`: MX4 — Đa dạng hóa 3 dòng nội dung để tích lũy đủ 7 tiếng (cấm dùng từ "xô").
     - `data-mx="5"`: MX5 — Diễn biến của 90% Người xem thầm lặng (Lurker) & Đường đi 84% Dark Social (nêu rõ `nguoi_thu_hai`, `kenh_rieng` và câu tin nhắn nguyên văn trong ngoặc kép).
   - Phần C: 3 Khung kịch bản thực địa & Bảng kê Điểm mù dữ liệu còn thiếu.
3. **Mỗi Section bắt buộc có đủ 3 khối tương tác (`G8`):**
   - `<div class="analysis-block">` (`🔍 Góc nhìn phân tích & Giả thuyết có lập luận`)
   - `<div class="question-block">` (`❓ Câu hỏi kiểm chứng thực tế cùng học viên` + `🔀 Phân nhánh Nếu A / Nếu B`)
   - `<div class="note-block" contenteditable="true">` (`💡 Ghi chú chốt tại buổi thảo luận` — tự lưu `localStorage`).
4. **Kiểm định tất định trước khi hoàn tất:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
   Bắt buộc đạt `"overall_pass": true` (0 từ cấm, 0 chữ `"FEDU"` trong văn bản hiển thị, 0 chữ `"xô"`).