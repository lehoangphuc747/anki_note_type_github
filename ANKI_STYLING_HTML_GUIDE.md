# 🎨 Styling & HTML Trong Anki

[← Quay lại Trang chủ](./README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

**Nguồn**: [Anki Manual - Styling & HTML](https://docs.ankiweb.net/templates/styling.html)

---

## 📑 Mục lục

- [Card Styling](#-card-styling)
- [Image Resizing](#️-image-resizing)
- [Field Styling](#-field-styling)
- [Audio Replay Buttons](#-audio-replay-buttons)
- [Text Direction](#-text-direction)
- [Other HTML](#-other-html)
- [Browser Appearance](#️-browser-appearance)
- [Platform-Specific CSS](#-platform-specific-css)
- [Installing Fonts](#-installing-fonts)
- [Night Mode](#-night-mode)
- [Fading and Scrolling](#-fading-and-scrolling)
- [Javascript](#-javascript)

---

## 🎨 Card Styling

Video hướng dẫn: [Styling Cards](http://www.youtube.com/watch?v=F1j1Zx0mXME&yt:cc=on) (Video hiển thị giao diện Anki 2.0 nhưng các khái niệm vẫn tương tự)

Phần styling của Cards screen có thể truy cập bằng cách click nút **"Styling"** bên cạnh nút "Back Template". Tại đây, bạn có thể thay đổi màu nền, font mặc định, căn chỉnh text, v.v.

### Các tùy chọn tiêu chuẩn

| Property | Mô tả |
|----------|-------|
| **font-family** | Tên font sử dụng. Nếu font có khoảng trắng như "MS Unicode", cần đặt trong dấu ngoặc kép: `font-family: "MS Unicode";` |
| **font-size** | Kích thước font (pixels). Giữ nguyên `px` ở cuối khi thay đổi |
| **text-align** | Căn chỉnh text: `center`, `left`, hoặc `right` |
| **color** | Màu text. Dùng tên màu đơn giản ("blue", "lightyellow") hoặc [HTML color codes](https://htmlcolorcodes.com/) |
| **background-color** | Màu nền của card |

### CSS tùy chỉnh

Bất kỳ CSS nào cũng có thể đặt trong phần styling - người dùng nâng cao có thể thêm background image hoặc gradient.

### Styling riêng cho từng card

Styling được chia sẻ giữa tất cả cards của note type đó. Tuy nhiên, có thể chỉ định styling riêng cho từng card:

```css
.card {
  background-color: yellow;
}
.card1 {
  background-color: blue;
}
```

Ví dụ trên sẽ dùng nền vàng cho tất cả cards trừ card đầu tiên (nền xanh).

---

## 🖼️ Image Resizing

Anki mặc định thu nhỏ hình ảnh để vừa màn hình. Để tắt tính năng này:

```css
img {
  max-width: none;
  max-height: none;
}
```

### Khắc phục lỗi trên AnkiDroid

AnkiDroid đôi khi [gặp vấn đề scale images](https://github.com/ankidroid/Anki-Android/issues/3612). Dùng `!important`:

```css
img {
  max-width: 300px !important;
  max-height: 300px !important;
}
```

### Không ảnh hưởng đến icon star (marked cards)

```css
img#star {
  /* styling riêng cho star icon */
}
```

### Debug styling với Chrome

Có thể khám phá styling của cards interactively bằng Chrome: [WebView Changes](https://addon-docs.ankiweb.net/porting2.0.html#webview-changes)

> 💡 **Anki 2.1.50+** hỗ trợ resize hình ảnh ngay trong editor.

---

## 🔤 Field Styling

Styling mặc định áp dụng cho toàn bộ card. Bạn có thể tạo styling riêng cho các fields hoặc phần cụ thể của card - **đặc biệt quan trọng khi học ngoại ngữ** vì Anki đôi khi không hiển thị đúng ký tự nếu không chọn font phù hợp.

### Ví dụ: Dùng font Thai cho field "Expression"

Template ban đầu:

```html
What is {{Expression}}?

{{Notes}}
```

### Bước 1: Wrap text với HTML

Thêm `<div class=mystyle1>` trước và `</div>` sau text muốn style:

**Style toàn bộ câu hỏi:**

```html
<div class=mystyle1>What is {{Expression}}?</div>

{{Notes}}
```

**Chỉ style field Expression:**

```html
What is <div class=mystyle1>{{Expression}}</div>?

{{Notes}}
```

### Bước 2: Thêm CSS vào Styling section

```css
.card {
  font-family: arial;
  font-size: 20px;
  text-align: center;
  color: black;
  background-color: white;
}

.mystyle1 {
  font-family: ayuthaya;
}
```

Có thể thêm nhiều properties:

```css
.mystyle1 {
  font-family: ayuthaya;
  font-size: 30px;
}
```

> 💡 Có thể bundle custom fonts với deck - xem phần [Installing Fonts](#-installing-fonts).

---

## 🔊 Audio Replay Buttons

Khi cards có audio hoặc TTS, Anki hiển thị nút replay. Có thể ẩn nút này trong preferences screen.

### Tùy chỉnh giao diện nút replay

```css
.replay-button svg {
  width: 20px;
  height: 20px;
}
.replay-button svg circle {
  fill: blue;
}
.replay-button svg path {
  stroke: white;
  fill: green;
}
```

---

## ↔️ Text Direction

Với ngôn ngữ viết từ phải sang trái (Arabic, Hebrew):

### Thay đổi toàn bộ card

```css
.card {
  direction: rtl;
}
```

### Chỉ thay đổi một số fields

```html
<div dir="rtl">{{Front}}</div>
```

> 📖 Để thay đổi direction trong editor, xem phần [editing](https://docs.ankiweb.net/editing.html#customizing-fields).

---

## 🌐 Other HTML

Templates có thể chứa **bất kỳ HTML nào** - tất cả layout của web pages đều có thể dùng cho cards:

- Tables
- Lists
- Images
- Links đến trang ngoài
- v.v.

**Ví dụ**: Dùng tables để hiển thị front và back ở bên trái/phải thay vì trên/dưới.

> 📖 Có nhiều hướng dẫn HTML tốt trên web nếu bạn muốn tìm hiểu thêm.

---

## 🖥️ Browser Appearance

Nếu card templates phức tạp, có thể khó đọc cột Question và Answer trong [card list](https://docs.ankiweb.net/browsing.html#cardnote-table). Tùy chọn **"Browser Appearance"** cho phép định nghĩa template riêng chỉ dùng trong browser.

- Cú pháp giống standard card templates
- Có thể chỉ hiển thị các fields quan trọng và thay đổi thứ tự

> 💡 Nếu text ở cột question lặp lại ở đầu cột answer, Anki sẽ chỉ hiển thị phần khác biệt trong cột answer.

---

## 📱 Platform-Specific CSS

Anki định nghĩa các CSS classes đặc biệt cho các platforms khác nhau:

```css
/* Windows */
.win .example {
  font-family: "Example1";
}

/* macOS */
.mac .example {
  font-family: "Example2";
}

/* Linux desktops */
.linux:not(.android) .example {
  font-family: "Example3";
}

/* both Linux desktops, and Android devices */
.linux .example {
  font-family: "Example4";
}

/* both Android and iOS */
.mobile .example {
  font-family: "Example5";
}

/* iOS */
.iphone .example,
.ipad .example {
  font-family: "Example6";
}

/* Android */
.android .example {
  font-family: "Example7";
}
```

Trong template:

```html
<div class="example">{{Field}}</div>
```

> 📖 Có thể dùng `.gecko`, `.opera`, `.ie` cho các browsers trên AnkiWeb. Xem [danh sách đầy đủ](http://rafael.adm.br/css_browser_selector/).

---

## 🔤 Installing Fonts

Có thể cài fonts trực tiếp vào Anki - hữu ích khi:
- Dùng Anki trên máy tính công ty/trường học (không có quyền cài font)
- Dùng Anki trên mobile

**Formats hỗ trợ**: TrueType (.ttf), OpenType (.otf), Web Open Font Format (.woff), v.v.

### Bước 1: Thêm Font vào Media Folder

1. **Đổi tên file** - thêm underscore ở đầu: `Arial.ttf` → `_arial.ttf`
   - Underscore báo cho Anki biết file này dùng trong template, không nên xóa khi check unused media
2. Mở **Anki application data folder** (xem [File Locations](https://docs.ankiweb.net/files.html#file-locations)), vào profile folder (e.g., "User 1")
3. Kéo file đã đổi tên vào folder **collection.media**

### Bước 2: Cập nhật Template

1. Click **Add** → chọn note type muốn thay đổi
2. Click **Cards**
3. Trong Styling section, thêm vào cuối (sau ký tự "}" cuối cùng):

```css
@font-face {
  font-family: myfont;
  src: url("_arial.ttf");
}
```

> ⚠️ Chỉ thay đổi phần "arial", giữ nguyên "myfont".

### Bước 3: Sử dụng Font

**Cho toàn bộ card**: Đổi `font-family` trong `.card` thành "myfont"

**Cho fields cụ thể**: Xem phần [Field Styling](#-field-styling)

> ⚠️ **Quan trọng**: Tên file phải khớp chính xác! Nếu file là `arial.TTF` mà viết `arial.ttf` trong template sẽ không hoạt động.

---

## 🌙 Night Mode

Tùy chỉnh giao diện khi Night Mode được bật:

### Background nhạt hơn

```css
.card.nightMode {
  background-color: #555;
}
```

### Text màu vàng khi Night Mode

```css
.nightMode .myclass {
  color: yellow;
}
```

---

## 📜 Fading and Scrolling

### Scrolling

Anki tự động scroll đến answer. Tìm element có `id=answer` và scroll đến đó.

- Đặt id trên element khác để điều chỉnh vị trí scroll
- Xóa `id=answer` để tắt scrolling

### Fading

Mặt question của card fade in mặc định. Điều chỉnh delay:

```html
<script>
  qFade = 100;
  if (typeof anki !== "undefined") anki.qFade = qFade;
</script>
```

- `100` (milliseconds) là mặc định
- Đặt `0` để tắt fading

---

## 💻 Javascript

Vì Anki cards được xử lý như web pages, có thể embed Javascript vào cards qua card template.

Tham khảo: [Card Templates User Input Guide](https://forums.ankiweb.net/t/card-templates-user-input-101-buttons-keyboard-shortcuts-etc-guide/13756)

> ⚠️ **Cảnh báo**: Javascript là tính năng nâng cao và nhiều thứ có thể xảy ra lỗi. **Javascript functionality được cung cấp không có hỗ trợ hoặc bảo hành**.

### Lưu ý quan trọng

1. **Test across platforms**: Mỗi Anki client có thể implement card display khác nhau
2. **Dùng `document.getElementById()`** thay vì `document.write()` vì nhiều clients giữ webpage chạy liên tục và cập nhật động
3. **`window.alert` có thể không khả dụng**
4. **Xem lỗi trong console**: [Console Output](https://addon-docs.ankiweb.net/console-output.html#console-output)
5. **Debug với Chrome**: [Inspector](https://addon-docs.ankiweb.net/debugging.html#webviews)

---

## 📚 Tài Nguyên Bổ Sung

- **[Hướng Dẫn Card Templates](./ANKI_CARD_TEMPLATES_GUIDE.md)** - Field Replacements và Card Generation
- **[Checks and Errors](./ANKI_CHECKS_ERRORS_GUIDE.md)** - Các lỗi thường gặp và cách khắc phục
- **[Các AI Tools Để Tạo Anki Templates](./AI_TOOLS_FOR_ANKI_TEMPLATES.md)** - Hướng dẫn sử dụng AI
- **[UI Style Categories](./UI_STYLE_CATEGORIES.md)** - Tham khảo các phong cách thiết kế UI
- **[HTML Color Codes](https://htmlcolorcodes.com/)** - Chọn màu sắc cho cards

---

**Chúc bạn tạo được những card templates đẹp mắt! 🎉**

