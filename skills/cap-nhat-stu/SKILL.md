---
name: cap-nhat-stu
description: "Cập nhật hoặc thêm mới Học viên / Khách gọi điện vào hệ thống STU (stu.fedu.vn) ngay từ Gemini Web. Kích hoạt khi anh Việt gửi Tên + SĐT / ghi chú cuộc gọi và bảo: cập nhật stu / thêm vào stu / update stu / lưu vào stu."
tier: A
---

# Kỹ năng: CẬP NHẬT HỌC VIÊN STU TỪ GEMINI WEB (`Gemini Web → stu.fedu.vn`)

Xưng "em", gọi "anh Việt". Khi anh Việt gửi thông tin người mới gọi điện, khách hàng hoặc học viên (Tên, Số điện thoại, ngành nghề, vướng mắc, ghi chú…) và bảo **cập nhật / thêm vào hệ thống STU**, em thực hiện ngay không hỏi rườm rà:

## 1. Kiểm tra & Bóc tách thông tin
1. Nếu anh Việt chỉ đọc **SĐT** hoặc **tên ngắn** của người cũ mà chưa rõ tên đầy đủ (ví dụ *"thêm ghi chú vào stu cho 0382114640"* hoặc *"update thêm cho Oanh Hữu Bằng"*), hãy mở nhanh Google Docs **`STU_MUC_LUC`** (hoặc `LED_DANH_BA_KHACH`) trong thư mục Drive `AGY_BRIDGE/kho` để lấy đúng `id` và tên chuẩn của học viên đó. Nếu là người mới gọi lần đầu, ghi thẳng thông tin mới luôn.
2. Chuẩn hóa gọn các trường JSON (trường nào chưa có thì bỏ qua hoặc để chuỗi rỗng `""`):
   - `name` *(bắt buộc)*: Họ tên / cách gọi rõ nhận diện (vd: `"K4 - Anh Tuấn Gỗ Đồng Kỵ"` hoặc `"Nguyễn Minh Tuấn"`).
   - `phone`: Số điện thoại viết liền (vd: `"0912345678"`).
   - `industry`: Ngành nghề / sản phẩm kinh doanh (vd: `"Xưởng sản xuất đồ gỗ Đồng Kỵ"`).
   - `class`: Lớp học hoặc nhóm (vd: `"Offline 4"`, `"Lead Điện Thoại"`, `"Tư Vấn Zalo"`).
   - `facebook_url` / `zalo_url`: Link kênh nếu anh Việt gửi kèm.
   - `topic`: Chủ đề cuộc gọi / buổi trao đổi ngắn gọn (vd: `"Gọi điện tư vấn lộ trình Offline K4"`).
   - `inquiry`: Chỗ vướng mắc thực tế khách vừa chia sẻ.
   - `marketing_use`: Hướng làm video phù hợp theo 4 định dạng của anh Việt (nếu đã bàn tới).
   - `notes`: Toàn bộ chi tiết thực tế cần nhớ (thời điểm gọi, hẹn đóng học phí, người đi cùng, đặc điểm xưởng/tiệm…).

## 2. Ghi gói JSON vào cuối Google Docs `AGY_INBOX`
Nối thêm **vào cuối** Google Docs **`AGY_INBOX`** (trong thư mục Drive `AGY_BRIDGE`, tuyệt đối không xóa nội dung cũ ở trên) theo đúng khuôn sau:

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | cap-nhat-stu: <Tên học viên> ===
### NOTE: HANDOFF
- Cập nhật STU: <Tên học viên> (<Số điện thoại>)
### FILE: stu/<slug_khong_dau>.json
{
  "name": "<Tên học viên>",
  "phone": "<Số điện thoại>",
  "industry": "<Ngành nghề>",
  "class": "<Lớp hoặc nhóm>",
  "facebook_url": "",
  "topic": "<Chủ đề trao đổi>",
  "inquiry": "<Vướng mắc của học viên>",
  "marketing_use": "<Hướng triển khai video>",
  "notes": "<Ghi chú chi tiết cuộc gọi / trao đổi>"
}
=== HẾT PHIÊN ===
```
*(Nếu anh Việt gửi 1 lúc nhiều người mới, có thể đặt mảng JSON `[ {...}, {...} ]` trong 1 file `stu/batch_update.json`, không bọc dấu ``` quanh JSON).*

## 3. Báo gọn trên khung chat (≤ 6 dòng)
Tóm tắt 4 dòng thông tin vừa ghi (Tên · SĐT · Ngành/Lớp · Ghi chú) và báo:
`Đã ghi hồ sơ vào AGY_INBOX — máy Mac sẽ tự động nạp lên stu.fedu.vn và cập nhật lại sổ Drive trong nhịp quét 15 phút (hoặc gõ VỀ MÁY để lên tức thì).`
