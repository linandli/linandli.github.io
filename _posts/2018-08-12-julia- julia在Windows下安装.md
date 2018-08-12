---
layout:     post
title:      "一、 julia在Windows下安装"
subtitle:   "Windows10 X64下安装julia1.0"
date:       2018-08-12 
author:     "Carlos"
header-img: "img/post-bg-unix-linux.jpg"
catalog: true
tags:
    - julia
    - Windows
---
# The Julia Language

Julia is a high-level, high-performance dynamic language for technical computing. The main homepage for Julia can be found at julialang.org. This is the GitHub repository of Julia source code, including instructions for compiling and installing Julia, below.

## 1、下载

###### 本次我们是在Windows10 64位下安装，所以我们选择Windows X64安装包

下载地址：https://julialang.org/downloads/

```
https://julialang-s3.julialang.org/bin/winnt/x64/1.0/julia-1.0.0-win64.exe
```

## 2、下载之后一步步安装
我安装在D盘下：D:\Program Files\Julia-1.0.0

```
 D:\Program Files\Julia-1.0.0 的目录

2018/08/10  18:05    <DIR>          .
2018/08/10  18:05    <DIR>          ..
2018/08/10  18:05    <DIR>          bin
2018/08/10  18:05    <DIR>          etc
2018/08/10  18:05    <DIR>          include
2018/08/10  18:05               841 julia.lnk
2018/08/10  18:05    <DIR>          lib
2018/08/09  07:00             5,265 LICENSE.md
2018/08/10  18:05    <DIR>          share
2018/08/10  18:05           112,412 Uninstall.exe
               3 个文件        118,518 字节
               7 个目录 50,124,070,912 可用字节
```

将目录D:\Program Files\Julia-1.0.0\bin配置到环境变量Path中

## 3、测试

```
D:\Program Files\Julia-1.0.0>julia
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.0.0 (2018-08-08)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

julia> 1 + 2
3

julia>
```

Ok！大功告成！

