---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---


### Mục tiêu tuần 2:

* Hiểu các dịch vụ mạng và máy tính cốt lõi của AWS bao gồm Amazon VPC và Amazon EC2.
* Học cách triển khai ứng dụng an toàn và quản lý tài nguyên thông qua các Vai trò quản lý danh tính và truy cập AWS (IAM Roles).
* Làm chủ môi trường phát triển trên đám mây và lập trình cộng tác bằng AWS Cloud9.
* Áp dụng các thực hành tốt nhất của AWS về bảo mật, phân vùng mạng và tối ưu hóa tài nguyên.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Nội dung học tập:**<br>&emsp; + Khái niệm Amazon VPC và mạng đám mây riêng tư.<br>&emsp; + Mục tiêu bảo mật (phân vùng, kiểm soát truy cập, mã hóa VPN) và các thành phần cơ bản (Security Groups, NACLs).<br>&emsp; + Cấu hình AWS Site-to-Site VPN.<br>&emsp; + Các tính năng nâng cao (NAT Gateways, VPC Flow Logs, CloudWatch, Systems Manager).<br> - **Thực hành:**<br>&emsp; + Chuẩn bị môi trường AWS và khởi chạy EC2 để kiểm thử VPC.<br>&emsp; + Cấu hình VPN và sử dụng IaC để tự động hóa triển khai. | 25/04/2026 | 26/04/2026      |
| 3   | - **Nội dung học tập:**<br>&emsp; + Tổng quan Amazon EC2, chuẩn bị khởi chạy và sự khác biệt giữa Linux và Windows.<br>&emsp; + Triển khai ứng dụng Node.js CRUD trên Linux và Windows EC2.<br>&emsp; + Giới hạn tài nguyên IAM, thực hành bảo mật và dọn dẹp sau workshop.<br> - **Thực hành:**<br>&emsp; + Khởi chạy và kết nối với các instance EC2 Windows và Linux.<br>&emsp; + Triển khai ứng dụng Node.js CRUD trên cả hai instance.<br>&emsp; + Cấu hình IAM role và policy để hạn chế tài nguyên. | 27/04/2026 | 27/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Nội dung học tập:**<br>&emsp; + IAM Roles so với Users/Policies và nguyên tắc quyền hạn tối thiểu.<br>&emsp; + Bảo mật truy cập ứng dụng vào AWS qua IAM Roles (không dùng credential tĩnh).<br>&emsp; + Giám sát, kiểm toán và các thực hành tốt nhất về IAM.<br> - **Thực hành:**<br>&emsp; + Tạo và gắn IAM Role cho EC2 để truy cập an toàn S3/DynamoDB.<br>&emsp; + Bật CloudTrail logging để theo dõi hoạt động IAM.<br>&emsp; + Thực hiện dọn dẹp tài nguyên sau khi kiểm thử. | 28/04/2026   | 28/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Nội dung học tập:**<br>&emsp; + Tổng quan AWS Cloud9, thiết lập môi trường và lợi ích cộng tác.<br>&emsp; + Triển khai ứng dụng trực tiếp từ Cloud9 và quản lý tài nguyên AWS.<br>&emsp; + Bảo mật IAM cho Cloud9 và thực hành tốt nhất về dọn dẹp môi trường.<br>  | 29/04/2026   | 30/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:**<br>&emsp; + Tạo môi trường Cloud9 và kiểm thử các tính năng code editor/terminal.<br>&emsp; + Triển khai ứng dụng mẫu, cấu hình IAM và chia sẻ môi trường.<br>&emsp; + Thực hiện dọn dẹp tài nguyên sau khi kiểm thử.                                                                                       | 30/04/2026   | 30/04/2026      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 2:

* Nắm vững kiến thức toàn diện về thiết kế VPC, các thành phần bảo mật và Site-to-Site VPN.
* Khởi chạy và quản lý thành công các máy chủ EC2 Linux và Windows, triển khai các ứng dụng web thực tế.
* Làm chủ việc cấu hình IAM Role để đảm bảo truy cập ứng dụng an toàn, không cần credential, và bật CloudTrail để kiểm toán.
* Thiết lập môi trường AWS Cloud9 IDE để phát triển cộng tác và tích hợp mượt mà với AWS.
* Áp dụng Infrastructure as Code và tuân thủ các nguyên tắc của AWS Well-Architected Framework trong suốt quá trình triển khai.


