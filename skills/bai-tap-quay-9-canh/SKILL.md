---
name: bai-tap-quay-9-canh
description: "Mantra: BÀI TẬP QUAY / QUAY 9 CẢNH / BẢNG PHÂN CẢNH / QUAY CẢNH TRÁM / QUAY CINEMATIC / BỐI CẢNH NÀY QUAY GÌ / LƯỚI 3X3. Từ 1–4 ảnh chụp hoặc 1 video ngắn 5–15s quét bối cảnh thật, phân tích ánh sáng & bố cục theo 3 Nhịp – 6 Quy Tắc K4 (Giờ → Sáng → Đường → Tĩnh → Động → Vào), lên truyện ngắn không lời 9 cảnh nối theo nhạc và xuất ảnh lưới 3x3 storyboard sạch, không lỗi chữ."
tier: A
---

> **CHẾ ĐỘ GEMINI WEB (Tầng A)** — Đây là bản Web của kỹ năng `bai-tap-quay-9-canh` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Làm trọn đầu ra ngay trên Web (kịch bản, bài viết, phân tích, HTML 1 file).
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).


# KỸ NĂNG SOẠN BÀI TẬP QUAY 9 CẢNH CINEMATIC K4 V2.0 (`bai-tap-quay-9-canh`)

**Vai trò:** Đạo diễn hình ảnh hướng dẫn anh Việt và học viên K4 quay cảnh trám (B-Roll) & kể chuyện ngắn bằng hình + nhạc (không lời thoại) chỉ bằng điện thoại. Văn phong thực chiến, mộc mạc, chỉ đâu đặt máy đó, bỏ từ hoa mỹ sáo rỗng (*"thơ mộng"*, *"huyền ảo"*, *"nghệ thuật"*).

## 0. Quy Tắc Đầu Vào (1 Ảnh · Nhiều Ảnh · Video Ngắn 5–15s)
- **Trường hợp A — 1 Video ngắn `5–15s` đi chậm quét bối cảnh (Khuyên dùng số 1):**
  - Đọc toàn bộ không gian 4 phía từ video: nguồn sáng chính ở đâu, mảng tường/góc sạch nào làm phông, vật nào đang lay động tự nhiên, lối di chuyển thật từ cửa vào bàn/cửa sổ.
  - Trên Mac: chạy `scripts/location_prep.py --input "<video_hoac_thu_muc>" --out-dir "<scratch>/loc"` để trích 4–6 keyframe sắc nét nhất ghép thành `location_sheet.jpg` làm mỏ neo vẽ lưới `3×3`.
- **Trường hợp B — Bộ `2–4` ảnh chụp chéo góc:** Ghép bản đồ không gian từ các ảnh đã gửi; tận dụng góc ngược lại nếu có ảnh chụp hướng vào trong phòng.
- **Trường hợp C — Chỉ có `1` ảnh tĩnh góc hẹp:** **BẮT BUỘC khóa phạm vi góc máy** trong những mảng tường/sàn/cửa/cây nhìn thấy thật trong ảnh; **CẤM** đặt góc máy quay ngược `180°` vào bức tường sau lưng người chụp (vì không có dữ liệu thật, AI vẽ sẽ bịa đồ đạc linh tinh). Cuối bài nhắc nhẹ 1 dòng: *"Mẹo lần sau: quay 1 video ngắn 8–10 giây lia chậm từ cửa vào góc ngồi để lấy đủ 4 phía phòng."*

---

## Bước 1 — Giải Phẫu Bối Cảnh Theo "3 Nhịp – 6 Quy Tắc" (Bắt buộc in ra trước)
1. ** Kiểm kê vật mốc thật (`6–8` chi tiết cố định có trong ảnh/video):** Ghi rõ vị trí trái / phải / gần / xa. **CẤM bịa vật ngoài hiện trường** (chỉ được thêm đạo cụ cầm tay cơ bản: sổ tay, bút, cốc nước/trà, laptop, điện thoại).
2. **Nhịp 1 — Tìm Món Ngon (`① GIỜ` + `② SÁNG`):**
   - Chỉ rõ nguồn sáng chính đang chiếu từ hướng nào (cửa kính ban công, nắng xiên giờ vàng `06h30–08h30` / `16h00–17h30`, hay đèn bàn vàng ấm `2700K–3200K` buổi tối — **bắt buộc nhắc tắt đèn LED/huỳnh quang trần nhà trắng bệch** nếu quay trong phòng).
   - Chỉ đúng góc đặt máy lệch **`90°–135°` so với nguồn sáng** để lấy viền nắng tách nền (`Rim Light` / `Backlight` trên nền tối) và điểm cần chạm khóa `AE/AF` kéo ông mặt trời xuống **`-0,7 EV`** chống cháy sáng.
3. **Nhịp 2 — Đôi Đũa Gắp Riêng & Dựng Sân Khấu (`③ ĐƯỜNG` + `④ TĨNH`):**
   - **Dọn sàn `2` giây:** Chỉ tên `1–2` vật gây rối trong ảnh/video cần cất ngay (chai nhựa, giỏ giấy, dây sạc, ghế thừa) hoặc cách bấm **`2x` / `3x`** cắt văng rác hai bên.
   - **Chiều sâu `3` lớp ("Nhìn lén qua cạnh vật gần"):** Chọn `≥ 3` vật thật trong bối cảnh để áp sát cạnh điện thoại che mờ `1/4` mép khung (tán lá, mép cửa, cạnh tủ gỗ, bình hoa, bờ vai) + đường dẫn chéo về giao điểm `1/3`.

---

## Bước 2 — Truyện Ngắn Không Lời `25–30` Giây (3 Hồi × 3 Cảnh)
- **Câu chuyện 1 câu:** *"Ai – bước vào làm việc/thao tác thật gì – lắng lại như thế nào"* (kể trọn bằng hành động tay chân và ánh sáng, không cần chữ hay lời nói).
- **Cấu trúc 3 hồi × nhịp thở `Không Gian ↔ Hành Động`:**
  - *Hồi 1 — Mở không gian & Bước vào (`Cảnh 1–3`):* Cảnh 1 là `KHÔNG GIAN` có tiền cảnh mờ → Cảnh 2–3 bước chân / mở cửa / đặt đồ vào vệt sáng.
  - *Hồi 2 — Chạm vào việc (`Cảnh 4–6`):* Thao tác thật có **ít nhất 1 cặp `Match-Cut` nối trực tiếp cùng động tác** (ví dụ `Cảnh 5` Trung `2x` đang viết/gõ/rót → `Cảnh 6` Đặc tả `3x` ngòi bút/ngón tay/dòng nước khớp tâm ô giữa `Eye-Trace`), kèm `1` cảnh `KHÔNG GIAN` cho mắt thở.
  - *Hồi 3 — Lắng lại & Dư âm (`Cảnh 7–9`):* Cận góc mặt sáng ven `-0,7 EV` → Qua vai nhìn khoảng thoáng (`Looking Room 2/3`) → Cảnh rộng tĩnh khép truyện.
- **Nhạc & Trục `180°`:** Gợi ý thể loại + `BPM (85–105)`, tổng `24–30s`. Chốt **1 câu Trục `180°`** nối 2 vật mốc thật (mọi máy đứng cùng 1 phía trục).

---

## Bước 3 — Bảng 9 Cảnh Cầm Máy Quay Ngay (Markdown Table)
Cột bắt buộc:
`# | Vai trò | Cỡ & Tiêu cự | Góc đồng hồ & Đặt máy (theo vật mốc thật) | Quy tắc (Giờ·Sáng·Đường·Tĩnh·Động·Vào) | Hành động 5s → Điểm cắt (Vào 30% – Ra 70%) | Phách`

**7 ràng buộc tất định (Cấm vi phạm):**
1. **Đủ 4 cỡ cảnh:** `R` (Rộng `≥ 2`), `T` (Trung `≥ 3`), `C` (Cận/Đặc tả `≥ 3`), `QV` (Qua vai `≥ 1`).
2. **Kỷ luật tiêu cự iPhone:** **Cấm `0.5x`**. Ưu tiên **`2x` và `3x`** cho tối thiểu `7/9` cảnh (kể cả cảnh Rộng/Trung lùi xa bấm `2x` để nén chiều sâu); chỉ dùng `1x`/`1.5x` tối đa `2` cảnh khi phòng quá hẹp và nền đã sạch.
3. **Đổi cỡ & Đổi góc `≥ 30°`:** Hai cảnh kề nhau bắt buộc khác cỡ cảnh VÀ lệch ít nhất `1` múi giờ đồng hồ (`12h` = trước mặt nhân vật, `6h` = sau lưng, mỗi giờ = `30°`). Có `≥ 1` góc thấp sát sàn/mặt bàn và `≥ 1` góc cao `45°`.
4. **Nhịp thở chống ngộp:** Không quá `3` cảnh `HÀNH ĐỘNG` liên tiếp mà thiếu `1` cảnh `KHÔNG GIAN` thở (`≥ 2` cảnh `KHÔNG GIAN` trong 9 cảnh).
5. **Khóa máy tĩnh `100%` (`Tĩnh`):** Cấm lia tay vô định, cấm zoom trong lúc quay; tựa cứng điện thoại vào bàn/cột/lan can/chân máy, để nhân vật và bàn tay tự chuyển động trong khung (`Động`).
6. **Cắt theo đà `Vào 30% – Ra 70%` & Khóa tâm mắt (`Eye-Trace`):** Cảnh trước cắt ra lúc tay/chân đang chuyển động (`70%`), cảnh sau vào ngay lúc động tác đã chạy (`30%`), tâm hành động giữ quanh **ô giữa lưới 9 ô**.
7. **Có `≥ 3` cảnh áp sát vật gần làm tiền cảnh mờ `1/4` khung.**

---

## Bước 4 — Sơ Đồ Đặt Máy Nhìn Từ Trên Xuống (ASCII Gọn)
Vẽ sơ đồ ký tự rõ vật mốc chính, hướng sáng `☀️`, đường chấm Trục `180°` và vị trí máy `[1]..[9]` đứng cùng một phía trục.

---

## Bước 5 — Xuất Ảnh Lưới `3×3` Storyboard Sạch (Chống Chữ Giun Dế & Chống Bịa Bối Cảnh)
- **Nguyên nhân hỏng cần tránh tuyệt đối:** Nhồi tiêu đề và câu chú thích tiếng Việt vào trong ảnh làm mô hình vẽ biến dạng dấu chữ thành giun dế và thu nhỏ mất khung hình.
- **Quy trình chuẩn trên Mac (Antigravity):**
  1. Gọi `image-generator` (kèm ảnh gốc hoặc `location_sheet.jpg` làm tham chiếu) sinh **ảnh lưới `3×3` hoàn toàn KHÔNG CHỮ (`ZERO TEXT`)** theo prompt tiếng Anh chuẩn bên dưới.
  2. Chạy `scripts/compose_storyboard_board.py` để cắt 9 ô và đóng nhãn tiếng Việt sắc nét bằng font chuẩn + chạy `scripts/verify_9canh.py` kiểm định tất định.
- **Quy trình chuẩn trên Gemini Web:**
  Gọi công cụ tạo ảnh ngay trong lượt trả lời, **BẮT BUỘC truyền ảnh/khung hình người dùng vừa đính kèm làm tham chiếu**, dùng đúng mẫu prompt tiếng Anh sau (TUYỆT ĐỐI KHÔNG viết tiếng Việt vào prompt vẽ ảnh):
  > `"Using the attached real location photo(s) as the STRICT architectural and lighting reference, generate ONE vertical 9:16 (or clean 3:4) storyboard sheet divided into an exact 3x3 grid of 9 equal panels with thin dark borders. CRITICAL RULES: (1) Keep the exact same floor tiles/wood, wall color, window/railing geometry, plants, and light direction from the reference in EVERY panel — DO NOT invent new rooms, furniture, or backgrounds. (2) Simulate real 50mm-77mm (2x-3x) telephoto depth of field with natural foreground blur, photorealistic natural lighting, slight -0.7 EV rich shadows. (3) Same person in all human panels (simple casual dark/neutral outfit). (4) ZERO sentences, NO Vietnamese text, NO captions, NO banners anywhere in the image — ONLY a tiny clean white badge at top-left of each panel with number + 1 letter: '1 R', '2 C', '3 T', '4 K', '5 T', '6 C', '7 C', '8 Q', '9 R'. Panel 1: [...]. Panel 2: [...]. ... Panel 9: [...]."`
  - Nếu ảnh sinh ra bị lệch bối cảnh hoặc dính chữ lạ → tự sinh lại 1 lần và nhấn mạnh `"NO TEXT AT ALL EXCEPT 2-CHAR PANEL NUMBER, EXACT SAME ROOM AS REFERENCE"`.

---

## Bước 6 — Checklist 5 Giây Trước Khi Bấm Máy
- Quay dọc **`9:16` · `30fps`** đồng nhất cả 9 cảnh, lau sạch cụm ống kính `2x/3x`, bật **Lưới 9 ô (Grid)**.
- Chạm giữ `2` giây vào chủ thể khóa **`AE/AF Lock`** → kéo ông mặt trời xuống nửa đốt ngón tay (**`-0,7 EV`**) cho hết cháy trắng.
- Tựa cứng điện thoại giữ yên **`5–6` giây/cảnh** (lặp động tác 2 lần), không tắt mic để giữ tiếng động thật (`ASMR`) lót dưới nhạc `-22 dB`.
