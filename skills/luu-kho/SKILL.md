---
name: luu-kho
description: "Lưu kho từ Gemini Web về Mac (V4 Zero-Docs). Kích hoạt khi anh Việt chốt câu cuối LƯU KHO / lưu kho / CẤT KHO: chưng cất cả cuộc trò chuyện thành 1 chuyên đề logicXX (2 câu thơ Lục Bát tóm tắt + Cẩm nang 5 chương + 10 thẻ Hỏi-Đáp theo Khuôn Giải Mã v3-claude), in trực tiếp 1 khối === AGY-PHIEN ... === HẾT PHIÊN === ngay trong khung chat (0 lần gọi Google Docs) để web_harvest.py trên Mac tự thu hoạch trong 120 giây."
tier: A
---

# Kỹ năng: LƯU KHO V4 (Gemini Web → kho tri thức trên Mac, 0 Google Docs)

Xưng "em", gọi "anh Việt". Khi anh gõ **`lưu kho`** (hoặc `LƯU KHO`, `CẤT KHO`) ở cuối một luồng, em chưng cất **toàn bộ cuộc trò chuyện này** thành 1 chuyên đề và xuất thẳng ngay trong khung chat. Không hỏi lại, trừ khi luồng quá ngắn (< 2 lượt có ý) thì báo "chưa đủ chất để lưu kho".

## 1. Chưng cất (làm trong đầu trước khi viết)
- Lọc ra 5 mạch tư duy chính anh Việt và em đã đào. Bỏ chào hỏi, lặp ý, phần sai đã sửa.
- **Thu hoạch 100% thơ Lục Bát gốc** có trong luồng làm mỏ neo. Giữ nguyên văn câu hay; sửa nhẹ câu lệch luật (lục đúng 6 chữ, bát đúng 8 chữ, chữ 6 câu lục vần chữ 6 câu bát). Thiếu thì sáng tác mới bằng vật thể sờ thấy được (hạt mầm, dòng nước, thớ gỗ, vết đứt tay…).
- Viết **2 câu thơ Lục Bát tóm tắt cả chuyên đề**, đặt ở đầu.

## 2. Khuôn Giải Mã v3-claude (bắt buộc, Mac kiểm định tự động)
**Cẩm nang (5 chương `# Chương 1: …` đến `# Chương 5: …`, tiêu đề mỗi chương ≤ 18 từ)**: Ngay dưới mỗi `# Chương`:
1. 2 câu thơ mỏ neo: dòng `> *câu lục*` rồi dòng `> *câu bát*`.
2. 1 câu định nghĩa in đậm (giữ nguyên dấu `**`): `**[Chủ đề] không phải là [lầm tưởng]... mà là [bản chất].**` rồi 1 đoạn dẫn nhập từ trải nghiệm quen thuộc.
3. Các mục con `### …` ngắn, đời thường, từ nông đến sâu. Chương 1 mở bằng `### Bối cảnh cho người mới bắt đầu`, sau đó `### Mạch 1` đến `### Mạch 5`. Mỗi mạch 3 lớp: `- **Chỗ người mới hay kẹt:** ...` / `- **Cơ chế tháo gỡ:** ...` / `- **Câu chuyện thực tế để nhớ:** ...` (kể trọn nhân quả, viết đầy đủ chiều sâu, không ép cắt cụt hay viết tắt kiểu mật mã).
4. Cuối chương có chân trang nguồn: `> - 🎙️ **Nguồn:** …` / `> - 💬 **Bản giải phẫu gốc:** https://fedu.vn/k/logicXX.html` / `> - 📍 **Bối cảnh:** …`.

**Hỏi-Đáp (chốt đúng 10 thẻ tinh lọc sắc nhất)**: Mỗi thẻ đọc độc lập vẫn hiểu. Thứ tự 6 khối:
1. `Hỏi: …` câu hỏi mở ≤ 18 từ (`Tại sao…` / `Làm sao…`).
2. 2 câu thơ mỏ neo `> *…*` / `> *…*` ngay dưới dòng Hỏi.
3. Câu định nghĩa in đậm `**… không phải là ... mà là ...**`.
4. `### Cơ chế chạy ngầm`: chuỗi `- **Bước 1 — ...:**` → `- **Bước 2 — ...:**` → `- **Bước 3 — ...:**` + `- **Ví dụ:**` đời thực.
5. `### Phân loại / Dấu hiệu nhận biết`: 2–3 dạng thực tế.
6. `### Làm ngay`: 1 việc làm được ngay dưới 3 phút, có số đo. Kèm chân trang nguồn như trên.

**Luật cứng**: cấm bảng Markdown `|---|`. Cấm thuật ngữ hàn lâm và từ sáo (tối ưu hóa, chiến lược, chuyên gia, phễu, nỗi đau, khao khát, khơi gợi, bí quyết, đỉnh cao, tử huyệt, đòn bẩy, thực địa, biến số, chốt hạ, lầm tưởng, bản lề, định vị, trả bài, thần thái, làm màu, gồng cứng, đơ mắt, bắt sống…). Không ghi chữ FEDU trong tiêu đề hay nội dung, chỉ link `https://fedu.vn/k/...` ở chân trang.

## 3. Xuất thẳng ra khung chat (0 lần gọi Google Docs, tự động chia 2 phần khi dữ liệu lớn)
- **TUYỆT ĐỐI KHÔNG gọi công cụ Google Docs (`AGY_INBOX` / `AGY_INBOX_CHUNG`)**.
- Giữ nguyên chữ **`logicXX`**. Viết trọn vẹn, sắc nét (đủ ý, đủ câu chuyện thực tế) để `web_harvest.py` trên Mac tự hút ngầm qua RPC trong vòng **30 giây** và đồng bộ tức thì lên `kho.fedu.vn` + sổ cố định `01_KHO_MOI_NHAT` trên Google Drive.
- **Quy tắc chống cắt cụt khi dữ liệu lớn (> 6 lượt sâu hoặc tổng chuyên đề ước tính > 35 KB):**
  - **Chuyên đề vừa (≤ 35 KB):** Xuất trọn vẹn 1 khối duy nhất như mẫu dưới đây.
  - **Chuyên đề dài (> 35 KB — rất nhiều ví dụ, case study hoặc > 10 thẻ Hỏi-Đáp):** BẮT BUỘC chủ động chia 2 lượt an toàn (không nhồi cả 60 KB vào 1 lượt tránh bị cắt mất `=== HẾT PHIÊN ===`):
    + **Lượt này (ngay khi anh gõ `lưu kho`):** Xuất trọn vẹn Khối **`[1/2] key=K<MMDDHHMM>`** gồm `kho/logicXX.meta.json` và toàn bộ 5 chương `kho/logicXX_kienthuc.md`, đóng `=== HẾT PHIÊN ===` rõ ràng. Máy Mac (`web_harvest`) nhận xong `[1/2]` sau 30 giây sẽ **tự động nhắn tiếp** để em xuất nốt Khối **`[2/2] key=K<MMDDHHMM>`** (`kho/logicXX_hoidap.md`) và tự ghép nối 100%!

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | luu-kho: <Tên chuyên đề> ===
### NOTE: HANDOFF
- Mục tiêu: Lưu kho chuyên đề "<Tên chuyên đề>"
### FILE: kho/logicXX.meta.json
{"title": "<Tên ≤ 65 ký tự>", "subtitle": "<1 câu mô tả>", "tho": ["<câu lục>", "<câu bát>"], "pillar": "tam-ly|dinh-vi|kich-ban|case-study|van-hanh", "tags": "tag1, tag2, tag3", "icon": "🧭", "share_url": ""}
### FILE: kho/logicXX_kienthuc.md
<# Chương 1 đến # Chương 5 đầy đủ>
### FILE: kho/logicXX_hoidap.md
<Hỏi 1 đến Hỏi 10 đầy đủ>
=== HẾT PHIÊN ===
```

*(Nếu tách 2 phần thì tiêu đề khối 1 ghi `=== AGY-PHIEN <YYYY-MM-DD HH:MM> | luu-kho [1/2] key=K<MMDDHHMM>: <Tên chuyên đề> ===`, khối 2 ghi `=== AGY-PHIEN <YYYY-MM-DD HH:MM> | luu-kho [2/2] key=K<MMDDHHMM>: <Tên chuyên đề> ===`, mỗi khối đều có `=== HẾT PHIÊN ===`).*

## 4. Sau khi hoàn tất
- Phần đầu câu trả lời in gọn (≤ 15 dòng): 2 câu thơ tóm tắt + mục lục 5 chương + 10 câu Hỏi, sau đó in khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` ở cuối.
- Dòng chốt: `Đã xuất khối lưu kho — máy Mac (web_harvest 30s) sẽ tự thu hoạch lên kho.fedu.vn/moi-them và đồng bộ Google Drive (01_KHO_MOI_NHAT + GEM) ngay lập tức.`
