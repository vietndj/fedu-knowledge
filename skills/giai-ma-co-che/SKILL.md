---
name: giai-ma-co-che
description: "Mantra: PHIM TAT / TAO PHIM TAT / CHECK PHIM TAT / GIAI MA / NNN / HHH / LLL. Thiết kế & đồng bộ phím tắt gõ nhanh iCloud CloudKit (iPhone + Mac) và bộ khuôn Giải Mã Cơ Chế 3 Tầng."
tier: A
---

> **CHẾ ĐỘ GEMINI WEB (Tầng A)** — Đây là bản Web của kỹ năng `giai-ma-co-che` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Làm trọn đầu ra ngay trên Web (kịch bản, bài viết, phân tích, HTML 1 file).
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).

> Tài liệu kèm: `references/kho_nguyen_van.md`


# Skill: Kiến Trúc Sư Phím Tắt Gõ Nhanh iCloud (`PHIM TAT`) & Giải Mã Cơ Chế

## 1. Khi nào kích hoạt Skill này? (Triggers tự nhiên)
Kích hoạt ngay lập tức khi anh Việt nói:
- **"Phím tắt"**, **"Tạo phím tắt"**, **"Làm phím tắt cho cái này"**, **"Đưa câu lệnh này vào phím tắt"**, **"Check lại phím tắt"**, **"Sửa phím tắt..."**, **"Xóa phím tắt..."**.
- Hoặc khi anh Việt gọi trực tiếp các khuôn giải mã: `nnn`, `hhh`, `lll`, `kkk`, `ggg`.

---

## 2. Quy Trình Cốt Lõi Khi Anh Việt Bảo "PHÍM TẮT" (4 Bước Bắt Buộc)

Mỗi khi anh Việt đưa một ý tưởng, một quy trình, một đoạn hội thoại hay một yêu cầu và bảo **"Phím tắt"** (hoặc *"Tạo phím tắt / Check phím tắt"*), bạn **KHÔNG** trả lời dài dòng lan man mà thực hiện đúng 4 bước sau:

### Bước 1: Quét Kho Phím Tắt Hiện Có Trên Máy (`--list`)
Chạy lệnh kiểm tra ngay lập tức để biết những phím tắt nào đang có trong `TextReplacements.db`, tránh trùng lặp và tìm phím trống:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

### Bước 2: Đề Xuất Tên Phím Tắt Dễ Ấn Kiểu `nnn` (Luật Triple-Tap & Telex-Safe)
1. **Ưu tiên số 1 — Chạm 3 lần cùng 1 phím (`xxx`):**
   - Chọn **3 chữ cái giống hệt nhau** gắn với chữ cái đầu của tác vụ (ví dụ: `nnn` = Nguyên lý/Giải mã, `hhh` = Hỏi-Đáp 3 tầng, `lll` = Link YouTube, `kkk` = Khám lỗi & Viết lại, `ggg` = Góc nhìn khoa học, `mmm` = Mindmap Mermaid, `ttt` = Thơ lục bát, `ppp` = Personalize/Phản xạ IF-THEN, `sss` = Slide).
   - Giúp anh Việt bấm 1 ngón cái trong `0.3 giây` trên iPhone mà không cần đảo ngón tay hay chuyển bàn phím số (`123`).
2. **Luật Cấm Bộ Gõ Tiếng Việt Telex (Sống Còn):**
   - **TUYỆT ĐỐI CẤM** đề xuất các phím lặp bị bộ gõ Telex biến thành chữ có dấu/mũ:
     - `aaa` ($\rightarrow$ `âa`), `eee` ($\rightarrow$ `êe`), `ooo` ($\rightarrow$ `ôo`), `ddd` ($\rightarrow$ `đd`), `www` ($\rightarrow$ `ưw`).
   - **Hạn chế tối đa** các phím bỏ dấu Telex (`fff`, `rrr`, `xxx`, `jjj`).
   - **Các phím Triple-Tap Vàng (An toàn 100% với Telex):**
     - Đang dùng (4 phím tinh gọn): `nnn`, `lll`, `ggg`, `ttt`.
     - Còn trống sẵn sàng dùng khi anh Việt yêu cầu tạo phím tắt mới: `hhh`, `kkk`, `mmm`, `ppp`, `sss`, `bbb`, `ccc`, `vvv`, `qqq`, `zzz`.

### Bước 3: Chế Tác Nội Dung Phím Tắt (`phrase`) Để Gõ Nhanh
Chuyển hóa yêu cầu của anh Việt thành một **Prompt 1 Dòng Chuẩn Vàng** đáp ứng đủ các tiêu chuẩn kỹ thuật của Apple `_KSTextReplacementHelper` và chất lượng tư duy:
1. **Gói gọn trên 1 dòng duy nhất (Single-line):** Tuyệt đối không có ký tự xuống dòng (`\n`), vì trên iPhone/Web chat ký tự `\n` trong Text Replacement có thể kích hoạt phím `Send` gửi tin nhắn khi chưa kịp dán dữ liệu. Dùng `### 1.`, `### 2.` hoặc dấu `/` để phân tách cấu trúc.
2. **Độ dài `< 1.980` đơn vị UTF-16 (`Code 0`):** Trần cứng của Apple là `2.000` UTF-16 units (vượt quá sẽ bị lỗi `Code 3: _KSTextReplacementErrorExpansionLength` và không đồng bộ lên iCloud).
3. **Không chứa Emoji:** Emoji tốn 2–4 UTF-16 units và dễ gây kẹt đồng bộ.
4. **Cấu trúc câu lệnh sắc bén:** Luôn chỉ rõ Vai trò + Quy tắc suy nghĩ ngầm + Cấu trúc đầu ra từng phần (`### 1... ### 2...`) + Cơ chế chống cắt cụt nếu bài dài (*"Nếu sắp hết dung lượng, dừng ở mục trọn vẹn và in đậm CÒN NHIỀU - GÕ TIẾP TỤC"*).
5. **Nếu phím tắt cần dán kèm Link hoặc Nội dung ở cuối:** Kết thúc bằng cụm như `Link video: ` (có dấu cách ở cuối) để anh Việt gõ phím tắt xong là dán link nối tiếp ngay.

### Bước 4: Trình Bày & Đồng Bộ Thẳng Lên iCloud CloudKit (`sync_icloud_shortcut.py`)
1. Trình bày rõ ràng cho anh Việt:
   - **Tên phím tắt đề xuất** (vì sao dễ bấm & dễ nhớ) + **Độ dài UTF-16**.
   - **Nguyên văn nội dung 1 dòng** trong khối `text`.
2. Thực thi lệnh đồng bộ tự động (chạy ngầm qua Headless XPC `_KSTextReplacementClientStore.requestSyncWithCompletionBlock_`, đẩy thẳng lên máy chủ iCloud CloudKit với `NEED_SAVE = 0` trong 4 giây kể cả khi màn hình Mac đang khóa):
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

---

## 3. Bản Đồ 4 Phím Tắt Tinh Gọn Đang Hoạt Động Trên Mac & iPhone Của Anh Việt

*(Đã đồng bộ iCloud `SYNCED(0)` — Đã dọn sạch toàn bộ các phím còn lại)*

| Phím tắt | Độ dài (UTF-16) | Cách nhớ 1 giây | Chức năng cốt lõi |
| :---: | :---: | :--- | :--- |
| **`nnn`** | `1.390` | **N**guyên lý / What-Why-How | Đào sâu ngay ý đang bàn trong chat theo mạch `What – Why – How` (tối đa `350` từ): vào thẳng bản chất, 3 lối giải thích khác biệt (đảo ngược, phóng to, đặt cạnh), cấm lặp ví dụ cũ |
| **`lll`** | `1.941` | **L**ink YouTube | Giải phẫu Video/Podcast chuẩn `v3-claude` thoáng mắt (`<= 40` từ/dòng, không bảng tràn mobile): Bản đồ 5 mạch + Điểm mù + Quy tắc hành động + 5 thẻ Hỏi-Đáp lượt 1 khớp `kho.fedu.vn` |
| **`ggg`** | `1.599` | **G**óc nhìn đa ngành | Mở rộng ý đang bàn qua `4–5` góc nhìn chọn lọc (Năng lượng, Tâm lý học, Tiến hóa, Vật lý & Lượng tử ẩn dụ, Thiết kế game, Kinh tế hành vi, Hệ thống) + phép thử loại góc + việc làm dưới `10` phút |
| **`ttt`** | `1.067` | **T**hơ Lục Bát dài | Tóm tắt toàn bộ nội dung thành bài thơ Lục Bát dài kèm giải thích & ẩn dụ từng khổ |

---

## 4. Kho Nguyên Văn 4 Phím Tắt Đang Chạy Trên Máy (`nnn`, `lll`, `ggg`, `ttt`) & Hook Tự Bung Trong Antigravity
- Lấy trực tiếp từ DB bằng `python3 [đường-dẫn-Mac] --show <shortcut>` hoặc đọc bản lưu nguyên văn tại [`references/kho_nguyen_van.md`](file://[đường-dẫn-Mac]).
- **Hook Tự Bung `PreInvocation` (`macos-shortcut-expander` trong `[đường-dẫn-Mac]`):** Gọi [`shortcut_expander_hook.py`](file://[đường-dẫn-Mac]) đọc trực tiếp `TextReplacements.db` (Read-Only, `~38ms`), tự động bung nguyên văn mọi phím tắt (`nnn`, `lll`, `ggg`, `ttt` và các phím thêm mới sau này) ngay khi anh Việt gõ phím tắt rồi bấm `Enter` trong Antigravity.

---

## 5. Checklist 9 Tiêu Chí Nghiệm Thu Chất Lượng (Khi chạy trực tiếp `nnn`, `hhh`, `lll` trong Antigravity)

| Hạng mục | Phép thử | Đạt khi |
|---|---|---|
| Câu lật bản chất | **Phép thử hoán đổi:** thay tên khái niệm bằng 1 khái niệm khác cùng họ, câu B còn đúng không? | Câu B chỉ đúng với khái niệm này. Vế A phải là lầm tưởng có thật mà người đọc từng nghĩ. |
| Thơ — vật thể | Gạch hết danh từ trong 2 câu thơ | $\ge 2$ danh từ là vật thể sờ/thấy được (đất, nước, lửa, gỗ, da, hạt...). 0 từ trừu tượng (*niềm tin, đỉnh cao, bứt phá, lao xao*). |
| Thơ — ánh xạ | Che phần giải thích, chỉ đọc 2 câu thơ | Đoán được cơ chế Bước 1 $\rightarrow$ Bước 2 của mục đó. |
| Thơ — luật | Đếm chữ & thanh | Lục 6 chữ, bát 8 chữ. Chữ 2-4-6 theo **B-T-B**; chữ 6 câu lục vần chữ 6 câu bát; chữ 6 và chữ 8 câu bát khác dấu (ngang/huyền). |
| How | Đếm bước | Có chuỗi `Bước 1 -> Bước 2 -> Bước 3` + 1 quá trình thực tế minh họa. |
| Phân loại | Hỏi "loại này khác loại kia ở logic gì?" | Mỗi loại có dấu hiệu nhận biết + logic ngầm riêng, không chồng lấn. |
| Câu hỏi mở (`hhh`/`lll`) | Trả lời được bằng Có/Không? | Không được — phải là Tại sao / Làm sao. |
| Quy luật bỏ túi | Đếm chữ + tính nghịch lý | $< 20$ chữ, có 2 vế ngược chiều. |
| Không lặp | So mục 2 với Tầng 1 | Không chép lại cùng ý. |
