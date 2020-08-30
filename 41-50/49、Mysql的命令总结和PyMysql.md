@Author：Runsen

@Date：2019/2/27




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。




@[TOC]




# 了解MySQL
MySQL是一个**关系型**数据库管理系统，由瑞典MySQL AB 公司开发，目前属于 Oracle 旗下产品。MySQL 是最流行的关系型数据库管理系统之一，在 WEB 应用方面，MySQL是最好的 RDBMS (Relational Database Management System，关系数据库管理系统) 应用软件。
MySQL是一种关系数据库管理系统，关系数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。
MySQL所使用的 SQL 语言是用于访问数据库的最常用标准化语言。MySQL 软件采用了双授权政策，分为社区版和商业版，由于其体积小、速度快、总体拥有成本低，尤其是开放源码这一特点，一般中小型网站的开发都选择 MySQL 作为网站数据库。


# MySql安装

## 安装和配置

下面（以CentOS Linux环境为例）。

Linux下有一个MySQL的分支版本，名为MariaDB，它由MySQL的一些原始开发者开发，有商业支持，旨在继续保持MySQL数据库在[GNU GPL](https://zh.wikipedia.org/wiki/GNU%E9%80%9A%E7%94%A8%E5%85%AC%E5%85%B1%E8%AE%B8%E5%8F%AF%E8%AF%81)下开源（因为大家担心MySQL被甲骨文收购后会不再开源）。如果决定要直接使用MariaDB作为MySQL的替代品，可以使用下面的命令进行安装。

   ```Shell
   yum install mariadb mariadb-server
   ```

  如果要安装官方版本的MySQL，可以在[MySQL官方网站](<https://www.mysql.com/>)下载安装文件。首先在下载页面中选择平台和版本，然后找到对应的下载链接。下面以MySQL 5.7.26版本和Red Hat Enterprise Linux为例，直接下载包含所有安装文件的归档文件，解归档之后通过包管理工具进行安装。

 ```Shell
 wget https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.26-1.el7.x86_64.rpm-bundle.tar
 tar -xvf mysql-5.7.26-1.el7.x86_64.rpm-bundle.tar
 ```

 如果系统上有MariaDB相关的文件，需要先移除MariaDB相关的文件。

 ```Shell
 yum list installed | grep mariadb | awk '{print $1}' | xargs yum erase -y
 ```

 接下来可以按照如下所示的顺序用RPM（Redhat Package Manager）工具安装MySQL。

 ```Shell
 rpm -ivh mysql-community-common-5.7.26-1.el7.x86_64.rpm
 rpm -ivh mysql-community-libs-5.7.26-1.el7.x86_64.rpm
 rpm -ivh mysql-community-client-5.7.26-1.el7.x86_64.rpm
 rpm -ivh mysql-community-server-5.7.26-1.el7.x86_64.rpm
 ```

 可以使用下面的命令查看已经安装的MySQL相关的包。

 ```Shell
 rpm -qa | grep mysql
 ```

## 启动MySQL服务。

 先修改MySQL的配置文件（`/etc/my.cnf`）添加一行`skip-grant-tables`，可以设置不进行身份验证即可连接MySQL服务器，然后就可以以超级管理员（root）身份登录。

 ```Shell
 vim /etc/my.cnf
 ```

 ```INI
 [mysqld]
 skip-grant-tables
 
 datadir=/var/lib/mysql
 socket=/var/lib/mysql/mysql.sock
 
 symbolic-links=0
 
 log-error=/var/log/mysqld.log
 pid-file=/var/run/mysqld/mysqld.pid
 ```

 接下来可以使用下面的命令来启动MySQL。

 ```Shell
 service mysqld start
 ```

 在CentOS 7中建议使用下面的命令来启动MySQL。

 ```Shell
 systemctl start mysqld
 ```

- 使用MySQL客户端工具连接服务器。

 命令行工具：

 ```Shell
 mysql -u root
 ```

 修改超级管理员（root）的访问口令为i_LOVE_macos_123。

 ```SQL
 use mysql;
 update user set authentication_string=password('i_LOVE_macos_123') where user='root';
 flush privileges;
 ```

 将MySQL配置文件中的`skip-grant-tables`去掉，然后重启服务器，重新登录。这一次需要提供用户名和口令才能连接MySQL服务器。

 ```Shell
 systemctl restart mysqld
 mysql -u root -p
 ```

 也可以选择图形化的客户端工具来连接MySQL服务器，可以选择下列工具之一：

 - MySQL Workbench（官方提供的工具）
 - Navicat for MySQL（界面简单优雅，功能直观强大）
 - SQLyog for MySQL（强大的MySQL数据库管理员工具）


# MySQLl命令
## MySQL进入与退出   
	- mysql –uusername -ppassword （进入）
	- exit  (退出）
![](https://img-blog.csdnimg.cn/20190227220439691.jpg)
##  库级操作语句
	- 显示所有的库：show databases;
	- 创建库：create database [if not exists] db_name; 
	- 删除库：drop database [if exists] db_name;
	- 进入数据库：use db_name;
![](https://img-blog.csdnimg.cn/20190227220941236.jpg)
## 表级操作语句
	- 显示所有的表：show tables;
	- 创建表：create table [if not exists]  tb_name (create definition…);
	- 显示创建表的信息：show create table tb_name;
	- 删除表：drop table tb_name;
![](https://img-blog.csdnimg.cn/20190227222358297.jpg)
* 注意：语句结束符：**每个语句都以 ; 或者 \G 结束**

## 插入数据
	- 全字段插入： INSERT INTO tb_name VALUE (all_values); 一般只用这种


​	
![](https://img-blog.csdnimg.cn/20190227223014419.jpg)

## 查询数据
	- SELECT field_names FROM tb_name;
	- SELECT * FROM tb_name;
	- SELECT field_names FROM tb_name WHERE conditions; 

![](https://img-blog.csdnimg.cn/20190227223616269.png)

## 修改数据
	- 修改所有数据：UPDATE  tb_name  SET field_1=value_1 ；
	- 修改多个： UPDATE  tb_name  SET field_1=value_1, field_2=value_2 …; 
	- 修改满足条件的数据： UPDATE  tb_name  SET field_1=value_1  WHERE  conditions; 

![](https://img-blog.csdnimg.cn/20190227224457869.jpg)

## 删除数据
	- 删除表中所有数据：DELETE  FROM  tb_name;
	- 删除表中满足条件的数据： DELETE  FROM  tb_name  WHERE  conditions;
![](https://img-blog.csdnimg.cn/20190227224858367.jpg)

## 数值类型
![](https://img-blog.csdnimg.cn/20190227220245409.png)
## 字符类

![](https://img-blog.csdnimg.cn/20190227220327863.png)


##  Python连接Mysql


Python连接Mysql，用的是pymysql




```python
import pymysql

config = {
    'host': '127.0.0.1',
    'port': 3306,
    'user': 'root',
    'passwd': '',
    'charset': 'utf8',
    'cursorclass': pymysql.cursors.DictCursor
}
conn = pymysql.connect(**config)
conn.autocommit(1)
cursor = conn.cursor()

try:
    # 创建数据库
    DB_NAME = 'test'
    cursor.execute('DROP DATABASE IF EXISTS %s' % DB_NAME)
    cursor.execute('CREATE DATABASE IF NOT EXISTS %s' % DB_NAME)
    conn.select_db(DB_NAME)

    # 创建表
    TABLE_NAME = 'user'
    cursor.execute('CREATE TABLE %s(id int primary key,name varchar(30))' % TABLE_NAME)

    # 批量插入纪录
    values = []
    for i in range(20):
        values.append((i, 'kk' + str(i)))
    cursor.executemany('INSERT INTO user values(%s,%s)', values)

    # 查询数据条目
    count = cursor.execute('SELECT * FROM %s' % TABLE_NAME)
    print('total records:', cursor.rowcount)

    # 获取表名信息
    desc = cursor.description
    print("%s %3s" % (desc[0][0], desc[1][0]))

    cursor.scroll(10, mode='absolute')
    results = cursor.fetchall()
    for result in results:
        print(result)

except:
    import traceback

    traceback.print_exc()
    # 发生错误时会滚
    conn.rollback()
finally:
    # 关闭游标连接
    cursor.close()
    # 关闭数据库连接
    conn.close()

```




