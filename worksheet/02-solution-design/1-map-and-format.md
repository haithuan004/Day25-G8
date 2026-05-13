---
artifact: 1 — FINAL kế hoạch giải pháp
bai-tap: 2 — Thiết kế giải pháp
phase: Chọn rủi ro + chọn tầng + chọn demo + chốt 3 lớp giải pháp
time: 11:00-11:55
input: 00-context.md + 01-test-set-review/3-FINAL-test-set-eval-plan.md
nop-cuoi: Có — file cuối Bài 2
---

# 1 — FINAL: Kế hoạch giải pháp

## Thông tin nhóm

- **Chủ đề**: Track 7 — Trợ lý sàng lọc CV và tuyển dụng
- **Thành viên**: Vũ Quang Phúc, Hồ Hải Thuận, Nguyễn Đức Mạnh
- **Ngày**: 2026-05-13

## Phần A — Chọn rủi ro và tầng giải pháp

### Rủi ro chính được chọn

- **ID tình huống**: T-01
- **Mô tả ngắn**: Khi recruiter cần lọc nhanh CV mơ hồ, CV scan lỗi, hoặc CV thiếu thông tin định lượng, AI có xu hướng điền thêm skill/số năm kinh nghiệm/mức độ phù hợp thay vì dừng ở mức uncertainty, làm shortlist sai và loại oan ứng viên.
- **Mức độ**: Nặng
- **Điểm rủi ro**: 25
- **Vì sao chọn tình huống này**: Đây là root failure nằm ở đầu pipeline. Nếu T-01 không được chặn, các lỗi T-02, T-07, T-08, T-09, và T-12 sẽ trở nên dễ xảy ra hơn.

### Tìm nguyên nhân gốc

- [x] Thiếu nguồn dữ liệu đúng.
- [x] AI đoán khi không biết.
- [x] Giao diện khiến người dùng tin quá mức.
- [x] Quy trình thiếu người duyệt hoặc thiếu bước chuyển sang người thật.
- [x] Không có theo dõi sau khi ra mắt.
- [ ] Khác

### Bảng nối nguyên nhân với tầng sửa

| Nguyên nhân gốc | Tầng ưu tiên sửa | Lớp giải pháp liên quan |
|---|---|---|
| OCR/parser/reading order làm mất hoặc lệch thông tin trong CV | Dữ liệu, ingestion, confidence gate | `3-architecture` là chính |
| Model có xu hướng “lấp chỗ trống” để trả lời hữu ích | System prompt + policy + refusal/evidence rule | `2-prompt` là chính |
| Recruiter nhìn score/summary quá trôi chảy và bỏ qua CV gốc | UI trust calibration + review affordance | `1-uiux` là chính |
| Quy trình shortlist under time pressure thiếu friction đúng lúc | UI + workflow gate + monitoring | `1-uiux` + `3-architecture` |
| Lỗi lặp đi lặp lại nhưng không ai thấy pattern | Logging + review loop | `3-architecture` là chính |

### Kết luận Phần A

**Nguyên nhân gốc**: Hệ thống chưa ép AI bám vào bằng chứng ở mức claim-level. Khi dữ liệu đầu vào yếu hoặc không đầy đủ, mô hình vẫn cố trả lời như thể chắc chắn. Giao diện và flow export hiện tại cũng chưa tạo đủ friction để recruiter quay lại CV gốc trước khi hành động.

**Tầng chính cần sửa**: Architecture là tầng gốc, prompt là tầng trung gian ngăn hallucination, UI là lớp cuối để giảm over-reliance.

**Vì sao cần 3 lớp giải pháp**:

- Lớp giao diện: nhắc recruiter đâu là claim đã xác minh, đâu là claim cần đọc tay.
- Lớp chỉ dẫn AI: cấm unsupported inference và bắt buộc uncertainty wording.
- Lớp kiến trúc dữ liệu: tạo evidence spans, OCR confidence, consent check, injection screening, và manual-review gate.

## Phần B — Chọn định dạng demo

| Lớp | Thư mục | Định dạng demo chọn | Thời gian dự kiến |
|---|---|---|---|
| Giao diện | `1-uiux` | ASCII UI + state table | 12 phút |
| Chỉ dẫn AI | `2-prompt` | Markdown prompt + few-shot + quick replay | 10 phút |
| Kiến trúc dữ liệu | `3-architecture` | ASCII architecture + component table | 13 phút |

**Lý do chọn demo**

- Giao diện: đủ trực quan để phản biện behavior của recruiter tại điểm ra quyết định.
- Chỉ dẫn AI: dễ xem rule, test, và chỉnh nhanh khi đối chiếu với bộ test.
- Kiến trúc dữ liệu: phù hợp để giải thích gate, log, OCR confidence, và escalation path.

## Phần C — Ba lớp giải pháp

### Lớp 1 — Giao diện (`artifact/1-uiux/`)

- **Cách tiếp cận**: Hiển thị claim-level evidence, OCR confidence, badge “cần review tay”, và modal chặn export nếu recruiter chưa review coverage bucket thấp.
- **Hành động phòng vệ bao phủ**: Thông báo + Phát hiện + Khắc phục
- **Demo**: `artifact/1-uiux/demo.md`
- **Trạng thái**: Xong
- **Người phụ trách chính**: Vũ Quang Phúc

### Lớp 2 — Chỉ dẫn AI (`artifact/2-prompt/`)

- **Cách tiếp cận**: Bắt AI chỉ được khẳng định skill/years/fit khi có evidence span rõ; protected attribute/proxy và pressure estimate phải bị từ chối.
- **Hành động phòng vệ bao phủ**: Ngăn + Từ chối + Hỏi lại
- **Demo**: `artifact/2-prompt/demo.md`
- **Trạng thái**: Xong
- **Người phụ trách chính**: Nguyễn Đức Mạnh

### Lớp 3 — Kiến trúc dữ liệu (`artifact/3-architecture/`)

- **Cách tiếp cận**: Bổ sung OCR/parser quality check, evidence extraction, consent/PII rule engine, prompt-injection screening, và manual-review queue.
- **Hành động phòng vệ bao phủ**: Ngăn + Phát hiện + Khắc phục
- **Demo**: `artifact/3-architecture/demo.md`
- **Trạng thái**: Xong
- **Người phụ trách chính**: Hồ Hải Thuận

## Tổng kiểm tra

| Câu hỏi | Trả lời |
|---|---|
| Rủi ro chính đã chọn là gì? | T-01 |
| Nguyên nhân gốc là gì? | Input yếu + model lấp chỗ trống + UI quá trôi chảy + thiếu friction/manual gate |
| 3 lớp giải pháp đã đủ chưa? | Giao diện: Có / Chỉ dẫn AI: Có / Kiến trúc: Có |
| 4 hành động đã bao phủ chưa? | Ngăn: Có / Phát hiện: Có / Khắc phục: Có / Thông báo: Có |
| Nhóm đã tổng hợp đầu vào từ các thành viên chưa? | Có — từ Phúc, Thuận, Mạnh trong `worksheet/team-inputs/` |
| Nhóm đã bỏ gì ra khỏi final? | Bản nháp không cùng hướng Track 7 hoặc không đủ metadata đã chuyển sang `archive/` |
