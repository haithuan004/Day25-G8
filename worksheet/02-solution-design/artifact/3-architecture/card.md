---
artifact: 3 — Lớp kiến trúc dữ liệu
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp kiến trúc dữ liệu

**Tình huống xử lý**: T-01, T-02, T-07, T-10, T-11, T-12

## 1. Giải pháp là gì?

Thêm pipeline `file ingest -> OCR/parser -> quality check -> evidence extraction -> policy/rule engine -> response builder -> logging`. Hệ thống chỉ cho phép summary/suggestion screening khi claim quan trọng có evidence và confidence đủ ngưỡng. Đồng thời bổ sung consent gate cho batch import, PII redaction cho shared notes, và injection screening cho nội dung CV.

## 2. Vì sao sửa ở lớp kiến trúc dữ liệu?

- Nhiều lỗi của Track 7 không bắt đầu ở câu chữ mô hình mà ở input quality, metadata thiếu, hoặc workflow gate thiếu.
- Nếu architecture không tạo evidence spans và confidence signal, prompt/UI sẽ không có vật liệu để chặn lỗi thật sự.

**Hành động phòng vệ chính**:

- [x] Ngăn lỗi bằng nguồn dữ liệu đúng
- [x] Phát hiện khi nguồn thiếu hoặc lỗi
- [x] Khắc phục bằng cách chuyển sang người thật
- [x] Ghi lại lỗi để cải thiện sau

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo có:

- Data flow của CV/JD
- Parser/OCR quality gate
- Evidence store cho từng claim
- Policy engine cho consent, PII, protected/proxy requests, injection
- Manual-review queue và monitoring log

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**

- Tăng latency vì phải OCR, extract, và run rule engine.
- Tăng complexity vận hành và nhu cầu tuning threshold.
- Có thể tạo nhiều manual review hơn trong giai đoạn đầu.

**Nhóm giảm vấn đề đó bằng cách nào?**

- Chỉ bật gate mạnh với high-impact actions như shortlist/export/reject support.
- Cache parser/evidence theo candidate version.
- Theo dõi false positive của gate để tinh chỉnh threshold thay vì mở gate quá lỏng.

## 5. Checklist trước khi nộp

- [x] Sơ đồ cho thấy dữ liệu đi từ đâu đến đâu.
- [x] Có bước kiểm tra nguồn trước khi AI trả lời.
- [x] Có cách xử lý khi không có dữ liệu.
- [x] Có cách chuyển sang người thật với tình huống rủi ro cao.
- [x] Có cách biết lỗi này có đang lặp lại không.

**Người phụ trách**: Hồ Hải Thuận
