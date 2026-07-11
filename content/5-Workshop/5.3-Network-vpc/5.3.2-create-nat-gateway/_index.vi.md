---
title : "Kiểm tra NAT Gateway & Định tuyến"
date : 2026-07-09
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

Ở bước trước, trình hướng dẫn **VPC and more** đã tự động cấu hình và cấp phát một NAT Gateway cho hệ thống của chúng ta. NAT (Network Address Translation) Gateway là một thành phần quan trọng trong kiến trúc Multi-tier (nhiều tầng): Nó đóng vai trò trung gian, cho phép các tài nguyên nằm trong các **Private Subnets** cô lập (như ECS Fargate Tasks) khởi tạo kết nối đi ra internet (ví dụ: để kéo Docker image hoặc gọi API bên ngoài), đồng thời chặn hoàn toàn mọi kết nối từ bên ngoài Internet đi ngược vào hạ tầng cốt lõi.

Trong phần này, chúng sẽ kiểm tra trạng thái hoạt động của NAT Gateway và phân tích sâu các Route Tables (Bảng định tuyến) để hiểu rõ chính xác luồng dữ liệu mạng của chúng ta được kiểm soát như thế nào.

#### 1. Kiểm tra NAT Gateway & Elastic IP
1. Trên bảng điều hướng bên trái của dịch vụ VPC, chọn **NAT gateways**.
2. Kiểm tra phần **State** (Trạng thái) của NAT Gateway (có tên `cloudforge-nat-...`) đang hiển thị màu xanh lá là **Available**.
3. Quan sát trường **Elastic IP address**: Đây là một địa chỉ IP công cộng (public IP) tĩnh duy nhất được AWS cấp phát riêng cho bạn. Kể từ lúc này, mọi lưu lượng truy cập internet chiều đi ra (outbound) từ bất kỳ máy chủ nào trong Private Subnet đều sẽ được "ẩn danh" (masqueraded) dưới địa chỉ public IP này.

   ![NAT Gateway Verification](/images/5-Workshop/5.3-Network-vpc/nat_gateway_verify.png)

#### 2. Phân tích Route Tables & Các Subnet liên kết
Route Table chứa các quy tắc mạng quyết định đích đến của các gói tin từ một subnet. Hệ thống tự động đã tạo ra các route tables chuyên biệt:

##### A. Public Route Table (Tên chứa `cloudforge-rtb-public`)
1. Chọn public route table này và nhấp vào tab **Routes**. Bạn sẽ thấy một quy tắc định tuyến:
   * **Destination:** `0.0.0.0/0` (Toàn bộ lưu lượng internet).
   * **Target:** Trỏ đến `igw-XXXX` (Internet Gateway). Đây chính là "chìa khóa" biến các subnet được liên kết với nó thành các "Public Subnets".
2. Chuyển sang tab **Subnet associations** → phần **Explicit subnet associations**: Kiểm tra xem 2 Public Subnets (`cloudforge-subnet-public-...`) đã được liên kết an toàn ở đây chưa.

   ![Public Route Table](/images/5-Workshop/5.3-Network-vpc/public_route_table.png)

##### B. Private Route Tables (Tên chứa `cloudforge-rtb-private`)
1. Chọn một private route table và nhấp vào tab **Routes**. Quan sát quy tắc định tuyến:
   * **Destination:** `0.0.0.0/0` (Toàn bộ lưu lượng ra internet).
   * **Target:** Trỏ trực tiếp đến `nat-XXXX` (Chính là NAT Gateway đã kiểm tra ở Bước 1). Điều này đảm bảo dữ liệu nội bộ được bảo vệ an toàn khi đi ra Internet.
2. Chuyển sang tab **Subnet associations**: Kiểm tra xem các Private Subnets (nơi sẽ lưu trữ ECS và RDS) đã được cô lập trong bảng này, hoàn toàn tách biệt khỏi Internet Gateway chưa.

   ![Private Route Table](/images/5-Workshop/5.3-Network-vpc/private_route_table.png)

***

**Bước tiếp theo:** Bây giờ hệ thống định tuyến ra internet đã rõ ràng, ở phần **5.3.3**, chúng ta sẽ kiểm tra một thành phần tối ưu hóa chi phí cực kỳ quan trọng: **S3 Gateway Endpoint**. Nó giúp đảm bảo rằng việc truyền tải dữ liệu lớn (như Video) sẽ không phát sinh phí xử lý dữ liệu không cần thiết qua NAT Gateway.