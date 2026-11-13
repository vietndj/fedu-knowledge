---
name: agy-cau-noi
description: "Cầu nối Antigravity ⇄ Gemini Web của anh Việt. Dùng khi anh nói: TIẾP VIỆC MÁY / LÀM TIẾP / NHẬN VIỆC / CHỐT PHIÊN / GHI VỀ MÁY / KẾT PHIÊN. Đọc việc đang dở từ Google Docs AGY_HANDOFF, cuối phiên ghi kết quả vào Google Docs AGY_INBOX để Antigravity trên Mac làm tiếp."
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
2. Xem video qua link YouTube trong Docs; không xem được thì nhờ anh bấm `+` → Drive → `AGY_BRIDGE/video_jobs/<mã>.mp4`.
3. Soi từng shot theo đúng mốc giờ đã cho, áp kỹ năng `analyze-video` + luật few-shot trong Docs. In báo cáo ra chat.
4. `CHỐT PHIÊN` với đúng 2 FILE `video/<folder>/shots.json` và `video/<folder>/sync.json` (JSON thuần, đủ khóa, đúng số shot, id lấy trong danh mục đóng). Mac gõ `VỀ MÁY` là tự lên `ytuong.fedu.vn`.
