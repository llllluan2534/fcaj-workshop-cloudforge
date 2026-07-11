---
title : "Tạo VPC & Subnets"
date : 2026-07-09
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

Để đảm bảo tính sẵn sàng cao và bảo mật mạnh mẽ cho các microservices, chúng ta sẽ thiết kế một Virtual Private Cloud (VPC) tùy chỉnh. Chúng ta sẽ tách biệt hoàn toàn các tài nguyên truy cập từ public (như Application Load Balancer) với logic xử lý nội bộ và cơ sở dữ liệu (ECS, RDS, Redis).

Thay vì tạo thủ công từng thành phần, chúng ta sẽ sử dụng trình hướng dẫn (wizard) **VPC and more** để cung cấp một mạng nhiều tầng (multi-tier), được định tuyến đầy đủ và trải rộng trên hai Availability Zones (Vùng sẵn sàng).

#### Các bước thực hiện

1. Điều hướng đến **VPC Console** trên AWS.
2. Nhấp vào nút màu cam **Create VPC**.
3. Trong phần **Resources to create**, chọn **VPC and more**.
4. Cấu hình các thông số mạng như sau:
   * **Name tag auto-generation:** Nhập `cloudforge`.
   * **IPv4 CIDR block:** `10.0.0.0/16` (Cung cấp 65,536 địa chỉ IP nội bộ).
   * **Number of Availability Zones (AZs):** Chọn `2` (ví dụ: `ap-southeast-1a` và `ap-southeast-1b` để đạt tính sẵn sàng cao).
   * **Number of public subnets:** Chọn `2` (Dành cho Application Load Balancer và NAT Gateway).
   * **Number of private subnets:** Chọn `2` (Dành cho ECS Fargate Workers, RDS PostgreSQL, và ElastiCache).
   * **NAT gateways ($):** Nhấp **In 1 AZ** (hoặc **Zonal**, tùy thuộc vào giao diện người dùng mới nhất của AWS). *(Lưu ý: Đối với môi trường thực tế production, AWS khuyến nghị dùng 1 NAT trên mỗi AZ, nhưng với dự án này, 1 AZ là đủ và giúp tiết kiệm chi phí).*
   * **VPC endpoints:** Chọn **S3 Gateway**. *(Rất quan trọng: Tùy chọn này cho phép ECS AI Workers trong private subnets của chúng ta kéo/đẩy video trực tiếp với S3 thông qua mạng nội bộ AWS, giúp bỏ qua hoàn toàn chi phí truyền tải dữ liệu qua NAT Gateway).*
   * **DNS options:** Đảm bảo đánh dấu chọn cả *Enable DNS resolution* và *Enable DNS hostnames*.

5. Ở phía bên phải màn hình, xem qua bảng **Preview**. Nó sẽ hiển thị một sơ đồ logic đẹp mắt, được tạo tự động về hạ tầng mạng mới của bạn.

   ![VPC Preview Map](/images/5-Workshop/5.3-Network-vpc/vpc_preview_map.png)

6. Nhấp vào nút **Create VPC** ở cuối trang.
7. Đợi một vài phút để AWS cấp phát tất cả các tài nguyên (VPC, Subnets, Internet Gateway, NAT Gateway, Route Tables, và S3 Endpoint). Khi hoàn tất, bạn sẽ thấy màn hình "Success".

   ![VPC Success](/images/5-Workshop/5.3-Network-vpc/vpc_success_creation.png)
