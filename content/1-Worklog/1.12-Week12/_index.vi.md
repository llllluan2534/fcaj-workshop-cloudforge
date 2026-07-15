---
title: "Worklog Tuần 12"
date: 2026-04-17
weight: 12
chapter: false
pre: " <b> 1.12 </b> "
---
### Mục tiêu tuần 12:

Thực hiện quá trình tích hợp và kiểm thử toàn bộ hệ thống (End-to-End) trên môi trường Staging Cloud thực tế để đánh giá tính sẵn sàng của kiến trúc trước khi ra mắt Production. Mục tiêu là phát hiện và xử lý dứt điểm các lỗi "hạ tầng Cloud ẩn" như IAM Roles, CORS, Network VPC, và giới hạn phần cứng thực.

**Target Branch:**
`main` (Staging environment)

### Các công việc cần triển khai trong tuần này (Tasks & Implementation Steps):
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2   | - **Test Kịch Bản Dòng Chảy Chính (Golden Flow):** <br>&emsp; + Thực hiện upload thành công 1 file video (độ dài > 5 phút) qua UI Staging. <br>&emsp; + Xác nhận App Runner nhận request và trigger thành công AWS Step Functions / ECS. <br>&emsp; + Xác nhận tiến trình WebSocket truyền về Frontend thông suốt. <br>&emsp; + Xác nhận Pipeline hoàn thành 100%. <br>- **Validate AWS IAM & Security:** <br>&emsp; + ECS Task lấy được file từ S3 mà không bị Access Denied. <br>&emsp; + App Runner đọc/ghi thành công vào RDS. <br>&emsp; + App Runner gọi được AWS Bedrock và SQS/Step Functions thành công. | 06/07/2026 | 06/07/2026 | [Internal Docs](#) |
| 3   | - **Validate Frontend WaveSurfer & S3 CORS:** <br>&emsp; + Đảm bảo trang Asset Detail load được `stream_url` (Presigned URL của S3). <br>&emsp; + Xác nhận thư viện WaveSurfer có thể kéo từng chunk byte-range từ S3 mà không bị đụng lỗi CORS Policy hay quá thời gian token. | 07/07/2026 | 07/07/2026 | [Internal Docs](#) |
| 4   | - **Test Phục Hồi Kết Nối & Đồng Bộ Trạng Thái (WebSocket Reconnect):** <br>&emsp; + Thực hiện upload 1 video dài, ngay khi tiến trình xử lý đạt khoảng 30%, tắt hoàn toàn tab trình duyệt. <br>&emsp; + Đợi 2 phút, sau đó mở lại ứng dụng. <br>&emsp; + Xác nhận Frontend khôi phục được trạng thái chính xác từ mảng `ingest_jobs` và tiếp tục theo dõi tiến trình trơn tru, chứng minh cơ chế EventBridge ➜ DB ➜ Redis hoạt động đúng đắn. | 08/07/2026 | 08/07/2026 | [Internal Docs](#) |
| 5   | - **Failure Testing (Kiểm Thử Kịch Bản Lỗi & Khôi Phục):** <br>&emsp; + Giả lập ECS Task crash giữa chừng (vd: out of memory do file video quá to). <br>&emsp; + Giả lập AWS Bedrock bị timeout / Rate Limit. <br>&emsp; + Giả lập Transcribe thất bại. <br>&emsp; + Giả lập file S3 không tồn tại. <br>&emsp; + Xác nhận cơ chế Retry và Catch của Step Functions hoạt động đúng. | 09/07/2026 | 09/07/2026 | [Internal Docs](#) |
| 6   | - **Cost Validation & Performance Audit:** <br>&emsp; + Upload thử 1 video 5 phút và đo đạc chi phí thực tế sinh ra trên hóa đơn AWS: Ghi nhận chi phí MediaConvert, AWS Transcribe, AWS Bedrock, và ECS Task. Ước lượng Cost/Video. <br>&emsp; + Kiểm tra xem App Runner có Auto-scale khi bắn nhiều request hay không. <br>&emsp; + Check CloudWatch Logs xem có rác (spam logs) hoặc lỗi ẩn nào bị in ra không. | 10/07/2026 | 10/07/2026 | [Internal Docs](#) |

### Kết quả đạt được tuần 12 (Definition of Done - DoD):

* ✅ Video 5 phút được xử lý và hiển thị Waveform, Transcript, Scene chính xác 100% trên Cloud.
* ✅ Lỗi liên quan đến IAM Role, S3 CORS, và VPC Network được khắc phục triệt để.
* ✅ Hệ thống khôi phục hoàn hảo trạng thái khi đóng/mở tab trình duyệt.
* ✅ Các kịch bản lỗi (Crash, Timeout) đều được bắt đúng cách (Catch) và cập nhật báo lỗi an toàn tới UI.
* ✅ Báo cáo Cost Validation (chi phí ước tính/video) được chốt.
* ✅ Xác nhận toàn bộ hệ thống đạt tiêu chuẩn MVP Ready trên AWS:
  * Khởi tạo hạ tầng mạng, bảo mật và cơ sở dữ liệu trên AWS.
  * Xây dựng luồng xử lý AI tự động (SQS, Step Functions, Amazon Bedrock).
  * Thiết lập pipeline CI/CD tự động deploy Backend/AI Worker lên ECS Fargate.
  * Cấu hình Load Balancer và tích hợp thành công luồng WebSocket.
  * Triển khai Frontend (Amplify) và thiết lập hệ thống giám sát (CloudWatch, X-Ray).
  * Soạn thảo tài liệu Workshop hướng dẫn triển khai toàn bộ kiến trúc dự án.
