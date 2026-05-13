---
artifact: 2 — Lớp chỉ dẫn AI
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp chỉ dẫn AI

**Tình huống xử lý**: T-01, T-04, T-05, T-08, T-09

## 1. Giải pháp là gì?

Nhóm thêm policy “evidence-bound screening”: AI chỉ được viết claim về skill, years, scope, fit, hoặc shortlist signal nếu claim đó map được vào bằng chứng có trong CV/JD. Prompt cũng cấm protected-attribute inference, cấm score override theo pressure, và bắt AI hỏi lại khi thiếu JD hoặc thiếu dữ kiện.

## 2. Vì sao sửa ở lớp chỉ dẫn AI?

- Unsupported inference phần lớn bắt đầu ở behavior “helpful guessing” của model.
- Pressure từ recruiter là trường hợp prompt cần chặn trực tiếp trước khi output ra UI.

**Hành động phòng vệ chính**:

- [x] Ngăn câu trả lời sai ngay từ đầu
- [x] Bắt buộc nêu evidence khi nói về thông tin quan trọng
- [x] Từ chối trả lời khi thiếu căn cứ
- [x] Chuyển người thật khi vượt phạm vi

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo gồm:

- System prompt rút gọn
- Few-shot cho unsupported inference, age proxy, và thiếu JD
- Bảng replay nhanh với vài case final

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**

- AI có thể thận trọng hơn, đôi khi trả lời “chưa đủ căn cứ” nhiều hơn mong muốn.
- Nếu prompt quá cứng, recruiter có thể thấy ít hữu ích hơn ở các case low-risk.

**Nhóm giảm vấn đề đó bằng cách nào?**

- Chỉ buộc evidence ở những claim high-impact.
- Dùng refusal mềm: từ chối suy diễn nhưng vẫn gợi ý hành động an toàn tiếp theo.
- Kết hợp với architecture để prompt có metadata confidence thật, không phải đoán.

## 5. Checklist trước khi nộp

- [x] Luật viết đủ cụ thể để AI làm theo.
- [x] Có mẫu câu khi AI không có đủ thông tin.
- [x] Có ví dụ cho tình huống dễ sai.
- [x] Có thử lại bằng tình huống trong Bài 1.
- [x] Không dùng prompt như cách duy nhất.

**Người phụ trách**: Nguyễn Đức Mạnh
