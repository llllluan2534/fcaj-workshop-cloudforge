---
title: "Báº£n Ä‘á» xuáº¥t"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


# Smart Media Analytics
## XÃ¢y dá»±ng há»‡ thá»‘ng phÃ¢n tÃ­ch vÃ  tÃ¬m kiáº¿m video báº±ng AI (Video Semantic Search)

### 1. TÃ³m táº¯t Ä‘iá»u hÃ nh
Smart Media Analytics (SMA) lÃ  há»‡ thá»‘ng local-first tá»± Ä‘á»™ng náº¡p, tÃ¡ch cáº£nh, phiÃªn Ã¢m vÃ  tÃ¬m kiáº¿m ngá»¯ nghÄ©a media. NgÆ°á»i dÃ¹ng chá»‰ cáº§n gÃµ yÃªu cáº§u tá»± nhiÃªn (VD: "hoÃ ng hÃ´n trÃªn biá»ƒn") Ä‘á»ƒ tÃ¬m Ä‘Ãºng timestamp video, tiáº¿t kiá»‡m thá»i gian xem thá»§ cÃ´ng.
Ban Ä‘áº§u, há»‡ thá»‘ng cháº¡y 100% ná»™i bá»™ qua Docker giÃºp báº£o máº­t vÃ  tá»‘i Æ°u chi phÃ­ thá»­ nghiá»‡m, sau Ä‘Ã³ cÃ³ thá»ƒ dá»… dÃ ng nÃ¢ng cáº¥p cáº¥u trÃºc tÆ°Æ¡ng á»©ng lÃªn AWS (S3, Bedrock, OpenSearch, RDS) khi cáº§n.

### 2. TuyÃªn bá»‘ váº¥n Ä‘á»
**Váº¥n Ä‘á» hiá»‡n táº¡i:** ThÆ° viá»‡n media phÃ¢n tÃ¡n, tÃªn file vÃ´ nghÄ©a khiáº¿n viá»‡c tÃ¬m cáº£nh quay thá»§ cÃ´ng tá»‘n ráº¥t nhiá»u thá»i gian. Náº¿u xá»­ lÃ½ toÃ n bá»™ qua AI Cloud ngay tá»« Ä‘áº§u sáº½ tá»‘n kÃ©m vÃ  cÃ³ nguy cÆ¡ rÃ² rá»‰ dá»¯ liá»‡u.

**Giáº£i phÃ¡p:** SMA giáº£i quyáº¿t bÃ i toÃ¡n nÃ y báº±ng má»™t pipeline xá»­ lÃ½ media tá»± Ä‘á»™ng theo hÆ°á»›ng local-first. Há»‡ thá»‘ng sá»­ dá»¥ng React dashboard Ä‘á»ƒ duyá»‡t asset, FastAPI Ä‘á»ƒ cung cáº¥p API, ChromaDB Ä‘á»ƒ lÆ°u vÃ  truy váº¥n vector embedding, PostgreSQL Ä‘á»ƒ lÆ°u metadata, MinIO Ä‘á»ƒ lÆ°u object media, Ollama Ä‘á»ƒ cháº¡y mÃ´ hÃ¬nh vision vÃ  embedding ná»™i bá»™, cÃ¹ng faster-whisper Ä‘á»ƒ phiÃªn Ã¢m Ã¢m thanh.
Khi triá»ƒn khai trÃªn AWS, cÃ¡c thÃ nh pháº§n nÃ y Ä‘Æ°á»£c Ã¡nh xáº¡ sang kiáº¿n trÃºc production tÆ°Æ¡ng á»©ng: MinIO sang Amazon S3, Ollama vision model sang AWS Bedrock, faster-whisper sang Amazon Transcribe, vÃ  PostgreSQL sang Amazon RDS PostgreSQL. BÃªn cáº¡nh Ä‘Ã³, há»‡ thá»‘ng cloud cÃ²n cÃ³ thá»ƒ dÃ¹ng CloudFront, Cognito, WAF, ECR, CloudWatch, Secrets Manager, X-Ray, SQS, EventBridge, Step Functions, API Gateway, App Runner, ECS Fargate, Lambda, ElastiCache vÃ  VPC Ä‘á»ƒ hoÃ n thiá»‡n vÃ²ng Ä‘á»i triá»ƒn khai vÃ  váº­n hÃ nh

**Lá»£i Ã­ch (ROI):** Giáº£i phÃ¡p giÃºp rÃºt ngáº¯n Ä‘Ã¡ng ká»ƒ thá»i gian tÃ¬m kiáº¿m footage, Ä‘á»c transcript vÃ  xÃ¡c Ä‘á»‹nh cáº£nh cáº§n dÃ¹ng, tá»« Ä‘Ã³ tÄƒng hiá»‡u quáº£ lÃ m viá»‡c cho nhÃ³m sÃ¡ng táº¡o. NgÆ°á»i dÃ¹ng cÃ³ thá»ƒ nháº­p truy váº¥n tá»± nhiÃªn nhÆ° â€œcáº£nh hoÃ ng hÃ´n trÃªn biá»ƒn cÃ³ tiáº¿ng sÃ³ngâ€ vÃ  nháº­n káº¿t quáº£ Ä‘Ãºng Ä‘oáº¡n video, Ä‘Ãºng timestamp, thay vÃ¬ pháº£i xem thá»§ cÃ´ng toÃ n bá»™ file.


### 3. Kiáº¿n trÃºc giáº£i phÃ¡p
SMA Ä‘Æ°á»£c thiáº¿t káº¿ theo hÆ°á»›ng hybrid local-to-cloud Ä‘á»ƒ vá»«a thuáº­n tiá»‡n khi phÃ¡t triá»ƒn ná»™i bá»™, vá»«a dá»… nÃ¢ng cáº¥p lÃªn mÃ´i trÆ°á»ng production sau nÃ y. á»ž giai Ä‘oáº¡n local, toÃ n bá»™ quy trÃ¬nh ingest media cháº¡y trong Docker Compose: há»‡ thá»‘ng nháº­n video vÃ  áº£nh, tá»± tÃ¡ch cáº£nh, phiÃªn Ã¢m Ã¢m thanh, táº¡o mÃ´ táº£ ná»™i dung báº±ng AI vÃ  lÆ°u dá»¯ liá»‡u xá»­ lÃ½ vÃ o mÃ´i trÆ°á»ng cá»¥c bá»™.

Khi triá»ƒn khai lÃªn AWS, kiáº¿n trÃºc cÃ³ thá»ƒ má»Ÿ rá»™ng mÃ  khÃ´ng cáº§n thay Ä‘á»•i lá»›n vá» logic xá»­ lÃ½. S3 dÃ¹ng Ä‘á»ƒ lÆ°u media, Bedrock vÃ  Transcribe Ä‘áº£m nhiá»‡m pháº§n AI, RDS PostgreSQL lÆ°u metadata, CloudFront káº¿t há»£p S3 phÃ¢n phá»‘i giao diá»‡n frontend, cÃ²n cÃ¡c dá»‹ch vá»¥ nhÆ° Cognito, WAF, ECR, Lambda, ECS Fargate, App Runner, Step Functions, SQS, EventBridge, CloudWatch, X-Ray, ElastiCache vÃ  VPC há»— trá»£ báº£o máº­t, Ä‘iá»u phá»‘i, giÃ¡m sÃ¡t vÃ  má»Ÿ rá»™ng há»‡ thá»‘ng.

![SMA Architecture](/images/2-Proposal/1.SMA_architecture.png)
![SMA Architecture](/images/2-Proposal/2.SMA_architecture.png)

**Danh sÃ¡ch dá»‹ch vá»¥ AWS sá»­ dá»¥ng trong kiáº¿n trÃºc**
Dá»±a trÃªn thiáº¿t káº¿ production, há»‡ thá»‘ng tÃ­ch há»£p sÃ¢u cÃ¡c dá»‹ch vá»¥ chuyÃªn biá»‡t cá»§a AWS:
- **Máº¡ng & PhÃ¢n phá»‘i (Networking & Delivery):**
  - **Amazon Route 53**: Quáº£n lÃ½ tÃªn miá»n (DNS).
  - **Amazon CloudFront**: Máº¡ng phÃ¢n phá»‘i ná»™i dung (CDN) giÃºp tÄƒng tá»‘c Ä‘á»™ táº£i Frontend vÃ  Media.
  - **Amazon VPC**: XÃ¢y dá»±ng máº¡ng riÃªng áº£o, bao gá»“m Internet Gateway vÃ  **NAT Gateway** Ä‘á»ƒ Private Subnet truy cáº­p an toÃ n ra Internet.
- **Lá»›p Báº£o máº­t (Security & Identity):**
  - **AWS WAF**: TÆ°á»ng lá»­a báº£o vá»‡ web khá»i cÃ¡c cuá»™c táº¥n cÃ´ng máº¡ng.
  - **Amazon Cognito**: Cung cáº¥p xÃ¡c thá»±c vÃ  phÃ¢n quyá»n ngÆ°á»i dÃ¹ng (quáº£n lÃ½ JWT token).
  - **AWS Secrets Manager**: LÆ°u trá»¯ an toÃ n cÃ¡c API Keys, database credentials.
- **LÆ°u trá»¯ & Database (Storage & Database):**
  - **Amazon S3**: LÆ°u trá»¯ toÃ n bá»™ media gá»‘c, keyframes (tÃ­ch há»£p **S3 Gateway Endpoint**).
  - **Amazon RDS (PostgreSQL)**: CÆ¡ sá»Ÿ dá»¯ liá»‡u quan há»‡ chÃ­nh Ä‘á»ƒ lÆ°u metadata.
  - **Amazon ElastiCache (Redis)**: Cache dá»¯ liá»‡u tá»‘c Ä‘á»™ cao Ä‘á»ƒ giáº£m táº£i DB.
- **TÃ­nh toÃ¡n & Xá»­ lÃ½ (Compute & API):**
  - **AWS App Runner**: Cháº¡y Web Service / API Backend (FastAPI) má»™t cÃ¡ch Ä‘Æ¡n giáº£n, auto-scaling.
  - **Amazon API Gateway**: Cá»•ng giao tiáº¿p cho REST API vÃ  WebSocket (WSS Push).
  - **Amazon ECS (Fargate)**: Triá»ƒn khai cÃ¡c tÃ¡c vá»¥ Auto Scaling Ä‘á»ƒ xá»­ lÃ½ video/hÃ¬nh áº£nh.
  - **AWS Lambda**: Thá»±c thi mÃ£ serverless (nhÆ° lÆ°u metadata, trigger events).
- **TrÃ­ tuá»‡ nhÃ¢n táº¡o (AI/ML):**
  - **Amazon Bedrock**: DÃ¹ng cÃ¡c model nhÆ° Nova Lite & Titan Embeddings Ä‘á»ƒ sinh embeddings vÃ  phÃ¢n tÃ­ch ngá»¯ nghÄ©a.
  - **Amazon Transcribe**: Nháº­n dáº¡ng vÃ  chuyá»ƒn giá»ng nÃ³i thÃ nh vÄƒn báº£n (Speech-to-Text).
- **TÃ­ch há»£p & Äiá»u phá»‘i (Integration):**
  - **Amazon SQS & Amazon EventBridge**: HÃ ng Ä‘á»£i tin nháº¯n vÃ  Event bus Ä‘á»ƒ truyá»n táº£i sá»± kiá»‡n ná»™i bá»™.
  - **AWS Step Functions**: Äiá»u phá»‘i chuá»—i quy trÃ¬nh lÃ m viá»‡c (workflow) phá»©c táº¡p (nhÆ° pipeline xá»­ lÃ½ video).
- **DevOps & GiÃ¡m sÃ¡t (Management & Governance):**
  - **Amazon ECR**: LÆ°u trá»¯ cÃ¡c Docker images cho ECS, App Runner.
  - **Amazon CloudWatch & AWS X-Ray**: Thu tháº­p logs, metrics, alarms vÃ  giÃ¡m sÃ¡t phÃ¢n tÃ¡n (Distributed Tracing).

**Thiáº¿t káº¿ thÃ nh pháº§n cá»‘t lÃµi**
- **Lá»›p Giao diá»‡n (Frontend):** á»¨ng dá»¥ng React truy cáº­p qua Route 53 + CloudFront, Ä‘Æ°á»£c báº£o vá»‡ báº±ng WAF vÃ  xÃ¡c thá»±c báº±ng Cognito.
- **Lá»›p á»¨ng dá»¥ng (API):** Nháº­n request tá»« API Gateway vÃ  Ä‘á»‹nh tuyáº¿n Ä‘áº¿n App Runner (Backend).
- **Lá»›p Xá»­ lÃ½ (Processing Pipeline):** Sá»­ dá»¥ng Step Functions, EventBridge vÃ  SQS Ä‘á»ƒ gá»i cÃ¡c ECS (Fargate) tasks xá»­ lÃ½ video, sau Ä‘Ã³ dÃ¹ng Bedrock & Transcribe Ä‘á»ƒ trÃ­ch xuáº¥t ngá»¯ nghÄ©a.
- **Lá»›p Dá»¯ liá»‡u (Data):** S3 lÆ°u trá»¯ file tÄ©nh, RDS lÆ°u trá»¯ siÃªu dá»¯ liá»‡u, ElastiCache lÆ°u Ä‘á»‡m vÃ  Lambda há»— trá»£ Ä‘áº©y dá»¯ liá»‡u tá»« luá»“ng xá»­ lÃ½. ToÃ n bá»™ náº±m trong VPC an toÃ n vá»›i NAT Gateway. CÃ¡c khÃ³a báº£o máº­t quáº£n lÃ½ táº­p trung á»Ÿ Secrets Manager. CloudWatch vÃ  X-Ray giÃ¡m sÃ¡t toÃ n bá»™ á»©ng dá»¥ng.

### 4. Triá»ƒn khai ká»¹ thuáº­t
Dá»± Ã¡n triá»ƒn khai qua 4 giai Ä‘oáº¡n: 
1. **NghiÃªn cá»©u kiáº¿n trÃºc**: Thiáº¿t káº¿ luá»“ng dá»¯ liá»‡u khá»›p vá»›i danh sÃ¡ch dá»‹ch vá»¥ AWS.
2. **XÃ¢y dá»±ng báº£n Local-first**: HoÃ n thiá»‡n pipeline ná»™i bá»™ vá»›i Docker Compose.
3. **Chuáº©n hÃ³a Cloud-ready**: Báº¯t Ä‘áº§u thay tháº¿ cÃ¡c container báº±ng AWS Services (App Runner, Bedrock, RDS).
4. **Triá»ƒn khai & Kiá»ƒm thá»­ AWS**: Sá»­ dá»¥ng CI/CD Ä‘á»ƒ build Docker images Ä‘áº©y lÃªn ECR, cáº¥u hÃ¬nh giÃ¡m sÃ¡t CloudWatch vÃ  X-Ray.

### 5. Æ¯á»›c tÃ­nh chi phÃ­ (MÃ´i trÆ°á»ng AWS)
Vá»›i quy mÃ´ kiáº¿n trÃºc production hoÃ n chá»‰nh sá»­ dá»¥ng hÆ¡n 20 dá»‹ch vá»¥ AWS nhÆ° trÃªn (bao gá»“m Multi-AZ vÃ  NAT Gateway cháº¡y 24/7), Æ°á»›c tÃ­nh chi phÃ­ cÆ¡ báº£n cho má»™t mÃ´i trÆ°á»ng nhá»/vá»«a nhÆ° sau:
| Dá»‹ch vá»¥ AWS | Má»¥c Ä‘Ã­ch sá»­ dá»¥ng | Æ¯á»›c tÃ­nh chi phÃ­ / ThÃ¡ng (USD) |
| --- | --- | --- |
| **Amazon RDS (PostgreSQL)** | Database chÃ­nh (Multi-AZ, `db.t4g.medium`, 20GB) | $68.00 |
| **AWS NAT Gateway** | Cho phÃ©p Private Subnet ra Internet (1 NAT, 24/7) | $32.40 |
| **Amazon ElastiCache** | Cache (Multi-AZ, `cache.t4g.micro`, 2 nodes) | $32.00 |
| **Amazon ECS (Fargate)** | Cháº¡y Auto Scaling Task xá»­ lÃ½ Video (~1 vCPU, 2GB RAM) | $15.00 |
| **Amazon Bedrock & Transcribe** | Xá»­ lÃ½ AI, Speech-to-Text, Embeddings (Æ¯á»›c lÆ°á»£ng cÆ¡ báº£n) | $15.00 |
| **AWS App Runner** | Web Service / API (1 instance tá»‘i thiá»ƒu) | $7.00 |
| **AWS WAF** | Web Application Firewall (1 Web ACL, 1 Rule) | $6.00 |
| **Amazon CloudWatch & X-Ray** | Logs, Metrics, Alarms, Distributed Tracing | $5.00 |
| **Amazon S3** | LÆ°u trá»¯ Media & Keyframes (Æ¯á»›c tÃ­nh ~50GB) | $2.00 |
| **AWS Secrets Manager** | Quáº£n lÃ½ Keys, Credentials (5 secrets) | $2.00 |
| **Amazon API Gateway** | REST API & WSS Push (Theo request) | $1.00 |
| **Amazon CloudFront** | CDN phÃ¢n phá»‘i ná»™i dung (Data Transfer) | $1.00 |
| **Amazon SQS, EventBridge, Step Functions** | Äiá»u phá»‘i Workflow, Event Bus, HÃ ng Ä‘á»£i | $1.00 |
| **Amazon Route 53** | Quáº£n lÃ½ DNS (1 Hosted Zone) | $0.50 |
| **Amazon Cognito** | XÃ¡c thá»±c ngÆ°á»i dÃ¹ng (JWT) | $0.00 (Free Tier) |
| **AWS Lambda** | LÆ°u Metadata & Embeddings | $0.00 (Free Tier) |
| **Tá»•ng cá»™ng Æ°á»›c tÃ­nh** | **ToÃ n bá»™ há»‡ thá»‘ng** | **~$187.90** |
### 8. ÄÃ¡nh giÃ¡ rá»§i ro
**Ma tráº­n rá»§i ro**
- Khá»‘i lÆ°á»£ng media lá»›n: áº¢nh hÆ°á»Ÿng cao, xÃ¡c suáº¥t trung bÃ¬nh.
- MÃ´ hÃ¬nh AI cháº¡y cháº­m trÃªn mÃ¡y local: áº¢nh hÆ°á»Ÿng trung bÃ¬nh, xÃ¡c suáº¥t cao.
- Sai lá»‡ch káº¿t quáº£ tÃ¬m kiáº¿m: áº¢nh hÆ°á»Ÿng trung bÃ¬nh, xÃ¡c suáº¥t trung bÃ¬nh.
- Chi phÃ­ cloud tÄƒng khi scale: áº¢nh hÆ°á»Ÿng cao, xÃ¡c suáº¥t tháº¥p Ä‘áº¿n trung bÃ¬nh.

**Chiáº¿n lÆ°á»£c giáº£m thiá»ƒu**
- DÃ¹ng pipeline local theo tá»«ng bÆ°á»›c, cache model vÃ  tá»‘i Æ°u batch processing.
- TÃ¡ch rÃµ metadata, vector search vÃ  object storage Ä‘á»ƒ dá»… thay tháº¿ khi lÃªn AWS.
- Giá»›i háº¡n ingest theo Ä‘á»£t vÃ  theo dÃµi hiá»‡u nÄƒng báº±ng log/metrics.
- Chá»‰ Ä‘Æ°a cÃ¡c thÃ nh pháº§n cáº§n scale lÃªn cloud thay vÃ¬ chuyá»ƒn toÃ n bá»™ ngay tá»« Ä‘áº§u.

**Káº¿ hoáº¡ch dá»± phÃ²ng**
- Náº¿u AI inference local quÃ¡ náº·ng, cÃ³ thá»ƒ giáº£m kÃ­ch thÆ°á»›c model hoáº·c chuyá»ƒn sang Bedrock á»Ÿ giai Ä‘oáº¡n cloud.
- Náº¿u vector search trong local cháº­m, cÃ³ thá»ƒ chuyá»ƒn sang OpenSearch Serverless sá»›m hÆ¡n.
- Náº¿u pipeline ingest lá»—i, há»‡ thá»‘ng váº«n giá»¯ metadata cÆ¡ báº£n Ä‘á»ƒ trÃ¡nh máº¥t toÃ n bá»™ thÆ° viá»‡n media.

### 9. Káº¿t quáº£ ká»³ vá»ng
- **Vá» máº·t ká»¹ thuáº­t**: SMA cho phÃ©p ngÆ°á»i dÃ¹ng náº¡p media, tá»± Ä‘á»™ng táº¡o chá»‰ má»¥c ngá»¯ nghÄ©a, tÃ¬m kiáº¿m báº±ng ngÃ´n ngá»¯ tá»± nhiÃªn vÃ  nháº£y trá»±c tiáº¿p tá»›i Ä‘Ãºng timestamp trong video.
- **Vá» máº·t sáº£n pháº©m**: Há»‡ thá»‘ng phÃ¹ há»£p cho nhÃ³m thiáº¿t káº¿, dá»±ng phim, nghiÃªn cá»©u ná»™i dung hoáº·c phÃ²ng lab cáº§n quáº£n lÃ½ media ná»™i bá»™ má»™t cÃ¡ch an toÃ n vÃ  hiá»‡u quáº£.
- **Vá» máº·t má»Ÿ rá»™ng**: Kiáº¿n trÃºc local-first giÃºp phÃ¡t triá»ƒn nhanh, cÃ²n mapping sang AWS giÃºp há»‡ thá»‘ng cÃ³ Ä‘Æ°á»ng nÃ¢ng cáº¥p rÃµ rÃ ng lÃªn mÃ´i trÆ°á»ng production khi cáº§n.