# 🃏 Card Generation & Conditional Replacement

[← Quay lại Trang chủ](./README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Reverse Cards

Video hướng dẫn: [Reversing Cards](http://www.youtube.com/watch?v=DnbKwHEQ1mA&yt:cc=on)

Để tạo cards hai chiều (ví dụ: "ookii"→"big" và "big"→"ookii"):

- **Basic (and reversed card)**: Tự động tạo 2 cards, mỗi chiều một card
- **Basic (optional reversed card)**: Chỉ tạo reverse card khi điền gì đó vào field "Add Reverse" (như "y")

---

## Empty Cards

Anki **không tạo cards với mặt trước trống**. Nếu "My Field" trống và front template chỉ chứa field đó, card sẽ không được tạo.

Khi chỉnh sửa note:
- Anki tự động tạo cards mới nếu trước đó trống nhưng giờ có nội dung
- Anki **không xóa** cards đã trống ngay lập tức (tránh mất dữ liệu)
- Dùng **Tools → Empty Cards** để xem và xóa cards trống

> ⚠️ Không thể xóa thủ công cards riêng lẻ vì chúng sẽ được tạo lại khi chỉnh sửa note.

---

## Conditional Replacement

Hiển thị text chỉ khi field có hoặc không có nội dung:

```html
This text is always shown.

{{#FieldName}}
    This text is only shown if FieldName has text in it
{{/FieldName}}

{{^FieldName}}
    This text is only shown if FieldName is empty
{{/FieldName}}
```

Ví dụ thực tế - chỉ hiển thị label Tags nếu có tags:

```html
{{#Tags}}
    Tags: {{Tags}}
{{/Tags}}
```

Styling có điều kiện - hiển thị field màu xanh nếu có Notes:

```html
{{#Notes}}
    <span style="color:blue;">
{{/Notes}}

{{FieldToFormat}}

{{#Notes}}
    </span>
{{/Notes}}
```

---

## Controlling Card Generation

Dùng conditional replacement để kiểm soát cards được tạo:

Chỉ tạo card nếu Expression không trống:

```html
{{#Expression}}
    {{Expression}}
    {{Notes}}
{{/Expression}}
```

Yêu cầu cả hai fields:

```html
{{#Expression}}
    {{#Notes}}
        {{Expression}}
        {{Notes}}
    {{/Notes}}
{{/Expression}}
```

> ⚠️ **Quan trọng**: Chỉ hoạt động khi đặt conditional replacement ở **mặt trước**. Đặt ở mặt sau chỉ tạo back trống.

Tránh back trống - yêu cầu Field 2 để tạo card:

```html
{{#Field 2}}
    {{Field 1}}
{{/Field 2}}
```

---

## Blank Cards

Khi thêm note mới mà templates và fields không tạo được cards nào, một blank card sẽ được tạo bằng template đầu tiên. Điều này cho phép thêm material chưa hoàn chỉnh và chỉnh sửa sau. Dùng **Empty Cards** để xóa nếu không cần.

---

## Cloze Templates

Cloze note type hoạt động khác với regular note types - chỉ có một template type dùng chung cho tất cả cloze deletions.

Card generation cho cloze:
1. Anki tìm `{{cloze:FieldName}}` trên front template
2. Tìm tất cả cloze references trong field như `{{c1::text}}`
3. Tạo một card cho mỗi số khác nhau

> ⚠️ Tags `{{cloze:…}}` chỉ hoạt động với cloze note type, không dùng được với regular note type.

Conditional generation cho cloze - hiển thị hint khác nhau cho mỗi cloze:

```html
{{cloze:Text}}

{{#c1}}
    {{Hint1}}
{{/c1}}

{{#c2}}
    {{Hint2}}
{{/c2}}
```

---

### ⬅️ [Bài trước: Special Fields](./03_SpecialFields.md) | [Bài tiếp theo: Text to Speech (TTS)](./05_TTS.md) ➡️

