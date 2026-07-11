---
title : "Tạo S3 Bucket"
date : 2026-07-10
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

Thành phần lưu trữ đầu tiên và quan trọng nhất của toàn bộ hệ thống Smart Media Analytics là **Amazon S3 (Simple Storage Service)**. Đây sẽ là nơi tiếp nhận, lưu trữ và bảo quản tất cả các file video và audio gốc do người dùng tải lên.

Để đảm bảo tính duy nhất trên toàn cầu và bảo mật dữ liệu, chúngữẽ khởi tạo một Bucket mới.

#### 1. Quá trình Khởi tạo Amazon S3 Bucket
Truy cập dịch vụ **Amazon S3** trên AWS Console → Nhấp **Create bucket**. Cấu hình các chi tiết thông qua các phân đoạn trực quan trên giao diện:

1. **Phân đoạn General configuration (Cấu hình chung):**
   - **AWS Region:** Chọn `ap-southeast-1` (Singapore) - Đảm bảo nằm cùng khu vực (region) với hạ tầng mạng VPC để tối ưu hóa độ trễ truyền tải.
   - **Bucket name:** Nhập `cloudforge-media-upload-<tên-của-bạn>` *(Lưu ý: Tên Bucket phải là định danh duy nhất trên toàn cầu trong toàn bộ hệ thống AWS).*
2. **Phân đoạn Object Ownership (Quyền sở hữu đối tượng):** Giữ nguyên cài đặt mặc định `ACLs disabled (recommended)` để quản lý quyền truy cập tập trung thông qua các chính sách IAM.
3. **Phân đoạn Block Public Access settings for this bucket:** 
   - Tích chọn **Block all public access**. Đây là tiêu chuẩn bảo mật bắt buộc (Best Practice) để cách ly hoàn toàn tài nguyên lưu trữ khỏi môi trường Internet công cộng, chỉ cho phép các dịch vụ thuộc tầng Backend truy cập nội bộ.
4. **Phân đoạn Bucket Versioning & Default encryption:** Giữ nguyên các thông số cấu hình mặc định (Tự động mã hóa bằng cơ chế SSE-S3).

Cuộn xuống cuối trang biểu mẫu và nhấp vào **Create bucket** để hoàn tất quá trình.

#### 2. Kích hoạt Chuyển tiếp Sự kiện đến Amazon EventBridge (Quan trọng)
Theo mặc định của hệ thống, Amazon S3 sẽ không chủ động phát dữ liệu sự kiện ra bên ngoài. Để luồng điều phối tác vụ (orchestration pipeline) bất đồng bộ trong Chương 5.6 hoạt động được, chúng ta cần kích hoạt tính năng thông báo:

1. Trong danh sách Buckets, nhấp vào tên của Bucket vừa tạo.
2. Điều hướng đến tab **Properties** trên thanh menu ngang.
3. Cuộn xuống phân đoạn **Amazon EventBridge**, nhấp **Edit**.
4. Chuyển trạng thái từ *Off* sang **On** và nhấp **Save changes**.

{{% notice tip %}}
**Lưu ý Thiết kế Hệ thống:** Việc chuyển trạng thái sang *On* cho phép Amazon S3 tự động đóng gói metadata dưới định dạng JSON và đẩy trực tiếp vào event Bus mặc định của EventBridge bất cứ khi nào có hành động tải file lên (`ObjectCreated`) xảy ra.
{{% /notice %}}

#### 3. Kết quả Triển khai
Hạ tầng lưu trữ phi cấu trúc (Object Storage) đã được thiết lập thành công và sẵn sàng đóng vai trò là nguồn cung cấp tác vụ cho toàn bộ luồng xử lý tự động ở các phần sau.

![S3 EventBridge Config](/images/5-Workshop/5.4-Database-setup/s3_eventbridge_enabled.png)

***

**Bước tiếp theo:** Hệ thống Lưu trữ File hiện đã sẵn sàng. Chúng ta sẽ tiếp tục thiết lập bộ nhớ dữ liệu có cấu trúc ở phần **5.4.2: Tạo RDS PostgreSQL** để phục vụ việc lưu trữ metadata và vector tìm kiếm cho AI.
