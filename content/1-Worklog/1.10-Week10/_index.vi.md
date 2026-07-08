---
title: "Worklog Tuáº§n 10"
date: 2026-04-17
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---


### Má»¥c tiÃªu tuáº§n 10:

* Hiá»ƒu rÃµ khÃ¡i niá»‡m IAM role vÃ  á»©ng dá»¥ng cá»§a nÃ³ trong viá»‡c cáº¥p quyá»n an toÃ n cho cÃ¡c dá»‹ch vá»¥ AWS.
* Náº¯m vá»¯ng nguyÃªn táº¯c cáº¥p quyá»n tá»‘i thiá»ƒu (least privilege) Ä‘á»ƒ báº£o vá»‡ tÃ i nguyÃªn hiá»‡u quáº£.
* Thá»±c hÃ nh táº¡o, gáº¯n vÃ  kiá»ƒm tra IAM role trÃªn EC2 instance.
* LÃ m quen vá»›i AWS Cloud9, má»™t mÃ´i trÆ°á»ng IDE trÃªn ná»n táº£ng Ä‘Ã¡m mÃ¢y.
* Quáº£n lÃ½ chi phÃ­ báº±ng cÃ¡ch váº­n hÃ nh vÃ  dá»n dáº¹p tÃ i nguyÃªn (Cloud9, IAM role) há»£p lÃ½.

### CÃ¡c cÃ´ng viá»‡c cáº§n triá»ƒn khai trong tuáº§n nÃ y:
| Thá»© | CÃ´ng viá»‡c                                                                                                                                                                                   | NgÃ y báº¯t Ä‘áº§u | NgÃ y hoÃ n thÃ nh | Nguá»“n tÃ i liá»‡u                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + TÃ¬m hiá»ƒu IAM role lÃ  gÃ¬ vÃ  cÃ¡ch á»©ng dá»¥ng truy cáº­p AWS services an toÃ n (khÃ´ng hardcode access key). <br>&emsp; + Náº¯m vá»¯ng cÃ¡c nguyÃªn táº¯c cáº¥p quyá»n tá»‘i thiá»ƒu. | 28/05/2026 | 28/05/2026 | <https://000048.awsstudygroup.com/> |
| 3   | - **Practice:** <br>&emsp; + Táº¡o IAM role vÃ  gáº¯n policy cáº§n thiáº¿t. <br>&emsp; + Gáº¯n role vÃ o EC2 instance vÃ  kiá»ƒm tra quyá»n truy cáº­p. <br>&emsp; + Thá»±c hiá»‡n dá»n dáº¹p role khá»i instance khi khÃ´ng cÃ²n sá»­ dá»¥ng. | 29/05/2026   | 29/05/2026      | <https://000048.awsstudygroup.com/>       |
| 4   | - **Learning Content:** <br>&emsp; + TÃ¬m hiá»ƒu AWS Cloud9 lÃ  gÃ¬ vÃ  cÃ¡ch thá»©c hoáº¡t Ä‘á»™ng dá»±a trÃªn EC2. <br>&emsp; + KhÃ¡m phÃ¡ cÃ¡ch lÃ m viá»‡c trong IDE (file explorer, terminal, editor) ngay trÃªn trÃ¬nh duyá»‡t. | 30/05/2026   | 30/05/2026      | <https://000049.awsstudygroup.com/>       |
| 5   | - **Practice:** <br>&emsp; + Táº¡o Cloud9 environment vá»›i cáº¥u hÃ¬nh instance vÃ  ná»n táº£ng phÃ¹ há»£p. <br>&emsp; + Má»Ÿ IDE, thá»­ code, thao tÃ¡c file vÃ  káº¿t ná»‘i thá»­ vá»›i tÃ i nguyÃªn AWS. | 31/05/2026   | 31/05/2026      | <https://000049.awsstudygroup.com/>       |
| 6   | - **Learning & Practice:** <br>&emsp; + TÃ¬m hiá»ƒu vá» quáº£n lÃ½ chi phÃ­ cho Cloud9 (dá»«ng instance khi khÃ´ng dÃ¹ng). <br>&emsp; + Dá»«ng mÃ´i trÆ°á»ng sau khi hoÃ n thÃ nh lab vÃ  kiá»ƒm tra tÃ i nguyÃªn EC2 backend Ä‘á»ƒ trÃ¡nh phÃ¡t sinh chi phÃ­. | 01/06/2026   | 01/06/2026      | <https://000049.awsstudygroup.com/>       |

### Káº¿t quáº£ Ä‘áº¡t Ä‘Æ°á»£c tuáº§n 10:

* Hiá»ƒu vÃ  váº­n dá»¥ng thÃ nh cÃ´ng IAM role Ä‘á»ƒ cáº¥p quyá»n cho á»©ng dá»¥ng cháº¡y trÃªn EC2 truy cáº­p an toÃ n cÃ¡c dá»‹ch vá»¥ AWS.
* Náº¯m vá»¯ng cÃ¡ch quáº£n lÃ½, Ä‘iá»u chá»‰nh vÃ  dá»n dáº¹p cÃ¡c quyá»n khÃ´ng cáº§n thiáº¿t tuÃ¢n theo nguyÃªn táº¯c quyá»n háº¡n tá»‘i thiá»ƒu.
* Khá»Ÿi táº¡o vÃ  thiáº¿t láº­p thÃ nh cÃ´ng mÃ´i trÆ°á»ng láº­p trÃ¬nh Ä‘Ã¡m mÃ¢y AWS Cloud9.
* Thá»±c hiá»‡n thÃ nh cÃ´ng viá»‡c láº­p trÃ¬nh, cháº¡y lá»‡nh vÃ  káº¿t ná»‘i tÃ i nguyÃªn ngay trÃªn trÃ¬nh duyá»‡t thÃ´ng qua Cloud9 IDE.
* Äáº£m báº£o kiá»ƒm soÃ¡t chi phÃ­ tá»‘t thÃ´ng qua viá»‡c dá»«ng hoáº·c táº¯t cÃ¡c mÃ´i trÆ°á»ng Cloud9/EC2 khi khÃ´ng cÃ³ nhu cáº§u sá»­ dá»¥ng.
