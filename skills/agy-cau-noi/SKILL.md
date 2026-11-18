---
name: agy-cau-noi
description: "Cầu nối Antigravity ⇄ Gemini Web của anh Việt. Dùng khi anh nói: TIẾP VIỆC MÁY / LÀM TIẾP / NHẬN VIỆC / CHỐT PHIÊN / GHI VỀ MÁY / KẾT PHIÊN / LƯU KHO, hoặc khi anh hỏi dữ liệu trong kho, học viên STU, hệ thống web fedu.vn, bối cảnh của anh."
tier: A
---

# Kỹ năng: AGY CẦU NỐI (Gemini Web ⇄ Antigravity trên Mac)

Anh Việt dùng 2 nơi làm việc: **Antigravity trên Mac** (chạy code, render, ship web, Telegram) và **Gemini Web** (tư duy, kịch bản, viết code, phân tích). Kỹ năng này giữ bối cảnh liền mạch giữa 2 nơi. Xưng "em", gọi "anh Việt".

## 1. Đầu phiên — `TIẾP VIỆC MÁY` / `LÀM TIẾP` / `NHẬN VIỆC`
1. Mở Google Docs **`AGY_HANDOFF`** trong thư mục Drive `AGY_BRIDGE` (dùng công cụ Google Drive/Docs).
2. Tóm lại cho anh trong ≤ 6 dòng: mục tiêu, đã chốt, còn dở, bước tiếp theo, file liên quan.
3. Nếu handoff nhắc tới kỹ năng nào (vd `3-tang`, `motion`) → áp dụng kỹ năng đó. Bản đầy đủ của mọi kỹ năng nằm trong repo GitHub `vietndj/fedu-knowledge`, thư mục `skills/` (link raw: `https://raw.githubusercontent.com/vietndj/fedu-knowledge/main/skills/<tên>/SKILL.md`).
4. Hỏi đúng 1 câu nếu thiếu dữ kiện quyết định; còn lại làm luôn.

## 2. Trong phiên
- Làm trọn những gì Web làm được: kịch bản, bài viết, phân tích 3 tầng, định hướng kênh, HTML 1 file, code (Python/TS/Remotion/JSON spec).
- Việc chỉ Mac làm được (render video, ffmpeg, deploy, CDP, Telegram, Zalo, CapCut, Google Flow): **không giả vờ chạy**, mà soạn sẵn spec/code đầy đủ để máy chạy.

## 3. Cuối phiên — `CHỐT PHIÊN` / `GHI VỀ MÁY` / `KẾT PHIÊN`
**Luật Zero-Docs (mặc định, 0% dừng hỏi Xác nhận/Hủy):** TUYỆT ĐỐI KHÔNG tự ý gọi công cụ Google Docs (`AGY_INBOX` / `AGY_INBOX_CHUNG`) trừ khi anh Việt yêu cầu rõ *"ghi vào Google Docs"*. Thay vào đó, **in trực tiếp 1 khối tự đóng ngay ở cuối câu trả lời trong khung chat** để `web_harvest.py` trên Mac tự hút ngầm qua trình duyệt trong 120 giây (đúng khuôn sau để máy tách tự động theo các dấu `###`):

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | <tiêu đề ngắn> ===
### NOTE: HANDOFF
- Mục tiêu: ...
- Đã chốt: ...
- Còn dở: ...
- Bước tiếp cho Antigravity: <lệnh/việc cụ thể, vd: "render Scene3 bằng Remotion", "ship lên k.fedu.vn">
- Kỹ năng liên quan: ...
### FILE: <đường-dẫn-tương-đối/ten-file.ext>
<toàn bộ nội dung file, không rút gọn, không "..." >
### FILE: <file khác nếu có>
<nội dung>
=== HẾT PHIÊN ===
```

Luật ghi:
- Kịch bản/bài viết chốt → `### FILE: kichban/<slug>.md`. Code → đường dẫn đích dự kiến, vd `### FILE: motion/Scene3.tsx`.
- Mỗi file viết **đầy đủ**; không dùng ``` bao quanh nội dung file.
- Sau khi in xong khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` trong chat, báo gọn: "Đã chốt phiên ngay trên khung chat — máy Mac (`web_harvest`) tự thu hoạch trong 120 giây (hoặc gõ `VỀ MÁY` để lấy ngay)."
- Không ghi mật khẩu, API token, mã PIN hệ thống. Riêng **số điện thoại, Zalo, email liên hệ của học viên/khách hàng** khi cập nhật STU thì **ghi đầy đủ 100%, không che giấu**.

## 4. Nếu chạy ở chế độ khác hoặc cần kéo thủ công
Giữ nguyên khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` trong chat; ở Mac gõ `VỀ MÁY` để kéo tức thì (không phụ thuộc Google Docs Extension).

## 5. Phân tích video — `PHÂN TÍCH VIDEO <mã>`
Mac đã tải video, cắt shot, đẩy ảnh lên kho ảnh và YouTube (em KHÔNG cắt ảnh).
1. Mở Google Docs `AGY_VIDEO_<mã>` trong `AGY_BRIDGE/video_jobs`.
2. Xem **video mp4 đính kèm trong chat** (Mac tự đính kèm). Link YouTube unlisted, link ảnh .webp, @Drive mp4 đều KHÔNG cho em thấy hình → nếu chưa có mp4 đính kèm thì nhờ anh bấm `+` → Thêm từ Drive → `AGY_BRIDGE/video_jobs/<mã>.mp4`. Không thấy hình thì KHÔNG CHỐT PHIÊN.
3. Soi từng shot theo đúng mốc giờ đã cho, áp kỹ năng `analyze-video` + luật few-shot trong Docs. In báo cáo ra chat.
4. `CHỐT PHIÊN` với đúng 2 FILE `video/<folder>/shots.json` và `video/<folder>/sync.json` (JSON thuần, đủ khóa, đúng số shot, id lấy trong danh mục đóng, sync có `"nguon_hinh": "video"`). Mac gõ `VỀ MÁY` là tự lên `ytuong.fedu.vn`.

## 6. Lưu kho — `LƯU KHO` / `lưu kho` / `CẤT KHO`
Áp kỹ năng `luu-kho` (V5 Deep-Think): chưng cất cả luồng thành chuyên đề `logicXX` (Cẩm nang **3 mạch** + **7 thẻ Hỏi-Đáp** sắc nhất, bỏ mục đệm rườm rà), **LUÔN tách 2 lượt `[1/2]` (`meta.json` + `kienthuc.md` `<= 12 KB`) và `[2/2]` (`hoidap.md` `<= 15 KB`)** in trực tiếp trong khung chat để máy Mac tự hút qua trình duyệt. **TUYỆT ĐỐI KHÔNG gọi công cụ Google Docs (`AGY_INBOX` / `AGY_INBOX_CHUNG`).**

## 7. Tra cứu dữ liệu toàn hệ thống — Kho, Học viên STU, Danh bạ SĐT, Web `fedu.vn`, Bối cảnh
Mỗi tối (và ngay sau mỗi lần cập nhật STU) máy Mac tự động cập nhật dữ liệu vào thư mục Google Drive **`AGY_BRIDGE/kho`**. Khi anh Việt hỏi bất kỳ dữ liệu hay số điện thoại nào, **tự mở đọc ngay file `00_TONG_DAI_FEDU`** (≤20KB) trong `AGY_BRIDGE/kho`:
- **Học viên, Số điện thoại học viên/khách, lớp K3/K4, tư vấn & khám kênh (`stu.fedu.vn` & `led.fedu.vn`):** mở **`STU_MUC_LUC`** (có sẵn SĐT thật của 367 học viên + chỉ số cuốn `STU_HO_SO_1..N`). Nếu là người mới gọi điện / đăng ký web chưa vào STU, mở thêm **`LED_DANH_BA_KHACH`** (426+ danh bạ & SĐT).
- **Bối cảnh, khóa học, 4 định dạng video & `thcn`:** mở `BOICANH_MASTER_FEDU`.
- **Kho Logic (`logic01..logicXX`), Giải mã cơ chế & Podcast:** mở `MUC_LUC_LOGIC_PODCAST` → mở `KHO_kien-thuc_*`, `KHO_hoi-dap_logicXX_1` hoặc `PODCAST_N`.
- **Bản đồ 15+ chuyên trang `fedu.vn` & tự động hóa:** mở `HE_THONG_WEB_FEDU`.
- **Video YouTube 90 ngày & lịch sử làm việc gần đây trên Mac:** mở `VIDEO30_MUC_LUC` hoặc `KHOAI_<YYYY-MM>` mới nhất.

## 8. Cập nhật / Thêm mới Học viên vào STU — `cập nhật stu` / `update stu` / `thêm vào stu`
Khi anh Việt gửi SĐT + Tên + nội dung trao đổi và bảo cập nhật/thêm vào STU, áp kỹ năng `cap-nhat-stu` (Zero-Docs): **in thẳng 1 khối `=== AGY-PHIEN <YYYY-MM-DD HH:MM> | cap-nhat-stu: <Tên> ===`** chứa `### FILE: stu/<slug>.patch` (`===PATCH=== ... ===END===`, kết thúc bằng `=== HẾT PHIÊN ===`) ngay trong khung chat để `web_harvest.py` trên Mac tự nạp lên `stu.fedu.vn` trong 60 giây. **TUYỆT ĐỐI KHÔNG gọi Google Docs (`AGY_INBOX` / `AGY_INBOX_CHUNG`).**
