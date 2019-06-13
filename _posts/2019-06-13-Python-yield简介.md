---
layout:     post
title:      "Python3 yield简介"
subtitle:   "yield简介"
date:       2019-06-13 
author:     "Carlos"
header-img: "img/post-bg-unix-linux.jpg"
catalog: true
tags:
    - Python
---

## 测试

```
#!/usr/bin/env python
# coding: utf-8

# In[5]:


def func(num):
    for i in range(num):
        yield i

data = func(10)

for _ in func(10):
    print(data.__next__())



0
1
2
3
4
5
6
7
8
9
```