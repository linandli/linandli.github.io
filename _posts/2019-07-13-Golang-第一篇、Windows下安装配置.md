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

> 最后在环境变量Path中添加：%GOBIN% 即可

---

## 三、测试

打开cmd命令窗口，测试如下：
```
cheng>go version
go version go1.12.7 windows/amd64
```

```
cheng>go env
set GOARCH=amd64
set GOBIN=C:\Go\bin
set GOCACHE=C:\Users\cheng\AppData\Local\go-build
set GOEXE=.exe
set GOFLAGS=
set GOHOSTARCH=amd64
set GOHOSTOS=windows
set GOOS=windows
set GOPATH=C:\GoPath
set GOPROXY=
set GORACE=
set GOROOT=C:\Go
set GOTMPDIR=
set GOTOOLDIR=C:\Go\pkg\tool\windows_amd64
set GCCGO=gccgo
set CC=gcc
set CXX=g++
set CGO_ENABLED=1
set GOMOD=
set CGO_CFLAGS=-g -O2
set CGO_CPPFLAGS=
set CGO_CXXFLAGS=-g -O2
set CGO_FFLAGS=-g -O2
set CGO_LDFLAGS=-g -O2
set PKG_CONFIG=pkg-config
set GOGCCFLAGS=-m64 -mthreads -fno-caret-diagnostics -Qunused-arguments -fmessage-length=0 -fdebug-prefix-map=C:\Users\cheng\AppData\Local\Temp\go-build469888466=/tmp/go-build -gno-record-gcc-switches
```

---

## 四、写个测试代码
test.go
```
package main
import (
    "fmt"
)

func main() {
    fmt.Println("Hello World!") 
}
```
运行代码：
```
go run test.go
```

结果如下：
```
Hello World!
```

---

# Ok, 大功告成！