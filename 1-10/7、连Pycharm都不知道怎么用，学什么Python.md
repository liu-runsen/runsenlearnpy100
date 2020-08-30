@Author ： By Runsen
@Author ： 2020/5/16



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。



我决定把去年写的Python文章整理一个专栏，垃圾的就直接删除，将多篇博文整理成一篇。




上篇[乘胜追击，将剩下的Git知识点搞定（六）](https://blog.csdn.net/weixin_44510615/article/details/106148028)





@[TOC]


工欲善其事必先利其器，Pycharm 是最受欢迎的Python开发工具，它提供的功能非常强大，我尽量把自己用的都写写吧

# 1、设置Python 解释器



在任何项目，第一步就是设置Python 解释器，就是那个Python.exe








在File->Setting->Projec: xxx 下找到 Project Interpreter。然后修改为你需要的 Python 解释器。注意这个地方一定要注意的是：在选择 Python 解释器的时候，一定要选择到 python.exe 这个文件，而不是 python 的安装文件夹。





![](https://img-blog.csdnimg.cn/20200516114228617.png)








咋RunsenPycharm中设置了有anacodna的 python.exe ，有远程的python.exe，有直接下载的python.exe






![](https://img-blog.csdnimg.cn/20200516114610502.png)



本地和anaconda不说了，太他妈简单了，就说如何远程虚拟机吧，连接Docker，可能小白都不知道什么是Docker，以后在说吧


## 1.1 远程配置

Pycharm设置远程应该是使用Django项目的时候，

![](https://img-blog.csdnimg.cn/20200516115034682.png)
其实很简单，我就拿我的Centos7 ip是192.168.9290





![](https://img-blog.csdnimg.cn/20200516120014224.png)


用户名的密码
![](https://img-blog.csdnimg.cn/20200516120120693.png)


![](https://img-blog.csdnimg.cn/20200516120415173.png)


然后就是配置中两个东西


![](https://img-blog.csdnimg.cn/20200516120520908.png)







![](https://img-blog.csdnimg.cn/20200516120755569.png)

![](https://img-blog.csdnimg.cn/20200516120818428.png)



![](https://img-blog.csdnimg.cn/20200516120842918.png)


![](https://img-blog.csdnimg.cn/20200516120936271.png)


出现了Deployment就说明OK了。


![](https://img-blog.csdnimg.cn/202005161210276.png)

# 2、调整字体及其大小

## 2.1 调整编辑器字体及其大小

所有的位置都是在Settings中，具体哪里看图

![](https://img-blog.csdnimg.cn/20200516121509710.png)

## 2.2 调整控制台的字体及其大小


![](https://img-blog.csdnimg.cn/20200516121815501.png)


# 3、设置编码




![](https://img-blog.csdnimg.cn/20200516121954173.png)
# 4、修改文件背景颜色

![](https://img-blog.csdnimg.cn/20200516122149105.png)



# 5、设置Git 和Github


## 5.1 配置git

Git的位置
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190510203756991.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)
## 5.2 配置github
![](https://img-blog.csdnimg.cn/20190510203845319.png)
现在就可以上传代码到github
![这里插入图片描述](https://img-blog.csdnimg.cn/20190510204021554.png)


上次代码到Github的Commit




![](https://img-blog.csdnimg.cn/20190510204131560.png)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20190510204224523.png)

![](https://img-blog.csdnimg.cn/2019051020425614.png)


## 5.3  下载仓库内容
![](https://img-blog.csdnimg.cn/20190510204438422.png)
![](https://img-blog.csdnimg.cn/20190510204645314.png)




# 6 、新建.py文件时默认添加信息



这是去年的博客

对于pycharm我们每次新建Python文件时需要加的注释信息和作者时间等信息可以使用模板的方式，这样每次新建文件之后就默认添加比较方便。
1、点击pycharm的右上角的file出现如下图点击settings：



![](https://img-blog.csdnimg.cn/20200330141119187.png)

2、接着就是找到如下图的地方：



![](https://img-blog.csdnimg.cn/20200330141752131.png)


3、在里面加上想要创建文件之后就默认添加的内容，下面是编辑内容的具体格式：
预定义的变量要扩展为格式为$ {<variable_name>}的相应值。

可用的预定义文件模板变量为：

$ {PROJECT_NAME} - 当前项目的名称。

$ {NAME} - 在文件创建过程中在“新建文件”对话框中指定的新文件的名称。

$ {USER} - 当前用户的登录名。

$ {DATE} - 当前的系统日期。

$ {TIME} - 当前系统时间。

$ {YEAR} - 今年。

$ {MONTH} - 当月。

$ {DAY} - 当月的当天。

$ {HOUR} - 目前的小时。

$ {MINUTE} - 当前分钟。

$ {PRODUCT_NAME} - 将在其中创建文件的IDE的名称。

$ {MONTH_NAME_SHORT} - 月份名称的前3个字母。 示例：1月，2月等

$ {MONTH_NAME_FULL} - 一个月的全名。 示例：1月，2月等



![](https://img-blog.csdnimg.cn/2020033014180732.png)


# 7、恢复代码


如果误删了代码，不要怕


![](https://img-blog.csdnimg.cn/20200516123222114.png)



![](https://img-blog.csdnimg.cn/202005161232476.png)


# 8、代码换行


写的代码多了，可以Soft--Wrap自动换行

![](https://img-blog.csdnimg.cn/20200516123356794.png)





# 9、Reformat Code

写的代码不够好看，直接Reformat

![](https://img-blog.csdnimg.cn/20200516123514734.png)


# 10、连接数据库

![](https://img-blog.csdnimg.cn/20200516123703954.png)


![](https://img-blog.csdnimg.cn/20190514212208760.png)


Host: 远程ip 若是连接本地MySQL 直接写localhost即可
Database: 填写数据库名称,不写默认连接之后,可以查看当前用户权限下的所有数据库
User: MySQL用户名
Password: MySQL密码

注意: 首次连接需要下载驱动,点击左下角的Download下载

下载完毕后,点击test connection ,测试连接 成功显示Successful Details

![](https://img-blog.csdnimg.cn/20190514212313839.png)

![](https://img-blog.csdnimg.cn/20190514212339278.png)


![](https://img-blog.csdnimg.cn/20190514212417852.png)



# 11、 Debug


![](https://img-blog.csdnimg.cn/20200516124041537.png)

![](https://img-blog.csdnimg.cn/20200516124106239.png)




![](https://img-blog.csdnimg.cn/20200516124202661.png)


前面的信息就可以显示出来
# 12、PyCharm 常用快捷键


熟悉每个编辑器的快捷键，能大大提高你的工作效率。





![](https://img-blog.csdnimg.cn/2020051612295584.png)


![](https://img-blog.csdnimg.cn/202005161230082.png)


# 总结


这里介绍了Pycharm的日常使用，关键就是不断地练习。

下面开始Python编程


