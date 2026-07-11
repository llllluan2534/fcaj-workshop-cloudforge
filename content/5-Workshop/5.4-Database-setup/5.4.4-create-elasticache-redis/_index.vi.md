---
title : "Tạo ElastiCache (Redis)"
date : 2026-07-10
weight : 4
chapter : false
pre : " <b> 5.4.4. </b> "
---

Trong kiến trúc AI Pipeline của chúng ta, Amazon ElastiCache (Redis) đóng hai vai trò cực kỳ quan trọng:
1. **Tốc độ (Caching):** Lưu trữ tạm thời các kết quả truy vấn thường xuyên để giảm tải cho Cơ sở dữ liệu chính.
2. **Quản lý hàng đợi (Message Broker):** Hoạt động như một trung gian để phân phối các tác vụ nặng (như tạo AI embeddings hoặc xử lý media) cho AI Workers xử lý bất đồng bộ.

Tương tự như RDS, chúng ta sẽ đặt cụm Redis này vào Private Subnet để đảm bảo tuân thủ kiến trúc bảo mật Zero-Trust.

#### 1. Tạo Subnet Group cho ElastiCache
1. Điều hướng đến **ElastiCache Console**, và chọn **Subnet groups** ở menu bên trái (Bên dưới *Configurations*).
2. Nhấp vào nút **Create subnet group**.
3. **Name:** `cloudforge-redis-subnet-group`
4. **Description:** `Subnet group for CloudForge Redis`
5. **VPC ID:** Chọn `cloudforge-vpc`.
6. **Availability Zones:** Chọn `ap-southeast-1a` và `ap-southeast-1b`.
7. **Subnet ID:** *Lưu ý Quan trọng:* Hệ thống có thể tự động chọn tất cả 4 subnets. Nhấp vào nút **Manage**, **bỏ chọn 2 Public Subnets**, và chỉ giữ lại 2 Private Subnets của dự án.
8. Nhấp **Create**.

![Redis Subnet Group](/images/5-Workshop/5.4-Database-setup/redis_subnet_group.png)

#### 2. Cấp phát Redis Cluster
Vì giao diện AWS ElastiCache mới sử dụng trình hướng dẫn từng bước (wizard), hãy làm theo các cấu hình sau:

1. Chuyển sang menu **Redis OSS caches** (dưới mục *Resources*), và nhấp vào nút màu cam **Create cache**. *(Nếu có thông báo giới thiệu Valkey hiện lên, hãy chọn **Continue with Redis OSS**).*
2. **Bước 1: Settings (Cài đặt):**
   * **Configuration:** Chọn **Redis OSS** → **Node-based cluster** → **Cluster cache**.
   * **Cluster mode:** Chọn **Disabled**.
   * **Cluster info:**
     * **Name:** `cloudforge-redis`
     * **Description:** `Redis cluster for Caching and Message Queue`
     * **Node type:** Chọn `cache.t3.micro` hoặc `cache.t4g.micro` (Tối ưu hóa chi phí).
     * **Number of replicas:** `0`.
   * **Connectivity:** Trong mục *Subnet groups*, chọn **Choose existing subnet group** → Chọn `cloudforge-redis-subnet-group` bạn vừa tạo.
   * Nhấp **Next** để tiếp tục sang bước 2.
3. **Bước 2: Advanced settings (Cài đặt nâng cao - Vô cùng quan trọng):**
   * **Security groups:** Nhấp **Manage** → Bỏ chọn nhóm `default`, chỉ chọn nhóm **`cloudforge-db-redis-sg`** → Nhấp **Save**.
   * **Backup:** Cuộn xuống và **bỏ chọn** *Enable automatic backups* để rút ngắn thời gian tạo.
   * Nhấp **Next**.
4. **Bước 3: Review and create (Xem lại và tạo):**
   * Xem lại các thông số của bạn và nhấp **Create** ở cuối trang. *(Quá trình này sẽ mất khoảng 3-5 phút).*

![Redis Connectivity](/images/5-Workshop/5.4-Database-setup/redis_connectivity.png)

#### 3. Lấy Thông tin Endpoint
Sau khi trạng thái của cụm Redis chuyển sang **Available**, hãy nhấp vào tên `cloudforge-redis`.
Dưới phần **Cluster details**, sao chép đoạn URL được cung cấp trong trường **Primary endpoint** (có dạng giống như `cloudforge-redis.xxxxxx.0001.apse1.cache.amazonaws.com:6379`) để lưu lại cấu hình kết nối này cho ứng dụng.

***

**Bước tiếp theo:** Hệ thống dữ liệu cốt lõi hiện đã hoàn thiện. Chúng ta sẽ chuyển sang phần **5.4.5** để tổng hợp tất cả các Endpoints cần thiết, chuẩn bị mọi thứ sẵn sàng cho việc triển khai mã nguồn Backend lên Cloud.