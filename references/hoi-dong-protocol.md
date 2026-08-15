# PROTOCOL HỘI ĐỒNG — bắt buộc tại GATE 2

> **Đây là LUẬT của skill, không phải hướng dẫn tham khảo.** Nếu agent bỏ qua protocol này ở GATE 2 → **gate CHƯA pass**, không được viết nội dung chi tiết ở Giai đoạn 5. Không có ngoại lệ cho "task nhẹ" hay "trang demo" — vì test skill mà bỏ gate = không test skill.

Protocol này tồn tại vì một lý do CỤ THỂ: rule "sinh 3 phương án → hội đồng chọn 1" ở SKILL.md dạng mô tả rất dễ bị agent skim ("hiểu rồi") rồi viết đi 1 phương án cho nhanh. Đây là failure mode đã xảy ra thực tế (case demo vòng tay phong thủy 2026-07-02) — chính USP lớn nhất của skill bị vô hiệu hóa.

Protocol yêu cầu agent **IN RA biên bản** — vì cái gì in ra là cái đã thực sự làm; cái giữ trong đầu là cái đã skim.

---

## 1. Khối TRỌNG YẾU — bắt buộc chạy hội đồng

Với mỗi trang sale page, agent BẮT BUỘC chạy hội đồng cho **tối thiểu 5 khối** dưới đây:

| # | Khối | Lý do phải chạy hội đồng |
|---|---|---|
| K1 | **Hero H1 (headline chính)** | Chiếm 80% thành bại trang. Sai = mọi thứ dưới vô nghĩa. |
| K2 | **Sub-headline** | Đỡ cho H1. Khách đọc 3 giây thì gồm H1 + Sub, không có phần khác. |
| K3 | **Big Idea → Opening story hook** | Câu chuyển từ vấn đề sang giải pháp — trục cảm xúc của trang. |
| K4 | **Guarantee wording** | Risk reversal là vũ khí gỡ phản đối mạnh nhất; sai câu = mất khách. |
| K5 | **CTA chính (nút mua/đăng ký)** | Điểm khách quyết định. Mỗi chữ tính. |

**Khuyến khích thêm** (tuỳ độ đắt của trang):
- K6: **Objection lớn nhất** — phản đối #1 của chân dung khách (thường là "đắt vậy?" hoặc "có hiệu quả không?")
- K7: **Offer positioning** — cách khung gói (nhấn giá / nhấn value stack / nhấn khan hiếm)
- K8: **PS cuối trang** — câu chốt cuối, đọc bởi ~30% khách skim

**Không cần chạy hội đồng cho:** FAQ, trust bar, disclaimer, footer, các bullet lợi ích lẻ (áp dụng pattern đã chọn từ đầu).

---

## 2. FORMAT bắt buộc — bảng chấm 5 vai × 3 phương án

Với MỖI khối trọng yếu, agent PHẢI in ra bảng dưới đây trong output. Không có bảng = gate chưa pass.

### Template bảng chấm

```markdown
### GATE 2 · Khối [Kn] — [TÊN KHỐI]

**Big Idea đã chốt:** [1 câu — copy từ giai đoạn 3]
**Chân dung khách:** [1 dòng cụ thể]
**Awareness stage:** [cold / warm / hot]

**3 phương án:**

**P1 — [góc tiếp cận, vd "theo khát vọng"]**
> [Câu / đoạn]

**P2 — [góc tiếp cận, vd "theo nỗi đau"]**
> [Câu / đoạn]

**P3 — [góc tiếp cận, vd "theo con số cụ thể"]**
> [Câu / đoạn]

**Hội đồng chấm** (thang 1–5, 5 là cao nhất):

| Tiêu chí | Vai chấm | P1 | P2 | P3 |
|---|---|---|---|---|
| Sức hút · rõ ràng | Copywriter | ? | ? | ? |
| Thuyết phục · lời hứa cụ thể | CRO Expert | ? | ? | ? |
| Khách có tin không · có gật đầu không | Khách khó tính (chân dung mục tiêu) | ? | ? | ? |
| Bám Big Idea xuyên suốt | Giám đốc sáng tạo | ? | ? | ? |
| Không bịa · YMYL an toàn · đạo đức | Người phản biện chất lượng | ? | ? | ? |
| **TỔNG** | | ? | ? | ? |

**Chốt:** [P? — hoặc GHÉP P? + P?]
**Lý do chọn (2–3 câu):** [Giải thích rõ, đặc biệt nếu điểm không cao nhất]
**Câu ghép cuối cùng (nếu ghép):**
> [Câu chốt cho khối này]
```

---

## 3. Quy tắc chấm — 5 vai

Mỗi vai chấm theo góc nhìn của mình, chấm THÀNH THẬT (không thiên vị phương án nào), thang 1–5 với neo cụ thể:

### Vai 1 — COPYWRITER
- **1:** câu rối, khó đọc, không nhớ nổi sau 3 giây
- **3:** đọc được, hiểu được, nhưng thiếu điểm nhấn
- **5:** đọc xong nhớ ngay, có 1 điểm nhấn (câu hỏi / hình ảnh / contrast) khiến muốn đọc tiếp

Chấm điểm: **sức hút + rõ ràng + nhịp câu**

### Vai 2 — CRO EXPERT
- **1:** không hứa gì cụ thể, câu chung chung ("chất lượng cao")
- **3:** có lời hứa nhưng mơ hồ ("tăng doanh số")
- **5:** lời hứa cụ thể ĐO ĐƯỢC (có số, có thời gian, có kết quả rõ)

Chấm điểm: **độ thuyết phục + lời hứa cụ thể + trigger hành động**

### Vai 3 — KHÁCH KHÓ TÍNH (chân dung mục tiêu, đóng đúng vai)
- **1:** đọc xong nghĩ "PR bịa", "sến", "lại quảng cáo" → lướt qua
- **3:** không bịa nhưng không chạm — "OK, bình thường"
- **5:** đọc xong nghĩ "Đúng là mình" hoặc "Nghe hợp lý, để đọc thêm"

**Quan trọng:** vai này phải đóng thật ĐÚNG chân dung — chị chủ shop 40t khác anh founder tech 30t. Điểm này thường lộ ra khi phương án đẹp về câu chữ nhưng khách thật không tin.

Chấm điểm: **niềm tin + đồng cảm + không cảnh giác**

### Vai 4 — GIÁM ĐỐC SÁNG TẠO
- **1:** không liên quan Big Idea, tách rời khỏi chiến lược đã chốt
- **3:** không phá Big Idea nhưng cũng không củng cố
- **5:** củng cố Big Idea, khớp với awareness stage của khách, hợp giọng brand

Chấm điểm: **bám Big Idea + khớp brand voice + xuyên suốt trang**

### Vai 5 — NGƯỜI PHẢN BIỆN CHẤT LƯỢNG (rule enforcer)
- **1:** BỊA số / testimonial / thành tựu (phá rule #1) HOẶC cam kết mạnh YMYL không có bằng chứng ("chắc chắn giàu")
- **3:** an toàn nhưng có chỗ mơ hồ có thể bị hiểu sai
- **5:** không bịa, YMYL an toàn, mọi tuyên bố truy được về dữ liệu thật, có disclaimer khi cần

**Vai này có quyền PHỦ QUYẾT** — nếu chấm 1 hoặc 2, phương án đó KHÔNG được chọn dù các vai khác cho điểm cao. Lý do: rule #1 anh Trí (KHÔNG BỊA) và YMYL là ranh giới đạo đức không thoả hiệp.

Chấm điểm: **không bịa + YMYL an toàn + đạo đức + truy nguồn được**

---

## 4. Nguyên tắc chọn phương án

Sau khi chấm, chọn theo thứ tự ưu tiên:

1. **Phương án có tổng cao nhất VÀ không bị Phản biện phủ quyết** (điểm vai 5 ≥ 3) → CHỌN THẲNG
2. **Phương án cao thứ 2 (không bị phủ quyết)** nếu phương án #1 bị vai 5 chấm 1–2 → CHỌN
3. **GHÉP 2 phương án** khi mỗi phương án có 1 điểm mạnh khác nhau (vd: P2 mạnh cảm xúc, P3 mạnh cụ thể → ghép nỗi đau P2 với chi tiết P3). PHẢI viết ra câu ghép cuối cùng, không được nói "kết hợp mấy ý".

**Cấm:**
- Chọn phương án bị vai 5 chấm 1 (bịa / vi phạm YMYL) dù các vai khác 5 hết
- Chọn phương án chỉ vì "hay nhất về câu chữ" khi khách thật không tin
- Ghép mơ hồ ("lấy tinh thần của cả 3") — phải ra CÂU CỤ THỂ

---

## 5. Điều kiện GATE 2 PASS

Gate 2 chỉ được coi là PASS khi:

- [ ] Đã in bảng chấm cho **tối thiểu 5 khối trọng yếu** (K1–K5)
- [ ] Mỗi bảng có đủ 3 phương án + đủ 5 vai chấm + tổng điểm
- [ ] Mỗi khối có **câu chốt cuối cùng** (không phải "sẽ chọn sau")
- [ ] Không phương án nào bị vai 5 chấm 1 mà vẫn được chọn
- [ ] User đã DUYỆT dàn ý tổng (16 bước, mỗi bước 1–2 dòng chốt) — nhắc lại đây là gate cuối gate 2

Nếu bất kỳ điều nào trên đây không đạt → **gate 2 CHƯA pass**, quay lại làm cho đủ. Không viết Giai đoạn 5 khi gate 2 chưa pass.

---

## 6. Rút gọn hợp lý khi task nhỏ

Trang < 500 từ / low-ticket < 500K / audience cực warm: có thể rút xuống **3 khối trọng yếu** (K1 Hero H1 + K4 Guarantee + K5 CTA chính). Nhưng KHÔNG được rút xuống 0 khối = không chạy hội đồng gì.

Trang > 2500 từ / high-ticket > 20 triệu / audience cold: chạy đủ **8 khối** (K1–K8), không rút.

Ranh giới:
- < 500K + cực warm → **3 khối**
- 500K–5 triệu + warm → **5 khối** (mặc định)
- > 5 triệu / cold / stakes cao → **8 khối**

---

## 7. Nếu có Agent tool (subagent) — chạy hội đồng THẬT

Nếu môi trường có Agent tool, khuyến khích spawn 5 subagent song song (mỗi subagent đóng 1 vai + chấm độc lập). Điểm mạnh: chấm không bị thiên vị bởi 1 head duy nhất; các vai không ảnh hưởng lẫn nhau.

Prompt mẫu cho subagent chấm:
> Anh là [VAI] trong hội đồng chấm phương án cho sale page. Big Idea: [X]. Chân dung: [Y]. Dưới đây là 3 phương án [tên khối]. Chấm mỗi phương án theo thang 1–5 dựa trên tiêu chí của vai anh: [tiêu chí]. Trả về JSON: `{p1: {score, reason}, p2: {score, reason}, p3: {score, reason}}`. Không thoả hiệp — nếu phương án nào bịa hoặc yếu, chấm 1.

Sau đó chính agent chủ tổng hợp bảng + chọn phương án. Đây là "adversarial verify" pattern.

Nếu không có Agent tool: tự lập luận đa vai, ghi rõ lý do chấm.

---

## 8. Ví dụ mẫu (case Hero H1 vòng tay phong thủy)

Đã có trong lịch sử phiên 2026-07-02 — ba phương án Hero H1 cho vòng tay phong thủy (theo khát vọng / theo nỗi đau / theo con số), 5 vai chấm, ra kết quả: P2 (nỗi đau) thắng thực chất, P3 (con số) bị vai 5 phủ quyết vì bịa số "590 chị em", câu chốt là ghép P2 + hook cụ thể của P3. Xem file skill history hoặc yêu cầu agent trình lại nếu cần.

---

**Tham khảo chéo:**
- Khung 16 bước: `16-buoc-khung-noi-dung.md`
- Chiến lược Big Idea + USP: `nghien-cuu-va-chien-luoc.md`
- Copy formulas cho từng khối: `copy-formulas-tri.md`
- Visual + palette: `visual-dct-brand.md`
