# 💡 Hint Fields (Trường Gợi Ý)

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Hint Fields là gì?

Hint Fields giúp bạn ẩn nội dung của một field cho đến khi bạn click vào nó. Tính năng này rất hữu ích để tạo các gợi ý (hints) mà bạn chỉ muốn xem khi thực sự cần thiết, tránh việc nhìn thấy đáp án quá sớm.

---

## Cú pháp

Thêm tiền tố `hint:` vào trước tên field:

```html
{{hint:MyField}}
```

## Cách hoạt động

1. Khi card hiển thị, Anki sẽ hiện một link text (ví dụ: "Show MyField").
2. Khi bạn click vào link đó, nội dung thực sự của field `MyField` sẽ hiện ra.
3. Nếu field `MyField` trống, link gợi ý sẽ không hiển thị.

---

## Tùy chỉnh giao diện Hint (Nâng cao)

Bạn có thể tùy chỉnh giao diện và hành vi của hint bằng HTML/CSS thủ công nếu không muốn dùng `{{hint:Field}}` mặc định:

```html
{{#Back}}
<a class=hint href="#"
onclick="this.style.display='none';document.getElementById('hint4753594160').style.display='inline-block';return false;">
Show Back</a><div id="hint4753594160" class=hint style="display: none">{{Back}}</div>
{{/Back}}
```

*Lưu ý: Cách thủ công này phức tạp hơn và yêu cầu Javascript cơ bản.*

---

### ⬅️ [Bài trước: Field Replacements Cơ Bản](./02_Fields_Basics.md) | [Bài tiếp theo: Dictionary Links & Media](./02b_Fields_Links_Media.md) ➡️

