# 📱 Platform & Night Mode

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## 📱 Platform-Specific CSS

Anki cung cấp các class CSS đặc biệt để bạn tùy chỉnh giao diện riêng cho từng thiết bị (Windows, Mac, Android, iOS...).

**Ví dụ CSS:**
```css
/* Windows */
.win .example { font-family: "Arial"; }

/* macOS */
.mac .example { font-family: "Helvetica"; }

/* iOS (iPhone/iPad) */
.mobile .example { font-size: 20px; }
.iphone .example { font-size: 18px; }

/* Android */
.android .example { font-size: 22px; }
```

**Cách dùng trong Template:**
Bạn cần bọc nội dung trong thẻ div có class tương ứng:
```html
<div class="example">{{Field}}</div>
```
*Lưu ý: Anki tự động thêm class `.win`, `.mac`, `.mobile`... vào thẻ `<body>` hoặc wrapper bao quanh card, nên bạn chỉ cần định nghĩa CSS như trên.*

---

## 🌙 Night Mode (Chế độ tối)

Khi người dùng bật Night Mode, Anki sẽ thêm class `.nightMode` vào card.

### Background nhạt hơn cho Night Mode
```css
.card.nightMode {
  background-color: #2a2a2a; /* Màu xám tối thay vì đen tuyền */
}
```

### Đổi màu chữ riêng cho Night Mode
```css
.nightMode .highlight {
  color: yellow; /* Màu vàng dễ đọc trên nền tối */
}

/* Mặc định (Day Mode) */
.highlight {
  color: blue; /* Màu xanh dễ đọc trên nền sáng */
}
```

---

### ⬅️ [Bài trước: Styling Nâng Cao](./06a_Styling_Advanced.md) | [Bài tiếp theo: Cài đặt Fonts](./06c_Styling_Fonts.md) ➡️

