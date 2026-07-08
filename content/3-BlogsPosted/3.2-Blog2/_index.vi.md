---
title: "Blog 2"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---


# Tá»± Ä‘á»™ng sá»‘ hÃ³a há»“ sÆ¡ bá»‡nh Ã¡n vá»›i Amazon Bedrock Data Automation vÃ  AWS HealthLake

HÃ´m nay mÃ¬nh muá»‘n chia sáº» má»™t kiáº¿n trÃºc khÃ¡ thÃº vá»‹ tá»« AWS dÃ nh cho lÄ©nh vá»±c y táº¿: tá»± Ä‘á»™ng sá»‘ hÃ³a há»“ sÆ¡ bá»‡nh Ã¡n báº±ng AI vá»›i Amazon Bedrock Data Automation káº¿t há»£p AWS HealthLake.

Trong quÃ¡ trÃ¬nh chuyá»ƒn Ä‘á»•i sá»‘, ráº¥t nhiá»u bá»‡nh viá»‡n váº«n Ä‘ang lÆ°u trá»¯ bá»‡nh Ã¡n dÆ°á»›i dáº¡ng giáº¥y hoáº·c PDF scan. Äiá»u nÃ y khiáº¿n viá»‡c tÃ¬m kiáº¿m thÃ´ng tin, tá»•ng há»£p lá»‹ch sá»­ Ä‘iá»u trá»‹ hay chia sáº» dá»¯ liá»‡u giá»¯a cÃ¡c há»‡ thá»‘ng máº¥t khÃ¡ nhiá»u thá»i gian. Náº¿u nháº­p liá»‡u thá»§ cÃ´ng thÃ¬ vá»«a tá»‘n nhÃ¢n lá»±c, vá»«a dá»… xáº£y ra sai sÃ³t.

BÃ i toÃ¡n Ä‘áº·t ra lÃ : lÃ m tháº¿ nÃ o Ä‘á»ƒ tá»± Ä‘á»™ng chuyá»ƒn cÃ¡c tÃ i liá»‡u y táº¿ khÃ´ng cÃ³ cáº¥u trÃºc thÃ nh dá»¯ liá»‡u sá»‘ cÃ³ thá»ƒ tÃ¬m kiáº¿m, phÃ¢n tÃ­ch vÃ  tÃ­ch há»£p vá»›i cÃ¡c há»‡ thá»‘ng quáº£n lÃ½ bá»‡nh viá»‡n?

AWS Ä‘Æ°a ra má»™t kiáº¿n trÃºc serverless káº¿t há»£p AI Ä‘á»ƒ giáº£i quyáº¿t bÃ i toÃ¡n nÃ y.

## Kiáº¿n trÃºc hoáº¡t Ä‘á»™ng nhÆ° tháº¿ nÃ o?

![Kiáº¿n trÃºc hoáº¡t Ä‘á»™ng](/images/blog_2.jpg)

ToÃ n bá»™ quy trÃ¬nh Ä‘Æ°á»£c kÃ­ch hoáº¡t tá»± Ä‘á»™ng ngay khi há»“ sÆ¡ Ä‘Æ°á»£c táº£i lÃªn Amazon S3.

Luá»“ng xá»­ lÃ½ gá»“m cÃ¡c bÆ°á»›c:
1. NgÆ°á»i dÃ¹ng upload há»“ sÆ¡ bá»‡nh Ã¡n (PDF hoáº·c hÃ¬nh áº£nh) lÃªn Amazon S3.
2. AWS Lambda nháº­n sá»± kiá»‡n upload vÃ  khá»Ÿi Ä‘á»™ng pipeline.
3. Amazon Bedrock Data Automation phÃ¢n tÃ­ch tÃ i liá»‡u, tá»± Ä‘á»™ng trÃ­ch xuáº¥t cÃ¡c thÃ´ng tin quan trá»ng nhÆ°:
   - ThÃ´ng tin bá»‡nh nhÃ¢n
   - Cháº©n Ä‘oÃ¡n
   - Káº¿t quáº£ xÃ©t nghiá»‡m
   - ÄÆ¡n thuá»‘c
   - Dáº¥u hiá»‡u sinh tá»“n
4. Dá»¯ liá»‡u sau Ä‘Ã³ Ä‘Æ°á»£c chuyá»ƒn sang chuáº©n FHIR R4.
5. AWS HealthLake lÆ°u trá»¯ vÃ  láº­p chá»‰ má»¥c Ä‘á»ƒ cÃ¡c há»‡ thá»‘ng y táº¿ cÃ³ thá»ƒ truy váº¥n thÃ´ng qua API tiÃªu chuáº©n.

Äiá»ƒm mÃ¬nh tháº¥y hay lÃ  toÃ n bá»™ quy trÃ¬nh hoáº¡t Ä‘á»™ng theo mÃ´ hÃ¬nh event-driven, nghÄ©a lÃ  chá»‰ xá»­ lÃ½ khi cÃ³ tÃ i liá»‡u má»›i Ä‘Æ°á»£c táº£i lÃªn, khÃ´ng cáº§n duy trÃ¬ mÃ¡y chá»§ cháº¡y liÃªn tá»¥c.

## Amazon Bedrock Data Automation cÃ³ gÃ¬ Ä‘áº·c biá»‡t?

Äiá»ƒm ná»•i báº­t nháº¥t lÃ  khÃ´ng cáº§n tá»± xÃ¢y dá»±ng pipeline OCR vÃ  NLP riÃªng.

ThÃ´ng thÆ°á»ng Ä‘á»ƒ xá»­ lÃ½ há»“ sÆ¡ bá»‡nh Ã¡n, doanh nghiá»‡p sáº½ pháº£i káº¿t há»£p nhiá»u bÆ°á»›c:
- OCR
- Layout Analysis
- Entity Extraction
- Chuáº©n hÃ³a dá»¯ liá»‡u
- Mapping sang FHIR

Giá» Ä‘Ã¢y Amazon Bedrock Data Automation giÃºp tá»± Ä‘á»™ng hÃ³a pháº§n lá»›n quy trÃ¬nh nÃ y, giáº£m Ä‘Ã¡ng ká»ƒ cÃ´ng sá»©c phÃ¡t triá»ƒn vÃ  báº£o trÃ¬.

ÄÃ¢y lÃ  hÆ°á»›ng tiáº¿p cáº­n ráº¥t phÃ¹ há»£p vá»›i cÃ¡c tá»• chá»©c muá»‘n nhanh chÃ³ng triá»ƒn khai AI mÃ  khÃ´ng cáº§n xÃ¢y dá»±ng mÃ´ hÃ¬nh tá»« Ä‘áº§u.

## Use Case 1: Sá»‘ hÃ³a bá»‡nh Ã¡n cÅ©

Má»™t bá»‡nh viá»‡n cÃ³ thá»ƒ cÃ³ hÃ ng triá»‡u há»“ sÆ¡ bá»‡nh Ã¡n giáº¥y Ä‘Æ°á»£c lÆ°u trá»¯ nhiá»u nÄƒm.
Thay vÃ¬ pháº£i nháº­p liá»‡u thá»§ cÃ´ng, toÃ n bá»™ tÃ i liá»‡u cÃ³ thá»ƒ Ä‘Æ°á»£c upload lÃªn Amazon S3.

Pipeline sáº½ tá»± Ä‘á»™ng:
- TrÃ­ch xuáº¥t dá»¯ liá»‡u
- Chuáº©n hÃ³a
- LÆ°u vÃ o AWS HealthLake

Sau Ä‘Ã³ bÃ¡c sÄ© chá»‰ cáº§n tÃ¬m kiáº¿m theo tÃªn bá»‡nh nhÃ¢n, mÃ£ bá»‡nh hoáº·c lá»‹ch sá»­ Ä‘iá»u trá»‹ thay vÃ¬ má»Ÿ tá»«ng táº­p há»“ sÆ¡ giáº¥y.

## Use Case 2: Há»— trá»£ AI phÃ¢n tÃ­ch há»“ sÆ¡ bá»‡nh nhÃ¢n

Khi dá»¯ liá»‡u Ä‘Ã£ Ä‘Æ°á»£c chuáº©n hÃ³a theo FHIR, viá»‡c xÃ¢y dá»±ng cÃ¡c á»©ng dá»¥ng AI sáº½ trá»Ÿ nÃªn dá»… dÃ ng hÆ¡n ráº¥t nhiá»u.

VÃ­ dá»¥:
- AI tÃ³m táº¯t lá»‹ch sá»­ Ä‘iá»u trá»‹
- Chatbot há»— trá»£ bÃ¡c sÄ© tra cá»©u bá»‡nh Ã¡n
- PhÃ¢n tÃ­ch xu hÆ°á»›ng Ä‘iá»u trá»‹
- Há»— trá»£ nghiÃªn cá»©u lÃ¢m sÃ ng
- Káº¿t ná»‘i dá»¯ liá»‡u giá»¯a nhiá»u bá»‡nh viá»‡n

ÄÃ¢y cÅ©ng lÃ  ná»n táº£ng quan trá»ng Ä‘á»ƒ phÃ¡t triá»ƒn cÃ¡c há»‡ thá»‘ng Generative AI trong lÄ©nh vá»±c y táº¿.

## VÃ¬ sao AWS sá»­ dá»¥ng HealthLake?

Äiá»ƒm mÃ¬nh Ä‘Ã¡nh giÃ¡ cao lÃ  AWS khÃ´ng chá»‰ táº­p trung vÃ o viá»‡c "Ä‘á»c Ä‘Æ°á»£c tÃ i liá»‡u", mÃ  cÃ²n chuáº©n hÃ³a dá»¯ liá»‡u theo FHIR (Fast Healthcare Interoperability Resources) â€” tiÃªu chuáº©n trao Ä‘á»•i dá»¯ liá»‡u y táº¿ Ä‘Æ°á»£c sá»­ dá»¥ng rá»™ng rÃ£i trÃªn tháº¿ giá»›i.

Äiá»u nÃ y giÃºp dá»¯ liá»‡u sau khi xá»­ lÃ½ khÃ´ng bá»‹ "khÃ³a" trong má»™t á»©ng dá»¥ng riÃªng, mÃ  cÃ³ thá»ƒ tÃ­ch há»£p vá»›i nhiá»u há»‡ thá»‘ng HIS, EMR hoáº·c cÃ¡c á»©ng dá»¥ng AI khÃ¡c.

## Má»™t vÃ i lÆ°u Ã½ khi triá»ƒn khai

AWS cÅ©ng lÆ°u Ã½ ráº±ng kiáº¿n trÃºc trong bÃ i viáº¿t Ä‘Æ°á»£c xÃ¢y dá»±ng Ä‘á»ƒ minh há»a.
Náº¿u triá»ƒn khai trÃªn dá»¯ liá»‡u bá»‡nh nhÃ¢n tháº­t, cáº§n bá»• sung thÃªm cÃ¡c yÃªu cáº§u vá» báº£o máº­t nhÆ°:
- MÃ£ hÃ³a dá»¯ liá»‡u khi lÆ°u trá»¯ vÃ  truyá»n táº£i.
- Quáº£n lÃ½ quyá»n truy cáº­p báº±ng IAM theo nguyÃªn táº¯c quyá»n tá»‘i thiá»ƒu.
- Theo dÃµi hoáº¡t Ä‘á»™ng báº±ng CloudTrail.
- Triá»ƒn khai trong mÃ´i trÆ°á»ng Ä‘Ã¡p á»©ng cÃ¡c yÃªu cáº§u tuÃ¢n thá»§ nhÆ° HIPAA (náº¿u Ã¡p dá»¥ng).

## Tá»•ng káº¿t

Theo mÃ¬nh, Ä‘iá»u Ä‘Ã¡ng giÃ¡ nháº¥t cá»§a kiáº¿n trÃºc nÃ y khÃ´ng náº±m á»Ÿ AI hay OCR riÃªng láº», mÃ  lÃ  kháº£ nÄƒng tá»± Ä‘á»™ng chuyá»ƒn Ä‘á»•i tÃ i liá»‡u y táº¿ khÃ´ng cÃ³ cáº¥u trÃºc thÃ nh dá»¯ liá»‡u chuáº©n hÃ³a, sáºµn sÃ ng cho cÃ¡c há»‡ thá»‘ng vÃ  á»©ng dá»¥ng AI sá»­ dá»¥ng.

ÄÃ¢y lÃ  má»™t vÃ­ dá»¥ Ä‘iá»ƒn hÃ¬nh cho cÃ¡ch AWS káº¿t há»£p Serverless + AI + Chuáº©n dá»¯ liá»‡u ngÃ nh Ä‘á»ƒ giáº£i quyáº¿t má»™t bÃ i toÃ¡n ráº¥t thá»±c táº¿ trong lÄ©nh vá»±c chÄƒm sÃ³c sá»©c khá»e.

- Tham kháº£o tá»« AWS Architecture Blog: [Automate medical record digitization with Amazon Bedrock Data Automation and AWS HealthLake](https://aws.amazon.com/blogs/architecture/automate-medical-record-digitization-with-amazon-bedrock-data-automation-and-aws-healthlake/)