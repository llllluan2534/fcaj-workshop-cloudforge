---
title: "Worklog Tuáº§n 4"
date: 2026-04-17
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Má»¥c tiÃªu tuáº§n 4:

* Hiá»ƒu sÃ¢u sáº¯c vá» kiáº¿n trÃºc vÃ  Æ°u Ä‘iá»ƒm cá»§a dá»‹ch vá»¥ cÆ¡ sá»Ÿ dá»¯ liá»‡u quan há»‡ Ä‘Æ°á»£c quáº£n lÃ½ (Managed Relational Database) - Amazon RDS.
* Náº¯m vá»¯ng cÃ¡c mÃ´ hÃ¬nh triá»ƒn khai DB instance, cÃ¡ch lá»±a chá»n Database Engine phÃ¹ há»£p (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server).
* Thá»±c hÃ nh táº¡o, cáº¥u hÃ¬nh vÃ  káº¿t ná»‘i an toÃ n Ä‘áº¿n Amazon RDS tá»« cÃ¡c mÃ´i trÆ°á»ng máº¡ng (VPC).
* Hiá»ƒu rÃµ cÆ¡ cháº¿ báº£o máº­t cÆ¡ sá»Ÿ dá»¯ liá»‡u trÃªn cloud thÃ´ng qua Security Group vÃ  Network ACLs.
* RÃ¨n luyá»‡n ká»¹ nÄƒng quáº£n trá»‹ chi phÃ­ thÃ´ng qua viá»‡c dá»n dáº¹p vÃ  xÃ³a bá» tÃ i nguyÃªn khÃ´ng sá»­ dá»¥ng.

### CÃ¡c cÃ´ng viá»‡c cáº§n triá»ƒn khai trong tuáº§n nÃ y:
| Thá»© | CÃ´ng viá»‡c                                                                                                                                                                                   | NgÃ y báº¯t Ä‘áº§u | NgÃ y hoÃ n thÃ nh | Nguá»“n tÃ i liá»‡u                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tá»•ng quan vá» Amazon RDS: TÃ¬m hiá»ƒu cÃ¡ch AWS tá»± Ä‘á»™ng hÃ³a cÃ¡c tÃ¡c vá»¥ quáº£n trá»‹ náº·ng ná» nhÆ° provisioning, patch há»‡ Ä‘iá»u hÃ nh, backup vÃ  monitoring. <br>&emsp; + Kiáº¿n trÃºc DB instance: MÃ´i trÆ°á»ng database Ä‘á»™c láº­p trÃªn cloud, linh hoáº¡t lá»±a chá»n cáº¥u hÃ¬nh compute vÃ  storage. | 07/05/2026   | 07/05/2026      | <https://000005.awsstudygroup.com/>       |
| 3   | - **Learning Content:** <br>&emsp; + CÃ¡c Database Engine Ä‘Æ°á»£c há»— trá»£: ÄÃ¡nh giÃ¡ Æ°u nhÆ°á»£c Ä‘iá»ƒm cá»§a MySQL, PostgreSQL, MariaDB, SQL Server, vÃ  Oracle. <br>&emsp; + CÆ¡ cháº¿ káº¿t ná»‘i: Kiáº¿n trÃºc máº¡ng trong VPC, vai trÃ² cá»§a endpoint vÃ  port khi káº¿t ná»‘i tá»« á»©ng dá»¥ng hoáº·c client. | 08/05/2026   | 08/05/2026      | <https://000005.awsstudygroup.com/>       |
| 4   | - **Learning Content:** <br>&emsp; + Báº£o máº­t vÃ  phÃ¢n quyá»n truy cáº­p: Táº§m quan trá»ng cá»§a viá»‡c cÃ´ láº­p database trong private subnet. <br>&emsp; + Dá»n dáº¹p tÃ i nguyÃªn: Hiá»ƒu vÃ²ng Ä‘á»i cá»§a DB instance, snapshot vÃ  cÃ¡ch quáº£n lÃ½ chi phÃ­ lÃ¢u dÃ i. | 09/05/2026   | 09/05/2026      | <https://000005.awsstudygroup.com/>       |
| 5   | - **Practice:** <br>&emsp; + Chuáº©n bá»‹ mÃ´i trÆ°á»ng: Kháº£o sÃ¡t vÃ  cáº¥u hÃ¬nh VPC, Subnet, Security Group Ä‘áº£m báº£o kiáº¿n trÃºc máº¡ng an toÃ n. <br>&emsp; + Khá»Ÿi táº¡o DB instance: Chá»n engine (vÃ­ dá»¥ MySQL), thiáº¿t láº­p username/password gá»‘c, chá»‰ Ä‘á»‹nh network vÃ  security group, sau Ä‘Ã³ chá» instance chuyá»ƒn sang tráº¡ng thÃ¡i Available. | 10/05/2026   | 10/05/2026      | <https://000005.awsstudygroup.com/>       |
| 6   | - **Practice:** <br>&emsp; + Káº¿t ná»‘i vÃ o database: Láº¥y endpoint tá»« console, dÃ¹ng tool (nhÆ° MySQL Workbench, DBeaver hoáº·c terminal) Ä‘á»ƒ káº¿t ná»‘i vÃ  cháº¡y thá»­ cÃ¡c truy váº¥n SQL cÆ¡ báº£n. <br>&emsp; + Tá»‘i Æ°u báº£o máº­t: Tinh chá»‰nh Security Group chá»‰ má»Ÿ port cho nhá»¯ng IP/Instance cáº§n thiáº¿t. <br>&emsp; + Resource Cleanup: XÃ³a toÃ n bá»™ DB instance vÃ  cÃ¡c manual snapshot Ä‘i kÃ¨m Ä‘á»ƒ tá»‘i Æ°u hÃ³a chi phÃ­. | 11/05/2026   | 11/05/2026      | <https://000005.awsstudygroup.com/>       |


### Káº¿t quáº£ Ä‘áº¡t Ä‘Æ°á»£c tuáº§n 4:

* Hiá»ƒu vÃ  váº­n dá»¥ng thÃ nh tháº¡o dá»‹ch vá»¥ Amazon RDS Ä‘á»ƒ thiáº¿t láº­p cÆ¡ sá»Ÿ dá»¯ liá»‡u quan há»‡ trÃªn mÃ´i trÆ°á»ng AWS.
* CÃ³ kháº£ nÄƒng lÃªn káº¿ hoáº¡ch máº¡ng vÃ  báº£o máº­t cháº·t cháº½ cho database báº±ng cÃ¡ch sá»­ dá»¥ng VPC, Subnet, vÃ  Security Group.
* Khá»Ÿi táº¡o thÃ nh cÃ´ng DB instance vÃ  thá»±c hiá»‡n káº¿t ná»‘i, truy váº¥n dá»¯ liá»‡u thÃ´ng qua cÃ¡c cÃ´ng cá»¥ quáº£n trá»‹ phá»• biáº¿n.
* Tháº¥u hiá»ƒu sÃ¢u sáº¯c cÃ¡c nguyÃªn táº¯c báº£o máº­t: KhÃ´ng bao giá» má»Ÿ public access cho database trá»« khi báº¯t buá»™c, vÃ  tuÃ¢n thá»§ nguyÃªn táº¯c least privilege.
* HoÃ n thÃ nh xuáº¥t sáº¯c khÃ¢u dá»n dáº¹p (cleanup), Ä‘áº£m báº£o khÃ´ng Ä‘á»ƒ láº¡i tÃ i nguyÃªn rÃ¡c gÃ¢y lÃ£ng phÃ­ ngÃ¢n sÃ¡ch.
