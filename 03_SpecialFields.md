# 📋 Special Fields Trong Anki

[← Quay lại Trang chủ](./README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

**Nguồn**: [Anki Manual - Templates](https://docs.ankiweb.net/templates/fields.html)

---

**Special Fields là gì?** Đây là các fields đặc biệt mà Anki tự động cung cấp. Bạn không cần tạo chúng - chúng luôn có sẵn và hiển thị thông tin về note/card của bạn.

---

## 1. {{Tags}} - Tags của note

**Là gì?** Hiển thị tất cả tags (nhãn) bạn đã gán cho note.

**Khi nào dùng?** Khi muốn xem tags trên card để phân loại hoặc nhớ nhóm từ vựng.

**Ví dụ template:**
```html
{{Front}}

{{#Tags}}
<p style="color: gray; font-size: 12px;">Tags: {{Tags}}</p>
{{/Tags}}
```

**Kết quả hiển thị:**
```
Từ vựng: Hello
Tags: basic, greeting, common
```

**Lưu ý**: Dùng `{{#Tags}}...{{/Tags}}` để chỉ hiển thị khi có tags (xem phần [Conditional Replacement](./01a_CardGeneration.md#conditional-replacement) trong Card Generation).

---

## 2. {{Type}} - Loại note type

**Là gì?** Hiển thị tên của note type (ví dụ: "Basic", "Basic (and reversed card)", v.v.)

**Khi nào dùng?** Ít khi dùng, chủ yếu cho debugging hoặc khi muốn biết card thuộc loại nào.

**Ví dụ template:**
```html
{{Front}}

<small>Note Type: {{Type}}</small>
```

**Kết quả hiển thị:**
```
Hello

Note Type: Basic
```

---

## 3. {{Deck}} - Tên deck

**Là gì?** Hiển thị tên deck mà card đang thuộc về.

**Khi nào dùng?** Khi bạn có nhiều decks và muốn biết card đang ở deck nào. Hữu ích khi học nhiều chủ đề khác nhau.

**Ví dụ template:**
```html
{{Front}}

<div style="background: #f0f0f0; padding: 5px;">
  Deck: {{Deck}}
</div>
```

**Kết quả hiển thị:**
```
Hello

Deck: English::Vocabulary
```

**Ví dụ thực tế**: Nếu bạn có decks "English::Beginner", "English::Advanced", card sẽ hiển thị đúng deck của nó.

---

## 4. {{Subdeck}} - Tên subdeck

**Là gì?** Giống {{Deck}} nhưng chỉ hiển thị tên subdeck (phần sau dấu `::`).

**Khi nào dùng?** Khi deck có cấu trúc phân cấp (ví dụ: `English::Beginner::Unit1`).

**So sánh:**
- `{{Deck}}` → `English::Beginner::Unit1`
- `{{Subdeck}}` → `Unit1`

**Ví dụ template:**
```html
{{Front}}

<p>Chapter: {{Subdeck}}</p>
```

---

## 5. {{CardFlag}} - Cờ đánh dấu card

**Là gì?** Hiển thị màu cờ bạn đã đánh dấu cho card (🔴 Đỏ, 🟠 Cam, 🟡 Vàng, 🟢 Xanh lá, 🔵 Xanh dương, 🟣 Tím, ⚫ Đen).

**Khi nào dùng?** Khi muốn hiển thị cờ đánh dấu trên card để nhắc nhở mức độ quan trọng hoặc tình trạng học.

**Ví dụ template:**
```html
{{Front}}

{{#CardFlag}}
<p>Flag: {{CardFlag}}</p>
{{/CardFlag}}
```

**Lưu ý**: Chỉ hiển thị khi bạn đã đánh dấu cờ cho card. Nếu chưa có cờ, sẽ không hiển thị gì (trừ khi dùng conditional).

---

## 6. {{Card}} - Loại card

**Là gì?** Hiển thị tên loại card (ví dụ: "Card 1", "Forward", "Reverse", v.v.)

**Khi nào dùng?** Khi muốn biết card đang ở chiều nào (thuận/nghịch) hoặc là card nào trong note type có nhiều cards.

**Ví dụ với Basic (and reversed card):**
- Front card → `{{Card}}` hiển thị: `Card 1` hoặc `Forward`
- Back card (reverse) → `{{Card}}` hiển thị: `Card 2` hoặc `Reverse`

**Ví dụ template:**
```html
{{Front}}

<small>{{Card}}</small>
```

---

## 7. {{FrontSide}} - Nội dung mặt trước

**Là gì?** Hiển thị lại toàn bộ nội dung mặt trước của card. Chỉ dùng được trong **back template** (mặt sau).

**Khi nào dùng?** Mặc định back template đã có `{{FrontSide}}` để bạn nhớ lại câu hỏi khi xem đáp án.

**Ví dụ back template mặc định:**
```html
{{FrontSide}}

<hr id=answer>

{{Back}}
```

**Kết quả:**
- Hiển thị nội dung front template (câu hỏi)
- Sau đó đường kẻ phân cách
- Sau đó đáp án

> ⚠️ **Lưu ý quan trọng**: 
> - `{{FrontSide}}` **không tự động** phát audio từ mặt trước
> - Nếu bạn có `{{tts en_US:Front}}` trên front template, nó sẽ **không** tự động phát trên back
> - Muốn audio phát cả hai mặt? Thêm lại TTS vào back template (xem [TTS Guide](./04_TTS.md))

---

## 📝 Tóm tắt nhanh

| Special Field | Hiển thị | Dùng khi nào |
|---------------|----------|--------------|
| `{{Tags}}` | Tags của note | Muốn xem nhãn phân loại |
| `{{Type}}` | Tên note type | Debugging (ít dùng) |
| `{{Deck}}` | Tên deck đầy đủ | Có nhiều decks, muốn biết card ở đâu |
| `{{Subdeck}}` | Tên subdeck | Deck có phân cấp (A::B::C) |
| `{{CardFlag}}` | Màu cờ đánh dấu | Đã đánh cờ cho card |
| `{{Card}}` | Tên loại card | Có cards thuận/nghịch, muốn phân biệt |
| `{{FrontSide}}` | Nội dung mặt trước | Dùng trong back template (mặc định) |

---

## 💡 Mẹo sử dụng

### Chỉ hiển thị khi có giá trị

```html
{{#Tags}}
  <p>Tags: {{Tags}}</p>
{{/Tags}}
```

### Styling cho special fields

```html
<div style="color: #666; font-size: 11px;">
  Deck: {{Deck}} | {{Card}}
</div>
```

### Kết hợp nhiều special fields

```html
{{Front}}

<div class="card-info">
  {{#Tags}}📌 {{Tags}} | {{/Tags}}
  📁 {{Deck}}
  {{#CardFlag}} | 🚩 {{CardFlag}}{{/CardFlag}}
</div>
```

---

### ⬅️ [Bài trước: Type Answer](./02d_Fields_TypeAnswer.md) | [Bài tiếp theo: Card Generation](./04_CardGeneration.md) ➡️
