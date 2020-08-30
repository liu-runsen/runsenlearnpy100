
@Author：Runsen
@Date：2020/04/03
![](https://img-blog.csdnimg.cn/20200527115119893.png)


作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。



@[TOC]

#  linux介绍


![](https://img-blog.csdnimg.cn/20190318121644669.png)

Linux是一套免费使用和自由传播的类Unix操作系统，是一个基于POSIX和UNIX的多用户、多任务、支持多线程和多CPU的操作系统。它能运行主要的UNIX工具软件、应用程序和网络协议。它支持32位和64位硬件。Linux继承了Unix以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。

# Linux系统发行版本

1. [Redhat](https://www.redhat.com/en)
2. [Ubuntu](https://www.ubuntu.com/)
3. [CentOS](https://www.centos.org/)
4. [Fedora](https://getfedora.org/)
5. [Debian](https://www.debian.org/)
6. [openSUSE](https://www.opensuse.org/)


#  Linux常用命令




基本必知 | 作用 | 示例
---|---|---
cd| 切换工作目录 | cd ~ 回到主目录 cd .. 回到上级路径 cd - 回到上次路径
pwd| 显示工作路径 | pwd
ls | 显示文件列表 | ls
mkdir | 创建文件夹 | mkdir test
rmdir | 删除文件夹 | rmdir test
cp | 复制 | cp a.txt b.txt
mv | 移动和重命名 | mv b.txt ../
cat | 查看文件内容 | cat a.txt
touch | 创建文件 | touch  c.txt
rm | 删除文件 | rm c.txt
help | 帮助 | help cd



Vim编辑py文件


# Vim 



![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9hM2MxNmEwZC1iN2E0LTQ1ZGItOTVkMy00NjA3ZGIwOGFjMTAucG5n?x-oss-process=image/format,png)


`VIM` （Unix及类Unix系统文本编辑器） 

`Vim` 是一个类似于Vi的著名的功能强大、高度可定制的文本编辑器，在Vi的基础上改进和增加了很多特性。 


重点


在Vim中，有命令模式，输入模式 和 末行模式三种模式。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9jMjZmZTJkMi02ZmQyLTQ1YTAtYTA1Ni1lMzk4ZDE3OTZkMzkucG5n?x-oss-process=image/format,png)



- 按 ESC 进入命令模式
- 输入 Shift + ； 进入末行模式
- 输入插入命令，如(i,a,o) 进入插入模式

`注意点 进入末行模式的前提一定是要命令模式，也就是输入完指令，必须先回到命令模式`

进入`vim   filename `

## 退出

+ :wq    末行模式，wq 保存退出
+ :q     末行模式，q 直接退出
- :q!    末行模式，q! 强制退出，不保存

## 移动光标

- gg    到文件第一行
- G      到文件最后一行   (Shift + g)
- ^      非空格行首
- 0       行首(数字0)
- $       行尾

	
## 输入模式

- i    从光标所在位置前面开始插入
- I    在当前行首插入
- a   从光标所在位置后面开始输入
- A   在当前行尾插入
- o   在光标所在行下方新增一行并进入输入模式
- O  在当前上面一行插入


- 进入输入模式后，在最后一行会出现--INSERT—的字



这些命令都是在命令模式下的
复制和粘贴(必须灵活使用)

- yy    复制整行内容
- 3yy  复制3行内容
- yw   复制当前光标到单词尾内容
- p      粘贴


## 删除

- dd  删除光标所在行
- dw  删除一个单词
- x     删除光标所在字符
- u    撤销上一次操作
- ctrl + r    撤销   u

## 块操作

  - v    块选择
  - ctrl + v   列块选择  
    
## 查找

- /    命令模式下输入：/   向前搜索
- ?    命令模式下输入：?   向后搜索
- n    向下查找
- N    向上查找


## 替换 末行模式

- :s/s1/s2 替换当前行第一个s1为s2
- :s/s1/s2/g 替换当前行中所有s1为s2
- :%s/s1/s2/g  替换文中所有s1为 s2


关键是要多练


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9lNzdmMDhhZS1mYWI4LTQ4MWQtYjNhNy1lNjJkOWNhMDFlYjEucG5n?x-oss-process=image/format,png)






