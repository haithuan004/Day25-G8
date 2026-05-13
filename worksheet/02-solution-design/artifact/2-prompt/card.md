---
artifact: 2 — Lớp chỉ dẫn AI
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
track: 7 — Trợ lý sàng lọc CV và tuyển dụng
nguoi-phu-trach: Nguyễn Đức Mạnh
---

# card.md — Lớp chỉ dẫn AI

**Tình huống xử lý chính**: T-01 (Bịa thông tin — AI suy diễn skill/experience từ CV mơ hồ hoặc OCR lỗi)  
**Tình huống liên quan**: T-02 (Missing must-have), T-07 (Export không có manual check), T-08 (Pressure estimate)  

Xem `../../1-map-and-format.md` Phần A.

---

## 1. Giải pháp là gì?

Khi CV không cung cấp bằng chứng rõ ràng cho một kỹ năng, chứng chỉ hoặc số năm kinh nghiệm cụ thể, AI **bắt buộc** phải ghi nhận gap thay vì suy diễn hoặc ước lượng. Luật được chia làm hai lớp: (1) **luật không suy diễn** — AI chỉ trích dẫn điều có trong CV, không điền chỗ trống bằng inference; (2) **luật từ chối có hướng dẫn** — khi recruiter ép estimate hoặc hỏi "gần đúng cũng được", AI từ chối ngắn gọn và đưa ra bước tiếp theo cụ thể (yêu cầu portfolio, đặt câu hỏi phỏng vấn kỹ thuật, hoặc ghi note pending verification).

Giải pháp được viết vào system prompt và có ví dụ mẫu câu phủ nhận rõ (few-shot), để AI không rơi vào trạng thái "helpful guessing" khi bị áp lực về thời gian.

---

## 2. Vì sao sửa ở lớp chỉ dẫn AI?

- **AI đang trả lời quá tự tin khi thiếu nguồn.** Khi CV chỉ ghi "digital marketing experience" mà không có số liệu cụ thể, AI có xu hướng suy diễn thành "có thể đã có kinh nghiệm Meta Ads" thay vì ghi gap.
- **AI đang chiều theo giả định sai của người dùng.** Recruiter hỏi theo kiểu "bạn này có 2 năm Meta Ads chưa?" — framing câu hỏi như xác nhận, AI có xu hướng confirm thay vì phản biện.
- **AI cần luật rõ: khi nào trả lời, khi nào từ chối, khi nào chuyển sang người thật.** Hiện chưa có boundary này trong prompt mặc định.
- **Có thể sửa nhanh bằng prompt trước khi thay đổi hệ thống lớn hơn.** Sửa ở lớp chỉ dẫn không yêu cầu thay đổi data pipeline hay UI.

**Hành động phòng vệ chính**:
- [x] Ngăn câu trả lời sai ngay từ đầu — luật "chỉ trích dẫn, không suy diễn"
- [x] Bắt buộc nêu nguồn khi nói về thông tin quan trọng — mọi claim về skill/experience phải có trích dẫn từ CV
- [x] Từ chối trả lời khi thiếu căn cứ — luật từ chối có hướng dẫn bước tiếp theo
- [x] Chuyển người thật khi vượt phạm vi — escalation path rõ khi CV mơ hồ và recruiter cần quyết định gấp

---

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo có:
- System prompt đầy đủ với 5 luật cốt lõi + cách nêu nguồn
- Mẫu câu khi thiếu bằng chứng trong CV
- Mẫu câu khi recruiter ép estimate
- Mẫu câu khi cần chuyển sang người thật
- 3 ví dụ hỏi đáp few-shot nhúng trong prompt
- Kết quả thử lại với T-01, T-02, T-08 từ Bài 1

---

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**

- **AI từ chối quá nhiều:** Nếu luật "phải có bằng chứng" áp dụng cứng với mọi câu hỏi, AI sẽ từ chối cả những câu recruiter chỉ cần tóm tắt sơ bộ — làm chậm quy trình và recruiter tắt tool.
- **Câu trả lời cứng và thiếu helpful:** Từ chối không kèm bước tiếp theo khiến recruiter không biết phải làm gì, tăng friction thay vì giảm.
- **OCR thấp bị xử lý như CV mơ hồ:** Nếu CV bị OCR lỗi nhưng nội dung thực ra đủ, AI có thể từ chối sai và tạo false gap.

**Nhóm giảm vấn đề đó bằng cách nào?**

- **Tách từ chối mềm và từ chối cứng:** Thông tin có thể thay đổi (số năm, chứng chỉ, scope công việc) → từ chối cứng + flag. Tóm tắt chung (ngành, vai trò) → AI được phép paraphrase có disclaimer.
- **Từ chối luôn kèm bước tiếp theo cụ thể:** Không chỉ nói "không đủ bằng chứng" mà ghi rõ: "Mình đề xuất hỏi thêm: [câu hỏi phỏng vấn kỹ thuật cụ thể]" hoặc "Recruiter có thể yêu cầu portfolio/link project."
- **Kiểm tra lại bằng bộ tình huống từ Bài 1:** Sau mỗi lần chỉnh prompt, chạy lại T-01, T-02, T-07, T-08 để đảm bảo không over-refusal và không under-refusal.

---

## 5. Checklist trước khi nộp

- [x] Luật viết đủ cụ thể để AI làm theo (5 luật có ví dụ mẫu câu trong demo.md).
- [x] Có mẫu câu khi AI không có đủ thông tin (Mẫu 1 và Mẫu 2 trong demo.md).
- [x] Có ví dụ cho tình huống dễ sai (T-01 pressure trap, T-02 missing must-have).
- [x] Có thử lại bằng tình huống trong Bài 1 (Phần 3 demo.md: T-01, T-02, T-08).
- [x] Không dùng prompt như cách duy nhất — card ghi rõ giới hạn và trường hợp cần sửa ở lớp dữ liệu (OCR confidence) hoặc quy trình (escalation path).

**Người phụ trách**: Nguyễn Đức Mạnh
