---
name: analyze-video
description: "Link video Reels/TikTok/Shorts/FB → phân tích phân cảnh qua Gemini Web (Mac cắt shot 0 token, Gemini Web soi video, tự lên ytuong.fedu.vn). Bản V2-WEB 13/11/2026; bản cũ soi ảnh trong Antigravity = analyze-video-may (đang tạm tắt)."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `analyze-video` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).
>
> **LUỒNG WEB ⇄ MAC (ưu tiên):** Mac đã tải video, cắt shot, đẩy ảnh lên R2 và đưa YouTube. Khi anh gõ `PHÂN TÍCH VIDEO <mã>`: mở Docs `AGY_VIDEO_<mã>` trong Drive `AGY_BRIDGE/video_jobs` → xem video (link YouTube, hoặc anh đính kèm `<mã>.mp4` từ Drive) → soi từng shot theo mốc giờ → in báo cáo 4 phần ra chat → `CHỐT PHIÊN` đúng 2 FILE `video/<folder>/shots.json` + `video/<folder>/sync.json` như yêu cầu trong Docs. KHÔNG tự cắt ảnh, KHÔNG đổi số shot. Link ảnh .webp và @Drive mp4 em KHÔNG nhìn được → bắt buộc có mp4 đính kèm trong chat; không thấy hình thì KHÔNG CHỐT PHIÊN. sync.json phải có `"nguon_hinh": "video"`.

> Tài liệu kèm: `references/broll-and-storyboard-pipeline.md`, `references/carousel-yt-upgrade.md`, `references/examples_and_catalog.md`, `references/youtube-token-troubleshoot.md`


# PHÂN TÍCH VIDEO V2-WEB — Mac làm tay chân, Gemini Web làm đầu óc

Agent trong Antigravity **KHÔNG soi ảnh, KHÔNG viết phân tích, KHÔNG sửa shot_info.json**. Chỉ gõ 1 lệnh rồi báo kết quả.
Model nhẹ nhất là đủ. Hết quota hẳn → anh Việt tự gõ cùng lệnh trong Terminal (0 token Antigravity).

## Quy trình (1 lệnh)
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
Chạy nền (`WaitMsBeforeAsync` 500), chờ thông báo xong, KHÔNG poll. Lệnh tự làm trọn vòng:
1. `check_scene_duplicate.py` — đã có thì in link cũ và dừng (`--force` để làm lại).
2. `analyze_and_upload.py` — tải, cắt shot, keyframe → R2, YouTube Sabakiz, Drive (script, 0 suy luận).
3. Đẩy Docs `AGY_VIDEO_<mã>` (shot + lời thoại + taxonomy + few-shot) và mp4 lên Drive `AGY_BRIDGE/video_jobs`.
4. `gemini_chat.py` qua Chrome CDP 9223 (/u/2 vietnd025) đính kèm mp4 → Gemini Web soi video → ghi `shots.json` + `sync.json` vào AGY_INBOX.
5. Dò AGY_INBOX (≤ 20 phút) → `bridge.py pull` → kiểm định (đủ shot, đủ khóa, id taxonomy, `nguon_hinh` = video/anh) → `sync_ai_analysis.py` + `upgrade_ideas_ai_native_v2.py` → ytuong.fedu.vn.

## Báo anh Việt (≤ 6 dòng)
Link báo cáo web + số shot + 1 câu `overview` (đọc `inbox/<phiên mới nhất>/files/video/<folder>/sync.json`). Không chép lại phân tích — bản đầy đủ nằm trên web và trong luồng Gemini.

## Mã lỗi
| Mã | Nghĩa | Xử lý |
|---|---|---|
| 2 | tải/cắt lỗi hoặc không vào được luồng Gemini (sai tài khoản, Chrome 9223 tắt) | báo anh, đọc 20 dòng cuối log |
| 3 | gửi Gemini lỗi / Gemini báo không ghi được | mở tab Gemini xem, gửi lại |
| 4 | quá 20 phút INBOX chưa có kết quả | Gemini xong sau thì `cau ve` |
| ❌ kiểm định | Gemini trả thiếu khóa/thiếu shot | nhắn lại luồng đó yêu cầu sửa, rồi `cau ve` |

## Đường cũ (tạm tắt — tốn token)
Chỉ dùng khi anh nói `PHÂN TÍCH MÁY <link>` hoặc Web hỏng ≥ 2 lần: hỏi anh trước, rồi đọc `[đường-dẫn-Mac]` làm theo (soi ảnh view_file, ~15–45 lượt model).
Khôi phục hẳn bản cũ: `tar xzf "[đường-dẫn-Mac] gia/agy_bridge/backups/analyze-video_skill_20261113.tgz" -C [đường-dẫn-Mac]`.

## Workflow phụ (giữ nguyên)
| Workflow | Trigger | File |
|---|---|---|
| Carousel → YouTube | sửa ≥ 2 báo cáo carousel | `references/carousel-yt-upgrade.md` |
| B-Roll Bank / Storyboard | `UP BROLL`, `/storyboard` | `references/broll-and-storyboard-pipeline.md` |
| YouTube token | lỗi upload kênh, quota | `references/youtube-token-troubleshoot.md` |
| Catalog nền tảng, 12 chốt chặn | Shopee/Lazada, deploy | `references/examples_and_catalog.md` |
