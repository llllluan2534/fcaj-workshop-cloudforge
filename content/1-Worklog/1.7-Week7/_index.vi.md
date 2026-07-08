---

title: "Worklog Tuáº§n 7"
date: 2026-04-17
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---



### Má»¥c tiÃªu tuáº§n 7:

* LÃ m quen vá»›i Route 53 Resolver, hiá»ƒu cÃ¡ch dÃ¹ng Outbound Endpoint, Inbound Endpoint vÃ  Resolver Rules.
* Thiáº¿t láº­p há»‡ thá»‘ng Hybrid DNS giá»¯a mÃ´i trÆ°á»ng AWS vÃ  mÃ´i trÆ°á»ng on-premise (hoáº·c AWS Managed AD).
* Cáº¥u hÃ¬nh Ä‘á»‹nh tuyáº¿n truy váº¥n DNS Ä‘á»“ng nháº¥t, cho phÃ©p hai bÃªn phÃ¢n giáº£i tÃªn miá»n ná»™i bá»™ cá»§a nhau má»™t cÃ¡ch liá»n máº¡ch.

### CÃ¡c cÃ´ng viá»‡c cáº§n triá»ƒn khai trong tuáº§n nÃ y:
| Thá»© | CÃ´ng viá»‡c                                                                                                                                                                                   | NgÃ y báº¯t Ä‘áº§u | NgÃ y hoÃ n thÃ nh | Nguá»“n tÃ i liá»‡u                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - **Learning Content:** <br>&emsp; + Tá»•ng quan Hybrid DNS & Route 53 Resolver: MÃ´ hÃ¬nh káº¿t há»£p há»‡ thá»‘ng DNS on-premise (hoáº·c AD) vá»›i DNS trong AWS. <br>&emsp; + Outbound Endpoint (Red Arrow): Cho phÃ©p Route 53 Resolver gá»­i truy váº¥n DNS ra ngoÃ i. | 11/06/2026   | 11/06/2026      | <https://000010.awsstudygroup.com/> |
| 3   | - **Learning Content:** <br>&emsp; + Resolver Rules (Forwarding rule): Äá»‹nh nghÄ©a luáº­t chuyá»ƒn tiáº¿p truy váº¥n tá»›i DNS server Ä‘Ã­ch qua Outbound Endpoint. <br>&emsp; + Inbound Endpoint (Blue Arrow): Cho phÃ©p há»‡ thá»‘ng DNS bÃªn ngoÃ i gá»­i truy váº¥n vÃ o VPC Ä‘á»ƒ Route 53 Resolver tráº£ lá»i. <br>&emsp; + DNS forwarding tá»« on-prem/AD vá» AWS: Cáº¥u hÃ¬nh rule trÃªn DNS ná»™i bá»™. | 12/06/2026   | 12/06/2026      | <https://000010.awsstudygroup.com/> |
| 4   | - **Practice:** <br>&emsp; + Chuáº©n bá»‹ mÃ´i trÆ°á»ng: Kiá»ƒm tra VPC, subnet, security group vÃ  mÃ´i trÆ°á»ng on-prem (hoáº·c Managed AD) cÃ³ sáºµn. <br>&emsp; + Táº¡o Outbound Endpoint: Äáº·t tÃªn, chá»n VPC, subnets, gÃ¡n security group cho phÃ©p port 53 (UDP/TCP) vÃ  kiá»ƒm tra tráº¡ng thÃ¡i "Operational". | 13/06/2026   | 13/06/2026      | <https://000010.awsstudygroup.com/> |
| 5   | - **Practice:** <br>&emsp; + Táº¡o Resolver Rule forward Ä‘áº¿n DNS AD/on-prem: Khai bÃ¡o domain ná»™i bá»™, trá» IP Ä‘Ã­ch vá» DNS server bÃªn ngoÃ i, gÃ¡n vÃ o VPC. <br>&emsp; + Táº¡o Inbound Endpoint: Cáº¥u hÃ¬nh cho phÃ©p UDP/TCP port 53 nháº­n tá»« ngoÃ i vÃ o vÃ  ghi láº¡i IP Ä‘á»ƒ dÃ¹ng cáº¥u hÃ¬nh forwarder. <br>&emsp; + Cáº¥u hÃ¬nh DNS forwarding trÃªn on-prem/AD trá» vá» Inbound Endpoint. | 14/06/2026   | 14/06/2026      | <https://000010.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Kiá»ƒm tra Private Hosted Zone trÃªn Route 53: Äáº£m báº£o báº£n ghi A/CNAME trá» Ä‘Ãºng IP private. <br>&emsp; + Kiá»ƒm tra phÃ¢n giáº£i hai chiá»u: DÃ¹ng nslookup/dig trÃªn EC2 AWS Ä‘á»ƒ truy váº¥n domain on-prem (vÃ  ngÆ°á»£c láº¡i tá»« on-prem truy váº¥n AWS private domain). Kháº¯c phá»¥c náº¿u cÃ³ lá»—i. | 15/06/2026   | 15/06/2026      | <https://000010.awsstudygroup.com/> |

### Káº¿t quáº£ Ä‘áº¡t Ä‘Æ°á»£c tuáº§n 7:

* Náº¯m báº¯t vÃ  váº­n dá»¥ng thá»±c táº¿ kiáº¿n trÃºc Hybrid DNS káº¿t ná»‘i há»‡ thá»‘ng máº¡ng on-premise vá»›i mÃ´i trÆ°á»ng AWS.
* Hiá»ƒu sÃ¢u sáº¯c vÃ  triá»ƒn khai thÃ nh tháº¡o cÃ¡c Inbound & Outbound Endpoints cá»§a Amazon Route 53 Resolver.
* LÃ m chá»§ viá»‡c thiáº¿t láº­p cÃ¡c Resolver Rules Ä‘á»ƒ Ä‘á»‹nh tuyáº¿n cÃ¡c truy váº¥n DNS (DNS Forwarding) Ä‘a chiá»u má»™t cÃ¡ch chÃ­nh xÃ¡c.
* CÃ³ kháº£ nÄƒng cháº©n Ä‘oÃ¡n, troubleshooting vÃ  kháº¯c phá»¥c sá»± cá»‘ phÃ¢n giáº£i tÃªn miá»n giá»¯a nhiá»u mÃ´i trÆ°á»ng káº¿t há»£p thÃ´ng qua cÃ¡c cÃ´ng cá»¥ nhÆ° nslookup hay dig.
* Äáº£m báº£o tÃ­nh liá»n máº¡ch vÃ  thá»‘ng nháº¥t cho cÃ¡c á»©ng dá»¥ng cháº¡y lai (hybrid) thÃ´ng qua há»‡ thá»‘ng phÃ¢n giáº£i tÃªn miá»n táº­p trung.
