---
name: sua-du-lieu
description: "Sửa hoặc thêm mới dữ liệu hệ thống FEDU (túi mù K4, nhạc nền, kho thơ, video ý tưởng) ngay từ Gemini Web về máy Mac (Zero-Docs). Kích hoạt khi anh Việt bảo: sửa túi mù / thêm câu túi mù / sửa nhạc / sửa thơ / sửa ý tưởng / sua-du-lieu."
tier: A
---

# Kỹ năng: SỬA DỮ LIỆU 2 CHIỀU TỪ GEMINI WEB (`sua-du-lieu`, Zero-Docs)

Xưng "em", gọi "anh Việt". Khi anh Việt yêu cầu sửa nội dung hoặc thêm mới mục vào các kho dữ liệu (`tuimu`, `nhac`, `tho`, `ytuong`):

## 0. Bắt buộc đọc bản mới nhất qua `@Google Drive` trước khi xuất patch `update`
- Không dùng trí nhớ hay bản đính kèm cũ trong Gem khi lấy `base_hash`.
- Luôn gọi `@Google Drive` mở trực tiếp file mục tiêu trong `AGY_BRIDGE/GEM/` (theo bảng tên & Drive ID dưới đây), đọc dòng `PACK_VERSION: ...` ở đầu file và mã `hash=...` hiện tại của đúng ID đó:
  - `tuimu` → `TUIMU_212.txt` (ID: `1eJmHzFrYiryR3HEEogOjiNb_HpSRyYz9K62GsPw7Teg`)
  - `nhac` → `NHAC_871_PROMPT.txt` (ID: `1P-XdN9uck4knBl2DUEhNKKnaTpMCCzH6zm_p694d1Hk`)
  - `tho` → `THO_MUC_LUC.txt` (ID: `13tfac_eHn7g_895mz-1h98hE2e4XTaVfUq7PH2zAPYQ`)
  - `ytuong` → `YTUONG_MUC_LUC.txt` (ID: `1QaiNAAkpG7m50U47TSR-A6CYixEn1qXzkIKdv1-0ZJI`)
  - Tổng đài tra nhanh → `00_TONG_DAI.txt` (ID: `1TQnoNHtk1oEwshY3HYdWhQtTQBeYTWvDuqFbPfX5erU`)

## 1. Quy tắc an toàn bắt buộc
1. **Chỉ hỗ trợ `op = "update"` hoặc `"add"`** — **TUYỆT ĐỐI CẤM `delete`**.
2. **Bắt buộc kèm `base_hash`** khi `op = "update"`:
   - Với `tuimu`: lấy đúng mã `hash=...` in ở dòng tiêu đề `=== Q... | ... | hash=xxxxxxxxxx ===` trong file `TUIMU_212.txt` vừa đọc qua `@Google Drive`.
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

## 3. Báo gọn trên khung chat (≤ 6 dòng phần đầu)
Dòng đầu ghi rõ `PACK_VERSION: <dòng lấy từ đầu file vừa đọc>` (để xác nhận không đọc bản cũ), tiếp theo tóm tắt (`target · id · op · field`), đặt khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` ngay bên dưới và kết thúc bằng:
`Đã xuất bản vá dữ liệu — máy Mac (web_harvest) sẽ kiểm tra hash + bất biến và tự áp trong 120 giây.`
