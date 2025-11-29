# 💻 Javascript trong Anki

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Khả năng & Giới hạn

Anki cards thực chất là các trang web thu nhỏ, nên bạn có thể nhúng Javascript để tạo tương tác (nút bấm, đồng hồ đếm ngược, animation...).

> ⚠️ **Cảnh báo quan trọng**: Javascript là tính năng nâng cao và **không được hỗ trợ chính thức**. Nếu code lỗi, card của bạn có thể không hiện ra. Code chạy được trên máy tính chưa chắc chạy được trên AnkiDroid/iOS.

---

## Những điều cần lưu ý

1.  **Không dùng `document.write()`**: Vì Anki load card động, hàm này có thể xóa sạch nội dung card. Hãy dùng `document.getElementById().innerHTML`.
2.  **Phạm vi biến (Scope)**: Javascript giữa mặt trước và mặt sau đôi khi tồn tại trong cùng một môi trường. Đặt tên biến cẩn thận để tránh xung đột.
3.  **Debug**: Bạn có thể dùng Chrome để debug webview của Anki.
    *   Xem hướng dẫn: [Anki WebView Debugging](https://addon-docs.ankiweb.net/debugging.html)

---

## Ví dụ đơn giản: Hiện thông báo

```html
<script>
   var myMessage = "Hello Anki User!";
   // Kiểm tra xem element có id="hello-box" có tồn tại không trước khi gán
   if (document.getElementById("hello-box")) {
       document.getElementById("hello-box").innerHTML = myMessage;
   }
</script>

<div id="hello-box"></div>
```

---

### ⬅️ [Bài trước: Cài đặt Fonts](./06c_Styling_Fonts.md) | [Bài tiếp theo: Checks and Errors](./07_Errors.md) ➡️

