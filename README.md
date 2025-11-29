# Anki Note Type Templates

Repository chia sẻ template Anki và tài liệu hướng dẫn học thiết kế card.

> **Tác giả**: Admin Phúc từ AnkiVN

---

## ⚠️ Lưu Ý: Phần Mềm Cần Cài Đặt Trước

Trước khi bắt đầu học thiết kế card templates, bạn cần chuẩn bị các công cụ sau:

### 📝 Editor & Công Cụ Phát Triển

- **[Visual Studio Code (VS Code)](https://code.visualstudio.com/)** - Editor code miễn phí, khuyên dùng để chỉnh sửa templates
- **[Anki Editor Extension](https://marketplace.visualstudio.com/items?itemName=pedro-bronsveld.anki-editor)** - Extension cho VS Code để hỗ trợ chỉnh sửa Anki templates với syntax highlighting

### 🔐 Tài Khoản Cần Thiết

- **Tài khoản GitHub** - Để sử dụng GitHub Copilot (AI coding assistant)
- **Tài khoản Google** - Để sử dụng AI Studio (công cụ AI miễn phí từ Google)

### 🔌 Anki Addons (Quan Trọng)

Cài đặt các addons sau trong Anki để hỗ trợ việc phát triển và test templates:

1. **[Add-on 31746032](https://ankiweb.net/shared/info/31746032)** - (Xem mô tả addon tại link)
2. **[Add-on 2055492159](https://ankiweb.net/shared/info/2055492159)** - (Xem mô tả addon tại link)
3. **[Add-on 571150035](https://ankiweb.net/shared/info/571150035)** - (Xem mô tả addon tại link)

> 💡 **Hướng dẫn cài addon**: Vào Anki → Tools → Add-ons → Get Add-ons → Nhập code số (ví dụ: `31746032`) → OK

---

## 📚 Lộ Trình Học Thiết Kế Card

Các bài hướng dẫn đã được phân loại chi tiết trong thư mục `guides`. Nếu bạn mới bắt đầu, hãy học theo thứ tự này:

### 1. Cơ Bản
- **[Card Templates Intro](./guides/01_Templates_Intro.md)** - Tổng quan về Card Templates
- **[Field Replacements (Cơ Bản)](./guides/02_Fields_Basics.md)** - Cách chèn dữ liệu, xuống dòng
- **[Hint Fields](./guides/02a_Fields_Hint.md)** - Tạo gợi ý ẩn/hiện
- **[Dictionary Links & Media](./guides/02b_Fields_Links_Media.md)** - Link tra từ điển và chèn ảnh tĩnh
- **[Language Support](./guides/02c_Fields_Language.md)** - Hỗ trợ tiếng Nhật (Furigana) và RTL
- **[Type Answer](./guides/02d_Fields_TypeAnswer.md)** - Tính năng gõ và kiểm tra đáp án
- **[Special Fields](./guides/03_SpecialFields.md)** - Các field đặc biệt (Tags, Deck, Flag...)
- **[Card Generation (Cơ Bản)](./guides/04_CardGen_Basics.md)** - Reverse Cards, Empty/Blank Cards
- **[Conditional Replacement](./guides/04a_CardGen_Conditional.md)** - Logic điều kiện `{{#Field}}`
- **[Cloze Templates](./guides/04b_CardGen_Cloze.md)** - Logic tạo card điền vào chỗ trống

### 2. Tính Năng
- **[Text to Speech (TTS)](./guides/05_TTS.md)** - Thêm giọng đọc tự động

### 3. Giao Diện & Nâng Cao
- **[Styling & HTML (Cơ Bản)](./guides/06_Styling_Basics.md)** - CSS cơ bản, chỉnh ảnh, font field
- **[Styling Nâng Cao](./guides/06a_Styling_Advanced.md)** - Audio button, Fading, Scrolling
- **[Platform & Night Mode](./guides/06b_Styling_Platform.md)** - Tùy biến cho Mobile/Desktop, Chế độ tối
- **[Cài Đặt Fonts](./guides/06c_Styling_Fonts.md)** - Hướng dẫn nhúng font tùy chỉnh
- **[Javascript](./guides/06d_Styling_JS.md)** - Lưu ý khi dùng JS trong Anki
- **[Checks and Errors](./guides/07_Errors.md)** - Sửa lỗi thường gặp

---

## 🛠️ Công Cụ & Tài Nguyên

- **[Template Mẫu (2026)](./%28Anki%29%20Template%20h%E1%BB%8Dc%20t%E1%BB%AB%20v%E1%BB%B1ng%20c%E1%BB%A7a%20Admin%20Ph%C3%BAc%20%5B2026%5D/README.md)** - Template học từ vựng có sẵn
- **[Phong Cách UI](./Tools_UI.md)** - Gợi ý phong cách thiết kế
- **[Công Cụ AI](./Tools_AI.md)** - Cách dùng AI để tạo template
- **[AnkiEco Templates](https://github.com/ikkz/anki-eco)** - Nguồn template tối giản, hiện đại và ấn tượng

---

**Languages**: [English](./README_EN.md) | Tiếng Việt
