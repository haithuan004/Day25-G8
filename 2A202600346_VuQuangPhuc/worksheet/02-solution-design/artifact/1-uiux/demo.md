---
artifact: 1 - Demo giao dien
format: phac thao cac man hinh chinh
---

# demo.md - Demo giao dien

## 1. Man hinh chinh

```text
+----------------------------------------------------------------------------------+
| Candidate Summary - Marketing Intern                             Confidence: LOW |
| CV source: scan.pdf (OCR quality: 0.58)                                          |
+----------------------------------------------------------------------------------+
| AI canh bao: Du lieu CV khong day du. Khong nen shortlist/reject chi dua vao AI. |
| [Mo CV goc] [Manual review] [Xem OCR issues]                                     |
+----------------------------------------------------------------------------------+
| Claims trich xuat                                                                 |
|                                                                                  |
| 1. "Da co 2 nam Meta Ads"                     [CAN REVIEW TAY]                   |
|    Ly do: Khong tim thay bang chung ro trong CV.                                 |
|                                                                                  |
| 2. "Co kinh nghiem viet noi dung cho CLB"      [DA CO BANG CHUNG]               |
|    Evidence: "Quan ly fanpage CLB Truyen thong, 12 bai/thang"                    |
|                                                                                  |
| 3. "Phu hop shortlist ngay"                    [KHONG CHO PHEP AUTO-DECIDE]      |
|    Ly do: Thieu bang chung cho 2 claim screening quan trong.                     |
+----------------------------------------------------------------------------------+
| Ghi chu shortlist chia se                                                        |
| - Ky nang da xac minh: content writing, fanpage operation                        |
| - Muc can review: paid ads experience, portfolio external                        |
| - PII da an trong note share                                                     |
+----------------------------------------------------------------------------------+
```

## 2. Trang thai can minh hoa

| Trang thai | Nguoi dung thay gi? | Nguoi dung lam gi tiep? |
|---|---|---|
| Co nguon xac minh | Claim co badge `Da co bang chung` va trich dan tu CV | Co the tiep tuc review/shortlist |
| Chua co nguon xac minh | Banner vang + claim `Can review tay` | Mo CV goc hoac portfolio, khong auto-quyet |
| AI khong nen tu tra loi | Claim `Khong cho phep auto-decide` | Chuyen manual review |
| Can chuyen sang nguoi that | Nut `Manual review` duoc dat noi bat | Day case cho recruiter/hiring manager doc tay |

## 3. Ghi chu cho tung thanh phan

- Banner canh bao: nam tren dau summary, chi hien khi confidence thap hoac parser loi.
- Badge claim-level: hien sat tung nhan dinh, tranh mot tong ket qua tu tin chung chung.
- Nut `Mo CV goc`: giup recruiter quay ve nguon chinh thay vi tin tom tat.
- Khu `Ghi chu shortlist chia se`: chi giu thong tin screening lien quan, da bo PII khong can thiet.

## 4. Kiem tra nhanh

- [x] Nhin vao demo la hieu rui ro dang duoc chan o dau.
- [x] Co trang thai khi AI khong co du thong tin.
- [x] Co cach chuyen sang nguoi that.
- [x] Cau chu du ngan de dat tren man hinh that.
