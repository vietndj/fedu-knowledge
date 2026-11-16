---
name: sua-du-lieu
description: "Sửa hoặc thêm mới dữ liệu hệ thống FEDU (túi mù K4, nhạc nền, kho thơ, video ý tưởng) ngay từ Gemini Web về máy Mac (Zero-Docs). Kích hoạt khi anh Việt bảo: sửa túi mù / thêm câu túi mù / sửa nhạc / sửa thơ / sửa ý tưởng / sua-du-lieu."
tier: A
---

# Kỹ năng: SỬA DỮ LIỆU 2 CHIỀU TỪ GEMINI WEB (`sua-du-lieu`, Zero-Docs)

Xưng "em", gọi "anh Việt". Khi anh Việt yêu cầu sửa nội dung hoặc thêm mới mục vào các kho dữ liệu (`tuimu`, `nhac`, `tho`, `ytuong`):

## 1. Quy tắc an toàn bắt buộc
1. **Chỉ hỗ trợ `op = "update"` hoặc `"add"`** — **TUYỆT ĐỐI CẤM `delete`**.
2. **Bắt buộc kèm `base_hash`** khi `op = "update"`:
   - Với `tuimu`: lấy đúng mã `hash=...` in ở dòng tiêu đề `=== Q... | ... | hash=xxxxxxxxxx ===` trong file `TUIMU_212.txt`.
   - Với `nhac`, `tho`, `ytuong`: cung cấp `base_hash` là 10 ký tự đầu SHA-1 của giá trị cũ (hoặc nếu anh Việt chỉ sửa nội dung từ file Gem, đối chiếu đúng ID trước khi xuất).
3. **Các trường hợp lệ (`field`)**:
   - `tuimu`: `question`, `answer`, `cat` (hoặc `op: "add"` với `new: {"cat": "...", "question": "...", "answer": "..."}`).
   - `nhac`: `title`, `category`, `bpm`, `archetype_label`, `vocal_tag`, `instruments_vi`, `note_personality`, `note`, `prompt`.
   - `tho`: `suite`, `category`, `poem`, `explanation`, `quote`.
   - `ytuong`: `title_vi`, `quick_takeaway`, `key_tech`, `purpose`, `practice_drill`.

## 2. Xuất thẳng khối JSON ngay trong khung chat (0 lần gọi Google Docs)
- **TUYỆT ĐỐI KHÔNG gọi Google Docs (`AGY_INBOX`)** trừ khi anh Việt yêu cầu rõ.
- In thẳng khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` ở cuối câu trả lời (không bọc dấu ```` ``` ```` quanh JSON):

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | sua-du-lieu: <Mô tả ngắn> ===
### NOTE: HANDOFF
- Vá dữ liệu <target>: <id> (<op>)
### FILE: patch/<slug>.json
[
  {
    "target": "tuimu",
    "op": "update",
    "id": "Q01",
    "field": "question",
    "new": "<Nội dung mới>",
    "base_hash": "<hash_10_ký_tự_từ_TUIMU_212>"
  }
]
=== HẾT PHIÊN ===
```

## 3. Báo gọn trên khung chat (≤ 5 dòng phần đầu)
Tóm tắt thay đổi (`target · id · op · field`), đặt khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` ngay bên dưới và kết thúc bằng:
`Đã xuất bản vá dữ liệu — máy Mac (web_harvest) sẽ kiểm tra hash + bất biến và tự áp trong 120 giây.`
