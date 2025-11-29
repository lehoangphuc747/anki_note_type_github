# 🧩 Cloze Templates (Điền Vào Chỗ Trống)

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Cơ chế hoạt động

Cloze note type hoạt động khác với các note type thông thường. Nó chỉ có **một template type** duy nhất dùng chung cho tất cả các cloze deletions (c1, c2, c3...).

Quy trình tạo card:
1. Anki tìm `{{cloze:FieldName}}` trên Front Template.
2. Quét nội dung field đó để tìm các cloze references như `{{c1::text}}`, `{{c2::text}}`.
3. Tạo một card riêng biệt cho mỗi số (c1, c2...) khác nhau.

> ⚠️ **Lưu ý**: Tags `{{cloze:…}}` chỉ hoạt động với Cloze Note Type. Bạn không thể dùng nó trong Regular Note Type (Basic).

---

## Conditional Generation cho Cloze

Bạn có thể hiển thị nội dung khác nhau tùy thuộc vào việc card nào đang được hiển thị (c1 hay c2...).

**Ví dụ:** Hiển thị gợi ý (Hint) khác nhau cho mỗi cloze.

```html
{{cloze:Text}}

{{#c1}}
    {{Hint1}}
{{/c1}}

{{#c2}}
    {{Hint2}}
{{/c2}}
```

**Giải thích:**
- Khi hiển thị card 1 (`c1`), nội dung trong `{{#c1}}...{{/c1}}` sẽ hiện ra (Hint 1).
- Khi hiển thị card 2 (`c2`), nội dung trong `{{#c2}}...{{/c2}}` sẽ hiện ra (Hint 2).

---

### ⬅️ [Bài trước: Conditional Replacement](./04a_CardGen_Conditional.md) | [Bài tiếp theo: Text to Speech (TTS)](./05_TTS.md) ➡️

