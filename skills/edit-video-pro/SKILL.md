---
name: edit-video-pro
description: "Mantra: EDIT PRO COA / DỰNG VIDEO PRO COA / EDIT PRO / DỰNG VIDEO TRONG THƯ MỤC NÀY / LÀM VIDEO TRONG THƯ MỤC / EDIT VIDEO TRONG THƯ MỤC / LÊN KẾ HOẠCH EDIT / EDIT VIDEO PRO / CẬP NHẬT EDIT VIDEO / CẬP NHẬT PHIÊN BẢN MỚI CỦA EDIT VIDEO / CẬP NHẬT EDIT PRO / UPDATE EDIT VIDEO / NÂNG CẤP EDIT VIDEO PRO / ẢNH THẺ EDIT.FEDU.VN / EDIT PRO BÁO ĐEN / EDIT 2 CAM. Hệ thống dựng video chuyên gia, 2 Cam, Cut-on-Action COA V4.2 & chuỗi B-Roll đa góc máy (PA1..PA5, Style G1..C10, CTA O1..O6, 4 Animation BĐS 3D M12/M13/Earth/Flycam & Verifier 43 cổng)."
tier: B
---

> **CHẾ ĐỘ GEMINI WEB (Tầng B)** — Đây là bản Web của kỹ năng `edit-video-pro` từ hệ thống Antigravity của anh Việt.
> - Bỏ qua mọi lệnh shell/python, đường dẫn `[đường-dẫn-Mac]`, cổng CDP, Verifier script: những thứ đó chỉ chạy trên Mac.
> - Giữ nguyên toàn bộ tư duy, khuôn, luật văn phong, cổng kiểm định bằng mắt.
> - Trên Web chỉ lên phương án + spec JSON/code đầy đủ trong khối `agy-patch`; việc render/dựng/ship để Antigravity chạy trên Mac.
> - Kết thúc phiên: làm theo kỹ năng `agy-cau-noi` (ghi kết quả vào Google Docs `AGY_INBOX`).

> Tài liệu kèm: `references/catalog_bds_style_spec.md`, `references/modes_quickstart.md`, `references/v3_spec_and_upgrade_index.md`


<!-- [SKILL_CONTRACT: 8 · ACK: c8-280fedu · VERSION: 3.8.10] -->

# EDIT VIDEO PRO V3.9 — CHUYÊN GIA `EXPERT`, 2 CAM FULL STUDIO, MÀN HÌNH CUỐI `CTA OUTRO` TỰ QUYẾT ĐỊNH THƯƠNG HIỆU & HẸN GIỜ TỰ ĐỘNG `60 GIÂY`

> **Định tuyến Tự động Tầng Đặc Quyền `HẬU KÌ` (`../hau-ki/SKILL.md`):** Nếu trên máy hiện tại tồn tại `../hau-ki/SKILL.md` (`../hau-ki/profile.json`) và người dùng KHÔNG yêu cầu tường minh *"dùng kỹ năng edit pro đã xuất bản"*, hệ thống tự động chạy ở chế độ **`HẬU KÌ` (`tier=master`)** (mở khóa trọn bộ công nghệ: Hook Staggered Kinetic Exit, Cảnh Trám Bento Dense 0% trống chỗ, Chủ đề Công nghệ AI thông minh, Tự sinh Logo Vector theo nội dung + Bảng Tổng Kết Các Quyết Định Tự Động ở cuối). Khi người dùng nói *"dùng kỹ năng edit pro đã xuất bản"*, truyền `--tier published` để chạy đúng bản đóng gói đại chúng.
>
> **Nguyên Lý Gốc V4.1 (`smart_guards.py`):** Engine tự xử lý tất định rough-cut A1..A6, quét giơ sổ V1, ngắt dòng `COMPOUND_SAFE_WRAP_ALL`/`SUB_ORPHAN`, khóa `G7_DESC_GROUNDED`/`P3_POSTER_NO_REPEAT` — chi tiết ở [`references/catalog_bds_style_spec.md`](file://[đường-dẫn-Mac]).

> **Cổng xác nhận tự động cập nhật (`--contract-ack`):** Nếu lệnh `scan-extract` vừa tự động nâng cấp lên phiên bản mới và in thông báo `[SKILL_CONTRACT_UPDATED: ...]`, ở lệnh kế tiếp (`curate-sequence`, `propose-fixes`, `apply-answers` hoặc `stop-decide`) bạn **bắt buộc** truyền thêm cờ `--contract-ack c8-280fedu` để xác nhận đã đọc quy trình V3.9 mới này. Các lượt chạy thông thường không cần truyền cờ này.

Kích hoạt ngay khi người dùng:
- **Khi người dùng yêu cầu `"edit video theo kiểu của Hằng"`, `"edit theo kiểu Hằng"`, `"làm video theo kiểu của Hằng"`, `"edit Hằng"`, `"edit Alice"`:**
  1. Nếu trên máy chưa có `$HOME/.gemini/config/skills/edit-hang/scripts/spa_pa2_engine.py`, tự động cài/cập nhật trong 3 giây:
     - macOS/Linux: `curl -fsSL https://media.fedu.vn/skills/edit-hang/install.sh | bash`
     - Windows: `powershell -NoProfile -ExecutionPolicy Bypass -Command "irm 'https://media.fedu.vn/skills/edit-hang/install.ps1' | iex"`
  2. Đọc ngay `$HOME/.gemini/config/skills/edit-hang/SKILL.md` và chạy quy trình 4 bước của `spa_pa2_engine.py --brand alice_thanh_hang` (`extract` tự nhận cảnh trám xung quanh -> biên tập `content.json` -> `audit` -> `render`) để xuất video có sẵn Logo `ALICE` cánh lá đỏ, Hook đã nhớ và Màn hình kết `Silk Ivory Atelier` kèm nút CTA đỏ.
- Gõ **`edit coa`** (hoặc **`hậu kì coa`**, **`dựng coa`**, **`vừa đi vừa nói`**, **`edit chuyển cảnh`**, **`edit video theo COA`**): Chạy trực tiếp bộ định tuyến tự nhận diện 1 lệnh duy nhất:
  `"$HOME/.mfx_v3/venv/bin/python" "$HOME/.gemini/config/skills/edit-video-pro/scripts/edit_video_pro_engine.py" coa --input "<FILE_HOẶC_THƯ_MỤC_COA>" --out "<OUT_MP4>" [--raw] [--hook-layout M10] [--outro O3]`
  * **Video có lời thoại (`spoken_words >= 8`, mặc định trên máy `master`):** Chạy **`COA PRO STUDIO V4.3`** (`coa_pro_studio_engine.py`: Lõi `COA V4.3 Chỉ lấy lần cuối` + `Hook Công Nghệ 3D Layer` + `Cảnh Trám/Motion Graphic 12 nguyên lý CHỈ trong lúc nói dài, 0% đè lên Vùng Thiêng chuyển cảnh` + `Phụ đề từ ghép` + `Nhạc 4-Diamond` + `CTA Outro`, xuất `cutaway_zone_strip.jpg` & `coa_seam_audit_strip.jpg`). Gõ **`edit coa thô`** (`--raw`) nếu chỉ cần cắt COA sạch không đồ họa.
  * **Video/Thư mục B-Roll không lời (`spoken_words < 8`):** Tự động chạy **`COA B-Roll Sequence V4.2`** (`broll_sequence_engine.py` + `verify_coa_sequence.py`).
- Gõ **`edit pro`** kèm kéo thả **1 thư mục** hoặc **1 file video lẻ** vào ô chat (không cần đặt tên `aroll`), hoặc gõ **`edit pro <đường dẫn thư mục hoặc file video>`**, hoặc nói tự nhiên kèm đường dẫn: **"Dựng video trong thư mục này"**, **"Làm video..."**, **"Edit video..."**, **"Edit Video Pro"**.
- **Khi người dùng yêu cầu `"edit 2 cam"` / `"edit hai cam"` (xuất MP4 sản phẩm và/hoặc đẩy vào Project CapCut Đa Lớp 4 Timelines):** Đọc mục 1 tại [`references/modes_quickstart.md`](file://[đường-dẫn-Mac]) và chạy `scripts/dualcam_engine.py run-both --dir "<THƯ_MỤC_2_CAM>" --capcut-project "<Tên_Project>" --out-mp4 "<OUT_EDIT_PRO_MP4>" --out-clean-switch-mp4 "<OUT_SWITCH_MP4>" --brand-name "<TÊN_THƯƠNG_HIỆU_TỰ_QUYẾT_ĐỊNH>" --brand-tagline "<ĐỊNH_VỊ_NGẮN>" --cta-text "<NÚT_CTA_KÊU_GỌI_HÀNH_ĐỘNG>"` (nếu thiếu tên thương hiệu/CTA, bắt buộc tự suy từ bối cảnh thư mục & lời thoại, không để trống CTA Outro cuối video).
- **Khi yêu cầu cập nhật / nâng cấp (`"cập nhật edit pro"`, `"update edit video"`...) hoặc thả thẻ QR `edit.fedu.vn`:**
  1. **Trên máy chủ của anh Việt (`../hau-ki/profile.json` tồn tại):** Tự động gọi Bộ Điều Phối Trung Tâm V2.0 `"$HOME/.mfx_v3/venv/bin/python" "$HOME/.gemini/config/skills/edit-video-pro/scripts/fedu_skill_hub.py"` (`--target <all|core|spa|hang|dung|tham|viet>` để đồng bộ Lõi + khóa SHA-256 `_vendor` + đóng gói các nhánh học viên; `doctor` để khám sức khỏe 0% rò rỉ thương hiệu chéo; `onboard` để khởi tạo & đóng gói chi nhánh học viên mới 1 chạm; `list-students` & `gates` để tra cứu sổ cái cổng 3 tầng `presets/gates_registry.json`).
  2. **Trên máy học viên (Đã có `~/.mfx_v3/venv`):** Windows: `& "$HOME\.mfx_v3\venv\Scripts\python.exe" "$HOME\.gemini\config\skills\edit-video-pro\scripts\edit_video_pro_engine.py" update` | macOS/Linux: `"$HOME/.mfx_v3/venv/bin/python" "$HOME/.gemini/config/skills/edit-video-pro/scripts/edit_video_pro_engine.py" update`
  3. **Máy mới chưa cài:** Windows: `powershell -NoProfile -ExecutionPolicy Bypass -Command "irm 'https://edit.fedu.vn/win' | iex"` | macOS/Linux: `curl -fsSL https://edit.fedu.vn/mac | bash`

## ⚡ CỔNG CHỐNG NGHẼN BƯỚC 0 (FAST-TRACK K4 — 0.3s, CẤM MÒ FILE THỦ CÔNG)
Khi nhắc tới học viên K4 hoặc `"k4 ho so"`, **BẮT BUỘC chạy ngay 1 lệnh duy nhất ở Bước 1** (`0.3s`):
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- **4 ĐIỀU CẤM TUYỆT ĐỐI:** (1) **CẤM `find "$HOME"`** mò thư mục học viên hay `music_db.json` (Hồ sơ ở `"$HOME/Documents/k4 ho so/<slug>"`, nhạc ở `[đường-dẫn-Mac]` & `"$HOME/Documents/CODE/nhac-fedu/data/music_db.json"`); (2) **CẤM đọc chồng chéo 3–4 `SKILL.md`** (`edit-video-pro` + `auto-edit-video` + `cinematic-video-auditor` + `nhac-bank`); (3) **CẤM `read_file` nguyên cục `video_styles_registry.json` / `bgm_catalog_v3.json`** (`PERF GUARD G1`); (4) **CẤM đọc toàn bộ `.html` khám kênh** (đã được `k4_fast_preflight.py` trích yếu 30 dòng).

## LUẬT BẮT BUỘC V3.6 (KHÔNG ĐƯỢC BỎ BƯỚC)
1. **Cú pháp 1 dòng phẳng theo HĐH (CẤM tách lệnh lẻ / CẤM tự tạo lại `venv`):**
   - **Windows (PowerShell):** `& "$HOME\.mfx_v3\venv\Scripts\python.exe" "$HOME\.gemini\config\skills\edit-video-pro\scripts\edit_video_pro_engine.py" ...`
   - **macOS / Linux:** `"$HOME/.mfx_v3/venv/bin/python" "$HOME/.gemini/config/skills/edit-video-pro/scripts/edit_video_pro_engine.py" ...` (nếu thiếu venv gọi `python3`). Nhắc chọn dòng 3 (`Yes, and always allow...`) nếu hỏi quyền ở Bước 1.
2. **Phân loại `CONTENT_MODE=BROLL` vs `CONTENT_MODE=EXPERT` tại `scan-extract`:**
   - **`CONTENT_MODE=BROLL`:** Nếu có `[BROLL_CURATION_REQUIRED]`, chạy **Bước 1.2b (`curate-sequence`)** theo 6 Luật `R1..R6` để nhận `===DỪNG 1===`. Chỉ có **1 Điểm dừng (`BROLL_STOP1`)** hiển thị 3 phương án nhịp (`1`: Nhịp Gọn · `2 ⭐`: Mặc định · `3`: Nhịp Thư), giữ đủ các góc đã duyệt, không hỏi Thương hiệu/Chữ/Bản đồ.
   - **`CONTENT_MODE=EXPERT`:** Gồm **Điểm dừng 1 (`EXPERT_STOP1`)** và **Điểm dừng 2 (`EXPERT_STOP2`)**, đều có bảng ảnh `1 / 2 ⭐ / 3`.
3. **Bảng Kèm Ảnh + Gõ `1`, `2`, `3` + Hẹn Giờ Tự Động `60 Giây`:**
   - Ở `===DỪNG 1===` và `===DỪNG 2===`, **BẮT BUỘC dán nguyên văn 100% khối chữ và bảng ảnh Markdown** giữa cặp thẻ.
   - **Hẹn giờ 60 giây (`schedule` tool):** Ngay trong lượt in bảng (`[STOP_OPEN] id=<STOP_TOKEN> default=2 timeout=60`), gọi `schedule` (`DurationSeconds: 60`, `TimerCondition: "any"`, `Prompt: "Hết 60 giây chờ điểm dừng <STOP_TOKEN>, tự động chạy phương án 2 (Mặc định)"`) rồi dừng lượt chờ.
   - **Khi nhận phản hồi hoặc hết 60 giây (`stop-decide` khóa `O_EXCL`):** Gõ `1`, `2`, `3` (`làm đi`/`ok` -> `2`) gọi `--answer "<1|2|3>" --source user`; hết 60s gọi `--answer 2 --source timer` để tự dựng **Phương án `2` ⭐**.
4. **Quy tắc kế hoạch `EXPERT` (clip `>= 8s`, tổng `N >= 2` khe trong `planner_prompt_payload.json`):**
   - Số cảnh **Poster → Motion Graphic** (`compare_sheet`, `anatomy_sheet`, `roadmap_sheet`, `proportion_sheet`, `checklist_sheet`, `macro_quote`) = `ceil(N / 2)` (`>= 1`); số cảnh **`ai_image`** >= `1` (không có B-Roll/Maps thì `= floor(N / 2)`); đan xen không xếp 3 cảnh cùng nhóm liên tiếp.
   - **Tiêu đề `title` trên Poster BẮT BUỘC viết Sentence case**, cấm IN HOA TOÀN BỘ.
   - **Hook đầu video (`0.0s .. hook_dur_s`):** Cung cấp `hook` và `hook_options` (`A`, `B`, `C`): `kicker` IN HOA `<= 4` từ, `l1` IN HOA `<= 22` ký tự, `l2` chữ thường/nhấn `<= 30` ký tự, 0% bịa số, 0% dấu `...`.

---


### 1.3. Bộ 10 Trường Phái Hook 3D (`M1..M10` · Khử Giật Chớp), 5 Hook `PA1..PA5`, 4 Animation BĐS 3D, Chế Độ `VLOG TỰ SỰ`, 10 Style `--palette`, 6 Outro `O1..O6`
- **Chế độ `VLOG TỰ SỰ` (`vlog` — Vlog đời thường `>= 8` cảnh montage, hạ nhạc `-18.5 dB`, CTA cá nhân):** Đọc mục 2 tại [`references/modes_quickstart.md`](file://[đường-dẫn-Mac]) (`--style nhat_ky|dien_anh|lua_moc`, lệnh `edit_video_pro_engine.py vlog --input ... --out ...`).
- Danh mục đầy đủ (lệnh script, tên palette, mô tả outro & bảng Style Vlog) → [`references/catalog_bds_style_spec.md`](file://[đường-dẫn-Mac]). Chỉ đọc khi người dùng gọi đúng chế độ/kiểu đó.


## BƯỚC 1 — QUÉT VIDEO/THƯ MỤC & CHUẨN BỊ ĐIỂM DỪNG 1

### 1.1. Chạy `scan-extract` (truyền thư mục hoặc 1 file video lẻ vào `--dir`)
- **Windows (PowerShell):**
```powershell
& "$HOME\.mfx_v3\venv\Scripts\python.exe" "$HOME\.gemini\config\skills\edit-video-pro\scripts\edit_video_pro_engine.py" scan-extract --dir "<THƯ_MỤC_HOẶC_FILE_VIDEO>"
```
- **macOS / Linux (Bash/Zsh):**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_
- Ghi nhớ ngay `WORK_DIR=`, `OUT=` và `CONTENT_MODE=BROLL|EXPERT`.
- **Nếu báo `[BLOCKED_BURNED_SUBTITLES]`:** Dán thông báo chặn, nhờ người dùng đổi sang file video gốc chưa chèn chữ và **DỪNG HẲN**.

### 1.2a. Nếu `CONTENT_MODE=EXPERT`: Rà soát lời thoại và gọi `propose-fixes` (nếu có chữ nghe nhầm)
Đọc kỹ từng câu trong `[CLAUSES_FOR_HOMOPHONE_SWEEP]`. Nếu phát hiện từ đồng âm / nghe nhầm:
- Cặp 1 âm tiết bắt buộc gắn mã câu `"C12:từ_sai=từ_đúng"`; cụm 2–4 âm tiết có thể ghi toàn cục `"cụm sai=cụm đúng"`.
- Cụm nghi ngờ tên riêng chưa chắc chắn thì truyền vào `--unsure "cụm chưa chắc"`.
- Lệnh (1 dòng):
  - Windows: `& "$HOME\.mfx_v3\venv\Scripts\python.exe" "$HOME\.gemini\config\skills\edit-video-pro\scripts\edit_video_pro_engine.py" propose-fixes --work-dir "<WORK_DIR>" --suggest "cụm sai=cụm đúng"`
  - macOS / Linux: `"$HOME/.mfx_v3/venv/bin/python" "$HOME/.gemini/config/skills/edit-video-pro/scripts/edit_video_pro_engine.py" propose-fixes --work-dir "<WORK_DIR>" --suggest "cụm sai=cụm đúng"`

### 1.2b. Nếu `CONTENT_MODE=BROLL` và có `[BROLL_CURATION_REQUIRED]`: Mở ảnh Curation & Chạy `curate-sequence` theo 6 Luật `R1..R6`
1. Mở xem TẤT CẢ các ảnh `CURATION_SHEETS` (`sequence_curation_sheet_*.jpg`), đọc `<WORK_DIR>/curation_template.json` và 6 Luật `R1..R6` tại mục 3 [`references/modes_quickstart.md`](file://[đường-dẫn-Mac]) để tạo `<WORK_DIR>/sequence_curation.json` (`R1` đổi góc=`KEEP`, `R2` bản lỗi=`DROP_RETAKE_OF_Txx`, `R3` nối động tác `seam_to_next: Lx-Fy`, `R4` UI nhân quả=`KEEP`, `R5` khóa `exit_t + 0.10`, `R6` ưu tiên chân máy).
2. Chạy kiểm định 7 Cổng `curate-sequence --work-dir "<WORK_DIR>" --curation-file "<WORK_DIR>/sequence_curation.json"` (lặp sửa `[G1..G7]` nếu `[CURATION_REJECTED]` tới khi nhận `===DỪNG 1===`).

### 1.3. Dán nguyên văn khối `===DỪNG 1=== ... ===HẾT===` và bật hẹn giờ 60 giây
1. Copy **nguyên văn từng dòng (bao gồm cả hình ảnh `![...](file:///...)`, bảng phương án `1 / 2 ⭐ / 3` và các dòng gạch đầu dòng `- `)** nằm bên trong cặp `===DỪNG 1===` và `===HẾT===`.
2. Gọi công cụ `schedule` (`DurationSeconds: 60, TimerCondition: "any"`) cho mã dừng tương ứng (`BROLL_STOP1` hoặc `EXPERT_STOP1`) rồi kết thúc lượt để chờ người dùng gõ `1`, `2`, `3` trong 60 giây.

---

## BƯỚC 2 — CHỐT PHƯƠNG ÁN ĐIỂM DỪNG 1 (`stop-decide`) & HIỂN THỊ ĐIỂM DỪNG 2

### 2.1. Xử lý lựa chọn ở Điểm dừng 1 (hoặc tự động chạy khi hết 60 giây)
- **Khi người dùng gõ `1`, `2`, `3`, `làm đi`, `ok` (hoặc khi hẹn giờ 60 giây nổ):**
  - Chạy lệnh nguyên tử `stop-decide`:
    - Windows: `& "$HOME\.mfx_v3\venv\Scripts\python.exe" "$HOME\.gemini\config\skills\edit-video-pro\scripts\edit_video_pro_engine.py" stop-decide --work-dir "<WORK_DIR>" --stop <BROLL_STOP1|EXPERT_STOP1> --answer "<1|2|3>" --source <user|timer> --out "<OUT>"`
    - macOS / Linux: `"$HOME/.mfx_v3/venv/bin/python" "$HOME/.gemini/config/skills/edit-video-pro/scripts/edit_video_pro_engine.py" stop-decide --work-dir "<WORK_DIR>" --stop <BROLL_STOP1|EXPERT_STOP1> --answer "<1|2|3>" --source <user|timer> --out "<OUT>"`
  - **Nếu là `BROLL_STOP1`:** Lệnh `stop-decide` tự động kết xuất hoàn chỉnh video Chuỗi B-Roll Đa Góc Máy ra `<OUT>` và kiểm định 5 cổng `G0..G4` — báo ngay kết quả kèm video `<OUT>` và kết thúc!
- **Nếu ở `EXPERT_STOP1` người dùng gõ chữ tự do (tên thương hiệu, từ cần sửa riêng, link Google Maps, hoặc thả ảnh logo):**
  - Gọi `stop-decide --work-dir "<WORK_DIR>" --stop EXPERT_STOP1 --answer "<nội dung>" --source user --lock-only` để khóa hẹn giờ, sau đó gọi `apply-answers --work-dir "<WORK_DIR>"` kèm các cờ tương ứng (`--brand-name`, `--speaker-name`, `--logo`, `--fix-asr`, `--maps-url`, `--accept-proposed`).

### 2.2. (Chỉ dành cho `EXPERT`) Lập kế hoạch `plan_draft.json` → `apply-plan` → `generate_image` → `import-ai-images` → `preview-cards`
1. Viết `<WORK_DIR>/plan_draft.json` từ `<WORK_DIR>/planner_prompt_payload.json` theo đúng cấu trúc `hook`, `hook_options`, `slots` (`compare_sheet`, `anatomy_sheet`, `roadmap_sheet`, `checklist_sheet`, `proportion_sheet`, `ai_image`, `map_zoom`...), `recap`.
2. Chạy `apply-plan --work-dir "<WORK_DIR>" --plan-file "<WORK_DIR>/plan_draft.json"`.
3. Với mọi khe `"kind": "ai_image"`, gọi `generate_image` (hậu tố cấm chữ `"Vertical 9:16 editorial photography, realistic natural lighting, shallow depth of field, clean composition, strictly NO text, NO letters, NO numbers, NO watermarks, NO logos, NO UI elements."`), kiểm tra không có chữ rác rồi chạy `import-ai-images --work-dir "<WORK_DIR>" --image "B2=<path>" --text-verdict "B2=none"`.
4. Chạy `preview-cards --work-dir "<WORK_DIR>"`:
   - Dán **nguyên văn khối nằm giữa `===DỪNG 2===` và `===HẾT===`** (gồm ảnh so sánh 3 phương án `stop2_choice_sheet.jpg`, bảng chọn `1 / 2 ⭐ / 3` có nhúng `pa1_thumb.jpg`, `pa2_thumb.jpg`, `pa3_thumb.jpg` và bảng các cảnh minh họa kèm ảnh xem trước).
   - Đặt ngay hẹn giờ `schedule` (`DurationSeconds: 60, TimerCondition: "any"`) cho `EXPERT_STOP2` và kết thúc lượt để chờ.

---

## BƯỚC 3 — KẾT XUẤT VIDEO CHUYÊN GIA (`EXPERT_STOP2`) & KIỂM ĐỊNH 43 CỔNG
Ngay khi người dùng gõ **`1`**, **`2`**, **`3`** (hoặc `làm đi`, `ok`), hoặc ngay khi hẹn giờ **60 giây** nổ ở **DỪNG 2**, chạy lệnh `stop-decide` cho `EXPERT_STOP2` để kết xuất video ra `<OUT>`:

- **Windows (PowerShell):**
```powershell
& "$HOME\.mfx_v3\venv\Scripts\python.exe" "$HOME\.gemini\config\skills\edit-video-pro\scripts\edit_video_pro_engine.py" stop-decide --work-dir "<WORK_DIR>" --stop EXPERT_STOP2 --answer "<1|2|3>" --source <user|timer> --out "<OUT>"
```
- **macOS / Linux:**
> _(lệnh chạy trên Mac — đã lược khi lên Web)_

- Kiểm tra bảng ảnh `<WORK_DIR>/preview_12frames.jpg`, đọc kết quả `VERIFIER` rồi báo trung thực kết quả kèm đường dẫn video `<OUT>` hoàn chỉnh. Tuyệt đối cấm báo hoàn tất nếu Verifier chưa `PASS`.


## 0B & 0C. CHUẨN DỰNG V3.9 (43 CỔNG) & CHỈ MỤC NÂNG CẤP FULL STUDIO
- Xem [`references/catalog_bds_style_spec.md`](file://[đường-dẫn-Mac]) (mục 0B & 0C) và `references/v3_spec_and_upgrade_index.md`.

---
## ⚡ Chuẩn Chuyển Động 12 Nguyên Lý Tự Động (Motion Core V8)
- **Động cơ vật lý dùng chung:** Mọi chuyển động thẻ, chữ, huy hiệu, biểu đồ, nút CTA và Outro bắt buộc dùng `_vendor.motion_core` (đồng bộ từ `[đường-dẫn-Mac]`, hồ sơ `talking_head`: có lấy đà ngược chiều, lò xo 1 nhịp nảy, nén giãn `sx*sy=1`, lệch pha Cha–Con và thoát cảnh `9 frames`; cấm viết hàm easing bậc 3 đơn điệu cục bộ).
- **Hậu kiểm tự động (Chế độ Cảnh báo `--mode warn`):** Sau khi xuất `.mp4`, hệ thống tự chạy `[đường-dẫn-Mac] --video <out.mp4> --profile talking_head --mode warn` (exit `0` không chặn render, ghi chỉ số 12 nguyên lý vào `motion/self_learning_ledger.jsonl`).
