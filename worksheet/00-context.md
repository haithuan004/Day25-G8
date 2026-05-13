---
title: 00 — Bối cảnh sản phẩm của nhóm
section: Day 25 — dùng lại cho mọi cuộc trò chuyện với AI
format: Nhóm
time: Điền 5 phút đầu buổi
---

# 00-context.md — Bối cảnh sản phẩm của nhóm

Điền file này một lần ở đầu buổi. Sau đó, mỗi lần dùng AI, hãy đưa toàn bộ nội dung file này vào đầu cuộc trò chuyện.

Lý do: AI không tự nhớ bối cảnh giữa các cuộc trò chuyện. Nếu mỗi lần đưa bối cảnh khác nhau, câu trả lời cũng sẽ lệch.

---

## 1. Sản phẩm

- **Tên sản phẩm / bot**: Trợ lý sàng lọc CV và tuyển dụng (module đánh giá CV trong ATS)
- **Sản phẩm giúp ai làm gì**: Hỗ trợ HR/recruiter đối chiếu CV với JD đã publish: xuất điểm 0–10 theo rubric nội bộ, 4–6 bullet “Lý do — AI (tham khảo)” gắn nhãn tiêu chí JD, kèm đoạn trích ngắn từ CV khi bóc tách được — nhằm giảm khối lượng đọc thủ công trong đợt tuyển (khoảng 100–300 CV/JD).
- **Người dùng gặp sản phẩm ở đâu**: Tab/màn **“CV review”** trong **ATS nội bộ** doanh nghiệp (vendor hoặc self-host), dữ liệu theo tenant; không crawl nguồn bên ngoài ATS.
- **Giai đoạn hiện tại**: Đang thử nghiệm (pilot nội bộ SME)

---

## 2. Phạm vi

**AI được làm gì**

- Nhận **JD đã publish (text)** + **file CV (PDF/DOC)** + **metadata ứng viên cơ bản** trong ATS làm đầu vào.
- Trả **điểm 0–10** map với rubric/JD và **4–6 bullet** giải thích, mỗi bullet gắn tiêu chí JD (ví dụ: stack, năm kinh nghiệm, chứng chỉ).
- Đính kèm **đoạn trích ngắn** từ CV làm căn cứ khi trích xuất được; nếu không trích được thì ghi rõ kiểu **“suy luận từ JD/CV — cần đọc tay”**.
- Cho phép danh sách ứng viên được **sắp xếp theo điểm AI** như một công cụ hỗ trợ, kèm trạng thái **“Chưa human review”** trên từng dòng.

**AI không được làm gì**

- **Không** gửi email từ chối/nhận thay người.
- **Không** đổi stage/trạng thái ứng viên trong ATS.
- **Không** đặt lịch phỏng vấn.
- **Không** ghi nhận pass/loại hay quyết định tuyển dụng cuối cùng thay người — mọi quyết định gắn với pháp lý/uy tín thương hiệu vẫn thuộc HR và quy trình nội bộ.

**Vì sao có giới hạn này**

- **Công bằng tuyển dụng & trách nhiệm pháp lý**: điểm và bullet chỉ mang tính tham khảo; quyết định loại/nhận phải có HITL theo policy.
- **Rủi ro vận hành**: tin vào sort từ AI + điểm quá mức dễ biến thành “lọc ngầm” — ứng viên đủ điều kiện vẫn có thể bị bỏ qua nếu CV nằm ngoài bucket điểm cao mà HR không mở file.
- **Chất lượng đầu vào**: CV scan, PDF nhiều cột, OCR/reading order lệch có thể làm sai nội dung đưa vào mô hình; cần tách bạch vai trò “trích xuất tài liệu” vs “suy luận JD”.
- **Hợp đồng & bảo mật**: vendor cam kết **không dùng CV khách để train** công khai; giới hạn cũng giảm rủi ro lộ/lạm dụng dữ liệu ứng viên.

---

## 3. Người dùng

- **Là ai**: **HR / recruiter in-house** doanh nghiệp **SME**, team tuyển nhỏ — thường là HR **dưới ~2 năm kinh nghiệm** hoặc HR **kiêm tuyển** một mass role (ví dụ Software Engineer Mid). C-level chỉ vào khi escalation (lương, seniority, case nhạy cảm), không phải user hằng ngày của module.
- **Họ hỏi AI khi nào**: Sau khi mở đợt ứng tuyển (rolling hoặc sau deadline), **giữa các sprint tuyển**, khi cần nộp **shortlist đầu tuần** cho hiring manager; áp lực **time-to-shortlist** và SLA từ HM.
- **Họ cần quyết định gì sau khi hỏi AI**: Ưu tiên đọc CV nào trước, ai đưa vào vòng sâu hơn / shortlist — dựa trên điểm + bullet tham khảo, **nhưng** vẫn phải tự đối chiếu file gốc khi nghi ngờ trích dẫn hoặc điểm lệch kỳ.
- **Khi nào họ dễ bị tổn thương / dễ hiểu sai**: Khối lượng **100–300 CV/đợt**, deadline ngắn; màn hình **mặc định sort giảm dần theo điểm AI** + badge “Chưa human review” nhỏ — dễ **ưu tiên đầu bảng** và **không mở** CV ở bucket điểm thấp; policy HITL trên giấy không tự đủ nếu hành vi thực tế vẫn lọc theo ngưỡng điểm.
- **Họ thường tin AI đến mức nào**: Có policy HITL bắt buộc trước quyết định loại/nhận, nhưng trong áp lực KPI họ **dễ tin sort + điểm** để “dọn đống” trước khi đọc sâu — cần coi đây là **over-reliance** tiềm ẩn chứ không chỉ “model sai”.

---

## 4. Bối cảnh ngành

- **Sự cố tương tự đã từng xảy ra**: Các hệ thống ATS/scoring tự động từng bị chỉ trích vì **thiên lệch** hoặc **ưu tiên sai tín hiệu** (kinh nghiệm: doanh nghiệp thu hồi hoặc điều chỉnh tool ML tuyển dụng khi phát hiện tác động công bằng). Ở bối cảnh module này, **sai trích xuất OCR/layout** hoặc **tiêu thụ UI theo điểm** cũng có thể dẫn tới **false negative** (ứng viên đủ must-have nhưng không được xem) hoặc **false positive** (lãng phí slot phỏng vấn, +3–8 giờ panel/tuần tùy quy mô).
- **Quy định hoặc ràng buộc liên quan**: Nguyên tắc **cơ hội việc làm công bằng**, bảo vệ dữ liệu cá nhân ứng viên, policy nội bộ về **HITL** và audit shortlist; điều khoản **vendor** về không train trên CV khách công khai.
- **Nguồn chính thức nên ưu tiên**: **JD đã publish** trong ATS; **nội dung CV ứng viên** đã nộp qua kênh chính thức; **metadata ứng viên** trong hệ thống — không dùng nguồn crawl ngoài làm căn cứ điểm số.

---

## 5. Ghi chú thêm

- **Track Day 24**: Track **7 — Trợ lý sàng lọc CV và tuyển dụng**; học viên tham chiếu risk map: **Hồ Hải Thuận**, mã **2A202600058**.
- **Rủi ro đã map (tóm tắt cho AI)**: (1) **Pipeline OCR/PDF/reading order** làm text đưa vào mô hình lệch → điểm + quote “có vẻ có căn cứ” nhưng sai; (2) **UI + governance**: sort theo điểm + không đủ coverage bucket thấp → thiếu cơ hội có hệ thống dù model chỉ sai vừa phải; (3) **Prompt-injection / thao túng CV** (văn ẩn, chỉ dẫn trong PDF) làm lệch scoring hoặc quote.
- **Harm đã nhận diện**: Direct user = HR thấy điểm + bullet; affected = **ứng viên** mất cơ hội dù không chạm ATS; hidden harm = **cứng hóa lợi thế CV “máy đọc tốt”** vs scan/layout phức tạp; test naive dễ miss **PDF gốc đúng nhưng reading order/cột sai**, timeline trong ảnh, đa ngôn ngữ token lạ.
- **Mục tiêu Day 25**: Thiết kế kiểm thử và giải pháp nhiều lớp (UI/UX, prompt/guardrail, kiến trúc dữ liệu) xoay quanh rủi ro đã chọn từ bài Day 24 — khi brainstorm, tránh gộp mọi lỗi thành “hallucination model” mà bỏ qua ingestion và hành vi người dùng trên ATS.

---

## Cách dùng

```text
1. Mở công cụ AI phù hợp với bước đang làm.
2. Đưa toàn bộ nội dung file này vào đầu cuộc trò chuyện.
3. Chọn prompt tham khảo từ thư mục ../prompts/ và chỉnh lại nếu cần.
4. Đọc lại bản nháp AI tạo ra.
5. Sửa lại cho đúng bối cảnh nhóm.
6. Lưu kết quả vào đúng file trong worksheet/.
```

Ghi chú: nội dung trong `[...]` là chỗ cần điền. Sau khi điền xong, xóa dấu ngoặc nếu không cần giữ.
