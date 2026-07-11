---
title : "Phân tích S3 Gateway Endpoint"
date : 2026-07-09
weight : 3
chapter : false
pre : " <b> 5.3.3. </b> "
---

Trong các hệ thống Media / AI Pipeline, các Worker nằm trong Private Subnets hoặc các máy chủ ở Public Subnets phải liên tục đọc và ghi các file dung lượng khổng lồ (như video độ phân giải cao và hình ảnh) vào Amazon S3.

Nếu dữ liệu từ Private Subnet đi theo đường định tuyến mặc định (`Private Subnet` → `NAT Gateway` → `Internet` → `S3`), AWS sẽ tính phí xử lý dữ liệu qua NAT Gateway (khoảng $0.045/GB). Với dung lượng video lớn của dự án, chi phí này sẽ tăng vọt. Để giải quyết bài toán tối ưu chi phí này, trình hướng dẫn **VPC and more** đã tự động cấp phát một **S3 Gateway Endpoint** để điều hướng các gói tin qua mạng nội bộ.

#### 1. Kiểm tra trạng thái Endpoint
1. Trên menu điều hướng bên trái của dịch vụ VPC, hãy chuyển đến **Endpoints** (nằm ngay dưới *Managed prefix lists*).
2. Kiểm tra danh sách và chọn Endpoint có tên chứa mã dịch vụ S3 cho khu vực Singapore: `com.amazonaws.ap-southeast-1.s3`.
3. Đảm bảo cột **Status** hiển thị màu xanh lá là **Available**.

   ![S3 Endpoint Verification](/images/5-Workshop/5.3-Network-vpc/s3_endpoint_verify.png)

#### 2. Phân tích cấu hình Route Table
Bí mật của đường tắt này là AWS tự động đưa vào một quy tắc định tuyến đặc biệt cho cả hai nhóm route table (Public và Private) trong dự án của chúng ta. Điều này giúp giữ cho mọi lưu lượng truy cập hướng tới S3 nằm hoàn toàn trong mạng nội bộ AWS thay vì vòng ra Internet.

##### A. Đối với Private Route Tables (Tối ưu hóa chi phí NAT)
1. Chọn một private route table (ví dụ: `cloudforge-rtb-private1`).
2. Trên tab **Routes**, quan sát quy tắc định tuyến chạy song song với NAT Gateway:
   - **Destination:** `pl-6fa54006` (IP Prefix List đại diện cho toàn bộ dịch vụ S3 tại Khu vực Singapore).
   - **Target:** Trỏ trực tiếp đến ID của S3 Endpoint (`vpce-xxxxxx`).
   - **Ý nghĩa:** Mọi hoạt động tải lên/tải xuống từ ứng dụng AI Worker (Private) tới S3 sẽ đi trực tiếp qua gateway này, **bỏ qua hoàn toàn NAT Gateway**. Điều này tối đa hóa tốc độ và giảm chi phí xử lý dữ liệu qua NAT xuống **$0**.

   ![S3 Endpoint Routes Private](/images/5-Workshop/5.3-Network-vpc/s3_endpoint_routes_private.png)

##### B. Đối với Public Route Table (Tối ưu hóa băng thông Public)
1. Chuyển sang chọn public route table `cloudforge-rtb-public`.
2. Trên tab **Routes**, bạn cũng sẽ thấy quy tắc trỏ dải IP `pl-6fa54006` đến `vpce-xxxxxx`, xuất hiện độc lập với Internet Gateway (`igw-xxxx`).
   - **Ý nghĩa:** Ngay cả các tài nguyên trong vùng Public (như Load Balancer hay Bastion Host, nếu có), khi tương tác với S3 cũng sẽ đi qua Endpoint nội bộ này. Điều này giúp giảm tải cho Internet Gateway và tăng cường tính bảo mật của luồng dữ liệu.

   ![S3 Endpoint Routes Public](/images/5-Workshop/5.3-Network-vpc/s3_endpoint_routes_public.png)

***

**Bước tiếp theo:** Bây giờ hạ tầng mạng cốt lõi, định tuyến và các đường tắt tối ưu chi phí của chúng ta đã được kiểm tra và hoạt động hoàn hảo, chúng ta sẽ chuyển sang phần **5.3.4: Cấu hình Security Groups** để thiết lập các lớp khóa tường lửa nghiêm ngặt cho từng dịch vụ cụ thể.