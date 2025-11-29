# 🔄 Field Replacements: Cơ Bản

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

**Nguồn**: [Anki Manual - Templates](https://docs.ankiweb.net/templates/fields.html)

---

## Cú pháp cơ bản

Template cơ bản nhất trông như thế này:

```html
{{Front}}
```

Khi bạn đặt text trong dấu ngoặc nhọn, Anki sẽ tìm field có tên đó và thay thế text bằng nội dung thực của field.

> ⚠️ **Lưu ý**: Tên field phân biệt chữ hoa/thường (case sensitive). Nếu bạn có field tên `Front`, viết `{{front}}` sẽ không hoạt động đúng.

---

## Thêm text tùy ý

Templates không giới hạn chỉ danh sách các fields. Bạn có thể thêm text tùy ý. Ví dụ, nếu bạn đang học thủ đô các nước với note type có field "Country":

```html
What's the capital city of {{Country}}?
```

---

## Back Template mặc định

```html
{{FrontSide}}

<hr id=answer>

{{Back}}
```

Nghĩa là: "Hiển thị text ở mặt trước, sau đó là đường kẻ phân cách, rồi field Back".

Phần `id=answer` cho Anki biết vị trí phân cách giữa câu hỏi và đáp án, giúp Anki tự động cuộn đến vị trí đáp án khi nhấn **show answer** (đặc biệt hữu ích trên mobile).

---

## Xuống dòng với `<br>`

Card templates giống như trang web, nên cần lệnh đặc biệt để xuống dòng:

```html
<!-- Viết như này: -->
one
two

<!-- Sẽ hiển thị: one two -->

<!-- Để xuống dòng, dùng <br>: -->
one<br>
two
```

Tương tự cho fields:

```html
{{Field 1}}<br>
{{Field 2}}
```

---

### ⬅️ [Bài trước: Card Templates Intro](./01_Templates_Intro.md) | [Bài tiếp theo: Hint Fields](./02a_Fields_Hint.md) ➡️
