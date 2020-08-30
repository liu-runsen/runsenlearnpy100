@Author：Runsen
@Date：2020/5/27

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。



这次内容是总结极客时间的Linux课程的知识点。耗时一天




@[TOC]



# 基础命令

Linux系统的命令通常都是如下所示的格式：

```Shell
命令名称 [命名参数] [命令对象]
```
## 获取登录信息
获取登录信息 - **w** / **who** / **last**/ **lastb**。

 ```Shell
maoli@ubuntu:~$ w
 08:07:38 up 2 min,  1 user,  load average: 0.83, 0.64, 0.27
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
maoli    tty7     :0               08:06    2:38   2.29s  0.31s /sbin/upstart -
maoli@ubuntu:~$ who
maoli    tty7         2020-05-28 08:06 (:0)
maoli@ubuntu:~$ last
maoli    tty7         :0               Thu May 28 08:06    gone - no logout
reboot   system boot  4.15.0-99-generi Thu May 28 08:04   still running
maoli    tty7         :0               Fri May  1 15:20 - down   (01:26)
reboot   system boot  4.15.0-99-generi Fri May  1 15:20 - 16:47  (01:26)
maoli    tty7         :0               Fri May  1 10:12 - crash  (05:08)
wtmp begins Fri May  1 10:12:22 2020
maoli@ubuntu:~$ sudo lastb
[sudo] maoli 的密码： 

btmp begins Fri May  1 15:20:29 2020

 ```



## 查看自己使用的Shell
查看自己使用的Shell - **ps**。

 Shell也被称为“壳”或“壳程序”，它是用户与操作系统内核交流的翻译官，简单的说就是人与计算机交互的界面和接口。目前很多Linux系统默认的Shell都是bash（<u>B</u>ourne <u>A</u>gain <u>SH</u>ell），因为它可以使用tab键进行命令和路径补全、可以保存历史命令、可以方便的配置环境变量以及执行批处理操作。

 ```Shell
maoli@ubuntu:~$ ps
   PID TTY          TIME CMD
  3621 pts/1    00:00:00 bash
  5082 pts/1    00:00:00 ps

 ```
## 查看命令的说明和位置 
 查看命令的说明和位置 - **whatis** / **which** / **whereis**。

 ```Shell
maoli@ubuntu:~$ whatis ps
ps (1)               - report a snapshot of the current processes.
maoli@ubuntu:~$ whatis python
python (1)           - an interpreted, interactive, object-oriented programmi...
maoli@ubuntu:~$ whereis ps
ps: /bin/ps /usr/share/man/man1/ps.1.gz
maoli@ubuntu:~$ whereis python
python: /usr/bin/python3.5m-config /usr/bin/python /usr/bin/python3.5 /usr/bin/python3.5m /usr/bin/python2.7 /usr/bin/python3.5-config /usr/lib/python3.5 /usr/lib/python2.7 /etc/python /etc/python3.5 /etc/python2.7 /usr/local/lib/python3.5 /usr/local/lib/python2.7 /usr/include/python3.5 /usr/include/python3.5m /usr/share/python /usr/share/man/man1/python.1.gz
maoli@ubuntu:~$ which ps
/bin/ps
maoli@ubuntu:~$ which python
/usr/bin/python
 ```
## 清除屏幕上显示的内容
清除屏幕上显示的内容 - **clear**。


## 查看帮助文档

查看帮助文档 - **man** / **info** / **help** / **apropos**。

 ```Shell
maoli@ubuntu:~$ ps --help

Usage:
 ps [options]

 Try 'ps --help <simple|list|output|threads|misc|all>'
  or 'ps --help <s|l|o|t|m|a>'
 for additional help text.

For more details see ps(1).
maoli@ubuntu:~$ man ps

 PS(1)                                User Commands                                PS(1)
 NAME
        ps - report a snapshot of the current processes.
 SYNOPSIS
        ps [options]
 DESCRIPTION
 ...
 ```
## 查看系统和主机名
 查看系统和主机名 - **uname** / **hostname**。

 ```Shell
maoli@ubuntu:~$ uname
Linux
maoli@ubuntu:~$ hostname
ubuntu
 ```


##  时间和日期

 时间和日期 - **date** / **cal**。

 ```Shell
maoli@ubuntu:~$ date
2020年 05月 28日 星期四 08:13:25 CST
maoli@ubuntu:~$ cal
      五月 2020         
日 一 二 三 四 五 六  
                1  2  
 3  4  5  6  7  8  9  
10 11 12 13 14 15 16  
17 18 19 20 21 22 23  
24 25 26 27 28 29 30  
31                    
maoli@ubuntu:~$ cal 5 2020
      五月 2020         
日 一 二 三 四 五 六  
                1  2  
 3  4  5  6  7  8  9  
10 11 12 13 14 15 16  
17 18 19 20 21 22 23  
24 25 26 27 28 29 30  
31        
 ```

## 重启和关机
8. 重启和关机 - **reboot** / **shutdown**。

 ```Shell
maoli@ubuntu:~$  shutdown -h +5   #五分钟关机
Shutdown scheduled for 四 2020-05-28 08:19:24 CST, use 'shutdown -c' to cancel. [root ~]# 
 maoli@ubuntu:~$ shutdown -c
maoli@ubuntu:~$ shutdown -r 12:00
Shutdown scheduled for 四 2020-05-28 12:00:00 CST, use 'shutdown -c' to cancel
 maoli@ubuntu:~$ shutdown -c
 ```

 说明：在执行`shutdown`命令时会向登录系统的用户发出警告，可以在命令后面跟上警告消息来替换默认的警告消息，也可以在`-h`参数后通过`now`来表示立刻关机。



## 退出登录
退出登录 -  **exit** / **logout**。


## 查看历史命令
查看历史命令 - **history**。

```Shell
maoli@ubuntu:~$ history
...
  625  date
  626  cal
  627  cal 5 2020
  628  shutdown -c
  629  shutdown -r 12:00
  630  shutdown -c
  631  history

maoli@ubuntu:~$ !631  
```


说明：查看到历史命令之后，可以用`!历史命令编号`来重新执行该命令；通过`history -c`可以清除历史命令。

# 实用程序

## 文件和文件夹操作


### 创建/删除空目录
创建/删除空目录 - **mkdir** / **rmdir**。

 ```Shell
 [root ~]# mkdir runsen
 [root ~]# mkdir -p abc/runsen
 [root ~]# rmdir runsen
 ```


### 创建/删除文件
创建/删除文件 - **touch** / **rm**。

 ```Shell
maoli@ubuntu:~$ touch readme.txt
maoli@ubuntu:~$  rm readme.txt 
 rm: remove regular empty file ‘readme.txt ’? y
 [root ~]# rm -rf xyz
 ```

 - `touch`命令用于创建空白文件或修改文件时间。在Linux系统中一个文件有三种时间：
   - 更改内容的时间 - mtime。
   - 更改权限的时间 - ctime。
   - 最后访问时间 - atime。
 - `rm`的几个重要参数：
   - `-i`：交互式删除，每个删除项都会进行询问。
   - `-r`：删除目录并递归的删除目录中的文件和目录。
   - `-f`：强制删除，忽略不存在的文件，没有任何提示。


### 切换和查看当前工作目录
3. 切换和查看当前工作目录 - **cd** / **pwd**。

 说明：`cd`命令后面可以跟相对路径（以当前路径作为参照）或绝对路径（以`/`开头）来切换到指定的目录，也可以用`cd ..`来返回上一级目录。返回到上上一级目录应该给` cd ../../
`命令。


### 查看目录内容
 查看目录内容 - **ls**。

 - `-l`：以长格式查看文件和目录。
 - `-a`：显示以点开头的文件和目录（隐藏文件）。
 - `-R`：遇到目录要进行递归展开（继续列出目录下面的文件和目录）。
 - `-d`：只列出目录，不列出其他内容。
 - `-S` / `-t`：按大小/时间排序。


### 查看文件内容
查看文件内容 - **cat** / **tac** / **head** / **tail** / **more** / **less** / **rev** / **od**。

 ```Shell
 maoli@ubuntu:~$  wget https://www.csdn.net/
--2020-05-28 08:25:01--  https://www.csdn.net/
正在解析主机 www.csdn.net (www.csdn.net)... 47.95.164.112
正在连接 www.csdn.net (www.csdn.net)|47.95.164.112|:443... 已连接。
已发出 HTTP 请求，正在等待回应... 200 OK
长度： 未指定 [text/html]
正在保存至: “index.html”

index.html              [  <=>               ] 420.39K  1.53MB/s    in 0.3s    

2020-05-28 08:25:02 (1.53 MB/s) - “index.html” 已保存 [430482]
maoli@ubuntu:~$ cat index.html
<!DOCTYPE html>
 ...
maoli@ubuntu:~$ head -10 index.html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <meta name="referrer"content="always">
    <meta name="msvalidate.01" content="3189512127C34C46BC74BED5852D45E4" />
    <title>CSDN-专业IT技术社区</title>
maoli@ubuntu:~$ tail -2 index.html 
<script src="https://g.csdnimg.cn/side-toolbar/2.0/side-toolbar.js"></script>
</html>
maoli@ubuntu:~$ less index.html  #相当于cat
maoli@ubuntu:~$ cat -n index.html |more
 ...
 ```

 说明：上面用到了一个名为`wget`的命令，它是一个网络下载器程序，可以从指定的URL下载资源。


### 拷贝/移动文件 
拷贝/移动文件 - **cp** / **mv**。

 ```Shell
maoli@ubuntu:~$ mkdir backup
maoli@ubuntu:~$ cp index.html backup/
maoli@ubuntu:~$ cd backup/
maoli@ubuntu:~/backup$ ls
index.html
maoli@ubuntu:~/backup$ mv index.html csdn.html
maoli@ubuntu:~/backup$ ls
csdn.html
 ```


### 文件重命名
文件重命名 - **rename**。

### 查找文件和查找内容
查找文件和查找内容 - **find** / **grep**。

 ```Shell‘
maoli@ubuntu:~/backup$ find ./ -name "*.html"
./csdn.html
maoli@ubuntu:~/backup$ find / -name "*.html"
/usr/local/java/jdk-11.0.6/README.html
/usr/local/python3/lib/python3.6/idlelib/help.html
/usr/local/python3/lib/python3.6/test/sgml_input.html
/usr/local/python3/lib/python3.6/test/test_difflib_expect.html
...
maoli@ubuntu:~/backup$  find . -type f -size +2k
./csdn.html
maoli@ubuntu:~/backup$ find . -type f -name "*.swp" -delete
maoli@ubuntu:~/backup$ grep "<script>" csdn.html -n
3192:        <script>
maoli@ubuntu:~/backup$ grep -E \<\/?script.*\> csdn.html -n
12:    <script src='//g.csdnimg.cn/tingyun/1.8.3/www.js' type='text/javascript'></script>
18:    <script src="//csdnimg.cn/public/common/libs/jquery/jquery-1.9.1.min.js" type="text/javascript"></script>
19:    <script src="//g.csdnimg.cn/??login-box/1.0.7/login-box.js,login-box/1.0.7/login-auto.js" type="text/javascript"></script>
 ...
 ```

 说明：`grep`在搜索字符串时可以使用正则表达式，如果需要使用正则表达式可以用`grep -E`或者直接使用`egrep`。
### 创建链接和查看链接
创建链接和查看链接 - **ln** / **readlink**。

 ```Shell
maoli@ubuntu:~/backup$ ls -l csdn.html
-rw-rw-r-- 1 maoli maoli 430482 5月  28 08:30 csdn.html
maoli@ubuntu:~/backup$ ln /home/maoli/backup/csdn.html /home/maoli/csdn
maoli@ubuntu:~/backup$ ls -l csdn.html
-rw-rw-r-- 2 maoli maoli 430482 5月  28 08:30 csdn.html
 ```

说明：链接可以分为硬链接和软链接（符号链接）。硬链接可以认为是一个指向文件数据的指针，就像Python中对象的引用计数，每添加一个硬链接，文件的对应链接数就增加1，只有当文件的链接数为0时，文件所对应的存储空间才有可能被其他文件覆盖。我们平常删除文件时其实并没有删除硬盘上的数据，我们删除的只是一个指针，或者说是数据的一条使用记录，所以类似于“文件粉碎机”之类的软件在“粉碎”文件时除了删除文件指针，还会在文件对应的存储区域填入数据来保证文件无法再恢复。软链接类似于Windows系统下的快捷方式，当软链接链接的文件被删除时，软链接也就失效了。


### 压缩/解压缩和归档/解归档 
.压缩/解压缩和归档/解归档 - **gzip** / **gunzip** / **xz**。

```Shell
maoli@ubuntu:~$ ls
 redis-4.0.10.tar.tar.gz
maoli@ubuntu:~$ gunzip  redis-4.0.10.tar.tar.gz
maoli@ubuntu:~$ ls
 redis-4.0.10.tar.tar
```
### 归档和解归档
归档和解归档 - **tar**。

 ```Shell
 maoli@ubuntu:~$  tar -xvf redis-4.0.10.tar
 redis-4.0.10/
 redis-4.0.10/.gitignore
 redis-4.0.10/00-RELEASENOTES
 redis-4.0.10/BUGS
 redis-4.0.10/CONTRIBUTING
 redis-4.0.10/COPYING
 redis-4.0.10/INSTALL
 redis-4.0.10/MANIFESTO
 redis-4.0.10/Makefile
 redis-4.0.10/README.md
 redis-4.0.10/deps/
 redis-4.0.10/deps/Makefile
 redis-4.0.10/deps/README.md
 ...
 ```

 说明：归档（也称为创建归档）和解归档都使用`tar`命令，通常创建归档需要`-cvf`三个参数，其中`c`表示创建（create），`v`表示显示创建归档详情（verbose），`f`表示指定归档的文件（file）；解归档需要加上`-xvf`参数，其中`x`表示抽取（extract），其他两个参数跟创建归档相同。


### 将标准输入转成命令行参数
将标准输入转成命令行参数 - **xargs**。

 下面的命令会将查找当前路径下的html文件，然后通过`xargs`将这些文件作为参数传给`rm`命令，实现查找并删除文件的操作。

 ```Shell
maoli@ubuntu:~$   find . -type f -name "*.html" | xargs rm -f
 ```

 下面的命令将a.txt文件中的多行内容变成一行输出到b.txt文件中，其中`<`表示从a.txt中读取输入，`>`表示将命令的执行结果输出到b.txt中。

 ```Shell
maoli@ubuntu:~$ xargs < a.txt > b.txt
 ```

### 显示文件或目录
 显示文件或目录 - **basename** / **dirname**。
### 其他相关工具
 其他相关工具。 

 - **sort** - 对内容排序
 - **uniq** - 去掉相邻重复内容
 - **tr** - 替换指定内容为新内容
 - **cut** / **paste** - 剪切/黏贴内容
 - **split** - 拆分文件
 - **file** - 判断文件类型
 - **wc** - 统计文件行数、单词数、字节数
 - **iconv** - 编码转换

 ```Shell
maoli@ubuntu:~$ cat foo.txt
 grape
 apple
 pitaya
maoli@ubuntu:~$ cat bar.txt
 100
 200
 300
 400
maoli@ubuntu:~$ paste foo.txt bar.txt
 grape   100
 apple   200
 pitaya  300
         400
maoli@ubuntu:~$ paste foo.txt bar.txt > hello.txt
maoli@ubuntu:~$ cut -b 4-8 hello.txt
 pe      10
 le      20
 aya     3
 0
maoli@ubuntu:~$ cat hello.txt | tr '\t' ','
 grape,100
 apple,200
 pitaya,300
 ,400
maoli@ubuntu:~$ split -l 100 sohu.html hello
maoli@ubuntu:~$ wget https://www.baidu.com/img/bd_logo1.png
maoli@ubuntu:~$ file bd_logo1.png
 bd_logo1.png: PNG image data, 540 x 258, 8-bit colormap, non-interlaced
maoli@ubuntu:~$ wc index.html 
  3820  18696 430482 index.html
maoli@ubuntu wget http://www.qq.com -O qq.html
maoli@ubuntu iconv -f gb2312 -t utf-8 qq.html
 ```

## 管道和重定向
### 管道的使用
管道的使用 - **\|**。

 例子：查找当前目录下文件个数。

 ```Shell
maoli@ubuntu:~$ find ./ | wc -l
80801
 ```

 例子：列出当前路径下的文件和文件夹，给每一项加一个编号。

 ```Shell
maoli@ubuntu:~$  ls | cat -n
     1	abc
     2	backup
 ```

 例子：查找record.log中包含AAA，但不包含BBB的记录的总数

 ```Shell
maoli@ubuntu:~$ cat record.log | grep AAA | grep -v BBB | wc -l
 ```
### 输出重定向
输出重定向和错误重定向 - **\>** / **>>** / **2\>**。

 ```Shell
maoli@ubuntu:~$ cat readme.txt
 banana
 apple
 grape
 apple
 grape
 watermelon
 pear
 pitaya
maoli@ubuntu:~$ cat readme.txt | sort | uniq > result.txt
maoli@ubuntu:~$ cat result.txt
 apple
 banana
 grape
 pear
 pitaya
 watermelon
 ```
### 输入重定向
 输入重定向 - **\<**。

 ```Shell
maoli@ubuntu:~$ echo 'hello, world!' > hello.txt
maoli@ubuntu:~$ echo 'I will show you some code.' >> hello.txt
maoli@ubuntu:~$ cat hello.txt
hello, world!
I will show you some code.
 ```


### 多重定向
多重定向 - **tee**。

 下面的命令除了在终端显示命令`ls`的结果之外，还会追加输出到`ls.txt`文件中。

 ```Shell
maoli@ubuntu:~$  ls | tee -a ls.txt
maoli@ubuntu:~$ cat ls.txt 
abc
backup
 ```

### 别名

 **alias**创建别名

 ```Shell
maoli@ubuntu:~$ alias ll='ls -l'
maoli@ubuntu:~$ alias frm='rm -rf'
maoli@ubuntu:~$ ll
量 144920
drwxrwxr-x  3 maoli maoli      4096 5月  28 08:20 abc
 maoli@ubuntu:~$frm abc
 ```

 **unalias**删除别名

 ```Shell
maoli@ubuntu:~$ funalias frm
maoli@ubuntu:~$ frm index.html
 -bash: frm: command not found
 ```

## 文本处理
### 字符流编辑器
字符流编辑器 - **sed**。

 sed是操作、过滤和转换文本内容的工具。假设有一个名为fruit.txt的文件，内容如下所示。

 ```Shell
maoli@ubuntu:~$ cat -n fruit.txt 
      1  banana
      2  grape
      3  apple
      4  watermelon
      5  orange
 ```

 接下来，我们在第2行后面添加一个pitaya。

 ```Shell
maoli@ubuntu:~$  sed '2a pitaya' fruit.txt 
 banana
 grape
 pitaya
 apple
 watermelon
 orange
 ```


 在第2行前面插入一个waxberry。

 ```Shell
maoli@ubuntu:~$ sed '2i waxberry' fruit.txt
 banana
 waxberry
 grape
 apple
 watermelon
 orange
 ```

 删除第3行。

 ```Shell
maoli@ubuntu:~$ sed '3d' fruit.txt
 banana
 grape
 watermelon
 orange
 ```

 删除第2行到第4行。

 ```Shell
maoli@ubuntu:~$ sed '2,4d' fruit.txt
 banana
 orange
 ```

 将文本中的字符a替换为@。

 ```Shell
maoli@ubuntu:~$ sed 's#a#@#' fruit.txt 
 b@nana
 gr@pe
 @pple
 w@termelon
 or@nge
 ```

 将文本中的字符a替换为@，使用全局模式。

 ```Shell
maoli@ubuntu:~$ sed 's#a#@#g' fruit.txt 
 b@n@n@
 gr@pe
 @pple
 w@termelon
 or@nge
 ```
### 模式匹配和处理语言
 模式匹配和处理语言 - **awk**。

 awk是一种编程语言，也是Linux系统中处理文本最为强大的工具，它的作者之一和现在的维护者就是之前提到过的Brian Kernighan（ken和dmr最亲密的伙伴）。通过该命令可以从文本中提取出指定的列、用正则表达式从文本中取出我们想要的内容、显示指定的行以及进行统计和运算，总之它非常强大。

 假设有一个名为fruit2.txt的文件，内容如下所示。

 ```Shell
\maoli@ubuntu:~$ cat fruit2.txt 
 1       banana      120
 2       grape       500
 3       apple       1230
 4       watermelon  80
 5       orange      400
 ```

 显示文件的第3行。

 ```Shell
maoli@ubuntu:~$ awk 'NR==3' fruit2.txt 
 3       apple       1230
 ```

 显示文件的第2列。

 ```Shell
maoli@ubuntu:~$awk '{print $2}' fruit2.txt 
 banana
 grape
 apple
 watermelon
 orange
 ```

 显示文件的最后一列。

 ```Shell
maoli@ubuntu:~$ awk '{print $NF}' fruit2.txt 
 120
 500
 1230
 80
 400
 ```

 输出末尾数字大于等于300的行。

 ```Shell
maoli@ubuntu:~$ awk '{if($3 >= 300) {print $0}}' fruit2.txt 
 2       grape       500
 3       apple       1230
 5       orange      400
 ```


# 用户管理
## 创建和删除用户
创建和删除用户 - **useradd** / **userdel**。需要用root账号创建

 ```Shell
 maoli@ubuntu:~$ su root
密码： 
root@ubuntu:/home/maoli# useradd Runsen
root@ubuntu:/home/maoli#  userdel Runsen
 ```

 - `-d` - 创建用户时为用户指定用户主目录
 - `-g` - 创建用户时指定用户所属的用户组


##  创建和删除用户组
创建和删除用户组 - **groupadd** / **groupdel**。

 用户组主要是为了方便对一个组里面所有用户的管理。


## 修改密码
修改密码 - **passwd**。

 ```Shell
root@ubuntu:/home/maoli# passwd maoli
 New password: 
 Retype new password: 
 passwd: all authentication tokens updated successfully.
 ```

如果使用`passwd`命令时没有指定命令作用的对象，则表示要修改当前用户的密码。如果想批量修改用户密码，可以使用`chpasswd`命令。

 - `-l` / `-u` - 锁定/解锁用户。
 - `-d` - 清除用户密码。
 - `-e` - 设置密码立即过期，用户登录时会强制要求修改密码。
 - `-i` - 设置密码过期多少天以后禁用该用户。


## 查看和修改密码有效期
 查看和修改密码有效期 - **chage**。

 设置maoli用户100天后必须修改密码，过期前15天通知该用户，过期后15天禁用该用户。

 ```Shell
 root@ubuntu:/home/maoli# chage -M 100 -W 15 -I 15 maoli
 ```

5. 切换用户 - **su**。

 ```Shell
root@ubuntu:/home/maoli#  su maoli
 maoli@ubuntu:~$ 
 ```

##  以管理员身份执行命令 
以管理员身份执行命令 - **sudo**。

 ```Shell
 maoli@ubuntu:~$  ls /root
 ls: cannot open directory /root: Permission denied
 maoli@ubuntu:~$ 
 sudo ls /root
 [sudo] password for maoli:
 ```

**说明**：如果希望用户能够以管理员身份执行命令，用户必须要出现在sudoers名单中，sudoers文件在 `/etc`目录下，如果希望直接编辑该文件也可以使用下面的命令。

## 编辑sudoers文件
编辑sudoers文件 - **visudo**。

 这里使用的编辑器是vim，关于vim的知识在前面有讲解。

[五十二、ViM的使用](https://maoli.blog.csdn.net/article/details/105285497)
该文件的部分内容如下所示：

 ```
 ## Allow root to run any commands anywhere 
 root    ALL=(ALL)   ALL
 
 ## Allows members of the 'sys' group to run networking, software, 
 ## service management apps and more.
 # %sys ALL = NETWORKING, SOFTWARE, SERVICES, STORAGE, DELEGATING, PROCESSES, LOCATE, DRIVERS
 ## Allows people in group wheel to run all commands
 %wheel  ALL=(ALL)   ALL
 
 ## Same thing without a password
 # %wheel    ALL=(ALL)   NOPASSWD: ALL
 
 ## Allows members of the users group to mount and unmount the
 ## cdrom as root
 # %users  ALL=/sbin/mount /mnt/cdrom, /sbin/umount /mnt/cdrom
 
 ## Allows members of the users group to shutdown this system
 # %users  localhost=/sbin/shutdown -h now
 ```


## 显示用户与用户组的信息 
显示用户与用户组的信息 - **id**。

```css
root@ubuntu:/home/maoli# id
uid=0(root) gid=0(root) 组=0(root)
```
## 给其他用户发消息
给其他用户发消息 -**write** / **wall**。

 发送方：

 ```Shell
 root@ubuntu# write maoli
Hello Maoli
EOF
 ```
键入EOF表示信息结束，用Crtl+D组合键发送信息。输入内容会出现在用户的屏幕上，同时通信中止。
 接收方：

 ```Shell
 maoli@ubuntu:~$  
 Message from root on pts/0 at 9:41 ...
 Hello Maoli
 EOF
 ```

10. 查看/设置是否接收其他用户发送的消息 - **mesg**。

 ```Shell
 maoli@ubuntu:~$   mesg
 is y 
 maoli@ubuntu:~$   mesg n
 maoli@ubuntu:~$ mesg
 is n
 ```

如果想要发送一条信息给系统中所有用户，可以使用wall命令，wall表示：write all。输入wall，然后编辑信息，如果shell支持可以使用中文。然后使用Crtl+D组合键发送信息。这样系统所有登录用户的桌面会收到信息。如 果在网络上，可以使用rwall命令把信息发送到局域网上所有的用户。

# 文件系统

## 文件和路径

1. 命名规则：文件名的最大长度与文件系统类型有关，一般情况下，文件名不应该超过255个字符，虽然绝大多数的字符都可以用于文件名，但是最好使用英文大小写字母、数字、下划线、点这样的符号。文件名中虽然可以使用空格，但应该尽可能避免使用空格，否则在输入文件名时需要用将文件名放在双引号中或者通过`\`对空格进行转义。
2. 扩展名：在Linux系统下文件的扩展名是可选的，但是使用扩展名有助于对文件内容的理解。有些应用程序要通过扩展名来识别文件，但是更多的应用程序并不依赖文件的扩展名，就像`file`命令在识别文件时并不是依据扩展名来判定文件的类型。
3. 隐藏文件：以点开头的文件在Linux系统中是隐藏文件（不可见文件）。

## 目录结构

1. /bin - 基本命令的二进制文件。
2. /boot - 引导加载程序的静态文件。
3. /dev - 设备文件。
4. **/etc** - 配置文件。
5. /home - 普通用户主目录的父目录。
6. /lib - 共享库文件。
7. /lib64 - 共享64位库文件。
8. /lost+found - 存放未链接文件。
9. /media - 自动识别设备的挂载目录。
10. /mnt - 临时挂载文件系统的挂载点。
11. /opt - 可选插件软件包安装位置。
12. /proc -  内核和进程信息。
13. **/root** - 超级管理员用户主目录。
14. /run - 存放系统运行时需要的东西。
15. /sbin - 超级用户的二进制文件。
16. /sys - 设备的伪文件系统。
17. /tmp - 临时文件夹。
18. **/usr** - 用户应用目录。
19. /var - 变量数据目录。

## 访问权限
### 改变文件模式
1. **chmod** - 改变文件模式比特。

 ```Shell
maoli@ubuntu:~/backup$ ls -l
总用量 424
-rw-rw-r-- 2 maoli maoli 430482 5月  28 08:30 csdn.html
maoli@ubuntu:~/backup$ chmod g+w,o+w csdn.html
maoli@ubuntu:~/backup$ ls -l
总用量 424
-rw-rw-rw- 2 maoli maoli 430482 5月  28 08:30 csdn.html
maoli@ubuntu:~/backup$ chmod 644 csdn.html 
maoli@ubuntu:~/backup$ ls -l
总用量 424
-rw-r--r-- 2 maoli maoli 430482 5月  28 08:30 csdn.html
 ```

  说明：通过上面的例子可以看出，用`chmod`改变文件模式比特有两种方式：一种是字符设定法，另一种是数字设定法。除了`chmod`之外，可以通过`umask`来设定哪些权限将在新文件的默认权限中被删除。
![](https://img-blog.csdnimg.cn/20200528094237104.png)
### 改变文件所有者
2. **chown** - 改变文件所有者。

 ```Shell
 maoli@ubuntu:~/backup$ ls -l
总用量 424
-rw-r--r-- 2 maoli maoli 430482 5月  28 08:30 csdn.html
maoli@ubuntu:~/backup$ sudo chown root csdn.html
[sudo] maoli 的密码： 
maoli@ubuntu:~/backup$ ls -l
总用量 424
-rw-r--r-- 2 root maoli 430482 5月  28 08:30 csdn.html
 ```

3. **chgrp** - 改变用户组。
