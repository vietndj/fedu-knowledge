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
Ghi **thêm vào cuối** Google Docs **`AGY_INBOX`** (thư mục `AGY_BRIDGE`; chưa có thì tạo). Không xóa phần cũ. Đúng khuôn sau (máy tách tự động theo các dấu `###`):

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
- Sau khi ghi xong, báo anh: "Đã ghi về máy — ở Antigravity gõ `VỀ MÁY`."
- Không ghi mật khẩu, token, PIN, số tài khoản vào Docs.

## 4. Nếu không truy cập được Google Docs
Xuất nguyên khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` trong chat để anh bấm Sao chép; ở Mac gõ `VỀ MÁY` (máy tự đọc clipboard).

## 5. Phân tích video — `PHÂN TÍCH VIDEO <mã>`
Mac đã tải video, cắt shot, đẩy ảnh lên kho ảnh và YouTube (em KHÔNG cắt ảnh).
1. Mở Google Docs `AGY_VIDEO_<mã>` trong `AGY_BRIDGE/video_jobs`.
2. Xem **video mp4 đính kèm trong chat** (Mac tự đính kèm). Link YouTube unlisted, link ảnh .webp, @Drive mp4 đều KHÔNG cho em thấy hình → nếu chưa có mp4 đính kèm thì nhờ anh bấm `+` → Thêm từ Drive → `AGY_BRIDGE/video_jobs/<mã>.mp4`. Không thấy hình thì KHÔNG CHỐT PHIÊN.
3. Soi từng shot theo đúng mốc giờ đã cho, áp kỹ năng `analyze-video` + luật few-shot trong Docs. In báo cáo ra chat.
4. `CHỐT PHIÊN` với đúng 2 FILE `video/<folder>/shots.json` và `video/<folder>/sync.json` (JSON thuần, đủ khóa, đúng số shot, id lấy trong danh mục đóng, sync có `"nguon_hinh": "video"`). Mac gõ `VỀ MÁY` là tự lên `ytuong.fedu.vn`.

## 6. Lưu kho — `LƯU KHO` / `lưu kho` / `CẤT KHO`
Áp kỹ năng `luu-kho` (V3 — 4 phần tự đóng chống cụt file): chưng cất cả luồng thành chuyên đề `logicXX` (2 câu thơ lục bát + Cẩm nang 5 chương + đúng 10 thẻ Hỏi-Đáp sắc nhất), ghi nối tiếp **4 khối tự đóng riêng biệt** `[1/4]..[4/4] key=K<MMDDHHMM>` vào cuối `AGY_INBOX` (`logicXX.meta.json` + `logicXX_kienthuc_p1.md` → `logicXX_kienthuc_p2.md` → `logicXX_hoidap_p1.md` → `logicXX_hoidap_p2.md`), mỗi khối đều kết thúc bằng `=== HẾT PHIÊN ===`. Chu trình sao lưu tối trên Mac (hoặc lệnh `VỀ MÁY` từ Remote Agent) sẽ tự ghép 4 mảnh, kiểm định và xuất bản lên `kho.fedu.vn` với 0 tốn token.

## 7. Tra cứu dữ liệu toàn hệ thống — Kho, Học viên STU, Web `fedu.vn`, Bối cảnh
Mỗi tối máy Mac tự động cập nhật dữ liệu mới vào thư mục Google Drive **`AGY_BRIDGE/kho`**. Khi anh Việt hỏi bất kỳ dữ liệu nào trong hệ thống, **tự mở đọc ngay file `00_TONG_DAI_FEDU`** (≤22KB) trong `AGY_BRIDGE/kho` bằng công cụ Google Drive mà không bắt anh đính kèm file:
- **Bối cảnh, khóa học, 4 định dạng video & `thcn`:** mở `BOICANH_MASTER_FEDU`.
- **Học viên, lớp K3/K4, tư vấn & khám kênh (`stu.fedu.vn`):** mở `STU_MUC_LUC` tìm dòng học viên để lấy số cuốn → mở đúng `STU_HO_SO_1..N`.
- **Kho Logic (`logic01..logicXX`), Giải mã cơ chế & Podcast:** mở `MUC_LUC_LOGIC_PODCAST` → mở `KHO_kien-thuc_*`, `KHO_hoi-dap_logicXX_1` hoặc `PODCAST_N`.
- **Bản đồ 15+ chuyên trang `fedu.vn` & tự động hóa:** mở `HE_THONG_WEB_FEDU`.
- **Video YouTube 90 ngày & lịch sử làm việc gần đây trên Mac:** mở `VIDEO30_MUC_LUC` hoặc `KHOAI_<YYYY-MM>` mới nhất.
