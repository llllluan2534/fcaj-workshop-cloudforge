---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Tại phần này, bạn cần tóm tắt các nội dung trong workshop mà bạn **dự tính** sẽ làm.

# Smart Media Analytics
## Giải pháp AI nội bộ cho quản lý, tìm kiếm và phân tích media theo ngữ nghĩa

### 1. Tóm tắt điều hành
Smart Media Analytics (SMA) là một hệ thống quản lý và tìm kiếm media theo hướng local-first, được thiết kế cho video editor, designer và nhóm nghiên cứu cần tra cứu nhanh nội dung hình ảnh, video và âm thanh. Hệ thống cho phép nạp media, tự động tách cảnh, phiên âm nội dung, mô tả ngữ cảnh bằng AI và tìm kiếm bằng ngôn ngữ tự nhiên, giúp người dùng nhanh chóng tìm đúng asset hoặc đúng timestamp trong video mà không cần xem thủ công toàn bộ file.

Trong giai đoạn phát triển nội bộ, SMA ưu tiên chạy hoàn toàn trên máy cục bộ thông qua Docker để đảm bảo tính riêng tư dữ liệu và giảm chi phí thử nghiệm. Khi cần mở rộng lên môi trường sản xuất, hệ thống có thể chuyển sang AWS với kiến trúc tương ứng gồm S3, Bedrock, Transcribe, OpenSearch Serverless, RDS PostgreSQL, CloudFront, Cognito và WAF. Cách tiếp cận này giúp SMA vừa phù hợp cho giai đoạn prototype, vừa có khả năng mở rộng rõ ràng về lâu dài.

### 2. Tuyên bố vấn đề
**Vấn đề hiện tại**
Việc quản lý media thường gặp khó khăn vì dữ liệu nằm rải rác nhiều nơi, tên file không phản ánh nội dung, và việc tìm đúng cảnh hoặc câu thoại trong video phải thực hiện thủ công. Với các dự án sáng tạo hoặc nghiên cứu, điều này làm mất rất nhiều thời gian, đặc biệt khi thư viện media tăng lên theo thời gian. Ngoài ra, nếu dùng trực tiếp các dịch vụ AI cloud cho toàn bộ pipeline, chi phí có thể tăng nhanh và dữ liệu nội bộ có nguy cơ bị lộ ra ngoài.

**Giải pháp**
SMA giải quyết bài toán này bằng một pipeline xử lý media tự động theo hướng local-first. Hệ thống sử dụng React dashboard để duyệt asset, FastAPI để cung cấp API, ChromaDB để lưu và truy vấn vector embedding, PostgreSQL để lưu metadata, MinIO để lưu object media, Ollama để chạy mô hình vision và embedding nội bộ, cùng faster-whisper để phiên âm âm thanh.
Khi triển khai trên AWS, các thành phần này được ánh xạ sang kiến trúc production tương ứng: MinIO sang Amazon S3, Ollama vision model sang AWS Bedrock, faster-whisper sang Amazon Transcribe, ChromaDB sang Amazon OpenSearch Serverless và PostgreSQL sang Amazon RDS PostgreSQL. Bên cạnh đó, hệ thống cloud còn có thể dùng CloudFront, Cognito, WAF, ECR, CloudWatch, Secrets Manager và CI/CD qua GitHub Actions để hoàn thiện vòng đời triển khai.

**Lợi ích và hoàn vốn đầu tư (ROI)**
Giải pháp giúp rút ngắn đáng kể thời gian tìm kiếm footage, đọc transcript và xác định cảnh cần dùng, từ đó tăng hiệu quả làm việc cho nhóm sáng tạo. Người dùng có thể nhập truy vấn tự nhiên như “cảnh hoàng hôn trên biển có tiếng sóng” và nhận kết quả đúng đoạn video, đúng timestamp, thay vì phải xem thủ công toàn bộ file.
Về dài hạn, SMA có thể phục vụ như một nền tảng media intelligence nội bộ cho phòng lab hoặc doanh nghiệp nhỏ. ROI đến từ việc tiết kiệm thời gian xử lý thủ công, giảm chi phí tra cứu media và hạn chế việc phải mua các công cụ quản lý media thương mại đắt tiền.

### 3. Kiến trúc giải pháp
SMA được xây dựng theo mô hình hybrid local-to-cloud. Ở lớp local, toàn bộ pipeline ingest chạy trong Docker Compose: video và ảnh được đưa vào hệ thống, cảnh được tách bằng PySceneDetect, âm thanh được phiên âm bằng faster-whisper, nội dung hình ảnh được mô tả bằng mô hình vision chạy qua Ollama, rồi dữ liệu được nhúng vector và lưu vào ChromaDB.
Ở lớp cloud, kiến trúc có thể nâng cấp sang AWS production mà không cần viết lại toàn bộ hệ thống. S3 giữ vai trò lưu trữ media, Bedrock xử lý AI multimodal, Transcribe tạo transcript, OpenSearch Serverless đảm nhiệm semantic search, RDS PostgreSQL lưu metadata, còn CloudFront + S3 có thể dùng để phân phối giao diện frontend. Cognito, WAF, Secrets Manager, ECR và CloudWatch hỗ trợ bảo mật, container registry, giám sát và vận hành.

![SMA Architecture](/images/2-Proposal/SMA_architecture.png)

**Dịch vụ AWS sử dụng**
- **Amazon S3**: Lưu trữ media gốc, thumbnail, scene frames và dữ liệu trung gian.
- **AWS Bedrock**: Hỗ trợ mô hình AI multimodal để mô tả nội dung ảnh/video và sinh ngữ nghĩa tìm kiếm.
- **Amazon Transcribe**: Chuyển giọng nói trong video thành văn bản để tra cứu theo transcript.
- **Amazon OpenSearch Serverless**: Lưu vector embedding và phục vụ semantic search.
- **Amazon RDS PostgreSQL**: Lưu metadata của asset, scene, transcript, tag và trạng thái ingest.
- **Amazon CloudFront**: Phân phối frontend nhanh và ổn định.
- **Amazon Cognito**: Xác thực và phân quyền người dùng truy cập dashboard.
- **AWS WAF**: Bảo vệ lớp web khỏi các truy cập bất thường và tấn công phổ biến.
- **Amazon ECR**: Lưu trữ Docker image cho quá trình CI/CD.
- **AWS CloudWatch**: Ghi log, theo dõi và cảnh báo trạng thái hệ thống.
- **AWS Secrets Manager**: Lưu trữ secrets, token và cấu hình nhạy cảm.
- **GitHub Actions**: Tự động build và push image trong quy trình triển khai.

**Thiết kế thành phần**
- **Frontend**: React 19 + Vite + Tailwind CSS, cung cấp dashboard để search, preview và quản lý asset.
- **Backend API**: FastAPI xử lý ingest, search, asset detail và các API nghiệp vụ.
- **Ingest pipeline**: Tách cảnh, tạo caption, phiên âm, sinh embedding và lưu metadata.
- **Vector search**: ChromaDB ở local hoặc OpenSearch Serverless ở AWS.
- **Object storage**: MinIO ở local hoặc S3 ở AWS.
- **Database**: PostgreSQL ở local hoặc RDS PostgreSQL ở AWS.
- **Security & ops**: Cognito, WAF, Secrets Manager, CloudWatch và CI/CD qua GitHub Actions.

### 4. Triển khai kỹ thuật
**Các giai đoạn triển khai**
Dự án SMA có thể chia thành 4 giai đoạn chính:
1. **Nghiên cứu và thiết kế kiến trúc**: Phân tích yêu cầu tìm kiếm media, timestamp seek, pipeline ingest và ánh xạ sang AWS targets.
2. **Xây dựng bản local-first**: Hoàn thiện Docker Compose, FastAPI, React dashboard, ChromaDB, PostgreSQL, MinIO và các module AI chạy nội bộ.
3. **Chuẩn hóa cloud-ready**: Tách cấu hình để dễ thay thế các thành phần local bằng dịch vụ AWS tương ứng.
4. **Triển khai và kiểm thử**: Thiết lập CI/CD, container registry, bảo mật, giám sát và thử nghiệm cloud deployment.

**Yêu cầu kỹ thuật**
- **Frontend**: React 19, Vite, Tailwind CSS, có video player hỗ trợ seek theo timestamp.
- **Backend**: Python 3.11, FastAPI, Uvicorn.
- **AI pipeline**: Ollama chạy mô hình vision và embedding, faster-whisper cho ASR, PySceneDetect và FFmpeg cho xử lý video.
- **Data layer**: PostgreSQL 16, ChromaDB, MinIO trong local; tương ứng RDS, OpenSearch Serverless và S3 trên AWS.
- **Triển khai**: Docker Compose cho local, GitHub Actions cho CI/CD, ECR cho container registry và CloudFront + S3 cho frontend production.

### 5. Tóm tắt triển khai lên AWS
Sau khi hoàn thiện phiên bản local-first, hệ thống SMA có thể được chuyển sang AWS theo hướng từng bước để giảm rủi ro và giữ nguyên logic xử lý chính. Ở lớp lưu trữ, MinIO sẽ được thay bằng Amazon S3 để lưu media gốc, thumbnail và file trung gian. Ở lớp AI và xử lý ngữ nghĩa, Ollama vision model có thể được thay bằng AWS Bedrock, faster-whisper được thay bằng Amazon Transcribe, còn ChromaDB được chuyển sang Amazon OpenSearch Serverless để phục vụ semantic search trên quy mô lớn hơn.

Phần dữ liệu cấu trúc sẽ được đưa sang Amazon RDS PostgreSQL để đảm bảo độ bền và khả năng quản trị tốt hơn so với chạy local. Giao diện React có thể được build và phân phối qua Amazon S3 kết hợp CloudFront để tăng tốc truy cập, trong khi Amazon Cognito dùng để xác thực người dùng và AWS WAF bảo vệ lớp web. Nếu cần tự động hóa triển khai, có thể dùng GitHub Actions để build Docker image, đẩy lên Amazon ECR và triển khai backend lên môi trường AWS.

Cách triển khai này giúp SMA giữ được mô hình local-first trong giai đoạn phát triển, nhưng vẫn có lộ trình rõ ràng để mở rộng sang production trên AWS khi số lượng media, người dùng và truy vấn tăng lên.

### 6. Giới thiệu các dịch vụ AWS sử dụng
Trong giai đoạn triển khai cloud, SMA tận dụng các dịch vụ managed để giảm công sức vận hành và tăng khả năng mở rộng. Amazon S3 dùng để lưu trữ media gốc, thumbnail và file trung gian. AWS Bedrock xử lý các tác vụ AI như mô tả nội dung hình ảnh/video, còn Amazon Transcribe đảm nhiệm chuyển âm thanh thành văn bản để phục vụ tìm kiếm theo thoại. Amazon OpenSearch Serverless được dùng cho semantic search và vector retrieval, trong khi Amazon RDS PostgreSQL lưu metadata của asset, scene, transcript và tag.
Bên cạnh đó, Amazon CloudFront và S3 có thể phân phối frontend, Amazon Cognito bảo vệ đăng nhập người dùng, AWS WAF tăng cường an toàn cho lớp web, Amazon ECR lưu trữ Docker image, còn CloudWatch và Secrets Manager hỗ trợ giám sát và quản lý cấu hình nhạy cảm. Nhờ cách tách vai trò rõ ràng này, hệ thống vừa phù hợp cho môi trường nội bộ vừa có đường nâng cấp rõ ràng lên production.

### 7. Ước tính chi phí
Ở giai đoạn local-first, chi phí gần như bằng 0 USD/tháng vì toàn bộ xử lý chạy trên máy cá nhân hoặc máy lab. Khi triển khai trên AWS, chi phí sẽ phụ thuộc vào số lượng media, thời lượng video, tần suất ingest và số lượt tìm kiếm của người dùng.
Với quy mô nhỏ cho phòng lab hoặc nhóm ít người dùng, có thể ước tính sơ bộ như sau:
- **Amazon S3**: khoảng 0.5 – 1.5 USD/tháng cho vài GB media và thumbnail.
- **Amazon RDS PostgreSQL**: khoảng 15 – 25 USD/tháng cho một instance nhỏ lưu metadata.
- **Amazon OpenSearch Serverless**: khoảng 5 – 20 USD/tháng, vì AWS tính phí theo OCU cho ingest và search, cùng với storage trên S3.
- **Amazon Transcribe**: khoảng 1 – 5 USD/tháng nếu chỉ xử lý một lượng audio nhỏ.
- **AWS Bedrock**: khoảng 2 – 10 USD/tháng tùy số lượt mô tả ảnh/video và tạo embedding.
- **CloudFront, Cognito, WAF, ECR, CloudWatch**: khoảng 1 – 5 USD/tháng cho mức sử dụng cơ bản.

**Tổng ước tính**: khoảng 24 – 66 USD/tháng cho kịch bản nhỏ. Con số này có thể thấp hơn nếu chỉ dùng thử nghiệm nội bộ, hoặc cao hơn nếu media tăng mạnh và số lượt truy vấn/search nhiều hơn. Để có số chính xác hơn, nên dùng AWS Pricing Calculator khi đã chốt dung lượng dữ liệu và mức tải dự kiến.

### 8. Đánh giá rủi ro
**Ma trận rủi ro**
- Khối lượng media lớn: Ảnh hưởng cao, xác suất trung bình.
- Mô hình AI chạy chậm trên máy local: Ảnh hưởng trung bình, xác suất cao.
- Sai lệch kết quả tìm kiếm: Ảnh hưởng trung bình, xác suất trung bình.
- Chi phí cloud tăng khi scale: Ảnh hưởng cao, xác suất thấp đến trung bình.

**Chiến lược giảm thiểu**
- Dùng pipeline local theo từng bước, cache model và tối ưu batch processing.
- Tách rõ metadata, vector search và object storage để dễ thay thế khi lên AWS.
- Giới hạn ingest theo đợt và theo dõi hiệu năng bằng log/metrics.
- Chỉ đưa các thành phần cần scale lên cloud thay vì chuyển toàn bộ ngay từ đầu.

**Kế hoạch dự phòng**
- Nếu AI inference local quá nặng, có thể giảm kích thước model hoặc chuyển sang Bedrock ở giai đoạn cloud.
- Nếu vector search trong local chậm, có thể chuyển sang OpenSearch Serverless sớm hơn.
- Nếu pipeline ingest lỗi, hệ thống vẫn giữ metadata cơ bản để tránh mất toàn bộ thư viện media.

### 9. Kết quả kỳ vọng
- **Về mặt kỹ thuật**: SMA cho phép người dùng nạp media, tự động tạo chỉ mục ngữ nghĩa, tìm kiếm bằng ngôn ngữ tự nhiên và nhảy trực tiếp tới đúng timestamp trong video.
- **Về mặt sản phẩm**: Hệ thống phù hợp cho nhóm thiết kế, dựng phim, nghiên cứu nội dung hoặc phòng lab cần quản lý media nội bộ một cách an toàn và hiệu quả.
- **Về mặt mở rộng**: Kiến trúc local-first giúp phát triển nhanh, còn mapping sang AWS giúp hệ thống có đường nâng cấp rõ ràng lên môi trường production khi cần.