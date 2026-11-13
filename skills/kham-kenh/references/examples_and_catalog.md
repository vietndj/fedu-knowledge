# kham-kenh V2.0 — Quy chuẩn Báo cáo HTML 3 Tầng, Bảng chấm 4 Định dạng, Khối Xác minh Chính chủ & Nhánh Benchmark

> Tài liệu chuẩn hóa cấu trúc HTML cho `kham-kenh` V2.0 (tích hợp **4 Định dạng 2.0**, **Vòng gửi xe 3s Hộp nhung × Nhẫn vàng**, **Lurker 90-9-1 & Dark Social**, **Khối Giả thuyết & Câu hỏi hỏi lại chính chủ** và **12 Cổng Kiểm Định `K0..K11`**).

---

## 1. Khối `<!-- KENH_META ... -->` bắt buộc ở đầu `report.html` (`Cổng K7`)

Ngay sau `<!DOCTYPE html>`, bắt buộc khai báo đủ 8 khóa thực địa (nêu rõ số đo từ kênh hoặc ghi `[giả định — cần hỏi chính chủ]`):

```html
<!DOCTYPE html>
<!-- KENH_META
san_pham: Dịch vụ điều trị nám & phục hồi da tại tiệm [số liệu kênh]
gia: 3 - 12 triệu đồng/liệu trình [giả định — cần hỏi chính chủ]
chu_ky_suy_nghi: 2 - 4 tuần theo dõi trước khi nhắn đặt lịch [giả định — cần hỏi chính chủ]
ap_dung_7h: co
giay_xem_tb: 18 giây [giả định — cần hỏi chính chủ]
nguoi_thu_hai: Chồng hoặc bạn thân đồng nghiệp nữ [giả định — cần hỏi chính chủ]
kenh_rieng: Zalo và Messenger
gio_quay_tuan: 2 - 3 giờ/tuần tại tiệm [giả định — cần hỏi chính chủ]
-->
<html lang="vi">
```

---

## 2. Quy chuẩn Tiêu đề Câu hỏi (`K2`) & Trần chữ Nén sắc bén (`K1`)

1. **100% thẻ `<h1>` và `<h2>` bắt buộc là câu hỏi kết thúc bằng dấu `?`**, viết theo chuẩn **Sentence case** (chỉ viết hoa chữ cái đầu câu và tên riêng, cấm Title Case).
2. **Độ dài tiêu đề:** Mọi thẻ `<h1>`, `<h2>`, `<h3>` phải **$\le 18$ từ**.
3. **Ngân sách từ (`Cổng K1`):**
   - **Chữ bình luận thuần** (loại trừ `.transcript-box`, `.script-card`, `details`, `nav`, `footer`): **$\le 3.000$ từ** (Tầng 1 $\le 700$ từ, Tầng 2 $\le 1.400$ từ, Tầng 3 $\le 900$ từ).
   - **Tổng số từ toàn trang:** **$\le 6.000$ từ**.
   - **Mỗi thẻ giải phẫu video đại diện (`.video-audit-card`):** Phần chữ nhận xét (ngoài `<details>` chứa transcript) **$\le 130$ từ**.

---

## 3. Mẫu Bảng Chấm Tổng Thể 12 Video (`.score-table` — `Cổng K3, K4, K5`)

Thay vì viết 12 thẻ dài lê thê lặp lại cùng 1 lỗi, đầu Tầng 2 đặt **1 Bảng Chấm Tổng Thể** cho toàn bộ các video đã tải về ($\ge 5$ đến $12$ dòng):

```html
<table class="score-table">
  <thead>
    <tr>
      <th>Video</th>
      <th>Lượt xem</th>
      <th>Định dạng hiện tại → Nên chuyển</th>
      <th>Hộp nhung (Thị giác 3s)</th>
      <th>Nhẫn vàng (Vi mô 3s)</th>
      <th>Đích người xem</th>
    </tr>
  </thead>
  <tbody>
    <tr data-format="talking-head" data-format-next="voice-over" data-hop-nhung="mot-phan" data-nhan-vang="rot" data-dich="1pct">
      <td>#01 — Chúc mùng 1 đầu tháng tại tiệm</td>
      <td>320</td>
      <td>Talking Head đứng → Voice-Over 3 lớp</td>
      <td>Đạt một phần (phòng sáng, chữ đè ngực)</td>
      <td>Rớt (42s đầu chỉ chào chúc xã giao)</td>
      <td>1% bình luận xã giao</td>
    </tr>
    <tr data-format="voice-over" data-format-next="story-25" data-hop-nhung="dat" data-nhan-vang="dat" data-dich="90pct">
      <td>#02 — Soi da ca nám chân sâu 4 năm</td>
      <td>4.800</td>
      <td>Voice-Over → Storytelling 2.5</td>
      <td>Đạt (cận cảnh máy soi sắc nét)</td>
      <td>Đạt (chỉ đúng vết nám gò má sau sinh)</td>
      <td>90% xem thầm lặng (Lurker)</td>
    </tr>
  </tbody>
</table>
```

- **Giá trị hợp lệ bắt buộc của các thuộc tính `data-*`:**
  - `data-format` và `data-format-next`: `voice-over` | `walk-talk` | `talking-head` | `story-25` | `khac`
  - `data-hop-nhung` và `data-nhan-vang`: `dat` | `rot` | `mot-phan`
  - `data-dich`: `1pct` | `90pct`

---

## 4. Mẫu Thẻ Giải Phẫu Video Đại Diện (`.video-audit-card` — 4 đến 6 thẻ, $\le 130$ từ/thẻ)

Chỉ chọn **4–6 video đại diện cho 4–6 nhóm lỗi/định dạng khác nhau** để mổ xẻ sâu. Transcript nguyên văn 3 nhịp bắt buộc đặt trong thẻ `<details>` để giao diện gọn và không làm loãng mạch đọc:

```html
<article class="video-audit-card"
         data-format="talking-head"
         data-format-next="voice-over"
         data-hop-nhung="mot-phan"
         data-nhan-vang="rot"
         data-dich="1pct">
  <h3>Vì sao video đứng nói 170 giây tại quầy chỉ giữ được người quen?</h3>
  <img src="videos/v01_strip.jpg" alt="3 nhịp khung hình video 01" />
  <div class="badge-row">
    <span>Talking Head → Voice-Over 3 lớp</span> •
    <span>Hộp nhung: Một phần</span> •
    <span>Nhẫn vàng: Rớt</span> •
    <span>Đích: 1% ồn ào</span>
  </div>
  <ol class="audit-3lines">
    <li><strong>1. Vòng gửi xe 3 giây (Hộp nhung × Nhẫn vàng):</strong> Tiệm sáng, thấy rõ 3 giường khách thật (giữ lại). Nhưng chữ phụ đề đè ngang ngực và 42 giây đầu chỉ chúc đầu tháng, chưa chạm vào vấn đề da của khách.</li>
    <li><strong>2. Lỗi kỹ thuật theo chuẩn 4 định dạng:</strong> Đứng nói 170 giây một góc máy tĩnh mà thiếu hẳn cảnh trám 3 lớp (Mồi – Băm – Nối) quay cận tay kỹ thuật viên.</li>
    <li><strong>3. Cách gọt lại ngay:</strong> Mở đầu bằng câu <em>“Còn đúng 3 tháng nữa là Tết, mảng nám gò má phải xử lý từ tháng 11 mới kịp bong sạch”</em>, rồi cắt ngay sang cảnh tay kỹ thuật viên đang chấm tinh chất ở giường số 2.</li>
  </ol>
  <details class="transcript-details">
    <summary>Xem lời thoại gốc đã bóc băng (3 nhịp)</summary>
    <div class="transcript-box">
      <p>🎯 Mở đầu (3s): Xin chào cả nhà, chúc cả nhà mùng 1 đầu tháng...</p>
      <p>• Ý triển khai: ...</p>
      <p>🏁 Kết câu: Chị em nào cần làm đẹp Tết thì nhắn em nhé.</p>
    </div>
  </details>
</article>
```

---

## 5. Mẫu Khối Giả Thuyết, Câu Hỏi Xác Minh Chính Chủ & Ô Ghi Chú (`Cổng K6, K8`)

Toàn báo cáo phải có **3 đến 6 cụm** `.analysis-block` + `.question-block` (đặt ở Tầng 1, dưới các video có số liệu bất thường ở Tầng 2, và ở Tầng 3), kèm ít nhất 1 khối `.note-block[contenteditable="true"]` tự lưu `localStorage`:

```html
<div class="analysis-block">
  <strong>🔍 Giả thuyết từ dữ liệu kênh:</strong> Video quay cận cảnh tay nặn mụn không lộ mặt đạt 4.800 lượt xem, gấp 15 lần video đứng nói tại quầy, cho thấy người xem thầm lặng trên kênh đang cần bằng chứng tay nghề hơn là lời chào hỏi.
</div>
<div class="question-block">
  <strong>❓ Câu hỏi cần hỏi lại chính chủ:</strong> Sau video 4.800 lượt xem đó, có khách nào lưu bài rồi nhắn riêng qua Zalo hỏi giá liệu trình không chị?<br/>
  <strong>🔀 Phân nhánh:</strong> Nếu có khách nhắn thật → Tăng tỷ lệ định dạng Voice-Over 3 lớp lên 50% trong 2 tuần đầu. Nếu chỉ hỏi dạo không chốt → Bổ sung ngay 1 câu gài tầng 2.5 ở cuối video để lọc khách có ngân sách.
</div>
<div class="note-block" contenteditable="true" data-note-id="note-tang-1">
  💡 Ghi chú xác minh cùng chính chủ (bấm vào đây để gõ trực tiếp — tự động lưu trên trình duyệt)...
</div>
```

Script lưu `localStorage` bắt buộc có ở cuối trang:
```html
<script>
document.querySelectorAll('.note-block[contenteditable="true"]').forEach((el, idx) => {
  const key = 'khamkenh_note_' + location.pathname + '_' + (el.dataset.noteId || idx);
  const saved = localStorage.getItem(key);
  if (saved) el.innerText = saved;
  el.addEventListener('input', () => localStorage.setItem(key, el.innerText));
});
</script>
```

---

## 6. Mẫu 4 Thẻ Kịch Bản Đại Diện Cho Đúng 4 Định Dạng (`Cổng K9`)

Ở Tầng 3, xuất **đúng 4 thẻ `.script-card`** với thuộc tính `data-format` lần lượt là `voice-over`, `walk-talk`, `talking-head`, `story-25`. Riêng thẻ `data-format="story-25"` bắt buộc có **1 câu trong ngoặc kép `“...”`** mà khách dùng để nói với người thứ hai (`nguoi_thu_hai`) khi gửi link qua Zalo/Messenger:

```html
<div class="script-card" data-format="voice-over">...</div>
<div class="script-card" data-format="walk-talk">...</div>
<div class="script-card" data-format="talking-head">...</div>
<div class="script-card" data-format="story-25">
  <h3>Kịch bản 4 (Storytelling 2.5): Lát cắt 5 giây soi gương & chiếc cớ đàng hoàng gửi chồng</h3>
  <div class="script-pre">
    🎯 Mở đầu (3s) [Quay cận ngón tay kéo nhẹ vạt tóc che gò má]: ...
    • Triển khai (Tầng 2 & Tầng 2.5): ... Khách có thể gửi video này qua Zalo cho chồng kèm câu: “Anh xem này, da em bị tăng sắc tố sau sinh chứ không phải đòi đi spa làm đẹp phù phiếm đâu, xử lý sớm đỡ tốn gấp ba lần”.
    🏁 Kết câu: ...
  </div>
</div>
```

---

## 7. Luật Phân Loại Học Viên (`student`) vs Kênh Mẫu (`benchmark`)
1. **`role = "student"`:** Học viên có trong `students_master.json` (hoặc anh Việt xác nhận). Xuất bản lên `stu.fedu.vn/audits/<student_id>.html` và đồng bộ sang `kho.fedu.vn/kham-kenh` qua `sync_kho_audits.py --ingest ... --student <id> --type kham-kenh --ship`.
2. **`role = "benchmark"`:** Kênh mẫu ngoài đời. **CẤM** tạo thẻ trong `students_master.json`. Xuất vào `kho-fedu-vn/docs/public/audits/kenhmau-<slug>.html` & `k/kenhmau-<slug>.html`, tạo 3 chương Markdown tại `kho-fedu-vn/docs/kien-thuc/kenhmau-<slug>/`, đăng ký `semantic_map.json` & `BENCHMARK_CHANNEL_MAP`, rồi chạy `build_related.py`, `build_fedu_graph.py` và `ship.py --site kho --auto-commit`.