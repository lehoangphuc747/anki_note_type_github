# 🔀 Conditional Replacement (Điều Kiện)

[← Quay lại Trang chủ](./README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Khái niệm

Conditional Replacement cho phép bạn hiển thị hoặc ẩn nội dung dựa trên việc một field có trống hay không. Cú pháp sử dụng dấu thăng `#` (nếu có) và dấu mũ `^` (nếu không).

---

## Cú pháp

### 1. Chỉ hiện khi field CÓ nội dung (`#`)

```html
This text is always shown.

{{#FieldName}}
    This text is only shown if FieldName has text in it
{{/FieldName}}
```

**Ví dụ thực tế**: Chỉ hiển thị nhãn "Tags:" nếu note đó thực sự có tags.

```html
{{#Tags}}
    Tags: {{Tags}}
{{/Tags}}
```

### 2. Chỉ hiện khi field TRỐNG (`^`)

```html
{{^FieldName}}
    This text is only shown if FieldName is empty
{{/FieldName}}
```

---

## Ứng dụng nâng cao

### Styling có điều kiện

Bạn có thể dùng conditional để bọc các thẻ HTML. Ví dụ: Chỉ hiển thị field `Notes` với màu xanh nếu nó có nội dung.

```html
{{#Notes}}
    <span style="color:blue;">
{{/Notes}}

{{FieldToFormat}}

{{#Notes}}
    </span>
{{/Notes}}
```

### Kiểm soát việc tạo Card (Controlling Card Generation)

Bạn có thể dùng conditional replacement để ngăn việc tạo card nếu thiếu thông tin quan trọng.

**Ví dụ:** Chỉ tạo card nếu field `Expression` có nội dung.

```html
{{#Expression}}
    {{Expression}}
    {{Notes}}
{{/Expression}}
```

**Ví dụ yêu cầu cả 2 fields:** Chỉ tạo card nếu CẢ `Expression` VÀ `Notes` đều có nội dung.

```html
{{#Expression}}
    {{#Notes}}
        {{Expression}}
        {{Notes}}
    {{/Notes}}
{{/Expression}}
```

> ⚠️ **Quan trọng**: Logic kiểm soát việc tạo card chỉ hoạt động khi bạn đặt conditional replacement ở **Mặt Trước (Front Template)**. Đặt ở mặt sau chỉ có tác dụng ẩn hiện nội dung, không ảnh hưởng việc tạo card.

**Tránh Back trống:**
Nếu bạn muốn chắc chắn card chỉ được tạo nếu có đáp án (Field 2), hãy bọc mặt trước bằng điều kiện kiểm tra Field 2.

```html
{{#Field 2}}
    {{Field 1}}
{{/Field 2}}
```

---

### ⬅️ [Bài trước: Card Generation Cơ Bản](./04_CardGen_Basics.md) | [Bài tiếp theo: Cloze Templates](./04b_CardGen_Cloze.md) ➡️

