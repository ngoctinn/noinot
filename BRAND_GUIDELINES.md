# Hướng Dẫn Quy Chuẩn Thương Hiệu & Bộ Logo "Nối Nốt" (Brand Guidelines)

Tài liệu quy chuẩn toàn diện về hệ thống nhận diện thương hiệu, biểu trưng (Logo) và tài nguyên thiết kế của dự án **Nối Nốt**.

---

## 1. Ý Nghĩa Biểu Trưng (Logo Concept & Symbolism)

- **Biểu tượng (Mark / Symbol)**: Được cấu thành từ 3 hình tròn tượng trưng cho các "Nốt" (Nodes / Connections / Notes).
- **Cầu nối mạng lưới (Bridge Network)**: Ba nốt liên kết hữu cơ theo dòng chảy mềm mại tạo thành dáng chữ **N** cách điệu (viết tắt của **Nối Nốt**).
- **Thông điệp cốt lõi**: Sự gắn kết, chuyển giao liền mạch, kết nối dữ liệu thông minh và lan tỏa giá trị bền vững.

---

## 2. Hệ Thống Màu Sắc Thương Hiệu (Brand Color Palette)

| Vai trò | Tên màu | HEX | RGB | Ứng dụng |
| :--- | :--- | :--- | :--- | :--- |
| **Chính (Primary)** | Primary Blue | `#2563EB` | `rgb(37, 99, 235)` | Nốt trung tâm, màu chủ đạo nhận diện, nút CTA chính |
| **Phụ (Secondary)** | Teal Green | `#10B981` | `rgb(16, 185, 129)` | Nốt bên trái, điểm nhấn tươi mới, biểu thị tăng trưởng |
| **Phụ (Secondary)** | Deep Blue | `#0284C7` | `rgb(2, 132, 199)` | Nốt bên phải, biểu thị sự tin cậy, vững chắc |
| **Chữ chính (Text)** | Slate Dark | `#0F172A` | `rgb(15, 23, 42)` | Màu chữ thương hiệu, tiêu đề, nền dark mode |
| **Chữ phụ (Text)** | Slate Gray | `#64748B` | `rgb(100, 116, 139)` | Màu chữ mô tả, phụ đề, đường viền phân cách |
| **Nền sáng (Bg)** | Light Gray | `#F1F5F9` | `rgb(241, 245, 249)` | Nền giao diện, card nền sáng nhẹ nhàng |

---

## 3. Kiểu Chữ Thương Hiệu (Typography)

- **Font chữ chính thức**: **Be Vietnam Pro**
- **Trọng số (Weights)**:
  - Tiêu đề & Wordmark: **Bold (700)** hoặc **SemiBold (600)**
  - Thân bài (Body): **Regular (400)** và **Medium (500)**
- **Đặc tính**: Thiết kế hiện đại mang chuẩn quốc tế, dấu thanh tiếng Việt được trau chuốt tinh tế, hiển thị rõ ràng trên mọi kích thước màn hình và thiết bị di động.

---

## 4. Danh Sách Tài Nguyên Logo Trong Thư Mục Dự Án

Toàn bộ tài nguyên đã được phân loại chuẩn tại thư mục `assets/logo/`:

```
assets/
├── logo/
│   ├── svg/                               # Định dạng Vector (Độ nét vô hạn, in ấn & web)
│   │   ├── logo-horizontal.svg            # Logo ngang chuẩn (Full Color trên nền sáng)
│   │   ├── logo-horizontal-dark.svg       # Logo ngang trên nền tối (#0F172A)
│   │   ├── logo-horizontal-white.svg      # Logo ngang đơn sắc trắng (nền trong suốt)
│   │   ├── logo-horizontal-black.svg      # Logo ngang đơn sắc đen (#0F172A)
│   │   ├── logo-horizontal-gray.svg       # Logo ngang đơn sắc xám (#64748B)
│   │   ├── logo-horizontal-outline.svg    # Logo ngang dạng viền nét (Outline)
│   │   ├── logo-horizontal-on-blue.svg    # Logo trắng trên nền Primary Blue
│   │   ├── logo-horizontal-on-teal.svg    # Logo trắng trên nền Teal Green
│   │   ├── logo-vertical.svg              # Logo bố cục dọc (Full Color)
│   │   ├── logo-vertical-dark.svg         # Logo dọc trên nền tối
│   │   ├── logo-vertical-white.svg        # Logo dọc đơn sắc trắng
│   │   ├── logo-symbol.svg                # Biểu tượng riêng (Full gradient)
│   │   ├── logo-symbol-white.svg          # Biểu tượng đơn sắc trắng
│   │   ├── logo-symbol-dark.svg           # Biểu tượng đơn sắc đen
│   │   ├── wordmark-dark.svg              # Chữ "Nối Nốt" riêng (màu tối)
│   │   ├── wordmark-white.svg             # Chữ "Nối Nốt" riêng (màu trắng)
│   │   ├── app-icon-primary.svg           # Vector App Icon gradient
│   │   ├── app-icon-white.svg             # Vector App Icon nền trắng
│   │   └── app-icon-dark.svg              # Vector App Icon nền tối
│   │
│   ├── png/                               # Định dạng Raster phân giải cao (Retina 2x)
│   │   ├── logo-horizontal.png            # 760x220px PNG trong suốt
│   │   ├── logo-horizontal-dark.png       # 760x220px PNG nền tối
│   │   ├── logo-horizontal-white.png      # 760x220px PNG trắng trong suốt
│   │   ├── logo-horizontal-black.png      # 760x220px PNG đen trong suốt
│   │   ├── logo-horizontal-gray.png       # 760x220px PNG xám
│   │   ├── logo-horizontal-outline.png    # 760x220px PNG outline
│   │   ├── logo-horizontal-on-blue.png    # 760x220px PNG nền xanh
│   │   ├── logo-horizontal-on-teal.png    # 760x220px PNG nền xanh ngọc
│   │   ├── logo-vertical.png              # 440x420px PNG dọc trong suốt
│   │   ├── logo-vertical-dark.png         # 440x420px PNG dọc nền tối
│   │   ├── logo-symbol.png                # 304x200px PNG biểu tượng riêng
│   │   ├── logo-symbol-white.png          # 304x200px PNG biểu tượng trắng
│   │   ├── wordmark-dark.png              # 460x140px PNG chữ riêng
│   │   ├── app-icon-1024.png              # 1024x1024px chuẩn App Store / Google Play
│   │   ├── app-icon-512.png               # 512x512px
│   │   ├── app-icon-192.png               # 192x192px Android home screen
│   │   ├── app-icon-ios.png               # 512x512px phiên bản nền trắng
│   │   ├── app-icon-dark.png              # 512x512px phiên bản Dark mode
│   │   ├── og-image-1200x630.png          # Social Media Share Card (Facebook, Zalo, Twitter)
│   │   ├── favicon-32x32.png
│   │   └── favicon-16x16.png
│   │
│   └── favicon/                           # Gói Favicon cho Website
│       ├── favicon.ico                    # Multi-size ICO (16x16, 32x32, 48x48)
│       ├── apple-touch-icon.png           # 180x180px chuẩn iOS Safari
│       ├── favicon-48x48.png
│       ├── favicon-32x32.png
│       └── favicon-16x16.png
├── fonts/                                 # Bộ font Be Vietnam Pro bản quyền Google
└── brand/
    └── showcase-preview.png               # Ảnh chụp tổng quan trang trưng bày
```

---

## 5. Quy Chuẩn Sử Dụng (Rules & Guidelines)

### A. Khoảng Cách An Toàn (Clear Space)
- Xung quanh logo luôn phải duy trì một khoảng không gian trống tối thiểu bằng bán kính của nốt biểu tượng ($x \approx 38px$).
- Không đặt chữ, hình ảnh hoặc các yếu tố đồ họa khác lấn chiếm vùng an toàn này.

### B. Kích Thước Tối Thiểu (Minimum Size)
- **Logo ngang**: Chiều rộng tối thiểu $80\text{px}$ (màn hình) hoặc $25\text{mm}$ (in ấn).
- **Logo dọc**: Chiều rộng tối thiểu $60\text{px}$ (màn hình) hoặc $20\text{mm}$ (in ấn).
- **Biểu tượng (Icon)**: Chiều rộng tối thiểu $24\text{px}$ (màn hình) hoặc $8\text{mm}$ (in ấn). Dưới $24\text{px}$ nên dùng gói `favicon-16x16.png`.

### C. Quy Tắc Nên Làm & Cấm Kỵ (Do's & Don'ts)
- **NÊN**:
  - Dùng bản SVG cho mọi ứng dụng web, app và in ấn để đảm bảo chất lượng sắc nét tuyệt đối.
  - Sử dụng phiên bản logo trắng đơn sắc trên các nền có màu đậm hoặc nền ảnh đã làm mờ/lọc tối.
  - Sử dụng phiên bản Dark Mode trên giao diện tối.
- **KHÔNG ĐƯỢC**:
  - Không kéo giãn, bóp méo tỉ lệ ngang dọc của logo.
  - Không thay đổi màu sắc hoặc trật tự chuyển màu của 3 nốt.
  - Không thêm hiệu ứng bóng đổ lòe loẹt, viền phát sáng (stroke/glow) làm biến dạng tính tối giản hiện đại.
  - Không đặt logo màu chuẩn trên nền đỏ, vàng, cam hoặc ảnh nền phức tạp làm mất độ tương phản.
