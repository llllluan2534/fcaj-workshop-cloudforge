---
title : "Cấu hình Security Groups"
date : 2026-07-10
weight : 4
chapter : false
pre : " <b> 5.3.4. </b> "
---

Security Groups đóng vai trò như các tường lửa ảo (virtual firewalls) ở cấp độ tài nguyên. Để đảm bảo tiêu chuẩn bảo mật cao nhất, chúng ta sẽ áp dụng mô hình **Zero-Trust**: các thành phần hệ thống sẽ chỉ chấp nhận lưu lượng truy cập từ các nguồn được ủy quyền cụ thể, tuyệt đối ngăn chặn việc truy cập mở rộng từ internet.

Trong phần này, chúng ta sẽ tạo 3 Security Groups cốt lõi bên trong `cloudforge-vpc`:

#### 1. ALB-SG (Tường lửa cho Application Load Balancer)
**Mục đích:** Đây là cổng duy nhất mở ra Internet để tiếp nhận lưu lượng truy cập từ người dùng.
1. Điều hướng đến **EC2 Console** hoặc **VPC Console** và chọn **Security Groups** ở menu bên trái.
2. Nhấp vào nút màu cam **Create security group**.
3. **Security group name:** `cloudforge-alb-sg`
4. **Description:** `Allow HTTP/HTTPS from Internet`
5. **VPC:** Chọn `cloudforge-vpc`.
6. Dưới phần **Inbound rules**, cấu hình như sau:
   - Type: `HTTP` | Port: `80` | Source: `0.0.0.0/0` (Anywhere IPv4)
   - Type: `HTTPS` | Port: `443` | Source: `0.0.0.0/0` (Anywhere IPv4)
7. **Outbound Rules:** Giữ nguyên Mặc định (Allow All Traffic).
8. Nhấp vào **Create security group**.

![ALB Security Group](/images/5-Workshop/5.3-Network-vpc/alb_sg.png)

#### 2. ECS-App-SG (Tường lửa cho Backend & AI Worker)
**Mục đích:** Chỉ chấp nhận các yêu cầu đã được lọc qua Load Balancer và cho phép các container nội bộ giao tiếp với nhau.
1. Tạo một security group mới tên là `cloudforge-ecs-app-sg` bên trong `cloudforge-vpc`.
2. **Inbound rules:**
   - Type: `Custom TCP` | Port: `8000` (Cổng Backend API) | Source: Chọn ID của `cloudforge-alb-sg`. *(Bảo vệ API, chỉ nhận lưu lượng từ ALB)*.
   - Type: `All TCP` | Port: `0-65535` | Source: Chọn ID của chính `cloudforge-ecs-app-sg`. *(Cho phép các container nội bộ liên lạc với nhau)*.

![ECS App Security Group](/images/5-Workshop/5.3-Network-vpc/ecs_app_sg.png)

#### 3. DB-Redis-SG (Tường lửa cho Database & Cache)
**Mục đích:** Khóa chặt tầng Dữ liệu (Data tier), chỉ cho phép các máy chủ xử lý (ECS containers) truy cập và đọc/ghi dữ liệu.
1. Tạo một security group mới tên là `cloudforge-db-redis-sg` bên trong `cloudforge-vpc`.
2. **Inbound rules:**
   - Type: `PostgreSQL` | Port: `5432` | Source: Chọn ID của `cloudforge-ecs-app-sg`.
   - Type: `Custom TCP` | Port: `6379` (Cổng Redis) | Source: Chọn ID của `cloudforge-ecs-app-sg`.

![DB Security Group](/images/5-Workshop/5.3-Network-vpc/sg_db_redis.png)

***

**Bước tiếp theo:** Với nền tảng mạng vững chắc và các lớp bảo mật Zero-Trust đã hoàn tất, chúng ta sẽ chuyển sang phần **5.4: Thiết lập Cơ sở dữ liệu** để cấp phát các cụm database.