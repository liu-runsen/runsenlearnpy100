@Author：Runsen
@Date：2020/5/27

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。




@[TOC]


# 磁盘管理

Linux磁盘管理常用三个命令为df、du和fdisk。


## 列出文件系统的磁盘使用状况
 列出文件系统的磁盘使用状况 - **df**。

```css
文件系统        容量  已用  可用 已用% 挂载点
udev            1.9G     0  1.9G    0% /dev
tmpfs           393M  6.3M  386M    2% /run
/dev/sda1        19G   13G  5.5G   69% /
tmpfs           2.0G  300K  2.0G    1% /dev/shm
tmpfs           5.0M  4.0K  5.0M    1% /run/lock
tmpfs           2.0G     0  2.0G    0% /sys/fs/cgroup
tmpfs           393M  4.0K  393M    1% /run/user/108
tmpfs           393M   60K  393M    1% /run/user/1000
/dev/sr0        1.6G  1.6G     0  100% /media/maoli/Ubuntu 16.04.6 LTS amd64
```
## 磁盘分区表操作
磁盘分区表操作 - **fdisk**。

```Shell
maoli@ubuntu:~$ sudo fdisk -l
[sudo] maoli 的密码： 

Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdc219461

设备       启动    Start   末尾   扇区  Size Id 类型
/dev/sda1  *        2048 39942143 39940096   19G 83 Linux
/dev/sda2       39944190 41940991  1996802  975M  5 扩展
/dev/sda5       39944192 41940991  1996800  975M 82 Linux 交换 / Solaris

```





## 磁盘分区工具

. 磁盘分区工具 - **parted**。


## 格式化文件系统
格式化文件系统 - **mkfs**。

```Shell
maoli@ubuntu:~$ mkfs -t ext4 -v /dev/sdb
```

- `-t` - 指定文件系统的类型。
- `-c` - 创建文件系统时检查磁盘损坏情况。
- `-v` - 显示详细信息。

##  文件系统检查


文件系统检查 - **fsck**。


## 转换或拷贝文件
转换或拷贝文件 - **dd**。


## 挂载/卸载
挂载/卸载 - **mount** / **umount**。

##  创建/激活/关闭交换分区
创建/激活/关闭交换分区 - **mkswap** / **swapon** / **swapoff**。



参考[菜鸟教程](https://www.runoob.com/linux/linux-filesystem.html)




# Shell

Shell是一个连接用户和操作系统的应用程序，它提供了人机交互的界面（接口），用户通过这个界面访问操作系统内核的服务。Shell脚本是一种为Shell编写的脚本程序，我们可以通过Shell脚本来进行系统管理，同时也可以通过它进行文件操作。


互联网上有大量关于Shell脚本的相关知识，我不打算再此对Shell脚本做一个全面系统的讲解，我们通过下面的代码来感性的认识下Shell脚本就行了。

## 新建Shell脚本

打开文本编辑器(可以使用 vi/vim 命令来创建文件)，新建一个文件 test.sh，扩展名为 sh（sh代表shell）。

```css
maoli@ubuntu:~$ vim test.sh

#!/bin/bash
echo "Hello World !"
```
输入一个`echo "Hello World !"`，这个语法和php很相似。运行一个sh需用 `chmod +x `脚本具有执行权限


```css
maoli@ubuntu:~$ chmod +x ./test.sh
maoli@ubuntu:~$ ./test.sh 
Hello World !

```

## 变量
变量名不加美元符号（\$，PHP语言中变量需要）。比如在shell中 定义变量`name = Runsen`，而在php就是`$name = Runsen`


使用一个定义过的变量，只要在变量名前面加美元符号即可，如：`$name`或者`${name}`。变量名外面的花括号是可选的，加不加都行。



变量支持字符串类型，浮点等类型，常见有这 3 个前缀：
- unset：删除变量
-  readonly：标记只读变量
- export：指定全局变量

```css
#!/bin/bash 

# 定义普通变量，没有特殊字符或者空格，可以不用引号
CITY=Dongguan

# 定义全局变量
export NAME=Runsen

# 定义只读变量
readonly AGE=20

# 打印变量的值
echo $CITY
echo $NAME
echo $AGE

# 删除 CITY 变量
unset CITY
# 不会输出 Dongguan
echo $CITY
```



## 预定义变量


预定义变量常用来获取命令行的输入，有下面这些：

```css
$0 ：脚本文件名
$1-9 ：第 1-9 个命令行参数名
$# ：命令行参数个数
$@ ：所有命令行参数
$* ：所有命令行参数
$? ：前一个命令的退出状态，可用于获取函数返回值
$$ ：执行的进程 ID
```

一个例子：

```css
#!/bin/bash 
echo "\$0 = $0"
echo "\$1 = $1"
echo "\$2 = $2"
echo "\$# = $#"
echo "\$@ = $@"
echo "\$* = $*"
echo "\$$ = $$"
echo "\$? = $?"
```
执行./hello.sh 1 2 3 4 5 的结果：


```css
# 程序名
$0 = ./hello.sh
# 第一个参数
$1 = 1
# 第二个参数
$2 = 2
# 一共有 5 个参数
$# = 5
# 打印出所有参数
$@ = 1 2 3 4 5
# 打印出所有参数
$* = 1 2 3 4 5
# 进程 ID
$$ = 9450
# 之前没有执行其他命令或者函数
$? = 0
```

## 语句

### if
**sh的流程控制不可为空**

```css
#!/bin/bash 
read VAR
# 下面这两种判断方法都可以，使用 [] 注意左右加空格
#if test $VAR -eq 10
if [ $VART -eq 10 ]
then
    echo "true"
else
    echo "false"
fi
```


read 的方法就python中的input，写成一行（适用于终端命令提示符）：

```css
if [ $VART -eq 10 ]; then echo "true"; else echo "false";fi
```




##  for 循环


 for 循环和Python没有什么区别，挺简单的

```css
# 普通 for 循环
for ((i = 1; i <= 3; i++))
do
    echo $i
done

# loop 依次代表每个元素 
for loop in 1 2 3 4 5
do
    echo "The value is: $loop"
done

# VAR 依次代表每个元素 ，{}产生连续数字
for VAR in {1..3}
do
    echo $VAR
done

#也可以写成一行，方便在命令行直接运行，注意空格和;号：
maoli@ubuntu:~$ for VAR in {1..3}; do  echo $VAR; done
1
2
3

```


## 打印


printf 命令模仿 C 程序库（library）里的 printf() 程序， 这里补充`-e `开启转义` \c `不换行，其他和Python一样。

```css
maoli@ubuntu:~$ echo "It is a test"
It is a test
maoli@ubuntu:~$ echo -e "OK! \n"
OK! 

maoli@ubuntu:~$ printf "%-10s %-8s %-4s\n" 姓名 性别 体重kg  
姓名     性别   体重kg
maoli@ubuntu:~$ printf "%-10s %-8s %-4.2f\n" Runsen 男 65
Runsen     男      65.00
```

## test 
Shell中的 test 命令用于检查某个条件是否成立，它可以进行数值、字符和文件三个方面的测试。



参数|	说明
--|--
-eq	|等于则为真
-ne	|不等于则为真
-gt	|大于则为真
-ge	|大于等于则为真
-lt	|小于则为真
-le	|小于等于则为真

比如下判断两个字符串是否相同t
```css
num1="Runsen"
num2="Runsen"
if test $num1 = $num2
then
    echo '两个字符串相等!'
else
    echo '两个字符串不相等!'
fi
两个字符串相等!
```



# Shell 函数
shell中函数的定义格式如下：


```css
#!/bin/bash


demoFun(){
    echo "这是我的第一个 shell 函数!"
}
echo "-----函数开始执行-----"
demoFun
echo "-----函数执行完毕-----"

-----函数开始执行-----
这是我的第一个 shell 函数!
-----函数执行完毕-----
```

#  shell实例


## 求和

例子1：输入两个整数m和n，计算从m到n的整数求和的结果。


```css
#!/usr/bin/bash
printf 'm = '
read m
printf 'n = '
read n
a=$m
sum=0
while [ $a -le $n ]
do
    sum=$[ sum + a ]
    a=$[ a + 1 ]
done
echo '结果: '$sum
```

## 创建文件夹和文件
例子2：自动创建文件夹和指定数量的文件。


```css
#!/usr/bin/bash
printf '输入文件名: '
read file
printf '输入文件数量(<1000): '
read num
if [ $num -ge 1000 ]
then
    echo '文件数量不能超过1000'
else
    if [ -e $dir -a -d $dir ]
    then
        rm -rf $dir
    else
        if [ -e $dir -a -f $dir ]
        then
            rm -f $dir
        fi
    fi
    mkdir -p $dir
    index=1
    while [ $index -le $num ]
    do
        if [ $index -lt 10 ]
        then
            pre='00'
        elif [ $index -lt 100 ]
        then
            pre='0'
        else
            pre=''
        fi
        touch $dir'/'$file'_'$pre$index
        index=$[ index + 1 ]
    done
fi
```

