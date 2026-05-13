---
artifact: 1 - FINAL ke hoach giai phap
bai-tap: 2 - Thiet ke giai phap
phase: Chon rui ro + chon tang + chon demo + chot 3 lop giai phap
time: 11:00-11:55
input: 00-context.md + 01-test-set-review/3-FINAL-test-set-eval-plan.md
nop-cuoi: Co - file cuoi Bai 2
---

# 1 - FINAL: Ke hoach giai phap

## Thong tin nhom

- **Chu de**: Track 7 - Tro ly sang loc CV va tuyen dung
- **Thanh vien**: Vu Quang Phuc - 2A202600346
- **Ngay**: 2026-05-13

## Phan A - Chon rui ro va tang giai phap

### Rui ro chinh duoc chon

- **ID tinh huong**: T-01
- **Mo ta ngan**: Khi recruiter can loc nhanh CV scan mo ho hoac CV parse loi, AI co xu huong suy dien them ky nang/so nam kinh nghiem thay vi chi bam vao bang chung co san, gay shortlist/reject sai cho ung vien.
- **Muc do**: Nang
- **Diem rui ro**: 25
- **Vi sao chon tinh huong nay**: Day la failure trung tam cua Track 7 vi no xay ra ngay diem bat dau workflow screening, co the gay loai oan ung vien tot, va de bi che giau boi cau van rat tu tin cua AI.

### Tim nguyen nhan goc

- [x] Thieu nguon du lieu dung.
- [x] AI doan khi khong biet.
- [x] Giao dien khien nguoi dung tin qua muc.
- [x] Quy trinh thieu nguoi duyet hoac thieu buoc chuyen sang nguoi that.
- [x] Khong co theo doi sau khi ra mat.
- [ ] Khac

### Bang noi nguyen nhan voi tang sua

| Nguyen nhan goc | Tang uu tien sua | Lop giai phap lien quan |
|---|---|---|
| CV parse loi, OCR thieu, link portfolio khong doc duoc | Du lieu / traceability / confidence gate | `3-architecture` la chinh |
| Model co xu huong lap cho trong bang suy dien "cho huu ich" | System prompt + evidence-bound output rule | `2-prompt` la chinh |
| Summary duoc hien thi gon va rat tu tin trong ATS | UX trust calibration + claim-level evidence | `1-uiux` la chinh |
| Recruiter dang gap va muon shortcut | Prompt refusal + UI manual review CTA | `1-uiux` + `2-prompt` |
| Loi lap lai nhieu lan nhung khong ai thay pattern | Logging + audit + re-test loop | `3-architecture` la chinh |

### Ket luan Phan A

**Nguyen nhan goc**: He thong chua ep AI bam sat bang chung o muc claim-level. Khi CV mo ho, parser loi, hoac nguon phu khong doc duoc, model van co dong luc "lap day cho trong" de giup recruiter loc nhanh. UI lai hien summary qua gon va tu tin, khien recruiter de bo qua CV goc. Cuoi cung, workflow chua co confidence gate va manual-review queue ro rang.

**Tang chinh can sua**: Du lieu/architecture la tang goc, sau do den prompt policy, va UI la lop can cuoi de giam over-reliance.

**Vi sao can 3 lop giai phap**:

- Lop giao dien: can lam recruiter thay bang chung, uncertainty, va lo trinh chuyen sang review tay.
- Lop chi dan AI: can cam AI bịa/suy dien khi khong co bang chung, va bat buoc dung wording dung muc tin cay.
- Lop kien truc du lieu: can tao evidence spans, confidence gate, va fallback khi parser/nguon loi.

## Phan B - Chon dinh dang demo

| Lop | Thu muc | Dinh dang demo chon | Thoi gian du kien |
|---|---|---|---|
| Giao dien | `1-uiux` | ASCII screen + bang state | 12 phut |
| Chi dan AI | `2-prompt` | Markdown prompt + 3 vi du hoi dap + ket qua thu lai | 10 phut |
| Kien truc du lieu | `3-architecture` | ASCII architecture + bang thanh phan | 13 phut |

**Ly do chon demo**

- Giao dien: ASCII du de minh hoa claim-level evidence, banner uncertainty, va nut manual review ma khong can dung cong cu design ngoai.
- Chi dan AI: Markdown ro nhat cho viec xem luat he thong, few-shot, va pass/fail check voi bo test.
- Kien truc du lieu: ASCII diagram hop voi workflow parse -> extract evidence -> confidence gate -> response builder -> logging.

## Phan C - Ba lop giai phap

### Lop 1 - Giao dien (`artifact/1-uiux/`)

- **Cach tiep can**: Thay summary mot khoi van ban tu tin bang giao dien co claim-level evidence, badge do tin cay, va nut "Review CV goc" / "Chuyen manual review".
- **Hanh dong phong ve bao phu**: Thong bao + Phat hien + Khac phuc
- **Demo**: `artifact/1-uiux/demo.md`
- **Trang thai**: Xong

Link chi tiet:

- `artifact/1-uiux/card.md`
- `artifact/1-uiux/demo.md`

### Lop 2 - Chi dan AI (`artifact/2-prompt/`)

- **Cach tiep can**: Bat buoc AI chi duoc viet claim ve ky nang/kinh nghiem khi co evidence span trong CV; neu khong co thi phai noi ro "chua thay bang chung" va/hoac escalate.
- **Hanh dong phong ve bao phu**: Ngan + Tu choi + Hoi lai + Dan nguon/evidence
- **Demo**: `artifact/2-prompt/demo.md`
- **Trang thai**: Xong

Link chi tiet:

- `artifact/2-prompt/card.md`
- `artifact/2-prompt/demo.md`

### Lop 3 - Kien truc du lieu (`artifact/3-architecture/`)

- **Cach tiep can**: Them pipeline OCR/parser quality check, evidence extraction, confidence gate, va manual-review queue; neu confidence thap thi cam AI de xuat shortlist/reject.
- **Hanh dong phong ve bao phu**: Ngan + Phat hien + Khac phuc
- **Demo**: `artifact/3-architecture/demo.md`
- **Trang thai**: Xong

Link chi tiet:

- `artifact/3-architecture/card.md`
- `artifact/3-architecture/demo.md`

## Tong kiem tra

| Cau hoi | Tra loi |
|---|---|
| Rui ro chinh da chon la gi? | T-01 |
| Nguyen nhan goc la gi? | CV/nguon yeu + model suy dien + UI qua tu tin + thieu confidence gate |
| 3 lop giai phap da du chua? | Giao dien: Co / Chi dan AI: Co / Kien truc: Co |
| 4 hanh dong da bao phu chua? | Ngan: Co / Phat hien: Co / Khac phuc: Co / Thong bao: Co |
| Nhom khac da gop y chua? | Chua, day la ban ca nhan hoa |
| Da sua gi sau tu phan bien? | Bo sung confidence gate, manual-review queue, va an PII o note share |

## Phan bien cheo: 4 cau tra loi ngan

| Goc phan bien | Tra loi |
|---|---|
| Dung tang | Co. Root cause chinh nam o bang chung du lieu va tendency suy dien, nen architecture + prompt la tang chinh, UI la lop chot |
| Cu the | Co. Moi lop deu co card va demo ro thanh phan va state |
| Du lop | Co. UI khong lap lai prompt; prompt khong thay the confidence gate; architecture khong giai quyet trust wording mot minh |
| Tac dung phu | Co latency, tang friction voi recruiter, va ton cong maintain parser/rubric; da giam bang only-on-risky-case gating va note ngan gon |
