# 📚 Hướng Dẫn Card Templates Trong Anki

[← Quay lại Trang chủ](./README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## 📑 Mục lục

- [Keyboard Shortcuts](#️-keyboard-shortcuts)
- [Giới Thiệu Về Card Templates](#-giới-thiệu-về-card-templates)
- [Field Replacements](#-field-replacements)
- [Card Generation](#-card-generation)
- [Tài Nguyên Bổ Sung](#-tài-nguyên-bổ-sung)

---

## ⌨️ Keyboard Shortcuts

| Phím | Chức năng |
|------|-----------|
| **← hoặc →** | Điều hướng giữa các chương |
| **S hoặc /** | Tìm kiếm trong tài liệu |
| **?** | Hiển thị trợ giúp |
| **Esc** | Ẩn trợ giúp |
| **Ctrl + 1** | Chuyển đến Front template |
| **Ctrl + 2** | Chuyển đến Back template |
| **Ctrl + 3** | Chuyển đến Styling (CSS) |

---

## 📝 Giới Thiệu Về Card Templates

Card templates cho Anki biết các trường (fields) nào sẽ xuất hiện ở mặt trước và mặt sau của card, và điều khiển các card nào sẽ được tạo ra khi các trường nhất định có nội dung. Bằng cách điều chỉnh card templates, bạn có thể thay đổi thiết kế và styling của nhiều card cùng một lúc.

### 🎥 Video Hướng Dẫn

- **[Switching Card Order](http://www.youtube.com/watch?v=DnbKwHEQ1mA&yt:cc=on)** - Thay đổi thứ tự card
- **[Styling Cards](http://www.youtube.com/watch?v=F1j1Zx0mXME&yt:cc=on)** - Tùy chỉnh styling cho cards
- **[Typing in the Answer](http://www.youtube.com/watch?v=5tYObQ3ocrw&yt:cc=on)** - Tính năng gõ đáp án

### 💻 Ngôn Ngữ Sử Dụng

Trong Anki, templates được viết bằng **HTML** (ngôn ngữ dùng để viết trang web). Phần styling sử dụng **CSS** (ngôn ngữ dùng để tạo style cho trang web).

---

## 🔄 Field Replacements

### Cú pháp cơ bản

Template cơ bản nhất trông như thế này:

```html
{{Front}}
```

Khi bạn đặt text trong dấu ngoặc nhọn, Anki sẽ tìm field có tên đó và thay thế text bằng nội dung thực của field.

> ⚠️ **Lưu ý**: Tên field phân biệt chữ hoa/thường (case sensitive). Nếu bạn có field tên `Front`, viết `{{front}}` sẽ không hoạt động đúng.

### Thêm text tùy ý

Templates không giới hạn chỉ danh sách các fields. Bạn có thể thêm text tùy ý. Ví dụ, nếu bạn đang học thủ đô các nước với note type có field "Country":

```html
What's the capital city of {{Country}}?
```

### Back Template mặc định

```html
{{FrontSide}}

<hr id=answer>

{{Back}}
```

Nghĩa là: "Hiển thị text ở mặt trước, sau đó là đường kẻ phân cách, rồi field Back".

Phần `id=answer` cho Anki biết vị trí phân cách giữa câu hỏi và đáp án, giúp Anki tự động cuộn đến vị trí đáp án khi nhấn **show answer** (đặc biệt hữu ích trên mobile).

### Xuống dòng với `<br>`

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

### 🔊 Text to Speech (TTS)

*Yêu cầu: Anki 2.1.20+, AnkiMobile 2.0.56+, AnkiDroid 2.17+*

Để Anki đọc field Front bằng giọng US English:

```html
{{tts en_US:Front}}
```

Xem danh sách tất cả voices có sẵn:

```html
{{tts-voices:}}
```

Chỉ định nhiều voices (Anki chọn voice đầu tiên có sẵn):

```html
{{tts ja_JP voices=Apple_Otoya,Microsoft_Haruka:Field}}
```

Điều chỉnh tốc độ:

```html
{{tts fr_FR speed=0.8:SomeField}}
```

Với cloze, chỉ đọc phần bị ẩn:

```html
{{tts en_US:cloze-only:Text}}
```

TTS nhiều fields hoặc text tĩnh (*Anki 2.1.50+*):

```html
[anki:tts lang=en_US] This text should be read. Here is {{Field1}} and {{Field2}}[/anki:tts]

This is other text on the template. It is outside of the tags so it should not be read.
```

---

### 📋 Special Fields

```html
The note's tags: {{Tags}}

The type of note: {{Type}}

The card's deck: {{Deck}}

The card's subdeck: {{Subdeck}}

The card's flag: {{CardFlag}}

The type of card ("Forward", etc): {{Card}}

The content of the front template
(only valid in back template): {{FrontSide}}
```

> ⚠️ **Lưu ý**: FrontSide không tự động phát audio từ mặt trước. Nếu muốn audio phát ở cả hai mặt, thêm audio fields vào back template.

---

### 💡 Hint Fields

Thêm field ẩn cho đến khi click hiển thị:

```html
{{hint:MyField}}
```

Hiển thị link "show hint", click để hiện nội dung field.

Tùy chỉnh hint thủ công:

```html
{{#Back}}
<a class=hint href="#"
onclick="this.style.display='none';document.getElementById('hint4753594160').style.display='inline-block';return false;">
Show Back</a><div id="hint4753594160" class=hint style="display: none">{{Back}}</div>
{{/Back}}
```

---

### 🔗 Dictionary Links

Tạo link tra từ điển tự động:

```html
{{Expression}}

<a href="http://example.com/search?q={{Expression}}">check in dictionary</a>
```

#### Xử lý HTML trong fields

Nếu field có formatting (bold, italic...), dùng `text:` để loại bỏ:

```html
<a href="http://example.com/search?q={{text:Expression}}">check in dictionary</a>
```

---

### 🔄 RTL Languages (Phải sang trái)

```html
<div dir=rtl>{{FieldThatHasRTLTextInIt}}</div>
```

---

### 🇯🇵 Ruby Characters / Furigana

Cú pháp: `Text[Ruby]`

| Raw Text | Filter | Kết quả |
|----------|--------|---------|
| `日本語[にほんご]` | `{{furigana:MyField}}` | 日本語 với にほんご ở trên |
| `日本語[にほんご]` | `{{kana:MyField}}` | にほんご |
| `日本語[にほんご]` | `{{kanji:MyField}}` | 日本語 |

---

### 🖼️ Media trên Template

Để thêm hình ảnh/âm thanh giống nhau cho mọi card:

1. Đổi tên file bắt đầu bằng underscore: `_logo.jpg`
2. Thêm vào template:

```html
<img src="_logo.jpg">
```

> ⚠️ **Không hỗ trợ**: Media references trong fields như `<img src="{{Expression}}.jpg">` hoặc `[sound:{{Word}}]`

---

### ⌨️ Type Answer (Gõ đáp án)

Video hướng dẫn: [Typing in the Answer](http://www.youtube.com/watch?v=5tYObQ3ocrw&yt:cc=on)

Thêm `type:` trước field muốn kiểm tra:

```html
{{Native Word}}
{{type:Foreign Word}}
```

Tùy chỉnh font:

```css
code#typeans { font-family: "myfontname"; }
```

Tùy chỉnh màu sắc với CSS classes: `typeGood`, `typeBad`, `typeMissed`

Tùy chỉnh kích thước:

```css
#typeans { font-size: 50px !important; }
```

Type answer cho cloze:

```html
{{cloze:Text}}
{{type:cloze:Text}}
{{Extra}}
```

Bỏ qua dấu accent:

```html
{{type:nc:Front}}
```

---

## 🃏 Card Generation

### Reverse Cards

Video hướng dẫn: [Reversing Cards](http://www.youtube.com/watch?v=DnbKwHEQ1mA&yt:cc=on)

Để tạo cards hai chiều (ví dụ: "ookii"→"big" và "big"→"ookii"):

- **Basic (and reversed card)**: Tự động tạo 2 cards, mỗi chiều một card
- **Basic (optional reversed card)**: Chỉ tạo reverse card khi điền gì đó vào field "Add Reverse" (như "y")

---

### Empty Cards

Anki **không tạo cards với mặt trước trống**. Nếu "My Field" trống và front template chỉ chứa field đó, card sẽ không được tạo.

Khi chỉnh sửa note:
- Anki tự động tạo cards mới nếu trước đó trống nhưng giờ có nội dung
- Anki **không xóa** cards đã trống ngay lập tức (tránh mất dữ liệu)
- Dùng **Tools → Empty Cards** để xem và xóa cards trống

> ⚠️ Không thể xóa thủ công cards riêng lẻ vì chúng sẽ được tạo lại khi chỉnh sửa note.

---

### Conditional Replacement

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

### Controlling Card Generation

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

### Blank Cards

Khi thêm note mới mà templates và fields không tạo được cards nào, một blank card sẽ được tạo bằng template đầu tiên. Điều này cho phép thêm material chưa hoàn chỉnh và chỉnh sửa sau. Dùng **Empty Cards** để xóa nếu không cần.

---

### Cloze Templates

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

## 📚 Tài Nguyên Bổ Sung

- **[Styling & HTML](./ANKI_STYLING_HTML_GUIDE.md)** - CSS styling, fonts, Night Mode, Javascript
- **[Checks and Errors](./ANKI_CHECKS_ERRORS_GUIDE.md)** - Các lỗi thường gặp và cách khắc phục
- **[Các AI Tools Để Tạo Anki Templates](./AI_TOOLS_FOR_ANKI_TEMPLATES.md)** - Hướng dẫn sử dụng AI để tạo templates
- **[UI Style Categories](./UI_STYLE_CATEGORIES.md)** - Tham khảo các phong cách thiết kế UI
- **[Anki Template Documentation](https://docs.ankiweb.net/templates/intro.html)** - Tài liệu chính thức về Anki templates

---

## 📝 Lưu ý

- Luôn preview card trước khi lưu để đảm bảo template hiển thị đúng
- Backup note types của bạn trước khi chỉnh sửa template phức tạp
- Nếu không quen với HTML/CSS, hãy sử dụng [AI tools](./AI_TOOLS_FOR_ANKI_TEMPLATES.md) để hỗ trợ

---

**Chúc bạn tạo được những card templates tuyệt vời! 🎉**
