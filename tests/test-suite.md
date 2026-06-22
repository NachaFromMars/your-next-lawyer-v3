# Test Suite V3 — 10 Case Mẫu

> Merge: 8 case Tiểu Tâm V2 + 2 case bổ sung = 10 case
> Cover: đơn giản → phức tạp, khẩn cấp → bình thường, 7 mảng pháp lý.

---

## Case 1: Hợp Đồng Vay Tiền Đơn Giản
**Input:** "Tôi cho bạn vay 50 triệu bằng giấy viết tay, 1 năm rồi không trả."
**Mảng:** Dân sự — Hợp đồng
**Council:** Quick (5)
**Triage:** 🟢
**Expected:**
- Trích dẫn: Điều 463-471 BLDS 2015 (HĐ vay), Điều 429 (thời hiệu 3 năm)
- Phản biện: Bên vay phủ nhận, nói đã trả, giấy tay giả
- Rủi ro: Giấy viết tay không công chứng → chứng cứ yếu hơn
- Roadmap: Thương lượng → Hòa giải → Khởi kiện TAND huyện
- Luật sư: Không cần nếu giấy tay rõ ràng
**QC min:** 5/5

## Case 2: Đất Đai Phức Tạp (Thừa kế + Sổ đỏ)
**Input:** "Ba tôi mất, để lại miếng đất có sổ đỏ. Anh trai tự ý sang tên rồi bán."
**Mảng:** Dân sự — Thừa kế + Đất đai
**Council:** Full (12)
**Triage:** 🟡 (nguy cơ tẩu tán)
**Expected:**
- Citation Gate: Verify Luật Đất đai 2024 (MỚI!) + BLDS 2015 thừa kế
- BPKCTT: Cần ngăn chặn giao dịch tiếp [Điều 111 BLTTDS]
- Phản biện: Anh trai viện dẫn di chúc/tặng cho
- Rủi ro: Bên thứ ba ngay tình → rất khó đòi
- Luật sư: CẦN — vụ phức tạp, nhiều bên
**QC min:** 5/5

## Case 3: Dân Sự/Hình Sự — Đặt Cọc 500tr Bên Bán Biến Mất
**Input:** "Đặt cọc 500 triệu mua nhà, bên bán biến mất, điện thoại tắt."
**Mảng:** Dân sự + Có thể Hình sự
**Council:** Full (12) hoặc Criminal (7)
**Triage:** 🟡
**Expected:**
- Ranh giới dân sự - hình sự [Điều 174 vs Điều 418 BLDS]
- Kịch bản song song: Tố giác HS + Khởi kiện DS
- BPKCTT: Phong tỏa tài sản
- Chi phí: Án phí 5% × 500tr = 25tr
**QC min:** 5/5

## Case 4: Lao Động — Sa Thải Trái Luật
**Input:** "Làm 3 năm, hôm nay sếp nói nghỉ việc, không cho lý do."
**Mảng:** Lao động
**Council:** Attack (5)
**Triage:** 🟢
**Expected:**
- Điều 36-41 BLLĐ 2019, sa thải không QĐ = trái luật
- Bồi thường ≥ 2 tháng lương + trợ cấp
- Thời hiệu: 1 năm [Điều 190 BLLĐ 2019]
- Roadmap: Yêu cầu QĐ → Sở LĐ-TB-XH → Kiện
**QC min:** 4/5

## Case 5: Khẩn Cấp — Bị Bắt Giam 🔴
**Input:** "Con trai tôi bị công an bắt hôm qua, không biết ở đâu!"
**Mảng:** Hình sự — KHẨN CẤP
**Council:** Triage → Criminal (7)
**Triage:** 🔴
**Expected:**
- 🔴 TRIAGE kích hoạt ngay
- Hành động ngay: Gọi 1900.6169 + Đến CA nơi bắt
- Quyền: LS từ khi tạm giữ [Điều 74 BLTTHS]
- Tạm giữ: 3 ngày (gia hạn tối đa 9 ngày) [Điều 117]
**QC min:** 3/5

## Case 6: Edge Case — Gần Hết Thời Hiệu
**Input:** "Tôi bị lừa 200 triệu, xảy ra tháng 8/2023."
**Mảng:** Dân sự — Thời hiệu sắp hết
**Council:** Quick (5)
**Triage:** 🟡
**Expected:**
- Thời hiệu 3 năm → hết 08/2026 → CÒN ~6 THÁNG
- Cảnh báo rõ ràng + Roadmap ưu tiên tốc độ
- Citation Gate: Verify Điều 429 BLDS + NQ hướng dẫn
**QC min:** 4/5

## Case 7: Edge Case — Mua Hàng Online Bị Lừa
**Input:** "Mua hàng online bị lừa, người bán ở tỉnh khác."
**Mảng:** Dân sự + Có thể Hình sự
**Council:** Quick (5)
**Triage:** 🟢
**Expected:**
- Thẩm quyền: Tòa nơi bị đơn cư trú [Điều 39-40 BLTTDS]
- < 2 triệu → chỉ dân sự; ≥ 2 triệu → có thể tố giác HS
- Thực tế: Lừa đảo online rất khó đòi → cân nhắc chi phí vs giá trị
**QC min:** 4/5

## Case 8: Soạn Đơn — Ly Hôn Thuận Tình
**Input:** "Soạn đơn ly hôn thuận tình cho tôi."
**Mảng:** HNGĐ — Soạn thảo
**Council:** Draft (3)
**Triage:** 🟢
**Expected:**
- Intake: Hỏi tối thiểu (có con? tài sản? cùng thỏa thuận?)
- PII: Dùng placeholder
- Đơn chuẩn format VN
- Checklist hồ sơ cần nộp
**QC min:** 3/5

## Case 9: Đất Đai Chưa Có Sổ Đỏ (Bổ sung)
**Input:** "Tranh chấp đất đai với hàng xóm, đất chưa có sổ đỏ."
**Mảng:** Đất đai + Hành chính
**Council:** Standard (8)
**Triage:** 🟢
**Expected:**
- Chưa có GCN → UBND huyện/tỉnh giải quyết (không phải tòa)
- Hòa giải UBND xã BẮT BUỘC trước
- Cần giấy tờ: hợp đồng, biên nhận, bản đồ địa chính
- Citation Gate: Verify Luật Đất đai 2024 (thay 2013)
**QC min:** 5/5

## Case 10: Công Ty Nợ BHXH (Bổ sung)
**Input:** "Công ty nợ BHXH 6 tháng, tôi sắp nghỉ việc."
**Mảng:** Lao động + Hình sự
**Council:** Criminal (7)
**Triage:** 🟡
**Expected:**
- Nợ BHXH ≥ 6 tháng → có thể truy cứu TNHS [Điều 216 BLHS]
- Quyền NLĐ: Yêu cầu đóng bù, khiếu nại Sở LĐ-TB-XH
- Liên hệ Công đoàn (có quyền kiện thay NLĐ)
- Roadmap: Khiếu nại → Thanh tra → Tố giác HS
**QC min:** 5/5

---

## Bảng Tổng Hợp

| Case | Mảng | Council | Triage | QC min |
|------|------|---------|:------:|:------:|
| 1 | HĐ Dân sự | Quick (5) | 🟢 | 5/5 |
| 2 | Đất đai + Thừa kế | Full (12) | 🟡 | 5/5 |
| 3 | Dân sự + Hình sự | Full (12) | 🟡 | 5/5 |
| 4 | Lao động | Attack (5) | 🟢 | 4/5 |
| 5 | Hình sự KHẨN | Triage→Criminal | 🔴 | 3/5 |
| 6 | Thời hiệu edge | Quick (5) | 🟡 | 4/5 |
| 7 | Online + thẩm quyền | Quick (5) | 🟢 | 4/5 |
| 8 | Soạn đơn HNGĐ | Draft (3) | 🟢 | 3/5 |
| 9 | Đất đai chưa GCN | Standard (8) | 🟢 | 5/5 |
| 10 | Lao động + HS | Criminal (7) | 🟡 | 5/5 |
