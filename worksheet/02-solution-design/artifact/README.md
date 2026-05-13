---
folder: artifact/ — 3 lớp giải pháp
bai-tap: 2 — Thiết kế giải pháp
phase: Xây demo
nop-cuoi: Có — nộp đủ 3 thư mục con
---

# Thư mục artifact/ — 3 lớp giải pháp

Rủi ro chính của nhóm là `T-01`: AI suy diễn skill/years/fit từ CV mơ hồ hoặc OCR lỗi.

## Ba lớp được chọn

| Thư mục | Lớp giải pháp | Trọng tâm |
|---|---|---|
| `1-uiux/` | Giao diện | Evidence, uncertainty, manual review, export friction |
| `2-prompt/` | Chỉ dẫn AI | Cấm unsupported inference, từ chối protected/proxy requests |
| `3-architecture/` | Kiến trúc dữ liệu | OCR quality gate, evidence extraction, consent/PII/injection screening |

## Vì sao 3 lớp này bổ sung cho nhau

- Nếu prompt drift, architecture vẫn có confidence gate.
- Nếu parser/OCR yếu, UI vẫn chặn recruiter auto-export chỉ theo score.
- Nếu recruiter cố ép AI “đoán giúp”, prompt từ chối và UI vẫn tạo friction.

## Người phụ trách chính

| Lớp | Người phụ trách |
|---|---|
| `1-uiux/` | Vũ Quang Phúc |
| `2-prompt/` | Nguyễn Đức Mạnh |
| `3-architecture/` | Hồ Hải Thuận |
