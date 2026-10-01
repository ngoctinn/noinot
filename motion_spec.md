# Motion Specification: Nối Nốt Logo

## 1. Brand Brief & Motion Personality

- **Brand**: Nối Nốt (Shared Context Platform)
- **Concept**: Hai chữ cái N liên kết với nhau qua các node mạng / nốt nhạc (bottom-left node và top-right node), tượng trưng cho việc nối kết liền mạch các domain và dữ liệu trong đời sống.
- **Personality Words**:
  1. **Connected** (Liên kết): Các node phát tín hiệu, hút và kết nối hai glyph N lại với nhau.
  2. **Precise** (Chính xác): Hình học sắc nét, các nét trượt vào khớp vị trí không sai lệch 1 pixel.
  3. **Swift** (Nhanh nhẹn, dứt khoát): Chuyển động gọn gàng, giảm thiểu độ trễ, gia tốc mượt mà.

---

## 2. Animation Timeline (Golden Ratio 20% : 50% : 30%)

- **Total Duration**: `1600ms`
- **Pacing Structure**:
  - `0ms - 320ms (0% - 20%)`: **Anticipation**.
    - Hai node tròn (`#node-left`, `#node-right`) xuất hiện với hiệu ứng scale pop + pulse nhẹ.
  - `320ms - 1120ms (20% - 70%)`: **Main Action**.
    - Thân chữ N bên trái (`#glyph-left-body`) bung nở và phóng lên từ node trái (`transform-origin: 380px 1581px`).
    - Thân chữ N bên phải (`#glyph-right-body`) bung nở và phóng xuống từ node phải (`transform-origin: 1668px 467px`).
    - Hai nét đan chéo gặp nhau ở trung tâm (1024, 1024), khóa liên kết.
  - `1120ms - 1600ms (70% - 100%)`: **Follow-through & Settle**.
    - Micro-overshoot nhẹ (1.02x -> 1.0x).
    - Toàn bộ logo ổn định về trạng thái tĩnh chuẩn xác (Final Frame Contract đạt 100% khớp vector).

---

## 3. Easing Tokens (Literal values in CSS Keyframes)

- **Anticipation**: `cubic-bezier(0.34, 1.56, 0.64, 1)` (elastic overshoot pop)
- **Action**: `cubic-bezier(0.16, 1, 0.3, 1)` (smooth deceleration ease-out)
- **Settle**: `cubic-bezier(0.25, 1, 0.5, 1)` (gentle landing)

---

## 4. Disney Principles Applied

1. **Staging**: Node khởi phát trước, dẫn mắt người xem theo đường chéo từ góc dưới-trái lên góc trên-phải.
2. **Anticipation**: Node co nhẹ rồi bung nở trước khi kéo thân chữ cái chuyển động.
3. **Slow In & Slow Out**: Sử dụng đường cong bezier mượt mà, không giật cục, không dùng linear easing.
4. **Follow Through & Overlapping Action**: Node trái bung trước node phải ~80ms; thân chữ kéo theo sau node tạo cảm giác có quán tính tự nhiên.
5. **Appeal**: Đồ họa vector hình học tối giản, sạch sẽ, không răng cưa.
