---
name: kho-logic
description: "Mantra: THEM KHO / XOA KHO / SUA KHO / GHIM KHO / share.gemini.google. Thu hoạch thơ Lục Bát gốc, chưng cất Cẩm nang & Hỏi-Đáp theo Khuôn Giải Mã v3-claude, xuất logicXX.html và đẩy kho.fedu.vn."
tier: A
---

> **CHẾ ĐỘ GEMINI WEB (Tầng A)** — Đây là bản Web của kỹ năng `kho-logic` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Làm trọn đầu ra ngay trên Web (kịch bản, bài viết, phân tích, HTML 1 file).
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).

> Tài liệu kèm: `references/examples_and_catalog.md`

# Kho Logic (`kho.fedu.vn` & `fedu.vn/k/logicXX.html`)
Kho kiến thức về tư duy hệ thống, nội dung, kịch bản, tâm lý, lưu trữ tại `kho.fedu.vn` (`[đường-dẫn-Mac]`) và đồng bộ 2 chiều với `[đường-dẫn-Mac]`.
*(Cơ chế RPC Sổ cái tự học `turn_ledger.json`, Khuôn Giải Mã Sắc Bén Kiểu Claude `v3-claude`, luật Lục Bát, ví dụ thật từ `deIs19lxp9lK` / `h1e8MuSMeQsd` & Admin CLI xem tại `references/examples_and_catalog.md`).*

## Bảng Điều Khiển Mantra & Tự Động Nhận Diện Đầu Vào

| Tín hiệu đầu vào / Mantra | Công cụ CLI | Chức năng tự động |
| :--- | :--- | :--- |
| **Gửi link `share.gemini.google/...` hoặc link trực tiếp `gemini.google.com/u/N/app/<id>` hoặc dán nội dung + `THEM KHO` / `KHO LOGIC`** | `fetch_gemini_share.py` $\rightarrow$ `harvest_poems.py` $\rightarrow$ `verify_kho_input.py` $\rightarrow$ `build_logic_html.py` $\rightarrow$ `them.py` $\rightarrow$ `ship.py` | Tải hội thoại (nếu là link `/app/<id>` tự động đọc thẳng qua Chrome CDP `9223` không cần bấm Share), khử trùng lặp lượt cũ, cấp số `logicXX`, thu hoạch thơ gốc, chưng cất **Cẩm nang Nhận thức (5 Chương + Bộ 10–15 Câu Hỏi-Đáp Giải Mã Gốc chuẩn `v3-claude`)**, kiểm định độ sắc bén với `CLAUDE2`, tạo `logicXX.html` và đẩy lên `kho.fedu.vn` |
| **Gõ `lưu kho` trên Gemini Web xong $\rightarrow$ về Mac gọi `VỀ MÁY` (hoặc Terminal: `cau ve`)** | `bridge.py pull` $\rightarrow$ `kho_inbox_apply.py` | Tự hút phiên `luu-kho` từ Google Docs `AGY_INBOX` về Mac, chuẩn hóa khuôn `v3-claude`, tự cấp mã `logicXX`, dựng `k/logicXX.html` và đẩy lên `kho.fedu.vn` |
| **Ghim luồng trên Gemini (`vietnd025` / `vietnd020`) + nói `THEM KHO` / `QUET GHIM`** | `cd "[đường-dẫn-Mac]" && python3 "[đường-dẫn-Mac]" --u auto --out /tmp/gemini_share_content.txt` | Tự vào Chrome CDP `9223` (ưu tiên `vietnd025` `/u/2`, có thể truyền `--account vietnd020` hoặc `--u /u/3`) đọc toàn bộ các luồng anh Việt đã **Ghim (Pin)** mà không cần bấm Share; tự lọc bỏ lượt đã có trong `turn_ledger.json`, xuất phần mới ra `/tmp/gemini_share_content.txt`, và sau khi làm xong dùng `--assign-logic logicXX --archive-to-all` để cất/bỏ ghim |
| **`XOA KHO`** | `cd "[đường-dẫn-Mac]" && python3 "[đường-dẫn-Mac]"` | Xóa 2 chiều bài viết/câu hỏi khỏi `kho.fedu.vn` VÀ xóa block + TOC trong `k/logicXX.html`, tự đánh lại số thứ tự |
| **`SUA KHO`** | `cd "[đường-dẫn-Mac]" && python3 "[đường-dẫn-Mac]"` | Sửa tiêu đề, tóm tắt, nội dung Markdown, tags và đồng bộ tiêu đề câu hỏi về file HTML gốc |
| **`GHIM KHO`** | `cd "[đường-dẫn-Mac]" && python3 "[đường-dẫn-Mac]"` | Ghim hoặc bỏ ghim (`--unpin`) chuyên đề/bài viết lên đầu trang chủ & danh mục |

---

## Quy Trình 7 Bước Tự Động Hóa 100% (`THEM KHO` / Link Gemini Share)

Khi nhận link `share.gemini.google/...` (`gemini.google.com/share/...`) hoặc văn bản hội thoại dán vào chat, thực thi **7 Bước khép kín** (không dừng giữa chừng). Trước khi biên tập Chương (Bước 3) & Hỏi-Đáp (Bước 4), chạy `python3 "[đường-dẫn-Mac] gia/brain.py" "<chủ đề chuyên đề>" --mode write` để nạp Khung Xương `v3-claude × Thịt Nguyễn Việt` và bảng từ cấm Dao 5:

### Bước 1: Thu thập Nội dung, Khử Trùng Lặp Theo Lượt & Cấp Mã `logicXX` (`fetch_gemini_share.py`)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Nếu `status == "DUPLICATE_ALL"` (`new_turns_count == 0`), dừng ngay và báo link trùng 100% với bài `logicXX` đã xuất bản.
- **Chỉ đọc thử / test link:** thêm `--no-learn --force-all --out /tmp/test_share_<code>.txt` để KHÔNG ghi `turn_ledger.json`.

### Bước 2: Thu Hoạch 100% Thơ Lục Bát Gốc (`harvest_poems.py`)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Gắn mã `P01..Pnn` cho MỌI cặp thơ trong hội thoại (mỏ neo đầu `##` và `📜 Lục bát đúc kết` cuối `###`) kèm lượt, heading, đoạn văn liền kề và phán quyết luật (`luc_bat_rules.py`): **PASS** / **WARN** (dùng được) / **FAIL** (lệch vần 6-6, chữ 6/8 thanh trắc, sai số chữ, dính chữ kiểu `đấtlinh`).
- Nạp nguyên `/tmp/logicXX_poems.md` cho Subagent ở Bước 4 làm **kho mỏ neo bắt buộc**.

### Bước 3: Chuẩn bị Bộ Chương Kiến Thức (`/tmp/kho_kienthuc_logicXX.md`) chuẩn `v3-claude-chapter`
- Biên tập thành 5 chương `# Chương 1: ...` đến `# Chương 5: ...`:
  - **Chương 1 (Bản đồ 5 mạch tư duy tổng quan):** Phải viết cho **người mới tinh đọc hiểu từ nông đến sâu**: mở đầu bằng mục `### Bối cảnh cho người mới bắt đầu` dẫn từ tình huống đời thường ai cũng gặp sang cuộc đối thoại gốc; mỗi `### Mạch 1..5` phải chia rõ 3 lớp: **Chỗ người mới hay kẹt (Bề mặt)** $\rightarrow$ **Cơ chế tháo gỡ (Bản chất)** $\rightarrow$ **Câu chuyện thực tế để nhớ** (kể trọn vẹn đầu đuôi nhân quả của từng hình ảnh ẩn dụ; **TUYỆT ĐỐI CẤM viết tắt cộc lốc kiểu mật mã `Mỏ chim bói cá → mũi tàu cao tốc`** và **CẤM dùng bảng Markdown `|---|---|`**).
- Ngay dưới mỗi `# Chương X` BẮT BUỘC mở đầu bằng:
  1. **2 câu thơ Lục Bát mỏ neo** (`> *Câu lục 6 chữ*` / `> *Câu bát 8 chữ*`) + comment `<!-- tho: ... -->`.
  2. **1 câu định nghĩa trực diện in đậm:** `**[Chủ đề chương] không phải là [lầm tưởng phổ biến]... mà là [bản chất thật sự].**` (qua phép thử hoán đổi) + 1 đoạn văn dẫn nhập từ trải nghiệm quen thuộc của người đọc mới.
  3. Các mục con chia bằng `###` ngắn gọn, đời thường, giải thích từ nông đến sâu.
  4. Cuối chương BẮT BUỘC có khối **Chân trang nguồn** (`> - 🎙️ **Nguồn:** ...` / `> - 💬 **Bản giải phẫu gốc:** ...` / `> - 📍 **Bối cảnh:** ...` — luôn dùng URL tuyệt đối `https://fedu.vn/k/...`, cấm dùng `/k/...`; khi lên web sẽ tự động hiển thị dạng **Accordion chỉ hiện dòng 📌 Bối cảnh**, bấm vào mới mở thông tin Nguồn phụ).

### Bước 4: Biên Soạn Bộ Câu Hỏi-Đáp Giải Mã Gốc (`/tmp/kho_hoidap_logicXX.md`) chuẩn `v3-claude` & Kiểm Định Với `CLAUDE2`
- **Không xé vụn:** Gom theo đơn vị lượt/cơ chế tự thân hoàn chỉnh (10–15 câu/chuyên đề), sao cho 6 tháng sau đọc độc lập 1 thẻ vẫn hiểu ngay toàn bộ câu chuyện mà không cần mở bài khác.
- **Cấu trúc 6 khối chuẩn `v3-claude` (chi tiết tại `references/examples_and_catalog.md`):**
  1. `Hỏi:` câu hỏi mở $\le 18$ từ xoáy thẳng chỗ kẹt (`Tại sao...` / `Làm sao...`).
  2. **Thơ Lục Bát mỏ neo ở ĐẦU:** `> *Câu lục*` / `> *Câu bát*` dùng vật thể sờ thấy được (hạt mầm, dòng nước, thớ gỗ, vết đứt tay...) chứa sẵn cơ chế bên dưới + `<!-- tho: goc|goc-sua|moi Pxx -->`.
  3. **Câu định nghĩa trực diện in đậm:** `**[Điều này] không phải là [lầm tưởng phổ biến]... mà là [bản chất thật sự].**` (dùng dấu `...` ngắt nhịp tự nhiên; vế B phải qua phép thử hoán đổi).
  4. **`### Cơ chế chạy ngầm`:** Giải thích ngắn gọn bản chất (What) + nguyên lý tồn tại (Why) + chuỗi vận hành **`Bước 1 → Bước 2 → Bước 3`** (How) + **`Ví dụ:`** đời thực cụ thể.
  5. **`### Phân loại / Dấu hiệu nhận biết`** (hoặc `### Hai góc nhìn đời thường`): Chia 2–3 dạng thực tế (nêu rõ logic chạy ngầm & dấu hiệu nhận biết) kèm các ẩn dụ vật lý đời thường trong hội thoại gốc.
  6. **`### Làm ngay`** + **Chân trang nguồn (`> - 🎙️ **Nguồn:** Podcast ...` / `> - 💬 **Bản giải phẫu gốc:** ...` / `> - 📍 **Bối cảnh:** ...`)**: 1 việc làm được ngay có số đo, kèm link YouTube Podcast gốc, mốc thời gian, link Gemini Share gốc và 1 câu tóm bối cảnh đoạn hội thoại.
- **Cấm tuyệt đối thuật ngữ khoa học/hàn lâm khó hiểu:** Không dùng *tư duy kỹ trị, phương trình tuyến tính, sự sụp đổ hàm sóng, Wave function collapse, Superposition, Negentropy, Dissipative structures, Overjustification Effect, Locus of Evaluation, sóng Gamma, mạng lưới trạng thái mặc định, Mimetic desire, Costly signaling...* (`verify_kho_input.py` sẽ tự động chặn).
- **Kiểm định độ sắc bén với `CLAUDE2`:** Đưa mẫu hoặc bộ file cho `CLAUDE2` (`claude-delegate` $\rightarrow$ `start_task_pro` / `run_task_pro`, `model="opus"`) rà soát phép thử hoán đổi và độ cô đọng trước khi xuất bản.

### Bước 5: Cổng Kiểm Định Tất Định (`verify_kho_input.py` + độ phủ thơ)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- `verify_kho_input.py` tự nhận diện chuẩn `v3-claude` & `v3-claude-chapter`, kiểm tra: thơ Lục Bát ở đầu, câu định nghĩa đậm `**... không phải ... mà là ...**`, tiêu đề `###`, chuỗi `Bước 1/2/3`, khối Chân trang nguồn `> - 🎙️ **Nguồn:**`, chặn 20+ thuật ngữ hàn lâm trong `JARGON_BLACKLIST`, và kiểm tra luật Lục Bát.
- Độ phủ phải `coverage = 1.0`: mọi `Pxx` đã dùng (`goc`/`goc-sua`) hoặc loại có lý do (`bo`); thơ FAIL chép nguyên văn sẽ bị chặn.

### Bước 6: Đóng Gói & Kiểm Định `logicXX.html` (`build_logic_html.py`)
Biên dịch ra giao diện InkDoc 2 cột Sticky TOC (hỗ trợ bảng `<table class="ink-table">`, hộp định nghĩa `.ink-flip-box`, subheadings `###`, và hộp Chân trang nguồn `.ink-provenance`) và tự động verify bảo toàn $\ge 95\%$ số từ:
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

### Bước 7: Nạp Vào `kho.fedu.vn`, Push GitHub & Ship Production (`them.py --replace` + `ship.py`)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

---

## Lệnh CLI Quản Trị Nhanh (`XOA KHO` / `SUA KHO` / `GHIM KHO`)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
