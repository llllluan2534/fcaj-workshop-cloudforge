---
title: "Worklog Tuần 4"
date: 2026-04-17
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu tuần 4:

* Hiểu sâu sắc về kiến trúc và ưu điểm của dịch vụ cơ sở dữ liệu quan hệ được quản lý (Managed Relational Database) - Amazon RDS.
* Nắm vững các mô hình triển khai DB instance, cách lựa chọn Database Engine phù hợp (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server).
* Thực hành tạo, cấu hình và kết nối an toàn đến Amazon RDS từ các môi trường mạng (VPC).
* Hiểu rõ cơ chế bảo mật cơ sở dữ liệu trên cloud thông qua Security Group và Network ACLs.
* Rèn luyện kỹ năng quản trị chi phí thông qua việc dọn dẹp và xóa bỏ tài nguyên không sử dụng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tổng quan về Amazon RDS: Tìm hiểu cách AWS tự động hóa các tác vụ quản trị nặng nề như provisioning, patch hệ điều hành, backup và monitoring. <br>&emsp; + Kiến trúc DB instance: Môi trường database độc lập trên cloud, linh hoạt lựa chọn cấu hình compute và storage. | 07/05/2026   | 07/05/2026      | <https://000005.awsstudygroup.com/>       |
| 3   | - **Learning Content:** <br>&emsp; + Các Database Engine được hỗ trợ: Đánh giá ưu nhược điểm của MySQL, PostgreSQL, MariaDB, SQL Server, và Oracle. <br>&emsp; + Cơ chế kết nối: Kiến trúc mạng trong VPC, vai trò của endpoint và port khi kết nối từ ứng dụng hoặc client. | 08/05/2026   | 08/05/2026      | <https://000005.awsstudygroup.com/>       |
| 4   | - **Learning Content:** <br>&emsp; + Bảo mật và phân quyền truy cập: Tầm quan trọng của việc cô lập database trong private subnet. <br>&emsp; + Dọn dẹp tài nguyên: Hiểu vòng đời của DB instance, snapshot và cách quản lý chi phí lâu dài. | 09/05/2026   | 09/05/2026      | <https://000005.awsstudygroup.com/>       |
| 5   | - **Practice:** <br>&emsp; + Chuẩn bị môi trường: Khảo sát và cấu hình VPC, Subnet, Security Group đảm bảo kiến trúc mạng an toàn. <br>&emsp; + Khởi tạo DB instance: Chọn engine (ví dụ MySQL), thiết lập username/password gốc, chỉ định network và security group, sau đó chờ instance chuyển sang trạng thái Available. | 10/05/2026   | 10/05/2026      | <https://000005.awsstudygroup.com/>       |
| 6   | - **Practice:** <br>&emsp; + Kết nối vào database: Lấy endpoint từ console, dùng tool (như MySQL Workbench, DBeaver hoặc terminal) để kết nối và chạy thử các truy vấn SQL cơ bản. <br>&emsp; + Tối ưu bảo mật: Tinh chỉnh Security Group chỉ mở port cho những IP/Instance cần thiết. <br>&emsp; + Resource Cleanup: Xóa toàn bộ DB instance và các manual snapshot đi kèm để tối ưu hóa chi phí. | 11/05/2026   | 11/05/2026      | <https://000005.awsstudygroup.com/>       |


### Kết quả đạt được tuần 4:

* Hiểu và vận dụng thành thạo dịch vụ Amazon RDS để thiết lập cơ sở dữ liệu quan hệ trên môi trường AWS.
* Có khả năng lên kế hoạch mạng và bảo mật chặt chẽ cho database bằng cách sử dụng VPC, Subnet, và Security Group.
* Khởi tạo thành công DB instance và thực hiện kết nối, truy vấn dữ liệu thông qua các công cụ quản trị phổ biến.
* Thấu hiểu sâu sắc các nguyên tắc bảo mật: Không bao giờ mở public access cho database trừ khi bắt buộc, và tuân thủ nguyên tắc least privilege.
* Hoàn thành xuất sắc khâu dọn dẹp (cleanup), đảm bảo không để lại tài nguyên rác gây lãng phí ngân sách.
