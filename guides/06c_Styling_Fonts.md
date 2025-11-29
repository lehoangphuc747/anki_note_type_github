# 🔤 Cài Đặt Fonts (Custom Fonts)

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Tại sao cần cài Font?
Nếu bạn dùng một font lạ trên máy tính, khi đồng bộ sang điện thoại (iOS/Android) font đó có thể bị lỗi ô vuông hoặc trở về font mặc định. Để đảm bảo hiển thị giống nhau mọi nơi, bạn cần nhúng font vào Anki.

**Formats hỗ trợ**: `.ttf` (khuyên dùng), `.otf`, `.woff`.

---

## Quy trình cài đặt (3 Bước)

### Bước 1: Thêm Font vào Media Folder
1. **Đổi tên file font**: Thêm dấu gạch dưới `_` vào đầu tên file.
   * Ví dụ: `Arial.ttf` ➡️ `_arial.ttf`
   * *Mục đích: Để Anki biết đây là file dùng chung, không xóa nhầm.*
2. **Copy vào thư mục media**: Tìm thư mục `collection.media` của Anki và paste file vào đó.

### Bước 2: Khai báo Font trong CSS
Mở cửa sổ **Styling**, thêm đoạn code sau vào cuối:

```css
@font-face {
  font-family: "MyCustomFont"; /* Tên bạn tự đặt để gọi sau này */
  src: url("_arial.ttf");      /* Tên file chính xác trong thư mục media */
}
```

> ⚠️ **Lưu ý**: Tên file trong `url()` phải khớp 100% với tên file thực tế (phân biệt hoa thường). `_Arial.ttf` khác `_arial.ttf`.

### Bước 3: Sử dụng Font
Bây giờ bạn có thể dùng tên font bạn vừa đặt ("MyCustomFont") cho bất kỳ class nào.

**Áp dụng cho toàn bộ card:**
```css
.card {
  font-family: "MyCustomFont", sans-serif;
}
```

**Áp dụng cho một field cụ thể:**
```css
.japanese-text {
  font-family: "MyCustomFont";
}
```

---

### ⬅️ [Bài trước: Platform & Night Mode](./06b_Styling_Platform.md) | [Bài tiếp theo: Javascript](./06d_Styling_JS.md) ➡️

