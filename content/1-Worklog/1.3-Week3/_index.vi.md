---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 3:

* Nghiên cứu sâu về giải pháp lưu trữ AWS thông qua việc thiết kế kiến trúc web tĩnh độ trễ thấp với Amazon S3 và CloudFront.
* Khám phá dịch vụ cơ sở dữ liệu quan hệ (Amazon RDS) để hiểu cơ chế tự động mở rộng, chuyển lỗi (failover) và bảo trì.
* Kết nối hạ tầng máy tính với tầng dữ liệu bằng cách thiết lập mạng an toàn giữa EC2 và cơ sở dữ liệu RDS.
* Mở rộng tư duy về mạng lưới đám mây qua việc tìm hiểu Amazon Lightsail VPC và giải pháp kết nối lai (Site-to-Site VPN).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Nội dung học tập:**<br>&emsp; + Học về các khái niệm liên quan đến Amazon S3 và vai trò của nó trong việc lưu trữ trang web tĩnh.<br>&emsp; + Tìm hiểu cài đặt Block Public Access và quyền truy cập object công khai để quản lý bảo mật.<br>&emsp; + Cải thiện hiệu suất trang web và phân phối toàn cầu bằng Amazon CloudFront.<br>&emsp; + Sử dụng bucket versioning để quản lý nhiều phiên bản file và sao chép liên khu vực (replication).<br>&emsp; + Ôn tập các thực hành tốt nhất (bảo mật, tối ưu chi phí) khi lưu trữ bằng S3.<br> | 01/05/2026 | 03/05/2026      |
| 3   |  - **Thực hành:**<br>&emsp; + Tạo và chuẩn bị một bucket S3, sau đó bật tính năng lưu trữ web tĩnh.<br>&emsp; + Cấu hình quyền công khai và kiểm tra trang web thông qua S3 endpoint.<br>&emsp; + Tích hợp Amazon CloudFront cho trang web tĩnh trên S3.<br>&emsp; + Bật versioning, thực hành di chuyển object và sao chép object qua các region khác nhau.<br>&emsp; + Thực hiện dọn dẹp tài nguyên (cleanup) để tránh phát sinh chi phí.                                           | 03/05/2026   | 03/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Nội dung học tập:**<br>&emsp; + Khái niệm về Amazon RDS, các lợi ích (tự động backup, scaling, HA) và các engine hỗ trợ.<br>&emsp; + Hiểu cách dùng EC2 làm client kết nối database và cấu hình Security Group cho SSH (port 22), MySQL (port 3306).<br>&emsp; + Khởi chạy RDS MySQL, cấu hình Multi-AZ, và cài đặt database client trên EC2.<br>&emsp; + Theo dõi hiệu suất bằng CloudWatch và tầm quan trọng của việc dọn dẹp tài nguyên.<br> | 04/05/2026   | 04/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành:**<br>&emsp; + Tạo EC2 instance, cài đặt MySQL client và kiểm tra kết nối SSH.<br>&emsp; + Khởi chạy RDS MySQL instance với tính năng tự động backup và Multi-AZ.<br>&emsp; + Cấu hình Security Group cho phép EC2 truy cập RDS, thực hiện kết nối và chạy các câu lệnh SQL.<br>&emsp; + Giám sát các chỉ số RDS qua CloudWatch và dọn dẹp toàn bộ tài nguyên để tránh phát sinh chi phí.                   | 05/05/2026   | 05/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Nội dung học tập:**<br>&emsp; + Kiến thức nền về Amazon Lightsail: dịch vụ instance đơn giản tự động tạo VPC, subnet, và IP để triển khai ứng dụng nhanh chóng.<br>&emsp; + Mục tiêu VPC & VPN Site-to-Site: hiểu vai trò mạng nội bộ của VPC và cách kết nối AWS với mạng on-premise qua VPN.<br>&emsp; + Nhận biết các chi phí liên quan đến VPN (connection-hour, data transfer, public IPv4).<br>&emsp; + Các khái niệm chính: VPC, Virtual Private Gateway, Customer Gateway, và kết nối VPN băng thông cao. | 06/05/2026   | 06/05/2026      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 3:


* Xây dựng thành công hệ thống web tĩnh phân phối toàn cầu nhờ sự kết hợp giữa S3 bucket và mạng phân phối nội dung CloudFront.
* Bảo vệ an toàn dữ liệu lưu trữ bằng cách kích hoạt object versioning và sao chép dự phòng liên khu vực trên S3.
* Đưa vào vận hành một cơ sở dữ liệu MySQL tiêu chuẩn sản xuất trên RDS, đồng thời kiểm nghiệm thành công kịch bản sự cố (Multi-AZ failover).
* Thiết lập mô hình client-server đáng tin cậy khi kết nối EC2 với RDS thông qua các quy tắc Security Group chặt chẽ.
* Nâng cao hiểu biết về kiến trúc mạng lai (Site-to-Site VPN) và quy trình tự động hóa hạ tầng của Amazon Lightsail.


