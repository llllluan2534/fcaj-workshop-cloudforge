---
title: "Worklog Tuần 6"
date: 2024-05-09
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---



### Mục tiêu tuần 6:

* Thiết lập AWS account đúng cách trước khi học CloudWatch.
* Nắm vững các khái niệm cơ bản về Amazon CloudWatch: metrics, logs, events và alarms.
* Tăng cường bảo mật cho root user thông qua việc cấu hình Multi-factor Authentication (MFA).
* Thực hành tạo và quản lý IAM user với quyền quản trị (Administrator Access) cho các tác vụ hàng ngày.
* Khám phá và làm quen với giao diện quản trị CloudWatch Console cũng như AWS CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tổng quan về CloudWatch: Công cụ theo dõi hiệu năng và quản lý service, bao gồm metrics, logs, events và alarms. <br>&emsp; + AWS Account & Root User: Hiểu quyền hạn của root user và lý do không nên dùng cho các tác vụ thường ngày. | 04/06/2026   | 04/06/2026      | <https://000008.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + Bảo mật Root User: Tại sao MFA lại cực kỳ quan trọng trong việc bảo vệ root user. <br>&emsp; + Tạo IAM User Quản trị: Gán quyền quản trị để giảm thiểu rủi ro bảo mật theo best practices của AWS. <br>&emsp; + Truy cập CloudWatch Console: Cách sử dụng IAM user thay thế root user để quản trị CloudWatch. | 05/06/2026   | 05/06/2026      | <https://000008.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Tạo AWS Account mới và hoàn tất quy trình xác thực. <br>&emsp; + Bảo mật Root User: Bật MFA (Virtual/Hardware) cho root account để nâng cao an toàn thông tin. | 06/06/2026   | 06/06/2026      | <https://000008.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Tạo IAM User Quản trị (Administrator Access) và lưu lại thông tin đăng nhập. <br>&emsp; + Cấu hình IAM Identity Center: Tạo permission set và gán quyền. <br>&emsp; + Sử dụng sign-in URL để đăng nhập bằng IAM user mới khởi tạo. | 07/06/2026   | 07/06/2026      | <https://000008.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Truy cập CloudWatch Console: Chọn region, kiểm tra metrics, thử tạo alarm cơ bản. <br>&emsp; + Cài đặt & cấu hình AWS CLI cho IAM user, chạy thử lệnh liên quan đến CloudWatch. <br>&emsp; + Kiểm tra các tài nguyên đang hoạt động, xác nhận metric đẩy lên CloudWatch và dọn dẹp tài nguyên (cleanup). | 08/06/2026   | 08/06/2026      | <https://000008.awsstudygroup.com/> |


### Kết quả đạt được tuần 6:

* Hiểu và thiết lập được một AWS Account hoàn chỉnh với độ bảo mật cao nhất, sẵn sàng cho môi trường production.
* Nắm bắt tầm quan trọng của việc cô lập quyền root user và áp dụng chuẩn best practice của AWS thông qua IAM User.
* Sử dụng và cài đặt thành thạo AWS CLI để tương tác với các tài nguyên AWS từ môi trường terminal.
* Làm quen giao diện quản trị Amazon CloudWatch, biết cách tìm kiếm và phân tích các metrics và alarms căn bản.
* Hoàn thiện khả năng quản lý danh tính với IAM Identity Center và xây dựng thói quen rà soát, dọn dẹp tài nguyên (cleanup) thường xuyên.
