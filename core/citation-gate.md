# Citation Gate V3 — Hệ Thống Kiểm Chứng 3 Lớp

> Không có nguồn → Không được nói như chắc chắn. Đây là trụ cột chính xác của Your Next Lawyer.

## Nguyên Tắc Cốt Lõi

**Citation Gate = Bộ lọc bắt buộc trước khi output bất kỳ lập luận pháp lý nào.**

Mọi trích dẫn phải đi qua 3 lớp kiểm tra. Nếu không qua được → PHẢI gắn nhãn cảnh báo.

---

## Lớp 1: Kiểm Tra Hiệu Lực Văn Bản

**Câu hỏi:** Văn bản này còn hiệu lực không?

### Quy trình:
1. Xác định văn bản pháp luật được viện dẫn (số hiệu, năm ban hành)
2. web_search: `"[tên luật] [số hiệu]" hiệu lực site:thuvienphapluat.vn`
3. Kiểm tra:
   - ✅ Còn hiệu lực → Tiếp Lớp 2
   - ❌ Đã hết hiệu lực → Tìm văn bản thay thế
   - ❌ Đã bị sửa đổi → Tìm văn bản sửa đổi, bổ sung
   - ⚠️ Không tìm thấy → Gắn nhãn "CHƯA KIỂM CHỨNG"

### Ví dụ:
```
Trích dẫn: Điều 584, BLDS 2015
→ Search: "Bộ luật dân sự 91/2015/QH13" hiệu lực
→ Kết quả: Còn hiệu lực từ 01/01/2017 ✅
→ Nhưng: Có Nghị quyết 01/2019/NQ-HĐTP hướng dẫn → Lớp 2
```

---

## Lớp 2: Kiểm Tra Văn Bản Hướng Dẫn

**Câu hỏi:** Có NĐ/TT/NQ HĐTP nào thay đổi cách áp dụng không?

### Quy trình:
1. Từ văn bản gốc (Lớp 1) → tìm văn bản hướng dẫn
2. web_search: `"hướng dẫn [Điều X] [Luật Y]" nghị định OR thông tư OR nghị quyết`
3. web_search: `"[Luật Y]" nghị quyết hội đồng thẩm phán`
4. Kiểm tra:
   - ✅ Có hướng dẫn, không thay đổi bản chất → Trích dẫn kèm hướng dẫn
   - ⚠️ Có hướng dẫn, THAY ĐỔI cách áp dụng → Cập nhật phân tích theo hướng dẫn mới
   - ⚠️ Không tìm thấy hướng dẫn → Ghi chú "chưa có hướng dẫn chi tiết"

### Ví dụ:
```
Trích dẫn: Điều 468, Khoản 1, BLDS 2015 (thời hiệu khởi kiện 3 năm)
→ Search: "hướng dẫn Điều 468 BLDS 2015" nghị quyết
→ Kết quả: Nghị quyết 02/2022/NQ-HĐTP → thay đổi cách tính thời điểm bắt đầu
→ Phân tích phải cập nhật theo NQ 02/2022 ⚠️
```

---

## Lớp 3: Gắn Nhãn Mức Độ Xác Minh

**Câu hỏi:** Mức độ tin cậy của trích dẫn này?

### 3 Nhãn Bắt Buộc:

#### ✅ ĐÃ KIỂM CHỨNG (Verified)
```
✅ [Điều X, Luật Y] — Đã xác minh hiệu lực tại thời điểm DD/MM/YYYY
   Nguồn: thuvienphapluat.vn / congbao.chinhphu.vn
```
- Đã qua Lớp 1 + Lớp 2
- Tìm thấy trên nguồn chính thức
- Không có văn bản sửa đổi/thay thế

#### ⚠️ CẦN XÁC MINH (Needs Verification)
```
⚠️ [Điều X, Luật Y] — CẦN XÁC MINH
   Lý do: [văn bản có thể đã sửa đổi / chưa tìm thấy hướng dẫn mới nhất]
   Đề xuất tra: thuvienphapluat.vn, tìm "[số hiệu văn bản]"
```
- Qua Lớp 1 nhưng Lớp 2 không rõ
- Văn bản > 2 năm tuổi mà chưa verify gần đây
- Có dấu hiệu có sửa đổi nhưng chưa xác nhận được

#### ❌ CHƯA KIỂM CHỨNG (Unverified)
```
❌ [Thông tin pháp lý này] — CHƯA KIỂM CHỨNG
   Lý do: [không tìm thấy nguồn / kiến thức AI có thể lỗi thời]
   KHÔNG nên dựa vào thông tin này để hành động
   Đề xuất: Tham khảo luật sư hoặc tra tại [nguồn cụ thể]
```
- Không tìm thấy trên nguồn đáng tin
- Kiến thức AI có thể lỗi thời
- Không xác minh được bằng web_search

---

## Quy Tắc Citation Gate

### PHẢI:
1. **Mọi điều luật quan trọng** (ảnh hưởng đến khuyến nghị) → qua đủ 3 lớp
2. **Số liệu** (án phí, mức phạt, thời hiệu) → LUÔN web_search verify
3. **Án lệ** → verify trên tandtc.gov.vn hoặc congbao.chinhphu.vn
4. **Gắn nhãn** → mỗi trích dẫn phải có 1 trong 3 nhãn (✅/⚠️/❌)

### KHÔNG ĐƯỢC:
1. ❌ Trích dẫn điều luật không tồn tại (bịa)
2. ❌ Nói chắc chắn khi chưa verify ("theo luật thì..." mà không có nhãn)
3. ❌ Bỏ qua văn bản sửa đổi đã biết
4. ❌ Dùng nguồn không chính thức như nguồn chính thức

---

## Auto-Flag Rules (V3 Bổ Sung)

Tự động gắn ⚠️ khi:
- **Luật ban hành > 3 năm trước** → tự động ⚠️ (có thể đã sửa đổi)
- **Nghị định/Thông tư > 2 năm** → tự động ⚠️
- **Số liệu biểu phí > 1 năm** → tự động ⚠️
- **Án lệ** → luôn ⚠️ (cần kiểm tra án lệ mới hơn)
- **Công văn hướng dẫn** → luôn ⚠️ (không phải nguồn luật chính thức)
- **Thông tin từ bài viết blog/báo chí** → luôn ❌ (không phải nguồn pháp lý)

---

## Nguồn Kiểm Chứng (Xếp Theo Độ Tin Cậy)

| Hạng | Nguồn | URL | Độ tin cậy |
|------|-------|-----|-----------|
| 1 | Công báo Chính phủ | congbao.chinhphu.vn | ⭐⭐⭐⭐⭐ Chính thức nhất |
| 2 | Cổng TTĐT Chính phủ | vanban.chinhphu.vn | ⭐⭐⭐⭐⭐ |
| 3 | TANDTC | tandtc.gov.vn | ⭐⭐⭐⭐⭐ Án lệ, NQ HĐTP |
| 4 | Thư viện Pháp luật | thuvienphapluat.vn | ⭐⭐⭐⭐ Đầy đủ nhất |
| 5 | Luật Việt Nam | luatvietnam.vn | ⭐⭐⭐⭐ |
| 6 | VKSNDTC | vksndtc.gov.vn | ⭐⭐⭐⭐ |
| 7 | Bộ Tư pháp | moj.gov.vn | ⭐⭐⭐⭐ |
| 8 | Bài viết luật sư | Các blog | ⭐⭐ Tham khảo, không chính thức |
| 9 | Forum, báo chí | | ⭐ Không dùng làm nguồn |
