---
layout:     post
title:      "Centos7安装erlang"
subtitle:   "Centos7安装erlang"
date:       2018-07-07 
author:     "Carlos"
header-img: "img/post-bg-unix-linux.jpg"
catalog: true
tags:
    - Linux
    - Erlang
---

## 一、安装Erlang
下载erlang安装包
```
wget http://erlang.org/download/otp_src_21.0.tar.gz
```

解压
```
tar -zxvf otp_src_21.0.tar.gz 
```

创建文件夹
```
mkdir /usr/local/erlang
```

编译
```
# cd otp_src_21.0/
# ./configure --prefix=/usr/local/erlang --without-javac
# make && make install
```

创建软连接
```
ln -s /usr/local/erlang/bin/erl /usr/bin/erl
```

测试
```
# erl
Erlang/OTP 21 [erts-10.0] [source] [64-bit] [smp:2:2] [ds:2:2:10] [async-threads:1] [hipe]

Eshell V10.0  (abort with ^G)
1> 
```
## OK! 大功告成！