# 🔊 Text to Speech (TTS) Trong Anki

[← Quay lại Trang chủ](./README.md)

**📅 Cập nhật lần cuối**: Tháng 1, 2025

**Nguồn**: [Anki Manual - Templates](https://docs.ankiweb.net/templates/fields.html)

---

*Yêu cầu: Anki 2.1.20+, AnkiMobile 2.0.56+, AnkiDroid 2.17+*

**TTS là gì?** Text to Speech (chuyển văn bản thành giọng nói) - Anki sẽ tự động đọc nội dung field bằng giọng nói nhân tạo.

---

## Cú pháp cơ bản

Cấu trúc: `{{tts [ngôn_ngữ]:[tên_field]}}`

**Ví dụ đơn giản nhất** - Đọc field "Front" bằng giọng US English:

```html
{{tts en_US:Front}}
```

**Giải thích**:
- `tts` = Text to Speech (báo cho Anki biết đây là lệnh đọc)
- `en_US` = Ngôn ngữ và vùng (en = English, US = United States)
- `Front` = Tên field cần đọc

---

## Xem danh sách voices có sẵn

Không biết có voices nào? Thêm dòng này vào template để xem danh sách:

```html
{{tts-voices:}}
```

Khi review card, bạn sẽ thấy danh sách tất cả voices có sẵn trên thiết bị của mình.

---

## Chọn voice cụ thể

Nếu có nhiều voices cho cùng một ngôn ngữ, bạn có thể chỉ định voice ưa thích:

```html
{{tts ja_JP voices=Apple_Otoya,Microsoft_Haruka:Field}}
```

**Cách hoạt động**: 
- Liệt kê nhiều voices, cách nhau bằng dấu phẩy
- Anki sẽ chọn **voice đầu tiên có sẵn** trên thiết bị
- Nếu `Apple_Otoya` có → dùng nó
- Nếu không có → dùng `Microsoft_Haruka`

---

## Điều chỉnh tốc độ đọc

Mặc định TTS đọc với tốc độ 1.0 (bình thường). Bạn có thể thay đổi:

```html
{{tts fr_FR speed=0.8:SomeField}}
```

**Giải thích**:
- `speed=0.8` = Đọc chậm hơn 20% (0.8 = 80% tốc độ bình thường)
- `speed=1.2` = Đọc nhanh hơn 20% (1.2 = 120% tốc độ bình thường)
- `speed=0.5` = Đọc rất chậm (50% tốc độ)
- `speed=2.0` = Đọc rất nhanh (200% tốc độ)

---

## TTS cho Cloze (chỉ đọc phần bị ẩn)

Với cloze deletion, bạn có thể chỉ đọc phần bị ẩn, không đọc toàn bộ:

```html
{{tts en_US:cloze-only:Text}}
```

**Ví dụ**:
- Field "Text" có: `I love {{c1::reading}} books`
- Bình thường: Đọc "I love reading books"
- Với `cloze-only`: Chỉ đọc "reading"

---

## TTS cho nhiều fields hoặc text tĩnh (*Anki 2.1.50+*)

Muốn đọc nhiều fields hoặc thêm text tĩnh? Dùng tag format:

```html
[anki:tts lang=en_US] This text should be read. Here is {{Field1}} and {{Field2}}[/anki:tts]

This is other text on the template. It is outside of the tags so it should not be read.
```

**Giải thích**:
- `[anki:tts lang=en_US]` = Bắt đầu TTS (mở tag)
- Mọi thứ bên trong sẽ được đọc
- `[/anki:tts]` = Kết thúc TTS (đóng tag)
- Text ngoài tag sẽ **không** được đọc

**Ví dụ thực tế**:

```html
[anki:tts lang=vi_VN] Từ: {{Word}}. Nghĩa: {{Meaning}}[/anki:tts]
```

---

## 📝 Các mã ngôn ngữ phổ biến

| Mã | Ngôn ngữ | Ví dụ |
|----|----------|-------|
| `en_US` | English (US) | {{tts en_US:Front}} |
| `en_GB` | English (UK) | {{tts en_GB:Front}} |
| `vi_VN` | Tiếng Việt | {{tts vi_VN:Front}} |
| `ja_JP` | Tiếng Nhật | {{tts ja_JP:Front}} |
| `zh_CN` | Tiếng Trung (TQ) | {{tts zh_CN:Front}} |
| `ko_KR` | Tiếng Hàn | {{tts ko_KR:Front}} |
| `fr_FR` | Tiếng Pháp | {{tts fr_FR:Front}} |
| `es_ES` | Tiếng Tây Ban Nha | {{tts es_ES:Front}} |
| `de_DE` | Tiếng Đức | {{tts de_DE:Front}} |

---

### ⬅️ [Bài trước: Cloze Templates](./04b_CardGen_Cloze.md) | [Bài tiếp theo: Styling & HTML](./06_Styling.md) ➡️
