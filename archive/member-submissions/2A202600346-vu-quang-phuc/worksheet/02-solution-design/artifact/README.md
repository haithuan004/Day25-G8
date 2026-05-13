---
folder: artifact/ - 3 lop giai phap
bai-tap: 2 - Thiet ke giai phap
phase: Xay demo
nop-cuoi: Co - nop du 3 thu muc con
---

# Thu muc artifact/ - 3 lop giai phap

Thu muc nay da duoc hoan thien cho rui ro chinh `T-01`: AI suy dien them ky nang/so nam kinh nghiem tu CV mo ho hoac parse loi.

## Cau truc da nop

```text
artifact/
├── 1-uiux/
│   ├── card.md
│   └── demo.md
│
├── 2-prompt/
│   ├── card.md
│   └── demo.md
│
└── 3-architecture/
    ├── card.md
    └── demo.md
```

## Vai tro cua tung lop

| Thu muc | Lop giai phap | Dieu duoc chung minh |
|---|---|---|
| `1-uiux/` | Giao dien | Recruiter thay bang chung, uncertainty, va duong chuyen sang manual review |
| `2-prompt/` | Chi dan AI | AI khong duoc suy dien khi thieu bang chung; phai tu choi/escalate dung luc |
| `3-architecture/` | Kien truc du lieu | He thong co parse quality check, evidence extraction, confidence gate, va logging |

## Mapping voi 4 hanh dong phong ve

| Hanh dong | Lop bao phu chinh |
|---|---|
| Ngan | `2-prompt/`, `3-architecture/` |
| Phat hien | `1-uiux/`, `3-architecture/` |
| Khac phuc | `1-uiux/`, `3-architecture/` |
| Thong bao | `1-uiux/` |

## Ghi chu

- 3 lop nay bo sung cho nhau, khong phai 3 bien the cung mot y tuong.
- Neu prompt fail, architecture van co confidence gate.
- Neu architecture co du lieu thieu, UI van thong bao va chan recruiter auto-quyet.
