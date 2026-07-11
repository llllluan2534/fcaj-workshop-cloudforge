---
title : "Tổng quan kiến trúc"
date : 2026-07-09
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Kiến trúc Smart Media Analytics (Team CloudForge)

**Smart Media Analytics** là một giải pháp phân tích video toàn diện, kết hợp sức mạnh của Generative AI với kiến trúc Serverless và Event-Driven trên AWS. Hệ thống được thiết kế với khả năng mở rộng cao, có thể xử lý các file video dung lượng lớn, trích xuất metadata thông minh và cung cấp tính năng Tìm kiếm Ngữ nghĩa (Semantic Search).

Dưới đây là sơ đồ kiến trúc tổng thể của toàn bộ hệ thống:

![Platform Architecture Overview](/images/5-Workshop/5.1-Workshop-overview/SMA_diagram.png)

#### Các luồng xử lý chính (Key Workflows)

1. **Frontend & Xác thực (Authentication):**
   - Web Application được lưu trữ trên **AWS Amplify**, với **Route 53** xử lý định tuyến DNS.
   - Việc xác thực người dùng được quản lý bởi **Amazon Cognito**, cấp phát các JWT token bảo mật.
   - Các API request từ client được xác thực bởi **API Gateway** và định tuyến qua **Application Load Balancer (ALB)** đến dịch vụ Backend API chạy trên **Amazon ECS (AWS Fargate)**.

2. **Tiếp nhận & Điều phối (Ingestion & Orchestration):**
   - Người dùng tải trực tiếp các file media lên **Amazon S3** một cách an toàn.
   - Một *Sự kiện Thông báo (Event Notification)* được kích hoạt và gửi đến hàng đợi tiếp nhận **Amazon SQS**.
   - Sự kiện được chuyển tiếp đến **Amazon EventBridge**, sau đó kích hoạt **AWS Step Functions**.
   - **Step Functions** đóng vai trò là bộ điều phối trung tâm, quản lý quy trình xử lý video từ đầu đến cuối.

3. **Luồng xử lý AI (AI Processing Pipeline):**
   - Các tác vụ tính toán nặng được thực thi trên **ECS AI Worker (AWS Fargate)** bên trong các Private Subnet (với Auto Scaling trải khắp các Availability Zone A & B).
   - ECS Worker kéo video xuống và lưu các keyframe vào S3 một cách an toàn thông qua **S3 Gateway Endpoint**, đảm bảo lưu lượng mạng luôn nằm trên hạ tầng toàn cầu của AWS và tối ưu hóa chi phí truyền tải dữ liệu.
   - Quá trình xử lý tận dụng các dịch vụ AI/ML được quản lý của AWS:
     - **Amazon Transcribe**: Chuyển đổi giọng nói thành văn bản (Speech-to-Text).
     - **Amazon Bedrock (Nova Lite & Titan Embeddings)**: Phân tích đa phương thức và tạo vector embeddings.
   - Tiến trình công việc được Worker xuất bản lên **ElastiCache for Redis** trong private subnet. **ECS Backend API** đăng ký (subscribe) các sự kiện này và đẩy các cập nhật tiến trình theo thời gian thực trực tiếp đến client thông qua kết nối **WebSocket (WSS)** được quản lý bởi ALB.

4. **Lưu trữ dữ liệu & Tìm kiếm ngữ nghĩa (Data Persistence & Semantic Search):**
   - Khi hoàn thành, ECS AI Worker ghi metadata và vector embeddings trực tiếp vào **RDS PostgreSQL** (được cấu hình Multi-AZ Primary/Replica để đảm bảo tính sẵn sàng cao).
   - Trong quá trình gửi yêu cầu tìm kiếm, **ECS Backend API** gọi Bedrock để tạo Query Vector và truy cập trực tiếp vào cơ sở dữ liệu RDS để thực thi Vector Search.

5. **CI/CD & Khả năng quan sát (Observability):**
   - **GitHub Actions** tự động hóa quy trình build, đẩy các Docker image lên **Amazon ECR**.
   - Sức khỏe hệ thống, truy vết (traces) và hiệu suất được theo dõi bằng **CloudWatch** (Logs, Metrics, Alarms) và **AWS X-Ray** (Distributed Tracing).
