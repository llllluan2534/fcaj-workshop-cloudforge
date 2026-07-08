---
title: "Blog 3"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
{{% notice warning %}}
âš ï¸ **LÆ°u Ã½:** CÃ¡c thÃ´ng tin dÆ°á»›i Ä‘Ã¢y chá»‰ nháº±m má»¥c Ä‘Ã­ch tham kháº£o, vui lÃ²ng **khÃ´ng sao chÃ©p nguyÃªn vÄƒn** cho bÃ i bÃ¡o cÃ¡o cá»§a báº¡n ká»ƒ cáº£ warning nÃ y.
{{% /notice %}}

# AI vÃ  Robot Ä‘ang thay Ä‘á»•i nÃ´ng nghiá»‡p bá»n vá»¯ng nhÆ° tháº¿ nÃ o vá»›i Amazon SageMaker AI?

HÃ´m nay mÃ¬nh muá»‘n chia sáº» má»™t bÃ i khÃ¡ thÃº vá»‹ tá»« AWS Architecture Blog vá» cÃ¡ch Aigen - má»™t cÃ´ng ty phÃ¡t triá»ƒn robot nÃ´ng nghiá»‡p tá»± hÃ nh - Ä‘Ã£ hiá»‡n Ä‘áº¡i hÃ³a toÃ n bá»™ pipeline AI báº±ng Amazon SageMaker AI Ä‘á»ƒ xÃ¢y dá»±ng há»‡ thá»‘ng canh tÃ¡c thÃ´ng minh vÃ  bá»n vá»¯ng.

Trong nÃ´ng nghiá»‡p hiá»‡n Ä‘áº¡i, viá»‡c sá»­ dá»¥ng robot Ä‘á»ƒ nháº­n diá»‡n cá» dáº¡i, theo dÃµi cÃ¢y trá»“ng hay tá»‘i Æ°u nÄƒng suáº¥t khÃ´ng cÃ²n quÃ¡ xa láº¡. Tuy nhiÃªn, khi sá»‘ lÆ°á»£ng robot ngÃ y cÃ ng tÄƒng thÃ¬ bÃ i toÃ¡n má»›i láº¡i xuáº¥t hiá»‡n:
* Robot hoáº¡t Ä‘á»™ng á»Ÿ nhá»¯ng khu vá»±c cÃ³ káº¿t ná»‘i Internet khÃ´ng á»•n Ä‘á»‹nh.
* Má»—i ngÃ y thu tháº­p hÃ ng nghÃ¬n hÃ¬nh áº£nh cáº§n gÃ¡n nhÃ£n Ä‘á»ƒ huáº¥n luyá»‡n AI.
* Háº¡ táº§ng GPU táº¡i chá»— (on-premises) khÃ´ng Ä‘á»§ sá»©c xá»­ lÃ½ Ä‘á»“ng thá»i viá»‡c huáº¥n luyá»‡n mÃ´ hÃ¬nh vÃ  gÃ¡n nhÃ£n dá»¯ liá»‡u.
* Chu ká»³ cáº­p nháº­t mÃ´ hÃ¬nh cháº­m khiáº¿n robot khÃ³ thÃ­ch nghi vá»›i Ä‘iá»u kiá»‡n thá»±c táº¿ ngoÃ i Ä‘á»“ng ruá»™ng.
* LÃ m sao Ä‘á»ƒ má»Ÿ rá»™ng hÃ ng trÄƒm robot ngoÃ i thá»±c Ä‘á»‹a mÃ  khÃ´ng pháº£i liÃªn tá»¥c Ä‘áº§u tÆ° thÃªm mÃ¡y chá»§ GPU?

AWS vÃ  Aigen Ä‘Ã£ giáº£i quyáº¿t bÃ i toÃ¡n nÃ y báº±ng má»™t kiáº¿n trÃºc AI cloud-native.

![Aigen Architecture](/images/blog_3.jpg)

### 1. Kiáº¿n trÃºc hoáº¡t Ä‘á»™ng nhÆ° tháº¿ nÃ o?
Robot sáº½ thu tháº­p dá»¯ liá»‡u trá»±c tiáº¿p ngoÃ i cÃ¡nh Ä‘á»“ng, bao gá»“m:
* HÃ¬nh áº£nh RGB vÃ  chiá»u sÃ¢u (Depth)
* Dá»¯ liá»‡u Ä‘iá»u hÆ°á»›ng
* ThÃ´ng tin cáº£m biáº¿n
* Metadata cá»§a tá»«ng nhiá»‡m vá»¥

Sau Ä‘Ã³ dá»¯ liá»‡u Ä‘Æ°á»£c gá»­i lÃªn Amazon S3 thÃ´ng qua AWS IoT Core.
Tiáº¿p theo, Amazon SageMaker AI Ä‘áº£m nhiá»‡m gáº§n nhÆ° toÃ n bá»™ pipeline Machine Learning:
* Tiá»n xá»­ lÃ½ dá»¯ liá»‡u.
* Tá»± Ä‘á»™ng gÃ¡n nhÃ£n báº±ng cÃ¡c mÃ´ hÃ¬nh thá»‹ giÃ¡c mÃ¡y tÃ­nh.
* Chá»‰ chuyá»ƒn nhá»¯ng áº£nh quan trá»ng cho con ngÆ°á»i kiá»ƒm tra (Human-in-the-loop).
* Huáº¥n luyá»‡n mÃ´ hÃ¬nh má»›i trÃªn cá»¥m GPU cá»§a SageMaker.
* Triá»ƒn khai mÃ´ hÃ¬nh tá»‘i Æ°u trá»Ÿ láº¡i robot ngoÃ i thá»±c Ä‘á»‹a.

Äiá»ƒm mÃ¬nh tháº¥y hay lÃ  AWS xÃ¢y dá»±ng má»™t vÃ²ng láº·p há»c liÃªn tá»¥c (continuous learning): robot thu tháº­p dá»¯ liá»‡u â†’ AI há»c tá»« dá»¯ liá»‡u má»›i â†’ mÃ´ hÃ¬nh Ä‘Æ°á»£c cáº£i thiá»‡n â†’ robot hoáº¡t Ä‘á»™ng chÃ­nh xÃ¡c hÆ¡n trong cÃ¡c mÃ¹a vá»¥ tiáº¿p theo.

### 2. Äiá»u gÃ¬ giÃºp giáº£m chi phÃ­ gÃ¡n nhÃ£n?
Má»™t trong nhá»¯ng Ä‘iá»ƒm ná»•i báº­t cá»§a giáº£i phÃ¡p lÃ  Active Learning.
Thay vÃ¬ yÃªu cáº§u con ngÆ°á»i gÃ¡n nhÃ£n toÃ n bá»™ hÃ ng triá»‡u bá»©c áº£nh, há»‡ thá»‘ng AI sáº½:
* Tá»± Ä‘á»™ng gÃ¡n nhÃ£n trÆ°á»›c.
* Chá»‰ chá»n nhá»¯ng hÃ¬nh áº£nh mÃ  mÃ´ hÃ¬nh chÆ°a cháº¯c cháº¯n Ä‘á»ƒ con ngÆ°á»i kiá»ƒm tra.
* DÃ¹ng cÃ¡c dá»¯ liá»‡u Ä‘Ã£ xÃ¡c nháº­n Ä‘á»ƒ tiáº¿p tá»¥c cáº£i thiá»‡n mÃ´ hÃ¬nh.

Nhá» Ä‘Ã³, Aigen vá»«a giáº£m Ä‘Ã¡ng ká»ƒ khá»‘i lÆ°á»£ng cÃ´ng viá»‡c thá»§ cÃ´ng, vá»«a nÃ¢ng cao cháº¥t lÆ°á»£ng dá»¯ liá»‡u huáº¥n luyá»‡n.

### 3. Use Case 1: Robot nháº­n diá»‡n vÃ  loáº¡i bá» cá» dáº¡i
Má»™t trong nhá»¯ng á»©ng dá»¥ng chÃ­nh cá»§a Aigen lÃ  phÃ¡t hiá»‡n cá» dáº¡i ngay trÃªn cÃ¡nh Ä‘á»“ng.
Robot sá»­ dá»¥ng Computer Vision Ä‘á»ƒ phÃ¢n biá»‡t cÃ¢y trá»“ng vÃ  cá» dáº¡i theo thá»i gian thá»±c, sau Ä‘Ã³ loáº¡i bá» cá» mÃ  khÃ´ng cáº§n phun thuá»‘c diá»‡t cá» trÃªn diá»‡n rá»™ng.
CÃ¡ch tiáº¿p cáº­n nÃ y giÃºp:
* Giáº£m lÆ°á»£ng hÃ³a cháº¥t sá»­ dá»¥ng.
* Báº£o vá»‡ Ä‘áº¥t vÃ  nguá»“n nÆ°á»›c.
* Tiáº¿t kiá»‡m chi phÃ­ cho nÃ´ng dÃ¢n.
* Háº¡n cháº¿ tÃ¬nh tráº¡ng cá» khÃ¡ng thuá»‘c.

### 4. Use Case 2: LiÃªn tá»¥c cáº£i thiá»‡n mÃ´ hÃ¬nh AI
Äiá»u kiá»‡n ngoÃ i thá»±c Ä‘á»‹a luÃ´n thay Ä‘á»•i:
* Ãnh sÃ¡ng khÃ¡c nhau.
* Äáº¥t khÃ¡c nhau.
* Giá»‘ng cÃ¢y khÃ¡c nhau.
* MÃ¹a vá»¥ khÃ¡c nhau.

Náº¿u mÃ´ hÃ¬nh khÃ´ng Ä‘Æ°á»£c cáº­p nháº­t thÆ°á»ng xuyÃªn thÃ¬ Ä‘á»™ chÃ­nh xÃ¡c sáº½ giáº£m.
Vá»›i Amazon SageMaker AI, dá»¯ liá»‡u má»›i Ä‘Æ°á»£c Ä‘Æ°a vÃ o pipeline Ä‘á»ƒ huáº¥n luyá»‡n láº¡i mÃ´ hÃ¬nh nhanh chÃ³ng, sau Ä‘Ã³ triá»ƒn khai ngÆ°á»£c trá»Ÿ láº¡i robot. Äiá»u nÃ y giÃºp há»‡ thá»‘ng thÃ­ch nghi tá»‘t hÆ¡n vá»›i tá»«ng cÃ¡nh Ä‘á»“ng vÃ  tá»«ng mÃ¹a vá»¥ mÃ  khÃ´ng bá»‹ giá»›i háº¡n bá»Ÿi háº¡ táº§ng GPU ná»™i bá»™.

### 5. Káº¿t quáº£ Ä‘áº¡t Ä‘Æ°á»£c
Theo AWS, sau khi chuyá»ƒn sang Amazon SageMaker AI, Aigen ghi nháº­n má»™t sá»‘ cáº£i thiá»‡n Ä‘Ã¡ng chÃº Ã½:
* TÄƒng 20 láº§n nÄƒng suáº¥t xá»­ lÃ½ gÃ¡n nhÃ£n dá»¯ liá»‡u.
* Giáº£m khoáº£ng 22,5 láº§n chi phÃ­ gÃ¡n nhÃ£n má»—i hÃ¬nh áº£nh.
* CÃ³ thá»ƒ thá»±c hiá»‡n hÃ ng trÄƒm thÃ­ nghiá»‡m huáº¥n luyá»‡n má»—i tuáº§n thay vÃ¬ chá»‰ vÃ i láº§n nhÆ° trÆ°á»›c.
* RÃºt ngáº¯n thá»i gian Ä‘Æ°a mÃ´ hÃ¬nh má»›i vÃ o robot tá»« vÃ i thÃ¡ng xuá»‘ng chá»‰ cÃ²n vÃ i tuáº§n.

### 6. GÃ³c nhÃ¬n cÃ¡ nhÃ¢n
Theo mÃ¬nh, Ä‘iá»ƒm Ä‘Ã¡ng há»c há»i tá»« kiáº¿n trÃºc nÃ y khÃ´ng chá»‰ lÃ  viá»‡c sá»­ dá»¥ng AI hay robot, mÃ  lÃ  thiáº¿t káº¿ má»™t pipeline Machine Learning cÃ³ kháº£ nÄƒng má»Ÿ rá»™ng.
Thay vÃ¬ Ä‘áº§u tÆ° thÃªm GPU má»—i khi sá»‘ lÆ°á»£ng robot tÄƒng lÃªn, Aigen chuyá»ƒn toÃ n bá»™ quÃ¡ trÃ¬nh huáº¥n luyá»‡n vÃ  quáº£n lÃ½ mÃ´ hÃ¬nh lÃªn ná»n táº£ng cloud cá»§a AWS. Robot chá»‰ táº­p trung vÃ o viá»‡c thu tháº­p dá»¯ liá»‡u vÃ  suy luáº­n (inference) táº¡i biÃªn (edge), cÃ²n nhá»¯ng tÃ¡c vá»¥ náº·ng nhÆ° huáº¥n luyá»‡n, gÃ¡n nhÃ£n hay tá»‘i Æ°u mÃ´ hÃ¬nh Ä‘Æ°á»£c xá»­ lÃ½ trÃªn Ä‘Ã¡m mÃ¢y.
ÄÃ¢y lÃ  má»™t vÃ­ dá»¥ ráº¥t hay vá» cÃ¡ch káº¿t há»£p AI + Robotics + Cloud Ä‘á»ƒ giáº£i quyáº¿t bÃ i toÃ¡n thá»±c táº¿ trong nÃ´ng nghiá»‡p thÃ´ng minh vÃ  phÃ¡t triá»ƒn bá»n vá»¯ng.

**Nguá»“n:** [AWS Architecture Blog â€“ How Aigen transformed agricultural robotics for sustainable farming with Amazon SageMaker AI](https://aws.amazon.com/blogs/architecture/how-aigen-transformed-agricultural-robotics-for-sustainable-farming-with-amazon-sagemaker-ai/)