# ⚠️ Checks and Errors Trong Anki

[← Quay lại Trang chủ](./README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

**Nguồn**: [Anki Manual - Checks and Errors](https://docs.ankiweb.net/templates/errors.html)

---

## 📑 Mục lục

- [Giới thiệu](#-giới-thiệu)
- [Cách sửa lỗi cơ bản](#-cách-sửa-lỗi-cơ-bản)
- [Template Syntax Error](#-template-syntax-error)
- [Identical Front Sides](#-identical-front-sides)
- [Front of Card is Blank](#-front-of-card-is-blank)
- [No Cloze Filter on Cloze Note Type](#-no-cloze-filter-on-cloze-note-type)

---

## 📋 Giới thiệu

Khi bạn lưu thay đổi note type hoặc export deck, **Anki 2.1.45+** kiểm tra một số lỗi phổ biến. Các lỗi này sẽ gây vấn đề sau này khi bất kỳ ai học các cards bị ảnh hưởng, vì vậy Anki sẽ không cho phép bạn tiếp tục trước khi sửa chúng.

> 📖 Vui lòng xem [Key Concepts](https://docs.ankiweb.net/getting-started.html#key-concepts) trước khi đọc tiếp.

---

## 🔧 Cách sửa lỗi cơ bản

Hầu hết các lỗi bên dưới yêu cầu bạn sửa đổi note type/card template. Để làm điều này:

1. Mở **Browse screen**, nhìn vào các items ở bên trái
2. Tìm **note type** được đề cập trong thông báo lỗi (có thể dùng thanh tìm kiếm ở góc trên trái)
3. Click vào note type để hiển thị cards/notes ở bên phải
4. Click nút **Cards…** ở đầu vùng chỉnh sửa để mở [templates screen](https://docs.ankiweb.net/templates/intro.html#the-templates-screen)

---

## ❌ Template Syntax Error

Loại lỗi này chỉ ra việc sử dụng không đúng cú pháp [field replacement](https://docs.ankiweb.net/templates/fields.html).

### Cách sửa lỗi template

| Platform | Cách thực hiện |
|----------|----------------|
| **Computer** | Edit card có vấn đề → Click nút **Cards…** |
| **AnkiMobile** | Đang xem card trong study screen → Tap cog/gear → **Card Template** |

> 💡 Khi sửa lỗi, nó sẽ cập nhật **tất cả cards** của loại đó - không cần sửa từng card riêng lẻ.

---

### Các lỗi cụ thể và cách sửa

#### ❌ Found '{{Field}}', but there is no field called 'Field'

**Nguyên nhân**: Template chứa tên field không tồn tại.

**Cách sửa**: Tìm `{{Field}}` trong card template và **xóa nó**.

---

#### ❌ Missing }} in {{Field

**Nguyên nhân**: Tìm thấy `{{` trong template nhưng không có `}}` tương ứng.

**Sai:**
```html
{{Field
```

**Đúng:**
```html
{{Field}}
```

---

#### ❌ Missing {{/Field}}

**Nguyên nhân**: Anki tìm thấy `{{#Field}}` hoặc `{{^Field}}` trong template mà không có `{{/Field}}` tương ứng.

**Cách sửa**: Xóa `{{#Field}}` hoặc `{{^Field}}` khỏi template, hoặc thêm `{{/Field}}` đóng lại.

---

#### ❌ Found {{/One}}, but expected {{/Two}}

**Nguyên nhân**: Conditional replacements phải được đóng theo **đúng thứ tự** mở.

**Sai:**
```html
{{#One}}
  {{#Two}}
    {{Three}}
  {{/One}}
{{/Two}}
```

**Đúng:**
```html
{{#One}}
  {{#Two}}
    {{Three}}
  {{/Two}}
{{/One}}
```

---

#### ❌ Found {{/Field}}, but missing '{{#Field}}' or '{{^Field}}'

**Nguyên nhân**: Closing tags phải có opening tags tương ứng.

**Sai:**
```html
{{Field}}
{{/Two}}
```

**Đúng:**
```html
{{Field}}
```

---

## 👯 Identical Front Sides

**Nguyên nhân**: Anki được cấu hình để tạo hai câu hỏi giống hệt nhau cho mỗi input. Điều này có thể xảy ra khi bạn thêm card type mới mà không điều chỉnh gì.

**Vấn đề**: 
- Cards giống nhau **gấp đôi khối lượng công việc**
- Làm cho lịch trình của Anki **kém hiệu quả hơn**

**Cách sửa**:
1. Mở [templates screen](https://docs.ankiweb.net/templates/intro.html#the-templates-screen)
2. Chọn một trong các duplicates ở phía trên
3. Dùng nút ở góc trên phải để **xóa card type** đã chọn

> ⚠️ Điều này sẽ xóa tất cả duplicate cards/notes đang sử dụng card type đó.

---

## 📄 Front of Card is Blank

**Nguyên nhân**: Anki hiển thị cards bằng cách kết hợp fields với template. Thông báo "blank front" có nghĩa:
- Không có field nào trong front template có text, **HOẶC**
- Có fields có text nhưng không được đưa vào front template

**Cách sửa**:
1. Edit card trên computer version
2. Click **Cards…**
3. Đảm bảo **ít nhất một field có text** được đưa vào front template
4. Có thể thêm fields bằng nút **Add Field**

### Lưu ý đặc biệt

| Trường hợp | Lưu ý |
|------------|-------|
| **Cloze note type** | Đảm bảo đã bao gồm một hoặc nhiều cloze deletions trong Text field, ví dụ: `{{c1::some cloze-deleted text}}` |
| **Type-in-the-answer** | Đảm bảo đã đưa thêm field khác vào front side |

---

## 🔲 No Cloze Filter on Cloze Note Type

Front và back templates của Cloze note type **phải có** [cloze](https://docs.ankiweb.net/editing.html#cloze-deletion) filter. Nếu thiếu, bạn cần thêm lại để Anki tạo cloze cards đúng cách.

---

### Single Empty Cards (Cards trống riêng lẻ)

Khi tạo clozes, mỗi số cloze được chuyển thành một card riêng biệt.

**Ví dụ** - tạo 3 cards:
```html
{{c1::This}} is a {{c2::sample}} {{c3::sentence}}.
```

Nếu sau đó bạn edit text và xóa hoặc thay đổi số cloze, card trước đó có thể trở nên trống.

**Ví dụ làm card 3 trống:**

```html
{{c1::This}} is a {{c2::sample}}
```

hoặc

```html
{{c1::This}} is a {{c2::sample}} {{c1::sentence}}.
```

**Cách sửa**:
1. Khi xem card 3, bạn sẽ thấy thông báo card trống
2. Vào **Tools menu** của main window
3. Chọn **Empty Cards** function để xóa blank cards

> ⚠️ **Quan trọng**: Kiểm tra các empty cards được báo cáo trước. Nếu không chắc chắn, tạo backup với **File > Export** trước khi tiếp tục.

---

### All Cloze Cards Empty (Tất cả cloze cards trống)

**Nguyên nhân**: Nếu vô tình sửa card template, có thể ngăn mọi cloze deletions hiển thị.

**Cách sửa**:

1. Edit một card có vấn đề
2. Ghi lại **tên của field đầu tiên** (thường là "Text")
3. Click nút **Cards…**
4. **Thay thế front text** bằng:

```html
{{cloze:Text}}
```

5. **Thay thế back text** bằng nội dung tương tự

> 💡 Nếu field có tên khác "Text", thay thế "Text" bằng tên field đó.

---

## 📚 Tài Nguyên Bổ Sung

- **[Hướng Dẫn Card Templates](./ANKI_CARD_TEMPLATES_GUIDE.md)** - Field Replacements và Card Generation
- **[Styling & HTML](./ANKI_STYLING_HTML_GUIDE.md)** - Tùy chỉnh giao diện cards
- **[Các AI Tools Để Tạo Anki Templates](./AI_TOOLS_FOR_ANKI_TEMPLATES.md)** - Hướng dẫn sử dụng AI
- **[Key Concepts](https://docs.ankiweb.net/getting-started.html#key-concepts)** - Khái niệm cơ bản trong Anki

---

## 📝 Tóm tắt các lỗi thường gặp

| Lỗi | Nguyên nhân | Cách sửa nhanh |
|-----|-------------|----------------|
| **Field không tồn tại** | Template chứa field không có | Xóa `{{Field}}` |
| **Thiếu `}}`** | Quên đóng ngoặc | Thêm `}}` |
| **Thiếu `{{/Field}}`** | Quên đóng conditional | Thêm `{{/Field}}` hoặc xóa opening tag |
| **Thứ tự đóng sai** | Nested conditionals đóng sai thứ tự | Đóng theo thứ tự LIFO (Last In, First Out) |
| **Front giống nhau** | Duplicate card types | Xóa card type trùng |
| **Front trống** | Không có field có text trên front | Thêm field có content vào front |
| **Cloze không hiển thị** | Thiếu cloze filter | Thêm `{{cloze:Text}}` |

---

**Chúc bạn sửa lỗi thành công! 🎉**

