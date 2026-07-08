---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---


### Mục tiêu tuần 10:

* Hiểu rõ khái niệm IAM role và ứng dụng của nó trong việc cấp quyền an toàn cho các dịch vụ AWS.
* Nắm vững nguyên tắc cấp quyền tối thiểu (least privilege) để bảo vệ tài nguyên hiệu quả.
* Thực hành tạo, gắn và kiểm tra IAM role trên EC2 instance.
* Làm quen với AWS Cloud9, một môi trường IDE trên nền tảng đám mây.
* Quản lý chi phí bằng cách vận hành và dọn dẹp tài nguyên (Cloud9, IAM role) hợp lý.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tìm hiểu IAM role là gì và cách ứng dụng truy cập AWS services an toàn (không hardcode access key). <br>&emsp; + Nắm vững các nguyên tắc cấp quyền tối thiểu. | 28/05/2026 | 28/05/2026 | <https://000048.awsstudygroup.com/> |
| 3   | - **Practice:** <br>&emsp; + Tạo IAM role và gắn policy cần thiết. <br>&emsp; + Gắn role vào EC2 instance và kiểm tra quyền truy cập. <br>&emsp; + Thực hiện dọn dẹp role khỏi instance khi không còn sử dụng. | 29/05/2026   | 29/05/2026      | <https://000048.awsstudygroup.com/>       |
| 4   | - **Learning Content:** <br>&emsp; + Tìm hiểu AWS Cloud9 là gì và cách thức hoạt động dựa trên EC2. <br>&emsp; + Khám phá cách làm việc trong IDE (file explorer, terminal, editor) ngay trên trình duyệt. | 30/05/2026   | 30/05/2026      | <https://000049.awsstudygroup.com/>       |
| 5   | - **Practice:** <br>&emsp; + Tạo Cloud9 environment với cấu hình instance và nền tảng phù hợp. <br>&emsp; + Mở IDE, thử code, thao tác file và kết nối thử với tài nguyên AWS. | 31/05/2026   | 31/05/2026      | <https://000049.awsstudygroup.com/>       |
| 6   | - **Learning & Practice:** <br>&emsp; + Tìm hiểu về quản lý chi phí cho Cloud9 (dừng instance khi không dùng). <br>&emsp; + Dừng môi trường sau khi hoàn thành lab và kiểm tra tài nguyên EC2 backend để tránh phát sinh chi phí. | 01/06/2026   | 01/06/2026      | <https://000049.awsstudygroup.com/>       |

### Kết quả đạt được tuần 10:

* Hiểu và vận dụng thành công IAM role để cấp quyền cho ứng dụng chạy trên EC2 truy cập an toàn các dịch vụ AWS.
* Nắm vững cách quản lý, điều chỉnh và dọn dẹp các quyền không cần thiết tuân theo nguyên tắc quyền hạn tối thiểu.
* Khởi tạo và thiết lập thành công môi trường lập trình đám mây AWS Cloud9.
* Thực hiện thành công việc lập trình, chạy lệnh và kết nối tài nguyên ngay trên trình duyệt thông qua Cloud9 IDE.
* Đảm bảo kiểm soát chi phí tốt thông qua việc dừng hoặc tắt các môi trường Cloud9/EC2 khi không có nhu cầu sử dụng.
