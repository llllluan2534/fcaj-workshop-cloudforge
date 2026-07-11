---
title : "Tạo RDS PostgreSQL"
date : 2026-07-10
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

Amazon RDS (Relational Database Service) giúp bạn dễ dàng thiết lập, vận hành và mở rộng cơ sở dữ liệu quan hệ trên đám mây. Đối với dự án này, chúng ta sẽ sử dụng engine **PostgreSQL** vì nó hỗ trợ hoàn hảo cho extension `pgvector` – một yêu cầu cốt lõi để lưu trữ vector embeddings cho tính năng tìm kiếm ngữ nghĩa của AI.

#### 1. Tạo DB Subnet Group
Trước khi khởi tạo cơ sở dữ liệu, RDS yêu cầu chúng ta định nghĩa một **Subnet Group** để xác định xem máy chủ cơ sở dữ liệu có thể được đặt vào các Private Subnets nào bên trong VPC của chúng ta.

1. Điều hướng đến **RDS Console** và chọn **Subnet groups** ở menu bên trái.
2. Nhấp vào nút màu cam **Create DB subnet group**.
3. **Name:** `cloudforge-db-subnet-group`
4. **Description:** `Subnet group for CloudForge Databases`
5. **VPC:** Chọn `cloudforge-vpc`.
6. **Add subnets:** Chọn 2 Availability Zones (`ap-southeast-1a` và `ap-southeast-1b`), sau đó tích chọn 2 Private Subnets tương ứng được chỉ định cho tầng Database.
7. Nhấp vào **Create**.

![DB Subnet Group](/images/5-Workshop/5.4-Database-setup/db_subnet_group.png)

#### 2. Cấp phát PostgreSQL Database
1. Chuyển sang menu **Databases** ở bên trái và nhấp vào **Create database**.
2. Từ menu xổ xuống, nhấp vào **Full configuration** để hiển thị tất cả các cấu hình hệ thống chuyên sâu.
3. **Engine options:** Chọn **PostgreSQL** (giữ nguyên phiên bản mặc định được hệ thống đề xuất).
4. **Templates & Durability:**
   - **Templates:** Chọn **Sandbox** (hoặc *Dev/Test*) để tối đa hóa việc tiết kiệm chi phí cho môi trường workshop.
   - **Deployment options:** Đảm bảo hệ thống mặc định chọn **Single-AZ DB instance deployment**.
5. **Settings:**
   - **DB instance identifier:** Thay đổi tên mặc định thành `cloudforge-db`.
   - **Credentials management:** Tích chọn **Self managed** để tự quản lý mật khẩu của bạn.
   - **Master username:** Giữ nguyên `postgres`.
   - **Master password / Confirm password:** Nhập một mật khẩu an toàn (ví dụ: `CloudForge2026!`).
6. **Instance configuration & Storage:**
   - **DB instance class:** Giữ nguyên lớp cấu hình thấp nhất được đề xuất (ví dụ: `db.t3.micro`).
   - **Allocated storage:** Giảm giá trị mặc định lớn xuống **20 GiB** (mức tối thiểu cho phép).
   - **Storage autoscaling:** Bỏ chọn *Enable storage autoscaling*.
7. **Connectivity (Mạng nội bộ - Vô cùng quan trọng):**
   - **Virtual private cloud (VPC):** Chọn `cloudforge-vpc`.
   - **DB Subnet group:** Chọn `cloudforge-db-subnet-group` vừa tạo ở bước 1.
   - **Public access:** Chọn **No** *(Đảm bảo cơ sở dữ liệu bị cô lập hoàn toàn khỏi Internet)*.
   - **VPC security group:** Chọn **Choose existing** → Xóa bỏ group `default` và chỉ chọn **`cloudforge-db-redis-sg`** (Tường lửa Zero-Trust bạn đã tạo ở phần 5.3.4).
8. Mở rộng phần **Additional configuration** ở phía dưới:
   - **Initial database name:** Nhập `cloudforge_db` (để AWS tự động tạo sẵn một DB rỗng).
   - **Backup:** Bỏ chọn *Enable automated backups* để tăng tốc quá trình cấp phát cho workshop.
9. Cuộn xuống dưới cùng và nhấp vào **Create database**. *(Quá trình cấp phát thực tế thường mất khoảng 3-5 phút).*

![RDS Connectivity Setup](/images/5-Workshop/5.4-Database-setup/rds_connectivity.png)

***

**Bước tiếp theo:** Trong khi chờ phiên bản RDS hoàn tất quá trình cấp phát, chúng ta sẽ chuyển sang phần **5.4.3** để kích hoạt extension `pgvector`, chuẩn bị sẵn sàng cho cơ sở dữ liệu lưu trữ các embeddings.