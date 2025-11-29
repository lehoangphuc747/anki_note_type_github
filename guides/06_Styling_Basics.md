# 🎨 Styling & HTML: Cơ Bản

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

**Nguồn**: [Anki Manual - Styling & HTML](https://docs.ankiweb.net/templates/styling.html)

---

## 🎨 Card Styling

Video hướng dẫn: [Styling Cards](http://www.youtube.com/watch?v=F1j1Zx0mXME&yt:cc=on)

Phần styling của Cards screen có thể truy cập bằng cách click nút **"Styling"** bên cạnh nút "Back Template". Tại đây, bạn có thể thay đổi màu nền, font mặc định, căn chỉnh text, v.v.

### Các tùy chọn tiêu chuẩn

| Property | Mô tả |
|----------|-------|
| **font-family** | Tên font sử dụng. Nếu font có khoảng trắng như "MS Unicode", cần đặt trong dấu ngoặc kép: `font-family: "MS Unicode";` |
| **font-size** | Kích thước font (pixels). Giữ nguyên `px` ở cuối khi thay đổi |
| **text-align** | Căn chỉnh text: `center`, `left`, hoặc `right` |
| **color** | Màu text. Dùng tên màu đơn giản ("blue", "lightyellow") hoặc [HTML color codes](https://htmlcolorcodes.com/) |
| **background-color** | Màu nền của card |

### Styling riêng cho từng card

Styling được chia sẻ giữa tất cả cards của note type đó. Tuy nhiên, có thể chỉ định styling riêng cho từng card:

```css
.card {
  background-color: yellow;
}
.card1 {
  background-color: blue;
}
```
Ví dụ trên sẽ dùng nền vàng cho tất cả cards trừ card đầu tiên (nền xanh).

---

## 🖼️ Image Resizing

Anki mặc định thu nhỏ hình ảnh để vừa màn hình. Để tắt tính năng này:

```css
img {
  max-width: none;
  max-height: none;
}
```

### Khắc phục lỗi trên AnkiDroid
AnkiDroid đôi khi gặp vấn đề scale images. Dùng `!important`:

```css
img {
  max-width: 300px !important;
  max-height: 300px !important;
}
```

### Không ảnh hưởng đến icon star (marked cards)
```css
img#star {
  /* styling riêng cho star icon */
}
```

---

## 🔤 Field Styling

Styling mặc định áp dụng cho toàn bộ card. Bạn có thể tạo styling riêng cho các fields hoặc phần cụ thể của card.

### Ví dụ: Dùng font Thai cho field "Expression"

**Bước 1: Wrap text với HTML trong Template**
```html
What is <div class=mystyle1>{{Expression}}</div>?
```

**Bước 2: Thêm CSS vào Styling section**
```css
.mystyle1 {
  font-family: ayuthaya;
  font-size: 30px;
  color: #a83232;
}
```

---

### ⬅️ [Bài trước: Text to Speech (TTS)](./05_TTS.md) | [Bài tiếp theo: Styling Nâng Cao](./06a_Styling_Advanced.md) ➡️
