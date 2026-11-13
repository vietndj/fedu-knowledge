# QUY TẮC: TỰ ĐỘNG NÂNG CẤP CAROUSEL → YOUTUBE

## Kích hoạt tự động
Khi người dùng yêu cầu **kiểm tra, sửa, hoặc nâng cấp từ 2 file báo cáo Carousel trở lên** (bất kỳ cách diễn đạt nào liên quan đến carousel, báo cáo phân cảnh, reports, YouTube iframe, sửa video trong reports/) — AI BẮT BUỘC phải:

1. **DỪNG LẠI, không thực thi ngay**
2. **Viết lệnh chạy `carousel_yt_upgrade.js`** đầy đủ với danh sách file cần xử lý
3. **Hỏi anh Việt:** "Lệnh này xử lý N file. OK để chạy?"
4. Khi anh gõ **OK** → thực thi

## Cú pháp lệnh

> _(lệnh chạy trên Mac — đã lược khi lên Web)_

## Quy trình 6 bước mỗi file (đã mã hóa trong script)

| Bước | Hành động | Điều kiện dừng |
|---|---|---|
| 1 | Quét HTML: đếm `<video>`, `<img>`, `<iframe>` trong `.carousel-stack` | Đã có youtube iframe → bỏ qua. Chỉ có 1 video 0 ảnh → bỏ qua |
| 2 | Tải video từ `<video src="...">` (Drive API proxy / R2 / Drive direct) | 404 tất cả nguồn → ❌ ghi lỗi, sang file tiếp |
| 3 | Upload YouTube Unlisted (`upload_yt.py`) | **Quota/Auth error → DỪNG TOÀN BỘ TASK** |
| 4 | Sửa HTML: thay `<video>` → `<iframe>` YT, giữ `<img>`, CSS 75vh + scroll-snap, nút ▲▼, sửa JS, verify `node -c` | JS lỗi 3 lần → ghi cảnh báo |
| 5 | Git push + `curl -sL` verify deploy (60 lần × 5s, follow redirect) | 5 phút không deploy → ghi lỗi |
| 6 | Playwright chụp production, bắt JS error | JS runtime error → ghi cảnh báo |

## Sửa lỗi chính so với lệnh cũ

| Lỗi cũ | Sửa mới |
|---|---|
| Dùng `yt-dlp` tải IG → đếm MP4 → kết luận "Single video" sai | Quét trực tiếp HTML: `<video>` + `<img>` trong `.carousel-stack` |
| `curl -s` không follow redirect 308 Cloudflare | `curl -sL` follow redirect |
| Thay toàn bộ `.carousel-stack` bằng iframe | Chỉ thay `<video>` → `<iframe>`, giữ nguyên `<img>` |
| CSS nhắm vào `.video-wrap` (không tồn tại) | CSS nhắm vào `.video-player-container` |

## Kết quả đầu ra
- `carousel_results.json` — JSON chi tiết
- `carousel_results.md` — Bảng markdown tổng hợp
- `screenshots/` — Ảnh chụp production mỗi file đã sửa

## Workspace
- Script: `[đường-dẫn-Mac]`
- Token YouTube: `[đường-dẫn-Mac]`
- Upload script: `[đường-dẫn-Mac]`

## Ngoại lệ (thực thi ngay, không cần hỏi)
- Sửa đúng 1 file carousel → làm luôn
- Anh nói rõ "làm luôn", "cứ chạy", "không cần hỏi"