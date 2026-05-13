---
artifact: 3 — Demo kiến trúc dữ liệu
format: ASCII architecture + component table
---

# demo.md — Demo kiến trúc dữ liệu

## 1. Sơ đồ cách hệ thống xử lý

```text
Recruiter opens candidate
  -> Attach JD + candidate CV
  -> File ingest
       -> OCR / parser
       -> Parser quality score
            -> low confidence? ---- yes ----> Manual review queue
            -> no -------------------------> Evidence extractor
  -> Evidence extractor
       -> claim candidates + supporting spans
  -> Policy / rule engine
       -> JD attached?
       -> consent ok for processing?
       -> PII detected in shared-note mode?
       -> prompt injection detected?
       -> protected/proxy request detected?
       -> enough evidence for high-impact claim?
  -> Response builder
       -> verified claims
       -> unsupported claims hidden or marked review
       -> shared mode note has PII redacted
  -> UI layer
       -> score + confidence + manual review CTA
  -> Logging / monitoring
       -> low-confidence clusters
       -> export without coverage attempts
       -> repeated injection attempts
```

## 2. Thành phần chính

| Thành phần | Nhận gì? | Làm gì? | Trả ra gì? |
|---|---|---|---|
| OCR / parser | PDF, DOCX, ảnh CV | Trích text, section, metadata | Structured text + parser warnings |
| Quality gate | Structured text | Tính confidence đọc được, phát hiện file không phải CV | Confidence + allow/manual-review |
| Evidence extractor | CV text + JD | Tạo claim + span hỗ trợ | Claim map |
| Policy engine | Claim map + user request | Chặn consent/PII/injection/proxy violations | Allow / refuse / redact / escalate |
| Response builder | Claim map đã qua rule | Tạo summary an toàn | Output cho UI |
| Monitoring log | Query + gate outcome | Theo dõi pattern lỗi lặp lại | Dashboard / audit |

## 3. Khi hệ thống gặp vấn đề

| Khi nào lỗi xảy ra? | Hệ thống làm gì? | Người dùng thấy gì? |
|---|---|---|
| OCR/parser confidence thấp | Không cho auto-decide | Banner low-confidence + Manual review |
| Thiếu JD hoặc JD sai | Dừng scoring | Yêu cầu gắn đúng JD |
| Yêu cầu import batch chưa rõ consent | Chặn workflow | Cảnh báo policy/legal |
| CV chứa instruction lạ | Flag injection | Không làm theo text đó, log sự kiện |
| Shared mode có PII | Redact | Note sạch để chia sẻ nội bộ |

## 4. Kiểm tra nhanh

- [x] Có gate cụ thể, không chỉ “AI trả lời tốt hơn”.
- [x] Có cách xử lý khi thiếu dữ liệu.
- [x] Có manual-review path.
- [x] Có monitoring để lần sau sửa tốt hơn.
