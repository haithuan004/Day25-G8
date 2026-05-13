---
title: 00 — Bối cảnh sản phẩm của nhóm
section: Day 25 — dùng lại cho mọi cuộc trò chuyện với AI
format: Nhóm
time: Điền 5 phút đầu buổi
---

# 00-context.md — Bối cảnh sản phẩm của nhóm

---

## 1. Sản phẩm

- **Tên sản phẩm / bot**: AI CV Screening Assistant — trợ lý sàng lọc CV tích hợp trong ATS nội bộ
- **Sản phẩm giúp ai làm gì**: Giúp HR recruiter đọc nhanh CV ứng viên — tóm tắt thông tin chính, so sánh với JD, và gợi ý câu hỏi phỏng vấn — thay thế việc đọc thủ công từng hồ sơ trong đợt tuyển dụng lớn.
- **Người dùng gặp sản phẩm ở đâu**: ATS nội bộ công ty — recruiter mở trang chi tiết CV và thấy AI summary bên cạnh CV gốc.
- **Giai đoạn hiện tại**: Chuẩn bị ra mắt — đang test nội bộ trước khi dùng thật trong đợt tuyển dụng.

---

## 2. Phạm vi

**AI được làm gì**
- Tóm tắt CV ứng viên: kinh nghiệm, kỹ năng, học vấn, dự án nổi bật
- So sánh CV với job description và nêu điểm khớp / không khớp rõ ràng
- Gợi ý 2–3 câu hỏi phỏng vấn dựa trên CV cụ thể của ứng viên
- Flag uncertainty khi CV thiếu thông tin hoặc không đủ cơ sở để đánh giá

**AI không được làm gì**
- Đưa ra quyết định shortlist hoặc reject cuối — quyền đó thuộc recruiter
- Tự động gửi email thông báo cho ứng viên
- Claim thông tin định lượng (số năm kinh nghiệm, scope dự án) khi CV không ghi rõ
- Đánh giá ứng viên theo bất kỳ đặc điểm nào ngoài năng lực và kinh nghiệm liên quan đến JD

**Vì sao có giới hạn này**
Quyết định tuyển dụng ảnh hưởng trực tiếp đến cơ hội nghề nghiệp của người thật. CV thường thiếu thông tin — AI suy diễn sai sẽ dẫn đến shortlist/reject oan mà ứng viên không có kênh khiếu nại. Recruiter cần giữ quyền kiểm soát và trách nhiệm cuối.

---

## 3. Người dùng

- **Là ai**: HR recruiter hoặc hiring manager tại startup/SME, 25–40 tuổi, không có chuyên môn kỹ thuật AI, xử lý 100–300 CV mỗi đợt tuyển dụng
- **Họ hỏi AI khi nào**: Khi mở từng CV trong ATS để quyết định có đưa vào shortlist không — thường trong 3–5 ngày làm shortlist
- **Họ cần quyết định gì sau khi hỏi AI**: Shortlist hay bỏ qua ứng viên này; có cần đọc lại CV gốc không; câu hỏi nào cần hỏi trong phỏng vấn
- **Khi nào họ dễ bị tổn thương / dễ hiểu sai**: Khi deadline gấp — recruiter đọc AI summary mà không đọc CV gốc, tin vào số liệu AI đưa ra (số năm kinh nghiệm, tên công nghệ) mà không verify
- **Họ thường tin AI đến mức nào**: Tin ngay khi summary trông chuyên nghiệp và đầy đủ, đặc biệt dưới áp lực thời gian

---

## 4. Bối cảnh ngành

- **Sự cố tương tự đã từng xảy ra**: Amazon AI recruiting tool (2018) bị tắt vì phát hiện hệ thống penalize CV có từ "women's" — bias học từ dữ liệu tuyển dụng lịch sử. Các ATS dùng NLP để parse CV cũng có documented cases về extraction error khi CV không theo format chuẩn.
- **Quy định hoặc ràng buộc liên quan**: Tuyển dụng phải đảm bảo không phân biệt đối xử theo giới tính, tuổi, xuất xứ (Bộ luật Lao động Việt Nam). AI summary không được là cơ sở duy nhất để reject ứng viên.
- **Nguồn chính thức nên ưu tiên**: CV gốc do ứng viên nộp là nguồn sự thật duy nhất — AI chỉ được claim điều có trong văn bản CV, không suy diễn thêm.

---

## 5. Ghi chú thêm

**Primary failure cần giải quyết (từ Day 24):**
Khi CV ứng viên thiếu thông tin định lượng (số năm kinh nghiệm, scope dự án), AI có xu hướng điền thông tin suy diễn vào tóm tắt thay vì báo cáo uncertainty và đề nghị recruiter xem CV gốc, gây hậu quả shortlist sai cho recruiter và mất cơ hội oan cho ứng viên.

**Safety question cần test:**
Trong AI assistant sàng lọc CV tích hợp trong ATS, khi CV ứng viên thiếu thông tin định lượng, AI có bịa hoặc suy diễn thông tin không có trong CV vào tóm tắt không, gây hậu quả cho ứng viên bị shortlist/reject sai?

**Thành viên nhóm:** Nguyễn Đức Mạnh
