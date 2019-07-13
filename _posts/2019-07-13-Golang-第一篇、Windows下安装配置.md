---
layout:     post
title:      "第一篇 Windows下安装配置Golang"
subtitle:   "Golang"
date:       2019-07-13 
author:     "Carlos"
header-img: "img/post-bg-unix-linux.jpg"
catalog: true
tags:
    - Golang
---

# 第一篇 Windows下安装配置Golang

## 一、安装 Go
Go语言的优劣，这里就不介绍了，下面直接讲Go 的安装：

Go 的官方网站：http://golang.org/ 或者：https://golang.google.cn/dl/

国内下载地址：http://www.golangtc.com/download 或者：https://studygolang.com/dl

下载对应平台的安装包

> ps:注意区分32位还是64位操作系统

安装包下载完成之后，点击安装，下一步下一步，安装完成即可。

---

## 二、环境变量配置
注意配置环境变量：GOROOT, GOPATH, GOBIN

- GOROOT: 
```
C:\Go
```
- GOPATH:
```
C:\GoPath
```
- GOBIN
```
C:\Go\bin
```

++ 最后在环境变量Path中添加：%GOBIN% 即可++