---
title: 00 — Bối cảnh sản phẩm của nhóm
section: Day 25 — dùng lại cho mọi cuộc trò chuyện với AI
format: Nhóm
time: Điền 5 phút đầu buổi
---

# 00-context.md — Bối cảnh sản phẩm của nhóm

## 1. Sản phẩm

- **Tên sản phẩm / bot**: AI CV Screening Assistant tích hợp trong ATS nội bộ
- **Sản phẩm giúp ai làm gì**: Hỗ trợ recruiter đọc nhanh CV, so sánh với JD, tạo tóm tắt có căn cứ, gợi ý câu hỏi phỏng vấn, và ưu tiên hồ sơ cần mở đọc trước trong các đợt tuyển số lượng lớn.
- **Người dùng gặp sản phẩm ở đâu**: ATS nội bộ công ty, chủ yếu ở trang danh sách ứng viên, trang chi tiết CV, màn hình shortlist, và tab review của recruiter/hiring manager.
- **Giai đoạn hiện tại**: Đang pilot nội bộ trước khi dùng thật trong quy trình tuyển dụng.

## 2. Phạm vi

**AI được làm gì**

- Đọc CV ứng viên cùng job description đã publish.
- Trả tóm tắt điểm mạnh, điểm thiếu, mức khớp với từng tiêu chí JD, và câu hỏi phỏng vấn gợi ý.
- Gắn bằng chứng ngắn từ CV khi có thể trích được; nếu không đủ bằng chứng thì phải nêu uncertainty.

**AI không được làm gì**

- Không được auto-reject, auto-shortlist, hay tự đổi stage ứng viên.
- Không được suy đoán số năm kinh nghiệm, quy mô dự án, protected attributes, hay lý do career gap nếu CV không ghi rõ.
- Không được tiết lộ PII không cần thiết hoặc dùng dữ liệu ứng viên ngoài phạm vi consent/policy.

**Vì sao có giới hạn này**

Tuyển dụng là bài toán fairness và trách nhiệm pháp lý cao. Nếu AI suy diễn sai hoặc bias ngay ở vòng sàng lọc đầu, ứng viên có thể bị loại oan mà không có cơ hội sửa sai. Ngoài ra, CV scan/OCR lỗi, layout nhiều cột, song ngữ, và hành vi over-reliance của recruiter đều có thể khuếch đại lỗi nếu không có guardrail rõ ràng.

## 3. Người dùng

- **Là ai**: HR recruiter, hiring coordinator, hoặc hiring manager trong startup/SME; thường không chuyên sâu kỹ thuật AI nhưng phải xử lý 100–300 CV trong thời gian ngắn.
- **Họ hỏi AI khi nào**: Khi cần rút shortlist đầu tiên, chuẩn bị review với hiring manager, hoặc so sánh nhiều hồ sơ gần giống nhau.
- **Họ cần quyết định gì sau khi hỏi AI**: Hồ sơ nào đọc sâu hơn, hồ sơ nào cần manual review, câu hỏi nào cần hỏi thêm, và có đủ căn cứ để chuyển tiếp sang vòng sau hay chưa.
- **Khi nào họ dễ bị tổn thương / dễ hiểu sai**: Khi deadline shortlist gấp, màn hình mặc định sort theo điểm AI, hoặc khi output AI viết quá trôi chảy khiến họ bỏ qua CV gốc.
- **Họ thường tin AI đến mức nào**: Có policy HITL nhưng trong áp lực thực tế họ dễ dùng AI như một bộ lọc ngầm nếu hệ thống không tạo friction đúng lúc.

## 4. Bối cảnh ngành

- **Sự cố tương tự đã từng xảy ra**:
  - Amazon dừng tool recruiting nội bộ vì bias với từ khóa liên quan đến phụ nữ.
  - EEOC kiện iTutorGroup vì phần mềm tự động loại ứng viên theo tuổi.
  - Workday bị kiện vì applicant screening có thể tạo tác động bất lợi theo race, age, disability.
  - Air Canada cho thấy chatbot trong kênh chính thức vẫn có thể tạo liability nếu người dùng tin output sai.
  - Rikunabi cho thấy AI/analytics trong tuyển dụng có thể vi phạm consent và quyền riêng tư.
- **Quy định hoặc ràng buộc liên quan**:
  - Không phân biệt đối xử trong tuyển dụng.
  - Bảo vệ dữ liệu cá nhân ứng viên, bao gồm consent và giới hạn xử lý.
  - Quy trình nội bộ phải giữ human-in-the-loop trước quyết định loại/nhận.
- **Nguồn chính thức nên ưu tiên**:
  - JD đã publish trong ATS.
  - CV gốc và file đính kèm ứng viên nộp qua kênh chính thức.
  - Metadata ứng viên trong ATS và policy tuyển dụng nội bộ.

## 5. Ghi chú thêm

- Đây là bài nhóm Track 7, đã được hợp nhất từ các bản nháp thành viên trong `worksheet/team-inputs/`.
- Primary risk được cả nhóm ưu tiên là: **AI suy diễn thêm thông tin không có bằng chứng rõ trong CV, đặc biệt khi CV mơ hồ, OCR lỗi, hoặc recruiter đang under time pressure**.
- Các nhóm rủi ro còn lại cần được bao phủ trong test set gồm: automation bias theo sort/score, bias theo proxy (tuổi, giới, tên trường, career gap), privacy/consent, prompt injection trong CV, và escalation khi confidence thấp.
