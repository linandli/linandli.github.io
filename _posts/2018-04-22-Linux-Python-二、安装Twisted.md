---
layout:     post
title:      "二、安装Twisted"
subtitle:   "安装Twisted"
date:       2018-04-22 
author:     "夕阳"
header-img: "img/post-bg-unix-linux.jpg"
catalog: true
tags:
    - Linux
    - Python
---


一、获取文件

```
[root@ecs-7b5c-0005 mnt]# wget https://pypi.python.org/packages/51/ec/d52f840767d96f4a68a227aad99915e11ae5c3ff40f353a3abe9c8e119b7/Twisted-18.4.0rc1.tar.bz2#md5=a6833ce0dc81142562171265d1440765
--2018-04-12 15:09:25--  https://pypi.python.org/packages/51/ec/d52f840767d96f4a68a227aad99915e11ae5c3ff40f353a3abe9c8e119b7/Twisted-18.4.0rc1.tar.bz2
Resolving pypi.python.org (pypi.python.org)... 151.101.72.223, 2a04:4e42:36::223
Connecting to pypi.python.org (pypi.python.org)|151.101.72.223|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3037115 (2.9M) [binary/octet-stream]
Saving to: ‘Twisted-18.4.0rc1.tar.bz2’

100%[==============================================>] 3,037,115   29.5KB/s   in 99s    

2018-04-12 15:11:05 (30.0 KB/s) - ‘Twisted-18.4.0rc1.tar.bz2’ saved [3037115/3037115]
```
二、解压，安装

1.解压

```
[root@ecs-7b5c-0005 mnt]# tar xvf Twisted-18.4.0rc1.tar.bz2
```
2.安装

```
# cd Twisted-18.4.0rc1/
# source /root/py3env/bin/activate
# python setup.py install
```

