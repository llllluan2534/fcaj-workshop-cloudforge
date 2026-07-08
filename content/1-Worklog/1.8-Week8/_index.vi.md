---
title: "Worklog Tuáº§n 8"
date: 2026-04-17
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---



### Má»¥c tiÃªu tuáº§n 8:

* LÃ m quen vá»›i AWS CLI, hiá»ƒu Ä‘Æ°á»£c sá»± tÆ°Æ¡ng quan giá»¯a cÃ¡c lá»‡nh CLI vÃ  API cá»§a AWS.
* Thá»±c hiá»‡n cÃ i Ä‘áº·t vÃ  cáº¥u hÃ¬nh thÃ nh cÃ´ng AWS CLI trÃªn há»‡ Ä‘iá»u hÃ nh cÃ¡ nhÃ¢n (Windows, macOS hoáº·c Linux).
* Quáº£n lÃ½ an toÃ n credentials (Access key ID, Secret access key) thÃ´ng qua thÆ° má»¥c `.aws` thay vÃ¬ dÃ¹ng root account.
* Thá»±c hÃ nh thao tÃ¡c vá»›i Ä‘a dáº¡ng dá»‹ch vá»¥ (IAM, S3, EC2) trá»±c tiáº¿p tá»« dÃ²ng lá»‡nh.
* Náº¯m vá»¯ng cÃ¡c bÆ°á»›c dá»n dáº¹p credentials Ä‘á»ƒ Ä‘áº£m báº£o an toÃ n báº£o máº­t.

### CÃ¡c cÃ´ng viá»‡c cáº§n triá»ƒn khai trong tuáº§n nÃ y:
| Thá»© | CÃ´ng viá»‡c                                                                                                                                                                                   | NgÃ y báº¯t Ä‘áº§u | NgÃ y hoÃ n thÃ nh | Nguá»“n tÃ i liá»‡u                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tá»•ng quan vá» AWS CLI: CÃ´ng cá»¥ dÃ²ng lá»‡nh quáº£n lÃ½ AWS tá»« terminal thay cho web console, há»— trá»£ tá»‘t cho tá»± Ä‘á»™ng hÃ³a vÃ  DevOps. Má»—i lá»‡nh CLI tÆ°Æ¡ng á»©ng má»™t API cá»§a AWS. <br>&emsp; + IAM user & credentials: YÃªu cáº§u báº¯t buá»™c dÃ¹ng IAM user (Access Key ID / Secret Access Key), khÃ´ng dÃ¹ng root account. Credentials Ä‘Æ°á»£c lÆ°u cá»¥c bá»™ Ä‘á»ƒ CLI xÃ¡c thá»±c. | 18/06/2026   | 18/06/2026      | <https://000011.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + CÃ¡ch cáº¥u hÃ¬nh AWS CLI: DÃ¹ng lá»‡nh `configure` Ä‘á»ƒ thiáº¿t láº­p Access key, region vÃ  format. CLI tá»± Ä‘á»™ng Ä‘á»c credentials tá»« thÆ° má»¥c config mÃ¡y local. <br>&emsp; + CÃ¡c lá»‡nh cÆ¡ báº£n: Kiá»ƒm tra version, danh tÃ­nh IAM (`sts get-caller-identity`); thao tÃ¡c S3 (liá»‡t kÃª, táº¡o, xÃ³a); thao tÃ¡c EC2 (liá»‡t kÃª regions/instances); thao tÃ¡c IAM (liá»‡t kÃª user/policies). | 19/06/2026   | 19/06/2026      | <https://000011.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Chuáº©n bá»‹ IAM user & credentials: Táº¡o IAM user cho CLI, táº¡o Access Key (use case CLI), lÆ°u láº¡i ID/Secret Key vÃ  region lab. <br>&emsp; + CÃ i Ä‘áº·t AWS CLI: Táº£i vÃ  cÃ i Ä‘áº·t theo há»‡ Ä‘iá»u hÃ nh (Windows, macOS, Linux). Cháº¡y thá»­ kiá»ƒm tra phiÃªn báº£n trÃªn terminal Ä‘á»ƒ xÃ¡c nháº­n. <br>&emsp; + Cáº¥u hÃ¬nh láº§n Ä‘áº§u: Cháº¡y `aws configure` nháº­p credentials, region, output format vÃ  kiá»ƒm tra file cáº¥u hÃ¬nh. | 20/06/2026   | 20/06/2026      | <https://000011.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Kiá»ƒm tra danh tÃ­nh: Cháº¡y lá»‡nh IAM xÃ¡c nháº­n account ID vÃ  ARN khá»›p vá»›i lab. <br>&emsp; + Thao tÃ¡c S3: DÃ¹ng CLI liá»‡t kÃª buckets hiá»‡n cÃ³, táº¡o má»™t S3 bucket má»›i (náº¿u lab yÃªu cáº§u) vÃ  xÃ¡c minh láº¡i báº±ng lá»‡nh liá»‡t kÃª. <br>&emsp; + Thao tÃ¡c EC2: DÃ¹ng CLI liá»‡t kÃª regions, liá»‡t kÃª EC2 instances trong region Ä‘ang dÃ¹ng, xem thÃ´ng tin má»™t instance cá»¥ thá»ƒ. | 21/06/2026   | 21/06/2026      | <https://000011.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Thao tÃ¡c IAM: DÃ¹ng CLI liá»‡t kÃª cÃ¡c IAM user, kiá»ƒm tra policies Ä‘Æ°á»£c gáº¯n vÃ o user hiá»‡n táº¡i Ä‘á»ƒ xÃ¡c minh quyá»n háº¡n theo lab. <br>&emsp; + Dá»n dáº¹p: XÃ³a Access Key trÃªn AWS Console Ä‘á»ƒ Ä‘áº£m báº£o an toÃ n náº¿u dÃ¹ng mÃ¡y public; xÃ³a file cáº¥u hÃ¬nh cá»¥c bá»™ náº¿u khÃ´ng muá»‘n giá»¯ credentials. | 22/06/2026   | 22/06/2026      | <https://000011.awsstudygroup.com/> |

### Káº¿t quáº£ Ä‘áº¡t Ä‘Æ°á»£c tuáº§n 8:

* HoÃ n thÃ nh thao tÃ¡c cÃ i Ä‘áº·t vÃ  cáº¥u hÃ¬nh AWS CLI phÃ¹ há»£p vá»›i mÃ´i trÆ°á»ng há»‡ Ä‘iá»u hÃ nh cÃ¡ nhÃ¢n.
* Hiá»ƒu rÃµ cÆ¡ cháº¿ xÃ¡c thá»±c qua Access key vÃ  Secret key, Ä‘áº£m báº£o thá»±c hÃ nh chuáº©n báº£o máº­t khi lÃ m viá»‡c vá»›i AWS.
* Tá»± tin quáº£n lÃ½ tÃ i nguyÃªn tá»« xa báº±ng CLI vá»›i nhiá»u dá»‹ch vá»¥ phá»• biáº¿n (Amazon S3, Amazon EC2, IAM).
* RÃ¨n luyá»‡n ká»¹ nÄƒng Ä‘á»c hiá»ƒu káº¿t quáº£ Ä‘áº§u ra (output JSON) vÃ  Ã¡p dá»¥ng tham sá»‘ `--query` Ä‘á»ƒ trÃ­ch xuáº¥t dá»¯ liá»‡u mong muá»‘n.
* XÃ¢y dá»±ng thÃ³i quen tá»‘t vá» quáº£n trá»‹ rá»§i ro báº±ng viá»‡c vÃ´ hiá»‡u hÃ³a hoáº·c xÃ³a credentials cá»¥c bá»™ sau khi káº¿t thÃºc dá»± Ã¡n.

