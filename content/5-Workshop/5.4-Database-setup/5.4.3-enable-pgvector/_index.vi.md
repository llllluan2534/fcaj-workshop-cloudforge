---
title : "Kích hoạt pgvector"
date : 2026-07-10
weight : 3
chapter : false
pre : " <b> 5.4.3. </b> "
---

Khi phiên bản Amazon RDS PostgreSQL đã được cấp phát thành công, bước tiếp theo là kết nối vào cơ sở dữ liệu và kích hoạt `pgvector` - extension cốt lõi giúp biến PostgreSQL truyền thống thành một cơ sở dữ liệu vector (Vector Database) có khả năng lưu trữ AI embeddings.

Do cụm RDS của chúng ta được đặt an toàn trong **Private Subnet** (tuân thủ mô hình Zero-Trust), nó không thể bị truy cập trực tiếp từ Internet. Thay vào đó, thao tác này phải được thực hiện thông qua một máy chủ trung gian (Bastion Host / EC2) nằm bên trong VPC.

#### 1. Lấy Thông tin Kết nối (Endpoint)
1. Điều hướng đến **RDS Console** → **Databases**.
2. Nhấp vào `cloudforge-db` (đảm bảo trạng thái của nó đã chuyển sang *Available*).
3. Trong tab **Connectivity & security**, sao chép đoạn URL dưới phần **Endpoint** (ví dụ: `cloudforge-db.xxxxxx.ap-southeast-1.rds.amazonaws.com`).

#### 2. Kết nối và Kích hoạt Extension
Chúng ta sẽ sử dụng một máy chủ EC2 (Bastion Host) được gắn Security Group `cloudforge-ecs-app-sg` để xuyên qua tường lửa của Database. Từ giao diện Terminal của EC2, hãy thực thi lần lượt các lệnh sau:

**Cài đặt công cụ PostgreSQL Client:**
```bash
sudo dnf install -y postgresql15
```

**Kết nối vào cơ sở dữ liệu:**
```bash
psql -h <NHẬP_ENDPOINT_CỦA_BẠN_Ở_ĐÂY> -U postgres -d cloudforge_db
```
*(Hệ thống sẽ yêu cầu bạn nhập mật khẩu; hãy nhập mật khẩu master mà bạn đã thiết lập trong quá trình khởi tạo RDS).*

Sau khi đăng nhập thành công vào giao diện dòng lệnh của PostgreSQL (`cloudforge_db=>`), hãy chạy lệnh SQL sau để kích hoạt extension:

```sql
CREATE EXTENSION IF NOT EXISTS vector;
```

#### 3. Kiểm tra Cài đặt
Để xác nhận extension đã được cài đặt thành công, hãy chạy lệnh:

```sql
SELECT extname, extversion FROM pg_extension WHERE extname = 'vector';
```

Nếu kết quả trả về hiển thị `vector` kèm theo phiên bản (ví dụ: `0.8.1`), xin chúc mừng! Cơ sở dữ liệu của bạn giờ đây đã hoàn toàn sẵn sàng để lưu trữ các vector đa chiều được tạo ra bởi Amazon Titan.

![Enable pgvector](/images/5-Workshop/5.4-Database-setup/enable_pgvector.png)

***

**Bước tiếp theo:** Với tầng lưu trữ dữ liệu bền vững (persistent data) đã hoàn tất, chúng ta sẽ chuyển sang phần **5.4.4: Tạo ElastiCache (Redis)** để xây dựng bộ nhớ đệm tốc độ cao và Message Queue cho AI Workers.
