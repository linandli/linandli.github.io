---
layout:     post
title:      "一、CentOS安装python3环境"
subtitle:   "CentOS安装python3环境"
date:       2018-04-22 
author:     "Carlos"
header-img: "img/post-bg-unix-linux.jpg"
catalog: true
tags:
    - Linux
    - Python
---


一、安装wget

```
[root@ecs-7b5c-0005 ~]# yum install wget
```
二、使用wget下载python3安装包(目前最新的release版本是3.6.5)

```
[root@ecs-7b5c-0005 ~]# wget https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tgz
```
三、解压安装包

```
[root@ecs-7b5c-0005 ~]# tar zxvf Python-3.6.5.tgz
```
四、创建一个空的文件夹

```
[root@ecs-7b5c-0005 ~]# mkdir /usr/local/python3
yum install openssl-devel -y 
```
五、编译安装Python3

```
./configure --prefix=/usr/local/python3
make && make install
```

==遇到错误：==

```
zipimport.ZipImportError: can't decompress data; zlib not available
```
解决方案：

是因为缺少zlib 的相关工具包导致的

```
yum -y install zlib*
```

最近遇到一个问题：
```
Traceback (most recent call last):
  File "/home/carlos/Python-3.7.0/Lib/runpy.py", line 193, in _run_module_as_main
    "__main__", mod_spec)
  File "/home/carlos/Python-3.7.0/Lib/runpy.py", line 85, in _run_code
    exec(code, run_globals)
  File "/home/carlos/Python-3.7.0/Lib/ensurepip/__main__.py", line 5, in <module>
    sys.exit(ensurepip._main())
  File "/home/carlos/Python-3.7.0/Lib/ensurepip/__init__.py", line 204, in _main
    default_pip=args.default_pip,
  File "/home/carlos/Python-3.7.0/Lib/ensurepip/__init__.py", line 117, in _bootstrap
    return _run_pip(args + [p[0] for p in _PROJECTS], additional_paths)
  File "/home/carlos/Python-3.7.0/Lib/ensurepip/__init__.py", line 27, in _run_pip
    import pip._internal
  File "/tmp/tmpgcm2i4lh/pip-10.0.1-py2.py3-none-any.whl/pip/_internal/__init__.py", line 42, in <module>
  File "/tmp/tmpgcm2i4lh/pip-10.0.1-py2.py3-none-any.whl/pip/_internal/cmdoptions.py", line 16, in <module>
  File "/tmp/tmpgcm2i4lh/pip-10.0.1-py2.py3-none-any.whl/pip/_internal/index.py", line 25, in <module>
  File "/tmp/tmpgcm2i4lh/pip-10.0.1-py2.py3-none-any.whl/pip/_internal/download.py", line 39, in <module>
  File "/tmp/tmpgcm2i4lh/pip-10.0.1-py2.py3-none-any.whl/pip/_internal/utils/glibc.py", line 3, in <module>
  File "/home/carlos/Python-3.7.0/Lib/ctypes/__init__.py", line 7, in <module>
    from _ctypes import Union, Structure, Array
ModuleNotFoundError: No module named '_ctypes'
```

## 最后发现：3.7版本需要一个新的包libffi-devel，安装此包之后再次进行编译安装即可
```
yum install libffi-devel -y
```



六、创建软链接

```
ln -s /usr/local/python3/bin/python3 /usr/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
```
七、测试

命令行中输入python3测试

```
[root@ecs-7b5c-0005 ~]# python3
Python 3.6.5 (default, Apr  6 2018, 20:06:09) 
[GCC 4.8.5 20150623 (Red Hat 4.8.5-11)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import this

The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!

>>> 
```

八、创建虚拟环境


```
python3 -m venv py3env
```
测试：

```
[root@ecs-7b5c-0005 ~]# source py3env/bin/activate
(py3env) [root@ecs-7b5c-0005 ~]# 

```



# 好了，大功告成！