---
artifact: 1 — Demo giao diện
format: ASCII UI + trạng thái chính
---

# demo.md — Demo giao diện

## 1. Màn hình chính

```text
+----------------------------------------------------------------------------------+
| Candidate Review - Data Analyst Intern                          Score: 7.2 / 10  |
| JD: Data Analyst Intern            CV source: scan.pdf          OCR: LOW (0.61)  |
+----------------------------------------------------------------------------------+
| Warning: CV quality thấp. Không nên shortlist/reject chỉ dựa vào AI summary.    |
| [Mở CV gốc] [Manual review] [Xem OCR issues]                                     |
+----------------------------------------------------------------------------------+
| Claims đã trích xuất                                                               |
|                                                                                  |
| 1. "Có 2 năm Python"                         [CẦN REVIEW TAY]                    |
|    Không tìm thấy mốc thời gian rõ trong CV.                                     |
|                                                                                  |
| 2. "Đã dùng Tableau để làm dashboard"          [ĐÃ XÁC MINH]                     |
|    Evidence: "Built sales dashboard in Tableau for capstone project"             |
|                                                                                  |
| 3. "Phù hợp shortlist ngay"                    [KHÔNG CHO AUTO-DECIDE]           |
|    Thiếu bằng chứng cho 2 claim quan trọng trong JD.                             |
+----------------------------------------------------------------------------------+
| Shared shortlist note                                                              |
| - Verified: Tableau, SQL basics                                                   |
| - Needs human review: years of Python, dataset scale                              |
| - PII hidden in shared mode                                                       |
+----------------------------------------------------------------------------------+
```

## 2. Trạng thái cần minh họa

| Trạng thái | Người dùng thấy gì? | Người dùng làm gì tiếp? |
|---|---|---|
| Có nguồn xác minh | Claim có evidence span và badge `Đã xác minh` | Có thể tiếp tục review |
| Chưa có nguồn xác minh | Claim có badge `Cần review tay` | Mở CV gốc hoặc hỏi thêm |
| AI không nên tự trả lời | Dòng `Không cho auto-decide` | Chuyển sang manual review |
| Cần chuyển sang người thật | Nút `Manual review` nổi bật | Đưa case cho recruiter/hiring manager đọc tay |

## 3. Modal chặn export

```text
Bạn đang export shortlist chỉ theo AI score.

- 8 hồ sơ trong bucket dưới ngưỡng chưa được mở CV gốc
- 3 hồ sơ top score có OCR confidence thấp

[Xem lại hồ sơ trước] [Tôi đã review đủ và vẫn muốn export]
```

## 4. Kiểm tra nhanh

- [x] Nhìn vào demo là hiểu rủi ro đang được chặn ở đâu.
- [x] Có trạng thái khi AI không có đủ thông tin.
- [x] Có cách chuyển sang người thật.
- [x] Có friction đúng lúc cho hành vi over-reliance.
