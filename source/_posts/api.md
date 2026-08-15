---
title: maze靶场api
date: 2025-12-12 19:33:54
tags: 靶场
---

![image-20251211153136755](../images/image-20251211153136755.png)

Nmap扫端口，访问80端口。

![image-20251211153148455](../images/image-20251211153148455.png)

观察源代码，发现新的目录

![img](../images/wps1.jpg) 

尝试访问backend-api路径。

![image-20251211153214584](../images/image-20251211153214584.png)

访问file.php

![image-20251211153240072](../images/image-20251211153240072.png)

 这里我们bp发包

![image-20251211153348413](../images/image-20251211153348413.png)

上传了一句话木马。蚁剑连接

![image-20251211153446631](../images/image-20251211153446631.png)

收集信息，发现了固定密码和用户

![image-20251211153836930](../images/image-20251211153836930.png)

![image-20251211153601008](../images/image-20251211153601008.png)

这个密码既可以登录网页，也可以登录ssh

ssh登录，得到flag

![image-20251211153804760](../images/image-20251211153804760.png)

sudo提权发现有hashcat。

![image-20251211153916599](../images/image-20251211153916599.png)

这里可以直接读flag

![image-20251211154018564](../images/image-20251211154018564.png)