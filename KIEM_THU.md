# Phạm vi kiểm thử

Ngày kiểm tra: 16/11/2026. JDK 21, Maven 3.9.9, Hibernate 6.6.59, H2 2.3.232, Tomcat nhúng 11.0.29.

Kết quả: **31 test, 0 failure, 0 error, 0 skipped**. Đóng gói WAR qua `mvn clean verify`.

| Bộ test | Số test | Phạm vi |
| --- | ---: | --- |
| AuthServiceIntegrationTest | 10 | Hash/salt; chưa kích hoạt; OTP hash/mục đích/sai/hết hạn/dùng lại; giới hạn gửi/thử; reset/phiên; input; rollback khi mail lỗi; khóa đăng nhập |
| AccountVideoWebTest | 8 | Form đăng ký/activate/login/logout; quên mật khẩu; phiên cũ; CRUD video; file mẫu MP4; byte Range; top10; 6/trang; quyền sở hữu/video ẩn; demo Multipart; chặn mailbox ngoài demo; CSRF |
| WebIntegrationTest | 5 | Đăng nhập rồi CRUD Category, JSP/UTF-8, upload/đọc/giữ/thay/xóa ảnh, lỗi dữ liệu/file, CSRF/ID/path, escape HTML, tìm kiếm/phân trang |
| JpaIntegrationTest | 8 | CRUD qua persistence context khác; JPQL, phân trang/count; trùng/rỗng/status; wildcard; rollback; Category–Video; ID không tồn tại |

Email được kiểm tra bằng MailSender giả lập và hộp thư file cục bộ, không gửi SMTP thật đến Gmail hay nhà cung cấp khác. Cần tự cấu hình SMTP và xác nhận email nhận thực tế theo hướng dẫn. MySQL trên máy sinh viên chưa được kết nối; test dùng H2 in-memory riêng.

Video mẫu được tạo bằng ffmpeg, codec H.264/AAC, thời lượng 3 giây. Kiểm thử xác nhận tải upload, lưu byte, trang chi tiết có HTML5 video, trả toàn bộ file và HTTP 206/416. Chưa có xác nhận phát/âm thanh bằng trình duyệt đồ họa; hãy thực hiện các bước play/tua trên máy của bạn.

Bản gốc giữ CRUD Category; chỉ bổ sung yêu cầu đăng nhập khi truy cập quản lý. Trong WAR không có H2, Tomcat nhúng hoặc lớp test. Gói không kèm mật khẩu SMTP, mật khẩu MySQL, database demo hoặc thư OTP đã gửi.
