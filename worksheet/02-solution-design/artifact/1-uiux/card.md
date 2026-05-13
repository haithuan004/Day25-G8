---
artifact: 1 — Lớp giao diện
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp giao diện

**Tình huống xử lý**: T-01 và T-07

## 1. Giải pháp là gì?

Thay vì hiển thị một khối summary trôi chảy và score lớn ở đầu màn hình, giao diện sẽ hiển thị từng claim kèm evidence span, OCR confidence, và trạng thái `Đã xác minh` / `Cần review tay`. Nếu recruiter định export shortlist chỉ theo score AI, hệ thống mở modal bắt xác nhận coverage bucket thấp và nhắc người dùng mở CV gốc trước khi tiếp tục.

## 2. Vì sao sửa ở lớp giao diện?

- Over-reliance xảy ra ở đúng khoảnh khắc recruiter nhìn score và quyết định có mở CV gốc hay không.
- Khi prompt hoặc OCR vẫn còn sai sót, UI là lớp cuối có thể giảm hại bằng cách làm uncertainty trở nên thấy được.

**Hành động phòng vệ chính**:

- [x] Thông báo rõ giới hạn
- [x] Phát hiện dấu hiệu thiếu nguồn
- [x] Chuyển người thật khi cần
- [x] Giúp người dùng kiểm tra lại nguồn

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo thể hiện:

- Score không đứng một mình, phải đi cùng evidence
- Banner low-confidence khi OCR/parser yếu
- Nút `Mở CV gốc` và `Manual review`
- Modal chặn export shortlist chỉ theo AI score

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**

- Recruiter thấy thêm friction và cảm giác hệ thống “chậm hơn”.
- Màn hình dễ rối nếu hiển thị mọi claim cùng lúc.

**Nhóm giảm vấn đề đó bằng cách nào?**

- Chỉ bật friction mạnh với task high-impact như shortlist/export.
- Mặc định chỉ mở 2-3 claim quan trọng nhất; phần còn lại để `Xem thêm`.
- Banner low-confidence chỉ hiện khi thật sự có parser/OCR issue hoặc missing-evidence.

## 5. Checklist trước khi nộp

- [x] Giải pháp gắn đúng với rủi ro chính.
- [x] Demo nhìn vào là hiểu vấn đề được chặn ở đâu.
- [x] Có đủ trạng thái bình thường và trạng thái lỗi.
- [x] Có cách chuyển sang người thật khi AI không nên tự xử lý.
- [x] Câu chữ trong giao diện ngắn, không đổ hết trách nhiệm cho người dùng.

**Người phụ trách**: Vũ Quang Phúc
