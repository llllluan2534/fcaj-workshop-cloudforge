---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Xây dựng ứng dụng tìm kiếm đầu tiên của bạn với Amazon OpenSearch Service

Trong thế giới điều khiển bằng dữ liệu ngày nay, khả năng tìm kiếm và phân tích thông tin theo thời gian thực không còn là một lợi thế cạnh tranh—nó là một sự cần thiết của doanh nghiệp. Từ các cảm biến IoT công nghiệp truyền hàng triệu số liệu mỗi giây, đến các nền tảng thương mại điện tử phải hiển thị ngay các sản phẩm phù hợp, và các đội bảo mật cần phát hiện các mối đe dọa khi chúng xuất hiện, tất cả đều yêu cầu một nền tảng tìm kiếm và phân tích mạnh mẽ.

Đây là lúc Amazon OpenSearch Service xuất hiện.

## OpenSearch Service là gì?

Amazon OpenSearch Service là một dịch vụ phân tích và tìm kiếm được quản lý hoàn toàn do AWS cung cấp. Thay vì lo lắng về việc quản lý cơ sở hạ tầng, các nhà phát triển có thể tập trung vào việc xây dựng các ứng dụng và mang lại giá trị cho doanh nghiệp.

Dịch vụ Amazon OpenSearch Serverless thậm chí còn tiến xa hơn bằng cách tự động mở rộng tài nguyên dựa trên nhu cầu, loại bỏ hoàn toàn sự cần thiết phải quản lý các máy chủ.

## Các Khái Niệm Cốt Lõi Bạn Nên Biết

Trước khi đi sâu vào triển khai, điều quan trọng là phải hiểu một số khái niệm cơ bản:

### Document & Index (Tài liệu & Chỉ mục)

Đơn vị dữ liệu cơ bản trong OpenSearch là một document, thường được lưu trữ ở định dạng JSON. Các document được tổ chức thành các index, tương tự như các bảng trong cơ sở dữ liệu truyền thống.

### Cluster & Node (Cụm & Nút)

OpenSearch hoạt động trên một kiến trúc phân tán.

Master nodes quản lý các hoạt động của cluster và siêu dữ liệu.
Data nodes lưu trữ dữ liệu và thực thi các truy vấn tìm kiếm.
Coordinator nodes định tuyến các yêu cầu một cách hiệu quả, giảm bớt khối lượng công việc cho các data nodes.
### Shard & Replica (Phân mảnh & Bản sao)

Một index được chia thành nhiều shard để có khả năng mở rộng (AWS thường khuyến nghị kích thước shard từ 10–50 GB). Mỗi shard có thể có một hoặc nhiều replica để cải thiện tính sẵn sàng và khả năng chịu lỗi.

### Inverted Index & BM25 (Chỉ mục đảo ngược & BM25)

Tìm kiếm toàn văn bản được hỗ trợ bởi một inverted index, trong khi mức độ liên quan của kết quả được xếp hạng bằng thuật toán BM25, cung cấp trải nghiệm tìm kiếm nhanh chóng và chính xác.

## Kiến trúc Ứng dụng Mẫu

Một ứng dụng tìm kiếm sẵn sàng cho sản xuất trên AWS thường được thiết kế bằng kiến trúc bảo mật nhiều lớp, trong đó mỗi thành phần hoạt động cùng nhau một cách liền mạch—từ frontend đến data cluster.

## Luồng Yêu cầu Chi tiết

Khi người dùng tương tác với ứng dụng, các yêu cầu sẽ theo một chuỗi các bước rõ ràng:

### Bước 1 – Truy cập Frontend

Người dùng truy cập ứng dụng thông qua AWS App Runner, nơi tự động lưu trữ và phục vụ frontend.

### Bước 2 – Xác thực

Amazon Cognito xử lý việc xác thực và phân quyền người dùng, đảm bảo rằng chỉ những người dùng hợp pháp mới có thể truy cập hệ thống.

### Bước 3 – Định tuyến Qua API Gateway

Tất cả các yêu cầu frontend đều đi qua Amazon API Gateway, hoạt động như một điểm truy cập duy nhất cho ứng dụng.

API Gateway xác thực các token do Cognito cấp và chuyển tiếp các yêu cầu đã được phân quyền đến các hàm AWS Lambda chạy bên trong VPC.

### Bước 4 – Xử lý Logic Nghiệp vụ với Lambda

Tùy thuộc vào loại yêu cầu, AWS Lambda thực hiện một trong hai nhiệm vụ chính:

Lập chỉ mục dữ liệu mới vào OpenSearch
Thực thi các truy vấn tìm kiếm đối với cluster hiện tại
### Bước 5 – OpenSearch trong Môi trường Bảo mật

Toàn bộ OpenSearch cluster nằm trong các mạng con riêng (private subnets) của Đám mây Riêng Ảo (VPC) và không bao giờ được hiển thị trực tiếp ra internet công cộng. Điều này cung cấp một lớp bảo vệ quan trọng cho dữ liệu kinh doanh nhạy cảm.
![Sơ đồ kiến trúc](/images/architecture.png)

## Kết luận

Với kiến trúc này, bạn có thể xây dựng một ứng dụng tìm kiếm sẵn sàng cho sản xuất trên AWS mà không cần quản lý cơ sở hạ tầng phức tạp.

Amazon OpenSearch Service cung cấp:

Khả năng tìm kiếm nhanh chóng và có thể mở rộng, phát triển cùng với nhu cầu của doanh nghiệp
Các tính năng bảo mật và tuân thủ được tích hợp sẵn với cấu hình tối thiểu
Quản lý cluster tự động, cho phép AWS xử lý độ phức tạp trong vận hành
Định giá linh hoạt, đảm bảo bạn chỉ trả tiền cho các tài nguyên bạn thực sự sử dụng

Mã nguồn hoàn chỉnh và hướng dẫn triển khai có sẵn trên GitHub:

https://github.com/aws-samples/sample-for-amazon-opensearch-service-tutorials-101

Bạn có thể clone kho lưu trữ và bắt đầu xây dựng ứng dụng tìm kiếm của riêng mình ngay hôm nay.

Bài viết gốc:
https://aws.amazon.com/blogs/big-data/amazon-opensearch-service-101-create-your-first-search-application-with-opensearch/