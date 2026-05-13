---
artifact: 3 - Lop kien truc du lieu
bai-tap: 2 - Thiet ke giai phap
demo: ./demo.md
---

# card.md - Lop kien truc du lieu

**Tinh huong xu ly**: T-01  
Xem `../../1-map-and-format.md` Phan A.

## 1. Giai phap la gi?

He thong them pipeline `parse -> quality check -> evidence extraction -> confidence gate -> response builder`. AI chi duoc tom tat va dua suggestion screening khi moi claim quan trong deu co evidence spans va confidence du nguong. Neu OCR/parse/link nguon loi, he thong chuyen case vao manual-review queue va log lai de audit.

## 2. Vi sao sua o lop kien truc du lieu?

- Nguyen nhan chinh cua T-01 nam o cho AI doc du lieu khong day du nhung van phai "tra loi cho xong".
- Neu khong co evidence spans va confidence gate, prompt/UI rat de bi qua mat.
- Day la lop co the ngan hallucination ngay tu nguon va tao trace de theo doi sau launch.

**Hanh dong phong ve chinh**:

- [x] Ngan loi bang nguon du lieu dung
- [x] Phat hien khi nguon thieu hoac loi
- [x] Khac phuc bang cach chuyen sang nguoi that
- [x] Ghi lai loi de cai thien sau

## 3. Demo nam o dau?

**File demo**: [`demo.md`](./demo.md)

Demo co:

- So do data flow
- Parser quality score
- Evidence store cho tung claim
- Confidence gate cho screening decision
- Manual-review queue va audit log

## 4. Tac dung phu

**Co the gay van de gi?**

- Tang latency vi can OCR/parse/quality check.
- Tang do phuc tap he thong va chi phi van hanh.
- Can co nguoi so huu rubric, threshold, va parser maintenance.

**Nhom giam van de do bang cach nao?**

- Chi bat quality gate/man-review cho nhom task high-impact nhu shortlist/reject recommendation.
- Cache ket qua parse va evidence spans tren candidate version ID.
- Dinh ky review log fail de chinh parser/rubric thay vi mo rong he thong vo toi va.

## 5. Checklist truoc khi nop

- [x] So do cho thay du lieu di tu dau den dau.
- [x] Co buoc kiem tra nguon truoc khi AI tra loi.
- [x] Co cach xu ly khi khong co du lieu.
- [x] Co cach chuyen sang nguoi that voi tinh huong rui ro cao.
- [x] Co cach biet loi nay co dang lap lai khong.

**Nguoi phu trach**: Vu Quang Phuc
