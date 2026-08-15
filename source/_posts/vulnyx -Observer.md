---
title: vulnyx-Observer
date: 2025-12-23 14:57:38
tags: 靶场
---

# vulnyx -Observer

nmap扫一下端口

![image-20251223142421256](../images/image-20251223142421256.png)

我们可以看到，OpenSSH 正在端口 80 上运行`22`，Apache httpd 服务器正在端口 80 上运行。

扫描网页目录但是没有发现。

访问80网页

![image-20251223143248019](../images/image-20251223143248019.png)

发现有人名，尝试ssh爆破。

用cewl生成密码字典。

```
cewl http://192.168.56.114 -w dict.txt
```

![image-20251223143849247](../images/image-20251223143849247.png)

![image-20251223144306384](../images/image-20251223144306384.png)

![image-20251223144339391](../images/image-20251223144339391.png)

ssh登录不了。因此要用x11转发登录。

![image-20251223144441928](../images/image-20251223144441928.png)

登录发现remo的凭证

```remo:REMisGOD```

ssh连接上，env发现rootkey变量。

![image-20251223144917045](../images/image-20251223144917045.png)

是base64编码的私钥。我们解码为id文件。

![image-20251223145018962](../images/image-20251223145018962.png)

![image-20251223145044017](../images/image-20251223145044017.png)

```
remo@observer:~$ echo $rootKEY |base64 -d >id1
```

用它登录root

![image-20251223145155850](../images/image-20251223145155850.png)

