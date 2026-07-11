---
title : "Kiểm tra Kết nối & Tổng hợp Endpoints"
date : 2026-07-10
weight : 5
chapter : false
pre : " <b> 5.4.5. </b> "
---

Sau khi cấp phát thành công RDS PostgreSQL và ElastiCache Redis, bước cuối cùng của phần Thiết lập Cơ sở dữ liệu là **kiểm tra và xác thực khả năng kết nối**. Bước này nhằm đảm bảo hệ thống tường lửa (Security Groups) và cấu hình định tuyến trong mạng nội bộ (Private Subnets) đang hoạt động chính xác theo đúng thiết kế.

Đồng thời, chúng ta sẽ tổng hợp lại toàn bộ các thông số kết nối để đóng gói chúng thành các biến môi trường (`.env`), sẵn sàng tiêm (inject) vào ứng dụng Backend trong các chương tiếp theo.

#### 1. Kiểm tra Kết nối Redis từ EC2
Do cụm Redis bị cô lập hoàn toàn bên trong Private Subnet, chúng ta bắt buộc phải sử dụng máy chủ trung gian EC2 (Bastion Host) nằm trong cùng mạng VPC để thực hiện việc kiểm tra.

Từ giao diện Terminal của máy chủ EC2, hãy tiến hành các bước sau:

**Bước 1: Cài đặt công cụ Redis CLI**
Trên hệ điều hành Amazon Linux 2023, gói công cụ dòng lệnh được AWS tối ưu hóa và định danh là `redis6`:
```bash
sudo dnf install -y redis6
```

**Bước 2: Lệnh Ping đến Redis Cluster**
Sử dụng Primary Endpoint thu thập được ở bài học trước (nhớ xóa phần đuôi định tuyến cổng `:6379` ở cuối chuỗi URL khi gán vào tham số `-h`):
```bash
redis6-cli -h <NHẬP_REDIS_ENDPOINT_CỦA_BẠN> -p 6379 --tls ping
```

**Kinh nghiệm Xử lý Sự cố (Troubleshooting):**
- **Tên lệnh hệ thống:** Đảm bảo bạn sử dụng chính xác lệnh `redis6-cli` thay vì `redis-cli` truyền thống để tương thích với cơ chế quản lý gói tin mới của Amazon Linux 2023.
- **Cờ bảo mật `--tls`:** ElastiCache mặc định kích hoạt mã hóa dữ liệu trên đường truyền (Encryption in transit). Nếu thiếu cờ `--tls`, kết nối từ EC2 đến Redis sẽ bị rơi vào trạng thái im lặng và treo (Timeout).
- **Kiểm tra Tường lửa:** Đảm bảo Security Group của Redis (`cloudforge-db-redis-sg`) đã được cấu hình mở Port 6379 với phần Source (nguồn) chấp nhận lưu lượng đến từ Security Group của ứng dụng (`cloudforge-ecs-app-sg`).

Nếu cấu hình mạng hoàn toàn chính xác, Terminal sẽ phản hồi lại bằng thông điệp:
```plaintext
PONG
```

#### 2. Kết quả Xác thực Kiến trúc Tổng thể
Để chứng minh lớp hạ tầng mạng và bảo mật Zero-Trust đã hoàn toàn thông suốt, chúng ta sẽ chạy đồng thời hai lệnh kiểm tra trạng thái kết nối đến cả dịch vụ Caching (Redis) và Cơ sở dữ liệu lõi (RDS PostgreSQL) ngay trên cùng một cửa sổ dòng lệnh.

![Test Connection Result](/images/5-Workshop/5.4-Database-setup/test_connection.png)

Kết quả trả về trên Terminal là minh chứng kỹ thuật khẳng định:
- Các máy chủ ứng dụng trong tương lai (ECS Tasks / AI Workers) đã có quyền truy cập hoàn toàn hợp lệ và an toàn vào các tầng dữ liệu cốt lõi.
- Vành đai phòng thủ Security Group đang hoạt động đúng thiết kế: Chặn mọi truy cập trái phép từ Internet nhưng mở cửa chính xác cho các tài nguyên nội bộ giao tiếp với nhau.

#### 3. Cấu trúc File Cấu hình Môi trường Mẫu (.env)
Sau khi xác minh các Endpoints hoạt động ổn định, chúng ta tiến hành cấu trúc các thông số này thành định dạng file cấu hình môi trường chuẩn mẫu để chuẩn bị cho việc triển khai Container:
```env
# Cấu hình Database
DB_HOST=cloudforge-db.xxxxxx.ap-southeast-1.rds.amazonaws.com
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=<NHẬP_MẬT_KHẨU_CỦA_BẠN_Ở_ĐÂY>
DB_NAME=cloudforge_db

# Cấu hình Redis Caching & Queue
REDIS_HOST=master.cloudforge-redis.xxxxxx.apse1.cache.amazonaws.com
REDIS_PORT=6379
```

{{% notice warning %}}
**Thực hành Bảo mật Tốt nhất (Best Practice):** Tuyệt đối không bao giờ lưu trữ thông tin nhạy cảm (như `DB_PASSWORD`) dưới dạng văn bản thô (plaintext) trực tiếp trong mã nguồn hoặc các kho lưu trữ mã nguồn mở (GitHub). Đối với một kiến trúc Production thực tế, các thông số này phải được cô lập, quản lý tập trung và tiêm động vào ứng dụng thông qua các dịch vụ chuyên dụng như AWS Secrets Manager.
{{% /notice %}}

***

**Bước tiếp theo:** Hệ thống nền tảng mạng và cơ sở dữ liệu đã sẵn sàng. Chúng ta sẽ chuyển sang phần **5.5: Security Setup** để thiết lập một két sắt quản lý Secrets an toàn, đưa cảnh báo bảo mật phía trên vào thực tiễn!