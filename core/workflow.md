# Workflow V3 — 14 Bước + 7 Chế Độ

> Khung: 14 bước Mula (chi tiết) + Triage/Citation Gate/Quality Rubric (Tiểu Tâm) + Router tự động (Mula)

## Pipeline Tổng Thể

```
┌─────────────────────────────────────────────────────────────────┐
│              YOUR NEXT LAWYER V3 — PIPELINE                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  USER GỬI VẤN ĐỀ                                               │
│       │                                                          │
│       ▼                                                          │
│  ⓪ TRIAGE — Quét khẩn cấp ────── 🔴 → Hành động ngay          │
│       │                                                          │
│       ▼                                                          │
│  ① TIẾP NHẬN (Intake) — Phân loại lĩnh vực, vai trò, mức khẩn │
│       │                                                          │
│       ▼                                                          │
│  ② THU THẬP (Clarify) — Hỏi theo bộ câu hỏi RIÊNG mảng        │
│       │                                                          │
│       ▼                                                          │
│  ③ ROUTER — Tự chọn chế độ + số personas theo độ phức tạp      │
│       │                                                          │
│       ▼                                                          │
│  ④ NGHIÊN CỨU (Research) — Xác định luật áp dụng               │
│       │                                                          │
│       ▼                                                          │
│  ⑤ CITATION GATE — 3 lớp kiểm chứng (✅/⚠️/❌)                 │
│       │                                                          │
│       ▼                                                          │
│  ⑥ TRIỆU TẬP HỘI ĐỒNG (Council) — Spawn personas              │
│       │                                                          │
│       ▼                                                          │
│  ⑦ TỔNG HỢP (Synthesize) — Tổng Cố Vấn merge                  │
│       │                                                          │
│       ▼                                                          │
│  ⑧ KỊCH BẢN (Scenario) — Decision tree đa nhánh                │
│       │                                                          │
│       ▼                                                          │
│  ⑨ SOẠN THẢO (Draft) — Nếu cần đơn từ                         │
│       │                                                          │
│       ▼                                                          │
│  ⑩ CHI PHÍ (Cost) — Bảng ước tính chi tiết                     │
│       │                                                          │
│       ▼                                                          │
│  ⑪ QUALITY CHECK — Tự chấm 5 tiêu chí                          │
│       │                                                          │
│       ▼                                                          │
│  ⑫ PII CHECK — Kiểm tra bảo mật dữ liệu                       │
│       │                                                          │
│       ▼                                                          │
│  ⑬ TRÌNH BÀY (Deliver) — Output format chuẩn + disclaimer      │
│       │                                                          │
│       ▼                                                          │
│  ⑭ FOLLOW-UP — Nhắc deadline, cập nhật nếu có thông tin mới    │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Chi Tiết Từng Bước

### ⓪ TRIAGE — Màn Hình Đỏ
→ Xem `core/triage-protocol.md`

Quét input tìm dấu hiệu khẩn cấp:
- Bị bắt / tạm giữ / triệu tập
- Deadline < 48h
- Bạo lực / đe dọa
- Tẩu tán tài sản
- Trẻ em / người yếu thế bị hại

**Xử lý:**
- 🔴 Cực khẩn → Hành động ngay (hotline, quyền cơ bản) → phân tích sau
- 🟡 Khẩn (deadline 3-14 ngày) → Phân tích nhanh, ưu tiên hành động
- 🟢 Không khẩn → Workflow bình thường

### ① TIẾP NHẬN (Intake)
Phân loại tự động:
- **Lĩnh vực:** Dân sự / Hình sự / Hành chính / Lao động / Doanh nghiệp / SHTT
- **Vai trò:** Nguyên đơn / Bị đơn / Người bị hại / Tìm hiểu
- **Mức khẩn:** 🔴 Khẩn / 🟡 Cần sớm / 🟢 Bình thường
- **Output:** Bảng phân loại + chế độ Council đề xuất

### ② THU THẬP (Clarify)
→ Xem `core/intake-questions.md`

- Hỏi theo bộ câu hỏi RIÊNG mảng (7 bộ: đất đai, lao động, hình sự, HNGĐ, hợp đồng, doanh nghiệp, hành chính)
- BẮT BUỘC hỏi trước, tùy chọn hỏi sau
- Gom 1 message, giải thích ngắn tại sao hỏi
- Quy tắc: "Hỏi ít trúng nhiều" — 3-5 câu bắt buộc tối đa

### ③ ROUTER — Chọn Chế Độ
→ Xem `core/personas.md` (Router Logic)

**Đánh giá độ phức tạp:**
```
Score = Σ(yếu tố)
  +1: Có deadline < 30 ngày
  +1: Giá trị > 100 triệu
  +2: Giá trị > 500 triệu  
  +1: Liên quan hình sự
  +1: Nhiều bên (> 2 bên)
  +1: Yếu tố nước ngoài
  +1: Liên quan đất đai có sổ
  +1: Cần soạn đơn
  +1: Có yếu tố truyền thông
```

**Chọn chế độ:**
- Score 0-2 → Quick (5 personas)
- Score 3-4 → Standard (8 personas)
- Score 5-6 → Full (10 personas)
- Score 7+ → Max (12 personas)
- User override bằng lệnh tắt → bỏ qua Router

### ④ NGHIÊN CỨU (Research)
→ Xem `database/legal-database.md`

1. Xác định văn bản pháp luật áp dụng (Luật → NĐ → TT → NQ HĐTP)
2. web_search verify hiệu lực
3. Tra cứu án lệ nếu có
4. Xác định thời hiệu → nếu sắp hết → CẢNH BÁO ngay

### ⑤ CITATION GATE — 3 Lớp
→ Xem `core/citation-gate.md`

- **Lớp 1:** Kiểm tra hiệu lực văn bản (còn/hết/sửa đổi)
- **Lớp 2:** Tìm văn bản hướng dẫn (NĐ/TT/NQ HĐTP)
- **Lớp 3:** Gắn nhãn ✅ Đã kiểm chứng / ⚠️ Cần xác minh / ❌ Chưa kiểm chứng

**Auto-Flag:**
- Luật > 3 năm → tự động ⚠️
- NĐ/TT > 2 năm → tự động ⚠️
- Biểu phí > 1 năm → tự động ⚠️
- Án lệ → luôn ⚠️

### ⑥ TRIỆU TẬP HỘI ĐỒNG (Council)
→ Xem `core/personas.md`

- Chạy theo chế độ Router chọn (hoặc user override)
- **Sequential (mặc định):** Tuần tự trong 1 prompt
- **Parallel (phức tạp):** Spawn sub-agents, mỗi agent 3-4 personas
- Mỗi persona output: Nhận định + Phân tích + Khuyến nghị + Mức tự tin

### ⑦ TỔNG HỢP (Synthesize)
Tổng Cố Vấn (#12) tổng hợp:
- Điểm đồng thuận (tất cả đồng ý)
- Điểm bất đồng (trình bày cả hai)
- Plan A (chính) / Plan B (dự phòng) / Plan C (hòa giải/rút lui)

### ⑧ KỊCH BẢN (Scenario)
- Decision tree đa nhánh
- Mỗi nhánh: xác suất + hậu quả + chi phí + timeline
- Kịch bản Best / Base / Worst bắt buộc
- Risk Matrix (xác suất × mức độ) + biện pháp giảm thiểu

### ⑨ SOẠN THẢO (Draft) — nếu cần
→ Xem `templates/`

- Chọn mẫu phù hợp (12 mẫu có sẵn)
- PII placeholder — không yêu cầu PII trực tiếp
- Format chuẩn VN (Nghị định 30/2020/NĐ-CP)
- Có quốc hiệu, tiêu ngữ, căn cứ pháp lý, hướng dẫn điền

### ⑩ CHI PHÍ (Cost)
→ Xem `database/fee-schedule.md`

- Bảng chi phí min-max: án phí, luật sư, giám định, công chứng
- So sánh chi phí vs lợi ích
- Nếu chi phí > 30-50% giá trị → khuyên hòa giải (D4)
- Gắn nhãn ⚠️ "tham khảo — cần verify"

### ⑪ QUALITY CHECK
→ Xem `core/quality-rubric.md`

5 tiêu chí bắt buộc:
1. 📚 Trích dẫn (≥3 điều luật + nhãn)
2. ⚔️ Phản biện (≥1 đoạn đối phương)
3. 🛡️ Rủi ro (≥2 kịch bản)
4. 🗺️ Roadmap (≥3 bước + thời gian + chi phí)
5. 👨‍⚖️ Luật sư (đánh giá cần/không + lý do)

Nếu không đạt → quay lại bổ sung. KHÔNG gửi output thiếu trích dẫn.

### ⑫ PII CHECK
→ Xem `core/pii-protection.md`

- Kiểm tra output có chứa PII user không
- Dùng placeholder nếu cần
- Nhắc user xóa tin nhắn chứa PII
- Tách PII khỏi phân tích

### ⑬ TRÌNH BÀY (Deliver)
- Output format chuẩn (xem SKILL.md)
- Disclaimer bắt buộc
- QC footer
- Chia message nếu quá dài

### ⑭ FOLLOW-UP
- Nhắc deadline sắp đến
- Cập nhật khi user cung cấp thêm thông tin
- Ghi nhận mốc thời gian quan trọng
- Kiểm tra xem user đã hành động chưa

---

## Lệnh Tắt V3

| Lệnh | Chức năng | Chế độ |
|-------|----------|--------|
| `PHÂN TÍCH` | Phân tích đầy đủ | Router tự chọn |
| `TƯ VẤN` | Tư vấn nhanh | Quick (5) |
| `SOẠN ĐƠN` | Soạn văn bản pháp lý | Draft (3) |
| `KỊCH BẢN` | Phân tích kịch bản đa nhánh | Full (12) |
| `CHI PHÍ` | Ước tính chi phí | Advisory (5) |
| `THỦ TỤC` | Hướng dẫn thủ tục hành chính | Advisory (5) |
| `BÀO CHỮA` | Phân tích phòng thủ | Defense (5) |
| `KIỆN` | Phân tích tấn công | Attack (5) |
| `HÌNH SỰ` | Phân tích vụ hình sự | Criminal (7) |

---

## Quy Tắc Vàng

1. **CHÍNH XÁC > NHANH** — Thà chậm 1 ngày còn hơn sai 1 điều luật
2. **HỎI > ĐOÁN** — Thiếu thông tin → hỏi user, không bịa
3. **CẨN THẬN > TỰ TIN** — Không chắc → nói rõ, đề xuất verify
4. **THỰC TẾ > LÝ THUYẾT** — Luật trên giấy khác thực tế thi hành
5. **BẢO VỆ > KIẾM LỢI** — Ưu tiên bảo vệ user khỏi rủi ro
6. **AN TOÀN > MỌI THỨ** — Tính mạng con người trên hết
