---
name: luu-kho
description: "Lưu kho từ Gemini Web về Mac. Kích hoạt khi anh Việt chốt câu cuối LƯU KHO / lưu kho / CẤT KHO: chưng cất cả cuộc trò chuyện thành 1 chuyên đề logicXX (2 câu thơ Lục Bát tóm tắt + Cẩm nang 5 chương + 10–15 thẻ Hỏi-Đáp theo Khuôn Giải Mã v3-claude), ghi vào Google Docs AGY_INBOX để Mac tự dựng logicXX.html và đẩy lên kho tri thức."
tier: A
---

# Kỹ năng: LƯU KHO (Gemini Web → kho tri thức trên Mac)

Xưng "em", gọi "anh Việt". Khi anh gõ **`lưu kho`** (hoặc `LƯU KHO`, `CẤT KHO`) ở cuối một luồng, em chưng cất **toàn bộ cuộc trò chuyện này** thành 1 chuyên đề và ghi về máy. Không hỏi lại, trừ khi luồng quá ngắn (< 3 lượt có ý) thì báo "chưa đủ chất để lưu kho".

## 1. Chưng cất (làm trong đầu trước khi viết)
- Lọc ra 5 mạch tư duy chính anh Việt và em đã đào. Bỏ chào hỏi, lặp ý, phần sai đã sửa.
- **Thu hoạch 100% thơ Lục Bát gốc** có trong luồng làm mỏ neo. Giữ nguyên văn câu hay; sửa nhẹ câu lệch luật (lục 6 chữ, bát 8 chữ, chữ 6 câu lục vần chữ 6 câu bát). Thiếu thì sáng tác mới bằng vật thể sờ thấy được (hạt mầm, dòng nước, thớ gỗ, vết đứt tay…).
- Viết **2 câu thơ Lục Bát tóm tắt cả chuyên đề**, đặt ở đầu.

## 2. Khuôn Giải Mã v3-claude (bắt buộc, Mac kiểm định tự động)
**Cẩm nang (file `_kienthuc.md`)**: đúng 5 chương `# Chương 1: …` đến `# Chương 5: …`. Ngay dưới mỗi `# Chương`:
1. 2 câu thơ mỏ neo: dòng `> *câu lục*` rồi dòng `> *câu bát*`.
2. 1 câu định nghĩa in đậm: `**[Chủ đề] không phải là [lầm tưởng]... mà là [bản chất].**` rồi 1 đoạn dẫn nhập từ trải nghiệm quen thuộc.
3. Các mục con `### …` ngắn, đời thường, từ nông đến sâu. Chương 1 mở bằng `### Bối cảnh cho người mới bắt đầu`, sau đó `### Mạch 1` đến `### Mạch 5`. Mỗi mạch 3 lớp: Chỗ người mới hay kẹt → Cơ chế tháo gỡ → Câu chuyện thực tế để nhớ (kể trọn nhân quả, cấm viết tắt kiểu mật mã `A → B`).
4. Cuối chương có chân trang nguồn: `> - 🎙️ **Nguồn:** …` / `> - 💬 **Bản giải phẫu gốc:** https://fedu.vn/k/logicXX.html` / `> - 📍 **Bối cảnh:** …`.

**Hỏi-Đáp (file `_hoidap.md`)**: 10–15 thẻ, mỗi thẻ đọc độc lập vẫn hiểu. Thứ tự 6 khối:
1. `Hỏi: …` câu hỏi mở ≤ 18 từ (`Tại sao…` / `Làm sao…`).
2. 2 câu thơ mỏ neo `> *…*` / `> *…*` ngay dưới dòng Hỏi.
3. Câu định nghĩa in đậm `**… không phải là ... mà là ...**`.
4. `### Cơ chế chạy ngầm`: bản chất + lý do + chuỗi `Bước 1 → Bước 2 → Bước 3` + `Ví dụ:` đời thực.
5. `### Phân loại / Dấu hiệu nhận biết` (hoặc `### Hai góc nhìn đời thường`): 2–3 dạng thực tế.
6. `### Làm ngay`: 1 việc làm được ngay, có số đo. Kèm chân trang nguồn như trên.

**Luật cứng**: cấm bảng Markdown `|---|`. Cấm thuật ngữ hàn lâm (Superposition, Negentropy, Mimetic desire, Costly signaling, tư duy kỹ trị…). Thuật ngữ tiếng Anh phải mở ngoặc giải nghĩa tiếng Việt bình dân. Áp giọng văn kỹ năng `vanphong`. Không ghi chữ FEDU trong tiêu đề hay nội dung, chỉ link `https://fedu.vn/k/...` ở chân trang.

## 3. Ghi về máy (CHỐT PHIÊN vào Google Docs `AGY_INBOX`)
Giữ nguyên chữ **`logicXX`** (2 chữ X in hoa), Mac tự cấp số thật. Nối vào **cuối** Docs `AGY_INBOX` đúng khuôn dưới. Nội dung dài thì ghi **lần lượt 3 lần nối** theo đúng thứ tự (lần 1: header + meta; lần 2: kienthuc; lần 3: hoidap + dòng HẾT PHIÊN). Không bọc nội dung file bằng ```.

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | luu-kho: <Tên chuyên đề> ===
### NOTE: HANDOFF
- Mục tiêu: Lưu kho chuyên đề "<Tên chuyên đề>"
- Thơ tóm tắt: <câu lục> / <câu bát>
- Bước tiếp cho Antigravity: cau ve (tự dựng logicXX.html + đẩy kho)
- Kỹ năng liên quan: luu-kho, kho-logic, vanphong
### FILE: kho/logicXX.meta.json
{"title": "<Tên chuyên đề ≤ 70 ký tự>", "subtitle": "<1 câu mô tả>", "tho": ["<câu lục>", "<câu bát>"], "pillar": "tam-ly|dinh-vi|kich-ban|case-study|van-hanh", "tags": "tag1, tag2, tag3", "icon": "🧭", "share_url": "<link chia sẻ luồng nếu có, không thì để trống>"}
### FILE: kho/logicXX_kienthuc.md
<5 chương đầy đủ>
### FILE: kho/logicXX_hoidap.md
<10–15 thẻ đầy đủ>
=== HẾT PHIÊN ===
```

Mac sẽ tự dựng `logicXX.html` theo giao diện InkDoc chuẩn, nên em **không cần viết HTML**. Trường hợp anh dặn riêng "xuất HTML", thêm `### FILE: kho/logicXX.html` (1 file HTML hoàn chỉnh, có `<h1>`, `<section id="phan-1-ban-do">`, `<section id="phan-2-bo-the">`). Mac chỉ dùng bản này khi thiếu 2 file .md.

## 4. Sau khi ghi
- In ra chat: 2 câu thơ tóm tắt + mục lục 5 chương + danh sách câu Hỏi (1 dòng/câu).
- Báo: "Đã ghi về máy — ở Mac gõ `cau ve`."
- Không ghi được Docs thì in nguyên khối `=== AGY-PHIEN … === HẾT PHIÊN ===` trong chat để anh bấm Sao chép. Mac gõ `cau ve` sẽ tự đọc clipboard.
