# Skill: Dựng sale page chuyển đổi cao (`dct-skill-sale-page-builder`)

Skill cho Claude Code. Đưa bạn đi từ **thông tin sản phẩm** đến một **trang bán hàng hoàn chỉnh** — nghiên cứu khách, chốt chiến lược, viết nội dung theo 16 bước bán hàng, rồi dựng ra file HTML chạy được trên điện thoại lẫn máy tính.

Đây là gói nặng nhất trong bộ: 12 file, quy trình 8 giai đoạn, 3 cổng dừng chờ bạn duyệt.

## Dùng khi nào

- "Viết sale page cho khoá học của tôi"
- "Làm landing page bán sản phẩm X"
- "Dựng trang đăng ký sự kiện"
- "Trang chốt đơn cho chiến dịch quảng cáo"

## Không dùng cho

- Trang chỉ để thu thông tin đổi quà → skill lead magnet
- Một bài đăng Facebook → skill viết bài
- Website hay ứng dụng nhiều trang
- Sửa ảnh, dựng video

## Cài vào máy

1. Bấm **Code → Download ZIP** trên trang GitHub này, giải nén.
2. Chép cả thư mục `dct-skill-sale-page-builder` vào:
   - Dùng cho mọi dự án: `~/.claude/skills/` (Windows: `C:\Users\<tên máy bạn>\.claude\skills\`)
   - Chỉ dùng cho một dự án: `<thư mục dự án>/.claude/skills/`
3. Mở lại Claude Code, nói "viết sale page cho [sản phẩm của bạn]".

## Nó làm gì — 8 giai đoạn

| GĐ | Việc |
|---|---|
| 0 | Chốt bối cảnh: bán gì, mục tiêu chuyển đổi, khách đến từ đâu, giá, hạn chót |
| 1 | Đọc dữ liệu nguồn bạn đưa · ⏸ **GATE 1** |
| 2 | Nghiên cứu sản phẩm · khách hàng · đối thủ (3 nhánh song song) |
| 3 | Chốt chiến lược: Big Idea, thông điệp, góc tiếp cận |
| 4 | Dàn ý 16 bước bán hàng — mỗi bước sinh 3 phương án rồi hội đồng chọn 1 · ⏸ **GATE 2** |
| 5 | Viết nội dung đầy đủ |
| 6 | Dựng HTML responsive (hoặc xuất sang Webcake nếu bạn đăng ở đó) |
| 7 | Tối ưu, rà soát · ⏸ **GATE 3** + cổng kiểm tra pháp lý bắt buộc |

Ba chỗ ⏸ là **cổng dừng** — skill phải chờ bạn duyệt mới đi tiếp.

## Trong gói có gì

| File | Nội dung |
|---|---|
| `SKILL.md` | Quy trình 8 giai đoạn, nguyên tắc bất di bất dịch, 12 vai trò |
| `references/16-buoc-khung-noi-dung.md` | 16 bước bán hàng — xương sống của trang |
| `references/nghien-cuu-va-chien-luoc.md` | Khung nghiên cứu sản phẩm / khách / đối thủ |
| `references/tam-ly-thuyet-phuc.md` | Nguyên lý tâm lý đằng sau từng khối |
| `references/cro-uiux-design.md` | Tối ưu chuyển đổi, bố cục, trải nghiệm |
| `references/copy-formulas-tri.md` | Công thức viết headline, CTA, xử lý phản đối |
| `references/visual-dct-brand.md` | 3 bảng màu, typography, quy tắc chọn palette |
| `references/html-build-guide.md` | Cách dựng file HTML sạch, nhẹ, chạy tốt trên điện thoại |
| `references/hoi-dong-protocol.md` | Cách chấm điểm 3 phương án rồi chọn 1 |
| `references/compliance-check.md` | Cổng pháp lý — cấm hứa gì, ngành nào rủi ro cao |
| `references/webcake-output.md` | Đưa trang sang Webcake / Pancake |
| `assets/sale-page-template.html` | Mẫu HTML đủ 16 khối, đã cấy sẵn hệ màu |

## Ba nguyên tắc gói này bám

1. **Phân tích trước, thiết kế sau** — không gõ chữ nào trước khi hiểu khách.
2. **Không bịa** — số liệu, tên khách, lời chứng thực, thành tựu, giá, cam kết chỉ dùng cái bạn đưa. Thiếu thì hỏi bạn. Một con số bịa làm sụp niềm tin cả trang.
3. **Mọi khối phải phục vụ chuyển đổi** — khối nào không đẩy người đọc tiến gần hơn tới nút bấm thì cắt.

## Lưu ý về pháp lý

Skill có một **cổng kiểm tra bắt buộc** trước khi xuất trang: rà các lời hứa không kiểm chứng được, cam kết kết quả, số liệu không nguồn, và những quy định riêng của ngành nhạy cảm (sức khoẻ, tài chính, tâm linh). Bạn vẫn là người chịu trách nhiệm cuối cùng cho nội dung đăng ra — đọc lại phần cam kết và con số trước khi chạy quảng cáo.
