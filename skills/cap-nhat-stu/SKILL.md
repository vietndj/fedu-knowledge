---
name: cap-nhat-stu
description: "Cập nhật hoặc thêm mới Học viên / Khách gọi điện vào hệ thống STU (stu.fedu.vn) ngay từ Gemini Web (Zero-Docs). Kích hoạt khi anh Việt gửi Tên + SĐT / ghi chú cuộc gọi và bảo: cập nhật stu / thêm vào stu / update stu / lưu vào stu."
tier: A
---

# Kỹ năng: CẬP NHẬT HỌC VIÊN STU TỪ GEMINI WEB (`Gemini Web → stu.fedu.vn`, Khuôn `===PATCH===`)

Xưng "em", gọi "anh Việt". Khi anh Việt gửi thông tin người mới gọi điện, khách hàng hoặc học viên (Tên, SĐT, ngành nghề, vướng mắc, ghi chú…) và bảo **cập nhật / thêm vào hệ thống STU**, em thực hiện ngay không hỏi rườm rà:

## 1. Kiểm tra & Bóc tách thông tin
1. Nếu anh Việt chỉ đọc **SĐT** hoặc **tên ngắn** của người cũ mà chưa rõ tên đầy đủ, đối chiếu nhanh `STU_MUC_LUC` trong `AGY_BRIDGE/kho` qua `@Google Drive` nếu cần; nếu không tra được cũng không sao — máy Mac tự đối khớp thông minh theo SĐT/tên.
2. Các trường hỗ trợ (`name` hoặc `phone` bắt buộc có ít nhất 1):
   - `name`, `phone`, `industry`, `class`, `facebook_url`, `zalo_url`, `topic`, `inquiry`, `marketing_use`, `notes`.

## 2. Xuất khối `===PATCH===` ngay trong khung chat (0 gọi Google Docs, 0 lỗi JSON)
Dùng khuôn văn bản thuần bên dưới để viết `"ngoặc kép"` hay nhiều dòng ghi chú cuộc gọi thoải mái không bị gãy cú pháp:

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | cap-nhat-stu: <Tên học viên> ===
### NOTE: HANDOFF
- Cập nhật STU: <Tên học viên> (<Số điện thoại>)
### FILE: stu/<slug_khong_dau>.patch
===PATCH===
target: stu
op: update
---name---
<Tên học viên>
---phone---
<Số điện thoại>
---industry---
<Ngành nghề>
---class---
<Lớp hoặc nhóm>
---topic---
<Chủ đề trao đổi>
---inquiry---
<Vướng mắc của học viên>
---marketing_use---
<Hướng triển khai video>
---notes---
<Ghi chú chi tiết cuộc gọi / trao đổi, nhiều dòng thoải mái>
===END===
=== HẾT PHIÊN ===
```
*(Nếu thêm nhiều học viên 1 lúc, đặt nhiều khối `===PATCH=== ... ===END===` nối tiếp nhau trong cùng 1 file).*

## 3. Báo gọn trên khung chat (≤ 5 dòng phần đầu)
Tóm tắt 4 dòng thông tin vừa xuất (Tên · SĐT · Ngành/Lớp · Ghi chú), đặt khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` ngay bên dưới và chốt:
`Đã xuất hồ sơ STU — máy Mac (web_harvest) sẽ tự nạp lên stu.fedu.vn trong 60 giây (hoặc gõ VỀ MÁY để lên tức thì).`
