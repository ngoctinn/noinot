# Nối Nốt — Showcase Poster Source

Thư mục này chứa toàn bộ mã nguồn HTML/CSS và công cụ để tái render (re-render) ấn phẩm bìa (poster / README banner) cho dự án **Nối Nốt**.

## Cấu hình ấn phẩm

- **Loại hình**: Poster / Banner Social & README
- **Kích thước gốc**: `1200x630` px (Render ở tỷ lệ 2× Retina: `2400x1260` px)
- **Ngôn ngữ hỗ trợ**: Tiếng Việt (`vi`, mặc định), Tiếng Anh (`en`)
- **Font chữ**: Inter (Google Fonts, hỗ trợ toàn diện tiếng Việt)
- **Visuals**: Logo vector hình học gốc của Nối Nốt (`node-left [380, 1581]`, `node-right [1668, 467]`)

---

## Cài đặt môi trường

```bash
npm install
```

Yêu cầu trình duyệt Chrome, Chromium hoặc Microsoft Edge đã cài đặt trên máy. Nếu trình duyệt nằm ở đường dẫn đặc biệt, đặt biến môi trường `CHROME_PATH`.

---

## Quy trình Re-render

### 1. Đóng gói mã nguồn thành tệp độc lập (Inline Assets)

```bash
node inline-assets.mjs --src poster.html --out dist/poster.html
```

### 2. Xuất ảnh PNG (Độ phân giải 2×: 2400×1260)

```bash
# Bản tiếng Việt (mặc định)
node capture.mjs --mode poster --src dist/poster.html --size 1200x630 --format png --lang vi --out ../noinot-poster.png

# Bản tiếng Anh (nếu cần)
node capture.mjs --mode poster --src dist/poster.html --size 1200x630 --format png --lang en --out ../noinot-poster-en.png
```

### 3. Xuất file PDF (nếu cần in ấn hoặc lưu trữ vector)

```bash
node capture.mjs --mode poster --src dist/poster.html --size 1200x630 --format pdf --lang vi --out ../noinot-poster.pdf
```

---

## Xem thử trực tiếp (Live Preview)

Mở `dist/poster.html` trong bất kỳ trình duyệt nào:
- Mặc định: `dist/poster.html`
- Chuyển ngôn ngữ: `dist/poster.html?lang=en`
- Thay đổi kích thước: `dist/poster.html?size=1200x630` (hoặc `?size=A4`)
