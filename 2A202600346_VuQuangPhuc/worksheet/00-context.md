---
title: 00 - Boi canh san pham cua nhom
section: Day 25 - dung lai cho moi cuoc tro chuyen voi AI
format: Ca nhan hoa tu bai nhom
time: Dien 5 phut dau buoi
---

# 00-context.md - Boi canh san pham cua nhom

## 1. San pham

- **Ten san pham / bot**: CV Screening Copilot
- **San pham giup ai lam gi**: Ho tro recruiter tom tat CV, doi chieu CV voi job description, danh dau diem manh - diem thieu, va goi y cau hoi phong van cho vi tri internship/junior.
- **Nguoi dung gap san pham o dau**: He thong ATS noi bo, trang danh sach ung vien, trang chi tiet CV, man hinh shortlist.
- **Giai doan hien tai**: Dang thu nghiem noi bo truoc khi rollout cho team tuyen dung.

## 2. Pham vi

**AI duoc lam gi**

- Tom tat thong tin co bang chung ro trong CV va ho so ung vien.
- So sanh CV voi tieu chi JD de neu ra diem phu hop va diem con thieu.
- Goi y cau hoi phong van dua tren bang chung co san trong CV.

**AI khong duoc lam gi**

- Khong duoc tu dong reject hoac auto-shortlist ung vien ma khong co nguoi duyet.
- Khong duoc suy doan ky nang, so nam kinh nghiem, do phu hop, suc khoe, tuoi, gioi, tinh trang hon nhan, thai san, ton giao, dan toc, hay "culture fit" tu tin hieu mo ho.
- Khong duoc day PII nhu so dien thoai, email, dia chi nha vao ghi chu chia se rong trong team neu khong can thiet.

**Vi sao co gioi han nay**

Workflow nay co rui ro phap ly va fairness cao. Neu AI suy dien qua muc hoac bieu hien thien lech, ung vien co the bi loai oan ngay tu vong dau, cong ty mat ung vien tot, va quyet dinh tuyen dung co the vi pham quy dinh chong phan biet doi xu.

## 3. Nguoi dung

- **La ai**: Recruiter va hiring coordinator, thuong xu ly nhieu CV cung luc, khong phai luc nao cung doc ky tung CV.
- **Ho hoi AI khi nao**: Khi can loc nhanh 50-200 CV, khi CV mo ho, CV scan/PDF parse xau, hoac khi can chuan bi shortlist va cau hoi phong van.
- **Ho can quyet dinh gi sau khi hoi AI**: Review tay tiep, dua vao shortlist, yeu cau them thong tin, hoac chuyen sang hiring manager.
- **Khi nao ho de bi ton thuong / de hieu sai**: Khi dang gap KPI loc CV nhanh, tin rang tom tat cua AI la "y kien cua he thong", hoac khi CV duoc viet lan tieng Viet - tieng Anh, co project ngoai truong, freelance, career break.
- **Ho thuong tin AI den muc nao**: Co xu huong tin kha nhieu neu cau tra loi duoc hien thi gon, tu tin, va nam ngay trong ATS chinh thuc.

## 4. Boi canh nganh

- **Su co tuong tu da tung xay ra**:
  - [EEOC sue iTutorGroup, 2022-05-05](https://www.eeoc.gov/newsroom/eeoc-sues-itutorgroup-age-discrimination): phan mem tuyen dung tu dong loai ung vien lon tuoi.
  - [Mobley v. Workday, lenh ngay 2024-07-12](https://caselaw.findlaw.com/court/us-dis-crt-n-d-cal/116378658.html): toa an lien bang cho phep mot phan vu kien ve cong cu screening thuat toan tiep tuc.
  - [Khieu nai Intuit/HireVue, 2025-03-19](https://www.aclu.org/press-releases/complaint-filed-against-intuit-and-hirevue-over-biased-ai-hiring-technology-that-works-worse-for-deaf-and-non-white-applicants): cong nghe video interview bi cho la bat loi cho ung vien Deaf va non-white.
- **Quy dinh hoac rang buoc lien quan**:
  - [EEOC + DOJ canh bao ngay 2022-05-12](https://www.eeoc.gov/newsroom/us-eeoc-and-department-justice-warn-against-disability-discrimination): cong cu AI trong tuyen dung co the vi pham ADA.
  - [New York City Local Law 144, bat dau enforcement 2023-07-05](https://regulations.ai/regulations/RAI-US-NY-NYCL1XX-2021): bias audit va thong bao khi dung AEDT.
  - [EEOC hearing ve AI trong quyet dinh viec lam, 2023-01-31](https://www.eeoc.gov/newsroom/eeoc-hearing-explores-potential-benefits-and-harms-artificial-intelligence-and-other): co quan lien bang xem xet tac dong dan quyen cua he thong tu dong.
- **Nguon chinh thuc nen uu tien**:
  - CV goc va file dinh kem cua ung vien.
  - Job description va rubric screening do cong ty phe duyet.
  - Chinh sach anti-discrimination, data privacy, va quy trinh escalate noi bo.

## 5. Ghi chu them

- Day 25 duoc lam tren nen Day 24 Track 7 cua Vu Quang Phuc.
- Rui ro uu tien cao nhat trong repo nay: AI suy dien them ky nang/kinh nghiem tu CV mo ho hoac parse loi, sau do day recruiter den quyet dinh shortlist/reject sai.
- Bo test can co du ca failure ve hallucination, fairness, pressure trap, privacy, escalation, va misuse.

## Cach dung

```text
1. Mo cong cu AI phu hop voi buoc dang lam.
2. Dua toan bo noi dung file nay vao dau cuoc tro chuyen.
3. Chon prompt tham khao tu thu muc ../prompts/ va chinh lai neu can.
4. Doc lai ban nhap AI tao ra.
5. Sua lai cho dung boi canh Track 7.
6. Luu ket qua vao dung file trong worksheet/.
```
