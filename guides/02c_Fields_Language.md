# 🌐 Hỗ Trợ Ngôn Ngữ (RTL & Furigana)

[← Quay lại Trang chủ](../README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

---

## 🔄 RTL Languages (Right-to-Left)

Nếu bạn học các ngôn ngữ viết từ phải sang trái như tiếng Ả Rập (Arabic), Do Thái (Hebrew), Ba Tư (Persian), bạn cần báo cho trình duyệt biết hướng văn bản đúng.

### Cú pháp

Bao quanh field bằng thẻ `div` với thuộc tính `dir=rtl`:

```html
<div dir=rtl>{{FieldThatHasRTLTextInIt}}</div>
```

---

## 🇯🇵 Ruby Characters / Furigana

Anki hỗ trợ hiển thị Furigana (chữ kana nhỏ trên đầu chữ Hán) cho tiếng Nhật.

### Cú pháp nhập liệu
Trong field, bạn nhập theo định dạng: `Kanji[Kana]` (có khoảng trắng trước Kanji nếu cần tách từ).

Ví dụ: `日本語[にほんご]`

### Các bộ lọc hiển thị

| Raw Text (Trong field) | Filter (Trong template) | Kết quả hiển thị | Giải thích |
|------------------------|-------------------------|------------------|------------|
| `日本語[にほんご]` | `{{furigana:MyField}}` | 日本語 (với にほんご ở trên) | Hiển thị chuẩn kiểu Ruby |
| `日本語[にほんご]` | `{{kana:MyField}}` | にほんご | Chỉ hiển thị Kana |
| `日本語[にほんご]` | `{{kanji:MyField}}` | 日本語 | Chỉ hiển thị Kanji (ẩn Kana) |

---

### ⬅️ [Bài trước: Dictionary Links & Media](./02b_Fields_Links_Media.md) | [Bài tiếp theo: Type Answer](./02d_Fields_TypeAnswer.md) ➡️

