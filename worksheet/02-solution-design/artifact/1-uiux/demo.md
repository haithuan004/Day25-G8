---
artifact: 1 — Demo giao diện
format: ASCII UI + trạng thái chính
---

# demo.md — Demo giao diện

## 1. Màn hình A — Trạng thái bình thường

```text
+----------------------------------------------------------------------------------+
| Candidate Review - Data Analyst Intern                          Score: 8.1 / 10  |
| JD: Data Analyst Intern            CV source: cv_final.pdf      OCR: OK (0.93)   |
+----------------------------------------------------------------------------------+
| Summary status: Có đủ bằng chứng cho các claim chính                             |
| [Mở CV gốc] [Xem JD] [Thêm vào shortlist]                                        |
+----------------------------------------------------------------------------------+
| Claims đã trích xuất                                                               |
|                                                                                  |
| 1. "Có kinh nghiệm Python qua 2 internship và 1 capstone project" [ĐÃ XÁC MINH] |
|    Evidence: "Python Intern - 06/2024 to 09/2024"                                |
|                                                                                  |
| 2. "Đã dùng Tableau để làm dashboard"           [ĐÃ XÁC MINH]                    |
|    Evidence: "Built sales dashboard in Tableau for capstone project"             |
|                                                                                  |
| 3. "Đáp ứng 3/4 yêu cầu chính của JD"           [ĐÃ XÁC MINH]                    |
|    Missing: AWS certificate not found in CV                                      |
+----------------------------------------------------------------------------------+
| Shared shortlist note                                                              |
| - Verified: Python, Tableau, SQL basics                                           |
| - Need interviewer follow-up: AWS hands-on depth                                  |
| - PII hidden in shared mode                                                       |
+----------------------------------------------------------------------------------+
```

## 2. Màn hình B — Trạng thái rủi ro cao / cần review tay

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
| 1. "Có 2 năm Python"                          [CẦN REVIEW TAY]                   |
|    Không tìm thấy mốc thời gian rõ trong CV.                                     |
|                                                                                  |
| 2. "Đã dùng Tableau để làm dashboard"           [ĐÃ XÁC MINH]                    |
|    Evidence: "Built sales dashboard in Tableau for capstone project"             |
|                                                                                  |
| 3. "Phù hợp shortlist ngay"                     [KHÔNG CHO AUTO-DECIDE]          |
|    Thiếu bằng chứng cho 2 claim quan trọng trong JD.                             |
+----------------------------------------------------------------------------------+
| Safe next step                                                                    |
| - Mở CV gốc để kiểm tra timeline Python                                           |
| - Nếu vẫn không rõ, chuyển hồ sơ sang manual review                               |
+----------------------------------------------------------------------------------+
```

## 3. Màn hình C — Modal chặn export shortlist

```text
Bạn đang export shortlist chỉ theo AI score.

- 8 hồ sơ trong bucket dưới ngưỡng chưa được mở CV gốc
- 3 hồ sơ top score có OCR confidence thấp
- 2 hồ sơ có claim "Cần review tay" nhưng chưa được xác nhận

[Xem lại hồ sơ trước] [Tôi đã review đủ và vẫn muốn export]
```

## 4. Trạng thái cần minh họa

| Trạng thái | Người dùng thấy gì? | Người dùng làm gì tiếp? |
|---|---|---|
| Có nguồn xác minh | Claim có evidence span và badge `Đã xác minh` | Có thể tiếp tục review hoặc shortlist |
| Chưa có nguồn xác minh | Claim có badge `Cần review tay` | Mở CV gốc hoặc hỏi thêm |
| AI không nên tự trả lời mạnh | Dòng `Không cho auto-decide` | Chuyển sang manual review |
| Cần chặn hành vi over-reliance | Modal export xuất hiện | Xem lại hồ sơ trước khi export |

## 5. Tại sao demo này dễ hiểu hơn

- Có **2 trạng thái chính**: bình thường và rủi ro cao.
- Cho thấy **AI không bị tắt hoàn toàn**; chỉ các claim yếu mới bị chặn.
- Cho thấy đúng điểm giao diện can thiệp vào hành vi nguy hiểm nhất: **export shortlist chỉ theo AI score**.

## 6. Kiểm tra nhanh

- [x] Nhìn vào demo là hiểu rủi ro đang được chặn ở đâu.
- [x] Có trạng thái khi AI không có đủ thông tin.
- [x] Có cách chuyển sang người thật.
- [x] Có friction đúng lúc cho hành vi over-reliance.
