# kho-logic — Cơ chế RPC Sổ Cái Tự Học (`turn_ledger.json`), Khuôn Giải Mã Sắc Bén Kiểu Claude (`v3-claude`), Luật Thơ Gốc & Admin CLI

> Phần tham chiếu tách từ `SKILL.md` (nội dung gốc giữ nguyên + bổ sung chuẩn `v3-claude` đã nghiệm thu bởi `CLAUDE2`).

<!-- gốc: SKILL.md dòng 31-36 -->
  - **Cơ chế RPC + Sổ Cái Tự Học (`scripts/turn_ledger.json`):**
    1. Tự động phân giải redirect `share.gemini.google` $\rightarrow$ `gemini.google.com/share/<id>` và gọi thẳng endpoint `batchexecute` (`ujx1Bf`) để tải 100% văn bản gốc trong `< 1s` (không bị kẹt bởi CSP hay `networkidle`).
    2. Tự động băm SHA-256 từng lượt hỏi–đáp (`turn_hash`) và đối chiếu với sổ cái [`scripts/turn_ledger.json`](file://[đường-dẫn-Mac]).
    3. Nếu link mới là một **nhánh tách ra từ giữa cuộc hội thoại cũ** (hoặc hỏi nối tiếp vào cuối hội thoại cũ), script **tự động bỏ qua các lượt đã từng nạp ở các bài `logicXX` trước**, chỉ trích xuất **các lượt mới tinh** ra `/tmp/gemini_share_content.txt` và tự động ghi nhớ các lượt mới vào `turn_ledger.json` cho các lần sau.
    4. Nếu `status == "DUPLICATE_ALL"` (`new_turns_count == 0`), dừng ngay và báo anh Việt biết link này trùng 100% với bài `logicXX` đã xuất bản.

## Chuẩn Đầu Ra Mặc Định: Khuôn Giải Mã Sắc Bén Kiểu Claude (`v3-claude`)
1. **Phần 1 (`/tmp/kho_kienthuc_logicXX.md` — 5 Chương Kiến Thức `v3-claude-chapter`):**
   - Chương 1 là **Bản đồ 5 mạch** (mở bằng thơ Lục Bát + câu định nghĩa đậm `**Logic XX không phải là... mà là...**` + bản đồ 5 mạch dạng mục ### + Chân trang nguồn).
   - Chương 2–5 giải mã 4–5 mạch lớn, chia bằng `###`, cuối mỗi chương có Chân trang nguồn.
2. **Phần 2 (`/tmp/kho_hoidap_logicXX.md` — Bộ 10–15 Câu Hỏi-Đáp Giải Mã Gốc `v3-claude`):**
   - Không xé vụn 1 lượt giải mã thành nhiều thẻ lẻ tẻ; gom thành 10–15 thẻ tự thân đầy đủ để 6 tháng sau đọc lại vẫn hiểu trọn bối cảnh:
```markdown
Hỏi: Tại sao đòi hỏi số liệu cam kết trước khi làm lại bóp nghẹt ý tưởng mới?
> *Hạt vừa vùi đất sáng mai*
> *Moi lên đo rễ ngắn dài, mầm khô.*
<!-- tho: goc P01 -->

**Đòi số liệu cam kết trước khi làm không phải là sự cẩn thận... mà là bắt một thứ chưa từng có phải trình ra bằng chứng của những thứ đã từng có.**

### Cơ chế chạy ngầm
- **Bước 1 — Số chỉ ghi lại quá khứ:** Sổ bán hàng chỉ có dòng cho món đã bán... món chưa nấu thì không có dòng nào.
- **Bước 2 — Ý mới chưa có quá khứ:** Nên khi bị hỏi "bán được bao nhiêu?"... câu trả lời thật duy nhất là "chưa biết".
- **Bước 3 — Cửa chỉ mở cho cái giống cũ:** Ý nào phải có số mới được làm... thì chỉ những ý na ná cái đã có mới lọt qua. Cái thật sự mới bị loại ngay ở cửa... trước khi kịp mọc rễ.
- **Ví dụ:** Quán phở muốn bán thêm bún chả cá. Hỏi "mỗi ngày bán được bao nhiêu bát?" thì không ai trả lời được. Nấu thử 20 bát, bán trong một buổi sáng... con số tự hiện ra.

### Hai loại câu hỏi số — phân biệt thế nào
- **Số đo sau khi làm thử:** "20 bát hôm qua, khách ăn hết mấy bát?" → dùng để sửa. *Dấu hiệu:* có sản phẩm thật trước, rồi mới có số.
- **Số đòi trước khi làm:** "Chắc chắn lãi thì mới làm?" → dùng để khỏi phải làm. *Dấu hiệu:* trong tay chưa có gì... nhưng đã đòi bảo hành.

### Làm ngay
Ý mới vừa nảy ra... thì trong 48 giờ đầu đừng mở bảng tính. Làm 1 bản nháp nhỏ nhất có thể đưa cho người thật xem: 1 video 30 giây, hoặc 1 mâm 20 bát. Có bản nháp rồi mới bắt đầu đếm.

> - 🎙️ **Nguồn:** Podcast The Diary Of A CEO (Steven Bartlett × Rick Rubin) · [Xem trên YouTube](https://www.youtube.com/watch?v=a_GiFiHXJ6g) · Mốc: *Đầu cuộc trò chuyện*
> - 💬 **Bản giải phẫu gốc:** [Gemini Share — Lượt 1/10](https://share.gemini.google/deIs19lxp9lK) · [Cẩm nang Logic 39](/k/logic39.html)
> - 📍 **Bối cảnh:** Steven liên tục hỏi Rick về công thức và số liệu... Rick điềm đạm đáp rằng họ không làm việc theo cách đó.
```

## Chuẩn Đầu Ra Cẩm Nang Nhận Thức (v2 — Hỏi-Đáp Giải Phẫu 3 Tầng, tương thích ngược)
1. **Phần 1 (`/tmp/logicXX_map.md` — Bản Đồ Nhận Thức):** 3–5 mạch tư duy cốt lõi của toàn bộ cuộc đối thoại.
2. **Phần 2 (`/tmp/kho_hoidap_logicXX.md` — Bộ Thẻ v2):** mỗi mục gốc có ẩn dụ / cơ chế / thơ = 1 thẻ độc lập:
```markdown
Hỏi: <Câu hỏi mở <= 20 từ: Tại sao / Làm sao ... xoáy thẳng chỗ kẹt?>
> *<Câu Lục 6 chữ — thơ GỐC Pxx nếu có>*
> *<Câu Bát 8 chữ — chữ 6 hiệp vần chữ 6 câu Lục; chữ 6 và 8 thanh Bằng>*
<!-- tho: goc Pxx | goc-sua Pxx — <lý do sửa> | moi -->
- **🔄 Lật bản chất:** Không phải <A - điều đám đông tưởng>, mà là <B - cơ chế thật>.
- **🎯 Tầng 1 — Bối cảnh & Cái bẫy bề mặt:** <Ai, hoàn cảnh nào, đã thử gì, kẹt ở đâu + lầm tưởng bề mặt>
- **🔬 Tầng 2 — Giải phẫu bản chất (Ẩn dụ: <Tên ẩn dụ gốc>):** <Cơ chế nhân quả + dẫn chứng gốc (mốc thời gian, nghiên cứu, ví dụ trong hội thoại)>
- **⚡ Tầng 3 — Nước đi lật thế cờ:** 1) <hành động làm ngay> 2) <...> (tối đa 3)
- **📌 Quy luật bỏ túi:** <= 20 chữ, mang về dùng được ngay>
```
- **Thơ mỏ neo ở ĐẦU** (Mental Hook): người đọc thấy hình ảnh vật lý trước, phần giải phẫu bên dưới giải nghĩa nó. Không đặt thơ dạy đời ở cuối.
- **Thẻ cũ 5 lớp** (`🎯 Bối cảnh & Lầm tưởng` → `🔬 Giải phẫu Sự thật` → `⚡ Thực chiến` → `📜 Thơ đúc kết` ở cuối) vẫn được `verify_kho_input.py`, `build_logic_html.py`, `them.py` và giao diện kho đọc đúng.

## Luật Bảo Toàn Thơ Gốc (`harvest_poems.py` + `luc_bat_rules.py`)
| Phán quyết | Ý nghĩa | Cách dùng trong thẻ |
|---|---|---|
| **PASS** | Đúng số chữ, vần 6-6, chữ 6/8 Bằng | Dùng nguyên văn<br/>`<!-- tho: goc Pxx -->` |
| **WARN** | Lỗi nhẹ: vần thông (in/inh), chữ 2 không Bằng, chữ 4 không Trắc, lặp chữ vần | Dùng nguyên văn được<br/>`<!-- tho: goc Pxx -->` |
| **FAIL** | Lệch vần 6-6 (hay hiệp nhầm chữ 8), chữ 6/8 thanh Trắc, sai số chữ, dính chữ | Sửa tối thiểu, giữ vật thể gốc<br/>`<!-- tho: goc-sua Pxx — lý do -->` |
| Không có thơ | Mục gốc thiếu thơ | Sáng tác vật thể tự nhiên/vật lý<br/>`<!-- tho: moi -->` |
| Thơ chuyển đoạn | Chỉ tóm bố cục, không gắn cơ chế | Loại có lý do<br/>`<!-- tho: bo Pxx: lý do -->` |
- Cổng độ phủ: `harvest_poems.py --check-coverage` yêu cầu `coverage = 1.0` (mọi Pxx được dùng hoặc loại có lý do) và chặn thơ FAIL bị chép nguyên văn.
- Comment `<!-- tho: ... -->` bị ẩn trên kho.fedu.vn và bị bỏ khi build `logicXX.html`.

## Ví dụ Thật Từ Link `share.gemini.google/deIs19lxp9lK` (Rick Rubin — "sáng tạo 3", 10 lượt)
- Thu hoạch: **41 cặp thơ** (33 mỏ neo đầu `##`, 8 đúc kết cuối `###`) → 16 PASS · 18 WARN · 7 FAIL.
- FAIL tiêu biểu: P03 `Mang cân đi đong gió trời / Cân xong mới biết rỗng không một đời` (trời ↔ không lệch vần, hiệp nhầm chữ 8 "đời"); P22 `dướiầm` dính chữ; P26 `đấtlinh` dính chữ; P28 chữ 8 "dọc" thanh Trắc; P38 thơm ↔ hơn không vần; P40 chữ 6 "thật" thanh Trắc.

**Thẻ dùng thơ gốc nguyên văn (P14 PASS):**
```markdown
Hỏi: Tại sao đăng video xong cứ ngồi canh lượt xem lại làm video sau tệ hơn?
> *Việc mình làm trọn tay mình*
> *Đưa ra ngoài cửa mặc tình thế gian*
<!-- tho: goc P14 -->
- **🔄 Lật bản chất:** Không phải bạn thiếu tài để làm video sau hay hơn, mà là bạn đã trao chìa khóa phòng dựng cho đám đông ngay khi bấm đăng.
- **🎯 Tầng 1 — Bối cảnh & Cái bẫy bề mặt:** Người làm nội dung đăng video xong là mở thống kê mỗi giờ, tưởng đang rút kinh nghiệm. Thực chất họ mang nỗi sợ mất lòng người xem vào lần bấm máy kế tiếp, nên video sau càng gượng, càng giống người khác.
- **🔬 Tầng 2 — Giải phẫu bản chất (Ẩn dụ: Lâu đài cát trong phòng thu):** Rick Rubin kể chỉ cần một người buột miệng khen bài này chắc chắn nổi [01:48:00], sự thuần khiết của bản thu lập tức đổ sập như lâu đài cát gặp sóng. Khi lượt xem là mục tiêu, nó thành cái roi; khi lượt xem chỉ là phần thưởng thêm [01:47:04], đầu óc được thả ra để làm việc tiếp.
- **⚡ Tầng 3 — Nước đi lật thế cờ:** 1) Dời vạch đích về lần xem lại bản dựng cuối: âm sạch, ý rõ, không còn chỗ lấn cấn là xong. 2) Bấm đăng xong mở ngay dự án kế tiếp, không ngồi đếm bình luận.
- **📌 Quy luật bỏ túi:** Vạch đích nằm trước nút đăng, không nằm sau lượt xem.
```

**Thẻ sửa tối thiểu thơ gốc lỗi luật (P28 FAIL → goc-sua):**
```markdown
Hỏi: Tại sao người mang quà đi tặng thì vững, còn người đi xin lời khen thì run?
> *Tay trao lòng đã nhẹ nhàng*
> *Tay xin mắt phải liếc ngang dò chừng*
<!-- tho: goc-sua P28 — bản gốc kết 'liếc ngang liếc dọc', chữ 8 'dọc' thanh trắc sai luật; thay 'dò chừng' giữ ý mắt láo liên -->
- **🔄 Lật bản chất:** Không phải người tặng quà can đảm hơn, mà là họ giữ trong tay cái nút bấm kết thúc, còn người đi xin đã đưa cái nút đó cho đám đông.
- **🎯 Tầng 1 — Bối cảnh & Cái bẫy bề mặt:** Cùng là đăng một video, một người đăng xong thấy nhẹ tênh, người kia canh màn hình từng phút, có một bình luận chê là xóa bài và nghi ngờ năng lực bản thân.
- **🔬 Tầng 2 — Giải phẫu bản chất (Ẩn dụ: Nước chảy từ chỗ cao xuống chỗ thấp):** Hạch hạnh nhân chỉ hú còi khi ta mất quyền kiểm soát. Người tặng xuất phát từ chỗ đã đủ, như mực nước cao, dòng chảy đẩy ra ngoài nên không có tạp chất nào chảy ngược vào. Người xin xuất phát từ chỗ thiếu, đám đông chưa khen thì họ chưa được phép xong việc.
- **⚡ Tầng 3 — Nước đi lật thế cờ:** 1) Viết một dòng trước khi đăng: món quà này dành cho ai và giúp họ điều gì. 2) Tự tuyên bố xong việc ngay lúc đăng, chê hay khen chỉ ghi nhận là chuyện khẩu vị.
- **📌 Quy luật bỏ túi:** Ai bấm nút kết thúc, người đó làm chủ cuộc chơi.
```
- Bộ demo đầy đủ 6 thẻ: `/tmp/kho_hoidap_demo_deIs19lxp9lK.md` (verify PASS, build InkDoc PASS).

<!-- gốc: SKILL.md dòng 97-113 -->
## Quy trình `XOA KHO` / `SUA KHO` / `GHIM KHO` & Local Admin Bridge

### 1. Xóa 2 chiều (`XOA KHO`)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Tự động xóa file `.md` trên kho và xóa luôn khối `<div class="dialogue-turn">` + mục lục trong `[đường-dẫn-Mac]`.

### 2. Sửa 2 chiều (`SUA KHO`)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

### 3. Ghim / Bỏ ghim chuyên đề hoặc bài viết (`GHIM KHO`)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_