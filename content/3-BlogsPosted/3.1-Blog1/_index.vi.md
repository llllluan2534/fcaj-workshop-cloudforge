---
title: "Blog 1"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# XÃ¢y dá»±ng á»©ng dá»¥ng tÃ¬m kiáº¿m Ä‘áº§u tiÃªn cá»§a báº¡n vá»›i Amazon OpenSearch Service

Trong tháº¿ giá»›i Ä‘iá»u khiá»ƒn báº±ng dá»¯ liá»‡u ngÃ y nay, kháº£ nÄƒng tÃ¬m kiáº¿m vÃ  phÃ¢n tÃ­ch thÃ´ng tin theo thá»i gian thá»±c khÃ´ng cÃ²n lÃ  má»™t lá»£i tháº¿ cáº¡nh tranhâ€”nÃ³ lÃ  má»™t sá»± cáº§n thiáº¿t cá»§a doanh nghiá»‡p. Tá»« cÃ¡c cáº£m biáº¿n IoT cÃ´ng nghiá»‡p truyá»n hÃ ng triá»‡u sá»‘ liá»‡u má»—i giÃ¢y, Ä‘áº¿n cÃ¡c ná»n táº£ng thÆ°Æ¡ng máº¡i Ä‘iá»‡n tá»­ pháº£i hiá»ƒn thá»‹ ngay cÃ¡c sáº£n pháº©m phÃ¹ há»£p, vÃ  cÃ¡c Ä‘á»™i báº£o máº­t cáº§n phÃ¡t hiá»‡n cÃ¡c má»‘i Ä‘e dá»a khi chÃºng xuáº¥t hiá»‡n, táº¥t cáº£ Ä‘á»u yÃªu cáº§u má»™t ná»n táº£ng tÃ¬m kiáº¿m vÃ  phÃ¢n tÃ­ch máº¡nh máº½.

ÄÃ¢y lÃ  lÃºc Amazon OpenSearch Service xuáº¥t hiá»‡n.

## OpenSearch Service lÃ  gÃ¬?

Amazon OpenSearch Service lÃ  má»™t dá»‹ch vá»¥ phÃ¢n tÃ­ch vÃ  tÃ¬m kiáº¿m Ä‘Æ°á»£c quáº£n lÃ½ hoÃ n toÃ n do AWS cung cáº¥p. Thay vÃ¬ lo láº¯ng vá» viá»‡c quáº£n lÃ½ cÆ¡ sá»Ÿ háº¡ táº§ng, cÃ¡c nhÃ  phÃ¡t triá»ƒn cÃ³ thá»ƒ táº­p trung vÃ o viá»‡c xÃ¢y dá»±ng cÃ¡c á»©ng dá»¥ng vÃ  mang láº¡i giÃ¡ trá»‹ cho doanh nghiá»‡p.

Dá»‹ch vá»¥ Amazon OpenSearch Serverless tháº­m chÃ­ cÃ²n tiáº¿n xa hÆ¡n báº±ng cÃ¡ch tá»± Ä‘á»™ng má»Ÿ rá»™ng tÃ i nguyÃªn dá»±a trÃªn nhu cáº§u, loáº¡i bá» hoÃ n toÃ n sá»± cáº§n thiáº¿t pháº£i quáº£n lÃ½ cÃ¡c mÃ¡y chá»§.

## CÃ¡c KhÃ¡i Niá»‡m Cá»‘t LÃµi Báº¡n NÃªn Biáº¿t

TrÆ°á»›c khi Ä‘i sÃ¢u vÃ o triá»ƒn khai, Ä‘iá»u quan trá»ng lÃ  pháº£i hiá»ƒu má»™t sá»‘ khÃ¡i niá»‡m cÆ¡ báº£n:

### Document & Index (TÃ i liá»‡u & Chá»‰ má»¥c)

ÄÆ¡n vá»‹ dá»¯ liá»‡u cÆ¡ báº£n trong OpenSearch lÃ  má»™t document, thÆ°á»ng Ä‘Æ°á»£c lÆ°u trá»¯ á»Ÿ Ä‘á»‹nh dáº¡ng JSON. CÃ¡c document Ä‘Æ°á»£c tá»• chá»©c thÃ nh cÃ¡c index, tÆ°Æ¡ng tá»± nhÆ° cÃ¡c báº£ng trong cÆ¡ sá»Ÿ dá»¯ liá»‡u truyá»n thá»‘ng.

### Cluster & Node (Cá»¥m & NÃºt)

OpenSearch hoáº¡t Ä‘á»™ng trÃªn má»™t kiáº¿n trÃºc phÃ¢n tÃ¡n.

Master nodes quáº£n lÃ½ cÃ¡c hoáº¡t Ä‘á»™ng cá»§a cluster vÃ  siÃªu dá»¯ liá»‡u.
Data nodes lÆ°u trá»¯ dá»¯ liá»‡u vÃ  thá»±c thi cÃ¡c truy váº¥n tÃ¬m kiáº¿m.
Coordinator nodes Ä‘á»‹nh tuyáº¿n cÃ¡c yÃªu cáº§u má»™t cÃ¡ch hiá»‡u quáº£, giáº£m bá»›t khá»‘i lÆ°á»£ng cÃ´ng viá»‡c cho cÃ¡c data nodes.
### Shard & Replica (PhÃ¢n máº£nh & Báº£n sao)

Má»™t index Ä‘Æ°á»£c chia thÃ nh nhiá»u shard Ä‘á»ƒ cÃ³ kháº£ nÄƒng má»Ÿ rá»™ng (AWS thÆ°á»ng khuyáº¿n nghá»‹ kÃ­ch thÆ°á»›c shard tá»« 10â€“50 GB). Má»—i shard cÃ³ thá»ƒ cÃ³ má»™t hoáº·c nhiá»u replica Ä‘á»ƒ cáº£i thiá»‡n tÃ­nh sáºµn sÃ ng vÃ  kháº£ nÄƒng chá»‹u lá»—i.

### Inverted Index & BM25 (Chá»‰ má»¥c Ä‘áº£o ngÆ°á»£c & BM25)

TÃ¬m kiáº¿m toÃ n vÄƒn báº£n Ä‘Æ°á»£c há»— trá»£ bá»Ÿi má»™t inverted index, trong khi má»©c Ä‘á»™ liÃªn quan cá»§a káº¿t quáº£ Ä‘Æ°á»£c xáº¿p háº¡ng báº±ng thuáº­t toÃ¡n BM25, cung cáº¥p tráº£i nghiá»‡m tÃ¬m kiáº¿m nhanh chÃ³ng vÃ  chÃ­nh xÃ¡c.

## Kiáº¿n trÃºc á»¨ng dá»¥ng Máº«u

Má»™t á»©ng dá»¥ng tÃ¬m kiáº¿m sáºµn sÃ ng cho sáº£n xuáº¥t trÃªn AWS thÆ°á»ng Ä‘Æ°á»£c thiáº¿t káº¿ báº±ng kiáº¿n trÃºc báº£o máº­t nhiá»u lá»›p, trong Ä‘Ã³ má»—i thÃ nh pháº§n hoáº¡t Ä‘á»™ng cÃ¹ng nhau má»™t cÃ¡ch liá»n máº¡châ€”tá»« frontend Ä‘áº¿n data cluster.

## Luá»“ng YÃªu cáº§u Chi tiáº¿t

Khi ngÆ°á»i dÃ¹ng tÆ°Æ¡ng tÃ¡c vá»›i á»©ng dá»¥ng, cÃ¡c yÃªu cáº§u sáº½ theo má»™t chuá»—i cÃ¡c bÆ°á»›c rÃµ rÃ ng:

### BÆ°á»›c 1 â€“ Truy cáº­p Frontend

NgÆ°á»i dÃ¹ng truy cáº­p á»©ng dá»¥ng thÃ´ng qua AWS App Runner, nÆ¡i tá»± Ä‘á»™ng lÆ°u trá»¯ vÃ  phá»¥c vá»¥ frontend.

### BÆ°á»›c 2 â€“ XÃ¡c thá»±c

Amazon Cognito xá»­ lÃ½ viá»‡c xÃ¡c thá»±c vÃ  phÃ¢n quyá»n ngÆ°á»i dÃ¹ng, Ä‘áº£m báº£o ráº±ng chá»‰ nhá»¯ng ngÆ°á»i dÃ¹ng há»£p phÃ¡p má»›i cÃ³ thá»ƒ truy cáº­p há»‡ thá»‘ng.

### BÆ°á»›c 3 â€“ Äá»‹nh tuyáº¿n Qua API Gateway

Táº¥t cáº£ cÃ¡c yÃªu cáº§u frontend Ä‘á»u Ä‘i qua Amazon API Gateway, hoáº¡t Ä‘á»™ng nhÆ° má»™t Ä‘iá»ƒm truy cáº­p duy nháº¥t cho á»©ng dá»¥ng.

API Gateway xÃ¡c thá»±c cÃ¡c token do Cognito cáº¥p vÃ  chuyá»ƒn tiáº¿p cÃ¡c yÃªu cáº§u Ä‘Ã£ Ä‘Æ°á»£c phÃ¢n quyá»n Ä‘áº¿n cÃ¡c hÃ m AWS Lambda cháº¡y bÃªn trong VPC.

### BÆ°á»›c 4 â€“ Xá»­ lÃ½ Logic Nghiá»‡p vá»¥ vá»›i Lambda

TÃ¹y thuá»™c vÃ o loáº¡i yÃªu cáº§u, AWS Lambda thá»±c hiá»‡n má»™t trong hai nhiá»‡m vá»¥ chÃ­nh:

Láº­p chá»‰ má»¥c dá»¯ liá»‡u má»›i vÃ o OpenSearch
Thá»±c thi cÃ¡c truy váº¥n tÃ¬m kiáº¿m Ä‘á»‘i vá»›i cluster hiá»‡n táº¡i
### BÆ°á»›c 5 â€“ OpenSearch trong MÃ´i trÆ°á»ng Báº£o máº­t

ToÃ n bá»™ OpenSearch cluster náº±m trong cÃ¡c máº¡ng con riÃªng (private subnets) cá»§a ÄÃ¡m mÃ¢y RiÃªng áº¢o (VPC) vÃ  khÃ´ng bao giá» Ä‘Æ°á»£c hiá»ƒn thá»‹ trá»±c tiáº¿p ra internet cÃ´ng cá»™ng. Äiá»u nÃ y cung cáº¥p má»™t lá»›p báº£o vá»‡ quan trá»ng cho dá»¯ liá»‡u kinh doanh nháº¡y cáº£m.
![SÆ¡ Ä‘á»“ kiáº¿n trÃºc](/images/architecture.png)

## Káº¿t luáº­n

Vá»›i kiáº¿n trÃºc nÃ y, báº¡n cÃ³ thá»ƒ xÃ¢y dá»±ng má»™t á»©ng dá»¥ng tÃ¬m kiáº¿m sáºµn sÃ ng cho sáº£n xuáº¥t trÃªn AWS mÃ  khÃ´ng cáº§n quáº£n lÃ½ cÆ¡ sá»Ÿ háº¡ táº§ng phá»©c táº¡p.

Amazon OpenSearch Service cung cáº¥p:

Kháº£ nÄƒng tÃ¬m kiáº¿m nhanh chÃ³ng vÃ  cÃ³ thá»ƒ má»Ÿ rá»™ng, phÃ¡t triá»ƒn cÃ¹ng vá»›i nhu cáº§u cá»§a doanh nghiá»‡p
CÃ¡c tÃ­nh nÄƒng báº£o máº­t vÃ  tuÃ¢n thá»§ Ä‘Æ°á»£c tÃ­ch há»£p sáºµn vá»›i cáº¥u hÃ¬nh tá»‘i thiá»ƒu
Quáº£n lÃ½ cluster tá»± Ä‘á»™ng, cho phÃ©p AWS xá»­ lÃ½ Ä‘á»™ phá»©c táº¡p trong váº­n hÃ nh
Äá»‹nh giÃ¡ linh hoáº¡t, Ä‘áº£m báº£o báº¡n chá»‰ tráº£ tiá»n cho cÃ¡c tÃ i nguyÃªn báº¡n thá»±c sá»± sá»­ dá»¥ng

MÃ£ nguá»“n hoÃ n chá»‰nh vÃ  hÆ°á»›ng dáº«n triá»ƒn khai cÃ³ sáºµn trÃªn GitHub:

https://github.com/aws-samples/sample-for-amazon-opensearch-service-tutorials-101

Báº¡n cÃ³ thá»ƒ clone kho lÆ°u trá»¯ vÃ  báº¯t Ä‘áº§u xÃ¢y dá»±ng á»©ng dá»¥ng tÃ¬m kiáº¿m cá»§a riÃªng mÃ¬nh ngay hÃ´m nay.

BÃ i viáº¿t gá»‘c:
https://aws.amazon.com/blogs/big-data/amazon-opensearch-service-101-create-your-first-search-application-with-opensearch/