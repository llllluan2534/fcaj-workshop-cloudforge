---
title : "Điều kiện tiên quyết & IAM"
date : 2026-07-09
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

Để tuân thủ nguyên tắc **Đặc quyền tối thiểu (Least Privilege)** và đảm bảo giao tiếp an toàn giữa các Microservices, chúng ta sẽ thiết lập các Group IAM cụ thể và các Role dựa trên JSON chính xác cho các container ECS Fargate và trình điều phối Step Functions.

#### 0. Tạo IAM Groups & Users (Môi trường Workshop)

Trước khi tạo các role cho service, hãy thiết lập các nhóm (group) IAM để quản lý quyền truy cập console cho nhóm của bạn.

1. Điều hướng đến **IAM > User groups > Create group**.
2. Tạo một nhóm admin:
   - **User group name:** `CloudForge-Admins`
   - **Permissions policy:** `AdministratorAccess`
   
   ![Create Admin Group](/images/5-Workshop/5.2-Prerequisite/iam_group_admin.png)

3. Tạo một nhóm developer (dành cho các thành viên trong nhóm triển khai mà không cần toàn quyền truy cập tài khoản):
   - **User group name:** `CloudForge-Developers`
   - **Permissions policy:** `PowerUserAccess`
   
   ![Create Dev Group](/images/5-Workshop/5.2-Prerequisite/iam_group_dev.png)

4. Chuyển đến **IAM > Users > Create user**, tạo user cho các thành viên trong nhóm của bạn (ví dụ: `cf-vy`, `cf-luan`), và gán họ vào các nhóm phù hợp.

   ![Assign Users](/images/5-Workshop/5.2-Prerequisite/iam_assign_users.png)

#### 1. Tạo IAM Roles cho Compute & Workflow

Trong AWS ECS Fargate, một container yêu cầu hai loại role: một **Execution Role** (để Fargate agent tải image và đẩy log) và một **Task Role** (để mã nguồn (code) thực tế của bạn có thể truy cập các dịch vụ AWS khác).

**Role 1: ECS Task Execution Role (Cấp hệ thống)**
1. Chuyển đến **IAM > Roles > Create role**. Chọn **AWS service > Elastic Container Service > Elastic Container Service Task**.
2. Đính kèm policy được quản lý: `AmazonECSTaskExecutionRolePolicy`.
3. Đặt tên: `ecsTaskExecutionRole` và nhấn Create.

   ![ECS Execution Role](/images/5-Workshop/5.2-Prerequisite/iam_ecs_execution_role.png)

**Role 2: ECS-Backend-TaskRole (API & Vector Search)**
Role này cho phép backend FastAPI/Node.js của bạn chuyển đổi văn bản thành vector qua Bedrock và đọc/ghi vào S3.
1. Chuyển đến **IAM > Policies > Create policy (tab JSON)**.
2. Dán đoạn JSON sau:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowS3Access",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": "arn:aws:s3:::cloudforge-media-storage/*"
        },
        {
            "Sid": "AllowBedrockVectorGeneration",
            "Effect": "Allow",
            "Action": "bedrock:InvokeModel",
            "Resource": "*"
        }
    ]
}
```
3. Đặt tên policy là `cloudforge-backend-policy` và tạo nó.
4. Chuyển đến **Roles > Create role** (Service: Elastic Container Service Task). Đính kèm `cloudforge-backend-policy`.
5. Đặt tên role: `ECS-Backend-TaskRole`.

![ECS Backend Role](/images/5-Workshop/5.2-Prerequisite/iam_ecs_backend_role.png)

**Role 3: ECS-Worker-TaskRole (Xử lý AI Nặng)**
Role này cho phép worker xử lý nền không đồng bộ (asynchronous) trích xuất cảnh quay, gọi Bedrock để phân tích đa phương thức, và gọi Transcribe cho tác vụ Speech-to-Text.

1. Chuyển đến **IAM > Policies > Create policy (tab JSON)**.
2. Dán đoạn JSON sau:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowFullS3MediaAccess",
            "Effect": "Allow",
            "Action": ["s3:GetObject", "s3:PutObject", "s3:ListBucket"],
            "Resource": ["arn:aws:s3:::cloudforge-media-storage", "arn:aws:s3:::cloudforge-media-storage/*"]
        },
        {
            "Sid": "AllowAIAndMLServices",
            "Effect": "Allow",
            "Action": [
                "bedrock:InvokeModel",
                "transcribe:StartTranscriptionJob",
                "transcribe:GetTranscriptionJob"
            ],
            "Resource": "*"
        }
    ]
}
```
3. Đặt tên policy là `cloudforge-ai-worker-policy`. Tạo nó, sau đó đính kèm vào một role mới có tên `ECS-Worker-TaskRole`.

![ECS Worker Role](/images/5-Workshop/5.2-Prerequisite/iam_ecs_worker_role.png)

**Role 4: StepFunctions-Orchestrator**
Role này cho phép Step Functions State Machine kích hoạt ECS AI Worker và tiêu thụ (consume) tin nhắn SQS.

1. Chuyển đến **IAM > Policies > Create policy (tab JSON)**.
2. Dán đoạn JSON sau:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowRunECSTask",
            "Effect": "Allow",
            "Action": "ecs:RunTask",
            "Resource": "arn:aws:ecs:*:*:task-definition/cloudforge-ai-worker:*"
        },
        {
            "Sid": "AllowPassRoleToECS",
            "Effect": "Allow",
            "Action": "iam:PassRole",
            "Resource": [
                "arn:aws:iam::*:role/ecsTaskExecutionRole",
                "arn:aws:iam::*:role/ECS-Worker-TaskRole"
            ]
        },
        {
            "Sid": "AllowSQSReceive",
            "Effect": "Allow",
            "Action": [
                "sqs:ReceiveMessage",
                "sqs:DeleteMessage",
                "sqs:GetQueueAttributes"
            ],
            "Resource": "arn:aws:sqs:*:*:cloudforge-ingest-queue"
        }
    ]
}
```
3. Đặt tên policy là `cloudforge-orchestrator-policy`.
4. Tạo một role (Trusted Entity: Step Functions) có tên `StepFunctions-Orchestrator` và đính kèm policy này.

![Final IAM Roles](/images/5-Workshop/5.2-Prerequisite/iam_final_roles.png)

#### 2. Cài đặt môi trường cục bộ (Local Environment Setup)
Trước khi bắt đầu triển khai, hãy đảm bảo máy của bạn đã được cài đặt các công cụ sau:

- **Git:** Để sao chép (clone) repository dự án.
- **Docker:** Để build các image frontend và backend ở local trước khi đẩy lên ECR.
- **AWS CLI:** Được cấu hình thông tin xác thực để chạy các lệnh triển khai.

Kiểm tra cấu hình AWS CLI của bạn:
```bash
aws configure
aws sts get-caller-identity
```
![AWS CLI Config](/images/5-Workshop/5.2-Prerequisite/aws_cli_config.png)

#### 3. Quyền truy cập Amazon Bedrock Model (Bản cập nhật mới của AWS)

Trước đây, Amazon Bedrock yêu cầu phải kích hoạt thủ công các foundation models cụ thể. Tuy nhiên, theo bản cập nhật mới nhất của AWS, trang Model Access đã bị gỡ bỏ.

Các Serverless foundation models (bao gồm **Nova Lite** và **Titan Embeddings** sử dụng trong dự án của chúng ta) hiện được **tự động kích hoạt** trên tất cả các commercial regions của AWS ngay trong lần gọi đầu tiên vào tài khoản. Do đó, bạn không cần phải thao tác thủ công trên AWS Console cho bước này nữa.

![Bedrock Model Access Auto](/images/5-Workshop/5.2-Prerequisite/bedrock_access_retired.png)