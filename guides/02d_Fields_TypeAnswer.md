# ⌨️ Type Answer (Gõ Đáp Án)

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## Giới thiệu

Tính năng **Type Answer** cho phép bạn gõ câu trả lời trực tiếp vào card và Anki sẽ so sánh với đáp án đúng, tô màu xanh (đúng) hoặc đỏ (sai) cho từng ký tự.

Video hướng dẫn: [Typing in the Answer](http://www.youtube.com/watch?v=5tYObQ3ocrw&yt:cc=on)

---

## Cú pháp cơ bản

Để bật tính năng này, bạn cần:
1. Thêm `type:` vào trước tên field đáp án trong **Front Template**.
2. Đảm bảo field đó cũng có mặt ở Back Template (thường Anki tự xử lý phần hiển thị kết quả).

**Ví dụ:**

Front Template:
```html
{{Native Word}}

{{type:Foreign Word}}
```

Back Template:
```html
{{FrontSide}}

<hr id=answer>

{{Foreign Word}}
```

---

## Type Answer cho Cloze

Với Cloze deletion, cú pháp hơi khác một chút:

```html
{{cloze:Text}}
{{type:cloze:Text}}
{{Extra}}
```

---

## Tùy chỉnh giao diện (Styling)

Bạn có thể chỉnh font chữ và kích thước của ô nhập liệu bằng CSS:

**Chỉnh font:**
```css
code#typeans { font-family: "myfontname"; }
```

**Chỉnh kích thước:**
```css
#typeans { font-size: 50px !important; }
```

**Màu sắc kết quả:**
Anki sử dụng các class CSS sau để hiển thị kết quả so sánh:
- `.typeGood`: Ký tự đúng (màu xanh lá)
- `.typeBad`: Ký tự sai (màu đỏ)
- `.typeMissed`: Ký tự bị thiếu (màu xám)

---

## Bỏ qua dấu accent (Type Answer Ignore Accents)

**Accent là gì?** Accent (dấu) là các ký hiệu trên chữ cái để chỉ cách phát âm (như `é`, `ü`, `ñ`, dấu thanh tiếng Việt).

**Khi nào dùng?** Khi bạn muốn Anki chấm đúng ngay cả khi bạn gõ thiếu dấu (ví dụ gõ "cafe" thay vì "café").

**Cú pháp:**
Thay `type:` bằng `type:nc:` (nc = no check accents).

```html
{{type:nc:Foreign Word}}
```

**Ví dụ so sánh:**

| Field đích | Bạn gõ | Chế độ thường (`type:`) | Chế độ bỏ qua dấu (`type:nc:`) |
|------------|--------|-------------------------|--------------------------------|
| `élite` | `elite` | ❌ Sai (thiếu `é`) | ✅ Đúng |
| `Nguyễn` | `Nguyen` | ❌ Sai (thiếu dấu) | ✅ Đúng |

> 💡 **Lưu ý**: Tính năng này hữu ích để tập trung học từ vựng thay vì bị phạt vì lỗi chính tả nhỏ. Tuy nhiên, nếu bạn đang học viết chính xác, hãy dùng chế độ thường.

---

### ⬅️ [Bài trước: Hỗ Trợ Ngôn Ngữ](./02c_Fields_Language.md) | [Bài tiếp theo: Special Fields](./03_SpecialFields.md) ➡️

