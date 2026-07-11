---
title: "Worklog Tuần 5"
date: 2024-05-16
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---


### Mục tiêu tuần 5:

* Hiểu rõ cơ chế hoạt động của Amazon EC2 Auto Scaling Group (ASG) và Load Balancer trong việc tự động điều chỉnh tài nguyên.
* Nắm vững kiến trúc triển khai ứng dụng FCJ Management có khả năng mở rộng linh hoạt.
* Thực hành tạo Target Group, khởi tạo Auto Scaling Group, và cấu hình các policy liên quan.
* Tích hợp Load Balancer vào ASG để phân phối lưu lượng truy cập cân bằng giữa các EC2 instances.
* Triển khai hệ thống giám sát bằng CloudWatch và nhận thông báo qua Amazon SNS khi có sự thay đổi về tài nguyên.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tổng quan Auto Scaling Group: Tự động điều chỉnh EC2 instance theo nhu cầu thực tế, tránh lãng phí. <br>&emsp; + Giới thiệu ứng dụng FCJ Management: Phân tích kiến trúc triển khai ứng dụng đồng loạt trên ASG. <br>- **Project - Smart Media Analysics (Frontend):** <br>&emsp; + Cấu hình React Router tổng cho dự án . Tạo khung Layout bọc ngoài (AppShell). | 14/05/2026   | 14/05/2026      | <https://000006.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + Load Balancer & Target Group: Cơ chế phân phối traffic đến các instance trong ASG. <br>&emsp; + Hướng mở rộng và giám sát: Ứng dụng CloudWatch metric để quyết định thêm/giảm instance kịp thời. <br>&emsp; + Thông báo & Rủi ro: Tích hợp Amazon SNS. <br>- **Project - Smart Media Analysics (Frontend):** <br>&emsp; + Xây dựng component Sidebar navigation và TopBar tích hợp Logo cùng khung tìm kiếm. <br>&emsp; + Phát triển HeaderBar dành riêng cho trang chi tiết Media (chứa title, timestamp, action buttons) | 15/05/2026   | 15/05/2026      | <https://000006.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Chuẩn bị VPC, subnet, Launch Template. <br>&emsp; + Tạo Target Group (FCJ-Management-TG) qua HTTP và đăng ký các EC2 instance. <br>&emsp; + Tạo Auto Scaling Group (FCJ-Management-ASG) kết nối với 3 public subnets. . | 16/05/2026   | 16/05/2026      | <https://000006.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Cấu hình Network & Kết nối Load Balancer: Chọn Attach to an existing load balancer, bật Health checks. <br>&emsp; + Cấu hình Scaling: Thiết lập Desired/Min/Max capacity (1/1/3) và thu thập metrics CloudWatch. <br>&emsp; + Thiết lập thông báo SNS gửi email khi có events.  | 17/05/2026   | 17/05/2026      | <https://000006.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Test & Điều chỉnh: Copy DNS của Load Balancer để truy cập app FCJ Management. Thay đổi Desired capacity để quan sát ASG tự động scale và check SNS email. <br>&emsp; + Dọn dẹp: Xóa ASG, Target Group, Load Balancer để không phát sinh cước. <br>- **Project - Smart Media Analysics (Frontend):** <br>&emsp;+ Xây dựng AIProcessingPanel để bắt WebSocket realtime, hiển thị thanh tiến trình xử lý AI (Extracting, Transcribing...). <br>&emsp;+ Lắp ráp AppShell hoàn chỉnh, đảm bảo điều hướng mượt mà, không bị layout shift và dark theme đồng nhất. | 18/05/2026   | 18/05/2026      | <https://000006.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* Vận hành thành thạo Auto Scaling Group kết hợp Load Balancer để đảm bảo high availability cho ứng dụng FCJ Management.
* Hiểu và thao tác nhuần nhuyễn quy trình tạo Target Group, kết nối Launch Template với ASG.
* Nắm bắt cách giám sát hệ thống với CloudWatch và phản ứng với các thông báo hệ thống thông qua Amazon SNS.
* Hoàn thiện kỹ năng phân tích và xử lý khi hệ thống cần mở rộng hoặc thu hẹp tài nguyên (scale out / scale in).
* Nắm vững các bước dọn dẹp tài nguyên (cleanup) phức tạp khi làm việc với nhiều dịch vụ AWS liên kết cùng lúc.
* Frontend: Hoàn thành cấu trúc Layout tổng thể (AppShell, Sidebar, Topbar) và module nhận tín hiệu xử lý AI realtime.
