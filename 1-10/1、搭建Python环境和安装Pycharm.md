
@Author ： By Runsen



Python环境搭建（一）
@[toc]

# 1、 搭建Python的基础环境


安装python的基础环境。

首先，我们需要访问Python官网：https://www.python.org/。



![](https://img-blog.csdnimg.cn/20200510185558709.png)


目前Python更新到3.8.2版本，这里我不建议大家安装Python3.8.2版本，而是选择安装Python3.6或者3.7稳定版。


![](https://img-blog.csdnimg.cn/20200510185650725.png)

下载后，双击下载包exe，进入 Python 安装向导，安装非常简单，你只需要使用默认的设置一直点击"下一步"直到安装完成即可，但是要记住在安装的过程需要选择“ADD Python3.6 to PATH"，这样是为了添加Python到环境变量。



![](https://img-blog.csdnimg.cn/20200510185704207.png)

如果你选择的是默认安装而不是自定义安装，可以忽略以下步骤，如下图这页默认全选，点击Next


![](https://img-blog.csdnimg.cn/20200510185725205.png)


如下图，打对勾的保持默认即可，下面红框是选择安装路径，其实我选择自定义安装的目的就是不想把程序安装在c盘，点击Install 等待安装完成

![(https://img-blog.csdnimg.cn/20200510185750708.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)
下面这个就是安装成功了，安装成功，我们就点击关闭就可以了close





![](https://img-blog.csdnimg.cn/20200510185806525.png)

那截止到这这个环境是安装好了是吧，那接下来我们是不是Python环境验证一下。我们用win+R打开命令窗口， 输入cmd点击确定。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510185819568.png)




查看python版本，如下图可以看到是我们上面所安装的python 3.6.7

![](https://img-blog.csdnimg.cn/2020051018584552.png)
python3.6之后版本都是有pip的，pip是Python安装包的管理工具，如下图可以看到安装python3.6.7之后就有了pip，如果是 command not found 那说明没有安装。


![](https://img-blog.csdnimg.cn/20200510185900328.png)


下面，我们在命令窗口中，输入python，打开python最原始的交互环境，打印一个hello python，也就是print("hello python)




![在这里插入图片描](https://img-blog.csdnimg.cn/20200510185913497.png)


在这里输完之后直接点击回车，点击回车之后，然后Python执行我们的语句。打印这个hello python
在这里，window系统Python安装完毕。

# 2、 安装Pycharm





![](https://img-blog.csdnimg.cn/20200510190124221.png)

选择下载window版本的Pycharm。



![](https://img-blog.csdnimg.cn/20200510190145246.png)



下载完成后，我们点击exe文件进行安装，安装会弹出下面界面，我们直接选择Next




![](https://img-blog.csdnimg.cn/20200510190158960.png)


下面界面就是选择安装目录。我们尽量不要默认安装，默认安装它是装C盘里了，你自己安装路径。但是注意注意有一点：安装路径千万不要中文。如果有中文的话可能会出问题。




![](https://img-blog.csdnimg.cn/20200510190219685.png)


然后点击下一步选择安装路径之后，点击下一步。
下一步完之后，它告诉你什么，创建一个桌面程序，它是64位的还是32位的，其实这里面不用多选
基本都是64位的操作系统。



![在这里插入图片描](https://img-blog.csdnimg.cn/20200510190300112.png)
点击下一步，我们不需要修改名字，直接点击install安装。



![](https://img-blog.csdnimg.cn/20200510190316166.png)



下面就是等待安装完成这个过程，不用管就等就行了，然后这就是安装完成了。

![](https://img-blog.csdnimg.cn/20200510190333204.png)
然后双击我们第一次使用PyCharm双击它，完之后弹出来一个小框，这个小框当中它是做什么的，就告诉我们是不是导入一些基本设置。我们第一次用之前也没有设置，那么就不导入了，直接就是do not，选择这个，然后OK。




![](https://img-blog.csdnimg.cn/20200510190352416.png)

OK完，这里边必须要让你同意服务条款，这边是什么都不用管了。把右侧的这个滚动条滑到最底部
点击accept同意这个按钮。



![](https://img-blog.csdnimg.cn/2020051019041190.png)

下面，写一个Hello Python程序。

我们点击create new project，这个是创建一个新的项目


![](https://img-blog.csdnimg.cn/2020051019043439.png)



创建新的项目之后，这里面就要输入我们项目的存储路径以及项目名称了。那么我这里边直接把最后一个字段去改掉。其实这个就是我们自己的一个名称了。这个项目路径和项目名称添加完之后，你自己起名字就可以，然后我就在这里边点击create了，就开始创建了



![](https://img-blog.csdnimg.cn/20200510190501557.png)



我们接下来，和上一次一样的操作。第一步在我们自己的项目名称，项目名称的那里面，点击右键这是第一步，第二步，把鼠标指针挪到new上，选择new。第三步，然后点击python file，创建一个python文件



![](https://img-blog.csdnimg.cn/20200510190525196.png)

我们的代码就要写到这个文件里，然后输入hello，这hello其实是这个文件名字

![](https://img-blog.csdnimg.cn/20200510190542698.png)
然后点击OK，点击完OK之后呈现到大家面前是这么样的页面，它分两个区域，一个是python文件列表区域

这个其实是我们项目的所有的文件列表，现在我们只创建了一个文件叫hello.py。然后还有就是代码编写区域
，我们所有代码都要在代码编写区域当中来进行写。


![](https://img-blog.csdnimg.cn/20200510190607666.png)

那么这里我们要做什么，输入跟我们之前输的那个东西是一样的，也是那行代码print("hello Python")。输入完之后右键在空白区域，空白区域右键就可以了，它会弹出来这么一个框是吧。在这个框我们点击 RunHello，跑一下这个代码，在你的IDE的最下面就会出现hello Python








![](https://img-blog.csdnimg.cn/20200510190625398.png)


