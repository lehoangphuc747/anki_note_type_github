# 🚀 Styling: Nâng Cao

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: 29/11/2025

---

## 🔊 Audio Replay Buttons

Khi cards có audio hoặc TTS, Anki hiển thị nút replay. Bạn có thể tùy chỉnh giao diện nút này:

```css
.replay-button svg {
  width: 20px;
  height: 20px;
}
.replay-button svg circle {
  fill: blue; /* Màu tròn nền */
}
.replay-button svg path {
  stroke: white;
  fill: green; /* Màu tam giác play */
}
```

---

## ↔️ Text Direction (RTL)

Với ngôn ngữ viết từ phải sang trái (Arabic, Hebrew):

**Thay đổi toàn bộ card:**
```css
.card {
  direction: rtl;
}
```

**Chỉ thay đổi một số fields:**
```html
<div dir="rtl">{{Front}}</div>
```

---

## 📜 Fading and Scrolling

### Scrolling
Anki tự động scroll đến answer. Nó tìm element có `id=answer` và scroll đến đó.
- Để tắt scrolling: Xóa `id=answer` khỏi template.
- Để đổi vị trí scroll: Chuyển `id=answer` sang thẻ HTML khác.

### Fading
Mặt question của card fade in mặc định. Điều chỉnh delay bằng Javascript (đặt ở mặt trước):

```html
<script>
  qFade = 100; /* 100ms (mặc định) */
  if (typeof anki !== "undefined") anki.qFade = qFade;
</script>
```
Đặt `qFade = 0` để tắt hiệu ứng fade.

---

## 🖥️ Browser Appearance

Nếu card templates quá phức tạp, cột Question/Answer trong Browser sẽ khó đọc. Bạn có thể định nghĩa template riêng cho Browser bằng cách chọn radio button **"Browser Appearance"** trong cửa sổ Cards.

- Giúp hiển thị gọn gàng hơn khi quản lý card.
- Cú pháp giống hệt template thường.

---

### ⬅️ [Bài trước: Styling Cơ Bản](./06_Styling_Basics.md) | [Bài tiếp theo: Platform & Night Mode](./06b_Styling_Platform.md) ➡️
