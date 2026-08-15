# Đích Webcake / Pancake — đưa sale page lên nền tảng dựng

Reference này dùng khi user nói trang sẽ **đăng trên Webcake** (builder của Pancake) hoặc dùng **Pancake POS** để chốt đơn. Đọc ở Giai đoạn 6B (sau khi đã có nội dung + bản HTML duyệt ở GĐ 6). Mục tiêu: chuyển đúng *nội dung* đã viết sang một trang Webcake chạy được, nối form về POS, không để lại rác của template gốc.

Toàn bộ cơ chế ở đây bám công cụ Webcake sẵn có: bộ codec `.pke` (giải mã / đóng gói file trang, kèm template trống 18 section) và MCP `webcake-landing` (dựng page_source JSON).

---

## 1. Sự thật nền tảng — đọc trước khi hứa với khách

**Webcake KHÔNG nhập được file HTML thô.** Nút *"Nhập trang từ file"* của Webcake chỉ nhận `.pke` — định dạng cây "khối" (component) riêng của Webcake, không phải HTML/CSS.

→ "Đưa sale page lên Webcake" **không phải** bê nguyên file HTML thả vào. Thực chất là **lấy nội dung (chữ + ảnh) rồi dựng lại trong Webcake** bằng khối của nó. Hệ quả: giao diện chạy theo template Webcake, không giống y bản HTML ở GĐ 6. Cái mình giữ là *nội dung + cấu trúc thuyết phục*, không phải *pixel thiết kế*.

Vì vậy vai trò của bản HTML (GĐ 6) khi đích là Webcake: **bản duyệt nội dung + demo cảm giác visual cho khách xem**, không phải file import. Nói rõ điều này với user để không kỳ vọng sai.

---

## 2. Hai con đường lên Webcake — chọn theo tình huống

| Đường | Khi nào dùng | Làm gì |
|---|---|---|
| **A — MCP `webcake-landing`** | Dựng trang mới thẳng trong tài khoản Webcake của bạn (org đã kết nối) | Gọi MCP dựng `page_source` JSON theo design system đã khoá, publish lấy link. Theo đúng protocol intake của MCP (khoá palette + type scale + spacing trước khi dựng). |
| **B — skill `webcake-pke`** | Muốn khung sẵn nhanh, hoặc sửa hàng loạt chữ/ảnh một trang `.pke` có sẵn | Import `template-mau-salepage.pke` (18 section dựng sẵn) → điền ô `[...]` + thay ảnh ngay trong Webcake; hoặc `decode → sửa JSON từng section → encode`. |

Mặc định cho một sale page mới, tay: **đường B** (template trống có sẵn đủ 18 section thuyết phục, chỉ điền nội dung). Cần dựng tự động/tùy biến sâu trong tài khoản: **đường A**.

---

## 3. Map 16 bước → Section Webcake

Template trống của `webcake-pke` đã dựng sẵn các section dưới đây. Ánh xạ nội dung 16 bước (đã chốt ở GĐ 4–5) vào đúng section. Mở template ra để khớp tên chính xác — vài section đặt tên theo thứ tự khối, không theo nghĩa.

| Bước / khối (16-buoc) | Section Webcake | Ghi chú |
|---|---|---|
| Pre-headline / banner cảnh báo | `section_warning` | dòng khoanh đối tượng hoặc cảnh báo trên cùng |
| B1–B2 Headline + Sub + CTA đầu | `section_hero` | ảnh/tiêu đề lớn + nút + (đếm ngược nếu có) |
| Hình thức giao hàng / thông số nhanh | `section_logistics` | ship / link học / thời lượng |
| B3 Vấn đề (khoét đau) | `section_pain` | |
| B4 Uy tín cá nhân | `section_authority` | thành tựu THẬT, không bịa |
| B5 Câu chuyện before–after | `section_ba` | |
| B6 Lợi ích | `section_benefits` | pattern "Tính năng → Lợi ích → Ý nghĩa" |
| B7 Tạo cảm xúc / hình dung | `section_imagine` | |
| B8 Rõ ràng — gói gồm gì | `section_modules` | module/buổi/thành phần |
| B9 + B13 Tạo giá trị + neo giá | `section_value` | value stack → lộ giá |
| B11 Lý do mua | `section_reasons` | 3–5 lý do cô đọng |
| B14 Bonus | `section_promises` | quà kèm + giá quy đổi |
| B12 Khan hiếm/cấp bách | khối đếm ngược + `section_warning` | mốc THẬT (xem §5) |
| Guarantee | `section_guarantee` | risk reversal |
| B15 Testimonial | `section_15` | phản hồi có tên/ảnh/video, xếp theo nhóm |
| B10 Xử lý từ chối / FAQ | `section_faq` | |
| B16 CTA + chốt cuối | `section_form` + `section_16` + `section_sticky` | form chốt đơn + nút dính |
| P.S. cuối trang (nếu có) | khối text trước footer | nhắc lợi ích #1 + urgency lần cuối |

Section CTA lặp: chèn nút "Đặt mua / Đăng ký" ở cuối các khu quyết định (sau lợi ích, sau bằng chứng, sau neo giá) — trỏ event cuộn tới `section_form` hoặc mở popup. Tần suất CTA theo `copy-formulas-tri.md §5`.

---

## 4. Form chốt đơn — điểm mạnh Webcake (nối POS Pancake)

Form là điểm chốt, đặt ở `section_form` (thường `id="dangky"`), luôn có 1 CTA dẫn xuống đây.

- **Trường form theo loại đơn:**
  - **Vật phẩm/sách ship COD:** chọn sản phẩm/combo + số lượng → tổng tự tính · Họ tên · SĐT · Địa chỉ (Tỉnh/Huyện/Xã/số nhà) · phương thức (Chuyển khoản / VNPAY / COD).
  - **Khóa học / sự kiện:** Họ tên · SĐT/Zalo · email (nếu cần gửi link) · gói/hạng vé.
  - **Sản phẩm cần tư vấn trước (luận riêng):** Họ tên · SĐT · nhu cầu — không bắt nhập địa chỉ ở bước đầu.
- **Nối đích:** cấu hình form đổ về **POS Pancake / CRM** của đúng brand (đơn hàng, hoặc lead). Đây là điểm phải set trong Webcake, ghi rõ trong bàn giao.
- **Popup cảm ơn + redirect:** sau khi submit → mở `popups/Default_Popup` (xác nhận đơn) hoặc chuyển **trang cảm ơn CỦA MÌNH**. Tuyệt đối không để redirect về trang cảm ơn của chủ template cũ (xem §7).

---

## 5. Countdown / urgency đúng cách Webcake

- Dùng **khối đếm ngược thật** neo vào mốc ngày–giờ cụ thể (hết ưu đãi / đóng cổng). Có thể lặp 2–3 lần dọc trang.
- **Cấm** countdown reset về đầu mỗi lần refresh (đó là khan hiếm giả) — trái rule scarcity THẬT ở `copy-formulas-tri.md §6`. Khan hiếm giả bị lộ = phá sạch niềm tin.
- `section_warning` trên cùng + `section_sticky` CTA dính đáy: dùng cho urgency thật ("đóng cổng 23:59 ngày X"), không dùng để doạ rỗng.

Mọi con số khan hiếm (số suất, số bộ, deadline) phải là số THẬT do user cung cấp — thiếu thì hỏi, không chế.

---

## 6. Bất biến khi sửa `.pke` — không đổi kẻo vỡ

Nếu đi đường B (sửa JSON qua `webcake-pke`), giữ nguyên:

- **`id`** của mọi khối — sự kiện (nút, cuộn tới, mở popup) trỏ theo `id`. Đổi id = đứt sự kiện.
- **`events`** — chỉ đổi khi muốn đổi điều hướng (cuộn tới / mở popup).
- **`responsive.{mobile,desktop}.styles`** — giữ layout. Sửa ảnh/chữ phải đổi **cả 2 layout** (desktop và mobile) để đồng bộ; sửa 1 bên → lệch giao diện trên điện thoại.
- **Ảnh:** phải là URL công khai (tải thẳng vào Webcake, hoặc host Supabase/Cloudinary). **KHÔNG** nhồi `data:image;base64,...` — file phình, dễ vượt giới hạn khi import.

Được đổi thoải mái: `specials.text` (chữ) · `specials.field_placeholder` (ô form) · `specials.src` + CSS `background:url(...)` (ảnh — nhớ đổi cả 2 chỗ) · `manifest.json` phần `settings` (title/description/ảnh share) + `name`.

Sửa xong `encode` lại rồi `decode` kiểm ngược, **đếm số section phải khớp**.

---

## 7. Dọn tàn dư — bắt buộc nếu bê template người khác

Lấy bất kỳ template Webcake nào (kể cả "miễn phí") là **thừa kế luôn danh tính + công cụ theo dõi của chủ cũ**. Để nguyên = trang mình chạy cho người khác hưởng. Xoá/thay 5 thứ trước khi publish:

| # | Tàn dư | Vì sao nguy hiểm | Phải làm |
|---|---|---|---|
| 1 | Mã theo dõi (GTM / FB Pixel chủ cũ) ở `settings.gg_tag_manager_id` / `settings.fb_tracking_code` | Dữ liệu khách bắn về tài khoản chủ cũ; GTM còn cho họ chèn script tuỳ ý lên trang mình | Xoá, hoặc thay mã của brand mình |
| 2 | Link nút / footer trỏ về web chủ cũ | Khách bấm bị dẫn đi; lộ là trang sao chép | Thay link của mình, hoặc bỏ |
| 3 | Redirect sau form (trang cảm ơn / callback chủ cũ) | Khách đăng ký xong bị đẩy đi → mất khách | Thay trang cảm ơn của mình |
| 4 | Ảnh host trên kho chủ cũ | Họ xoá là bể ảnh | Tự host lại |
| 5 | Chữ sót (tên người, lời chứng, lý lịch chủ cũ) | Trang hiện nội dung sai ngành | Đọc & thay TỪNG khối |

Kiểm nhanh sau khi decode — phải ra **0 kết quả** trước khi publish:

```bash
grep -rinE "ten-mien-chu-cu|ten-thuong-hieu-chu-cu|GTM-|fb_tracking_code" thu-muc-decode/
```

---

## 8. Đầu ra khi đích là Webcake

Ngoài bản HTML duyệt nội dung (GĐ 6), giao thêm cho user:

1. **Bảng "khối copy → Section Webcake"** — mỗi khối 16 bước ghi rõ dán vào section nào (theo §3), để người dựng điền không lạc.
2. **Danh sách cấu hình cần set trong Webcake:** đích Form (POS Pancake/CRM của brand nào) · mốc Countdown · Popup/redirect cảm ơn · link các nút · ảnh cần host + URL.
3. **Placeholder còn trống** cần user điền: giá, ảnh thật, bonus, số TK, chính sách ship.

---

## 9. Checklist trước khi publish (Webcake)

- [ ] Nội dung 16 bước đã map đủ vào section, không sót khối trọng yếu (Hero H1 · Sub · Guarantee · CTA · Form)
- [ ] Form nối đúng POS/CRM của **đúng brand**; có popup/redirect cảm ơn của mình
- [ ] Countdown neo mốc THẬT, không reset khi refresh
- [ ] CTA lặp đủ theo độ dài trang, cùng một đích
- [ ] Ảnh đều là URL công khai (không base64), đồng bộ desktop ↔ mobile
- [ ] Đã dọn 5 tàn dư (§7) → grep ra 0 kết quả
- [ ] Còn ô `[...]` nào chưa điền không
- [ ] Đã qua **Compliance Check (GĐ 7.5)** trước khi publish

---

**Tham khảo chéo:**
- Cơ chế `.pke` + template trống + codec: skill `webcake-pke`
- Dựng page_source tự động trong tài khoản: MCP `webcake-landing`
- Khan hiếm/CTA đúng cách: `copy-formulas-tri.md` §5–6
- Map 16 bước → section trang nói chung: `cro-uiux-design.md`
- Lọc pháp lý trước khi publish: `compliance-check.md`
