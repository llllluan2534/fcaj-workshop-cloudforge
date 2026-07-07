---
title: "Worklog Tuần 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Làm quen với môi trường làm việc, văn hóa và các thành viên của đội FCJ.
* Tạo tài khoản AWS Free Tier, cài đặt AWS CLI và các công cụ quản lý chi phí cần thiết (AWS Budgets).
* Nắm bắt kiến thức nền tảng về hệ sinh thái AWS và các nhóm dịch vụ cốt lõi.
* Nắm vững các kiến thức cơ bản về Amazon EC2, bao gồm kết nối SSH và cấu hình Elastic IP.
* Khám phá kiến trúc serverless với AWS Lambda và cơ sở dữ liệu được quản lý qua Amazon RDS.
* Hiểu rõ các nguyên tắc cơ bản của Identity and Access Management (IAM) và các khái niệm kiểm soát truy cập.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 1   | - Làm quen với các thành viên FCJ <br> - Tạo tài khoản AWS mới và thiết lập thông tin thanh toán <br> - Tham gia chương trình kickoff onboarding - First Cloud AI Journey và gặp gỡ các thành viên FCJ <br>                                              | 17/04/2026 | 17/04/2026      |                                           |
| 2   | - Làm quen với các thành viên FCAJ <br>  - Tìm hiểu cách đội nhóm tổ chức và làm việc <br>                  - Đọc và lưu ý các nội quy, quy định tại đơn vị thực tập                                                                                                   | 18/04/2026 | 18/04/2026      |    
| 3   | - Tạo tài khoản AWS Free Tier <br> - Tìm hiểu AWS Console & AWS CLI <br> - **Thực hành:** <br>&emsp; + Tạo tài khoản AWS <br>&emsp; + Cài đặt & cấu hình AWS CLI <br> &emsp; + Cách sử dụng AWS CLI | 19/04/2026 | 19/04/2026      | <https://000001.awsstudygroup.com/1-aws-free-tier-2025-revolution/> |                                       |
| 4   | - Có kiến thức nền tảng về các dịch vụ đám mây AWS và các danh mục chính: <br>&emsp; * Compute <br>&emsp; * Storage <br>&emsp; * Networking <br>&emsp; * Databases <br>&emsp; * Security <br>&emsp; * Monitoring & Management <br>&emsp; * Analytics & AI/ML <br>| 20/04/2026 | 20/04/2026 |  |
| 5   | - Tìm hiểu EC2 cơ bản <br>&emsp; + Instance types <br>&emsp; + AMI <br>&emsp; + EBS <br>&emsp; + Security Group <br> - Các phương pháp kết nối SSH vào EC2 <br>&emsp; + Key Pair <br>&emsp;  - Elastic IP <br>&emsp; + Khái niệm và cách sử dụng <br>&emsp; + Gắn IP tĩnh cho EC2 <br> - AWS Budgets <br>&emsp; + Tạo cảnh báo chi phí qua email <br> - Lambda Web App <br>&emsp; + Tạo serverless function từ blueprint <br>&emsp; + Test request/response <br>&emsp; + Xóa sau khi thực hành <br> - RDS Database <br>&emsp; + Tạo cụm Aurora PostgreSQL <br>&emsp; + Kết nối và kiểm tra <br>&emsp; + Xóa cụm để tránh phát sinh chi phí | 22/04/2026 | 23/04/2026      | <https://000001.awsstudygroup.com/1-aws-free-tier-2025-revolution/> |
| 6   | - Tìm hiểu IAM cơ bản <br>&emsp; + Quản lý truy cập tập trung <br>&emsp; + Kiểm soát quyền cho các tài nguyên AWS <br> - IAM Groups & Users <br>&emsp; + Tạo groups <br>&emsp; + Thêm users <br>&emsp; + Gắn policies <br> - IAM Roles <br>&emsp; + Quyền truy cập tạm thời <br>&emsp; + Chuyển đổi Role (Role switching) | 24/04/2026 | 24/04/2026      | https://000002.awsstudygroup.com/ |


### Kết quả đạt được tuần 1:

* Đã làm quen với các thành viên FCJ và hiểu về nội quy thực tập cũng như cách phối hợp nhóm.

* Khởi tạo và cấu hình thành công tài khoản AWS Free Tier.

* Thiết lập AWS Budgets và tạo các cảnh báo chi phí qua email.

* Hiểu AWS là gì và nắm được các nhóm dịch vụ cơ bản: 
  * Compute
  * Storage
  * Networking 
  * Database
  * Security
  * Monitoring & Management
  * Analytics & AI/ML

* Trở nên quen thuộc với AWS Management Console và biết cách tìm kiếm, truy cập, sử dụng các dịch vụ qua giao diện web.

* Đã cài đặt và cấu hình AWS CLI trên máy tính, bao gồm:
  * Access Key
  * Secret Key
  * Default Region

* Tìm hiểu và thực hành các khái niệm cơ bản về EC2:
  * Instance types, AMI, EBS, Security Group
  * Các phương thức kết nối SSH (Key Pair, PuTTY / Terminal)
  * Elastic IP (khái niệm, cách dùng và cấp phát IP tĩnh)

* Khám phá các kiến trúc serverless và cơ sở dữ liệu:
  * Xây dựng một Lambda Web App từ blueprint
  * Tạo một cụm RDS Aurora PostgreSQL

* Hiểu các khái niệm cơ bản của IAM và quản lý truy cập:
  * Tạo IAM Groups & Users
  * Gắn policies
  * Khám phá IAM Roles (Truy cập tạm thời, chuyển đổi Role)

* Đạt được khả năng kết nối giữa giao diện web và CLI để quản lý tài nguyên AWS song song.
