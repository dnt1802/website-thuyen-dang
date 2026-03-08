# Thuyên Đặng AI Training - Website Dự Án

Trang web này được xây dựng dạng Static HTML/CSS/JS (Vanilla + Tailwind CSS), sử dụng `localStorage` làm CMS database cho Blog và Video nhằm mục đích Demo/Chạy trực tiếp mà không cần Backend.

## 1. Cấu trúc thư mục
- `index.html`: Trang chủ (Hero, Testimonials, CTA)
- `about.html`: Trang thông tin cá nhân và timeline kinh nghiệm
- `course.html`: Trang hiển thị khoá học (Nhúng video YouTube, mock Stripe checkout)
- `blog.html`: Nơi đọc bài viết Blog (Parse Markdown thành HTML)
- `contact.html`: Trang liên hệ có tích hợp EmailJS giả lập
- `admin.html`: Trang quản trị (Dashboard quản lý Blog và Video)
- `css/globals.css`: Các tuỳ chỉnh CSS chung (Màu chủ đạo `#007BFF`, animations)
- `js/app.js`: Logic chung toàn trang (Mobile menu, lazy load, scroll animations)
- `js/cms-store.js`: Logic `localStorage` cho CMS
- `js/admin.js`: Logic dành riêng cho trang Admin.

## 2. Hướng dẫn chạy Web
Vì đây là Static HTML, bạn có thể:
1. Giải nén thư mục dự án.
2. Có thể cài đặt extension `Live Server` trên VSCode, sau đó Right-click lên `index.html` và chọn "Open with Live Server".
3. Hoặc đơn giản là mở trực tiếp file `index.html` lên bằng trình duyệt Chrome/Edge/Firefox.

## 3. Hướng dẫn sửa tham số 3rd Party
### A. Tích hợp Stripe 
Mở file `course.html` và tìm đến dòng `const stripePublicKey = "pk_test_TYooMQauvdEDq54NiTphI7jx";`. 
Thay bằng khoá Publishable Key thật của tài khoản Stripe của bạn nếu bạn muốn tạo form Checkout thực tế (Cần có môi trường Node.js server riêng để tạo session). Ở chế độ HTML tĩnh này, nó đang là một Mock redirect báo đã đăng ký.

### B. Tích hợp EmailJS
Mở file `contact.html` và tìm tới các phần sau:
1. Khởi tạo: `emailjs.init("YOUR_EMAILJS_PUBLIC_KEY");`
2. Gọi hàm gửi: `emailjs.sendForm('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', this)`
Đăng ký tài khoản tại [EmailJS](https://www.emailjs.com/) rồi lấy các tham số thay thế vào đây để nhận form thực tế.

## 4. Hướng dẫn Quản trị (CMS Demo)
1. Mở file `admin.html` trên trình duyệt.
2. Bạn có thể thêm/sửa bài viết Blog (hỗ trợ viết bằng Markdown Editor rất trực quan).
3. Bạn có thể Thêm link video YouTube mới để hiển thị bên mục "Khóa học".
4. Sau khi thêm dữ liệu, về trang `blog.html` và `course.html` để xem sự thay đổi ngay lập tức.
*(Lưu ý: Dữ liệu được lưu trong trình duyệt của bạn qua LocalStorage. Sẽ mất trắng nếu bạn xóa Cache/Storage của trình duyệt này)*

## 5. Deploy lên Netlify/Cloudflare
- Kéo thả toàn bộ thư mục `ai-trainer-project` này (Hoặc upload file `.zip`) trực tiếp vào khung Deploy thủ công của Netlify hoặc Cloudflare Pages.
- Web sẽ chạy mượt mà không cần config build settings (vì là file tĩnh HTML thuần).
