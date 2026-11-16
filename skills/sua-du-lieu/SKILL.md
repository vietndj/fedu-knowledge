---
name: sua-du-lieu
description: "Tra cứu bản đầy đủ & sửa/thêm mới dữ liệu FEDU (túi mù K4, nhạc nền, kho thơ, video ý tưởng) 2 chiều từ Gemini Web về máy Mac bằng khuôn khối ===PATCH=== (0% lỗi JSON). Kích hoạt khi anh Việt bảo: sửa túi mù / lấy prompt nhạc / sửa nhạc / sửa thơ / sửa ý tưởng / sua-du-lieu."
tier: A
---

# Kỹ năng: SỬA DỮ LIỆU 2 CHIỀU TỪ GEMINI WEB (`sua-du-lieu`, Khuôn `===PATCH===`)

Xưng "em", gọi "anh Việt". Khi anh Việt yêu cầu tra cứu bản đầy đủ hoặc sửa/thêm dữ liệu cho `tuimu`, `nhac`, `tho`, `ytuong`:

## 0. Hai tầng dữ liệu — Bắt buộc mở `AGY_BRIDGE/kho/` qua `@Google Drive` trước khi tra/sửa
- **10 file trong Gem (`AGY_BRIDGE/GEM/`) CHỈ LÀ MỤC LỤC RÚT GỌN** (chứa ID, nhóm, tóm tắt và tên file `kho=...`). Không dùng mục lục Gem để lấy nội dung dài hay suy ra `base_hash`.
- Luôn dùng `@Google Drive` mở file đầy đủ tương ứng trong `AGY_BRIDGE/kho/` để lấy **100% nguyên văn** (nhất là `prompt` nhạc đầy đủ ~2.100 ký tự) và đúng **`base_hash` theo từng trường (`h_<field>=...`)**:
  - **Nhạc (`nhac`):** Tra `NHAC_871_PROMPT.txt` để biết tên file `kho=NHAC_DM_<nhóm>_p<n>`, rồi mở `NHAC_DM_<nhóm>_p<n>` trong `AGY_BRIDGE/kho/` để lấy nguyên văn trường `prompt:` và `h_prompt=...` / `h_title=...`.
  - **Túi mù (`tuimu`):** Mở `TUIMU_<NHÓM>` trong `AGY_BRIDGE/kho/` để lấy `h_q`, `h_lead`, `h_new`, `h_pro`, `h_punch`.
  - **Thơ (`tho`):** Mở `THO_FULL_p<n>` trong `AGY_BRIDGE/kho/` lấy `h_poem`, `h_explanation`, `h_quote`.
  - **Ý tưởng (`ytuong`):** Mở `YTUONG_FULL_p<n>` trong `AGY_BRIDGE/kho/` lấy `h_title_vi`, `h_quick_takeaway`, `h_key_tech`.
  - Nếu lần trước bị máy Mac từ chối, mở `AGY_BRIDGE/kho/_FEEDBACK_LATEST` để xem ngay lý do và hash đúng.

## 1. Quy tắc an toàn bắt buộc
1. **Chỉ hỗ trợ `op: update` hoặc `op: add`** — **TUYỆT ĐỐI CẤM `delete`**.
2. **Chỉ xuất khuôn khối thuần `===PATCH=== ... ===END===` — CẤM xuất JSON** (để không bao giờ gãy dấu ngoặc kép `"` hay xuống dòng).
3. **Túi mù chỉ sửa từng trường nguồn:** `q`, `lead`, `new`, `pro`, `punch`, `cat` (KHÔNG sửa gộp khối `answer` HTML).
4. **Nhạc:** Bắt buộc lấy nguyên văn full `prompt` từ `NHAC_DM_*` trước khi tạo thử hoặc chỉnh sửa. Hệ thống Mac sẽ từ chối nếu `prompt` mới ngắn hơn 80% bản gốc (trừ khi cố ý cắt ngắn và thêm dòng `allow_shrink: yes`).
5. **Bắt buộc kèm `base_hash` đúng của trường đang sửa** (`h_<field>` vừa đọc trong `AGY_BRIDGE/kho/`).

## 2. Khuôn xuất chuẩn trong khung chat (0 gọi Google Docs)
Đặt khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` ở cuối câu trả lời, bên trong là `### FILE: patch/<slug>.patch`:

```
=== AGY-PHIEN <YYYY-MM-DD HH:MM> | sua-du-lieu: <Mô tả ngắn> ===
### NOTE: HANDOFF
- Vá dữ liệu <target>: <id>.<field> (<op>)
### FILE: patch/<slug>.patch
===PATCH===
target: <tuimu|nhac|tho|ytuong>
op: update
id: <Q16 | track_id | poem_id | video_id>
field: <tên_trường>
base_hash: <mã_10_ký_tự_từ_kho>
---NEW---
Nội dung mới viết tự nhiên, xuống dòng và dùng "ngoặc kép" thoải mái.
===END===
=== HẾT PHIÊN ===
```

*(Khi `op: add` cần nhiều trường: thay `---NEW---` bằng từng đoạn `---cat---`, `---q---`, `---lead---`, `---new---`, `---pro---`, `---punch---` cho `tuimu`, hoặc `---title---`, `---category---`, `---bpm---`, `---prompt---` cho `nhac`. Có thể đặt nhiều khối `===PATCH=== ... ===END===` trong cùng 1 file).*

## 3. Báo gọn trên khung chat (≤ 5 dòng phần đầu)
Ghi rõ tên file `kho/...` vừa đọc, tóm tắt (`target · id · field`), đặt khối `=== AGY-PHIEN ... === HẾT PHIÊN ===` bên dưới và kết thúc bằng:
`Đã xuất bản vá — máy Mac sẽ kiểm tra hash, build, deploy lên web thật và đồng bộ lại Drive trong 60 giây.`
