# Chi Tiết Kỹ Thuật V3.5/V3.7 & Chỉ Mục Nâng Cấp Nhanh (`edit-video-pro`)

## 1. Chuẩn Dựng Video Chuyên Gia V3.5 (Chốt Cùng Thư Ký Claude2 — Áp Dụng Tất Định)
1. **Tầng 0 — Rough-Cut Tự Động (Cắt Khoảng Lặng & Lặp Ý / Nói Vấp 3 Tầng trước khi lên EDL):**
   - Trong `scan-extract` (chế độ `EXPERT`), hệ thống tự động chạy `perform_roughcut_on_aroll`:
     - **Hysteresis RMS Silence Detector (`10ms` hop):** Bắt chính xác mọi khoảng nghỉ nhìn kịch bản / lấy hơi dài (`>= 0.40s`), giữ đệm thoại tự nhiên (`pre_pad=0.06s`, `post_pad=0.09s`) và micro-fade `8ms` (`384` mẫu @ 48kHz) chống tiếng click.
     - **3-Tier Retake Detector:** Tự động cắt các đoạn nói nháp/lặp lại và chỉ giữ lại **lần nói cuối hoàn chỉnh nhất** dựa trên: (a) `retake_bridge` (từ kéo dài bắc cầu qua khoảng nghỉ `>= 0.70s`), (b) `ngram4_retake` (cụm `>= 4` từ lặp lại trong `<= 25s`), (c) `subclause_retake` (cụm 2–3 từ nói vấp giữa vế câu kèm từ chỉ định `đấy/đó/thôi/này` rồi nói lại).
     - **Đồng bộ Hình–Tiếng tuyệt đối (`0.000000s` drift):** Lượng tử hóa theo chỉ số khung hình `target_fps` (`2000` mẫu âm thanh / khung ở `24fps`), xuất `_aroll_roughcut.mp4` làm nguồn chuẩn cho toàn bộ các bước sau.
2. **Căn Chỉnh Bố Cục Khuôn Mặt Chủ Thể (`OpticalArollFramer` Dynamic Overscan):**
   - Tự động tính hệ số phóng nền `s0 = max(s_cover, min(s_need, s_ceil))` để kéo tâm mặt người nói về đúng **Trục Vàng Điện Ảnh `(X = 540, Y = 700)`** (mắt ở 1/3 trên `Y ≈ 640..680px`, kích thước mặt `>= 215px`), triệt tiêu hoàn toàn lỗi người bị tụt thấp (`Y > 900px`) hoặc lệch trục ngang.
3. **Cảnh Trám B-Roll Full Màn Hình 9:16 & Chống Lặp Đoạn:**
   - Video dọc 9:16 mặc định **CHỈ dùng `broll_clip` (Full màn hình 1080x1920)**; loại bỏ `broll_split`, `broll_framed`, `broll_bento` khỏi danh sách tự động để không bao giờ chia đôi màn hình làm bé mặt người nói.
   - Chấm điểm từng cửa sổ thời gian (`best_windows`) để loại bỏ vùng có hộp thoại/pop-up hệ thống đè màn hình và phân bổ các đoạn thời gian không trùng nhau khi tái sử dụng cùng 1 file B-Roll.
4. **Ngân Sách Đọc Hiểu Thẻ Đồ Họa / Poster Motion Graphic (`<= 20` âm tiết, `>= 4.5s`):**
   - Các khe `POSTER` (`compare_sheet`, `roadmap_sheet`, `checklist_sheet`, `anatomy_sheet`, `proportion_sheet`) bắt buộc có thời lượng **`4.5s – 5.0s`** (giữ tĩnh đọc chữ `>= 3.5s`).
   - Tổng dung lượng chữ toàn thẻ **tối đa `<= 20` âm tiết** (`2–3` dòng, mỗi ô `<= 4` từ, tốc độ đọc `<= 4.5` âm tiết/giây). Hộp `takeaway` ("GHI NHỚ") là tùy chọn (`""`) và tự động ẩn khi không cần thiết để khung thẻ co khít (`min_frame_h = 420px`).
5. **Chế Độ `C10 · Báo Đen Bôi Sáng` — Thẻ Báo & Văn Bản Bôi Dạ Quang Trên Nền Gradient Đen (Mantra: `edit pro báo đen` / `--palette bao_den | da_quang | to_bao | c10`):**
   - Kích hoạt khi truyền `--palette finpath_dark` ở bước `apply-answers` (hoặc đặt `"style_pack": "finpath_dark_highlight"` trong `plan_draft.json`):
     - **Nền Studio Dark Slate Gradient (`#161A24 → #07080C`)** kèm lưới tọa độ mờ `54px` và 4 góc nhấn `#CCFF00`.
     - **Cụm Tiêu Đề Phía Trên (nằm trên nền Gradient Đen):** Dùng Hệ Font của anh Việt (`FDAeonik-Bold` / `SVN-IntegralCF-Bold` màu Trắng kết hợp cụm từ khóa nhấn bằng Serif Nghiêng `SVN-Acta-BoldItalic` / `FDIvarFine-SemiBold` màu `#CCFF00` Neon Lime + gạch chân phát sáng).
     - **Khối Tờ Báo / Văn Bản Pháp Lý Trắng Ngà (`#F9FAFB` ở giữa):** Xếp chồng 3 lớp giấy báo + Masthead báo chí `"THỜI BÁO TÀI CHÍNH & PHÁP LÝ"` + các đoạn cắt báo chí với **vệt bút dạ quang `#CCFF00` vát chéo `7°` quét mượt `smootherstep_c2`** qua dòng Headline (`c2`) và cơ chế **làm dịu chữ phụ xuống `58%` (`Dim-to-Focus`)** ở dòng trích dẫn (`c3`).
6. **Hệ Thống 42 Cổng Kiểm Định Độc Lập (`edit_video_pro_verifier.py`):**
   - Gồm 35 cổng V2.8 + **7 cổng V3.5 mới**: `V_R1_silence` (khoảng lặng còn lại `<= 0.65s`), `V_R2_retake` (0 cụm lặp ý), `V_R3_sync` (sai số A/V `<= 0.020s`), `V_C1_framing` (tâm mặt trong `X ∈ [460, 620], Y ∈ [580, 820]`), `V_B1_broll_unique` (0 trùng đoạn B-Roll), `V_B2_broll_kind` (100% `broll_clip` full màn hình), `V_M1_reading` (thời lượng thẻ `>= 4.4s` & tốc độ đọc `<= 4.5` âm tiết/giây).

---

## 2. Bảng Chỉ Mục Nâng Cấp Nhanh & Tăng Tốc Full Studio V3.2 ("Muốn Sửa X -> Mở Đúng 1 File Y")
Khi anh Việt yêu cầu cập nhật hoặc nâng cấp tính năng, **TUYỆT ĐỐI KHÔNG đọc tràn lan các file lớn**, mà tra bảng dưới đây để sửa đúng 1 nơi duy nhất (100% Full Studio, không cắt bớt tính năng):

| Hạng mục anh Việt muốn nâng cấp | File duy nhất cần mở / sửa | Cơ chế tự động đồng bộ & Cache |
| :--- | :--- | :--- |
| **1. Chỉnh thông số Màn hình đen chữ (`MOI, AEO, TIEMPO`), cỡ chữ, tọa độ Y, độ trễ dòng 2 (`+0.358s`), ngưỡng 2 Cam, dB nhạc đẩy `4-Diamond`, hoặc chữ Hook/Outro** | `presets/dualcam_viet_style.json` (`~95 dòng`) | Đọc động lúc chạy; tự động băm lại đúng phần thay đổi trong `_dualcam_work/studio_cache/` và giữ nguyên cache các phần còn lại! |
| **2. Chỉnh thuật toán Nhận diện 2 Cam vs B-Roll (`Multi-Window FFT`), Quy hoạch Màn hình đen chữ, Nhạc đẩy `4-Diamond`, hoặc Đóng gói CapCut 2 Chế độ (`Máy Anh Việt` vs `Máy Học Viên`)** | `scripts/dualcam_v3_upgrade.py` | Tự động ánh xạ sang `capcut-sub/scripts/` qua Thin Wrapper (`15 dòng`), **0% cần copy thủ công** giữa 2 skill! |
| **3. Chỉnh bộ Tăng tốc Full Studio (`fastcopy` APFS `cp -c`, `Minimal CapCut Skeleton ~18KB`, `Segment/Asset Hash Cache`, `2-Worker Parallel`)** | `scripts/studio_accelerator.py` (`~245 dòng`) | Tự động tăng tốc toàn bộ luồng Full Studio từ `~110s` xuống `~6-10s` khi chạy lại / cập nhật! |
| **4. Chỉnh luồng điều phối 2 Cam & Kết xuất bộ biến thể Studio (7 Hook, 2 Poster, 2 Outro)** | `scripts/dualcam_engine.py` | Đã tích hợp `studio_cache` + `ThreadPoolExecutor(max_workers=2)`. |

---

## 3. Chi Tiết 6 Luật Curation Chuỗi B-Roll Đa Góc Máy (`R1..R6` — `curate-sequence`)
Khi người quay bấm máy nhiều góc liên hoàn (`CONTENT_MODE=BROLL` và có `[BROLL_CURATION_REQUIRED]`), thực hiện đúng 3 thao tác trước khi in Điểm dừng 1:
1. Mở xem trực tiếp TẤT CẢ các ảnh `CURATION_SHEETS` (`sequence_curation_sheet_*.jpg`) và đọc `<WORK_DIR>/curation_template.json`.
2. Tạo `<WORK_DIR>/sequence_curation.json` có mảng `"takes"` giữ nguyên đủ thứ tự `T01..Tnn`, điền các trường (`take`, `see`, `angle_id`, `scale` thuộc `["ECU","CU","MS","OTS","WS"]`, `action`, `prev_link`, `phase_in` `1..5`, `phase_out` `1..5`, `decision`, `defect`, `trim_window`) tuân thủ nghiêm ngặt **6 Luật Nếu–Thì Tổng Quát**:
   - **LUẬT R1 (Đổi Góc Máy / Đổi Tiêu Cự Zoom / Tiền Cảnh Điện Ảnh = BẮT BUỘC `KEEP`):**
     * Nếu take có vị trí đặt máy mới, hướng nhìn mới (trước mặt, ngang hông, qua vai trái/phải `OTS`, qua khung cửa, sau tán cây/rèm đung đưa trong gió) HOẶC đổi cỡ cảnh / tiêu cự zoom (`WS <-> MS <-> CU <-> ECU`), dù chủ thể vẫn đang làm tiếp cùng công việc $\rightarrow$ cấp `angle_id` hoặc `scale` mới và **BẮT BUỘC đặt `"decision": "KEEP"`**! Tuyệt đối cấm xóa cảnh đổi góc/zoom hay cảnh tiền cảnh gió thổi.
   - **LUẬT R2 (Chỉ Loại Bản Quay Lại Cùng Hệt Góc Đặt Máy Khi Có Lỗi Rõ — `DROP_RETAKE_OF_Txx`):**
     * Nếu hai take liền kề (cách nhau $\le 3$ takes, gợi ý `retake_cand_of`) có cùng hệt góc đặt máy & cỡ cảnh và diễn lại cùng một ý: soi kỹ hậu cảnh & chuyển động trên ảnh để **chỉ giữ 1 bản sạch nhất (`"KEEP"`)**, còn bản bị lỗi đánh `"decision": "DROP_RETAKE_OF_Txx"` (trong đó `Txx` là mã bản sạch được giữ) kèm `"defect"`:
       * `"STRANGER"`: có người lạ / bóng người đi ngang hậu cảnh (đặc biệt chú ý các hàng có cảnh báo `bg_intruder_hint: true` — **bắt buộc loại bản dính người lạ và giữ bản quay lại sạch!**).
       * `"EXIT_EARLY"` / `"FLUB"` / `"SHAKE"` / `"DUP_ACTION"`: bản nháp lỗi nhịp, rung máy hoặc 2 cú cận bước chân trùng hệt nhau.
   - **LUẬT R3 (Cắt Nối Sát Động Tác `Seam Handover Lx-Fy` & `Match-on-Action` — CẤM MỞ MÁY 2 LẦN / NGỒI 2 LẦN / ĐẨY CỬA 2 LẦN):**
     * Nếu 2–3 take liên tiếp khác góc máy quay nối tiếp cùng một hành động (ví dụ: mở nắp laptop ở góc rộng $\rightarrow$ mở nốt 15% nắp laptop ở góc qua vai; hoặc bước tới ghế $\rightarrow$ hạ người ngồi xuống $\rightarrow$ ngồi tựa lưng; hoặc đẩy cửa kính $\rightarrow$ bước qua cửa; hoặc đặt bình hoa lên bàn $\rightarrow$ vuốt chỉnh tán hoa):
       1. **BẮT BUỘC `"KEEP"` TẤT CẢ các góc máy đó** (cấm xóa góc sau!).
       2. **Căn chỉnh điểm nối ĐỦ SÁT bằng trường `"seam_to_next"` (`Lx-Fy`):** Khi cảnh trước đã thực hiện gần hết động tác (ví dụ mở nắp laptop ~85% tại `L2`), cảnh sau **phải vào sát ngay ở phần cuối động tác đó (`F4` hoặc `F5`) để diễn nốt**, tuyệt đối không chiếu lại từ đầu làm động tác bị lặp 2 lần!
       3. Trong `curation_template.json` và trên dải ảnh vi mô `L1, L2, L3 → F1..F6` của `sequence_curation_sheet_*.jpg`, mỗi cặp chuyển giao đều đã có sẵn `"seam_candidates"` và mã gợi ý `"seam_to_next"` (ví dụ `"L2-F4"`, `"L2-F5"`, `"L3-F5"`, `"L3-F1"`): hãy **giữ nguyên hoặc chọn mã `"seam_to_next": "Lx-Fy"`** phù hợp nhất và ghi `phase_in` / `phase_out` tăng đơn điệu (`1->2`, `2->3`, `4->5`)!
   - **LUẬT R4 (Mắt Xích Nhân Quả & Sự Kiện Tinh Tế Trên Màn Hình / Thiết Bị = BẮT BUỘC `KEEP`):**
     * Nếu sau cảnh thao tác trên điện thoại / bàn phím / chuột có một góc quay màn hình thiết bị hiển thị kết quả phản hồi (cửa sổ thông báo nhận file bung ra, gõ dòng lệnh chuyển trạng thái xử lý, con trỏ thao tác) $\rightarrow$ đặt `"prev_link": "CAUSE_EFFECT_OF_Txx"`, `"decision": "KEEP"`, và giữ `trim_window` ôm trọn mốc `suggested_window_s` chứa khoảnh khắc giao diện thay đổi. **CẤM dùng `DROP_UNUSABLE`** cho cảnh màn hình tĩnh có sự kiện UI!
   - **LUẬT R5 (Chốt Chặn Rời Khung — Không Để Lọt Nền Trống Sau `exit_t`):**
     * Nếu take có `exit_t` khác `null` (chủ thể bước qua cửa rời khung hoặc nhấc đồ vật khỏi mặt bàn để lại khung trống ở cuối take) $\rightarrow$ điểm kết thúc `trim_window[1]` **BẮT BUỘC `<= exit_t + 0.10`**.
   - **LUẬT R6 (Ưu Tiên Khoảng Chân Máy Đã Đứng Yên & Gương Mặt Không Bị Che):**
     * Trong một take dài, luôn ưu tiên `suggested_window_s` (đã tự động chọn khoảng chân máy tĩnh sau khi ngừng lia/chỉnh tripod và gương mặt lộ diện rõ nét).

---

## 4. Chi Tiết Chế Độ `"edit 2 cam"` / `"edit hai cam"` (`scripts/dualcam_engine.py` V3.0)
Lệnh chạy:
`"$HOME/.mfx_v3/venv/bin/python" "$HOME/.gemini/config/skills/edit-video-pro/scripts/dualcam_engine.py" run-both --dir "<THƯ_MỤC_2_CAM>" --out-mp4 "<OUT_EDIT_PRO_MP4>" --out-clean-switch-mp4 "<OUT_SWITCH_MP4>"`
*(Lưu ý: Mặc định mỗi thư mục chỉ tạo và ghi đè **1 Project CapCut duy nhất** trùng tên thư mục gốc, bên trong đã có đủ 4 Timelines gồm cả Timeline 01 Máy Anh Việt và Timeline 02 Máy Học Viên; KHÔNG đặt tên `--capcut-project` mới qua các vòng sửa và KHÔNG đẻ thêm project `- Bản Học Viên` rời bên ngoài trừ khi truyền cờ `--export-student-capcut`).*
1. **Chặng 1 (Tự động nhận diện 2 Cam Chính vs Cảnh Trám 0% cần đặt tên & Khóa Mắt / Màu Gốc):** Tự động quét mọi file video trong thư mục, kiểm tra đồng thuận độ trễ đa cửa sổ (`Multi-Window FFT Lag Consistency >= 3/4 cửa sổ ±5ms`) để phân biệt **2 Video Chính (`Cam A` = Master Audio SNR cao nhất, `Cam Z` = Góc máy 2 tắt tiếng chống vang)** và tách các file còn lại vào **Kho Cảnh Trám (`Local B-Roll`)**; nhận diện 3 nhánh không gian màu (`REC709_SDR` / `HDR_HLG_PQ` / `CAMERA_LOG`, giữ 100% màu gốc `bt709` và tắt sạch 100% LUT / Khớp màu trong CapCut), cắt bỏ câu lặp & meta-talk, khóa tâm mắt (`0.0px` Eye-Lock tại `(621px, 640px)`) và chuyển cam theo từng câu/ý.
2. **Chặng 2 (Màn Hình Đen Chữ Tóm Tắt Sắc Bén + Đẩy Nhạc 4-Diamond & Đóng Gói 1 Project CapCut 4 Timelines):** Tự động đặt **Màn hình đen chữ tóm tắt 2 tầng (`Retrospective Sharp Summary`)** tại ranh giới khép lại khối ý (khóa mệnh đề mở, gộp shot ngắn dưới lớp phủ `1.291s` để luôn đổi góc máy qua màn đen, đạt `Gate 10 Anti-Parrot` 0% trùng bigram & `Gate 8A` `t1_size >= 15.0`) kèm **Nhạc nhảy vọt lên `0dB` theo đường cong 4-Diamond (`-20dB -> 0dB -> 0dB -> -20dB`)** khớp `cues.drop` trên `nhac.fedu.vn`; xuất đồng thời **Video Sản Phẩm `.mp4` hoàn chỉnh** và **1 Project CapCut 4 Timelines** (Timeline 01 dùng Preset Compound Clip `MOI, AEO, TIEMPO` `subdraft/<UUID>`, Timeline 02 dùng Nền đen tự chứa `black_card_1080x1920.mp4` + 2 Track Chữ Native Phẳng `Tier 1` & `Tier 2` lệch nhịp `+0.358s`).