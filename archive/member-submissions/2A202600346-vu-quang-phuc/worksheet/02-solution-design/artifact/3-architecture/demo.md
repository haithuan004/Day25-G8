---
artifact: 3 - Demo kien truc du lieu
format: so do xu ly + bang thanh phan
---

# demo.md - Demo kien truc du lieu

## 1. So do cach he thong xu ly

```text
Recruiter request
  -> Candidate file loader
  -> OCR / CV parser
  -> Parse quality check
       -> quality >= threshold?
          -> No  -> Manual review queue
               -> UI shows "Du lieu khong du de AI tu quyet"
               -> Audit log
          -> Yes -> Evidence extractor
               -> Claims + evidence spans + confidence
               -> Policy gate
                    -> Protected attribute request? -> Refuse + log
                    -> Missing evidence for key claim? -> Manual review + log
                    -> Sufficient evidence? -> Response builder
                         -> Output summary + verified claims only
                         -> UI badges + PII-redacted note
  -> Monitoring dashboard
       -> repeated low-confidence cases
       -> repeated refusal/misuse attempts
       -> parser failure clusters
```

## 2. Thanh phan chinh

| Thanh phan | Nhan gi? | Lam gi? | Tra ra gi? |
|---|---|---|---|
| OCR / CV parser | PDF, DOCX, image CV | Rut text, section, link, metadata | Structured candidate text + parser warnings |
| Parse quality check | Structured text + warnings | Tinh quality/confidence cho do day du va tinh doc duoc | Quality score + gate decision |
| Evidence extractor | CV text + JD rubric | Tao claim co evidence spans | Claims, evidence snippets, confidence |
| Policy gate | Claims + request cua recruiter | Chan misuse, chan unsupported shortlist/reject | Allow / refuse / manual review |
| Response builder | Claims da duyet | Tao summary an toan, redact PII neu can | Output cho UI |
| Audit log | Query, gate outcome, confidence | Luu pattern loi va misuse | Bao cao monitoring |

## 3. Khi he thong gap van de

| Khi nao loi xay ra? | He thong lam gi? | Nguoi dung thay gi? |
|---|---|---|
| Nguon chinh thuc/CV khong du | Chan screening recommendation | Banner "Khong du bang chung, can review tay" |
| OCR/parse loi hoac qua cham | Dung pipeline screening, log parser issue | Khong co shortlist/reject suggestion |
| Cau hoi vuot pham vi AI | Policy gate tu choi | Message refusal ngan + goi y quay lai rubric cong viec |
| Loi nay lap lai nhieu lan | Dashboard canh bao theo cluster | Team van hanh xem duoc top fail patterns |

## 4. Kiem tra nhanh

- [x] So do khong chi la "AI tra loi tot hon", ma co gate cu the.
- [x] Co cach xu ly khi thieu du lieu.
- [x] Co cach chuyen sang nguoi that.
- [x] Co monitoring de lan sau sua tot hon.
