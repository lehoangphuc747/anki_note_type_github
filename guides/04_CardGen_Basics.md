# 🃏 Card Generation: Cơ Bản

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Reverse Cards (Card Hai Chiều)

Video hướng dẫn: [Reversing Cards](http://www.youtube.com/watch?v=DnbKwHEQ1mA&yt:cc=on)

Để tạo cards hai chiều (ví dụ: học từ "Mèo" → "Cat" và ngược lại "Cat" → "Mèo"):

- **Basic (and reversed card)**: Tự động tạo 2 cards, mỗi chiều một card.
- **Basic (optional reversed card)**: Chỉ tạo reverse card khi bạn điền gì đó vào field "Add Reverse" (ví dụ điền chữ "y"). Nếu để trống field này, chỉ tạo card 1 chiều.

---

## Empty Cards (Card Trống)

Anki có cơ chế thông minh để tránh tạo ra các card vô nghĩa:

**Anki KHÔNG tạo cards nếu mặt trước trống.**
Ví dụ: Nếu Template yêu cầu hiển thị field `{{My Field}}` ở mặt trước, nhưng trong Note đó field `My Field` lại trống, Anki sẽ không tạo card đó.

Khi chỉnh sửa note:
- Anki tự động tạo thêm cards mới nếu bạn điền thêm thông tin vào field trước đó bị trống.
- Anki **không xóa ngay** các cards đã trở nên trống (để tránh bạn mất dữ liệu lịch sử học tập nếu lỡ tay xóa nhầm field).
- Dùng menu **Tools → Empty Cards** để quét và xóa các cards trống này.

> ⚠️ **Lưu ý**: Bạn không thể xóa thủ công từng card riêng lẻ trong Note Type có nhiều card. Bạn phải chỉnh sửa nội dung field hoặc logic của Template.

---

## Blank Cards

Khi bạn thêm một note mới mà dựa trên templates và nội dung các fields hiện tại **không tạo được bất kỳ card nào** (ví dụ tất cả fields mặt trước đều trống), Anki sẽ tạo ra một **Blank Card** (card trắng) sử dụng template đầu tiên.

Điều này giúp bạn vẫn lưu được note đó (nháp) và sửa lại sau. Dùng **Empty Cards** để xóa chúng nếu không cần thiết.

---

### ⬅️ [Bài trước: Special Fields](./03_SpecialFields.md) | [Bài tiếp theo: Conditional Replacement](./04a_CardGen_Conditional.md) ➡️
