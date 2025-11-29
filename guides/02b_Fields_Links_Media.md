# 🔗 Dictionary Links & Media

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: 29/11/2025

---

## 🔗 Dictionary Links (Link Tra Từ Điển)

Bạn có thể tạo link để tự động tra cứu từ vựng trên các trang web bên ngoài (Google Translate, Cambridge Dictionary, v.v.).

### Cú pháp cơ bản

```html
{{Expression}}

<a href="http://example.com/search?q={{Expression}}">check in dictionary</a>
```

Khi click vào link "check in dictionary", trình duyệt sẽ mở URL `http://example.com/search?q=` nối với nội dung của field `Expression`.

### Xử lý HTML trong fields

Nếu field của bạn có chứa định dạng (như **bold**, *italic*), link có thể bị lỗi vì chứa cả các thẻ HTML. Dùng `text:` để lấy nội dung văn bản thuần túy:

```html
<a href="http://example.com/search?q={{text:Expression}}">check in dictionary</a>
```

---

## 🖼️ Media trên Template (Media Tĩnh)

Đôi khi bạn muốn thêm một hình ảnh hoặc logo cố định xuất hiện trên **tất cả** các cards (ví dụ: logo của bộ thẻ, hình nền trang trí).

### Cách thực hiện

1. **Chuẩn bị file**: Đổi tên file ảnh/âm thanh bắt đầu bằng dấu gạch dưới `_`. Ví dụ: `_logo.jpg`.
   > *Dấu `_` báo cho Anki biết đây là file dùng chung trong template, tránh bị xóa nhầm khi dùng tính năng "Check Unused Media".*
   
2. **Copy file**: Đưa file `_logo.jpg` vào thư mục `collection.media` của Anki.

3. **Thêm vào Template**:

```html
<img src="_logo.jpg">
```

> ⚠️ **Lưu ý**: Anki không hỗ trợ tham chiếu media động trong tên field (ví dụ: `<img src="{{Expression}}.jpg">` sẽ không hoạt động ổn định).

---

### ⬅️ [Bài trước: Hint Fields](./02a_Fields_Hint.md) | [Bài tiếp theo: Hỗ Trợ Ngôn Ngữ](./02c_Fields_Language.md) ➡️
