# Tính toán điện nhà máy

Công cụ web tính toán hệ thống điện cho nhà máy. Toàn bộ nằm trong **một file `index.html`**: không cần cài đặt, không cần máy chủ. Chạy được trên máy tính, điện thoại và máy tính bảng. Số liệu nhập được lưu ngay trên trình duyệt của thiết bị.

## Các module

| Nhóm | Module | Nội dung chính |
|---|---|---|
| Nguồn & trung thế | **MBA** – Phụ tải & chọn máy biến áp | Bảng phụ tải, Ku, Ks, công suất trước/sau bù, chọn số lượng và công suất MBA, tổn thất điện năng/năm |
| | **TT** – Tủ trung thế & cáp trung thế | Ur, BIL, Ik tủ, cầu chì hoặc VCB + gợi ý chỉnh định rơ le 50/51, cáp trung thế, chống sét van |
| | **Ik** – Ngắn mạch hạ thế | I"k3, ip, I"k2 lần lượt qua MBA, thanh cái, cáp; Icu gợi ý tại từng tủ |
| Phân phối hạ thế | **TC** – Thanh cái | Kích thước, số thanh/pha, ổn định nhiệt, ổn định động, thanh N/PE |
| | **CÁP** – Tiết diện cáp & CB | Dòng cho phép có hiệu chỉnh, sụt áp, ngắn mạch, PE, cắt nhanh khi chạm vỏ, sóng hài bậc 3 |
| | **ĐC** – Động cơ | Dòng định mức (IE3), dòng khởi động, sụt áp khởi động, CB/contactor/rơ le/khởi động mềm/biến tần, cáp |
| | **BÙ** – Bù công suất phản kháng | kVAr, chia cấp, loại tụ theo sóng hài, cảnh báo cộng hưởng, CB/cáp tủ bù |
| Dự phòng & an toàn | **MF** – Máy phát dự phòng | kVA theo tải và khởi động động cơ, ATS, nhiên liệu |
| | **TĐ** – Tiếp địa | Điện trở cọc, nhóm cọc, thanh nối, số cọc cần thiết |
| Tiện ích | **CS** – Chiếu sáng | Số đèn, lưới bố trí, độ rọi, W/m² |
| | **MÁNG** – Máng/thang cáp | Bề rộng theo hệ số lấp đầy hoặc xếp một lớp |
| | **BT** – Tiết kiệm bằng biến tần | kWh, tiền, thời gian hoàn vốn, giảm CO₂ |
| | **QĐ** – Quy đổi | kW ↔ HP ↔ kVA ↔ kVAr ↔ A |

Mỗi module có: kết quả chính, danh sách kiểm tra (Đạt / Lưu ý / Không đạt), bảng chi tiết, **diễn giải công thức kèm số thay vào**, nút *Sao chép kết quả* (dán vào Zalo, email, báo cáo) và *In hoặc lưu PDF*.

## Đưa lên GitHub Pages (khoảng 5 phút)

1. Đăng nhập [github.com](https://github.com) → nút **New** (tạo repository mới).
2. Đặt tên, ví dụ `tinh-toan-dien`, chọn **Public** → **Create repository**.
3. Trong repository vừa tạo, bấm **Add file → Upload files**. Giải nén file zip, kéo thả **tất cả các file** (`index.html`, `README.md`, `manifest.webmanifest`, các file `icon-*.png`, `apple-touch-icon.png`, `logo.svg`, `logo-1024.png`) vào → **Commit changes**.
4. Vào **Settings → Pages**. Tại *Build and deployment*, chọn *Source*: **Deploy from a branch**. Chọn *Branch*: **main**, thư mục **/ (root)** → **Save**.
5. Chờ 1–2 phút, trang sẽ chạy tại:
   `https://<tên-tài-khoản>.github.io/tinh-toan-dien/`

**Dùng trên điện thoại:** mở đường link trên bằng Chrome/Safari → *Thêm vào màn hình chính* để dùng như một ứng dụng.

**Cập nhật phiên bản mới:** vào repository → **Add file → Upload files** → kéo file `index.html` mới vào (ghi đè) → **Commit changes**. Trang tự cập nhật sau 1–2 phút.

> Lưu ý: GitHub Pages miễn phí yêu cầu repository **Public**, tức là ai có link đều xem được công cụ (không xem được số liệu bạn nhập, vì số liệu chỉ lưu trên trình duyệt của từng máy).

## Logo và màu sắc

Logo là tia sét gồm ba dải song song màu **đỏ – vàng – xanh**, tượng trưng ba pha L1 – L2 – L3, đặt trên nền xanh than.

| File | Dùng cho |
|---|---|
| `logo.svg` | Logo gốc dạng vector, phóng to không vỡ (in ấn, báo cáo) |
| `logo-1024.png` | Ảnh logo nền trong suốt (ảnh đại diện nhóm Zalo, slide) |
| `icon-192.png`, `icon-512.png`, `manifest.webmanifest` | Biểu tượng khi “Thêm vào màn hình chính” trên Android |
| `apple-touch-icon.png` | Biểu tượng trên iPhone/iPad |

Mã màu: đỏ `#E5382F`, vàng `#F6C21C`, xanh `#2F80ED`, nền logo `#1E2626`, thanh menu `#27302F`, màu nút chính (đồng) `#A45E27`.

## Chỉnh sửa bảng tra

Mở `index.html` bằng Notepad++ hoặc VS Code, tìm các mục sau (Ctrl+F):

| Tìm | Nội dung |
|---|---|
| `const AMP =` | Dòng cho phép của cáp theo IEC 60364-5-52 – thay bằng số liệu catalogue hãng cáp đang dùng |
| `const R20_CU =` | Điện trở ruột đồng ở 20 °C |
| `const CB_IN =` / `const FRAMES =` | Dãy dòng định mức CB, khung MCCB/ACB |
| `const T_STD =` | Dãy công suất MBA |
| `const MKW =`, `MEFF`, `MCOS` | Hiệu suất, cosφ động cơ theo kW |
| `const FUSE =` | Dãy cầu chì trung thế |

## Cơ sở tính toán

IEC 60364-5-52 / 5-54 / 4-41 / 4-43, IEC 60909-0, IEC 61439-1, IEC 60076, IEC 62271-1, IEC 60034-30-1, IEC 60831; Schneider Electric *Electrical Installation Guide* và *MV Design Guide*; TCVN 9358:2012, TCVN 7114-1.

## Giới hạn

Đây là công cụ **tính sơ bộ, hỗ trợ kỹ sư**. Bảng tra là giá trị tham chiếu theo tiêu chuẩn. Kết quả cần được kỹ sư có chuyên môn kiểm tra, đối chiếu catalogue nhà sản xuất và quy định của điện lực trước khi dùng cho thiết kế, mua sắm, thi công.
