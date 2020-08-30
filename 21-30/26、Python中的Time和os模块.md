@Author: Runsen
@[TOC]

# 日期与时间管理的库
datetime 与time 



```python
import datetime 
t = datetime.time(1, 20, 1) 
# Lets show the different compoenets # datetime.time(hour,minute,second,microsecond) 
print(t) 
print('hour  :', t.hour) 
print('minute:', t.minute)
print('second:', t.second) 
print('microsecond:', t.microsecond) 
print('tzinfo:', t.tzinfo)
```

    01:20:01
    hour  : 1
    minute: 20
    second: 1
    microsecond: 0
    tzinfo: None
    


```python
import time 
time.time() #10位
```




    1557212908.1839943




```python
print('Earliest  :', datetime.time.min) 
print('Latest    :', datetime.time.max) 
print('Resolution:', datetime.time.resolution) 
```

    Earliest  : 00:00:00
    Latest    : 23:59:59.999999
    Resolution: 0:00:00.000001
    


```python
today = datetime.date.today()
print(today)
print('ctime:', today.ctime()) 
print('tuple:', today.timetuple()) 
print('ordinal:', today.toordinal())
print('Year:', today.year) 
print('Mon :', today.month)
print('Day :', today.day) 
```

    2019-05-07
    ctime: Tue May  7 00:00:00 2019
    tuple: time.struct_time(tm_year=2019, tm_mon=5, tm_mday=7, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=1, tm_yday=127, tm_isdst=-1)
    ordinal: 737186
    Year: 2019
    Mon : 5
    Day : 7
    


```python
print('Earliest  :', datetime.date.min) 
print('Latest    :', datetime.date.max)
print('Resolution:', datetime.date.resolution) 
```

    Earliest  : 0001-01-01
    Latest    : 9999-12-31
    Resolution: 1 day, 0:00:00
    


```python
d1 = datetime.date(2019, 5, 7)
print('d1:', d1) 
d2 = d1.replace(year=1990)
print('d2:', d2) 
```

    d1: 2019-05-07
    d2: 1990-05-07
    

# os 操作模块
OS模块简单的来说它是一个Python的系统编程的操作模块，可以处理文件和目录这些我们日常手动需要做的 操作。 可以查看OS模块的帮助文档：
 
import os #导入os模块  
help(os)   #查看os模块帮助文档，里面详细的模块相关函数和使用方法



# OS模块重要函数和变量:
- os.sep 更改操作系统中的路径分隔符。 
- os.getcwd()获取当前路径，这个在Python代码中比较 常用。 
- os.listdir() 列出当前目录下的所有文件和文件夹。 
- os.remove() 方法可以删除指定 的文件。 
- os.system() 方法用来运行shell命令。 
- os.chdir() 改变当前目录，到指定目录 中。

# OS模块函数作用详解
- os.system函数可以运行shello命令，Linux系统中就是终端模拟器中的命令。 也有一些函数可以执行外部 程序，包括execv，它会退出Python解释器，并且将控制权交给被执行的程序。
- os.sep变量主要用于系统路 径中的分隔符。 Windows系统通过是“\”，Linux类系统如Ubuntu的分隔符是“/”，而苹果Mac OS系统中 是“:”。

- os.sep 可以取代操作系统特定的路径分割符。
- os.name字符串指示你正在使用的平台。比如对于Windows，它是'nt'，而对于Linux/Unix用户，它 是'posix'。
- os.getcwd()函数得到当前工作目录，即当前Python脚本工作的目录路径。
- os.getenv()和os.putenv()函数分别用来读取和设置环境变量。
- os.listdir()返回指定目录下的所有文件和目录名。
- os.remove()函数用来删除一个文件。
- os.system()函数用来运行shell命令。
- os.linesep字符串给出当前平台使用的行终止符。例如，Windows使用'\r\n'，Linux使用'\n'而Mac使 用'\r'。
- os.path.split()函数返回一个路径的目录名和文件名。
- os.path.isfile()和os.path.isdir()函数分别检验给出的路径是一个文件还是目录。
- os.path.existe()函数用来检验给出的路径是否真地存在

- os.listdir(dirname)：列出dirname下的目录和文件
- os.getcwd()：获得当前工作目录
- os.curdir:返回但前目录（'.')
- os.chdir(dirname):改变工作目录到dirname
# os.path模块
- os.path.isdir(name):判断name是不是一个目录，name不是目录就返回false
- os.path.isfile(name):判断name是不是一个文件，不存在name也返回false
- os.path.exists(name):判断是否存在文件或目录name
- os.path.getsize(name):获得文件大小，如果name是目录返回0L
- os.path.abspath(name):获得绝对路径
- os.path.normpath(path):规范path字符串形式
- os.path.split(name):分割文件名与目录（事实上，如果你完全使用目录，它也会将最后一个目录作为文件 名而分离，同时它不会判断文件或目录是否存在）
- os.path.splitext():分离文件名与扩展名
- os.path.join(path,name):连接目录与文件名或目录
- os.path.basename(path):返回文件名
- os.path.dirname(path):返回文件路径

以上就是总结的Python os模块的一些比较重要的内容。

