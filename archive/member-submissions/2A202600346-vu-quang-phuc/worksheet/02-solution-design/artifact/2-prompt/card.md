---
artifact: 2 - Lop chi dan AI
bai-tap: 2 - Thiet ke giai phap
demo: ./demo.md
---

# card.md - Lop chi dan AI

**Tinh huong xu ly**: T-01  
Xem `../../1-map-and-format.md` Phan A.

## 1. Giai phap la gi?

Them system prompt evidence-bound cho CV Screening Copilot: moi claim ve ky nang, kinh nghiem, so nam, muc do phu hop, hoac de xuat shortlist phai gan voi bang chung tu CV. Neu khong co evidence span, AI phai noi ro "chua thay bang chung" va chuyen sang huong manual review thay vi lap day cho trong.

## 2. Vi sao sua o lop chi dan AI?

- Model dang co xu huong "huu ich" bang cach suy dien thay vi giu boundary.
- Recruiter co the gay pressure de AI doan nhanh, nen can luat refusal ro rang.
- Prompt la noi nhanh nhat de enforce: khi nao tom tat, khi nao canh bao, khi nao tu choi, khi nao escalate.

**Hanh dong phong ve chinh**:

- [x] Ngan cau tra loi sai ngay tu dau
- [x] Bat buoc neu evidence khi noi thong tin quan trong
- [x] Tu choi tra loi khi thieu can cu
- [x] Chuyen nguoi that khi vuot pham vi

## 3. Demo nam o dau?

**File demo**: [`demo.md`](./demo.md)

Demo co:

- Luat evidence-bound cho AI
- Mau cau khi thieu bang chung
- Mau cau khi can chuyen sang manual review
- 3 vi du hoi dap
- Thu lai voi cac case T-01, T-06, T-09

## 4. Tac dung phu

**Co the gay van de gi?**

- AI co the than trong qua muc va tra loi "chua chac" nhieu hon, lam recruiter thay cham.
- Wording co the cung neu prompt dat rule qua cat.
- Neu khong co architecture ho tro evidence span, prompt don le van co the fail trong mot so truong hop parser rat xau.

**Nhom giam van de do bang cach nao?**

- Chi bat buoc evidence rule cho claim screening high-impact, khong bat output nao cung dai dong.
- Them few-shot mau "refuse mem" de AI van huu ich: de xuat mo CV goc, manual review, hoac yeu cau them file ro hon.
- Phu hop voi `3-architecture` de prompt nhan duoc metadata confidence va evidence spans that.

## 5. Checklist truoc khi nop

- [x] Luat viet du cu the de AI lam theo.
- [x] Co mau cau khi AI khong co du thong tin.
- [x] Co vi du cho tinh huong de sai.
- [x] Co thu lai bang tinh huong trong Bai 1.
- [x] Khong dung prompt nhu cach duy nhat.

**Nguoi phu trach**: Vu Quang Phuc
