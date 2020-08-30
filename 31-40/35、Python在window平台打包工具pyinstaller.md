Java 一次编译到处运行，Python没有这么好本事，但是也有一个pyinstaller可以打包exe，在window平台下运行



@[TOC]



# pyinstaller

安装`pip install pyinstaller`

# 参数


|参数  |含 义 |
|--|--|
| -F | 只生成一个exe文件 |
| –distpath| 指定生成的exe存放的目录 |
| –workpath | 指定编译中临时文件存放的目录 |
|-i | 创建一个目录包含：exe文件、依赖文件|
| -F | 指定exe图标 |	
|-p	|指定exe依赖的包、模块
|-d	|编译为debug模式，获取运行中的日志信息
|-clean|	清理编译时临时文件
|-c	|使用控制台
|-w	|使用窗口
|-version-file	|添加exe版本信息

# 计算机小助手例子


在我桌面有demo8.py文件，psutil这个标准库是计算计算机的性能的。


```python
# -*- coding：utf-8 -*-
# time ：2019/3/28 22:44
# author: Runsen
print('欢迎您,我是您的计算机小助手')
import psutil as ps
import time
print('本机开机的时间是:{}'.format(time.strftime('%Y-%m-%d %H:%M:%S',time.localtime(ps.boot_time()))))
print("-------------------------")
print("CPU部分")
print("-------------------------")
print('本机物理CPU个数:{}个'.format(ps.cpu_count()))
print('本机逻辑CPU个数:{}个'.format(ps.cpu_count(logical=False)))
print("-------------------------")
print('内容部分')
print("-------------------------")
print('本机内存大小为:{}个字节'.format(ps.virtual_memory().total))
print('本机已用内存大小为:{}个字节'.format(ps.virtual_memory().used))
print('本机已用内存大小占比为:{}%'.format(ps.virtual_memory().percent))
input()
```

# 注意点：


一定要在代码最后面加上`input()`,这样打开exe不会一散而过，



![](https://img-blog.csdnimg.cn/20190328231100468.png)



cd 到代码的目录执行 `pyinstaller -F demo8.py`

这样就会生成日记等文件

![](https://img-blog.csdnimg.cn/20190328231232777.jpg)


我们找到exe

![](https://img-blog.csdnimg.cn/20190328231312320.jpg)

双击打开它，这样就显示出电脑的内存占用，说明下电脑的内存和你下载的东西无关，就是看你打开了多少网页和程序。


![](https://img-blog.csdnimg.cn/20190328231336607.jpg)

和jar包比起来就是给人家完爆的感觉。





