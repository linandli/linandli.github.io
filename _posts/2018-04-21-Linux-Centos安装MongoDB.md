---
layout:     post
title:      "一、CentOS7下安装MongoDB"
subtitle:   "CentOS7下安装MongoDB"
date:       2018-04-21 
author:     "Carlos"
header-img: "img/post-bg-unix-linux.jpg"
catalog: true
tags:
    - Linux
---

# 一、CentOS7下安装MongoDB

# 安装步骤：

#### 1、配置MongoDB的yum源

```
# vim /etc/yum.repos.d/mongodb-org-3.6.repo
```
添加以下配置：

```
[mongodb-org-3.6]  
name=MongoDB Repository  
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.6/x86_64/  
gpgcheck=1  
enabled=1  
gpgkey=https://www.mongodb.org/static/pgp/server-3.6.asc

```
这里可以修改 gpgcheck=0, 省去gpg验证

如果连接超时，可以尝试将https改为http

安装之前先更新所有包 ：yum update （可选操作）
#### 2、安装MongoDB

```
# yum -y install mongodb-org
```

安装完成后

查看mongo安装位置 whereis mongod

查看修改配置文件 ： vim /etc/mongod.conf

#### 3、修改mongod.conf配置文件


```
# network interfaces
net:
  port: 23456
  bindIp: 127.0.0.1  # Listen to local interface only, comment to listen on all interfaces.

```

修改端口号和绑定IP

#### 4、启动MongoDB

```
mongod -f /etc/mongod.conf
```
启动mongdb之后，创建用户：

```
mongo --port 23456

use admin

db.createUser({user:"togeek",pwd:"tuji2013",roles:["root"]})

验证：
db.auth("togeek", "tuji2013")
```
杀掉mongod进程，重新启动：

```
mongod -f /etc/mongod.conf --auth
```
用户名和密码登录：

```
# mongo --port 23456 -u "togeek" -p "tuji2013" --authenticationDatabase "admin"
```
若要远程登录连接MongoDB，需要修改配置文件：

```
# vim /etc/mongod.conf


# network interfaces
net:
  port: 23456
  bindIp: 0.0.0.0  # Listen to local interface only, comment to listen on all interfaces.

```

#### 5、启动服务

因为从始至终都使用root权限进行操作，所以需要在mongd.service设置User

```
[root@ecs-7b5c-0005 mongodb]# vim /usr/lib/systemd/system/mongod.service
```


```
[Unit]
Description=High-performance, schema-free document-oriented database
After=network.target
Documentation=https://docs.mongodb.org/manual

[Service]
User=root
#Group=root
Environment="OPTIONS=-f /etc/mongod.conf --auth"
ExecStart=/usr/bin/mongod $OPTIONS
ExecStartPre=/usr/bin/mkdir -p /var/run/mongodb
ExecStartPre=/usr/bin/chown mongod:mongod /var/run/mongodb
ExecStartPre=/usr/bin/chmod 0755 /var/run/mongodb
PermissionsStartOnly=true
PIDFile=/mnt/mongodb/mongod.pid
Type=forking
# file size
LimitFSIZE=infinity
# cpu time
LimitCPU=infinity
# virtual memory size
LimitAS=infinity
# open files
LimitNOFILE=64000
# processes/threads
LimitNPROC=64000
# locked memory
LimitMEMLOCK=infinity
# total threads (user+kernel)
TasksMax=infinity
TasksAccounting=false
# Recommended limits for for mongod as specified in
# http://docs.mongodb.org/manual/reference/ulimit/#recommended-settings
```

启动服务：

```
[root@ecs-7b5c-0005 mongodb]# systemctl start mongod.service
```
查看服务状态：

```
[root@ecs-7b5c-0005 mongodb]# systemctl status mongod.service

```
结束服务：

```

[root@ecs-7b5c-0005 mongodb]# systemctl stop mongod.service

```
重启服务：

```

[root@ecs-7b5c-0005 mongodb]# systemctl restart mongod.service

```

