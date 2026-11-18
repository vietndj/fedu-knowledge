---
name: luu-kho
description: "Lưu kho từ Gemini Web về Mac (V5 Deep-Think). Kích hoạt khi anh Việt chốt câu cuối LƯU KHO / lưu kho / CẤT KHO: chưng cất cả cuộc trò chuyện thành 1 chuyên đề logicXX (Cẩm nang 3 mạch + 7 thẻ Hỏi-Đáp v3-claude), LUÔN tách 2 lượt [1/2] và [2/2] in trực tiếp trong khung chat để web_harvest.py trên Mac tự thu hoạch."
tier: A
---

# Kỹ năng: LƯU KHO V5 (Gemini Web → kho tri thức trên Mac, Luôn 2 Lượt)

Xưng "em", gọi "anh Việt". Khi anh gõ **`lưu kho`** (hoặc `LƯU KHO`, `CẤT KHO`) ở cuối một luồng, em chưng cất **toàn bộ cuộc trò chuyện này** thành 1 chuyên đề và xuất thẳng ngay trong khung chat. Không hỏi lại, trừ khi luồng quá ngắn (< 2 lượt có ý) thì báo "chưa đủ chất để lưu kho".

## 1. Chưng cất (dành 70% suy nghĩ cho bước này — chọn lọc sắc bén, bỏ phần thừa)
- **Đào tìm đúng 3 mạch tư duy xương sống** anh Việt và em đã mở ra (ba mạch, không phải năm — gộp các ý gần nhau, giữ lại xương cốt sắc nhất). Bỏ chào hỏi, lặp ý, phần sai đã sửa.
- Với mỗi mạch, tự hỏi: *"Nếu chỉ được nói 1 câu lật lại cách nghĩ cũ về mạch này, câu đó là gì?"* — đó chính là câu định nghĩa đậm.
- **Thu hoạch thơ Lục Bát gốc** có trong luồng. Giữ nguyên văn câu hay; sửa nhẹ câu lệch luật (lục 6 chữ, bát 8 chữ, chữ 6 câu lục vần chữ 6 câu bát). Thiếu thì sáng tác bằng vật thể sờ được (hạt mầm, dòng nước, thớ gỗ, vết đứt tay…).

## 2. Khuôn Giải Mã v3-claude (tinh gọn, Mac kiểm định tự động)

### Cẩm nang (3 mạch `# Mạch 1: …` đến `# Mạch 3: …`, tiêu đề mỗi mạch ≤ 18 từ):
Ngay dưới mỗi `# Mạch`:
1. 2 câu thơ Lục Bát mỏ neo: dòng `> *câu lục*` rồi dòng `> *câu bát*`.
2. 1 câu định nghĩa in đậm: `**[Chủ đề] không phải là [lầm tưởng]... mà là [bản chất].**`
3. 1 đoạn dẫn nhập ngắn từ trải nghiệm quen thuộc (2–4 câu).
4. Các mục con `### …` viết tự do — cơ chế tháo gỡ, câu chuyện thực tế, góc nhìn lật ngược. Viết theo mạch suy nghĩ tự nhiên, **KHÔNG ép khuôn cứng** kiểu "Chỗ kẹt / Cơ chế / Câu chuyện" nếu ý không vừa khuôn.
5. Cuối mỗi mạch ghi đúng 1 dòng nguồn: `> - 🎙️ **Nguồn:** Hội thoại Gemini · <YYYY-MM-DD>`

### Hỏi-Đáp (5–7 thẻ tinh lọc sắc nhất, không viết 10 thẻ loãng):
Mỗi thẻ đọc độc lập vẫn hiểu. Thứ tự 5 khối gọn:
1. `Hỏi: …` câu hỏi mở ≤ 18 từ (`Tại sao…` / `Làm sao…`).
2. 2 câu thơ mỏ neo `> *…*` / `> *…*` ngay dưới dòng Hỏi.
3. Câu định nghĩa in đậm `**… không phải là ... mà là ...**`.
4. `### Cơ chế chạy ngầm`: giải thích bản chất + 1 ví dụ đời thực cụ thể (3–8 dòng). **CẤM lặp khuôn "Bước 1→2→3" cho mọi thẻ và BỎ HẲN mục "Phân loại / Dấu hiệu nhận biết"** — mỗi thẻ phải tự chọn cách trình bày sắc nhất với cơ chế đó (so sánh, phản ví dụ, nhân-quả, liệt kê phản trực giác, hoặc phân tích liền mạch; không để 2 thẻ liên tiếp giống hệt cấu trúc diễn giải).
5. `### Làm ngay`: 1 việc làm được ngay dưới 3 phút, có số đo, kèm 1 dòng nguồn `> - 🎙️ **Nguồn:** Hội thoại Gemini · <YYYY-MM-DD>`.

**Luật cứng**: cấm bảng Markdown `|---|`. Cấm thuật ngữ hàn lâm và từ sáo (tối ưu hóa, chiến lược, chuyên gia, phễu, nỗi đau, khao khát, khơi gợi, bí quyết, đỉnh cao, tử huyệt, đòn bẩy, thực địa, biến số, chốt hạ, lầm tưởng, bản lề, định vị, trả bài, thần thái, làm màu, gồng cứng, đơ mắt, bắt sống). Không ghi chữ FEDU trong tiêu đề hay nội dung.

## 3. Xuất LUÔN 2 lượt (bắt buộc với mọi chuyên đề, không tự ước lượng kích thước)

- **TUYỆT ĐỐI KHÔNG gọi công cụ Google Docs (`AGY_INBOX` / `AGY_INBOX_CHUNG`)**.
- Giữ nguyên chữ **`logicXX`**. Không bọc code block ```` ``` ```` quanh `=== AGY-PHIEN` và không gắn comment `<!-- ... -->`.
- **LUÔN tách 2 lượt** (dù bài ngắn hay dài) với cùng mã `key=K<MMDDHHMM>`:

### Lượt [1/2] (xuất ngay khi anh Việt gõ `lưu kho` — giới hạn ≤ 12 KB):
Chỉ xuất `kho/logicXX.meta.json` và toàn bộ 3 mạch `kho/logicXX_kienthuc.md`, rồi **dừng ngay sau `=== HẾT PHIÊN ===`** (KHÔNG viết phần Hỏi-Đáp ở lượt này).

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | luu-kho [1/2] key=K<MMDDHHMM>: <Tên chuyên đề> ===
### NOTE: HANDOFF
- Mục tiêu: Lưu kho chuyên đề "<Tên chuyên đề>"
### FILE: kho/logicXX.meta.json
{"title": "<Tên ≤ 65 ký tự>", "subtitle": "<1 câu mô tả>", "tho": ["<câu lục>", "<câu bát>"], "pillar": "tam-ly|dinh-vi|kich-ban|case-study|van-hanh", "tags": "tag1, tag2, tag3", "icon": "🧭", "share_url": ""}
### FILE: kho/logicXX_kienthuc.md
<# Mạch 1 đến # Mạch 3 đầy đủ>
=== HẾT PHIÊN ===
```

### Lượt [2/2] (máy Mac tự nhắn tiếp sau ~18 giây — giới hạn ≤ 15 KB):
Xuất trọn 7 thẻ `kho/logicXX_hoidap.md` và đóng `=== HẾT PHIÊN ===`:

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | luu-kho [2/2] key=K<MMDDHHMM>: <Tên chuyên đề> ===
### FILE: kho/logicXX_hoidap.md
<Hỏi 1 đến Hỏi 7 đầy đủ>
=== HẾT PHIÊN ===
```

## 4. Sau khi hoàn tất mỗi lượt
- Phần đầu câu trả lời in gọn (≤ 8 dòng): 2 câu thơ tóm tắt + danh sách nội dung đã xuất.
- Dòng chốt lượt 1: `Đã xuất [1/2] — máy Mac sẽ tự nhắn tiếp để lấy [2/2] (7 thẻ Hỏi-Đáp).`
- Dòng chốt lượt 2: `Đã xuất [2/2] — web_harvest sẽ tự thu hoạch lên kho.fedu.vn và đồng bộ Drive ngay lập tức.`
