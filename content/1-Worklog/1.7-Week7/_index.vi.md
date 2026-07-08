---

title: "Worklog Tuần 7"
date: 2026-04-17
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---



### Mục tiêu tuần 7:

* Làm quen với Route 53 Resolver, hiểu cách dùng Outbound Endpoint, Inbound Endpoint và Resolver Rules.
* Thiết lập hệ thống Hybrid DNS giữa môi trường AWS và môi trường on-premise (hoặc AWS Managed AD).
* Cấu hình định tuyến truy vấn DNS đồng nhất, cho phép hai bên phân giải tên miền nội bộ của nhau một cách liền mạch.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tổng quan Hybrid DNS & Route 53 Resolver: Mô hình kết hợp hệ thống DNS on-premise (hoặc AD) với DNS trong AWS. <br>&emsp; + Outbound Endpoint (Red Arrow): Cho phép Route 53 Resolver gửi truy vấn DNS ra ngoài. | 11/06/2026   | 11/06/2026      | <https://000010.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + Resolver Rules (Forwarding rule): Định nghĩa luật chuyển tiếp truy vấn tới DNS server đích qua Outbound Endpoint. <br>&emsp; + Inbound Endpoint (Blue Arrow): Cho phép hệ thống DNS bên ngoài gửi truy vấn vào VPC để Route 53 Resolver trả lời. <br>&emsp; + DNS forwarding từ on-prem/AD về AWS: Cấu hình rule trên DNS nội bộ. | 12/06/2026   | 12/06/2026      | <https://000010.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Chuẩn bị môi trường: Kiểm tra VPC, subnet, security group và môi trường on-prem (hoặc Managed AD) có sẵn. <br>&emsp; + Tạo Outbound Endpoint: Đặt tên, chọn VPC, subnets, gán security group cho phép port 53 (UDP/TCP) và kiểm tra trạng thái "Operational". | 13/06/2026   | 13/06/2026      | <https://000010.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Tạo Resolver Rule forward đến DNS AD/on-prem: Khai báo domain nội bộ, trỏ IP đích về DNS server bên ngoài, gán vào VPC. <br>&emsp; + Tạo Inbound Endpoint: Cấu hình cho phép UDP/TCP port 53 nhận từ ngoài vào và ghi lại IP để dùng cấu hình forwarder. <br>&emsp; + Cấu hình DNS forwarding trên on-prem/AD trỏ về Inbound Endpoint. | 14/06/2026   | 14/06/2026      | <https://000010.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Kiểm tra Private Hosted Zone trên Route 53: Đảm bảo bản ghi A/CNAME trỏ đúng IP private. <br>&emsp; + Kiểm tra phân giải hai chiều: Dùng nslookup/dig trên EC2 AWS để truy vấn domain on-prem (và ngược lại từ on-prem truy vấn AWS private domain). Khắc phục nếu có lỗi. | 15/06/2026   | 15/06/2026      | <https://000010.awsstudygroup.com/> |

### Kết quả đạt được tuần 7:

* Nắm bắt và vận dụng thực tế kiến trúc Hybrid DNS kết nối hệ thống mạng on-premise với môi trường AWS.
* Hiểu sâu sắc và triển khai thành thạo các Inbound & Outbound Endpoints của Amazon Route 53 Resolver.
* Làm chủ việc thiết lập các Resolver Rules để định tuyến các truy vấn DNS (DNS Forwarding) đa chiều một cách chính xác.
* Có khả năng chẩn đoán, troubleshooting và khắc phục sự cố phân giải tên miền giữa nhiều môi trường kết hợp thông qua các công cụ như nslookup hay dig.
* Đảm bảo tính liền mạch và thống nhất cho các ứng dụng chạy lai (hybrid) thông qua hệ thống phân giải tên miền tập trung.
