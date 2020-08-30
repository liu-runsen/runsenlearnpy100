
@Author：Runsen
@Date：2019/03/19




@[TOC]

# 什么是redis
Redis是一个开源的使用ANSI C语言编写、支持网络、可基于内存亦可持久化的日志型、Key-Value数据库，并提供多种语言的API。从2010年3月15日起，Redis的开发工作由VMware主持。从2013年5月开始，Redis的开发由Pivotal赞助。

Redis特性
- Redis支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。
- Redis不仅仅支持简单的key-value类型的数据，同时还把value分为list，set，zset，hash等数据结构存储。
- 因为Redis交换数据快，所以在服务器中常用来存储一些需要频繁调取的数据，提高效率。







# redis安装




检查是否安装gcc环境

```css
[root@VM_0_16_centos ~]# rpm -qa|grep gcc*
//无则安装。
[root@VM_0_16_centos ~]# yum install gcc-c++
```

创建目录，下载源码（通过华为镜像），解压源码

```css
[root@VM_0_16_centos redis]# mkdir /usr/lib/redis
[root@VM_0_16_centos redis]# cd /usr/lib/redis/
[root@VM_0_16_centos redis]# wget https://mirrors.huaweicloud.com/redis/redis-5.0.5.tar.gz
[root@VM_0_16_centos redis]# tar -zxvf redis-5.0.5.tar.gz 
```

进入文件夹，编译

```css
[root@VM_0_16_centos redis]# cd ./redis-5.0.5/
[root@VM_0_16_centos redis-5.0.5]# make
```

编译成功


安装，并检查是否安装了服务


```css
[root@VM_0_16_centos redis-5.0.5]# make PREFIX=/usr/local/redis install
//查看是否有此服务
[root@VM_0_16_centos bin]# ls /usr/local/redis/bin
redis-benchmark  redis-check-aof  redis-check-rdb  redis-cli  redis-sentinel  redis-server
把解压目录下配置文件复制到安装路径下

[root@VM_0_16_centos usr]# cp /usr/lib/redis/redis-5.0.5/redis.conf  /usr/local/redis/
由于前端启动模式启动后不可以随意关闭（进程断开），所以需要配置后端模式启动

```

修改后端启动（即守护进程开启），取消ip绑定


```css
[root@VM_0_16_centos ~]# vim /usr/local/redis/redis.conf
注释掉bind 127.0.0.1
#bind 127.0.0.1
更改protected-mode yes为
protected-mode no

更改daemonize no为
daemonize yes
```

设置密码
requirepass 要很长的密码

启动，并指定配置文件

```css

[root@VM_0_16_centos ~]# cd /usr/local/redis/

[root@VM_0_16_centos redis]# ./bin/redis-server ./redis.conf

1675:C 15 Sep 2019 22:50:52.157 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo

1675:C 15 Sep 2019 22:50:52.157 # Redis version=5.0.5, bits=64, commit=00000000, modified=0, pid=1675, just started
1675:C 15 Sep 2019 22:50:52.157 # Configuration loaded
通过端口（6379）查看服务是否启动
[root@VM_0_16_centos redis]# ps -ef|grep redis
root     1676     1  0 22:50 ?        00:00:00 ./bin/redis-server *:6379
root      1900  1219  0 22:52 pts/6    00:00:00 grep –color=auto redis
本地客户端连接和redis服务关闭
[root@VM_0_16_centos redis]# ./bin/redis-cli
127.0.0.1:6379> eixt
[root@VM_0_16_centos redis]# ./bin/redis-cli shutdown
通过外部（ip）连接,(需要开放云服务器相应端口)
[root@VM_0_16_centos redis]# ./bin/redis-cli -h 49.ip.ip.2 -p 6379 -a 密码
Warning: Using a password with ‘-a’ or ‘-u’ option on the command line interface may not be safe.
49.ip.ip.2:6379> 
```








# Redis数据模型
 

Redis支持五种数据类型：string（字符串），hash（哈希），list（列表），set（集合）及zset(sorted set：有序集合)。

1. String   ------>  字符串
2. Hash     ------>  哈希
3. List        ------>  列表
4. set         ------>  集合
5. Zset       ------>  有序集合


![](https://img-blog.csdnimg.cn/20190319160041710.png)




## Redis基本使用

![](https://img-blog.csdnimg.cn/20190319160059375.png)
- 连接redis：`redis-cli`

- 退出：`exit`
- 操作服务端：`service redis start/stop/restart`
- 切换数据库：select n

![](https://img-blog.csdnimg.cn/2019031916011549.png)

# Redis五大数据类型使用
## 全局key操作
对5 个数据类型都使用的命令
```shell
查看所有的key：keys *
删除键值对：del key
改名：rename  key  new_key
设置过期时间：expire key seconds
```

## String类型

strings是redis最基本的数据类型，一个key对应一个value
```shell
设置数据：set  key  value
查看数据：get  key
追加数据：append  key  value
删除数据：del key;
```

## List类型

```shell
添加数据：rpush key value [value…]
lpush key value [value…]     头部添加数据

查看数据：lrange key start stop
lindex key index      查看某个数据 

修改数据：lset key index value
删除数据：rpop key
lpop key 头部删除数据 
```
## Hash类型
```shell
添加数据：hset key field value 
查看域值：hget key field
hgetall key  查看所有的field和value
查看所有的value：hvals key
查看所有的field：hkeys key
```
## Set类型

```shell
添加数据：sadd key member [member …]
查看数据：smembers key
随机删除：spop key
指定删除：srem key member [member …]
```

## Sorted Set类型

```shell
添加数据： zadd key score member [score2 member2 …] 
查看数据： zrange key start stop 
zrangebyscore key min max 通过scores值查看
删除数据：zrem key member [member …]
通过索引删除多个数据：zremrangebyrank key min max
zremrangebyscore key min max  -- 通过scores值删除
```



**flushall 删除所有数据**


