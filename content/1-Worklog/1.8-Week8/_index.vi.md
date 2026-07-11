---
title: "Worklog Tuần 8"
date: 2026-04-17
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---



### Mục tiêu tuần 8:

* Làm quen với AWS CLI, hiểu được sự tương quan giữa các lệnh CLI và API của AWS.
* Thực hiện cài đặt và cấu hình thành công AWS CLI trên hệ điều hành cá nhân (Windows, macOS hoặc Linux).
* Quản lý an toàn credentials (Access key ID, Secret access key) thông qua thư mục `.aws` thay vì dùng root account.
* Thực hành thao tác với đa dạng dịch vụ (IAM, S3, EC2) trực tiếp từ dòng lệnh.
* Nắm vững các bước dọn dẹp credentials để đảm bảo an toàn bảo mật.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tổng quan về AWS CLI: Công cụ dòng lệnh quản lý AWS từ terminal thay cho web console, hỗ trợ tốt cho tự động hóa và DevOps. Mỗi lệnh CLI tương ứng một API của AWS. <br>&emsp; + IAM user & credentials: Yêu cầu bắt buộc dùng IAM user (Access Key ID / Secret Access Key), không dùng root account. Credentials được lưu cục bộ để CLI xác thực. <br>- **Project - Smart Media Analysics (Frontend):** <br>&emsp; + Tích hợp API Search qua React Query gọi endpoint `POST /api/v1/search`. <br>&emsp; + Đồng bộ hóa trạng thái tìm kiếm (query, media_type, tags) lên URL Search Params. | 18/06/2026   | 18/06/2026      | <https://000011.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + Cách cấu hình AWS CLI: Dùng lệnh `configure` để thiết lập Access key, region và format. CLI tự động đọc credentials từ thư mục config máy local. <br>&emsp; + Các lệnh cơ bản: Kiểm tra version, danh tính IAM (`sts get-caller-identity`); thao tác S3 (liệt kê, tạo, xóa); thao tác EC2 (liệt kê regions/instances); thao tác IAM (liệt kê user/policies). <br>- **Project - Smart Media Analysics (Frontend):** <br>&emsp; + Xử lý Abort Request tránh race condition và điều khiển khóa giao diện (UI Lock) khi Loading. <br>&emsp; + Xây dựng Empty Query Validation, kiểm soát hiển thị lỗi và quản lý Search History. | 19/06/2026   | 19/06/2026      | <https://000011.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Chuẩn bị IAM user & credentials: Tạo IAM user cho CLI, tạo Access Key (use case CLI), lưu lại ID/Secret Key và region lab. <br>&emsp; + Cài đặt AWS CLI: Tải và cài đặt theo hệ điều hành (Windows, macOS, Linux). Chạy thử kiểm tra phiên bản trên terminal để xác nhận. <br>&emsp; + Cấu hình lần đầu: Chạy `aws configure` nhập credentials, region, output format và kiểm tra file cấu hình. | 20/06/2026   | 20/06/2026      | <https://000011.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Kiểm tra danh tính: Chạy lệnh IAM xác nhận account ID và ARN khớp với lab. <br>&emsp; + Thao tác S3: Dùng CLI liệt kê buckets hiện có, tạo một S3 bucket mới (nếu lab yêu cầu) và xác minh lại bằng lệnh liệt kê. <br>&emsp; + Thao tác EC2: Dùng CLI liệt kê regions, liệt kê EC2 instances trong region đang dùng, xem thông tin một instance cụ thể. | 21/06/2026   | 21/06/2026      | <https://000011.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Thao tác IAM: Dùng CLI liệt kê các IAM user, kiểm tra policies được gắn vào user hiện tại để xác minh quyền hạn theo lab. <br>&emsp; + Dọn dẹp: Xóa Access Key trên AWS Console để đảm bảo an toàn nếu dùng máy public; xóa file cấu hình cục bộ nếu không muốn giữ credentials. | 22/06/2026   | 22/06/2026      | <https://000011.awsstudygroup.com/> |

### Kết quả đạt được tuần 8:

* Hoàn thành thao tác cài đặt và cấu hình AWS CLI phù hợp với môi trường hệ điều hành cá nhân.
* Hiểu rõ cơ chế xác thực qua Access key và Secret key, đảm bảo thực hành chuẩn bảo mật khi làm việc với AWS.
* Tự tin quản lý tài nguyên từ xa bằng CLI với nhiều dịch vụ phổ biến (Amazon S3, Amazon EC2, IAM).
* Rèn luyện kỹ năng đọc hiểu kết quả đầu ra (output JSON) và áp dụng tham số `--query` để trích xuất dữ liệu mong muốn.
* Xây dựng thói quen tốt về quản trị rủi ro bằng việc vô hiệu hóa hoặc xóa credentials cục bộ sau khi kết thúc dự án.
