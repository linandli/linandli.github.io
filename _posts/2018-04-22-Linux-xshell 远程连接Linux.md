---
layout:     post
title:      "xshell 远程连接Linux"
subtitle:   "xshell 远程连接Linux"
date:       2016-08-09 
author:     "Carlos"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Linux
    - Windows
---

# xshell 远程连接Linux
　　　Linux系统（Ubuntu 16.04）

　　　Windows系统（win10）

　　　工具：xshell


```
Linux下，

sudo apt-get update
sudo apt-get install openssh-server

安装成功后，启动：
sudo service ssh start


接下来修改配置：

sudo vim /etc/ssh/sshd_config

把配置文件中的"PermitRootLogin without-password"注掉

增加"PermitRootLogin yes"

最后查询IP：
ifconfig
```


```
在Win端安装Xshell, 个人版足够使用

然后连接Linux中查到的IP

输入用户名和密码之后，大功告成！
```


　　　