# Visual design — brand Dương Cao Trí

Hướng dẫn màu, typography, layout cụ thể để dựng HTML sale page **đúng brand Trí**. Đọc ở Giai đoạn 6 (dựng HTML) trước khi mở template. Mọi giá trị dưới đây đã được cấy sẵn vào `assets/sale-page-template.html` — file này giải thích **VÌ SAO** và **KHI NÀO** thay đổi.

**Nguyên tắc gốc:** rõ ràng > bóng bẩy. Trang sale phải đọc được trên điện thoại rẻ tiền, mạng chậm, dưới nắng chói. Visual phục vụ chuyển đổi, không phục vụ giải thưởng thiết kế.

---

## 1. Bảng màu — 3 palette theo bối cảnh

Trí có **1 palette canonical** (dùng mặc định) + **2 variant** dùng khi bối cảnh đòi hỏi. KHÔNG tự chế palette mới cho từng trang.

### Palette A — CANONICAL (mặc định, dùng ~80% trường hợp)
Trầm - tin cậy - authority. Phù hợp: khoá học chuyên môn, tư vấn founder, sản phẩm trung-cao cấp.

| Vai trò | HEX | Khi dùng |
|---|---|---|
| **Brand** | `#1a2b4a` | Xanh đen chủ đạo — H1/H2/H3, offer box background, footer |
| **Accent** | `#e8623d` | Cam đất NHẤN — CTA button, icon check, highlight từ khoá |
| **Accent-dark** | `#c94e2c` | Hover state, gạch chéo giá gốc |
| **BG** | `#ffffff` | Nền chính |
| **BG-soft** | `#f6f7f9` | Nền section xen kẽ |
| **Ink** | `#1c2126` | Chữ chính |
| **Ink-soft** | `#55606b` | Chữ phụ, caption, sub-headline |
| **Line** | `#e6e9ee` | Viền card, divider |
| **Scarcity-bg** | `#fff3ec` | Nền badge khan hiếm (kèm border `#f2c3ac`) |

Combo an toàn:
- Headline: `#1a2b4a` trên `#ffffff`
- CTA: chữ trắng trên nền `#e8623d`, shadow cam
- Testimonial card: `#ffffff` viền `#e6e9ee` trên nền `#f6f7f9`
- Offer box: chữ trắng trên nền `#1a2b4a`

### Palette B — IMPULSE / URGENCY (đỏ-vàng, dùng ~15%)
Nóng - cấp bách - impulse. Phù hợp: khoá học low-ticket có deadline, sự kiện đóng cổng, flash sale, offer 24h.

| Vai trò | HEX | Khi dùng |
|---|---|---|
| **BG gradient** | `#160202` → `#3a0202` → `#7a0404` → `#c20808` | Nền tối đỏ, radial gradient |
| **Gold** | `#FFE100` | Headline, số nổi bật, viền CTA |
| **Gold-soft** | `#FFF3A8` | Highlight text |
| **Cream** | `#F7E9C8` | Body text (đủ contrast trên nền tối) |
| **Muted** | `#e9c9a8` | Caption, disclaimer |
| **Panel** | `rgba(0,0,0,.26)` | Card background (semi-transparent) |

Ghi chú: chỉ dùng khi urgency là trục chính; không dùng cho sản phẩm authority/trust dài hạn.

### Palette C — PREMIUM / AUTHORITY (đen-đồng, dùng ~5%)
Cao cấp - độc quyền - có kiểm soát. Phù hợp: mastermind, coaching 1-1, sản phẩm cao cấp > 20 triệu.

| Vai trò | HEX | Khi dùng |
|---|---|---|
| **BG** | `#0d0d0d` | Nền đen |
| **Ink** | `#f5f5f5` | Chữ chính |
| **Ink-soft** | `#a3a3a3` | Chữ phụ |
| **Bronze** | `#c9a961` | Accent đồng — H1, CTA border, divider |
| **Bronze-dark** | `#8a6d3b` | Hover, active |
| **Line** | `#2a2a2a` | Viền card |

Combo an toàn: text trắng ngà `#f5f5f5` trên nền đen; CTA viền đồng `#c9a961` trên nền đen; H1 màu đồng.

### Quy tắc chọn palette
Hỏi thứ tự:
1. **Sản phẩm nào?** Low-ticket impulse (< 1 triệu, offer ngắn) → **B**. Mastermind/coaching cao cấp → **C**. Còn lại → **A**.
2. **Traffic từ đâu?** Ads impulse Facebook → **B** OK. Traffic từ blog/email/nội dung dài của Trí → **A**.
3. **Awareness stage của khách?** Cold + cần cảm xúc mạnh → **B**. Warm + đã biết Trí → **A** hoặc **C**.

---

## 2. Typography

### Font stack
```css
--font: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
```

**Tại sao system font?** Tải nhanh (0 request), quen mắt người Việt (Windows/iOS/Android đã sẵn), an toàn nhất. Chỉ đổi khi có brand guide riêng.

**Variant** — nếu cần tính cách rõ hơn:
- **Palette A/C:** thêm `"Be Vietnam Pro"` (Google Fonts) làm heading — sạch, hiện đại, hỗ trợ tiếng Việt tốt
- **Palette B:** `"Oswald"` (compressed uppercase heading) + `"Roboto"` (body) — kiểu poster impulse

### Thang cỡ chữ (mobile-first)

| Element | Mobile (<720px) | Desktop (≥720px) | Weight | Line-height |
|---|---|---|---|---|
| H1 (hero) | 30px | 46px | 800 | 1.15–1.2 |
| H2 (section) | 24px | 34px | 800 | 1.2–1.3 |
| H3 (sub) | 20px | 20px | 700 | 1.3 |
| Lead paragraph | 18px | 21px | 400 | 1.5 |
| Body | 17px | 18px | 400 | 1.65 |
| CTA button | 18–19px | 19–22px | 800 | 1.2 |
| Eyebrow | 13px | 13px | 700 UPPERCASE | letter-spacing .12em |
| Caption | 14px | 14px | 400 | 1.4 |

**Tại sao body 17–18px?** Nhỏ hơn 16px = mỏi mắt trên mobile. Lớn hơn 20px = trẻ con / thiếu chuyên nghiệp cho audience founder.

### Quy tắc
- **Mobile-first**: cấu hình mobile trước, dùng `@media (min-width: 720px)` để scale lên
- **Line-height body 1.5–1.65** — thoáng, dễ quét mắt
- **Không dùng font-weight 300** (quá mảnh, mất ấn tượng trên headline)
- **IN HOA** chỉ cho: CTA button + eyebrow + urgency banner. Cấm in hoa cả câu dài (khó đọc)
- **Letter-spacing âm nhẹ** (`-0.01em`) cho headline lớn — trông chuyên nghiệp hơn

---

## 3. Layout & spacing

### Container
```css
--maxw: 860px;  /* độ rộng đọc tối ưu */
```

**Tại sao 860px?** Nghiên cứu typography: 60–75 ký tự/dòng là tối ưu. 860px cho ~70 ký tự với body 18px. Rộng hơn → mắt phải nhảy dòng khó. Hẹp hơn → nhiều lần enter, đọc mệt.

Ngoại lệ: section grid 2 cột (before/after, hero image + text) có thể mở rộng lên 1000–1100px.

### Section padding
```css
section { padding: 56px 0; }              /* mobile */
@media (min-width:720px) { section { padding: 80px 0; } }
```

Mỗi section nghỉ ~2 lần chiều cao trung bình — mắt được thở, phân cấp rõ.

### Grid gap
- Card grid (testimonial, benefit): `gap: 16–18px`
- Bullets list: `gap: 14px`
- Form field: `gap: 6–8px`

### Border radius
```css
--radius: 14px;
```
Tròn vừa phải — không sắc lạnh (radius 0–4px trông cũ), không bo tròn quá (radius 20+ trẻ con).

### Bóng đổ (shadow)
- CTA nổi: `box-shadow: 0 8px 22px rgba(232,98,61,.32)` (dùng accent color, alpha 30%)
- Card thường: **KHÔNG shadow** — dùng border `1px solid var(--line)` cho gọn
- Sticky mobile CTA: `box-shadow: 0 -4px 16px rgba(0,0,0,.06)` (bóng lên, nhẹ)

---

## 4. Component visual — quy chuẩn

### CTA button (canonical, Palette A)
```css
.cta {
  background: var(--accent);         /* #e8623d */
  color: #fff;
  font-weight: 800;
  font-size: 19px;
  padding: 18px 34px;
  border-radius: 14px;
  box-shadow: 0 8px 22px rgba(232,98,61,.32);
  transition: transform .15s, background .15s;
}
.cta:hover { background: #c94e2c; transform: translateY(-2px); }
```

Quy tắc:
- CTA phải **cùng màu accent** xuyên trang — khách nhớ "chỗ nào cam là chỗ mua"
- Padding rộng (18–20px dọc, 30–36px ngang) — thumb-friendly trên mobile
- Micro-animation `translateY(-2px)` khi hover — sinh động không quá đà
- CTA trên offer box: đảo màu (nền trắng, chữ cam) để nổi hơn nền brand xanh đen

### CTA pulse (dùng khi urgency mạnh — Palette B, hoặc cuối trang)
```css
@keyframes pulse {
  0%, 100% { box-shadow: 0 8px 22px rgba(232,98,61,.32); }
  50%      { box-shadow: 0 8px 32px rgba(232,98,61,.55); }
}
.cta.pulse { animation: pulse 2s ease-in-out infinite; }
```

**Cẩn thận:** dùng tối đa **1 CTA pulse trên trang** (thường là CTA cuối hoặc CTA offer). Nhiều pulse = mắt loạn = giảm chuyển đổi.

### Countdown (đếm ngược thật)
```css
.countdown {
  display: flex;
  gap: 8px;
  justify-content: center;
}
.countdown-cell {
  background: rgba(26,43,74,.06);
  border: 1px solid var(--line);
  border-radius: 10px;
  padding: 10px 14px;
  min-width: 64px;
  text-align: center;
}
.countdown-cell b {
  font-size: 26px;
  font-weight: 800;
  color: var(--brand);
  display: block;
  font-variant-numeric: tabular-nums;  /* số cùng chiều rộng, không nhảy */
}
.countdown-cell span {
  font-size: 12px;
  color: var(--ink-soft);
  letter-spacing: .05em;
}
```

JS đếm ngược: xem `assets/sale-page-template.html` phần script cuối.

**Cấm:**
- Countdown reset khi refresh trang
- Countdown về 0 rồi vẫn hiển thị offer y nguyên (fake)

### Badge guarantee (huy chương cam kết)
```css
.guarantee-badge {
  display: inline-block;
  width: 120px;
  height: 120px;
  border-radius: 50%;
  background: linear-gradient(135deg, #e8623d, #c94e2c);
  color: #fff;
  display: grid;
  place-items: center;
  font-family: inherit;
  font-weight: 800;
  text-align: center;
  padding: 12px;
  box-shadow: 0 12px 28px rgba(232,98,61,.35);
}
.guarantee-badge .big { font-size: 28px; line-height: 1; }
.guarantee-badge .small { font-size: 11px; letter-spacing: .1em; text-transform: uppercase; }
```

Cấu trúc HTML:
```html
<div class="guarantee-badge">
  <div>
    <div class="big">30</div>
    <div class="small">ngày<br>hoàn tiền</div>
  </div>
</div>
```

Đặt gần offer box hoặc CTA — chuyển sự chú ý sang "rủi ro thấp".

### Sticky CTA mobile
- Cố định đáy màn hình mobile, không hiển thị desktop
- Nền trắng, viền trên nhẹ
- Chiều cao ~64px (thumb reach)
- `padding-bottom: 84px` cho body để tránh sticky che nội dung cuối

### Offer box (bảng giá + bonus)
- Nền brand đậm (`#1a2b4a`), chữ trắng — tạo tương phản mạnh, hút chú ý
- Padding lớn (36–48px)
- CTA bên trong: đảo màu (nền trắng, chữ cam) để nổi hơn nền tối

### FAQ (accordion)
- Dùng `<details><summary>` HTML native — nhẹ, không cần JS, accessible
- Summary color = brand; icon +/– bên phải màu accent
- Khi mở: `p` màu ink-soft, padding trên 12px

---

## 5. Ảnh & icon

### Ảnh sản phẩm / cover
- **Kích thước:** 1200×800 (3:2) hoặc 1600×900 (16:9) — tải nhanh, đẹp trên retina
- **Format:** WebP (nhỏ 30% so với JPEG cùng chất lượng); fallback JPEG
- **Compression:** ≤200KB cho ảnh full-width
- **Border-radius:** 14px (khớp `--radius`) — trừ khi ảnh là logo hoặc icon

### Ảnh testimonial (avatar)
- Vuông, 48×48 hoặc 64×64
- Border-radius: 50% (tròn)
- object-fit: cover
- **KHÔNG dùng ảnh stock** cho testimonial — chỉ ảnh THẬT của học viên

### Icon
- Ưu tiên **inline SVG** (không cần load thư viện)
- Icon check: `✓` U+2713 (không dùng emoji check ✅ — trẻ con)
- Icon cảnh báo: `⚠` hoặc SVG tam giác
- **KHÔNG emoji trang trí** — bám rule Trí (feedback_no_emoji)

---

## 6. Responsive — mobile-first checklist

Kiểm bằng DevTools ở 3 kích thước:
- **iPhone SE 375px** — kích thước hẹp nhất còn nhiều người dùng
- **iPhone Pro 393px** — chuẩn iOS phổ biến
- **iPad Mini 768px** — breakpoint chuyển sang desktop layout

Checklist:
- [ ] Body font ≥17px trên mobile
- [ ] CTA button rộng ≥60% chiều rộng màn hình
- [ ] Không có horizontal scroll (kể cả 375px)
- [ ] Ảnh full-width không vỡ tỉ lệ
- [ ] Grid 2 cột → 1 cột dưới 720px
- [ ] Section padding giảm còn 40–56px (không cần 80px như desktop)
- [ ] Sticky mobile CTA hiện, không đè nội dung cuối (body `padding-bottom: 84px`)
- [ ] Tap target ≥44×44px (Apple HIG)

---

## 7. Performance visual (ảnh hưởng chuyển đổi)

Mỗi 100ms tải chậm = giảm ~1% chuyển đổi (nghiên cứu Amazon, Google).

Bắt buộc:
- **CSS inline** trong `<style>` (một request ít hơn)
- **JS chỉ khi cần** — countdown, form validation. Đừng nhúng jQuery/framework cho sale page
- **Ảnh lazy-load:** `<img loading="lazy">` cho ảnh dưới fold
- **Ảnh có width/height attribute** — tránh layout shift (CLS)
- **Font system-native** hoặc `font-display: swap` nếu load Google Fonts

Cấm:
- Video autoplay có tiếng (audience khó chịu, browser chặn)
- Popup xin email chặn nội dung ngay khi vào trang
- Chat widget cồng kềnh (Tawk.to, Zendesk full stack) — thay bằng nút Zalo/Messenger đơn giản

---

## 8. Accessibility (a11y) — không phải "nice-to-have"

Trong tệp founder tuổi 40+, một phần đáng kể **cần glasses / dùng dark mode / tay to bấm bằng thumb**. A11y tốt = chuyển đổi tốt.

- Contrast: text `#1c2126` trên `#ffffff` = 15.4:1 (AAA). Đừng để contrast dưới 4.5:1 (AA)
- Focus visible: `.cta:focus-visible { outline: 3px solid var(--brand); }` — người dùng keyboard/screen reader thấy được
- `alt=""` cho mọi ảnh — không rỗng
- Tap target ≥44×44px
- Không dùng chỉ MÀU để phân biệt (thêm icon/text) — cho người mù màu

---

## 9. Bám nhất quán qua nhiều trang

Nếu Trí có nhiều sale page (Xưởng Nội Dung, Mastermind, sản phẩm mới…), tất cả **PHẢI** dùng cùng palette + typography + component style. Khách nhớ "trang của Trí" là nhớ **cảm giác thị giác nhất quán**, không phải nhớ tên miền.

Nếu bắt buộc phải break brand (vd sự kiện đặc biệt), viết vào SKILL.md dự án là "brand exception cho X" — không thành thói quen.

---

**Tham khảo chéo:**
- HTML template có sẵn design tokens: `../assets/sale-page-template.html`
- Hướng dẫn build HTML: `html-build-guide.md`
- CRO + UI/UX rules: `cro-uiux-design.md`
- Copy formulas: `copy-formulas-tri.md`
