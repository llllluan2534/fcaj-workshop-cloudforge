---
title : "Thiết lập Cơ sở dữ liệu"
date : 2026-07-10
weight : 4 
chapter : false
pre : " <b> 5.4. </b> "
---

### Tổng quan Hệ thống Dữ liệu Cốt lõi

Trong chương này, chúng ta sẽ xây dựng một nền tảng dữ liệu vững chắc và bảo mật cho ứng dụng Smart Media Analytics. Để tuân thủ nghiêm ngặt kiến trúc bảo mật **Zero-Trust**, tất cả các dịch vụ cơ sở dữ liệu sẽ được triển khai hoàn toàn bên trong vùng mạng nội bộ (**Private Subnets**) và được bảo vệ bởi các lớp tường lửa chuyên biệt.

Các thành phần cốt lõi cần thiết lập bao gồm:
1. **Amazon S3:** Lưu trữ đối tượng vô hạn (Object Storage), đóng vai trò như "két sắt" để tiếp nhận và lưu giữ toàn bộ các file video và audio gốc.
2. **Amazon RDS PostgreSQL:** Đóng vai trò là cơ sở dữ liệu quan hệ chính, được tích hợp sẵn extension `pgvector` để hỗ trợ tính năng Tìm kiếm Ngữ nghĩa (Semantic Search) cho các mô hình AI.
3. **Amazon ElastiCache (Redis):** Đóng vai trò là bộ nhớ đệm (Caching) tốc độ cực cao và Message Broker để phân phối các tác vụ cho AI Workers xử lý bất đồng bộ.

Kết thúc chương này, không chỉ khả năng giao tiếp bảo mật của hệ thống dữ liệu được kiểm chứng, mà bạn còn thu thập được toàn bộ các thông số kết nối cần thiết để đóng gói thành các biến môi trường (`.env`), hoàn toàn sẵn sàng cho việc triển khai ứng dụng.

### Nội dung Thực hành

- [Tạo S3 Bucket](5.4.1-create-s3-bucket/)
- [Tạo RDS PostgreSQL](5.4.2-create-rds-postgresql/)
- [Kích hoạt pgvector](5.4.3-enable-pgvector/)
- [Tạo ElastiCache (Redis)](5.4.4-create-elasticache-redis/)
- [Kiểm tra Kết nối & Tổng hợp Endpoints](5.4.5-test-connection/)
