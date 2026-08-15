# Hướng dẫn dựng HTML sale page (Giai đoạn 6)

Mục tiêu: một file **self-contained, responsive, tải nhanh, dễ chỉnh** mà anh Trí có thể triển khai ngay (mở trực tiếp, up hosting, hoặc dán vào nền tảng landing page).

## Nguyên tắc kỹ thuật

- **Một file `.html` tự chứa**: CSS trong `<style>`, JS (nếu có) trong `<script>` ở cuối. Không phụ thuộc framework nặng. Dễ mang đi, không vỡ khi thiếu mạng.
- **Design tokens qua CSS variables** ở `:root`: màu brand, màu nhấn CTA, nền, chữ, cỡ chữ, bo góc, khoảng cách. Đổi brand = đổi vài biến, không sửa khắp nơi.
- **Mobile-first**: viết CSS cho mobile trước, dùng `@media (min-width: …)` để nâng lên desktop. Layout 1 cột trên mobile, giãn thành nhiều cột ở breakpoint lớn.
- **Ảnh**: `loading="lazy"` cho ảnh dưới màn đầu, `width/height` để tránh nhảy layout, `alt` mô tả. Nén trước khi dùng. Ảnh Hero ưu tiên tải nhanh.
- **CTA là thẻ `<a>`** trỏ tới link mua/đăng ký thật (hỏi anh Trí link đích: form, cổng thanh toán, Messenger, hay Zalo). Chưa có thì để `href="#dang-ky"` cuộn tới form + ghi chú cần thay link.
- **Accessibility**: heading đúng cấp (một `<h1>`), tương phản AA, `:focus-visible` cho nút, `aria-label` khi cần.
- **Không popup phiền, không auto-audio, không hiệu ứng gây phân tâm.** Micro-interaction tinh tế (hover nút, fade khi cuộn) thì được nếu không cản đọc.

---

## Màu sắc — Xu hướng 2025–2026

Xu hướng mạnh nhất hiện tại là **nền sáng cực nhạt + mesh gradient cực nhẹ** thay vì màu phẳng. Tạo cảm giác cao cấp, hiện đại, dễ đọc.

### Bảng màu nền chuẩn (chọn 1 trong các nhóm sau)

| Nhóm | Mã màu | Dùng khi |
|------|--------|----------|
| **Trắng kem** | `#FCFCFA` · `#FAF9F6` · `#F8F7F4` | Sản phẩm cao cấp, tâm linh, wellness |
| **Xám rất nhạt** | `#F5F5F5` · `#F4F4F4` · `#F2F2F2` | Khoá học, B2B, chuyên nghiệp |
| **Mesh gradient nhẹ** | Trắng → Kem, Trắng → Xám nhạt, Kem → Vàng rất nhạt | Dùng ở hero/section điểm nhấn, KHÔNG làm nền toàn trang |

**Cách áp dụng mesh gradient** (dùng CSS, không cần ảnh):
```css
background: linear-gradient(135deg, #FCFCFA 0%, #F5F0E8 50%, #FAF9F6 100%);
/* hoặc radial-gradient cho hiệu ứng mềm hơn */
background: radial-gradient(ellipse at 20% 20%, #F8F4EE 0%, #FCFCFA 60%, #F5F5F5 100%);
```

**Màu chữ trên nền sáng:** `#1A1A1A` (gần đen, không full black) cho body; `#111111` cho heading.

**Màu accent/CTA:** Giữ nguyên theo brand (đỏ, vàng, xanh...) — nền sáng làm cho màu accent nổi bật hơn nhiều.

---

## Font chữ — Chuẩn 2025–2026

**Ưu tiên theo thứ tự:**

1. **Be Vietnam Pro** — lựa chọn hàng đầu cho tiếng Việt, hiện đại, dễ đọc, hỗ trợ dấu chuẩn
2. **Inter** — neutral, cực dễ đọc, phổ biến nhất cho landing page quốc tế
3. **SF Pro Display / SF Pro Text** — system font Apple, không cần load, cực nhanh
4. **Roboto** — Android/Google standard, fallback tốt
5. **Open Sans / Noto Sans** — fallback an toàn, hỗ trợ tiếng Việt tốt

**Cách nạp (Google Fonts — chỉ load weight cần thiết):**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;600;700;800&display=swap" rel="stylesheet">
```

**Font stack trong CSS:**
```css
:root {
  --font-main: 'Be Vietnam Pro', Inter, 'SF Pro Display', -apple-system, BlinkMacSystemFont, sans-serif;
}
body { font-family: var(--font-main); }
```

**Phân cấp cỡ chữ (mobile-first):**
```css
h1   { font-size: clamp(1.75rem, 6vw, 3rem);   font-weight: 800; line-height: 1.15; }
h2   { font-size: clamp(1.35rem, 4vw, 2rem);   font-weight: 700; line-height: 1.25; }
h3   { font-size: clamp(1.05rem, 3vw, 1.35rem); font-weight: 600; }
body { font-size: 16px; line-height: 1.75; }
```

**Quy tắc font:**
- Chỉ load **1 font family**, tối đa **4 weight** (400, 600, 700, 800)
- Heading: 700–800, uppercase nếu ngắn (< 8 từ), mixed case nếu dài
- Body: 400, không in đậm toàn đoạn — chỉ bold từ khoá quan trọng
- Không mix quá 2 font family trong 1 trang

## Bộ khung có sẵn

`assets/sale-page-template.html` là khung khởi đầu: đã có design tokens, layout responsive mobile-first, các section theo map 16 bước, style nút CTA nổi bật, khối testimonial, bảng giá/ưu đãi, FAQ, sticky CTA trên mobile. **Cách dùng:**
1. Copy template ra file mới trong thư mục sản phẩm (vd cùng chỗ project sale page hiện tại).
2. Thay design tokens ở `:root` theo brand (màu, font, bo góc).
3. Điền nội dung thật từ dàn ý 16 bước đã duyệt vào từng section; xoá section không dùng.
4. Thay/chèn ảnh thật; chỗ chưa có ảnh để placeholder ghi "CẦN ẢNH THẬT".
5. Gắn link CTA thật.
6. Rà theo checklist ở `cro-uiux-design.md`, mở thử ở khổ mobile lẫn desktop.

## Kiểm tra hiển thị

Nếu môi trường có công cụ preview (mcp Claude_Preview / trình duyệt), mở trang ở cả khổ ~390px (mobile) và ~1280px (desktop) để soi mạch đọc, nút, khoảng trắng. Không có thì tự rà bằng cách đọc CSS + mô tả cho anh Trí cách mở kiểm tra.

## Bàn giao

Đưa anh Trí: (1) file `.html` hoàn chỉnh, (2) tóm tắt các quyết định thiết kế/chiến lược chính và **vì sao** (để anh nắm logic, không chỉ nhận file), (3) danh sách chỗ cần bổ sung dữ liệu thật (ảnh, testimonial, link CTA) nếu còn.
