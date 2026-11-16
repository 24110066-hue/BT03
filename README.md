24110066-Nguyễn Hữu Vinh BT03

Hướng dẫn:

1.
Mở MySQL Workbench, kết nối MySQL rồi chạy:
CREATE DATABASE IF NOT EXISTS servletjpa
CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

2. Cấu hình kết nối database

Trong thư mục config của project:
- Copy db.properties.example.
- Đổi tên bản copy thành db.properties.
- Mở file và sửa:

db.url=jdbc:mysql://localhost:3306/servletjpa?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Ho_Chi_Minh&characterEncoding=UTF-8
db.user=root
db.password=MAT_KHAU_MYSQL_CUA_BAN
db.schema=update


3. Cấu hình email gửi OTP thật

Copy config/mail.properties.example thành config/mail.properties, rồi sửa:
mail.mode=smtp
mail.host=smtp.gmail.com
mail.port=587
mail.ssl=false
mail.username=EMAIL_GUI_CUA_BAN@gmail.com
mail.password=MAT_KHAU_UNG_DUNG
mail.from=EMAIL_GUI_CUA_BAN@gmail.com

Với Gmail, bật Xác minh 2 bước và tạo Mật khẩu ứng dụng theo hướng dẫn Google. Dùng mật khẩu ứng dụng này, không dùng mật khẩu đăng nhập Gmail thông thường. support.google.com


4. Khởi động
Trong thư mục có pom.xml, chạy:
.\CHAY_MYSQL_SMTP.bat

Sau khi khởi động, mở:

http://localhost:8080/jpa-category/home
