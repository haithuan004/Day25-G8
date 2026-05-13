---
artifact: 3 — Demo kiến trúc dữ liệu
format: Mermaid flow + component table
---

# demo.md — Demo kiến trúc dữ liệu

## 1. Sơ đồ cách hệ thống xử lý (Mermaid)

### 1.1 Luồng tổng thể: ingest → gate → evidence → policy → UI

Luồng đọc từ trên xuống; nhánh **fallback** dừng hoặc chuyển sang người; **thông báo** gắn với UI/audit.

```mermaid
flowchart TD
    IN[Claim map + metadata request] --> JD{JD đã gắn và hợp lệ?}
    JD -->|Không| F1[📢 Yêu cầu gắn đúng JD]
    F1 --> S1[⛔ Dừng scoring / không auto-decide]
    JD -->|Có| CS{Consent xử lý OK?}

    CS -->|Không: batch chưa rõ| F2[📢 Cảnh báo policy / legal]
    F2 --> S2[⛔ Chặn workflow]
    CS -->|Có| PII{Shared-note mode có PII?}

    PII -->|Có| RD[Redact PII]
    RD --> NPII[📢 Note đã làm sạch để chia sẻ]
    NPII --> INJ
    PII -->|Không| INJ{Có prompt injection?}

    INJ -->|Có| NI[📢 Không thực thi instruction lạ]
    NI --> LOGI[📝 Log sự kiện injection]
    LOGI --> PR
    INJ -->|Không| PR{Protected / proxy request?}

    PR -->|Có| ESC[📢 Escalate / từ chối theo policy]
    PR -->|Không| EV{Đủ evidence cho claim high-impact?}

    EV -->|Không| HID[Ẩn hoặc đánh dấu cần review]
    HID --> NH[📢 Unsupported / cần duyệt tay]
    EV -->|Có| OUT[Verified claims đầy đủ]
    NH --> RBIN[→ Response builder: an toàn, phần yếu ẩn/mark review]
    OUT --> RBIN

    S1 -.-> MON[Monitoring: export không coverage, injection lặp]
    S2 -.-> MON
    LOGI -.-> MON
    ESC -.-> MON
    NH -.-> MON

    %% ĐỊNH NGHĨA LẠI MÀU SẮC ĐỂ ĐẠT ĐỘ TƯƠNG PHẢN TỐI ĐA
    classDef notify fill:#fff176,stroke:#fbc02d,stroke-width:2px,color:#000,font-weight:bold
    classDef stop fill:#ef9a9a,stroke:#c62828,stroke-width:2px,color:#000,font-weight:bold
    classDef ok fill:#a5d6a7,stroke:#2e7d32,stroke-width:2px,color:#000,font-weight:bold
    classDef decision fill:#81d4fa,stroke:#0288d1,stroke-width:2px,color:#000,font-weight:bold
    classDef monitor fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px,color:#4a148c,font-weight:bold,stroke-dasharray: 5 5
    classDef default color:#000,font-weight:bold

    %% Áp dụng class
    class F1,F2,NPII,NI,NH,ESC notify
    class S1,S2 stop
    class OUT,RBIN ok
    class JD,CS,PII,INJ,PR,EV,HID decision
    class MON,LOGI monitor
```

### 1.2 Policy engine: kiểm tra tuần tự, chặn / redact / escalate

Thứ tự phản ánh “dừng sớm khi thiếu điều kiện bắt buộc”, sau đó mới xử lý nội dung rủi ro và độ bao phủ evidence.

```mermaid
flowchart TD
    IN[Claim map + metadata request] --> JD{JD đã gắn và hợp lệ?}
    JD -->|Không| F1[📢 Yêu cầu gắn đúng JD]
    F1 --> S1[⛔ Dừng scoring / không auto-decide]
    JD -->|Có| CS{Consent xử lý OK?}

    CS -->|Không: batch chưa rõ| F2[📢 Cảnh báo policy / legal]
    F2 --> S2[⛔ Chặn workflow]
    CS -->|Có| PII{Shared-note mode có PII?}

    PII -->|Có| RD[Redact PII]
    RD --> NPII[📢 Note đã làm sạch để chia sẻ]
    NPII --> INJ
    PII -->|Không| INJ{Có prompt injection?}

    INJ -->|Có| NI[📢 Không thực thi instruction lạ]
    NI --> LOGI[📝 Log sự kiện injection]
    LOGI --> PR
    INJ -->|Không| PR{Protected / proxy request?}

    PR -->|Có| ESC[📢 Escalate / từ chối theo policy]
    PR -->|Không| EV{Đủ evidence cho claim high-impact?}

    EV -->|Không| HID[Ẩn hoặc đánh dấu cần review]
    HID --> NH[📢 Unsupported / cần duyệt tay]
    EV -->|Có| OUT[Verified claims đầy đủ]
    NH --> RBIN[→ Response builder: an toàn, phần yếu ẩn/mark review]
    OUT --> RBIN

    S1 -.-> MON[Monitoring: export không coverage, injection lặp]
    S2 -.-> MON
    LOGI -.-> MON
    ESC -.-> MON
    NH -.-> MON

    classDef notify fill:#fff8e6,stroke:#c90,stroke-width:2px
    classDef stop fill:#ffecec,stroke:#c33,stroke-width:2px
    classDef ok fill:#e8f5e9,stroke:#2e7d32

    class F1,F2,NPII,NI,NH,ESC notify
    class S1,S2 stop
    class OUT,RBIN ok
```

### 1.3 Gom nhánh lỗi → người dùng + hệ thống

```mermaid
flowchart LR
    subgraph user["Phản hồi cho người dùng"]
        U1[Banner / toast]
        U2[CTA manual review]
        U3[Form bổ sung JD / consent]
    end

    subgraph sys["Hệ thống"]
        L[Audit log]
        M[Metrics: low-confidence, injection]
    end

    MRQ[Manual review queue] --> U1
    MRQ --> U2
    JDMISS[Thiếu JD / consent] --> U3
    POL[Policy refuse / redact] --> U1

    MRQ --> L
    POL --> L
    OCRLOW[OCR thấp] --> M
    INJINJ[Injection flag] --> M
```

---

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
