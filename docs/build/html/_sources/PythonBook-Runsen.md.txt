# Python从小白变成大师教程（共十五万字）

人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen

@Author：Runsen

@微信：RunsenLiu

@公众号：Python之王

![](https://img-blog.csdnimg.cn/20200716234914987.jpg)



# 前言、Python的前世和发展

## Python的前世

1989年圣诞节前夕，山雨欲来风满楼，计算机程序设计语言界隐隐有大事要发生，果然不出所料。江湖人称龟叔(Guido von Rossum)，就是这位祖籍荷兰的大牛，在圣诞节百无聊赖的期间，发明了Python。




![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9kZDA0ZDIyMS04Y2JjLTQ2M2QtODczNS1hMGUzZTQwODFjMzgucG5n?x-oss-process=image/format,png)


之所以选中Python作为程序的名字，是因为龟叔是BBC电视剧——蒙提·派森的飞行马戏团（Monty Python's Flying Circus）的爱好者。ABC是由参加设计的一种教学语言。就龟叔本人看来，ABC这种语言非常优美和强大，是专门为非专业程序员设计的。

但是由于ABC语言并没有成功，究其原因，龟叔认为是非开放造成的。龟叔决心在Python中避免这一错误，并获取了非常好的效果，完美结合了C和其他一些语言。

就这样，Python在龟叔手中诞生了。那时，龟叔还在荷兰的CWI（Centrum voor Wiskunde en Informatica，国家数学和计算机科学研究院）。龟叔给Python的定位是“优雅”、“明确”、“简单”

1991年，第一个Python编译器诞生。它是用C语言实现的，并能够调用C语言的库文件。从一出生，Python已经具有了 ：类，函数，异常处理，包含表和词典在内的核心数据类型，以及模块为基础的拓展系统。

实际上，Python第一个实现是在 Mac 计算机上。可以说，Python是从ABC发展起来，主要受到了 Modula-3（另一种相当优美且强大的语言，为小型团体所设计的）的影响，并且结合了Unix shell 和C的习惯。

1991年初，Python发布了第一个公开发行版。

2000年10月16日，Python 2.0版本发布，增加了实现完整的垃圾回收，并且支持Unicode。同时，整个开发过程更加透明，社群对开发进度的影响逐渐扩大。

2008年12月3日，Python 3.0版本发布，此版不完全兼容之前的Python源代码。不过，很多新特性后来也被移植到旧的Python 2.6，2.7版本

## Python的特性


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS8wNjFmZDlmNS0zNjJlLTQxMzMtOWE4OS05ZjI1ZmZjMGI4M2QucG5n?x-oss-process=image/format,png)

（1）简单易学：Python极其容易上手，因为Python有极其简单的说明文档。

（2）免费、开源：Python是FLOSS（自由/开放源码软件）之一。使用者可以自由地发布这个软件的拷贝、阅读它的源代码、对它做改动、把它的一部分用于新的自由软件中。

（3）高层语言：用Python语言编写程序的时候无需考虑诸如如何管理你的程序使用的内存一类的底层细节。

（4）可移植性：由于它的开源本质，Python已经被移植在许多平台上（经过改动使它能够工作在不同平台 上）。这些平台包括Linux、Windows、FreeBSD、Macintosh、Solaris、OS/2、Amiga、AROS、AS/400、 BeOS、OS/390、z/OS、Palm OS、QNX、VMS、Psion、Acom RISC OS、VxWorks、PlayStation、Sharp Zaurus、Windows CE、PocketPC、Symbian以及Google基于linux开发的android平台。

（5）丰富的库：Python标准库确实很庞大。它可以帮助处理各种工作，包括正则表达式、文档生成、单元测试、线程、数据库、网页浏览器、CGI、FTP、电子邮件、XML、XML-RPC、HTML、WAV文件、密码系统、GUI（图形用户界面）

上面介绍了Python的优点，其实python的也有缺点

（1）运行较慢：相较于c， c++  ，Java编译型语言，python、javascript解释型语言不是编译成机器码，而是编译成中间码。Python在解释器而不是编译器的帮助下执行，这将导致它变慢，因为编译和执行有助于它正常工作。

因为Python在定义变量或函数时不会声明类型，即使在编译为pyc字节码后变量的类型以及函数返回类型都是未知的，通过上下文推算出实际的类型，是需要占用内存消耗的。比如a + b 先要通过复杂的上下文推荐得出a和b的实际类型，进而再转换为对应的机器指令，不像其他强类型语言，比如java，所有数据类型在编译为class文件时都已经确定了，不需要额外耗时去做类型推算。

（2）性能差：Python的开箱即用的性能速度依然落后于其他语言，比如说具有同样简单语法的Nim和Julia，却可以被编译为机器代码，具有更高的性能优势。

比如，著名的知乎推荐系统用Go替代Python，随着业务发展，发现 Python 作为动态解释型语言，较低的运行效率和较高的后期维护成本带来的问题逐渐暴露出来：

- 运行效率较低。知乎目前机房机柜空间已经不足，按照目前的用户和流量增长速度，可预见将在短期内服务器资源告急（针对这一点，知乎正在由单机房架构升级为异地多活架构）；
- Python 过于灵活的语言特性，导致多人协作和项目维护成本较高

毕竟Python是通用型，高级的动态编程语言。强调的是 code readability，它的句法使得程序员能够比在C++或者java的静态编程语言相比，编写更少的代码行数。

下面介绍一些的 Python常用高级特性

（1）lambda

lambda函数可以使用任意数量的参数，但必须始终只有一个表达式，我们这样做是因为lambda函数的目的是执行某种简单的表达式或操作，而无需完全使用def定义函数。

```
In [1]: x = lambda a, b : a * b

In [2]: x(2,3)
Out[2]: 6
```

我们执行了一些基本的数学运算，而无需定义完整的函数。这是Python的众多功能之一，使其成为一种简洁易用的编程语言。

（2）Map

Map函数是一个内置的Python函数，用于将函数应用于像列表或字典这样的元素序列。这是执行此类操作的非常干净且最重要的可读方式。map不改变原list，而是返回一个新list

```
In [3]: list(map(lambda x:x*x ,(1,2,3)))
Out[3]: [1, 4, 9]
```

（3）列表循环

列表解析式（List comprehension）或者称为列表推导式，是 Python 中非常强大和优雅的方法。它可以基于现有的列表做一些操作，从而快速创建新列表。

```
In [4]: a,*b,c,d = list(range(10))

In [5]: a
Out[5]: 0

In [6]: b
Out[6]: [1, 2, 3, 4, 5, 6, 7]

In [7]: c
Out[7]: 8

In [8]: d
Out[8]: 9

In [9]: [x*x for x in range(5) if x%2!=0]
Out[9]: [1, 9]
```

（4）生成器

通过列表⽣成式，我们可以直接创建⼀个列表。但是，受到内存限制，列表容量肯定是有限的。

在Python中，这种⼀边循环⼀边计算的机制，称为⽣成器：generator。这样就不必创建完整的list，从⽽节省⼤量的空间。

```
In [10]: a = (i for i in range(5))

In [11]: a
Out[12]: <generator object <genexpr> at 0x0000023269845750>

In [13]: next(a)
Out[13]: 0

In [14]: next(a)
Out[14]: 1
```

## Python发展

进入2020年3月，新的编程语言排行榜新鲜出炉，TIOBE 最新发布了 3 月编程语言排行榜。


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS8xYzMxN2I1MS0yMTZjLTQyYzAtYjc3NS0yNWZmZWRmZWFhNWUucG5n?x-oss-process=image/format,png)



从榜单中我们可以看到，前三名分别为Java、C、Python。相较于上个月，Python继续以1.85% 上升至 10.11%，以10.11%  的份额稳居第三。

Python可以应用于众多领域，如：数据分析、组件集成、网络服务、图像处理、数值计算和科学计算等众多领域。目前业内几乎所有大中型互联网企业都在使用Python，如：Youtube、Dropbox、BT、Quora（中国知乎）、豆瓣、知乎、Google、Yahoo!、Facebook、NASA、百度、腾讯、汽车之家、美团等。互联网公司广泛使用Python来做的事一般有：自动化运维、自动化测试、大数据分析、爬虫、Web 等。

不可否认，Python 确实是这个时代最流行、也必须要掌握的编程语言。Python 可以运用在数据处理、Web 开发、人工智能等多个领域，它的语言简洁、开发效率高、可移植性强，并且可以和其他编程语言（比如 C++）轻松无缝衔接。现如今，不少学校的文科生甚至中学生也开设了此课程，可见其重要程度。

Python职业发展方向

（1）网络爬虫

Python较为常用的情况就是网络爬虫，最早使用Python进行网络爬虫的是Google，而Python也因此被带动发展起来。

Python在这个方面有许多工具上的积累，例如，用于模拟HTTP请求的Requests、用于HTML DOM解析的PyQuery/BeautifulSoup、用于自动化分布式爬取任务的Scrapy，都使得Python成为数据爬取的首选语言之一。Python同时特别擅于分析与计算爬取后的数据。

（2）Linux运维

用python实现的测试工具及过程，包含服务器端、客户端、web、andriod、client端的自动化测试，自动化性能测试的执行、监控和分析，常用selenium appium等框架。

（3）Python Web网站工程师

我们都知道Web一直都是不可忽视的存在，我们离不开网络，离不开Web，利用Python的框架，Django，flask可以做网站，而且都是一些精美的前端界面，还有我们需要掌握一些数据的应用。

（4）Python自动化测试

大家都知道，就是Python语言对测试的帮助是非常大的，自动化测试中Python语言的用途很广，可以说Python太强大，掌握和熟悉自动化的流程，方法和我们总使用的各个模板，到现在为止，我了解的Python使用最多的应该是自动化测试。

（5）数据分析

我们都知道现在来临了大数据的时代，数据可以说明一切问题的原因，现在很多做数据分析的不是原来那么简单，Python语言成为了做数据分析师的第一首选，它同时可以给工作带来很大的效率。

（6）人工智能

人工智能是现在大火的一个方向，这让Python语言的未来充满了无限的潜力。机器学习，特别是当前热门的深度学习中的大部分工具框架都提供了Python接口，因为Python的简洁清晰的语法是深受开发者喜爱的。

@Author ： By Runsen





# 1、 搭建Python的基础环境

## 安装python的基础环境



首先，我们需要访问Python官网：https://www.python.org/。

![](https://img-blog.csdnimg.cn/20200510185558709.png)


目前Python更新到3.8.2版本，这里我不建议大家安装Python3.8.2版本，而是选择安装Python3.6或者3.7稳定版。


![](https://img-blog.csdnimg.cn/20200510185650725.png)

下载后，双击下载包exe，进入 Python 安装向导，安装非常简单，你只需要使用默认的设置一直点击"下一步"直到安装完成即可，但是要记住在安装的过程需要选择“ADD Python3.6 to PATH"，这样是为了添加Python到环境变量。



![](https://img-blog.csdnimg.cn/20200510185704207.png)

如果你选择的是默认安装而不是自定义安装，可以忽略以下步骤，如下图这页默认全选，点击Next


![](https://img-blog.csdnimg.cn/20200510185725205.png)


如下图，打对勾的保持默认即可，下面红框是选择安装路径，其实我选择自定义安装的目的就是不想把程序安装在c盘，点击Install 等待安装完成

![](https://img-blog.csdnimg.cn/20200510185750708.png)
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

## 安装Pycharm



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

﻿@Author ： By Runsen



# 2、搭建Jupyter Notebook环境

## 1、Jupyter notebook历史

Jupyter 创始人 Fernando Pérez 的说法，他最初的梦想是做一个综合 Ju （Julia）、Py （Python）和 R 三种科学运算语言的计算工具平台，所以将其命名为 Ju-Py-te-R。发展到现在，Jupyter 已经成为一个几乎支持所有语言，能够把软件代码、计算输出、解释文档、多媒体资源整合在一起的多功能科学运算平台。

在Pycham中只能运行一共py文件，而在Jupyter notebook可以运行一行代码就可以了。

## 2 、环境搭建

你可以直接是通过 pip 命令安装。


```clike
pip install jupyter
```

你也可以下载anaconda




   Anaconda官网下载链接：https://www.anaconda.com/distribution/#download-section，选择Python3版本的安装包下载即可


![](https://img-blog.csdnimg.cn/20200510224126168.png)



   

   如果下载速度过慢，可以选择安装Anaconda的清华镜像，网址https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive


  下载完成之后，直接双击安装包安装即可。安装后添加清华镜像源解决conda install 下载速度慢的问题，打开Anaconda Prompt命令行，依次添加命令

 

```clike
 conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
 conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
 conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
 conda config --set show_channel_urls yes
```

之前说清华源，不适应了，现在OK，可以使用清华源

## 3、conda常见命令

conda不仅可以方便安装，更新，卸载工具包，而且安装时能自动安装相应的依赖包。conda命令多数时候是在配置虚拟环境时使用，下面是conda常见命令

```python
conda list              //查看当前的包
conda search request    //查找request库
conda install request   //安装request库
conda uninstall request //删除request库
conda update request    //更新request库
```

很多时候不同的库依赖不同的依赖包，需要创建虚拟环境，下面是conda创建虚拟环境的常用命令

```
conda info --envs       //查看安装好的环境
# deeplearn代指克隆得到的新环境的名称，base代指被克隆的环境的名称
conda create --name deeplearn --clone base
# 激活虚拟环境
activate envname //for windows
source activate envname //for liunx and mac
# 退出虚拟坏境
deactivate
#查看当前的包
conda list
```

![](https://img-blog.csdnimg.cn/20200510225507691.png)


```clik
#查看安装好的环境
conda info --envs  
```



![](https://img-blog.csdnimg.cn/20200510225537392.png)

## 4、虚拟环境搭建

   在创建的虚拟环境上运行jupyter notebook,但发现在notebook中的python其实并没有运行在指定的虚拟环境引擎上，只需要安装nb_conda_kernels插件即可解决，注意是在base环境下安装，而不是虚拟环境

```clike
(base) conda install nb_conda_kernels
```

安装成功后，在kernel -> change kernel中即可切换到指定的虚拟环境

![](https://img-blog.csdnimg.cn/20200510224404138.png)
你可以可以新建Notebook的时候设置kernel 



![](https://img-blog.csdnimg.cn/20200510224300139.png)

## 5、修改jupyter notebook的打开路径




安装好jupyter notebook 后打开的是默认文档位置，需要来修改存放文件的路径。

下面教大家修改jupyter notebook的打开路径

打开jupyter notebook 文件所在的位置

![](https://img-blog.csdnimg.cn/20190217140534777.png)
 右键， 打开属性
 ![](https://img-blog.csdnimg.cn/2019021714085440.png)

按照下图配置参数
![](https://img-blog.csdnimg.cn/2019021714135627.png)
这样打开jupyter notebook就不是默认文档位置了。


![](https://img-blog.csdnimg.cn/20200510224701876.png)

## 6、pip 和conda的区别

conda可以让你同时管理安装处理有关的python任务和跟python无关任务，即pip可以允许在任何环境中安装 python包，conda允许你在conda环境中安装任何语言包（包括C语言或者python）。


conda使用一个新的包格式，你不能交替使用conda和pip，

因为pip不能安装和解析conda的包格式。可以使用这两个工具，但是它们是不能交互的。

conda安装库是在一个地方，而且需要根据Python的环境和依赖库而定，比如numpy的版本有的过高，导致安装这个库使用的时候报错。

pip安装就是根据Python的版本而定，有的时候conda安装不了，可以采用pip安装。

﻿# 3、新手Jupyter不会用，我十招教你盘她

上次教大家搭建好了Jupyter，并学习了一些conda命令。

如果你是新手，Jupyter不会用，那么我教你盘她

## 1、官方文档

安装好了anaconda只好，大家应该见到这些玩意，还有一个spider我删除了，有Pycharm就可以不要spider了。我这里的jupyter是设置了deeplearn为默认环境，所以有jupyter后面多了deeplearn。
![](https://img-blog.csdnimg.cn/20200510230541144.png)

我们点击那个Navigator，等一下就可以下面的图片了。

![](https://img-blog.csdnimg.cn/20200510230905927.png)
我们选择learning，点击jupyter就可以看文档了。大家学习都是要这样，先去官方文档。

![](https://img-blog.csdnimg.cn/2020051023101055.png)

浏览器就来到了：https://jupyter.org/documentation.html



![](https://img-blog.csdnimg.cn/20200510231149252.png)

然后，我们点击jupyter notebook


来到官方文档：https://jupyter-notebook.readthedocs.io/en/stable/

读英文不行啊，建议大家安装Chrome，直接翻译中文简体。

![](https://img-blog.csdnimg.cn/20200510231403855.png)
这里建议停留十分钟，大家把jupyter的官方文档看一遍，再继续看下面。

## 2、创建一个jupter notebook

下面，我们就真正开始学习Jupyter ，我不想抄官方文档，就把自己的经验那出来算了。



该页面是启动之后默认打开的页面。我们可以看到当前目录下已有的文件，可以查看已有的jupyter 文件(灰色表示未在运行，绿色表示正在运行)，可以点击查看子目录下的内容，jupyter 默认访问的是8888端口

![](https://img-blog.csdnimg.cn/2020051023215453.png)



创建一个jupter notebook非常的简单，点击右侧的New，选择Python3会在新的页面中建立一个未命名的notebook文件，选择Text File会新的页面中建立一个未命名的txt文件，选择Folder会在当前页面中建立一个未命名文件夹，选择Terminal会在新的页面中建立Terminal。

![](https://img-blog.csdnimg.cn/20200510232402410.png)



下面就是新建的内容
![](https://img-blog.csdnimg.cn/20200510232421600.png)




重命名直接点击文件名就可以了。

![](https://img-blog.csdnimg.cn/20200510232528566.png)

可以在左侧进行勾选，对文件夹进行重命名，移动或删除，对文件进行复制，重命名，移动，编辑和删除。



![](https://img-blog.csdnimg.cn/20200510232642912.png)


![](https://img-blog.csdnimg.cn/20200510232757852.png)
如果这个后台删除了，那么你就访问不了你的jupyter了。

## 3、Notebook使用



下面，教大家学习一下Notebook使用
、![](https://img-blog.csdnimg.cn/20200510233001843.png)


现在我们在help中点击Notebook help，来到了官方的教程，建议你还是看一看。

![](https://img-blog.csdnimg.cn/20200510233259224.png)

官方的教程的网页
![](https://img-blog.csdnimg.cn/20200510233449759.png)

## 4、 编辑模式



每一个cell有两种模式：命令模式和编辑模式。



![](https://img-blog.csdnimg.cn/20200510234214589.png)


如下图所示：最左侧是蓝色的条是命令模式，是绿色的条表示编辑模式(此时cell中有光标，可以进行代码编写)。在命令模式下，按下enter或者鼠标单击代码框可以进入编辑模式。在编辑模式下，按下esc或者鼠标单击代码框左侧区域即可进入命令模式。



![](https://img-blog.csdnimg.cn/20200510234332838.png)


在编辑模式下，按住SHIFT+ENTER就可以运行代码了。

## 5、命令模式


命令模式就是使用Markdown。

![](https://img-blog.csdnimg.cn/20200510234800502.png)

![](https://img-blog.csdnimg.cn/20200510235339934.png)

在命令模式下，可以按住下面的键，实现下面的效果。


- 按下A：向上增加空白的cell

- 按下B：向下增加空白的cell

- 按下D两次（DD）：删除该cell

- 按下X：剪贴该cell

- 按下V：粘贴该cell

- 按下L：打开、关闭行号


- 按下M：进入Markdown模式

- 按下Y：退出Markdown模式，回到代码编辑模式



当进入Markdown模式的时候，cell左边的 In【】会消失掉

## 6、Markdown语法


我直接把CSDN上的Markdown给你搬过来。

下面是常见的快捷键

![](https://img-blog.csdnimg.cn/20200510235521475.png)



目录，标题和文本样式

![](https://img-blog.csdnimg.cn/20200510235912274.png)


![](https://img-blog.csdnimg.cn/20200511000002261.png)

我觉得你还是写博客直接看CSDN的帮助文档算了。

## 6、Latex数学公式

Latex我不想写了，直接看我之前的文章

[手把手教你插入数学公式，妈妈再也不用担心我写不了论文了](https://maoli.blog.csdn.net/article/details/105377233)

## 7、Notebook小技巧

这篇文写得不错，总结了Notebook的27个小技巧，文章链接：http://liuchengxu.org/pelican-blog/jupyter-notebook-tips.html。这是原创，大家不要看那些转载的。

## 8、保存文件


我们新建的名字叫ipynb，为什么我喜欢用Jupyter，就是因为可以保存很多类型的文件，比如pdf，html，markdowm，latex。



![](https://img-blog.csdnimg.cn/20200510233632667.png)

## 9、误删了怎么恢复


 直接在一个单元格中输入：history （如图）
就会展示出历史代码（前提是你运行过的，否则不会打印出来）

![](https://img-blog.csdnimg.cn/20200511000624937.png)

## 10、大招

我把大招留在最后，就是你遇到不会的模块怎么办？遇到代码不会怎么办？


![在这里插入图片描述](https://img-blog.csdnimg.cn/20200511001045804.png)



![](https://img-blog.csdnimg.cn/20200511001207980.png)


# 4、学编程语言前，不了解Git，怎么入坑

上次教大家搭建好Python的两个IDE，分别是Pycharm和Jupyter

是不是我们正式开始写Python代码呢？

![](https://img-blog.csdnimg.cn/20200511102801436.png)

我的回答是**NO**


怎么了，环境安装好了不是就开始写吗？

这是不对的，学任何编程语言都要看下Git和Github

## 1、了解Git

说到Git，Runsen要说下LInux 的大神，是由伟大的Linux创始人Linus创作


就是这个大神，看不惯微软的window系统，就直接搞Linux。

![](https://img-blog.csdnimg.cn/20200511103241263.png)
我们回到Git。Git是一个分布式版本控制软件，在Git之前有一个SVN的东西，Linus在写LInux内核的时候，使用的是SVN进行代码提交。


Linus用SVN觉得不爽，就是因为SVN不能够分布式版本控制，这也是Git和最核心的区别

我先把git的官方网站的链接给你扔出来：https://git-scm.com/。


走，我们去Git的官方网站学习。

## 2、 版本控制


无论Git还是SVM都是用来版本控制，所谓的版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。 除了项目源代码，你可以对任何类型的文件进行版本控制。


![](https://img-blog.csdnimg.cn/20190801172329866.jpg)
比如，在我们写毕业论文时可能会遇到，多次修改之后的论文命名方式：

```text
论文_改.doc、论文_改改.doc、论文_改改改.doc、论文_改改改改.doc、论文_改改改改再改.doc、
论文_改改改改再改TM不改了.doc
```



我还是大三，还不用写论文。

重命名也太OUT了，SVN就出来，你可以提交多个版本，然后托管到代码仓库，进行管理，如果需要就回退。这方便了许多，但是如果这个写代码的跑路，要换Runsen来维护，那是不是没辙。因为这是托管到写代码的跑路人的仓库，我没得用啊。


接下来人们又遇到一个问题，如何让在不同系统上的开发者协同工作？ 于是，大神Linus发现。其实是LInus写Linux内核的时候，被逼无奈，花了2个星期用c写出了git。

Git是目前世界上最先进的分布式版本控制系统，解决了在不同系统上的开发者协同工作的问题。

## 3、Git安装


听我吹了这么久，是不是要安装Git开始学习了。再说了，我怎么会一直吹逼。



ubuntu下安装就是一行命令

```clike
sudo apt-get install git
```


centos下安装也是一行代码

```clike
sudo yum install git 
```


麻烦的就是Windows了，去git官网下，链接：https://git-scm.com/downloads


![](https://img-blog.csdnimg.cn/20200511110116465.png)


选择Window，然后下载安装包，选择路径，下面就是傻逼操作，



安装好了Git，你就可以看见Git GUI和GIT Bash。
![](https://img-blog.csdnimg.cn/20200511110358860.png)

出现这两个东西，基本安装成功了。


你在CMD窗口，执行Git，如果有反应就是OK 了。
、
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200511110645861.png)




没有就赶紧去path配置环境变量

![](https://img-blog.csdnimg.cn/20200511110622869.png)

## 4、创建本地仓库

下面，我教你创建一个文件夹用于存放项目文件，新建一个myporject的文件夹


```clike
cd ~/myproject/
```


初始化myporject的文件夹

```clike
git init
```

![](https://img-blog.csdnimg.cn/20200511111454107.png)

会创建一个.git的隐藏文件，关于版本控制的文件都存放在这里，绝对不要改动


![](https://img-blog.csdnimg.cn/20200511111521736.png?)


没有这东西，你的Git就不能用了。

## 5、配置个人信息

 你可以配置全局信息或者本项目个人信息



配置全局信息直接`--global `

```clike
git config --global user.name 'MaoliRunsen'
git config --global user.email '2953510364@qq.com'
```

配置信息会保存在家目录下，名字和Email跟注册Github的一致。


```clike
cat ~/.gitconfig
```


![](https://img-blog.csdnimg.cn/20200511111821813.png)

 配置本项目个人信息

```clike
git config user.name 'MaoliRunsen'
git config user.email '2953510364@qq.com'
```




 配置信息存储在当前目录下的.git/config下

```clike
cat .git/config

```


‘![](https://img-blog.csdnimg.cn/20200511112131423.png)

## 6、 添加文件

创建好了本地仓库，就准备开始开发了。

在项目文件加下创建readme.txt文件，输入以下内容。

```clike
我是Runsen，一个化工的专业的码农
这是一个git学习的项目。
将所有的博客进行汇总整理

```


先添加到暂存区

```clike
git add readme.txt


```

 提交到仓库

```clike
git commit -m '第一次提交文件'

```


![在这里插入图片描述](https://img-blog.csdnimg.cn/20200511112510924.png)


`git commit`命令的，-m参数后输入的内容是提交说明。命令执行成功后显示几个文件被改动，加了多少行。每提交一次就会生成一个版本。

`git add . `可以一次性把当前目录中所有有改动的文件都添加到暂存区。

## 7、修改文件

按照这个操作流程，修改readme.txt内容如下


```clike
我是Runsen，一个化工的专业的码农
这是一个git学习的项目。
将所有的博客进行汇总整理
然后删除之前Git的博客。

```

然后再次提交，Git add 和Git commit

## 8、错误提交


结果我在提交的时候，发现了commit错误了，这不是第一次提交，而是第二次，其实我是故意的。

辛勤的工作一段时候，我提交了2次了，有2个的版本，怎么查看这些提交记录呢？

git log是 查看历史版本


![](https://img-blog.csdnimg.cn/20200511113628514.png)




从上图中看到，我们需要删除第二次的Commit，如何删除呢，答案就是版本回退

## 9、 版本回退

这是就reset就可以了，

```clike
git reset --hard HEAD^

```


重要点终于来了：

- HEAD表示当前最新版本
- HEAD^表示当前最新版本的前一个版本
- HEAD^^表示当前最新版本的前两个版本，以此类推
- HEAD~1表示当前最新版本的前一个版本
- HEAD~8表示当前最新版本的前8个版本，以此类推


这是我们查看Git lo 就发现只有第一次的提交，可以看日期时间区别。

![](https://img-blog.csdnimg.cn/20200511114411272.png)



git reset --hard 版本号

当版本非常多时选择这种方法。版本号就是每次commit生成的hash值，只用取前几位数。

这是查看readdme.txt



![](https://img-blog.csdnimg.cn/20200511115705382.png)


没有了`然后删除之前Git的博客。`


这样就会产生一个问题，如果你提交错误和选择回退，这样你辛苦写的代码会消失。


因此，如果Commit错误了，回退是错误的办法。

## 10、回到原来版本

既然回退是错误，那么就需要回到原来最新版本，不然你写的代码全没了

只要上面的命令行窗口还没有被关掉，你就可以顺着往上找到上面最新的commit id是 af316a589238fffca87806ceed36a96992cf66b9，于是就可以指定回到未来的某个版本，只要前八个：af316a58


![](https://img-blog.csdnimg.cn/20200511121036962.png)

![](https://img-blog.csdnimg.cn/20200511121355806.png)

![](https://img-blog.csdnimg.cn/20200511121411904.png)

readdme就回到第二次的状态。

假如你是一个大傻逼，不小心关闭了窗口，就后悔了，想恢复到新版本怎么办？找不到新版本的commit id怎么办？


Git提供了一个命令git reflog用来记录你的每一次命令，然后你可以根据对应的commit id回到你想要的版本：


![](https://img-blog.csdnimg.cn/20200511121612698.png)


af316a58同样可以找的到。如果你删除了git的隐藏文件，那你真的凉凉了，回家睡觉去吧。

## 11、正确方法

上面都是演示一些git的常见错误，我们现在是回到了错误提交的commit上，所以还没有解决。



直接用git commit --amend 就可以了，修改本地最近一次已提交的注释

![](https://img-blog.csdnimg.cn/2020051112274258.png)



下面把第一次改为第二次，这是Vim的用法。

![在这里插入图片描](https://img-blog.csdnimg.cn/20200511122658437.png)


你再看看Git log，OK 解决。

![](https://img-blog.csdnimg.cn/20200511122830348.png)


每次在做一些大动作（rebasing）之前，建议备份整个版本库，以防万一。


git的历史记录是不可修改的，也就是说你不能更改任何已经发生的事情。你做的任何操作都只是在原来的操作上修改。也就是说，即使你删除了一个分支，修改了一个提交，或者强制重置，你仍然可以回滚这些操作。

## 12、 总结


今天简单了入了Git的坑，还没完，下面还是要继续把Git搞定，才能开始学习编程语言。

下篇的内容跟下图几张图有关。

![](https://img-blog.csdnimg.cn/20190801172352872.png)
![](https://img-blog.csdnimg.cn/20190801172403911.png)

# 5、开始Github和码云之旅，新手如何上路

上次大家一些Git的小知识，下面我们先开始Github之旅，再继续学习Git。

![](https://img-blog.csdnimg.cn/20200511154104470.png)

## 1、了解Github


我梦想这有女朋友问我：Git或GitHub到底是什么，它们之间有什么区别？


别睡了，孩子！没钱没身高没样子，简直就是又穷又丑又矮的典型，天天做白日梦？


梦想的女朋友：Git或GitHub到底是什么？

我：Git是一个跟踪代码更改的版本控制系统，而GitHub是一个基于Web的Git版本控制存储库托管服务。它提供了Git的所有分布式版本控制和源代码管理（SCM）功能，并提供了一些自己的特性。对于开发人员而言，这是他们可以在其中存储项目并与志趣相投的人建立联系的地方。您可以将其视为“代码云”。（百度百科）




![](https://img-blog.csdnimg.cn/20200511154654782.png)



其实，Github就是放代码的地方，通过Git来上传提交代码。

## 2、注册Github



百度搜索GitHub或者直接点击https://github.com/进入官网



![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051115501360.png)



注意每一个人都有自己的UserName，所以你创建Github的名字一定要亮，看起来很牛逼。


Email你可以使用国内的邮箱都是可以的，要用常用的，注册一个账号就是一个简单的事，


登录就可以看得自己的仓库和名字。
![](https://img-blog.csdnimg.cn/20200511155805204.png)

## 3、访问不了Github怎么办




访问Github突然上不去了，出现了网页无法正常运行？





![](https://img-blog.csdnimg.cn/20200511160126677.png)


你应该知道Github在外国，当然访问慢了。只要修改hosts，80%可以解决。

打开Dns检测|Dns查询 ，这里推荐站长工具

http://tool.chinaz.com/dns?type=1&host=github.com&ip=

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200511160714439.png)

.把检测列表里的TTL值最小的IP输入到hosts里，并对应写上github官网域名

下面是不同系统的hosts


```clike
Windows 系统位于 C:\Windows\System32\drivers\etc\
Android（安卓）系统hosts位于 /etc/
Mac（苹果电脑）系统hosts位于 /etc/
iPhone（iOS）系统hosts位于 /etc/
Linux系统hosts位于 /etc/
```




我这里使用Notepad++打开的，填写的是以前的hosts

![](https://img-blog.csdnimg.cn/20200511160405188.png)

如果你的Github真的访问不了，那用码云吧，码云是我国开发者为了打破Github垄断，仿照Github诞生的，网址：https://gitee.com/

## 4、了解一些项目页面



现在我找到一个Java项目，找到一个很多人点赞的Java项目，写的应该是教程，




![](https://img-blog.csdnimg.cn/20200511162353692.png)


如果你能够修复bug或自己添加功能 ，请发一个pull request吧！如果你提交了一个pull request，维护者就会将你的分支与已有的分支作比较来决定是否要合并。


不要想得不可能，我记得的有一个6岁的孩子pull request通过了，就是因为在注释中写了一个*号，可以显得更加严谨好看。

## 5、 在码云平台创建项目



虽然主要使用github最主流，但是国内访问速度慢，而且托管私有项目收费，国内一般使用码云gitee，国内访问速度快，-而且托管私有项目免费，- 小公司中使用gitlab或者码云来搭建。大厂有自己的项目托管仓库。






在码云和Github创建项目都是一样的，不管是是使用github还是使用码云，步骤是差不多的，区别是github是全英文的慢一点。这里我以码云为例。







![](https://img-blog.csdnimg.cn/20200511164043356.png)


然后由上往下输入你项目的名字、项目的描述，选择这个项目是不是公开(Public)或是作为私人项目(Private)。





![](https://img-blog.csdnimg.cn/2020051116441760.png)

创建成功后，之后会出现以下界面的信息。




![](https://img-blog.csdnimg.cn/20200511165134582.png)

创建好仓库后，你的仓库会有两个地址，一个是https，一个是ssh。因为使用https需要输入用户名和密码，推荐使用ssh的方式。要使用ssh你需要设置你账户的ssh公钥。
‘








下一步点击下载SSH，复制下来，也就是git@gitee.com:MaoliRUNsen/python_from_novice_to_master.git



远程仓库里已经存在项目文件，你买了台新电脑，需要将项目从远程仓库clone到本地进行工作。



在新电脑新建一个文件夹，再使用git clone git@gitee.com:MaoliRUNsen/python_from_novice_to_master.git克隆下来。
![](https://img-blog.csdnimg.cn/20200511165326630.png)

只要你克隆远程仓库，这样你就可以同步到码云。

## 6、Git创建项目

要把本地仓库和远程仓库联系起来有两种方式， 上面是第一种，另一种是通过Git创建项目


和第一种方式的区别在于先创建仓库，

 ```linux
  git init	# 创建仓库
  git remote add origin git@gitee.com:MaoliRUNsen/python_from_novice_to_master.git
 ```

## 7、推送到远程仓库


当本地工作完成，需要将代码推送到远程仓库，使用`git push`命令

```linux
git push origin master
```

push前需要add和commit

## 8、更新到本地仓库

你的同事和你协同开发，他工作的那部分内容完成了，并且已经推送到远程仓库，你接下来的工作需要依赖他的那部分代码，那么你需要将远程仓库代码拉取到本地仓库，使用`git pull`命令

```linux
git pull origin master
```

## 9、仓库成员管理

终于到了重点的时候，我们在新建项目的时候，只是写了基本设置


![](https://img-blog.csdnimg.cn/202005111719161.png)


仓库是需要管理，其实这也叫做项目管理。我们主要看仓库成员管理和部署公钥管理



| 成员角色         | 权限                     |
| ---------------- | ------------------------- |
| 访客（登录用户） | 对于公有仓库：创建 Issue、评论、Clone 和 Pull 仓库、打包下载代码、Fork 仓库、 Fork 仓库提交 Pull Request、下载附件 |
| 报告者           | 继承访客的权限。 私有仓库：不能查看代码、不能下载代码、不能 Push 、不能 Fork 、 不能提交 Pull Request、可下载附件，不能上传附件，不能删除附件 |
| 观察者           | 继承报告者权限 私有仓库：创建 Wiki、可以 Clone 下载代码、可以 Pull、不能 Fork |
| 开发者           | 创建 Issue、评论、Clone 和 Pull 仓库、Fork 仓库、打包下载代码、创建 Pull Request、 创建分支、推送分支、删除分支、创建标签（里程碑）、 创建 Wiki、可上传附件，可删除自己上传的附件，不能删除他人上传的附件、 |
| 管理员           | 创建 Issue、评论、Clone 和 Pull 仓库、打包下载代码、创建 Pull Request、 创建分支、推送分支、删除分支、创建标签（里程碑）、创建 Wiki、 添加仓库成员、强制推送分支、编辑仓库属性、可上传附件，可删除自己或他人上传的附件、 不能转移/清空/删除仓库 |



这里你直接可以邀请用户，注意这个和Fork是不一样的，Fork就是提交修改的请求，需要成员的同意。新建成员就可以同意提交修改的请求。

![](https://img-blog.csdnimg.cn/20200511172334850.png)

## 10、部署公钥管理

公钥是什么，就是管理这个项目的钥匙，一般都是项目成员有的。


SSH协议的Git服务，在使用SSH协议访问仓库仓库之前，需要先配置好账户/仓库的SSH公钥。


你需要用Git的SSH 创建Key，然后把这个key放在这个仓库中，一般针对是仓库不是你托管的，在别人平台，你也是项目的成员。




```clike
YIUYE@DESKTOP-5EEO47M MINGW64 ~
$ ssh-keygen -t rsa -C "2953510364@qq.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/YIUYE/.ssh/id_rsa):
/c/Users/YIUYE/.ssh/id_rsa already exists.
Overwrite (y/n)?

YIUYE@DESKTOP-5EEO47M MINGW64 ~
$ pwd
/c/Users/YIUYE

YIUYE@DESKTOP-5EEO47M MINGW64 ~
$ cd .ssh

YIUYE@DESKTOP-5EEO47M MINGW64 ~/.ssh
$ ls
id_rsa  id_rsa.pub  known_hosts

YIUYE@DESKTOP-5EEO47M MINGW64 ~/.ssh
$ cat id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC/bZaaJ9lO2a9AAuMWVpdsZfIVr4wqBA2vNAsButaNIMAx0OkYrfTloLl138+khQqteZ5b9lZdmiYEuAIS8UlBEdHmNo4LiJrLi4DdqOajpsbbdTmjCc4rlEraKOH2qVOTNEj6E+0oeYnnbQlGcA/nKdVbN8bfcsMWiN82Bjn19dP3LXC4oubRP2jWR/X3KyYcX58z1oltCbaIHtgRs1kFp6srFcU067CSmMulxmFXTalWkRSPq1d/gNWUYpii14YBIFUvwLmJlrUtXBcGZGqZhqu50FjpRcCY0TRV3DqZAR2/KnsRN7VeyuYCDmeXKc+UyNeS3zPFgKS7oyFi60CB 2953510364@qq.com

```


![](https://img-blog.csdnimg.cn/20200511173541967.png)



复制生成后的 ssh key，通过仓库主页 「管理」->「部署公钥管理」->「添加部署公钥」 ，添加生成的 public key 添加到仓库中。




![](https://img-blog.csdnimg.cn/20200511173830397.png)






添加后，在终端（Terminal）中输入

```clike
ssh -T git@gitee.com
```

首次使用需要确认并添加主机到本机SSH可信列表。若返回 Hi XXX! You've successfully authenticated, but Gitee.com does not provide shell access. 内容，则证明添加成功

![](https://img-blog.csdnimg.cn/20200511173932897.png)



部署公钥管理是针对不是你的项目而已，由于项目是我，做这个是没有任何意义的。

## 11、如何白嫖别人的资料



Github上有很多开源免费的资料，很多人为了Star就开源了很多学习资料，在我国都是分享学习资料比较多，比如我搜索Python

![](https://img-blog.csdnimg.cn/20200511174245742.png)



下面就有几千个学习资料，所以学东西最好在Github，然后你就下载下来，学习别人是怎么写代码。


![](https://img-blog.csdnimg.cn/20200511174408224.png)


还有很多人是为了找项目，在原始项目进行二次开发。白嫖的时候，请你注意版权。

## 12、文章推荐


我主要推荐的Github的help官方文档


https://help.github.com/en


![](https://img-blog.csdnimg.cn/20200511174803457.png)



Github就主要看企业的文档和Github的桌面版

![](https://img-blog.csdnimg.cn/20200511174951617.png)



Github的桌面版以后接着写，还有码云的help官方文档：https://gitee.com/help/

![](https://img-blog.csdnimg.cn/20200511175058983.png)
看不懂英文的，翻译也不对，那直接看码云的文档，和Github是基本一样的。

# 6、乘胜追击，将剩下的Git知识点搞定

@Author ： By Runsen
@Date： 2020/5/15


先上图回顾回顾
![](https://img-blog.csdnimg.cn/20190801172352872.png)
![](https://img-blog.csdnimg.cn/20190801172403911.png)

## 1、对比文件


![](https://img-blog.csdnimg.cn/2020051519080911.png)

我先通过git log 查看以前的信息。对比文件的命名很简单


```css
git diff HEAD HEAD^ -- 文件名
```

HEAD表示当前的版本，HEAD^ 表示上一个版本。
![](https://img-blog.csdnimg.cn/20200515190922878.png)

## 2、文件删除


删除没有添加进版本库中的工作区中的文件，那直接删除不用做任何操作。

如果已添加进工作区但没有提交的文件，先要先撤回工作区


比如，现在我写了一个`文件添加到版本库.txt`。


![](https://img-blog.csdnimg.cn/20200515191245233.png)



先提交下，git status 查看状态，绿色就是在版本库。



![](https://img-blog.csdnimg.cn/2020051519143026.png)
现在就是使用

```css
git reset HEAD

```


就可以撤销了，不行git status 查看状态，红色就是在工作区。


![](https://img-blog.csdnimg.cn/20200515191748504.png)


如果我已提交到版本库，突然间我发现写错了代码，老板看了，肯定扣我工资 ，不行，我赶紧要回来。

![](https://img-blog.csdnimg.cn/20200515192532376.png?)


去码云看看，发现存在了。现在怎么把这个文件撤回呢？

![](https://img-blog.csdnimg.cn/20200515192615841.png)


有人说，我直接去Github码云上删除，恩，是一种办法，而且是一个猪办法

![](https://img-blog.csdnimg.cn/20200515193131734.png)
如果项目不是在你的账号创建的，就没资格用客户端删东西。




答案就是回滚，再提交，只需要执行：



```css
git revert HEAD
git push
```


![](https://img-blog.csdnimg.cn/20200515193748656.png)




这时候就没有了
![](https://img-blog.csdnimg.cn/20200515193809887.png)

## 3、创建分支

正常的开发项目中都是多人协作，每个人的任务一般不会一天就完成，如果把没有完成的代码提交到远程仓库会影响被人工作。git提供了分支的功能就不用担心了，可以创建一个自己的分支，在上面干活，想提交就提交，等到工作完成再一次性合并到原来的分支。



新建git仓库时会默认创建一个分支master，它叫主分支。一般情况我们不会直接在主分支上干活，它主要用来发布版本。


我创建一个开发分支develop



```css
git branch develop
```


再切换到develop分支

```css
git checkout develop

```

‘
![](https://img-blog.csdnimg.cn/20200515194148130.png)

使用git branch命令查看当前分支。-b参数表示创建并切换。



如果想创建的时候，直接切换，直接-b参数


```css
git checkout-b  develop 

```

## 4、合并分支



创建好develop分支，菜比的我，24小时之后开发完毕，提交：


![](https://img-blog.csdnimg.cn/20200515194525171.png)




```css
$ git add .
$ git commit -m '24小时之后开发完毕'

```


![](https://img-blog.csdnimg.cn/20200515194625617.png)

现在切换到master


```css
$ git checkout master
Switched to branch 'master'
```


查看工作区，你会发现刚才写的文件没有了，不要惊慌，因为那个提交是在develop分支上，现在Runsne把develop分支的工作合并到master分支上：


![](https://img-blog.csdnimg.cn/20200515194803519.png)





```css
git merge develop

```





![](https://img-blog.csdnimg.cn/20200515194857226.png)



这个时候就出现了
![](https://img-blog.csdnimg.cn/20200515194917844.png)

## 5、删除分支




合并完之后你也可以删除掉develop分支：

```css
$ git branch -d develop
Deleted branch develop (was 25942c9)).
$ git branch
* master

```



![](https://img-blog.csdnimg.cn/20200515195109608.png)

OK搞定，把之前的Git文章全部删除


![](https://img-blog.csdnimg.cn/20200515195234117.png)

# 7、连Pycharm都不知道怎么用，学什么Python

@Date： 2020/5/16

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。


工欲善其事必先利其器，Pycharm 是最受欢迎的Python开发工具，它提供的功能非常强大，我尽量把自己用的都写写吧

## 1、设置Python 解释器



在任何项目，第一步就是设置Python 解释器，就是那个Python.exe


在File->Setting->Projec: xxx 下找到 Project Interpreter。然后修改为你需要的 Python 解释器。注意这个地方一定要注意的是：在选择 Python 解释器的时候，一定要选择到 python.exe 这个文件，而不是 python 的安装文件夹。





![](https://img-blog.csdnimg.cn/20200516114228617.png)








咋RunsenPycharm中设置了有anacodna的 python.exe ，有远程的python.exe，有直接下载的python.exe






![](https://img-blog.csdnimg.cn/20200516114610502.png)



本地和anaconda不说了，太他妈简单了，就说如何远程虚拟机吧，连接Docker，可能小白都不知道什么是Docker，以后在说吧

###  1.1 远程配置

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

## 2、调整字体及其大小

### 2.1 调整编辑器字体及其大小

所有的位置都是在Settings中，具体哪里看图

![](https://img-blog.csdnimg.cn/20200516121509710.png)

### 2.2 调整控制台的字体及其大小


![](https://img-blog.csdnimg.cn/20200516121815501.png)

## 3、设置编码


![](https://img-blog.csdnimg.cn/20200516121954173.png)

## 4、修改文件背景颜色

![](https://img-blog.csdnimg.cn/20200516122149105.png)

## 5、设置Git 和Github

### 5.1 配置git

Git的位置
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190510203756991.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)

### 5.2 配置github

![](https://img-blog.csdnimg.cn/20190510203845319.png)
现在就可以上传代码到github
![这里插入图片描述](https://img-blog.csdnimg.cn/20190510204021554.png)


上次代码到Github的Commit




![](https://img-blog.csdnimg.cn/20190510204131560.png)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20190510204224523.png)

![](https://img-blog.csdnimg.cn/2019051020425614.png)

### 5.3  下载仓库内容

![](https://img-blog.csdnimg.cn/20190510204438422.png)
![](https://img-blog.csdnimg.cn/20190510204645314.png)

## 6 、新建.py文件时默认添加信息



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

## 7、恢复代码


如果误删了代码，不要怕


![](https://img-blog.csdnimg.cn/20200516123222114.png)



![](https://img-blog.csdnimg.cn/202005161232476.png)

## 8、代码换行


写的代码多了，可以Soft--Wrap自动换行

![](https://img-blog.csdnimg.cn/20200516123356794.png)

## 9、Reformat Code

写的代码不够好看，直接Reformat

![](https://img-blog.csdnimg.cn/20200516123514734.png)

## 10、连接数据库

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

## 11、Debug




![](https://img-blog.csdnimg.cn/20200516124041537.png)

![](https://img-blog.csdnimg.cn/20200516124106239.png)




![](https://img-blog.csdnimg.cn/20200516124202661.png)


前面的信息就可以显示出来

## 12、PyCharm 常用快捷键


熟悉每个编辑器的快捷键，能大大提高你的工作效率。



![](https://img-blog.csdnimg.cn/2020051612295584.png)


![](https://img-blog.csdnimg.cn/202005161230082.png)


这里介绍了Pycharm的日常使用，关键就是不断地练习。

# 8、第一篇、小白看的 Python 基础教程，详细得很



本文是第一篇，一共四篇打下Python基础

@Author：Runsen

@Date：Writern By 2019/04/15 and supplied By 2020/3/31

@公众号：Python之王


一共四篇，声明下：Python的入门难度为0，比Java，C++根本不能比，你会英语基本没问题。

本文是第一篇

## 1、基本概念

### 1.1 四种类型

python中数有四种类型：整数、长整数、浮点数和复数。
　　

- 	整数， 如 1
- 	长整数 是比较大的整数
- 	浮点数 如 1.23、3E-2
- 	复数 如 1 + 2j、 1.1 + 2.2j

### 1.2 字符串

字符串（字符的序列）
　　

- 	python中单引号和双引号使用完全相同。
- 	使用三引号('''或""")可以指定一个多行字符串。
- 	转义符 `'\'`
- 	自然字符串， 通过在字符串前加r或R。 如` r"this is a line with \n"` 则`\n`会显示，并不是换行。
- 	python允许处理`unicode`字符串，加前缀u或U， 如 `u"this is an unicode string"`。
- 	字符串是不可变的。
- 	按字面意义级联字符串，如"this " "is " "string"会被自动转换为this is string。

### 1.3 标识符的命名

标识符的命名


- 	第一个字符必须是字母表中字母或下划线'_'。
- 	标识符的其他的部分有字母、数字和下划线组成。
- 	标识符对大小写敏感。

### 1.4 对象


　python程序中用到的任何“东西”都成为“对象”。

### 1.5 逻辑行和物理行


- 物理行：就是程序员所写代码的所在行。
- 逻辑行：是指源代码经过预编译后，代码所在的那一行。


Python假定每个物理行都对应着一个逻辑行。例如：print( "Hello World" ) 就是一个物理行，Python希望每行只有一个语句，因为这样看起来更加易读。

如果你想要在一个物理行中使用多于一个逻辑行，那么你需要使用分号（; ）来特别地标明这种用法。分号表示一个逻辑行/语句的结束。

例如：

```python
count = 5
print ( "count" )
```

与下面的语句等同：

```python
count = 5；
print ( "count" );
```

当然也可以写成下面这种：

```python
count = 5 ; print ( "count" );
```

甚至可以写成这样：

```python
count = 5 ; print ( "count" )
````

我们使用`\`的换行

```python
print \
("Runsen")
```

### 1.6 缩进

空白在python是非常重要的，行首的空白是最重要的，又称为缩进。行首的空白（空格和制表符）用来决定逻辑行的缩进层次，从而决定语句。

## 2、运算符与表达式

### 2.1 运算符与其用法

| 运算符 | 名称                                                        | 例子                                                         |
| ------ | ----------------------------------------------------------- | ------------------------------------------------------------ |
| +      | 两个对象相加                                                | 加法，如3 + 5得到8,字符也可以相加'a' + 'b'得到'ab'           |
| -      | 一个数减去另一个数                                          | 5 - 2得到3                                                   |
| *      | 乘	两个数相乘或是返回一个被重复若干次的字符串            | 2 * 3得到6,'a' * 3得到'aaa'                                  |
| \*\*   | 幂	返回x的y次幂                                          | 3 ** 4得到81（即3 * 3 * 3 * 3）                              |
| /      | 除	x除以y                                                | 4/3得到1（整数的除法得到整数结果）。4.0/3或4/3.0得到1.3333   |
| //     | 取整除	返回商的整数部分                                  | 4 // 3.0得到1.                                               |
| %      | 取模	返回除法的余数                                      | 8%3得到2。-25.5%2.25得到1.5                                  |
| <<     | 左移，把一个数的二进制左移一定数目，也就是在右边补多少个0， | 如	2 << 2得到8，二进制10变成1000                          |
| >>     | 右移	把一个数的比特向右移一定数目,也就是在右边删除位数   | 10>>2得到2，二进制1010变成10，直接删除后面2位                |
| &      | 按位与                                                      | 数的按位与	9 & 13得到9，二进制1001&1101，变成1001，两个值相应的位置都为1，那么该结果就是1，不然就是0 |
| \|     | 按位或                                                      | 数的按位或	5 \| 3得到7。二进制101&11，变成111，如果两个值相应的位置有一个是1,那么该结果就是1，也就是如果都是0，该结果就是0，101和11没有都是0，所以111 |
| ^      | 按位异或                                                    | 数的按位异或	5 ^ 3得到6，二进制101&11，变成110，两个值相应的位置相同,那么该结果就是0，也就是如果都是0或者都是1，该结果就是0，101和11，第一个都是1，所以110 |
| ~      | 按位翻转                                                    | x的按位翻转是-(x+1)	~5得到6                               |
| <      | 小于	返回x是否小于y。                                    | 所有比较运算符返回1表示真，返回0表示假。	5 < 3返回0（即False）而3 < 5返回1（即True）。还可以被任意连接：3 < 5 < 7返回True。 |
| >      | 大于	返回x是否大于y                                      | 5 > 3返回True。如果两个操作数需要都是数字                    |
| <=     | 小于等于	返回x是否小于等于y                              | x = 3; y = 6; x <= y返回True                                 |
| >=     | 大于等于	返回x是否大于等于y                              | x = 4; y = 3; x >= y返回True                                 |
| ==     | 等于	比较对象是否相等                                    | x = 2; y = 2; x == y返回True                                 |
| !=     | 不等于	比较两个对象是否不相等                            | x = 2; y = 3; x != y返回True。                               |
| not    | 布尔“非”	如果x为True，返回False                          | x = True; not y返回False。                                   |
| or     | 布尔“或”	如果x是True，它返回True，否则它返回y的计算值。  | x = True; y = False; x or y返回True                          |

### 2.2 运算符优先级

运算符优先级（从低到高）

| 运算符               | 描述             |
| -------------------- | ---------------- |
| lambda               | Lambda表达式     |
| or                   | 布尔“或”         |
| and                  | 布尔“与”         |
| not x                | 布尔“非”         |
| in，not in           | 成员测试         |
| is，is not           | 同一性测试       |
| <，<=，>，>=，!=，== | 比较             |
| `| `                 | 按位或           |
| ^                    | 按位异或         |
| `| `                 | 按位或           |
| &                    | 按位与           |
| <<，>>               | 移位             |
| +，-                 | 加法与减法       |
| *，/，%              | 乘法、除法与取余 |
| +x，-x               | 正负号           |
| ~x                   | 按位翻转         |
| **                   | 指数             |
| ~x                   | 按位翻转         |
| x.attribute          | 属性参考         |
| x[index]             | 下标             |
| x[index:index]       | 寻址段           |
| f(arguments...)      | 函数调用         |
| (experession,...)    | 绑定或元组显示   |
| [expression,...]     | 列表显示         |
| {key:datum,...}      | 字典显示         |
| 'expression,...'     | 字符串           |

### 2.3 输出

python 控制台输出 使用print

```python
print ("abc"  )　　#打印abc并换行
print ("abc%s" % "d"  )　　#打印abcd
print ("abc%sef%s" % ("d", "g")  )　　#打印abcdefg
```

## 3、控制流

### 3.1 if 语句

```python
i = 10
n = int(input("enter a number:"))

if n == i:
    print( "equal")
elif n < i:
    print( "lower")
else:
    print ("higher")
```

### 3.2 while语句

```python
while True:
    pass
else:
    pass
#else语句可选，当while为False时，else语句被执行。 pass是空语句。
```

for 循环 for..in

```python
for i in range(0, 5):
    print (i)
else:
    pass
# 打印0到4
```

注：当for循环结束后执行else语句；
`range(a, b)返回一个序列，从a开始到b为止，但不包括b，range默认步长为1，可以指定步长，range(0,10,2)；`

### 3.3 break语句

终止循环语句，如果从for或while中终止，任何对应循环的else将不执行。

### 3.4 continue语句

continue语句用来调过当前循环的剩余语句，然后继续下一轮循环。

下面就是 break 和 continue 主要的 区别：

- break：跳出整个循环
- continue：跳出本次循环，继续执行下一次循环
  希望大家牢记。

## 4、函数

函数通过def定义。def关键字后跟函数的标识符名称，然后跟一对圆括号，括号之内可以包含一些变量名，该行以冒号结尾；接下来是一块语句，即函数体。

```python
def sumOf(a, b):
    return a + b
```

### 4.1  函数形参

函数中的参数名称为‘形参’，调用函数时传递的值为‘实参’

### 4.2 局部变量

在函数内定义的变量与函数外具有相同名称的其他变量没有任何关系，即变量名称对于函数来说是局部的。这称为变量的作用域。

`global语句， 为定义在函数外的变量赋值时使用global语句。`


```python
def func():
    global x
    print( "x is ", x)
    x = 1

x = 3
func()
print(x)
#3
#1 
```

### 4.3 默认参数


通过使用默认参数可以使函数的一些参数是‘可选的’。

```python　　
def say(msg, times =  1):
    print(msg * times)

say("Runsen")
say("Runsen", 3)
```

注意：只有在形参表末尾的那些参数可以有默认参数值，即不能在声明函数形参的时候，先声明有默认值的形参而后声明没有默认值的形参，只是因为赋给形参的值是根据位置而赋值的。

### 4.4 关键参数

如果某个函数有很多参数，而现在只想指定其中的部分，那么可以通过命名为这些参数赋值（称为‘关键参数’）。
优点：不必担心参数的顺序，使函数变的更加简单；假设其他参数都有默认值，可以只给我们想要的那些参数赋值。

```python
def func(a, b=2, c=3):
    print ("a is %s, b is %s, c is %s") % (a, b, c)

func(1) #a is 1, b is 2, c is 3
func(1, 5) #a is 1, b is 5, c is 3
func(1, c = 10) #a is 1, b is 2, c is 10
func(c = 20, a = 30) #a is 30, b is 2, c is 20
```

### 4.5 return 语句

　return语句用来从一个函数返回，即跳出函数。可从函数返回一个值。
　没有返回值的return语句等价于return None。None表示没有任何东西的特殊类型。

### 4.6  文档字符串

`__doc__`   (文档字符串)

```python
def func():
    '''This is self-defined function
	Do nothing
	'''
    pass

print(func.__doc__)

#This is self-defined function
#
#Do nothing
```

## 5、模块

模块就是一个包含了所有你定义的函数和变量的文件，模块必须以.py为扩展名。模块可以从其他程序中‘输入’`(import)`以便利用它的功能。

在python程序中导入其他模块使用'import', 所导入的模块必须在sys.path所列的目录中，因为sys.path第一个字符串是空串''即当前目录，所以程序中可导入当前目录的模块。

### 5.1 字节编译的.pyc文件


导入模块比较费时，python做了优化，以便导入模块更快些。一种方法是创建字节编译的文件，这些文件以.pyc为扩展名。

pyc是一种二进制文件，是py文件经编译后产生的一种byte code，而且是跨平台的（平台无关）字节码，是有python虚拟机执行的，类似于


java或.net虚拟机的概念。pyc的内容，是跟python的版本相关的，不同版本编译后的pyc文件是不同的。

### 5.2  from .. import

如果想直接使用其他模块的变量或其他，而不加'模块名+.'前缀，可以使用from .. import。

例如想直接使用sys的argv，from sys import argv 或 from sys import *

### 5.3 模块的__name__


每个模块都有一个名称，py文件对应模块名默认为py文件名，也可在py文件中为__name__赋值；如果是__name__，说明这个模块被用户

### 5.4 dir()函数

dir(sys)返回sys模块的名称列表；如果不提供参数，即dir()，则返回当前模块中定义名称列表。

 ### 5.5 del

del -> 删除一个变量/名称，del之后，该变量就不能再使用。

## 6、数据结构

python有三种内建的数据结构：列表、元组和字典。

###  6.1 列表

list是处理一组有序项目的数据结构，列表是可变的数据结构。列表的项目包含在方括号[]中，

eg: [1, 2, 3]， 空列表[]。判断列表中是否包含某项可以使用in， 

比如 l = [1, 2, 3]; print 1 in l; #True；

支持索引和切片操作；索引时若超出范围，则IndexError；

使用函数len()查看长度；使用del可以删除列表中的项，eg: del l[0] # 如果超出范围，则IndexError
　　　　
list函数如下：

```python　　　　
append（value）　　---向列表尾添加项value
l = [1, 2, 2]
l.append(3) #[1, 2, 2, 3]

count(value)　　---返回列表中值为value的项的个数
l = [1, 2, 2]
print( l.count(2)) # 2

extend(list2)　　---向列表尾添加列表list2
l = [1, 2, 2]
l1 = [10, 20]
l.extend(l1)
print (l )  #[1, 2, 2, 10, 20]

index(value, [start, [stop]])　　---返回列表中第一个出现的值为value的索引，如果没有，则异常 ValueError

l = [1, 2, 2]
a = 4
try:
    print( l.index(a))
except ValueError, ve:
    print( "there is no %d in list" % a
　　　　insert(i, value))　　---向列表i位置插入项vlaue，如果没有i，则添加到列表尾部

l = [1, 2, 2]

l.insert(1, 100)
print l #[1, 100, 2, 2]

l.insert(100, 1000)
print l #[1, 100, 2, 2, 1000]

pop([i])　　---返回i位置项，并从列表中删除；如果不提供参数，则删除最后一个项；如果提供，但是i超出索引范围，则异常IndexError

l = [0, 1, 2, 3, 4, 5]

print( l.pop()) # 5
print( l) #[0, 1, 2, 3, 4]

print( l.pop(1)) #1
print( l) #[0, 2, 3, 4]

try:
    l.pop(100)
except IndexError, ie:
    print( "index out of range")

remove(value)　　---删除列表中第一次出现的value，如果列表中没有vlaue，则异常ValueError

l = [1, 2, 3, 1, 2, 3]

l.remove(2)
print (l )#[1, 3, 1, 2, 3]

try:
    l.remove(10)
except ValueError, ve:
    print ("there is no 10 in list")

reverse()　　---列表反转

l = [1, 2, 3]
l.reverse()
print (l) #[3, 2, 1]

sort(cmp=None, key=None, reverse=False)　　---列表排序

l5 = [10, 5, 20, 1, 30]
l5.sort()
print( l5) #[1, 5, 10, 20, 30]

l6 = ["bcd", "abc", "cde", "bbb"]
l6.sort(cmp = lambda s1, s2: cmp(s1[0],s2[1]))
print( l6) #['abc', 'bbb', 'bcd', 'cde']

l7 = ["bcd", "abc", "cde", "bbb", "faf"]
l7.sort(key = lambda s: s[1])
print (l7) #['faf', 'abc', 'bbb', 'bcd', 'cde']
```

# 9、第二篇、小白看的 Python 基础教程，详细得很

﻿


本文是第二篇

@Author：Runsen

@公众号：Python之王

### 6.2 元组

tuple和list十分相似，但是tuple是不可变的，即不能修改tuple，元组通过圆括号中用逗号分割的项定义。

- 支持索引和切片操作
- 可以使用 in查看一个元素是否在tuple中。
- 空元组()
- 只含有一个元素的元组("a",) #需要加个逗号

优点：tuple比list速度快；对不需要修改的数据进行‘写保护’，可以是代码更安全

`tuple与list可以相互转换，使用内置的函数list()和tuple()。`

```python
l = [1, 2, 3]
print( l )# [1, 2, 3]

t = tuple(l)
print(t) # (1, 2, 3)

l = list(t)
print (l) #[1, 2, 3]
```

元组最通常的用法是用在打印语句，如下例：

```python
name = "Runsen"
age = 20
print( "Name: %s; Age: %d") % (name, age)
# Name: Runsen; Age: 20
```

**函数如下：**

- count(value)　　

返回元组中值为value的元素的个数

```python
t = (1, 2, 3, 1, 2, 3)
print (t.count(2) )# 2
```

- index(value, [start, [stop]])　　

返回列表中第一个出现的值为value的索引，如果没有，则异常 `ValueError`



```python
t = (1, 2, 3, 1, 2, 3)
print( t.index(3) )# 2
try:
    print (t.index(4))
except ValueError as V:
    print(V)  # there is no 4 in tuple
```

### 6.3 字典

字典由键值对组成，键必须是唯一的；

eg: `d = {key1:value1, key2:value2}；`

空字典用{}表示；字典中的键值对是没有顺序的，如果想要一个特定的顺序，那么使用前需要对它们排序；

`d[key] = value`，如果字典中已有`key`，则为其赋值为`value`，否则添加新的键值对`key/value`；

使用`del d[key] `可以删除键值对；判断字典中是否有某键，可以使用in 或 not in；


```python
d = {}
d["1"] = "one"
d["2"] = "two"
d["3"] = "three"

del d["3"]

for key, value in d.items():
    print ("%s --> %s" % (key, value))
#1 --> one
#2 --> two
```

**dict函数如下:**

- clear()　

删除字典中所有元素

```python
d1 = {"1":"one", "2":"two"}
d1.clear()
print (d1 )# {}
```

- copy()　

返回字典的一个副本(浅复制)

```python
d1 = {"1":"one", "2":"two"}
d2 = d1.copy()
print( d2 )#{'1': 'one', '2': 'two'}

print(d1 == d2) # True
print(d1 is d2) # False
```

浅复制值相同，但是对象不同，内存地址不同。



- dict.fromkeys(seq,val=None) 

创建并返回一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值(默认为None)

```python
l = [1, 2, 3]
t = (1, 2, 3)
d3 = {}.fromkeys(l)
print (d3) #{1: None, 2: None, 3: None}

d4 = {}.fromkeys(t, "default")
print(d4) #{1: 'default', 2: 'default', 3: 'default'}
```

- get(key,[default])　　

返回字典dict中键key对应值，如果字典中不存在此键，则返回default的值(default默认值为None)

```python
d5 = {1:"one", 2:"two", 3:"three"}
print (d5.get(1) )#one
print (d5.get(5)) #None
print (d5.get(5, "test") )#test

```

- has_key(key)　　


判断字典中是否有键key

```python
d6 = {1:"one", 2:"two", 3:"three"}
print( d6.has_key(1) ) #True
print (d6.has_key(5))  #False

```

- items()　　


返回一个包含字典中(键, 值)对元组的列表

```python
d7 = {1:"one", 2:"two", 3:"three"}
for item in d7.items():
    print (item)
#(1, 'one')
#(2, 'two')
#(3, 'three')

for key, value in d7.items():
    print ("%s -- %s" % (key, value))
#1 -- one
#2 -- two
#3 -- three

```

- keys()　


返回一个包含字典中所有键的列表

```python
d8 = {1:"one", 2:"two", 3:"three"}

for key in d8.keys():
    print (key)
#1
#2
#3

```

- values()　


返回一个包含字典中所有值的列表

```python
d8 = {1:"one", 2:"two", 3:"three"}
for value in d8.values():
    print( value)
#one
#two
#three

```

- pop(key, [default])　　



若字典中key键存在，删除并返回dict[key]，若不存在，且未给出default值，引发KeyError异常

```python
d9 = {1:"one", 2:"two", 3:"three"}
print (d9.pop(1) )#one
print( d9) #{2: 'two', 3: 'three'}
print( d9.pop(5, None)) #None
try:
    d9.pop(5)  # raise KeyError
except KeyError, ke:
    print ( "KeyError:", ke) #KeyError:5

```

- popitem()　　


删除任意键值对，并返回该键值对，如果字典为空，则产生异常KeyError

```python
d10 = {1:"one", 2:"two", 3:"three"}

print (d10.popitem() ) #(1, 'one')
print (d10)  #{2: 'two', 3: 'three'}

```

- setdefault(key,[default])　　


若字典中有key，则返回vlaue值，若没有key，则加上该key，值为default，默认None

```python
d = {1:"one", 2:"two", 3:"three"}

print (d.setdefault(1))  #one
print (d.setdefault(5))  #None
print( d)  #{1: 'one', 2: 'two', 3: 'three', 5: None}
print (d.setdefault(6, "six")) #six
print (d)  #{1: 'one', 2: 'two', 3: 'three', 5: None, 6: 'six'}

```

- update(dict2)　


把dict2的元素加入到dict中去，键字重复时会覆盖dict中的键值

```python
d = {1:"one", 2:"two", 3:"three"}
d2 = {1:"first", 4:"forth"}

d.update(d2)
print (d)  #{1: 'first', 2: 'two', 3: 'three', 4: 'forth'}

```

- viewitems()　　


返回一个view对象，（key, value）pair的列表，类似于视图。优点是，如果字典发生变化，view会同步发生变化。在
迭代过程中，字典不允许改变，否则会报异常

```python
d = {1:"one", 2:"two", 3:"three"}
for key, value in d.viewitems():
    print ("%s - %s" % (key, value))
#1 - one
#2 - two
#3 - three

```

- viewkeys()　　


返回一个view对象，key的列表

```python
d = {1:"one", 2:"two", 3:"three"}
for key in d.viewkeys():
    print( key)
#1
#2
#3

```

- viewvalues()　

返回一个view对象，value的列表

```python
d = {1:"one", 2:"two", 3:"three"}
for value in d.viewvalues():
    print (value)
#one
#two
#three

```

### 6.4 序列

序列类型是指容器内的元素从0开始的索引顺序访问，一次可以访问一个或者多个元素；列表、元组和字符串都是序列。
序列的三个主要特点是

- 索引操作符和切片操作符
- 索引可以得到特定元素
- 切片可以得到部分序列


**索引操作符和切片操作符**

```python
numbers = ["zero", "one", "two", "three", "four"]
  
print (numbers[1] )# one
print (numbers[-1] )# four
#print( numbers[5]) # raise IndexError
print (numbers[:]) # ['zero', 'one', 'two', 'three', 'four']
print (numbers[3:]) # ['three', 'four']
print (numbers[:2]) # ['zero', 'one']
print (numbers[2:4] )# ['two', 'three']
print (numbers[1:-1] )# ['one', 'two', 'three'] 

```


切片操作符中的第一个数（冒号之前）表示切片开始的位置，第二个数（冒号之后）表示切片到哪里结束。 

如果不指定第一个数，Python就从序列首开始。如果没有指定第二个数，则Python会停止在序列尾。 

注意，返回的序列从开始位置 开始 ，刚好在结束位置之前 结束。即开始位置是包含在序列切片中的，而结束位置被排斥在切片外。 可以用负数做切片。负数用在从序列尾开始计算的位置。

# 10、第三篇、小白看的 Python 基础教程，详细得很

﻿

本文是第三篇

@Author：Runsen

@公众号：Python之王


上面两个基本搞定了Python中数据结构，下面花一篇讲讲最重要的类。

## 7、面向对象编程

万物皆是对象，Python当然支持面向对象编程。类和对象是面向对象编程的两个主要方面，类创建一个新的对象，对象是这个类的实例。

对象可以使用类的变量，属于对象或类的变量被称为域；对象也可以使用属于类的函数，这样的函数称为类的方法；域和方法可以合称为类的属性。


域有两种类型

- 属于实例的
- 属于类本身

它们分别被称为实例变量和类变量。类使用关键字`class`创建，类的域和方法被列在一个缩进块中。

类的方法必须有一个额外的第一个参数，但是在调用时不为这个参数赋值，这个特殊变量指对象本身，按照惯例它的名称是self，类似Java中的this。


在类中下面两个特都方法需要注意：

- `__init__`方法：在类的一个对象被创建时调用该方法；相当于c++中的构造函数，就是当这个类调用了，那么这个`__init__ `方法就要执行。

- `__del__`方法：在类的对象被销毁时调用该方法；相当于c++中的析构函数。在使用del删除一个对象时也就调用`__del__`方法，`__del__`是最后调用的。

Python中所有的类成员(包括数据成员)都是public的，没有Java的私有类，也就是人人都有调用类，虽然编写变成很简单，
但是资源人人都可以随意分配访问，在项目中确实一个不好的东西。

但是Python 类的却有私有变量和私有方法之说，这个是一个例外，如果使用的数据成员以双下划线为前缀，则为私有变量。

你实例化这个类，访问不了。这是很多人忽略 的


比如：

```python
class public():
    _name = 'protected类型的变量'
    __info = '私有类型的变量'
    def _f(self):
        print("这是一个protected类型的方法")
    def __f2(self):
        print('这是一个私有类型的方法')
    def get(self):
        return(self.__info)
pub = public()
# 先打印可以访问的
print(pub._name)
pub._f()
####结果如下####
protected类型的变量
这是一个protected类型的方法


# 打印下类 私有变量和私有方法
print(pub.__info)
报错：'public' object has no attribute '__info'
pub._f2()
报错：pub._f2()
```

但是私有属性和方法可以在同一个类中被调用

```python
pub.get()
#######
'私有类型的变量'
```


上面是很多人不知道的，下面，我来声明一个Person类


```python　
   
class Person():
    Count = 0
    def __init__(self, name, age):
        Person.Count += 1
        self.name = name
        self.__age = age
    
p = Person("Runsen", 20)

print(p.Count)

# 1 说明我实例化，这个__init__方法就要执行


print(p.name) #Runsen
print (p.__age) 
#AttributeError: Person instance has no attribute '__age'
#私有变量访问不了，报错
```

## 8、继承

面向对象编程 (OOP)，英语全称：Object Oriented Programming，面向对象编程的一个主要功能就是“继承”。继承是指这样一种能力：它可以使用现有类的所有功能，并在无需重新编写原来的类的情况下对这些功能进行扩展。

继承，其实这样理解，就是我写了一个爸爸类和儿子类，爸爸有钱，儿子却没钱，于是儿子决定继承爸爸，调用爸爸的钱（爸爸类的变量和方法）。

继承一个类，基本使用下面的五个方法。

### 8.1 直接调用父类属性方法；

爸爸有钱，儿子却没钱，于是儿子用爸爸的钱

```python
class Father():
    def __init__(self):
        self.money= 1000 
    def action(self):
        print('调用父类的方法')
 
class Son(Father):
    pass
 
son=Son()     # 子类Son 继承父类Father的所有属性和方法
son.action()  # 调用父类属性
输出：调用父类的方法
son.money     # 调用父类属性
输出：1000
```

### 8.2 强制调用父类私有属性方法；

爸爸说，你这个儿子，老是用我的钱，我决定藏私房钱。儿子试试`super()`拿你的私房钱，但是这里需要注意`super()`强制调用父类私有属性方法，就是重写方法，私有变量是不能用supper继承不了，还不可以访问父类中的私有属性方法的变量，就是儿子是拿不了私房钱的。


```python
class Father():
    __money  = 1000 #私有变量是继承不了
    
    def __action(self):  # 父类的私有方法
        money = 1000
        print('调用父类的方法')
 
class Son(Father):
        
    def action(self):
        super()._Father__action()
        print(money) 
        
son=Son()
son.action() 

调用父类的方法
name 'money' is not defined
```

### 8.3 重写父类属性方法；

突然间儿子竟然有钱，决定不用爸爸的钱，用自己的钱，决定重写父类属性方法。

```python
class Father():
    def __init__(self):
        self.money = 0
    
    def action(self):
        print('调用父类的方法')
 
class Son(Father):
    def __init__(self):
        self.money = 1000
      
    def action(self):
        print('子类重写父类的方法')
 
son=Son()     # 子类Son继承父类Father的所有属性和方法
son.action()  # 子类Son调用自身的action方法而不是父类的action方法
son.money     # 自己的1000
```

### 8.4 调用父类的__init__方法

如果爸爸把钱放在`__init__`，儿子有没有可能拿到爸爸的钱，都不是私有变量，就不是私房钱，当然可以拿到


我们先看看如果不用super，能不能拿到。

```python
class Father():
    def __init__(self):
        self.money = 1000
 
class Son(Father):
    def __init__(self):
        pass
    
son=Son()
print(son.money)

# 报错：'Son' object has no attribute 'money'

```

连super不用就像拿钱，太小看你爸爸我了。


```python
class Father():
    def __init__(self):
        self.money = 1000
 
class Son(Father):
    def __init__(self):
        super().__init__()
        #也可以用 Father.__init__(self)  这里面的self一定要加上(上面两个相同)
        
        
son=Son()
print(son.money) 

1000
```

### 8.5 继承父类初始化过程中的参数

有的时候，爸爸需要挣钱和花钱，就是我们初始化过程中的参数，儿子很好奇，决定看看爸爸口袋还要多少钱。

我们这里先写死了earn_money和spend_money

```python
class Father():
    def __init__(self):
        self.earn_money=1000
        self.spend_money= -500
 
class Son(Father):
    def __init__(self):
        super().__init__()
        #也可以用 Father.__init__(self)  这里面的self一定要加上
        
    def add(self):
        return self.earn_money+self.spend_money
        
        
son=Son()
print(son.add())

500

```


儿子发现爸爸钱不够，于是偷偷的拿了点钱过来。

```python
class Father():
    def __init__(self,a,b):
        self.earn_money = a
        self.spend_money= b
    def add(self):
        return self.a + self.b
 
#调用父类初始化参数a,b并增加额外参数c
class Son(Father):
    def __init__(self,a,b,c=1000):  # c固定值
        Father.__init__(self,a,b)  
        self.son_money = c
        
    def add(self):
        return self.earn_money+self.spend_money + self.son_money
        
   
        
son=Son(1000,-500)   # 所以c可以不用显示表达出来
print(son.add())     # 调用子类add函数

1500

```


以上基本涵盖了Python类的继承，调用父类的属性和方法基础内容，可以自己动手写些案例，加深理解。

## 9、输入/输出

程序与用户的交互需要使用输入/输出，主要包括控制台和文件；对于控制台可以使用input和print。input(xxx)输入xxx，
然后读取用户的输入并返回。

```python
In [1]: input()
1
Out[1]: '1'

```

## 10、文件输入/输出

可以使用file类打开一个文件，使用file的read、readline和write来恰当的读写文件。对文件读写能力取决于打开文件时使用的模式，
常用模式

- 读模式("r")
- 写模式("w")
- 追加模式("a")



文件操作之后需要调用close方法来关闭文件。如果用with open就不用slose了。

还有r+，w+，a+


- r：仅仅表示读入
- r+：既可以读取还可以写入
- w: 仅仅表示写入
- w+：既可以读取还可以写入


但r+与w+不同的是，不会把原先存在txt中的东西清空，下面是他们的对比，反正尽量用a+，基本没什么错报出来。


| 描述                 | r+       | w+       | a+                       |
| -------------------- | -------- | -------- | ------------------------ |
| 当前文件不存在时文件 | 抛出异常 | 创建文件 | 创建文件                 |
| 打开后原文件内容     | 保留     | 清空     | 保留                     |
| 初始位置             | 0        | 0        | 文件尾                   |
| 写入位置             | 标记位置 | 标记位置 | **写入时默认跳至文件尾** |


补充个例子吧：



```python
test = '''\
This is a program about file I/O.
Author: Runsen
Date: 2020/3/31
'''
f = open("test.txt", "w") 
f.write(test) 
f.close() 

f = open("test.txt") #默认r
while True:
    line = f.readline()
    if len(line) == 0:  
        break
    print(line)
f.close()

######
This is a program about file I/O.

Author: Runsen

Date: 2020/3/31

```

## 11、存储器

存储器，大家应该不知道。python提供一个标准的模块，成为pickle，使用它可以在一个文件中存储任何python对象，之后可以完整的取出来，这被称为持久地存储对象；还有另外一个模块成为cPickle，它的功能和pickle完全一样，只不过它是用c写的，要比pickle速度快(大约快1000倍)。


```python
import pickle

datafile = "data.data"

mylist = ["Runsen", "is", "20"]

f = open("test.txt", "wb+")
pickle.dump(mylist, f)
f.close()

del mylist

f = open(datafile,'rb+')
mylist = pickle.load(f)

print(mylist)
#["Runsen", "is", "20"]

```

## 12、异常


当程序中出现某些异常的状况时，异常就发生了。

python中可以使用`try ... except `处理。


```python
try:
    print (1/0)
except ZeroDivisionError as e:
    print(e)
except:
    print( "error or exception occurred.")

#integer division or modulo by zero

```

# 11、最后一篇，小白看的Python基础教程，详细得很

﻿


@Author：Runsen

## 13、Python标准库


Python标准库是随Pthon附带安装的，包含了大量极其有用的模块。


我们主要了解下sys和os就够了。

### 13.1 sys模块　　

sys模块主要是针对与Python解释器相关的变量和方法，不是主机操作系统。



```python
sys.argv    #获取命令行参数列表，第一个元素是程序本身
sys.exit(n) #退出Python程序，exit(0)表示正常退出。当参数非0时，会引发一个SystemExit异常，可以在程序中捕获该异常
sys.version #获取Python解释程器的版本信息
sys.maxsize #最大的Int值，64位平台是2**63 - 1
sys.path    #返回模块的搜索路径，初始化时使用PYTHONPATH环境变量的值
sys.platform    #返回操作系统平台名称
sys.stdin   #输入相关
sys.stdout  #输出相关
sys.stderr  #错误相关
sys.exc_info()  #返回异常信息三元元组
sys.getdefaultencoding()    #获取系统当前编码，默认为utf-8
sys.setdefaultencoding()    #设置系统的默认编码
sys.getfilesystemencoding() #获取文件系统使用编码方式，默认是utf-8
sys.modules #以字典的形式返回所有当前Python环境中已经导入的模块
sys.builtin_module_names    #返回一个列表，包含所有已经编译到Python解释器里的模块的名字
sys.copyright   #当前Python的版权信息
sys.flags   #命令行标识状态信息列表。只读。
sys.getrefcount(object) #返回对象的引用数量
sys.getrecursionlimit() #返回Python最大递归深度，默认1000
sys.getsizeof(object[, default])    #返回对象的大小
sys.getswitchinterval() #返回线程切换时间间隔，默认0.005秒
sys.setswitchinterval(interval) #设置线程切换的时间间隔，单位秒
sys.getwindowsversion() #返回当前windwos系统的版本信息
sys.hash_info   #返回Python默认的哈希方法的参数
sys.implementation  #当前正在运行的Python解释器的具体实现，比如CPython
sys.thread_info #当前线程信息
```


上面是sys模块所有语法，我们看看就够了，了解下sys.argv和sys.path就足够了



sys.argv是一个脚本执行参数列表，列表的第一个元素是脚本名称，从第二个元素开始才是真正的参数。


```python
# test.py
import sys

for index, arg in enumerate(sys.argv):
    print("第%d个参数是： %s" % (index, arg))

#输出
第0个参数是： test.py
第1个参数是： 1
第2个参数是： 2
第3个参数是： 3
第4个参数是： 4 
```


argv：获取程序外部向程序传递的参数



```python
#  script.py

import sys
print(sys.argv[0])
print(sys.argv[1])
```

运行：

```python
# python script.py argv1
sys.py
argv1
```



sys.path


path是一个目录列表，供Python从中查找模块。在Python启动时，sys.path根据内建规则和PYTHONPATH变量进行初始化。sys.path的第一个元素通常是个空字符串，表示当前目录。

```python
>>> sys.path
['', 'C:\\Python36\\Lib\\idlelib', 'C:\\Python36\\python36.zip', 'C:\\Python36\\DLLs', 'C:\\Python36\\lib', 'C:\\Python36', 'C:\\Python36\\lib\\site-packages']
```

sys.path本质上是一个列表，可以进行append、insert、pop、remove等各种列表相关的操作，但通常都进行append操作，添加自己想要的查找路径。


sys.stdin、sys.stdout、sys.stderr


- stdin用于所有的交互式输入（包括input()函数）。
- stdout用于print()的打印输出或者input()函数的提示符。
- stderr用于解释器自己的提示信息和错误信息。

简而言之，这三个属性就是操作系统的标准输入、输出和错误流，它们返回的都是一个“文件类型”对象，支持read()、write()和flush()等操作。



```python
>>> import sys
>>> s = sys.stdin.readline()        
i don't like python
>>> s
'i don't like python\n'
>>> sys.stdout.write(s)
i don't like python 
20
```





python3中sys.stdin与input的区别：

input()方法和stdin()类似，不同的是input()括号内可以直接填写说明文字。

```python
s = input('Please input something！')

print('Please input something！',)  # 逗号表示不换行
s = sys.stdin.readline()[:-1]  # -1 抛弃输入流中的'\n' 换行符
```


当我们print(obj)的时候，事实上是调用了sys.stdout.write(obj+'\n')，将内容打印到控制台（默认是显示器），然后追加一个换行符。以下两行等价：



```python
sys.stdout.write('hello'+'\n') 
print('hello')
```

### 13.2 os模块　　

该模块包含普遍的操作系统功能

- os.name字符串指示你正在使用的平台。比如对于Windows，它是'nt'，而对于Linux/Unix用户，它是'posix'

- os.getcwd()函数得到当前工作目录，即当前Python脚本工作的目录路径
- os.getenv()和os.putenv()函数分别用来读取和设置环境变量
- os.listdir()返回指定目录下的所有文件和目录名
- os.remove()函数用来删除一个文件
- os.system()函数用来运行shell命令
- os.linesep字符串给出当前平台使用的行终止符。例如，Windows使用'\r\n'，Linux使用'\n'而Mac使用'\r'
- os.sep 操作系统特定的路径分割符
- os.path.split()函数返回一个路径的目录名和文件名
- os.path.isfile()和os.path.isdir()函数分别检验给出的路径是一个文件还是目录
- os.path.existe()函数用来检验给出的路径是否真地存在

## 14、类中的特别方法




| 名称                  | 说明                                               |
| --------------------- | -------------------------------------------------- |
| __init__(self,...)    | 这个方法在新建对象恰好要被返回使用之前被调用。     |
| __del__(self)         | 恰好在对象要被删除之前调用。                       |
| __str__(self)         | 在我们对对象使用print语句或是使用str()的时候调用。 |
| __getitem__(self,key) | 使用x[key]索引操作符的时候调用。                   |
| __len__(self)         | 对序列对象使用内建的len()函数的时候调用。          |



下面的类中定义了上表中的方法：

```python
class Array:
    __list = []

    def __init__(self):
        print "constructor"

    def __del__(self):
        print "destructor"

    def __str__(self):
        return "this self-defined array class"

    def __getitem__(self, key):
        return self.__list[key]

    def __len__(self):
        return len(self.__list)

    def Add(self, value):
        self.__list.append(value)

    def Remove(self, index):
        del self.__list[index]

    def DisplayItems(self):
        print "show all items----"
        for item in self.__list:
            print item

arr = Array()   #constructor
print(arr)    #this self-defined array class
print(len(arr))   #0
arr.Add(1)
arr.Add(2)
arr.Add(3)
print(len(arr))   #3
print(arr[0])   #1
arr.DisplayItems()
#show all items----
#1
#2
#3
arr.Remove(1)
arr.DisplayItems()
#show all items----
#1
#3
#destructor

```

## 15、列表推导式



通过列表综合，可以从一个已有的列表导出一个新的列表。

```python
list1 = [1, 2, 3, 4, 5]
list2 = [i*2 for i in list1 if i > 3]

print(list1)  #[1, 2, 3, 4, 5]
print(list2)  #[8, 10]

```

## 16、 *和**args区别




当函数接收元组或字典形式的参数的时候，有一种特殊的方法，使用*和**前缀。

该方法在函数需要获取可变数量的参数的时候特别有用。
　


由于在args变量前有*前缀，所有多余的函数参数都会作为一个元组存储在args中。如果使用的是**前缀，多余的参数则会被认为是一个字典的键/值对。


 *args接受元组

**args接受字典



```python
def powersum(power, *args):
    total = 0
    for i in args:
        total += pow(i, power)
    return total

print (powersum(2, 1, 2, 3))  

#14 1^2+2^2+3^2 = 14


def displaydic(**args):
    for key,value in args.items():
        print( "key:%s;value:%s" % (key, value))

displaydic(a="one", b="two", c="three")


#key:a;value:one
#key:c;value:three
#key:b;value:two

```

## 17、lambda函数

lambda语句被用来创建新的函数对象，并在运行时返回它们。lambda需要一个参数，后面仅跟单个表达式作为函数体，而表达式的值被这个


新建的函数返回。 注意，print语句也不能用在lambda形式中，只能使用表达式。

```python
func = lambda s: s * 3
print(func("Runsen "))  # Runsen Runsen Runsen


func2 = lambda a, b: a * b

print(func2(2, 3))  #6

```

## 18、exec/eval



exec语句用来执行储存在字符串或文件中的Python语句


eval语句用来计算存储在字符串中的有效Python表达式。




```python　　　　
cmd = "print 'hello world'"
exec cmd   #hello world

expression = "10 * 2 + 5"
print(eval(expression))    #25

```


exec还批量创建变量，这个大家可能忽视



```python
for i in range(8):
    exec('v' + str(i) + ' = ' + str(i))
    print('v' + str(i) + ':', eval('v' + str(i)))
    
v0: 0
v1: 1
v2: 2
v3: 3
v4: 4
v5: 5
v6: 6
v7: 7
    

```

## 19、assert


assert语句用来断言某个条件是真的，并且在它非真的时候引发一个错误--AssertionError。

```python
>>> assert True     # 条件为 true 正常执行
>>> assert False    # 条件为 false 触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError

```


assert一般和try except连用

```python
flag = True

assert flag == True

try:
    assert flag == False
except AssertionError:
    print ("failed")
else:
    print ("pass")
    
    
failed

```

## 20、repr

repr函数用来取得对象的规范字符串表示。

注意，在大多数时候有eval(repr(object)) == object。

可以通过定义类的__repr__方法来控制对象在被repr函数调用的时候返回的内容。

```python
arr = [1, 2, 3]
print(arr)    #[1, 2, 3]
print(repr(arr))    #[1, 2, 3]

```

其实Python就是这么简单，学Python就是看官方文档，看demo，代码跟做英语阅读似的，多看官方文档，然后调下第三方库，实现需求就行了。

# 12、深入Python列表和元组

﻿

## 什么是列表和元组



列表是动态的，长度大小不固定，可以随意地增加、删减或者改变


而元组是静态的，长度大小固定，无法增加删减或者改变


定义列表和函数

```python
l = [1, 2, 'hello', 'world'] # 列表中同时含有 int 和 string 类型的元素
l
[1, 2, 'hello', 'world']

tup = ('jason', 22) # 元组中同时含有 int 和 string 类型的元素
tup
('jason', 22)

```


对于列表来说，由于其是动态的，我们只需简单地在列表末尾，加入

对于元组来说，实际上就是创建了一个新的元组，然后把原来两个元组的值依次填充.




```python
tup = (1, 2, 3, 4)
new_tup = tup + (5, ) # 创建新的元组 new_tup，并依次填充原元组的值
new _tup
(1, 2, 3, 4, 5)

l = [1, 2, 3, 4]
l.append(5) # 添加元素 5 到原列表的末尾
l
[1, 2, 3, 4, 5]

```

Python 中的列表和元组都支持负数索引，列表和元组都支持切片操作


```python
l = [1, 2, 3, 4]
l[-1]
4

tup = (1, 2, 3, 4)
tup[-1]
4


list = [1, 2, 3, 4]
l[1:3] # 返回列表中索引从 1 到 2 的子列表
[2, 3]

tup = (1, 2, 3, 4)
tup[1:3] # 返回元组中索引从 1 到 2 的子元组
(2, 3) 

```

## 列表和元组常见的内置函数


```python
l = [3, 2, 3, 7, 8, 1]
l.count(3) 
2
l.index(7)
3
l.reverse()
l
[1, 8, 7, 3, 2, 3]
l.sort()
l
[1, 2, 3, 3, 7, 8]

tup = (3, 2, 3, 7, 8, 1)
tup.count(3)
2
tup.index(7)
3
list(reversed(tup))
[1, 8, 7, 3, 2, 3]
sorted(tup)
[1, 2, 3, 3, 7, 8]

```

## 列表和元组存储方式

```python
l = []
l.__sizeof__() // 空列表的存储空间为 40 字节
40
l.append(1)
l.__sizeof__() 
72 // 加入了元素 1 之后，列表为其分配了可以存储 4 个元素的空间 (72 - 40)/8 = 4
l.append(2) 
l.__sizeof__()
72 // 由于之前分配了空间，所以加入元素 2，列表空间不变
l.append(3)
l.__sizeof__() 
72 // 同上
l.append(4)
l.__sizeof__() 
72 // 同上
l.append(5)
l.__sizeof__() 
104 // 加入元素 5 之后，列表的空间不足，所以又额外分配了可以存储 4 个元素的空间

```

元组的初始化速度，要比列表快 5 倍。

```python
python3 -m timeit 'x=(1,2,3,4,5,6)'
20000000 loops, best of 5: 9.97 nsec per loop
python3 -m timeit 'x=[1,2,3,4,5,6]'
5000000 loops, best of 5: 50.1 nsec per loop
```




因此如果存储的数据和数量不变，选择元组


如果存储的数据或数量是可变的，选择列表



下面有两种方法创建列表，哪个初始化更快，运行时间更快。

```python
# 创建空列表
# option A
empty_list = list()

# option B
empty_list = []

```

![](https://img-blog.csdnimg.cn/20190523000342208.png)

测试结果，虽然直接创建元组初始化速度最快，但是由于要用list函数转一道反而不如直接创建列表的速度快。

# 13、深入Python字典和集合

## 字典和集合

字典是一系列无序元素的组合，其长度大小可变，元素可以任意地删减和改变。不过要注意，这里的元素，是一对键（key）和值（value）


相比列表和元组，字典的性能更优，特别是对于查找、添加和删除，字典都能在常数的时间复杂度内完成


而集合和字典基本相同，唯一的区别，就是集合没有键和值的配对是一系列无序的、唯一的元素组合。

```python
d1 = {'name': 'jason', 'age': 20, 'gender': 'male'}
d2 = dict({'name': 'jason', 'age': 20, 'gender': 'male'})
d3 = dict([('name', 'jason'), ('age', 20), ('gender', 'male')])
d4 = dict(name='jason', age=20, gender='male') 
d1 == d2 == d3 ==d4
True

s1 = {1, 2, 3}
s2 = Set([1, 2, 3])
s1 == s2
True

```

集合并不支持索引操作，因为集合本质上是一个哈希表，和列表不一样

```和集合
s = {1, 2, 3}
s[0]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'set' object does not support indexing
```

想要判断一个元素在不在字典或集合内，我们可以用 value  in dict/set

```和集合
s = {1, 2, 3}
1 in s
True
10 in s
False

d = {'name': 'Runsen', 'age': 20}
'name' in d
True
'location' in d
False

```

**字典的增删改**

```和集合
In [1]: d = {'name': 'Runsen', 'age': 20}^M
   ...:

In [2]: d['gender'] = 'male'

In [3]: d['birthday'] = '1999-10-01'

In [4]: d
Out[4]: {'name': 'Runsen', 'age': 20, 'gender': 'male', 'birthday': '1999-10-01'}

In [5]: d['birthday'] = '1999/10/01'

In [6]: d.pop('birthday')
Out[6]: '1999/10/01'

In [8]: d
Out[8]: {'name': 'Runsen', 'age': 20, 'gender': 'male'}


In [9]: s = {1, 2, 3}^M
   ...:

In [10]: s.add(4)

In [11]: s
Out[11]: {1, 2, 3, 4}

In [12]: s.remove(4)

In [13]: s
Out[13]: {1, 2, 3}****

```

**字典的升序和降序排序**

```和集合
d = {'b': 1, 'a': 2, 'c': 10}
d_sorted_by_key = sorted(d.items(), key=lambda x: x[0]) # 根据字典键的升序排序
d_sorted_by_value = sorted(d.items(), key=lambda x: x[1]) # 根据字典值的升序排序
d_sorted_by_key
[('a', 2), ('b', 1), ('c', 10)]
d_sorted_by_value
[('b', 1), ('a', 2), ('c', 10)]
```

## 增删查找

字典和集合是进行过性能高度优化的数据结构，特别是对于查找、添加和删除操作


**列表的做法**

```和集合
# list version
def find_unique_price_using_list(products):
    unique_price_list = []
    for _, price in products: # A
        if price not in unique_price_list: #B
            unique_price_list.append(price)
    return len(unique_price_list)

# products id 和 price
products = [
    (143121312, 100), 
    (432314553, 30),
    (32421912367, 150),
    (937153201, 30)
]
print('number of unique price is: {}'.format(find_unique_price_using_list(products)))

# 输出
number of unique price is: 3
```


**集合的做法**



```python
# set version
def find_unique_price_using_set(products):
    unique_price_set = set()
    for _, price in products:
        unique_price_set.add(price)
    return len(unique_price_set)        

products = [
    (143121312, 100), 
    (432314553, 30),
    (32421912367, 150),
    (937153201, 30)
]
print('number of unique price is: {}'.format(find_unique_price_using_set(products)))

# 输出
number of unique price is: 3
```

比较运行的时间，也就是性能

```python
import time
id = [x for x in range(0, 100000)]
price = [x for x in range(200000, 300000)]
products = list(zip(id, price))

# 计算列表版本的时间
start_using_list = time.perf_counter()
find_unique_price_using_list(products)
end_using_list = time.perf_counter()
print("time elapse using list: {}".format(end_using_list - start_using_list))
## 输出
time elapse using list: 41.61519479751587


# 计算集合版本的时间
start_using_set = time.perf_counter()
find_unique_price_using_set(products)
end_using_set = time.perf_counter()
print("time elapse using set: {}".format(end_using_set - start_using_set))
# 输出
time elapse using set: 0.008238077163696289
```


在性能上集合完爆列表



对于字典，哈希表存储了哈希值，键和值这桑三个元素

![](https://img-blog.csdnimg.cn/20190523142853281.png)





字典和集合都是无序的数据结构，其内部的哈希表存储结构，保证了查找，插入，删除操作的高效性。所以，字典和集合通常运用在对元素的查找，去重




初始化字典的方式有两种方法，比较下哪一种更高效，

```python
In [20]: timeit a ={'name':"runsen",'age':20}
127 ns ± 0.8 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)

In [21]: timeit b =dict({'name':"runsen",'age':20})
438 ns ± 3.41 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

```

第一种，因为不用调用相关的函数


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS83NjUxNjE3Yy1hMWM0LTRjMGEtYjkyNC04YmMxMzk3NTAwODkucG5n?x-oss-process=image/format,png)


字典的键可以是一个列表吗？下面这段代码中，字典的初始化是否正确

```python
In [22]: d = {'name': 'Runsen', ['education']: [' primary school', 'junior middle school']}^M
    ...:
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-22-13cd196aef11> in <module>
----> 1 d = {'name': 'Runsen', ['education']: [' primary school', 'junior middle school']}

TypeError: unhashable type: 'list'

In [23]: d = {'name': 'Runsen', ('education'): [' primary school', 'junior middle school']}^M
    ...:
    ...:

In [24]: d
Out[24]: {'name': 'Runsen', 'education': [' primary school', 'junior middle school']}


```

用列表作为 Key 在这里是不被允许的，因为列表是一个动态变化的数据结构，字典当中的 key 要求是不可变的，原因也很好理解.

key 首先是不重复的，如果 Key 是可以变化的话，那么随着 Key 的变化，这里就有可能就会有重复的 Key，那么这就和字典的定义相违背；如果把这里的列表换成之前我们讲过的元组是可以的，因为元组不可变。

# 14、深入Python条件和循坏

## 条件控制

简单来说：当判断的条件为真时，执行某种代码逻辑，这就是条件控制。


那么在讲条件控制之前，可以给大家讲一个程序员当中流传的比较真实的一个例子

说有一天一个程序员，他的媳妇让他去出去买两个包子，那出去之前，他媳妇这么跟他说的，说老公你出去给我买两个包子
，如果看见卖西瓜的就买一个回来。

结果这个程序员回来了，买一个包子。结果媳妇给他一顿揍。
![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS8zZmYzYThiNy1mMzU1LTQ5YTgtYWRhZi1mNTkzZjc3YWI5ZGQucG5n?x-oss-process=image/format,png)


然后问他为啥，你为啥就买一个包子回来？，他回答他媳妇说我看见了卖西瓜的，所以买了一个包子。

其实这个就是条件控制一个典型的，一个生活化的一个说明场景


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS85YTdjMWVhZS1lNmU0LTQyODUtOWZjMS05ZTFjYjBlZThmYmQucG5n?x-oss-process=image/format,png)

## 条件语句


条件控制就是我们常见的的if else



```python
# y = |x|
if x < 0:
    y = -x
else:
    y = x

```

在条件语句后面加上 冒号：

python不支持switch语句，但是支持elif

```python
if condition_1:
    statement_1
elif condition_2:
    statement_2
...
elif condition_i:
    statement_i
else:
    statement_n

```

不少人喜欢省略半段的条件，就像这样

```python
if s: # s is a string
    ...
if l: # l is a list
    ...
if i: # i is an int
    ...
... 

```

![](https://img-blog.csdnimg.cn/2019052409161133.png)

## 循环语句


一般通过for循环和while循环实现

```python
l = [1, 2, 3, 4]
for item in l:
    print(item)
1
2
3
4

```


在python数据结构只要时可迭代对象，如列表，集合，等等，就可以遍历

```python
for item in <iterable>:
    ...

```

但是字典本身只有键时课迭代的，如何要遍历字典的值和键值对，要通过内置的函数values() 和items()  实现

```python
d = {'name': 'jason', 'dob': '2000-01-01', 'gender': 'male'}
for k in d: # 遍历字典的键
    print(k)
name
dob
gender

for v in d.values(): # 遍历字典的值
    print(v)
jason
2000-01-01
male    

for k, v in d.items(): # 遍历字典的键值对
    print('key: {}, value: {}'.format(k, v))
key: name, value: jason
key: dob, value: 2000-01-01
key: gender, value: male 

```

当然可以通过索引来遍历元素

```python
l = [1, 2, 3, 4, 5, 6, 7]
for index in range(0, len(l)):
    if index < 5:
        print(l[index])        
        
1
2
3
4
5

```

别忘了还有一个更重要的enumerate() 函数

```python
l = [1, 2, 3, 4, 5, 6, 7]
for index, item in enumerate(l):
    if index < 5:
        print(item)  
              
1
2
3
4
5

```

在循环语句中，要通过continue 或break 一起使用


continue，就是让程序跳过当前这层循环，继续执行下面的循环



break 则是指完全跳出所在的整个循环体


现在找出价格小于1000，颜色不是红色的产品名称和颜色组合，如果不用continue

```python
# name_price: 产品名称 (str) 到价格 (int) 的映射字典
# name_color: 产品名字 (str) 到颜色 (list of str) 的映射字典
for name, price in name_price.items():
    if price < 1000:
        if name in name_color:
            for color in name_color[name]:
                if color != 'red':
                    print('name: {}, color: {}'.format(name, color))
        else:
            print('name: {}, color: {}'.format(name, 'None'))


```

共用了5层for 或if 的嵌套

加上了continue，只有3层

```python
# name_price: 产品名称 (str) 到价格 (int) 的映射字典
# name_color: 产品名字 (str) 到颜色 (list of str) 的映射字典
for name, price in name_price.items():
    if price >= 1000:
        continue
    if name not in name_color:
        print('name: {}, color: {}'.format(name, 'None'))
    for color in name_color[name]:
        if color == 'red':
            continue
        print('name: {}, color: {}'.format(name, color))


```


while

```python
l = [1, 2, 3, 4]
index = 0
while index < len(l):
    print(l[index])
    index += 1


```


那么在什么场合使用for和continue

如果只是遍历已知的集合，找出满足条件的元素，使用for更加的简洁

如果需要在满足某个条件前，要不停的重复操作，并且没有特定的集合来遍历


例如

```python
while True:
    try:
        text = input('Please enter your questions, enter "q" to exit')
        if text == 'q':
            print('Exit system')
            break
        ...
        ...
        print(response)
    except as err:
        print('Encountered error: {}'.format(err))
        break 


```


for 循环和while循环的效率问题

```python
i = 0
while i < 1000000
    i += 1

for i in range(0, 1000000):
    pass



```

range（）函数直接时C语言写的，调用的速度非常快，for循环的效率更高



对于有些大神直接写成一行操作

```python
expression1 if condition else expression2 for item in iterable


```

分解成

```python
for item in iterable:
    if condition:
        expression1
    else:
        expression2


```


如何没有else

```python
expression for item in iterable if condition


```


现在绘制 y = 2*|x| + 5 的函数图像


只需一行

```python
y = [value * 2 + 5 if x > 0 else -value * 2 + 5 for value in x]


```

在处理字符串时，将文件逐行读取，按照逗号分隔单词，去掉首位空字符，过滤小于3的单词，最后返回单词组成的列表

```python
text = ' Today,  is, Sunday'
text_list = [s.strip() for s in text.split(',') if len(s.strip()) > 3]
print(text_list)
['Today', 'Sunday']


```

给定两个列表 x、y，要求返回 x、y 中所有元素对组成的元组

```python
[(xx, yy) for xx in x for yy in y if x != y]


```


```python
l = []
for xx in x:
    for yy in y:
        if x != y:
            l.append((x, y))


```



# 15、深入Python输入和输出



﻿

在很多时候，你会想要让你的程序与用户（可能是你自己）交互。你会从用户那里得到输入，然后打印一些结果。我们可以使用iinput和print语句来完成这些功能。

## input

```python
name = input('your name:')
gender = input('you are a boy?(y/n)')

###### 输入 ######
your name:Jack
you are a boy?

welcome_str = 'Welcome to the matrix {prefix} {name}.'
welcome_dic = {
    'prefix': 'Mr.' if gender == 'y' else 'Mrs',
    'name': name
}

print('authorizing...')
print(welcome_str.format(**welcome_dic))

########## 输出 ##########
authorizing...
Welcome to the matrix Mr. Jack.

```

input函数暂停运行，等待键盘输入，直到按下回车，输入的类型永远时字符串



```python
a = input()
1
b = input()
2

print('a + b = {}'.format(a + b))
########## 输出 ##############
a + b = 12
print('type of a is {}, type of b is {}'.format(type(a), type(b)))
########## 输出 ##############
type of a is <class 'str'>, type of b is <class 'str'>
print('a + b = {}'.format(int(a) + int(b)))
########## 输出 ##############
a + b = 3

```

## 文件输入和输出

生产级别的 Python 代码，大部分 I/O 则来自于文件

这里有个in.text

```python
Mr. Johnson had never been up in an aerophane before and he had read a lot about air accidents, so one day when a friend offered to take him for a ride in his own small phane, Mr. Johnson was very worried about accepting. Finally, however, his friend persuaded him that it was very safe, and Mr. Johnson boarded the plane.

His friend started the engine and began to taxi onto the runway of the airport. Mr. Johnson had heard that the most dangerous part of a flight were the take-off and the landing, so he was extremely frightened and closed his eyes.

After a minute or two he opened them again, looked out of the window of the plane, and said to his friend。

"Look at those people down there. They look as small as ants, don't they?"

"Those are ants," answered his friend. "We're still on the ground."
```

现在

- 读取文件
- 去掉所有标点和换行符，将大写变为小写
- 合并相同的词，统计每个词出现的频率，将词频从大到小排序
- 将结果按行输出文件out.txt

```python
import re

# 你不用太关心这个函数
def parse(text):
    # 使用正则表达式去除标点符号和换行符
    text = re.sub(r'[^\w ]', '', text)

    # 转为小写
    text = text.lower()
    
    # 生成所有单词的列表
    word_list = text.split(' ')
    
    # 去除空白单词
    word_list = filter(None, word_list)
    
    # 生成单词和词频的字典
    word_cnt = {}
    for word in word_list:
        if word not in word_cnt:
            word_cnt[word] = 0
        word_cnt[word] += 1
    
    # 按照词频排序
    sorted_word_cnt = sorted(word_cnt.items(), key=lambda kv: kv[1], reverse=True)
    
    return sorted_word_cnt

with open('in.txt', 'r') as fin:
    text = fin.read()

word_and_freq = parse(text)

with open('out.txt', 'w') as fout:
    for word, freq in word_and_freq:
        fout.write('{} {}\n'.format(word, freq))

########## 输出 (省略较长的中间结果) ##########



```

![](https://img-blog.csdnimg.cn/20190523215923502.png)



但是有个问题，如果文件非常的大容易造成内存奔溃

这个时候给 read 指定参数 size，还可以通过 readline() 函数，每次读取一行，

## json文件读取


```python
import json

params = {
    'symbol': '123456',
    'type': 'limit',
    'price': 123.4,
    'amount': 23
}

params_str = json.dumps(params)

print('after json serialization')
print('type of params_str = {}, params_str = {}'.format(type(params_str), params))

original_params = json.loads(params_str)

print('after json deserialization')
print('type of original_params = {}, original_params = {}'.format(type(original_params), original_params))

########## 输出 ##########

after json serialization
type of params_str = <class 'str'>, params_str = {'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}
after json deserialization
type of original_params = <class 'dict'>, original_params = {'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}

```

json.dumps() 这个函数，接受 Python 的基本数据类型 字典，然后转化string （json的字符串）

json.loads() 这个函数，接受一个合法字符串(json)，然后 转化为字典

**json 的读入**

```python
import json

params = {
    'symbol': '123456',
    'type': 'limit',
    'price': 123.4,
    'amount': 23
}

with open('params.json', 'w') as fout:
    params_str = json.dump(params, fout)

with open('params.json', 'r') as fin:
    original_params = json.load(fin)

print('after json deserialization')
print('type of original_params = {}, original_params = {}'.format(type(original_params), original_params))

########## 输出 ##########

after json deserialization
type of original_params = <class 'dict'>, original_params = {'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}

```



# 16、深入Python字符串

## 什么字符串

字符串是由独立字符组成的一个序列，通常包含在单引号（‘ ’），双引号（”“）

三引号（''' '''）


```python
s1 = 'hello'
s2 = "hello"
s3 = """hello"""
s1 == s2 == s3
True

```

三引号字符串常用于函数的注释

```python
def calculate_similarity(item1, item2):
    """
    Calculate similarity between two items
    Args:
        item1: 1st item
        item2: 2nd item
    Returns:
      similarity score between item1 and item2
    """

```

## 转义字符

用 \ 开头的字符串，来表示一些特定意义的字符

```python
s = 'a\nb\tc'
print(s)
a
b	  c

len(s)
5
```

代码中的'\n'，表示一个字符——换行符；'\t'也表示一个字符，四个空格

字符 a，换行，字符 b，然后制表符，最后打印字符 c
最后打印的输出横跨了两行，但是整个字符串 s 仍然只有 5 

## 常用操作

```python
name = 'jason'
name[0]
'j'
name[1:3]
'as'


for char in name:
    print(char)   
j
a
s
o
n


```

注意python的字符串是不可变的


```python
s = 'hello'
s[0] = 'H'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment

```

只能通过船创建新的字符串

```python
s = 'H' + s[1:]
s = s.replace('h', 'H')

```


在java 中有可变的字符串，StringBuilder  ，每次改变字符串，无需创建新的字符串，时间复杂度为O（1） 

但是在python中如果想要改变字符串，往往需要O（n)的时间复杂度，n是新字符串的长度

## 拼接字符串

```python
str1 += str2  # 表示 str1 = str1 + str2

# 这个时间复杂度是多少
s = ''
for n in range(0, 100000):
    s += str(n)

```

在python2中总的时间复杂度就为 O(1) + O(2) + … + O(n) = O（n^2)

但是在python3中 str1 += str2 首先会检测str1 是否有其他的引用

所以在python3中时间复杂度是O（n）





```python
l = []
for n in range(0, 100000):
    l.append(str(n))
l = ' '.join(l) 

```

由于列表的 append 操作是 O(1) 复杂度，时间复杂度为 n*O(1)=O(n)。

## split分割

```python
def query_data(namespace, table):
    """
    given namespace and table, query database to get corresponding
    data         
    """

path = 'hive://ads/training_table'
namespace = path.split('//')[1].split('/')[0] # 返回'ads'
table = path.split('//')[1].split('/')[1] # 返回 'training_table'
data = query_data(namespace, table) 

```

- string.strip(str)，表示去掉首尾的 str 
- tring.lstrip(str)，表示只去掉开头的 str
- string.rstrip(str)，表示只去掉尾部的 str


在读入文件时候，如果开头和结尾都含有空字符，就采用strip函数

```python
s = ' my name is jason '
s.strip()
'my name is jason'


```

## 格式化


format

```python
print('no data available for person with id: {}, name: {}'.format(id, name))

```



```python
print('no data available for person with id: %s, name: %s' % (id, name))


```

**%s 表示字符串型，%d 表示整型**




**两种字符串拼接操作，哪个更好**

```python
s = ''
for n in range(0, 100000):
    s += str(n)


```

```python
l = []
for n in range(0, 100000):
    l.append(str(n))
    
s = ' '.join(l)


```

对于上面的两种拼接操作，计算运行时间



```python
# 第一个 +=
import time
start_time  =time.perf_counter()
s = ''
for n in range(0,1000000):
    s += str(n)
end_time = time.perf_counter()
# 5.7604558070000005
print(end_time - start_time)
# 第二个 join
import time
start_time  =time.perf_counter()
s = []
for n in range(0,1000000):
    s.append(str(n))
''.join(s)
end_time = time.perf_counter()
# 0.622547053
print(end_time - start_time)



# 第三个 map
import time
start_time = time.perf_counter()
s = ''.join(map(str, range(0, 1000000)))
end_time = time.perf_counter()
# 0.403433529
print(end_time - start_time)


```


结果：

- 对于数据量大的map好过join，join好过 +=


- 对于数据量小的map 好过 += 好过join


![](https://img-blog.csdnimg.cn/2019052315133017.png)

# 17、深入Python异常处理

﻿@Author：BY Runsen

## 异常处理

在Python 中的错误和异常是什么？

通常来说，程序中的错误至少包括两种，一种是语法错误，另一种则是异常。所谓语法错误，你应该很清楚，也就是你写的代码不符合编程规范，无法被识别与执行，比如下面这个例子的语法错误

下面的代码无法被识别和执行

```python
if name is not None
    print(name)
```

If 语句漏掉了冒号，不符合 Python 的语法规范，所以程序就会报错invalid syntax。


异常则是指程序的语法正确，也可以被执行，但在执行过程中遇到了错误，抛出了异常

```python
10 / 0
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: integer division or modulo by zero

order * 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'order' is not defined

1 + [1, 2]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'int' and 'list'

```

常见的报错是ZeroDIvision NameError 和 typeError

还有很多其他异常的类型如keyError 字典的键找不到和FileNotFoundError 文件不存在



如何处理异常，通常是用try except来解决

```python
try:
    s = input('please enter two numbers separated by comma: ')
    num1 = int(s.split(',')[0].strip())
    num2 = int(s.split(',')[1].strip())
    ... 
except ValueError as err:
    print('Value Error: {}'.format(err))

print('continue')

```

如果我们输入a,b，程序便会抛出异常invalid literal for int() with base 10:'a'

```python
please enter two numbers separated by comma: a,b
Value Error: invalid literal for int() with base 10: 'a'
continue
```

大型社交网站的后台，需要针对用户发送的请求返回相应记录。用户记录往往储存在 key-value 结构的数据库中，每次有请求过来后，我们拿到用户的 ID，并用 ID 查询数据库中此人的记录，就能返回相应的结果。而数据库返回的原始数据，往往是 json string 的形式，这就需要我们首先对 json string 进行 decode（解码），你可能很容易想到下面的方法：



```python
import json
raw_data = queryDB(uid) # 根据用户的 id，返回相应的信息
data = json.loads(raw_data)

```

上面的代码是不是就足够呢？

json.loads()函数中，如果输入的字符串不符合规范，那么就无法解码，就会抛出异常


因此写之前就应该考虑如何处理异常

```python
try:
    data = json.loads(raw_data)
    ....
except JSONDecodeError as err:
    print('JSONDecodeError: {}'.format(err))

```





# 18、深入Python函数

﻿@Author ：By Runsen

## 函数

在Python中的函数就是为了实现某一段功能的代码段，可以重复利用。

就是以后不要重复造轮子，遇到那个场景就用那个函数，就是函数式编程


下面，我定义一个 my_func，传入一个Hello World，再打印一个Hello World

```python
def my_func(message):
    print('Got a message: {}'.format(message))

# 调用函数 my_func()
my_func('Hello World')
# 输出
Got a message: Hello World
```

简单的知识点


- def是函数的声明
- my_func是函数的名称
- message 是函数的参数
- print 是函数的主体部分
- 在函数的最后 可以返回调用结果（return 或yield ），也可以不返回




定义在前，调用在后


```python
def my_sum(a, b):
    return a + b

result = my_sum(3, 5)
print(result)

# 输出
8

```



对于函数的参数可以设定默认值

```python
def func(param = 0):
    ...

```

如果param没有传入，那么参数默认是0，如果传入了参数，就覆盖默认值

## 多态


传入的参数可以接受任何数据类型


比如，列表

```python
print(my_sum([1, 2], [3, 4]))

# 输出
[1, 2, 3, 4]

```

再比如，字符串

```python
print(my_sum('hello ', 'world'))

# 输出
hello world

```

当然，如果参数数据类型不同，而两者无法相加

```
print(my_sum([1, 2], 'hello'))
TypeError: can only concatenate list (not "str") to list

```

同一个函数可以应用到整数，列表，字符串等等的操作称为`多态`。这可不是变态。

## 函数嵌套

函数嵌套就是函数中有函数，就叫嵌套函数了。


```python
def f1():
    print('hello')
    def f2():
        print('world')
    f2()
f1()

# 输出
hello
world

```


函数的嵌套保证了内部函数的调用，内部函数只能被外部函数所调用，不会作用于全局域中。




合理使用函数嵌套，提高运算速度

比如计算5的阶乘。

```python
def factorial(input):
    
    if not isinstance(input, int):
        raise Exception('input must be an integer.')
    if input < 0:
        raise Exception('input must be greater or equal to 0' )
  
    def inner_factorial(input):
        if input <= 1:
            return 1
        return input * inner_factorial(input-1)
    return inner_factorial(input)


print(factorial(5))

120

```

## 函数变量作用域


如果变量是izai函数内部定义的，称为局部变量，只在函数内部有效，当函数执行完毕，局部变量就会被回收。


全局变量就是写在函数外面的。

```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    if value < MIN_VALUE or value > MAX_VALUE:
        raise Exception('validation check fails')


```

这里的MIN_VELUE 和MAX_VALUE就是全局变量，但是我们不能在函数的内部随意改变全局变量的值

```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    ...
    MIN_VALUE += 1
    ...
validation_check(5)
UnboundLocalError: local variable 'MIN_VALUE' referenced before assignment


```


要想改变  必须加上global这个声明


```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    global MIN_VALUE
    ...
    MIN_VALUE += 1
    ...
validation_check(5)


```

global告诉python解析器，函数内部的变量MIN_VALUE就是定义的全局变量，这里输入的是2，这样修改的全局变量的值

```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    MIN_VALUE = 3
    ...


```


```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check():
    MIN_VALUE = 3
    print(MIN_VALUE)
validation_check()
print(MIN_VALUE)


# 3
# 1

```

对于嵌套函数来说，内部函数无法修改外部函数定义的变量，可以访问，想要修改就要加上 nonolocal 

```python
def outer():
    x = "local"
    def inner():
        nonlocal x # nonlocal 关键字表示这里的 x 就是外部函数 outer 定义的变量 x
        x = 'nonlocal'
        print("inner:", x)
    inner()
    print("outer:", x)
outer()
# 输出
inner: nonlocal
outer: nonlocal


```

不加就不会覆盖

```python
def outer():
    x = "local"
    def inner():
        x = 'nonlocal' # 这里的 x 是 inner 这个函数的局部变量
        print("inner:", x)
    inner()
    print("outer:", x)
outer()
# 输出
inner: nonlocal
outer: local


```

## 闭包


闭包就是在函数里面调用函数，一般用return来执行，return出内部调用的函数名。

计算一个数的n次幂

```python
def nth_power(exponent):
    def exponent_of(base):
        return base ** exponent
    return exponent_of # 返回值是 exponent_of 函数

square = nth_power(2) # 计算一个数的平方
cube = nth_power(3) # 计算一个数的立方 
square
# 输出
<function __main__.nth_power.<locals>.exponent(base)>

cube
# 输出
<function __main__.nth_power.<locals>.exponent(base)>

print(square(2))  # 计算 2 的平方
print(cube(2)) # 计算 2 的立方
# 输出
4 # 2^2
8 # 2^3


```

# 19、深入Python匿名函数

﻿

@Author：By Runsen

## 1、匿名函数

匿名函数不需要显示地定义函数名，使用【lambda + 参数 +表达式】的方式

### 1.1 lambda 函数

lambda 函数的形式




```python
lambda argument1, argument2,... argumentN : expression

```

套入函数，使用lambda 

```python
square = lambda x: x**2
square(3)

9

```

lambda 返回的一个函数对象



注意：lambda 和def 的区别

lambda 是一个表达式，def 是一个语句


```python
[(lambda x: x*x)(x) for x in range(10)]
# 输出
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

```

lambda 可以用作函数的参数，def 不能

```python
l = [(1, 20), (3, 0), (9, 10), (2, -1)]
l.sort(key=lambda x: x[1]) # 按列表中元祖的第二个元素排序
print(l)
# 输出
[(2, -1), (3, 0), (9, 10), (1, 20)]

```


lambda 是只有一行的简单表达式

```python
squared = map(lambda x: x**2, [1, 2, 3, 4, 5])

```

如果不用lambda ，你用def就需要多写好多行

```python
def square(x):
    return x**2

squared = map(square, [1, 2, 3, 4, 5])

```

在tkinter 中实现的简单功能

```python
from tkinter import Button, mainloop
button = Button(
    text='This is a button',
    command=lambda: print('being pressed')) # 点击时调用 lambda 函数
button.pack()
mainloop()

```

![](https://img-blog.csdnimg.cn/20190602104359313.png)

主要你按压就出现being pressed


你用def就是下面的样子

```python
from tkinter import Button, mainloop

def print_message():
    print('being pressed')

button = Button(
    text='This is a button',
    command=print_message) # 点击时调用 lambda 函数
button.pack()
mainloop()

```

使用def 要写好多行，多定义一个函数

### 1.2 函数式编程

函数式编程是指代码每一块都是不可变的，都是由纯函数的组成


这里的纯函数 值函数本身相互独立，对于相同的输入都有相同的输出


传入一个列表将列表的元素变为原来的2倍

```python
def multiply_2(l):
    for index in range(0, len(l)):
        l[index] *= 2
    return l


```

这段代码不是纯函数的形式，因为我多次调用，每次得到的结果不一样

```python
def multiply_2_pure(l):
    new_list = []
    for item in l:
        new_list.append(item * 2)
    return new_list


```

纯函数的形式，应该在函数里面定义一个新的列表

## 2、其他函数 


对于纯函数python 提供了几个函数

### 2.1 map 


map 函数的形式

```python
（ function ，iterable ）

```

第一个参数是函数的对象，第二个是一个可迭代对象






```python
l = [1, 2, 3, 4, 5]
new_list = map(lambda x: x * 2, l) 
list(new_list)
# [2， 4， 6， 8， 10]

```

### 2.2 filter


filter通常对一个集合做g过滤的操作

```python
l = [1, 2, 3, 4, 5]
new_list = filter(lambda x: x % 2 == 0, l)
list(new_list)
 # [2, 4]

```

### 2.3 reduce

reduce通常对一个集合做累积的操作

```python
import functools

l = [1, 2, 3, 4, 5]
product = functools.reduce(lambda x, y: x * y, l) 
product
# 1*2*3*4*5 = 120

```

## 3、思考题

### 3.1 如何根据值来排序

```python
d = {'mike': 10, 'lucy': 2, 'ben': 30}


sorted(d.items(),key=lambda x:x[1],reverse=True)

```

注意 reduce在3中已经放进functools模块中了

```python
>>> map(lambda x: x ** 2, [1, 2, 3, 4, 5])
<map object at 0x000001CAD42A8CF8>
>>> filter(lambda x: x % 2 ==0, [1,2,3,4,5])
<filter object at 0x000001CAD42A8C88>
>>> reduce(lambda x,y: x*y,[1,2,3,4,5])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'reduce' is not defined
>>> from functools import reduce
>>> reduce(lambda x,y: x*y,[1,2,3,4,5])
120
map,filter返回的只是一个对象，reduce在3中已经放进fucntools模块中了

```

#  20、深入Python迭代器和生成器

﻿@Author：By Runsen

## 1、 迭代器

### 1.1 容器

首先，在了解迭代器之前，需要知道什么是容器

一切都是对象，对象的抽象就是类，而对象的集合就是容器。

容器，就是有多个对象组成的东西。

比如：列表[0,1,2]，元组(1,2,3),字典{’0:'0','1':"1'}  集合{1,2,3}都是容器

所有的容器都是可迭代对象，也就是可以遍历元素。

可迭代对象：可以被转化为不依赖索引取值的容器，这样的对象就叫做可迭代对象，可以通过__iter__() 来生成不依赖索引取值的容器。


你看下图iter(111)是不是报错了。

![](https://img-blog.csdnimg.cn/20190711224541684.png)






因为111不能遍历，所以iter(111)直接报错。


现在写一个is_iterable判断是不是迭代器

```python
def is_iterable(param):
    try: 
        iter(param) 
        return True
    except TypeError:
        return False

params = [
    1234,
    '1234',
    [1, 2, 3, 4],
    set([1, 2, 3, 4]),
    {1:1, 2:2, 3:3, 4:4},
    (1, 2, 3, 4)
]
    
for param in params:
    print('{} is iterable? {}'.format(param, is_iterable(param)))

########## 输出 ##########

1234 is iterable? False
1234 is iterable? True
[1, 2, 3, 4] is iterable? True
{1, 2, 3, 4} is iterable? True
{1: 1, 2: 2, 3: 3, 4: 4} is iterable? True
(1, 2, 3, 4) is iterable? True

```

只要for i in 可以遍历，都是迭代器

### 1.2 取值

迭代器提供了一个next方法，调用这个方法，得到了容器的下一个对象或者一个stopiteration 的报错  ，没有下一个对象




```python
>>> a = iter("123")
>>> next(a)
'1'
>>> next(a)
'2'
>>> next(a)
'3'
>>> next(a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

但是迭代和枚举不完全一样


迭代你并不知道总量是多少

## 2、生成器





那么什么又是生成器，和迭代器又有什么关系？


**生成器就是一个迭代器的例子**，如果说迭代器是人，那么生成器就人中的一个人。

为什么会出来一个生成器，其实很简单声明一个迭代器很简单,但是很容易造成内存不够



比如下图（i for i in range(1000000000) 通过元组方式生成迭代器



![](https://img-blog.csdnimg.cn/20190711225225435.png)

![](https://img-blog.csdnimg.cn/20190711225452564.png)

[i for i in range(1000000000] 它也是一个迭代器，只不会太大了，跑不起来。于是生成器就出来了。

不信比一比内存和消耗的时间，代码如下。


```python
import os
import psutil

# 显示当前 python 程序占用的内存大小
def show_memory_info(hint):
    pid = os.getpid()
    p = psutil.Process(pid)
    
    info = p.memory_full_info()
    memory = info.uss / 1024. / 1024
    print('{} memory used: {} MB'.format(hint, memory))
    
def test_iterator():
    show_memory_info('initing iterator')
    list_1 = [i for i in range(100000000)]
    show_memory_info('after iterator initiated')
    print(sum(list_1))
    show_memory_info('after sum called')

def test_generator():
    show_memory_info('initing generator')
    list_2 = (i for i in range(100000000))
    show_memory_info('after generator initiated')
    print(sum(list_2))
    show_memory_info('after sum called')

%time test_iterator()
%time test_generator()

########## 输出 ##########

initing iterator memory used: 48.9765625 MB
after iterator initiated memory used: 3920.30078125 MB
4999999950000000
after sum called memory used: 3920.3046875 MB
Wall time: 17 s
initing generator memory used: 50.359375 MB
after generator initiated memory used: 50.359375 MB
4999999950000000
after sum called memory used: 50.109375 MB
Wall time: 12.5 s

```

对了，生成器还有一个yield关键字，不信，去菜鸟看看，说真的菜鸟教程真心不错。



![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS81YmIyODg1Ni03NjQwLTRhZTEtOGZhYi0yYmQ1MmI4YTNkYmYucG5n?x-oss-process=image/format,png)



yield在scrapy用的多，然后我在其他地方没有见到过。


yield和return也很好区别，return就返回值，结束函数，yield只是保存，不会结束函数。想下，你用scrapy爬错，爬一个就return，不干了，这怎么行。

## 3、 练习

### 3.1 给定一个列表和一个数字，求这个数字的位置

这好像是leetcode哪题，我忘记了。如果使用枚举的方法，也就是遍历，很简单。

```python
# 枚举的方法
def index_normal(L, target):
    result = []
    for i, num in enumerate(L):
        if num == target:
            result.append(i)
    return result

print(index_normal([1, 6, 2, 4, 5, 2, 8, 6, 3, 2], 2))

########## 输出 ##########

[2, 5, 9]

```


使用迭代器，需要用list转变为列表，才能print输出




```python
def index_generator(L, target):
    for i, num in enumerate(L):
        if num == target:
            yield i

print(list(index_generator([1, 6, 2, 4, 5, 2, 8, 6, 3, 2], 2)))

########## 输出 ##########

[2, 5, 9]

```

(1 in iter([1,2,3]))  #   True

```python
b = (i for i in range(5))  # 生成器

print(2 in b)
print(4 in b)
print(3 in b)

########## 输出 ##########

True
True
True


```

### 3.2 判断第一个子列是不是第二个的子序列

这我记得，https://leetcode.com/problems/is-subsequence/








![](https://img-blog.csdnimg.cn/20190713220951609.png)



 在去leetcode国际版找一个大神写的代码少的完美写法，

```python
def is_subsequence(a, b):
    b = iter(b) # 迭代器
    return all(i in b for i in a)

print(is_subsequence([1, 3, 5], [1, 2, 3, 4, 5]))
print(is_subsequence([1, 4, 3], [1, 2, 3, 4, 5]))

########## 输出 ##########

True
False

```

竟然有一个all就可以搞定了。我太菜了，菜得天天抄别人代码。


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS81NTMwZTMwZi00NTQzLTQwMTEtYWQzMC1lMDk5YjBkZWVhMWQucG5n?x-oss-process=image/format,png)

### 3.3 验证$1^3+2^3+3^3+……+n^3=(1+2+3+……+n)^2？$


生成器玩法，这个公式好像高中学的，



```python
def generator(k):
    i = 1
    while True:
        yield i ** k
        i += 1

gen_1 = generator(1)
gen_3 = generator(3)
print(gen_1)
print(gen_3)

def get_sum(n):
    sum_1, sum_3 = 0, 0
    for i in range(n):
        next_1 = next(gen_1)
        next_3 = next(gen_3)
        print('next_1 = {}, next_3 = {}'.format(next_1, next_3))
        sum_1 += next_1
        sum_3 += next_3
    print(sum_1 * sum_1, sum_3)

get_sum(8)

########## 输出 ##########

<generator object generator at 0x000001E70651C4F8>
<generator object generator at 0x000001E70651C390>
next_1 = 1, next_3 = 1
next_1 = 2, next_3 = 8
next_1 = 3, next_3 = 27
next_1 = 4, next_3 = 64
next_1 = 5, next_3 = 125
next_1 = 6, next_3 = 216
next_1 = 7, next_3 = 343
next_1 = 8, next_3 = 512
1296 1296

```

经过我三摧残，终于想起来之前的东西。



# 21、深入Python强大的装饰器

﻿

@Author：By Runsen

## 1、装饰器

### 1.1 装饰器入门


装饰器，顾名思义，就是用来“装饰”的。比如@Runsen就是一个装饰器，其中"Runsen"是你的装饰器的名字。它能装饰的东西有：函数、类。





先看两段代码，在这里my_decorator就是一个装饰器，其实装饰器就是一个函数来的函数

```python
def my_decorator(func):
    def wrapper():
        print('wrapper of decorator')
        func()
    return wrapper

def greet():
    print('hello world')

greet = my_decorator(greet)
greet()

# 输出
wrapper of decorator
hello world
```


my_decorator函数传入greet函数名方法，中间有一个wrapper内函数方法，  return wrapper说明要执行wrapper内函数，wrapper内函数，执行greet函数名方法


greet = my_decorator(greet)这个代码可以用装饰器来替代，在greet上面加一个@my_decorator，直接执行greet()



```python
def my_decorator(func):
    def wrapper():
        print('wrapper of decorator')
        func()
    return wrapper

@my_decorator
def greet():
    print('hello world')

greet()

wrapper of decorator
hello world
```


装饰器就是继承了 my_decorator函数，因此先调用my_decorator中的wrapper打印出
wrapper of decorator，然后func()被调用，指的就是 greet(),所以在打印出hello world

### 1.2 带参数的装饰器

有时候函数需要传入参数，这时候用*args, **kwargs接受就可以了。

```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print('wrapper of decorator')
        func(*args, **kwargs)
    return wrapper
    
def repeat(num):
    def my_decorator(func):
        def wrapper(*args, **kwargs):
            for i in range(num):
                print('wrapper of decorator')
                func(*args, **kwargs)
        return wrapper
    return my_decorator


@repeat(4)
def greet(message):
    print(message)

greet('hello world')

# 输出：
wrapper of decorator
hello world
wrapper of decorator
hello world
wrapper of decorator
hello world
wrapper of decorator
hello world


```


但是自定义参数的装饰器将改变函数本身的元信息，即函数不再是本身的函数

```python
**greet.__name__
## 输出
'wrapper'

help(greet)
# 输出
Help on function wrapper in module __main__:

wrapper(*args, **kwargs)
```

这时，需要使用内置模块functools.wrap会保留原函数的元信

在源代码中@functools.wraps也是这么来的


```python
import functools

def my_decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('wrapper of decorator')
        func(*args, **kwargs)
    return wrapper
    
@my_decorator
def greet(message):
    print(message)

greet.__name__

# 输出
'greet'

```

## 2、装饰器进阶

### 2.1  类装饰器

类装饰器主要依赖函数__call__	，每当调用一个类的实例，函数__call__就会执行一次



```python
class Count:
    def __init__(self, func):
        self.func = func
        self.num_calls = 0

    def __call__(self, *args, **kwargs):
        self.num_calls += 1
        print('num of calls is: {}'.format(self.num_calls))
        return self.func(*args, **kwargs)

@Count
def example():
    print("hello world")

example()

# 输出
num of calls is: 1
hello world

example()

# 输出
num of calls is: 2
hello world
```

### 2.2 装饰器的嵌套

如果一个函数上面有多个装饰器，叫做装饰器的嵌套


从下到上

```python
@decorator1
@decorator2
@decorator3
def func():
    ...

```

那么相当于，从里到外

```python
decorator1(decorator2(decorator3(func)))


import functools

def my_decorator1(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('execute decorator1')
        func(*args, **kwargs)
    return wrapper


def my_decorator2(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('execute decorator2')
        func(*args, **kwargs)
    return wrapper


@my_decorator1
@my_decorator2
def greet(message):
    print(message)


greet('hello world')

# 输出
execute decorator1
execute decorator2
hello world

```

## 3、装饰器用法实例

### 3.1 身份认证


```python
import functools

def authenticate(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        request = args[0]
        if check_user_logged_in(request): # 如果用户处于登录状态
            return func(*args, **kwargs) # 执行函数 post_comment() 
        else:
            raise Exception('Authentication failed')
    return wrapper
    
@authenticate
def post_comment(request, ...)
    ...
 


```

### 3.2 日志记录


```python
import time
import functools

def log_execution_time(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.perf_counter()
        res = func(*args, **kwargs)
        end = time.perf_counter()
        print('{} took {} ms'.format(func.__name__, (end - start) * 1000))
        return res
    return wrapper
    
@log_execution_time
def calculate_similarity(items):
    ...


```

### 3.3 输入合理性


```python
import functools

def validation_check(input):
    @functools.wraps(func)
    def wrapper(*args, **kwargs): 
        ... # 检查输入是否合法
    
@validation_check
def neural_network_training(param1, param2, ...):
    ...


```

所谓的装饰器，其实就是通过装饰器函数，来修改函数的一些功能，使得原函数不需要修改

代码来源：极客时间Python专栏

# 22、上篇 | Python的进程和线程

@Author: Runsen 

## 进程和线程

我们打开我们的计算机就会看到进程和线程


![](https://img-blog.csdnimg.cn/20190409220332456.png)


那什么是进程什么是线程

我的理解是进程是指在系统中正在运行的一个应用程序；程序一旦运行就是进程，或者更专业化来说：进程是指程序执行时的一个实例。

线程是进程的一个实体。

进程——资源分配的最小单位，线程——程序执行的最小单位。



我举个例子，**比如打开qq，就是一个线程，有很多个qq上号就是进程**

## python线程和进程的使用

现在讲python线程和进程的使用


 ![](https://img-blog.csdnimg.cn/20190409220401431.png)


 在Python中线程和进程的使用就是通过Thread这个类。这个类在我们的_thread和threading模块中。

![](https://img-blog.csdnimg.cn/201904092204568.png)


我们看一个标准的多线程的例子。


![](https://img-blog.csdnimg.cn/2019040922060320.png)

## 练习

下面我们来练习下， 加深hreading模块的使用。


我写了下面的代码

```python
# -*- coding：utf-8 -*-
# time ：2019/4/9 21:52
# author: Runsen
import threading
import time
def fun1():
    print('hello')
    time.sleep(2)
    print('Bye')
def fun2():
    print('hi')
    time.sleep(2)
    print('OUT')
t1 = threading.Thread(target=fun1)
t2 = threading.Thread(target=fun2)
t1.start()
t2.start()
# t1.join()
# t2.join()
print('主线程完毕')
```

我们先不加join()来阻塞，t1和t2两个线程同时执行，由于位置先打印hello，再打印hi，这个时候都sleep2秒钟，但是他sleep2秒钟，主程序还是在执行，所以下面打印print('主线程完毕')，最后才打印Bye和OUT

```
hello
hi
主线程完毕
Bye
OUT
```

## 线程间变量的共享

![](https://img-blog.csdnimg.cn/20190409221959273.png)





![](https://img-blog.csdnimg.cn/20190409222051749.png)


代码如上图所示，打印的a是1还是2，

答案是 ：2。因为出现了global，线程间变量的共享，在func中的a是全局变量。



下面，我们提高一点点难度，代码如下图所示，还是猜一猜a是啥东西。注意:这里出现了join来阻塞来增加了加和减的操作。





![](https://img-blog.csdnimg.cn/20190409222525518.png)


相信很多人都认为是0，其实这个a的值是变化的，可能这次是0 ，下次是1，还有可能是1000000，a就是在[-1000000，1000000]中的一个随机数。



为什么呢？这是因为虽然他们是同时运行的，但是同时在修改我们的a，那就乱了。这是导致a，for i in range(1000000)，就是遍历了1000000，incr和decr的方法都加上一起了，在这1000000次遍历中，不知道有多少加，多少减，比如，我1000000都是加，没有减，a就是1000000。






如果你就是想出现0，其实加一个互斥锁就可以了。这样你加多少次，我就减多少次，加减的次数不会叠加。因此来了lock的用法。



![](https://img-blog.csdnimg.cn/20190409222743790.png)

这个a怎么运行都是 0。因为我们把这个a锁上了，这样就加1000000次，减1000000次，怎么出来都是我们的0。



# 23、下篇 | Python线程和进程

﻿

@Author：Runsen

## 队列

上文锁能解决问题，但是不常见

![](https://img-blog.csdnimg.cn/20190409223407931.png)


```python
from queue import Queue
from threading import Thread
from random import randint
my_queue = Queue(3)
def f1(my_queus):
    for i in range(3):
        num = randint(0,10)
        print(num)
        my_queue.put(num)
def f2(my_queus):
    for i in range(3):
        num = my_queue.get()
        print(num)
t1 = Thread(target=f1,args=(my_queue,))
t2 = Thread(target=f2,args=(my_queue,))
t1.start()
t2.start()
t1.join()
t2.join()
```



0
5
10
0
5
10、


![](https://img-blog.csdnimg.cn/20190409224419329.png)

## 线程池

![](https://img-blog.csdnimg.cn/20190409224540227.png)

```python
from multiprocessing.pool import ThreadPool
import time
def hello(name):
    print('hello,{}'.format(name))
    time.sleep(2)
    print('Bye')
t = ThreadPool(3)
for i in range(3):
    t.apply_async(hello,args=(i,))
t.close()
t.join()

OUT：
几乎一起完成
hello,0
hello,1
hello,2
几乎一起完成
Bye
Bye
Bye
```


![](https://img-blog.csdnimg.cn/2019040922534897.png)

对于进程和线程，可以提高爬虫速度

## 多线程典型例子



```python
# -*- coding：utf-8 -*-
# time ：2019/4/23 10:13
# author: 毛利

import threading
import time
import random
MONEY = 0
gLock = threading.Lock()

def Procuder():
    while True:
        global MONEY
        random_money = random.randint(10,100)
        gLock.acquire()
        MONEY += random_money
        gLock.release()
        print ('生产者%s-生产了%d' % (threading.current_thread,random_money))
        time.sleep(0.5)

def Customer():
    while True:
        global MONEY
        random_money = random.randint(10,100)
        if MONEY > random_money:
            print ('消费者%s-消费了：%d' % (threading.current_thread,random_money))
            gLock.acquire()
            MONEY -= random_money
            gLock.release()
        else:
            print ('需要消费的钱为：%d，余额为：%d，' % (random_money,MONEY))
        time.sleep(0.5)

def p_c_test():
    # 执行3个线程，来当作生产者
    for x in range(3):
        th = threading.Thread(target=Procuder)
        th.start()
    # 执行3个线程，来当作消费者
    for x in range(3):
        th = threading.Thread(target=Customer)
        th.start()

if __name__ == "__main__":
    p_c_test()
```

![](https://img-blog.csdnimg.cn/20190424214132327.png)

# 24、深入Python多线程和多进程

@Author ： Runsen

## 多进程和多线程

- 基本概念

> “多任务”就是操作系统可以同时运行多个任务。


单核CPU操作系统轮流让各个任务交替执行，任务1执行0.01秒，切换到任务2执行0.01秒反复执行。表面上看，每个任务都是交替执行的，但是，由于CPU的执行速度实在是太快了，感觉就像所有任务都在同时执行一样。真正的并行执行多任务只能在多核CPU上实现，但是，由于任务数量远远多于CPU的核心数量，所以，操作系统也会自动把很多任务轮流调度到每个核心上执行。

- 并行和并发

> 并行：当系统有一个以上CPU时,则线程的操作有可能非并发。当一个CPU执行一个线程时，另一个CPU可以执行另一个线程，两个线程互不抢占CPU资源，可以同时进行，这种方式我们称之为并行(Parallel)。


> 并发：当有多个线程在操作时,如果系统只有一个CPU,则它根本不可能真正同时进行一个以上的线程，它只能把CPU运行时间划分成若干个时间段,再将时间 段分配给各个线程执行，在一个时间段的线程代码运行时，其它线程处于挂起状。这种方式称为并发(Concurrent)。

## 进程、线程、协程

一个任务就是一个进程（Process），比如打开一个浏览器就是启动一个浏览器进程。
有些进程不止同时干一件事，比如Word，它可以同时进行打字、拼写检查、打印等事情。在一个进程内部，要同时干多件事，就需要同时运行多个“子任务”，我们把进程内的这些“子任务”称为线程（Thread）。一个进程至少有一个线程。

- 进程：每个进程都有自己独立的内存空间，不同进程之间的内存空间不共享。
  密集CPU任务，需要充分使用多核CPU资源（服务器，大量的并行计算）时，用多进程。
  进程之间的通信有操作系统传递，导致通讯效率低，切换开销大。

- 线程：一个进程可以有多个线程，所有线程共享进程的内存空间，通讯效率高，切换开销小。
  共享意味着竞争，导致数据不安全，为了保护内存空间的数据安全，引入"互斥锁"。
  一个线程在访问内存空间的时候，其他线程不允许访问，必须等待之前的线程访问结束，才能使用这个内存空间。
  密集I/O任务（网络I/O，磁盘I/O，数据库I/O）使用多线程合适。
  对于一些要求同时进行并且又要共享某些变量的并发操作，只能用线程，不能用进程。

- 互斥锁：一种安全有序的让多个线程访问内存空间的机制。

- 协程：又称微线程，在单线程上执行多个任务，用函数切换，开销极小。不通过操作系统调度，没有进程、线程的切换开销
  多线程请求返回是无序的，哪个线程有数据返回就处理哪个线程，而协程返回的数据是有序的

缺陷：单线程执行，处理密集CPU和本地磁盘IO的时候，性能较低。处理网络I/O性能还是比较高.

- GIL 全局解释器锁：线程的执行权限，在Python的进程里只有一个GIL。
  一个线程需要执行任务，必须获取GIL。
  好处：直接杜绝了多个线程访问内存空间的安全问题。
  坏处：Python的多线程不是真正多线程，不能充分利用多核CPU的资源。
  但是，在I/O阻塞的时候，解释器会释放GIL。

## 多进程

- fork—支持linux/unix
  os模块封装了常见的系统调用，其中就包括fork
  在Unix/Linux操作系统中，提供了一个fork()系统函数，它非常特殊。
  编写完毕的代码，在没有运行的时候，称之为程序，正在运行着的代码，就成为进程

- 程序执行os.fork()时，操作系统会创建一个新的进程（子进程），然后复制父进程的所有信息到子进程中
  普通的函数调用，调用一次，返回一次，但是fork()调用一次，返回两次，因为操作系统自动把当前进程（称为父进程）复制了一份（称为子进程），然后，分别在父进程和子进程内返回。

- 然后父进程和子进程都会从fork()函数中得到一个返回值，在子进程中这个值一定是0，而父进程中是子进程的 id号
  这样做的理由是，一个父进程可以fork出很多子进程，所以，父进程要记下每个子进程的ID，而子进程只需要调用getppid()就可以拿到父进程的ID。
- multiprosessing—跨平台
  multiprocessing模块是跨平台版本的多进程模块。
  multiprocessing模块提供了一个Process类来代表一个进程对象。


- 	创建子进程
   创建子进程时，只需要传入一个执行函数和函数的参数，创建一个Process实例，用start()方法启动。
    join()方法可以等待子进程结束后再继续往下运行，通常用于进程间的同步。

 ```python
def proc(name): #子进程要执行的代码
    print('运行子进程 %s (%s)...' %(name, os.getpid()))  #得到子进程id

p=Process(target=proc,args=('test',)) #传入函数名和参数
print('子进程将要执行...')
p.start()
p.join()
print('子进程结束')
 ```

Process([group [, target [, name [, args [, kwargs]]]]])

- 	target：表示这个进程实例所调用对象；
- 	args：表示调用对象的位置参数元组；
- 	kwargs：表示调用对象的关键字参数字典；
- 	name：为当前进程实例的别名；
- 	group：大多数情况下用不到；

Process类常用方法：

- 	is_alive()：判断进程实例是否还在执行；
- 	join([timeout])：是否等待进程实例执行结束，或等待多少秒；
- 	start()：启动进程实例（创建子进程）；
- 	run()：如果没有给定target参数，对这个对象调用start()方法时，就将执行对象中的run()方法；
- 	terminate()：不管任务是否完成，立即终止；

Process类常用属性：

- name：当前进程实例别名，默认为Process-N，N为从1开始递增的整数；
- pid：当前进程实例的PID值；

- pool类
  如果要启动大量的子进程，可以用进程池的方式批量创建子进程。
  初始化Pool时，可以指定一个最大进程数，当有新的请求提交到Pool中时，如果池还没有满，那么就会创建一个新的进程用来执行该请求；但如果池中的进程数已经达到指定的最大值，那么该请求就会等待，直到池中有进程结束，才会创建新的进程来执行

```python
def task(name):
    print('运行子进程%s(%s)'%(name,os.getpid()))
    start=time()
    sleep(random.random()*3)
    end=time()
    print('子进程%s运行 %.2f 秒'%(name,(end-start)))   #子进程01213是同时进行的，某个进程运行完毕后再运行子进程4

if __name__ == '__main__':
    print('父进程%s'%os.getpid())
    p=Pool(4)  #最多同时跑4个子进程，默认大小为cpu核数
    for i in range(5):
        p.apply_async(task,args=(i,))
    p.close()    #调用close之后不能添加新的进程了
    p.join()
    print('所有进程完毕')
```

调用join（）会等待所有子进程执行完毕，调用之前必须先调用close，调用close之后不能添加新的进程了

子进程
很多时候，子进程并不是自身，而是一个外部进程。我们创建了子进程后，还需要控制子进程的输入和输出。
subprocess模块启动一个子进程，控制其输入和输出。
子进程可以通过communicate()方法输入

## 进程间通信

python提供了很多进程间通信的方式，queue用于在多进程间通信，pipe用于两个进程间通信。

- 	Queue
   可以使用multiprocessing模块的Queue实现多进程之间的数据传递，Queue本身是一个消息列队程序，是多进程安全的队列。

- 	Put方法用以插入数据到队列中，它有两个可选参数:blocked和timeout。如果blocked为True(默认值)，并且timeout为正值，该方法会阻塞timeout指定的时间，直到该队列有剩余的空间。如果超时，会抛出Queue.Full异常。如果blocked为False，但该Queue已满，会立即抛出Queue.Full异常。
- 	Get方法可以从队列读取并且删除一个元素。同样，Get方法有两个可选参数:blocked和timeout。如果blocked为True(默认值)，并且timeout为正值，那么在等待时间内没有取到任何元素，会抛出Queue.Empty异常。如果blocked为False,分两种情况:如果Queue有一个值可用，则立即返回该值;否则，如果队列为空，则立即抛出Queue.Empty异常。

## Pipe

Pipe常用来在两个进程间进行通信，两个进程分别位于管道的两端。
Pipe方法返回(conn1, conn2)代表一个管道的两个端。
Pipe方法有duplex参数，如果duplex参数为True(默认值)，那么这个管道是全双工模式，也就是说conn1和conn2均可收发。若duplex为False, conn1只负责接收消息，conn2只负责发送消息。
send和recv方法分别是发送和接收消息的方法。例如，在全双工模式下，可以调用connl.send发送消息，connl.recv接收消息。如果没有消息可接收，recv方法会一直阻塞。如果管道已经被关闭，那么recv方法会抛出EOFError

## 多线程（threading）

多任务可以由多进程完成，也可以由一个进程内多线程完成。
多线程运行有如下优点:

- 可以把运行时间长的任务放到后台去处理。
- 用户界面可以更加吸引人，比如用户点击了一个按钮去触发某些事件的处理，可以弹出一个进度条来显示处理的进度。
- 程序的运行速度可能加快。
- 在一些需要等待的任务实现上，如用户输入、文件读写和网络收发数据等，线程就比较有用了。在这种情况下我们可以释放一些珍贵的资源，如内存占用等。



**threading模块一般通过两种方式创建多线程:**
1)	 把一个函数传入并创建Thread实例，然后调用start方法开始执行
2)	直接从threading. Thread继承并创建线程类，然后重写__init__方法和run方法

```python
import threading,time
def loop1():
    print('线程 %s 运行...'%threading.current_thread().name)  #显示子线程实例名字
    n=0
    while n<3:
        n=n+1
        print('%s >>> %s'%(threading.current_thread().name,n))     #current_thread()函数返回当前线程实例
        time.sleep(0.5)
    print('线程 %s 结束...'%threading.current_thread().name)

def loop2():
    print('线程 %s 运行...'%threading.current_thread().name)
    n=0
    while n<2:
        n+=1
        print('%s >>> %s' %(threading.current_thread().name,n))
        time.sleep(0.5)
    print('线程 %s 结束...' % threading.current_thread().name)

if __name__ == '__main__':
    print('---开始---:%s'%time.ctime(),'\n')
    # 显示当前线程，即主线程实例名字
    print('%s 运行'%threading.current_thread().name)
    # 创建子线程，子线程名字在创建时指定，loopthread为子线程的名字，不指定为默认名
    t=threading.Thread(target=loop1,name='子线程1')
    p=threading.Thread(target=loop2,name='子线程2')
    #子线程可以全部start之后再join，即为同步运行，分开执行，为运行完子线程1，再运行子线程2
    t.start()
    t.join()
    p.start()
    p.join()
    while True:
        length=len(threading.enumerate())
        print('当前运行线程数量：%d'%length)
        if length<=1:
            break
    print('thread %s ended'%threading.current_thread().name)
```

任何进程默认就会启动一个线程，该线程称为主线程，主线程又可以启动新的线程， threading模块current_thread()函数返回当前线程的实例。

## 线程同步—lock

多线程和多进程最大的不同在于，多进程中，同一个变量，各自有一份拷贝存在于每个进程中，互不影响，而多线程中，所有变量都由所有线程共享，所以，任何一个变量都可以被任何一个线程修改，因此，线程之间共享数据最大的危险在于多个线程同时改一个变量

```python
t.start()
p.start()
t.join()
p.join()
```

多线程交替运行，每个线程有自己的局部变量，导致赋予全局变量的值会打乱，确保全局变量的值为正确值，要给change_it()上一把锁，其他线程不能同时执行change_it()，只能等待，直到锁被释放后，获得该锁以后才能改。锁只有一个，无论多少线程，同一时刻最多只有一个线程持有该锁，所以，不会造成修改的冲突。

```python
def change_it(n):
    # 先存后取，结果应该为0:
    global balance
    balance = balance + n
    balance = balance - n

def thread(n):
    for i in range(1000):
        #获取锁
        lock.acquire()
        try:
            change_it(n)
        finally:
            #改完释放锁
            lock.release()

if __name__ == '__main__':
    balance=0
    lock=threading.Lock()
    t1 = threading.Thread(target=thread, args=(5,))
    t2 = threading.Thread(target=thread, args=(8,))
    t1.start()
    t2.start()
    t1.join()
    t2.join()
    print(balance)
```

ThreadLocal: 解决参数在一个线程中各个函数之间互相传递的问题。
local_data = threading.local()  #创建全局ThreadLocal对象
local_data为一个ThreadLocal对象，每个thread对其可读写属性，但互不影响。可以把local_school看成全局变量，但每个属性如local_data.data都是线程的局部变量，可以理解为全局变量local_data是一个dict，不但可以用local_data.data，还可以绑定其他变量，如local_data.teacher等等可以任意读写而互不干扰，也不用管理锁的问题，ThreadLocal内部会处理。
ThreadLocal最常用的地方就是为每个线程绑定一个数据库连接，HTTP请求，用户身份信息等，这样一个线程的所有调用到的处理函数都可以非常方便地访问这些资源。

## 协程 (coroutine )

协程又称微线程，纤程，是一种用户级的轻量级线程。
协程拥有自己的寄存器上下文和栈。协程调度切换时，将寄存器上下文和栈保存到其他地方，在切回来的时候，恢复先前保存的寄存器上下文和栈。因此协程能保留上一次调用时的状态，每次过程重入时，就相当于进人上一次调用的状态。
在并发编程中，协程与线程类似，每个协程表示一个执行单元，有自己的本地数据，与其他协程共享全局数据和其他资源。
协程需要用户自己来编写调度逻辑，对于CPU来说，协程其实是单线程，所以CPU不
用去考虑怎么调度、切换上下文，这就省去了CPU的切换开销，所以协程在一定程度上又好于多线程。

Python通过yield提供了对协程的基本支持，但是不完全，第三方gevent库提供了比较完善的协程支持。gevent是一个基于协程的Python网络函数库，使用greenlet在libev事件循环顶部提供了一个有高级别并发性的API。

主要特性：

- 基于libev的快速事件循环，Linux上是epoll机制。
- 基于greenlet的轻量级执行单元。
- API复用了Python标准库里的内容。	
- 支持SSL的协作式sockets.
- 可通过线程池或c-ares实现DNS查询。
- 通过monkey patching功能使得第三方模块变成协作式。

## 分布式进程

在Thread和Process中，应当优选Process，因为Process更稳定，而且，Process可以分布到多台机器上，而Thread最多只能分布到同一台机器的多个CPU上。

Python的multiprocessing模块不但支持多进程，其中managers子模块还支持把多进程分布到多台机器上。一个服务进程可以作为调度者，将任务分布到其他多个进程中，依靠网络通信。

# 25、深入Python中的协程

﻿

@Author： runsen 

## 协程是实现并发编程的一种方式

https://docs.python.org/zh-cn/3/library/asyncio.html




一说并发，你肯定想到了多线程 ， 多进程模型，没错，多线程 和 多进程，正是解决并发问题的经典模型之一

但是你了解过协程Coroutine吗？

协程：是单线程下的并发，又称微线程。


就是只有一个线程，如何提高速度，解决并发编程

英文名Coroutine。

协程比线程的单位更小——协程




注意协程这个概念完全是程序员自己想出来的东西，它对于操作系统来说根本不存在。操作系统只有进程和线程。



从一个demo学起

```cpp
import time 

def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    time.sleep(1)
    print("Maoli prints" + str(num) + " OK")

def main(nums):
    for num in nums:
        print_num(num)
%time main([i for i in range(1,6)])


Maoli is printing 1 nows
Maoli prints1 OK
Maoli is printing 2 nows
Maoli prints2 OK
Maoli is printing 3 nows
Maoli prints3 OK
Maoli is printing 4 nows
Maoli prints4 OK
Maoli is printing 5 nows
Maoli prints5 OK
Wall time: 5 s
```


%time 需要在jupyter notebook中运行。



上面代码是从上到下执行的。


下面将上面代码改为协程版

**注意py版本3.7以上**，主要使用的是asyncio

```cpp
import asyncio

async def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    await asyncio.sleep(1)
    print("Maoli prints" + str(num) + " OK")

async def main(nums):
    for num in nums:
        await print_num(num)
%time asyncio.run(main([i for i in range(1,6)]))


Maoli is printing 1 nows
Maoli prints1 OK
Maoli is printing 2 nows
Maoli prints2 OK
Maoli is printing 3 nows
Maoli prints3 OK
Maoli is printing 4 nows
Maoli prints4 OK
Maoli is printing 5 nows
Maoli prints5 OK
Wall time: 5.01 s
```



asyncio.run() 函数用来运行最高层级的入口点 "main()" 函数

await 是同步调用等待一个协程。以下代码段会在等待 1 秒后打印 num，速度上没有发生改变。

需要引入asyncio.create_task才可以

## 可等待对象


如果一个对象可以在 await 语句中使用，那么它就是 可等待 对象

协程中的还一个重要概念，任务（Task）

如果写一个数字是一个任务，那么毛利我要完成5个任务


毛利我写个1-5都这么慢，不行，我要加速写

asyncio.create_task() 函数用来并发运行作为 asyncio 任务 的多个协程。


```cpp
import asyncio

async def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    await asyncio.sleep(1)
    print("Maoli prints" + str(num) + " OK")

async def main(nums):
    tasks = [asyncio.create_task(print_num(num)) for num in nums]
    for task in tasks:
        await task
%time asyncio.run(main([i for i in range(1,6)]))


Maoli is printing 1 nows
Maoli is printing 2 nows
Maoli is printing 3 nows
Maoli is printing 4 nows
Maoli is printing 5 nows
Maoli prints1 OK
Maoli prints3 OK
Maoli prints5 OK
Maoli prints2 OK
Maoli prints4 OK
Wall time: 1.01 s
```



还可以写成`await asyncio.gather(*tasks)`这种方法

```cpp
import asyncio

async def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    await asyncio.sleep(1)
    print("Maoli prints" + str(num) + " OK")

async def main(nums):
    tasks = [asyncio.create_task(print_num(num)) for num in nums]
    await asyncio.gather(*tasks)
%time asyncio.run(main([i for i in range(1,6)]))

```



*tasks 解包列表，将列表变成了函数的参数；与之对应的是，  ** dict 将字典变成了函数的参数。



#asyncio 队列

asyncio也是只有在Pytohn3.7才有的东西。


asyncio 队列被设计成与 queue 模块类似。



```cpp
import asyncio
import random

async def consumer(queue, id):
    while True:
        val = await queue.get()
        print('{} get a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def producer(queue, id):
    for i in range(5):
        val = random.randint(1, 10)
        await queue.put(val)
        print('{} put a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def main():
    # 创建队列
    queue = asyncio.Queue()
    # 消费者1号
    consumer_1 = asyncio.create_task(consumer(queue, 'consumer_1'))
    # 消费者2号
    consumer_2 = asyncio.create_task(consumer(queue, 'consumer_2'))
    # 生产者1号
    producer_1 = asyncio.create_task(producer(queue, 'producer_1'))
    # 生产者2号
    producer_2 = asyncio.create_task(producer(queue, 'producer_2'))
    # stop 10秒
    await asyncio.sleep(10)
    consumer_1.cancel()
    consumer_2.cancel()
    
    await asyncio.gather(consumer_1, consumer_2, producer_1, producer_2, return_exceptions=True)

%time asyncio.run(main())

```

协程的写法简洁清晰，只要把 async / await 语法和 create_task 结合来用，就是Python中比较常见的协程

## 典型的例子

 典型的生产者和消费者

```
import asyncio
import random

async def consumer(queue, id):
    while True:
        val = await queue.get()
        print('{} get a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def producer(queue, id):
    for i in range(5):
        val = random.randint(1, 10)
        await queue.put(val)
        print('{} put a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def main():
    queue = asyncio.Queue()

    consumer_1 = asyncio.create_task(consumer(queue, 'consumer_1'))
    consumer_2 = asyncio.create_task(consumer(queue, 'consumer_2'))

    producer_1 = asyncio.create_task(producer(queue, 'producer_1'))
    producer_2 = asyncio.create_task(producer(queue, 'producer_2'))

    await asyncio.sleep(10)
    consumer_1.cancel()
    consumer_2.cancel()
    
    await asyncio.gather(consumer_1, consumer_2, producer_1, producer_2, return_exceptions=True)

%time asyncio.run(main())

########## 输出 ##########

producer_1 put a val: 5
producer_2 put a val: 3
consumer_1 get a val: 5
consumer_2 get a val: 3
producer_1 put a val: 1
producer_2 put a val: 3
consumer_2 get a val: 1
consumer_1 get a val: 3
producer_1 put a val: 6
producer_2 put a val: 10
consumer_1 get a val: 6
consumer_2 get a val: 10
producer_1 put a val: 4
producer_2 put a val: 5
consumer_2 get a val: 4
consumer_1 get a val: 5
producer_1 put a val: 2
producer_2 put a val: 8
consumer_1 get a val: 2
consumer_2 get a val: 8
Wall time: 10 s

```

## 真实的爬虫

```python
import requests
from bs4 import BeautifulSoup

def main():
    url = "https://movie.douban.com/cinema/later/beijing/"
    init_page = requests.get(url).content
    init_soup = BeautifulSoup(init_page, 'lxml')

    all_movies = init_soup.find('div', id="showing-soon")
    for each_movie in all_movies.find_all('div', class_="item"):
        all_a_tag = each_movie.find_all('a')
        all_li_tag = each_movie.find_all('li')

        movie_name = all_a_tag[1].text
        url_to_fetch = all_a_tag[1]['href']
        movie_date = all_li_tag[0].text

        response_item = requests.get(url_to_fetch).content
        soup_item = BeautifulSoup(response_item, 'lxml')
        img_tag = soup_item.find('img')

        print('{} {} {}'.format(movie_name, movie_date, img_tag['src']))

%time main()

```

Wall time: 26 s




```python
import asyncio
import aiohttp

from bs4 import BeautifulSoup

async def fetch_content(url):
    async with aiohttp.ClientSession(
        connector=aiohttp.TCPConnector(ssl=False)
    ) as session:
        async with session.get(url) as response:
            return await response.text()

async def main():
    url = "https://movie.douban.com/cinema/later/beijing/"
    init_page = await fetch_content(url)
    init_soup = BeautifulSoup(init_page, 'lxml')

    movie_names, urls_to_fetch, movie_dates = [], [], []

    all_movies = init_soup.find('div', id="showing-soon")
    for each_movie in all_movies.find_all('div', class_="item"):
        all_a_tag = each_movie.find_all('a')
        all_li_tag = each_movie.find_all('li')

        movie_names.append(all_a_tag[1].text)
        urls_to_fetch.append(all_a_tag[1]['href'])
        movie_dates.append(all_li_tag[0].text)

    tasks = [fetch_content(url) for url in urls_to_fetch]
    pages = await asyncio.gather(*tasks)

    for movie_name, movie_date, page in zip(movie_names, movie_dates, pages):
        soup_item = BeautifulSoup(page, 'lxml')
        img_tag = soup_item.find('img')

        print('{} {} {}'.format(movie_name, movie_date, img_tag['src']))

%time asyncio.run(main())


```

Wall time: 4.57 s，速度快了5倍。

# 26、Python中的Time和os模块

﻿@Author: Runsen

## 日期与时间管理的库datetime 与time 



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


## os 操作模块

OS模块简单的来说它是一个Python的系统编程的操作模块，可以处理文件和目录这些我们日常手动需要做的 操作。 可以查看OS模块的帮助文档：

import os #导入os模块  
help(os)   #查看os模块帮助文档，里面详细的模块相关函数和使用方法

### OS模块重要函数和变量:

- os.sep 更改操作系统中的路径分隔符。 
- os.getcwd()获取当前路径，这个在Python代码中比较 常用。 
- os.listdir() 列出当前目录下的所有文件和文件夹。 
- os.remove() 方法可以删除指定 的文件。 
- os.system() 方法用来运行shell命令。 
- os.chdir() 改变当前目录，到指定目录 中。

### OS模块函数作用详解

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

### os.path模块

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

# 27、Python序列化pickle标准库﻿

听过Python序列化pickle标准库吗？

## 序列化


序列化 (Serialization)是将对象的状态信息转换为可以存储或传输的形式的过程。就是将数据结构转化成你看不懂的东西


pickle提供四个功能：dumps,dump,loads,load 和json 一样


从小demo入手

```python
import pickle
data = [{'a': 'A', 'b': 2, 'c': 2.22}]
# 使用 pickle.dumps() 可以将一个对象转换为二进制字符串（dump string）：
data_string = pickle.dumps(data)
print("DATA:")
print(data)
print("PICKLE:")
print(data_string)
```

---



```python
DATA:
[{'a': 'A', 'b': 2, 'c': 2.22}]
PICKLE:
b'\x80\x03]q\x00}q\x01(X\x01\x00\x00\x00aq\x02X\x01\x00\x00\x00Aq\x03X\x01\x00\x00\x00bq\x04K\x02X\x01\x00\x00\x00cq\x05G@\x01\xc2\x8f\\(\xf5\xc3ua.'
```


现在给你这个data_string 你能知道这是啥吗？


 虽然 pickle 编码的字符串并不一定可读，但是我们可以用 pickle.loads() 来从这个字符串中恢复原对象中的内容（load string）：

```python
# pickle.loads() 来从这个字符串中恢复原对象中的内容（load string）：
data_from_string = pickle.loads(data_string)
print(data_from_string)
```


dumps 和loads 相反的作用

```python
[{'a': 'A', 'b': 2, 'c': 2.22}]
```







dumps 可以接受一个可省略的 protocol 参数（默认为 0）




```python
data_string_0 = pickle.dumps(data, 0)
print("Pickle 0:", data_string_0)
data_string_1 = pickle.dumps(data, 1)
print("Pickle 1:", data_string_1)
data_string_2 = pickle.dumps(data, 2)
print("Pickle 2:", data_string_2)
# 如果 protocol 参数指定为负数，那么将调用当前的最高级的编码协议进行编码：
print("Pickle -1:", pickle.dumps(data, -1))
```


输出如下


```python
Pickle 0: b'(lp0\n(dp1\nVa\np2\nVA\np3\nsVb\np4\nL2L\nsVc\np5\nL3L\nsa.'
Pickle 1: b']q\x00}q\x01(X\x01\x00\x00\x00aq\x02X\x01\x00\x00\x00Aq\x03X\x01\x00\x00\x00bq\x04K\x02X\x01\x00\x00\x00cq\x05K\x03ua.'
Pickle 2: b'\x80\x02]q\x00}q\x01(X\x01\x00\x00\x00aq\x02X\x01\x00\x00\x00Aq\x03X\x01\x00\x00\x00bq\x04K\x02X\x01\x00\x00\x00cq\x05K\x03ua.'
Pickle -1: b'\x80\x04\x95\x1c\x00\x00\x00\x00\x00\x00\x00]\x94}\x94(\x8c\x01a\x94\x8c\x01A\x94\x8c\x01b\x94K\x02\x8c\x01c\x94K\x03ua.'
```



从这些格式中恢复对象时，不需要指定所用的协议，pickle.load() 会自动识别：

```python
print("Load 1:", pickle.loads(data_string_1))
print("Load 2:", pickle.loads(data_string_2))

OUT：
Load 1: [{'a': 'A', 'b': 2, 'c': 3}]
Load 2: [{'a': 'A', 'b': 2, 'c': 3}]
```



## 存储和读取 pickle 文件




```python
# 存储和读取 pickle 文件
with open('data.pkl', 'wb') as f:
    pickle.dump(data, f)

with open('data.pkl',"rb") as f:
    data_from_file = pickle.load(f)

print(data_from_file)

# 清理生成的文件：
os.remove('data.pkl')

OUT：
[{'a': 'A', 'b': 2, 'c': 3}]
```

# 28、Python中的日志处理logging模块

﻿@Author：Runsen

## 日志logging

日志是一种可以追踪某些软件运行时所发生事件的方法。软件开发人员可以向他们的代码中调用日志记录相关的方法来表明发生了某些事情。一个事件可以用一个可包含可选变量数据的消息来描述。此外，事件也有重要性的概念，这个重要性也可以被称为严重性级（level）。

![](https://img-blog.csdnimg.cn/20190418234643545.png)





Logging 中几种级别：DEBUG < INFO < WARNING < ERROR < CRITICAL




![](https://img-blog.csdnimg.cn/20190418234723863.png)


![](https://img-blog.csdnimg.cn/20190418234754723.png)


logging模块是python内置的标准模块，主要用于输出运行日志，可以设置输出日志的等级、日志保存路径、日志文件和回滚等；
可以说，logging模块主要由4部分组成：



-  Logger 记录器，提供了应用程序代码能直接使用的接口
-  Handler 处理器，将记录器产生的日志记录发送至合适的目的地，或者说将Logger产生的日志传到指定位置
-  Filters 过滤器，对输出的日志进行过滤，它可以决定输出哪些日志记录
-  Formatter 格式化器，控制日志输出的格式，指明了最终输出中日志记录的布局





![](https://img-blog.csdnimg.cn/20190418234825414.png)

## 模块化组件使用

- 创建一个logger（日志处理器）对象
- 定义handler(日志处理器)，决定把日志发到哪里


![](https://img-blog.csdnimg.cn/20190418235053974.png)




- 设置日志级别（level）和输出格式Formatters（日志格式器）
- 把handler添加到对应的logger中去



![](https://img-blog.csdnimg.cn/20190418235206590.png)

# 29、Python标准库 collections

﻿

@Author：Runsen


## collections 


计数器（counter）以字典的形式返回序列中各个字符出现的次数，值为key，次数为value


Counter是对字典类型的补充，用于追踪值得出现次数 ps:具备字典的所有功能 + 自己的功能


```python
import collections

counter_test = collections.Counter("asfafjhadgkhjkgfjhgfjhaghdg")
print(counter_test)
```

 Counter({'h': 5, 'g': 5, 'a': 4, 'f': 4, 'j': 4, 'd': 2, 'k': 2, 's': 1})
    

数量从大到小排列，获取前N个元素 


```python
# most_common(N)数量从大到小排列，获取前N个元素 
counter_test.most_common(3)
```




[('h', 5), ('g', 5), ('a', 4)]



列出所有不同的元素并排序

```python
# sorted()列出所有不同的元素并排序 
sorted(counter_test)
```



['a', 'd', 'f', 'g', 'h', 'j', 'k', 's']


转换成字符串 

```python
# 转换成字符串 
''.join(sorted(counter_test.elements())) 
```




'aaaaddffffggggghhhhhjjjjkks'




```python
# 取得元素重复次数的值
counter_test['a']
```

4



 update()更新计数器

```python
# update()更新计数器，其实就是增加；如果原来没有，则新建，如果有则加一
d = collections.Counter('simsalabim') 
counter_test.update(d) 
print(counter_test) 
```

 Counter({'a': 6, 'h': 5, 'g': 5, 'f': 4, 'j': 4, 's': 3, 'd': 2, 'k': 2, 'i': 2, 'm': 2, 'l': 1, 'b': 1})
    


```python
# elements()取得计数器中的所有元素，注：此处非所有元素集合，而是包含所有元素集合的迭代器 
counter_test = collections.Counter('abcabc') 
sorted(counter_test.elements()) 
```




['a', 'a', 'b', 'b', 'c', 'c']




```python
# subtract()相减，原来的计数器中的每一个元素的数量减去后添加的元素的数量 

counter_test = collections.Counter('which') 
print(counter_test)
counter_test.subtract('watch') 
print(counter_test)
```

Counter({'h': 2, 'w': 1, 'i': 1, 'c': 1})
Counter({'h': 1, 'i': 1, 'w': 0, 'c': 0, 'a': -1, 't': -1})
    

## 有序字典（orderedDict)  



```python
from collections import OrderedDict 
dic = OrderedDict() 
dic['k1'] = 'v1' 
dic['k2'] = 'v2' 
dic['k3'] = 'v3' 
print(dic) 

```

OrderedDict([('k1', 'v1'), ('k2', 'v2'), ('k3', 'v3')])
    


```python
# 得字典所有的键 
print(dic.keys())

```

odict_keys(['k1', 'k2', 'k3'])
    


```python
# 取得字典所有值 
print(dic.values())

```

odict_values(['v1', 'v2', 'v3'])
    


```python
# items() 方法以列表返回可遍历的(键, 值) 元组数组 
print(dic.items())

```

odict_items([('k1', 'v1'), ('k2', 'v2'), ('k3', 'v3')])
    


```python
#pop()方法，删除指定的键值 
dic.pop('k1')  
print(dic) 


```

OrderedDict([('k2', 'v2'), ('k3', 'v3')])
    


```python
#item()方法，默认删除字典最后一个元素 
dic.popitem() 
print(dic) 

```

OrderedDict([('k2', 'v2')])
    


```python
# move_to_end('k')方法将指定键值一道最后
dic.move_to_end('k2') 
print(dic)

```

 OrderedDict([('k2', 'v2')])
    


```python
# update()更新字典 
dic.update({'k1':'v1111','k10':'v10'}) 
print(dic) 

```

OrderedDict([('k2', 'v2'), ('k1', 'v1111'), ('k10', 'v10')])
    

## 默认字典（defaultdict） 


```python
#导入collections模块
import collections
my_dict = collections.defaultdict(list)
my_dict['k1'].append('v1')
print(my_dict)

```

defaultdict(<class 'list'>, {'k1': ['v1']})
    


```python
# 练习：元素分类
# 有如下值集合 [11,22,33,44,55,66,77,88,99,90...]，
# 将所有大于 66 的值保存至字典的第一个key中，将小于 66 的值保存至第二个key的值中。
# 即： {'k1': 大于66 , 'k2': 小于66}

### 1、不用默认指点的写法要判断字典中是否已有{'k1':[]}
all_list = [11,22,33,44,55,66,77,88,99,90,]
dic = {}
for i in all_list:
    if i > 66:
        if "k1" in dic.keys():
            dic['k1'].append(i)
        else:
            dic['k1'] = [i,]
    else:
        if "k2" in dic.keys():
            dic['k2'].append(i)
        else:
            dic['k2'] = [i,]

print(dic)

### 2、默认字典
all_list = [11,22,33,44,55,66,77,88,99,90,]
dic = collections.defaultdict(list)
for i in all_list:
    if i > 66:
        dic['k1'].append(i)
    else:
        dic['k2'].append(i)
print(dic)


```

{'k2': [11, 22, 33, 44, 55, 66], 'k1': [77, 88, 99, 90]}
defaultdict(<class 'list'>, {'k2': [11, 22, 33, 44, 55, 66], 'k1': [77, 88, 99, 90]})

## 可命名元组（namedtuple)


```python
### 根据nametuple可以创建一个包含tuple所有功能以及其他功能的类型。 

from collections import namedtuple #创建(给元组命名) 
Mytuple = namedtuple('Mytuple',['x','y','z']) 
obj = Mytuple(11,22,33) #通过x,y,z取得元组的值 
print(obj.x )
print(obj.y )
print(obj.z )

```

  11
  22
  33
    

## 双向队列（deque) 



```python
from collections import deque #创建双向队列 
d = deque() 
d.append('1') 
d.append('2')

# append()向队列中插入数据（从右边插入） 
d.append('3') 
print(d) 


```

deque(['1', '2', '3'])
    


```python
# appendleft()向队列中插入数据（从左边插入） 
d.appendleft('4') 
print(d) 

```

deque(['4', '1', '2', '3'])
    


```python
## clear()清空队列 
d.clear() 
print(d) 

```

deque([])



```python
# count()计数 
d.append('1') 
print(d) 
d.count('1') 

```

deque(['1'])

1




```python
# extend()从右边向队列添加额外元素 
d.extend(['qq','ww','ee']) 
print(d) 



```

deque(['1', 'qq', 'ww', 'ee'])
    


```python
## extendleft()从左边向队列添加元素 
d.extendleft(['qq','ww','ee']) 
print(d) 




```

deque(['ee', 'ww', 'qq', '1', 'qq', 'ww', 'ee'])



```python
# index()取得元素下标 
d.index('1') 




```




3




```python
# insert()指定位置插入元素 
d.insert(1,'nn') 
print(d) 



```

deque(['ee', 'nn', 'ww', 'qq', '1', 'qq', 'ww', 'ee'])



```python
# pop()从右边移除一个元素 
d.pop() 

print(d) 
deque(['1','nn'])



```

deque(['ee', 'nn', 'ww', 'qq', '1', 'qq', 'ww'])





deque(['1', 'nn'])




```python
# popleft()从左边移除一个元素 
d.popleft() 
print(d) 



```

deque(['nn', 'ww', 'qq', '1', 'qq', 'ww'])
    


```python
# remove()移除指定元素 
d.remove('1') 
print(d) 
deque(['2'])



```

  deque(['nn', 'ww', 'qq', 'qq', 'ww'])





  deque(['2'])




```python
# reverse()反转队列 
print(d) 
d.reverse() 
print(d) 
deque(['2','1'])


```

  deque(['nn', 'ww', 'qq', 'qq', 'ww'])
  deque(['ww', 'qq', 'qq', 'ww', 'nn'])
  deque(['2', '1'])




```python
## rotate()将右边指定的元素个数移到队列左边 
d.append('4') 
d.append('5') 
d.append('6') 
print(d) 
d.rotate(3) 
print(d) 


```

  deque(['ww', 'qq', 'qq', 'ww', 'nn', '4', '5', '6'])
  deque(['4', '5', '6', 'ww', 'qq', 'qq', 'ww', 'nn'])

## 单向队列（先进先出 FIFO ）



```python
import queue # 创建单向队列 
>>> q = queue.Queue()

1.添加元素 
>>> q.put('11') 
>>> q.put('22')

2.qsize()获取队列中元素个数 
>>> q.qsize() 
2

3.get()取得元素（先进先出) 
>>> q.get() 
11 
>>> q.get() 
22
```



# 30、Python中的Json解析模块









﻿

@Author：Runsen

## 什么是json


JSON(JavaScript Object Notation, JS 对象简谱) 是一种轻量级的数据交换格式。


它基于 ECMAScript (欧洲计算机协会制定的js规范)的一个子集，采用完全独立于编程语言的文本格式来存储和表示数据。简洁和清晰的层次结构使得 JSON 成为理想的数据交换语言。 易于人阅读和编写，同时也易于机器解析和生成，并有效地提升网络传输效率。

## JS对象

```python
var teacher_1 = {
    name: ‘Runsen’,
    age: 18,
    feature : [‘高’, ‘富’,  ‘帅’]
}
```

## JSON字符串

```python
{
    “name”: “Runsen”,
    “age”: 18,
    “ feature “ : [‘高’, ‘富’,  ‘帅’]
}
```

## Python字典

```python
{
    ‘name’: ‘Runsen’,
    ‘age’: 18
    ‘feature’ : [‘高’, ‘富’,  ‘帅’]
}
```

注意点：

- 字符串必须用双引号（即：””）来包括
- 值可以是字符串、数字、true、false、null、列表，或字典。




![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS8wYjY2OTcxNC02ZDg3LTQyOTItYjBiZC02OWQ4MGVhZTQxNmEucG5n?x-oss-process=image/format,png)

## Json模块API

常用json就知道，json模块提供了四个常用的方法：dumps、dump、loads、load，用于字符串 和 python数据类型间进行转换。


- json.dumps(obj)    --> 将python数据转化为json

Indent实现缩进，ensure_ascii 是否用ascii解析 

- json.loads(s)      -->将json数据转换为python的数据

- json.dump(obj, fp)  -->转换为json并保存到文件中

- json.load(fp) -->  从文件中读取json，并转化为python数据

## Json模块使用


```python
import json
my_dict = {'a':'1','b':'2','c':'3','d':'4'}
print(type(my_dict))
a = json.dumps(my_dict)
print(a)
print(type(a))
b=json.loads(a)
print(b)
print(type(b))
OUT：
<class 'dict'>
{"a": "1", "b": "2", "c": "3", "d": "4"}
<class 'str'> #json的字符串
{'a': '1', 'b': '2', 'c': '3', 'd': '4'}
<class 'dict'>
——————————
>>> import json
>>> print (json.dumps('中国'))
"\u4e2d\u56fd"
>>> print(json.dumps('中国', ensure_ascii=False))
"中国"
——————————
#json.dump() 和 json.load() 来编码和解码JSON数据,用于处理文件。

import json
my_dict = {'a':'1','b':'2','c':'3','d':'4'}
json.dump(my_dict,open('a.txt','w'))
print(json.load(open('a.txt','r')))
OUT:
会生成一个“a.txt"文件
{'a': '1', 'b': '2', 'c': '3', 'd': '4'}
```



# 31、Python读写docx文件



﻿

@Author：Runsen

## Python读写docx文件


Python读写word文档有现成的库可以处理

`pip install python-docx`安装一下。
https://python-docx.readthedocs.io/en/latest/

学习官网： http://python-docx.readthedocs.org/en/latest/



```python
import docx
# 新建,打开,保存文件。

import docx
#新建文档
doc_new = docx.Document()
# 保存文档
doc_new.save('demo.docx')
#读取文档
doc = docx.Document('demo.docx')
```

 **python-docx包含了word文档的相关对象**

- doc.paragraphs    #段落
- doc.tables        #表格
- doc.sections      #节  
- doc.styles        #样式
- doc.inline_shapes   #内置图形


```python
# 插入段落。

doc.add_paragraph('第一段',style=None) #插入一个段落，文本为“第一段”
#默认是不应用样式，这里也可以不写style参数，或者指定一个段落样式

doc.add_paragraph('第二段',style='Heading 2')
#这些样式都是word默认带有的样式，可以直接罗列出来有哪些段落样式
print ([s.name for s in doc.styles if s.type==1])

```

    ['Normal', 'Header', 'Footer', 'Heading 1', 'Heading 2', 'Heading 3', 'Heading 4', 'Heading 5', 'Heading 6', 'Heading 7', 'Heading 8', 'Heading 9', 'No Spacing', 'Title', 'Subtitle', 'List Paragraph', 'Body Text', 'Body Text 2', 'Body Text 3', 'List', 'List 2', 'List 3', 'List Bullet', 'List Bullet 2', 'List Bullet 3', 'List Number', 'List Number 2', 'List Number 3', 'List Continue', 'List Continue 2', 'List Continue 3', 'macro', 'Quote', 'Caption', 'Intense Quote', 'TOC Heading']



```python
# 新增样式
from docx.shared import RGBColor #这个是docx的颜色类
#新建文档
#新增样式(第一个参数是样式名称，第二个参数是样式类型：1代表段落；2代表字符；3代表表格)
style = doc.styles.add_style('style name 1', 2)
#设置具体样式(修改样式字体为蓝色，当然还可以修改其他的)
style.font.color.rgb = RGBColor(0x0, 0x0, 0xff)
```


```python
# 字符样式
# 插入一个空白段落
p = doc.add_paragraph('')
# 写入
p.add_run('毛利1', style="Heading 1 Char")
p.add_run('毛利2')
p.add_run('毛利3', style="Heading 2 Char")
#这样一个段落就应用了两个字符样式，中间“毛利”就没应用样式
print(p.text) #输出结果是u'123456789' 也还是连续的

```

    毛利1毛利2毛利3



```python
# 设置字体
r = p.add_run('毛利4')
r.font.bold = True    #加粗
r.font.italic = True  #倾斜 
```


```python
# 表格操作

#新建一个2x3的表格，style可以不写
table=doc.add_table(rows=2,cols=3,style=None)
#可以用table 的rows和columns得到这个表格的行数和列数
print (len(table.rows))
print (len(table.columns))
#遍历表格rows
for index,row in enumerate(table.rows):
    row.cells[0].text = '毛利{}'.format(index)
    print(row.cells[0].text)

#新增行或列
table.add_row()
table.add_column(width=1)
```

    2
    3
    毛利0
    毛利1



    <docx.table._Column at 0x17a7f928128>





```python
# 官方例子
from docx import Document
from docx.shared import Inches

document = Document()

document.add_heading('Document Title', 0)
# 段落
p = document.add_paragraph('A plain paragraph having some ')
p.add_run('bold').bold = True
p.add_run(' and some ')
p.add_run('italic.').italic = True
# 
document.add_heading('Heading, level 1', level=1)
document.add_paragraph('Intense quote', style='Intense Quote')

document.add_paragraph(
    'first item in unordered list', style='List Bullet'
)
document.add_paragraph(
    'first item in ordered list', style='List Number'
)

# document.add_picture('monty-truth.png', width=Inches(1.25))

records = (
    (3, '101', 'Spam'),
    (7, '422', 'Eggs'),
    (4, '631', 'Spam, spam, eggs, and spam')
)

table = document.add_table(rows=1, cols=3)
hdr_cells = table.rows[0].cells
hdr_cells[0].text = 'Qty'
hdr_cells[1].text = 'Id'
hdr_cells[2].text = 'Desc'
for qty, id, desc in records:
    row_cells = table.add_row().cells
    row_cells[0].text = str(qty)
    row_cells[1].text = id
    row_cells[2].text = desc

document.add_page_break()

document.save('demo1.docx')

```




![](https://img-blog.csdnimg.cn/20190505223424346.png)




![](https://img-blog.csdnimg.cn/20190505223505857.png)
参考： http://python-docx.readthedocs.org/en/latest/

# 32、教你Python制作简单的二维码









﻿@Author：Runsen


## 安装MyQR

cmd 窗口中用 pip 命令安装

```
pip install MyQR
```


这个库提供了两种使用方法，一种是直接使用命令行的方式，另外一种使用import引入

先在最原始的IDE上

```
from MyQR import myqr
myqr.run('1234567')
```

![](https://img-blog.csdnimg.cn/20190425123522141.png)

在看下源码
![](https://img-blog.csdnimg.cn/20190425123316449.png)

位置参数
单词：STR

可选参数
版本：int，从1到40

级别：str，仅限其中一个（l'、'm'、'q'、'h'）

picutre:str，图像的文件名

着色：布尔

constrast:浮动

亮度：浮动

保存“name:str”，输出文件名如“example.png”

save_dir:str，输出目录

![](https://img-blog.csdnimg.cn/20190425131139766.png0)


```
from MyQR import myqr
myqr.run(words='123456',picture='1.jpg',save_name='demo.png',colorized=True)
```

![](https://img-blog.csdnimg.cn/20190425124718125.png)

## 动图

```
from MyQR import myqr
myqr.run(words='https://www.baidu.com',picture='1.gif',save_name='demo1.gif',colorized=True)
```

![](https://img-blog.csdnimg.cn/20190425125335676.gif)


第二种cmd下的方法

参数

```shell
'''
myqr     Words
        [-v {1,2,3,...,40}]
        [-l {L,M,Q,H}]
        [-n output-filename]
        [-d output-directory]
        [-p picture_file]
        [-c]
        [-con contrast]
        [-bri brightness]
'''
```


-v 参数是控制二维码边长的，范围 1至40，数字越大边长越大；

-l 控制纠错水平，范围是L、M、Q、H，从左到右依次升高。默认纠错等级是最高级的H。

-n 控制文件名，格式可以是 .jpg， .png ，.bmp ，.gif ；

-d 控制位置，控制二维码图片的保存位置。

-p 参数可以把原二维码和同目录下另一张图片结合形成新的黑白艺术二维码。

-con 用以调节图片的对比度，1.0 表示原始图片，更小的值表示更低对比度，更大反之。默认为1.0。

-bri 用来调节图片的亮度，其余用法和取值与 -con 相同。


![](https://img-blog.csdnimg.cn/20190425125634355.png)

![](https://img-blog.csdnimg.cn/2019042512570917.png)



![](https://img-blog.csdnimg.cn/20190425125721429.png)


![](https://img-blog.csdnimg.cn/20190425130043254.png)


![](https://img-blog.csdnimg.cn/2019042513010215.gif)

![](https://img-blog.csdnimg.cn/20190425130513425.png)


![](https://img-blog.csdnimg.cn/20190425130523197.png)

## 搜索范冰冰


```python
from MyQR import myqr
myqr.run(words='https://www.baidu.com/s?wd=%E8%8C%83%E5%86%B0%E5%86%B0&rsv_spt=1&rsv_iqid=0xa48f245a0000d799&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf8&tn=baiduhome_pg&rsv_enter=1&rsv_sug3=12&rsv_sug1=10&rsv_sug7=100&rsv_t=b7
a30UsfuYzvKe8JVKCYqvrCF%2FVdbjT%2B0viM0p7fh8j%2BUKcUaEJF%2FTojpsWfmTDc%2FL5s&rsv_sug2
=0&inputT=3459&rsv_sug4=3459&rsv_sug=1',picture='2.png',save_name='demo1.png',colorized=True)
```



![](https://img-blog.csdnimg.cn/20190425132652811.png)


出现的问题：cannot write mode RGBA as JPEG


原因：RGBA意思是红色，绿色，蓝色，Alpha的色彩空间，Alpha指透明度。而JPG不支持透明度，所以要么丢弃Alpha,要么保存为.png文件


```python
from PIL import Image
image = Image.open('2.jpg')
# image = image.convert("RGB") 
image.save("2.png")
```

# 33、自从我会了Python中的PIL，发现了其实超级简单

﻿PIL全称是Python Image Library，顾名思义，是用来做图像处理的。

## 了解PIL

`PIL` (Python Image Library) 已经算是 `Python` 处理图片的标准库了，兼具强大的功能和简洁的` API.`
但是`PIL`库的更新非常缓慢， 并且它只支持到`python2.7`，不支持`python3`

由于PIL库更新太慢了，于是于是一群志愿者在PIL库的基础上创建了一个新的分支版本，命名为`Pillow`.

`Pillow`目前最新支持到`python3.6`，它的维护和开发十分活跃，兼容PIL库的绝大多数语法，并且增加了许多新的特性，推荐直接使用`Pillow`

## 概念了解


PIL中所涉及的基本概念有如下几个：

- 通道(bands)
- 尺寸(size)
- 坐标系统(coordinate system)



### 通道

每张图片都是由一个或者多个数据通道构成，如果这些通道具有相同的维数和深度，PIL允许将这些通道进行叠加

以RGB图像为例，每张图片都是由三个数据通道叠加构成，分别为R 、G 、B。

对于灰度图像（没有色彩的图片， RGB色彩分量全部相等），只有一个通道。

灰度指的是黑白图像中点的颜色深度，范围一般是0到255， 白色为255，黑色为0

## 图片尺寸
指的是图片的宽度和高度

通过size属性可以获取图片的尺寸，它的返回值是一个元祖，元祖里面有两个值，分别是水平和垂直方向上的像素个数

### 坐标系统

PIL使用笛卡尔像素坐标系统，图像的左上角为左边的原点（0，0），这就意味着，x轴的数值是从左到右增长的，y轴的数值是从上到下增长的。 

在我们处理图像的时候，常常需要去表示一个矩形的图像区域。Pillow中很多方法都需要传入一个表示矩形区域的元祖

这个元祖包含四个值，分别表示矩形四条边距离x轴或者y轴的距离。顺序是（左，顶，右，底）
例如，一个800x600的像素图像表示为（0， 0， 800， 600）







我们可以用PIL干嘛呢？

第一，可以将两张图片合并在一起

**Image.blend(image1,image2,alpha)**




合成公式为：out=image1(1.0- alpha)+image2alpha

```python
from PIL import Image
im1 = Image.open("1.jpg")
im2 = Image.open("2.jpg")
print(im1.mode,im1.size)  # RGB (500, 300)
print(im2.mode,im2.size)   # RGB (500, 300)
im = Image.blend(im1, im2, 0.5)
im.save('3.jpg')
```

这是1.jpg
![](https://img-blog.csdnimg.cn/20190502220733889.jpg)
这是2.jpg
![](https://img-blog.csdnimg.cn/20190502220739252.jpg)


这是3.jpg



![合成后的图片](https://img-blog.csdnimg.cn/2019050222074462.jpg)

当然除了上面的方法还可以使用Composite类
Image.composite(image1,image2, mask) ⇒ image
复合类使用给定的两张图像及mask图像作为透明度，插值出一张新的图像。变量mask图像的模式可以为“1”，“L”或者“RGBA”。所有图像必须有相同的尺寸。


看一波源码，如下图所示


![](https://img-blog.csdnimg.cn/20190502221303486.png)


一波代码开干


```python
from PIL import Image
im1 = Image.open("1.jpg")
im2 = Image.open("2.jpg")
r,g,b = im1.split()
print(b.mode)
print(im1.mode,im1.size)
print(im2.mode,im2.size)
im = Image.composite(im1,im2,mask=b)
im.save('4.jpg')
```

这是4.jpg




![](https://img-blog.csdnimg.cn/20190502222239658.jpg)

## Filter类

im.filter(filter) ⇒ image


返回一个使用给定滤波器处理过的图像的拷贝。在该模块中，预先定义了很多增强滤波器，可以通过filter()函数使用，预定义滤波器包括：

- BLUR
- CONTOUR
- DETAIL
- EDGE_ENHANCE
- EDGE_ENHANCE_MORE
- EMBOSS
- FIND_EDGES
- SMOOTH


再看一波源码，如下图所示



![](https://img-blog.csdnimg.cn/20190502223542859.png)


一波代码开干


```python
from PIL import Image
from PIL import ImageFilter                         ## 调取ImageFilter
img = Image.open("1.jpg")
blu = img.filter(ImageFilter.BLUR)                ##均值滤波
con = img.filter(ImageFilter.CONTOUR)             ##找轮廓
edge = img.filter(ImageFilter.FIND_EDGES)         ##边缘检测
blu.save('均值滤波.jpg')
con.save('找轮廓.jpg')
edge.save('边缘检测.jpg')
```

这是均值滤波.jpg



![](https://img-blog.csdnimg.cn/20190502223351590.jpg)

这是找轮廓.jpg



![](https://img-blog.csdnimg.cn/20190502223356699.jpg)

这是边缘检测.jpg



![](https://img-blog.csdnimg.cn/20190502223400421.jpg)

## PIL所有操作

原图
![1.jpg](https://img-blog.csdnimg.cn/20190328222744357.jpg)

```python
# 导入模块
from PIL import Image
# 打开图片
image = Image.open('1.jpg')
image.show()
# 新建图片
newImage= Image.new('RGB', (100, 100), 'red')
newImage.save('new.jpg')
# 获得图像尺寸:
w, h = image.size
print('原本图像大小: %sx%s' % (w, h))
# 缩放到50%:
image.thumbnail((w//2, h//2))
print('缩放后图片的大小: %sx%s' % (w//2, h//2))
# 把缩放后的图像用jpeg格式保存:
image.save('2.jpg', 'jpeg')
# 复制图片
image2 = image.copy()
image2.save("3.jpg")
```

剪切 粘贴，合并图像

```python
# 剪切图片
# 设置要拷贝的区域
box = (0, 0, 100, 100)
image3 = image.crop(box)
image3.save("4.jpg")
# 这个region可以用来后续的操作(region其实就是一个Image对象)
region = image.crop(box)
# 处理复制的矩形选区并粘贴到原图
region = region.transpose(Image.ROTATE_180)
image.paste(region, box)
image.save('5.jpg')
```

旋转和翻转图像

```python
# 保持原图像不变。逆时针旋转。
image.rotate(90).save('6.jpg')
# 水平翻转，
image.transpose(Image.FLIP_LEFT_RIGHT).save('7.jpg')
# 垂直翻转
image.transpose(Image.FLIP_TOP_BOTTOM).save('8.jpg')
```

过滤操作

```python
from PIL import Image, ImageFilter
im = Image.open('1.jpg')
# 高斯模糊
im.filter(ImageFilter.GaussianBlur).save(r'高斯模糊.jpg')
# 普通模糊
im.filter(ImageFilter.BLUR).save(r'普通模糊.jpg')
# 边缘增强
im.filter(ImageFilter.EDGE_ENHANCE).save(r'边缘增强.jpg')
# 找到边缘
im.filter(ImageFilter.FIND_EDGES).save(r'找到边缘.jpg')
# 浮雕
im.filter(ImageFilter.EMBOSS).save(r'浮雕.jpg')
# 轮廓
im.filter(ImageFilter.CONTOUR).save(r'轮廓.jpg')
# 锐化
im.filter(ImageFilter.SHARPEN).save(r'锐化.jpg')
# 平滑
im.filter(ImageFilter.SMOOTH).save(r'平滑.jpg')
# 细节
im.filter(ImageFilter.DETAIL).save(r'细节.jpg')
```

![](https://img-blog.csdnimg.cn/20190328223500732.jpg)

# 34、使用pytesser3 和pillow完成图形验证码的识别





﻿

@Author: Runsen

## 灰度化


像素点是最小的图片单元，一张图片由很多像素点构成，一个像素点的颜色是由RGB三个值来表现的，所以一个像素点对应三个颜色向量矩阵，我们对图像的处理就是对这个像素点的操作。

图片的灰度化，就是让像素点矩阵中的每一个像素点满足 R=G=B，此时这个值叫做灰度值，白色为0，黑色为255
灰度转化一般公式为：


`R=G=B = 处理前的 RX0.3 + GX0.59 + B*0.11`


```
from PIL import Image
image = Image.open('code.jpg')
im = image.convert('L')
```

## 二值化


图像的二值化，就是将图像的像素点矩阵中的每个像素点的灰度值设置为0（黑色）或255（白色），从而实现二值化，将整个图像呈现出明显的只有黑和白的视觉效果。

二值化原理是利用设定的一个阈值来判断图像像素是0还是255， 一般小于阈值的像素点变为0， 大于的变成255

这个临界灰度值就被称为阈值，阈值的设置很重要，阈值过大或过小都会对图片造成损坏

选择阈值的原则是：既要尽可能保存图片信息，又要尽可能减少背景和噪声的干扰


常用阈值选择的方法是：


- 灰度平局值法： 取127 （0~255的中数， （0+255）/2 = 127）

- 平均值法：

计算像素点矩阵中的所有像素点的灰度值的平均值avg
        

- 迭代法：

选择一个近似阈值作为估计值的初始值，然后进行分割图像，根据产生的子图像的特征来选取新的阈值，在利用新的阈值分割图像，经过多次循环，使得错误分割的图像像素点降到最小。

## 降噪

经过了二值化处理，整个图片像素就被分为了两个值0和255.

如果一个像素点是图片或者干扰因素的一部分，那么她的灰度值一定是0（黑色），如果一个点是背景，其灰度值应该是255，白色

所以对于孤立的噪点，他的周围应该都是白色，或者大多数点都是白色的，所以在判断的时候条件应该放宽，一个点是黑色并且相邻的点为白色的点的个数大于一个固定的值，那么这个点就是噪点。

我们根据一个点A的RGB值，与周围的8个点的RBG值比较，设定一个值N（0 <N <8），当A的RGB值与周围8个点的RGB相等或者小于N时，此点为噪点


下面是用比较古老的`pytesser3`识别验证码

pytesser3 的安装
`pip install pytesser3`

先安装`Tesseract` ，下载好后

将Tesseract.exe 和 `testdata` 复制到 `pytesser3`文件中
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190331224106775.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)

将pytesser3包下面__init__文件内tesseract_exe_name的值设置为为你的tesseract.exe的路径



![在这里插入图片描述](https://img-blog.csdnimg.cn/20190331224114649.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190331224118834.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)

```python
# -*- coding：utf-8 -*-
# time ：2019/3/30 22:03
# author: 毛利
from pytesser3 import image_to_string
from PIL import Image

def binazing(image):
    '''
    对图片进行灰度和二值化
    :param image:
    :return:
    '''
    image = image.convert('L')
    w,h = image.size
    # print(w,h)
    ### 二值化
    pixdata = image.load()
    for i in range(h):
        for j in range(w):

            if pixdata[j,i] > 170:
                pixdata[j,i] = 255
            else:
                pixdata[j, i] = 0
    return image

def depoint(image):
    '''
    对图片进行降噪
    :param image:
    :return:
    '''
    pixdata = image.load()
    w,h = image.size
    for y in range(1,h-1):
        for x in range(1,w-1):
            count = 0
            if pixdata[x,y-1] >245:
                count =count +1
            if pixdata[x,y+1] >245:
                count =count +1
            if pixdata[x-1,y] >245:
                count =count +1
            if pixdata[x+1,y] >245:
                count =count +1
            if pixdata[x-1, y - 1] > 245:
                count = count + 1
            if pixdata[x+1, y + 1] > 245:
                count = count + 1
            if pixdata[x - 1, y+1] > 245:
                count = count + 1
            if pixdata[x + 1, y-1] > 245:
                count = count + 1
            if count>4:
                pixdata[x,y] =255
    return image

if __name__ == '__main__':
    image = Image.open('111.jpg')
    image = binazing(image)
    image = depoint(image)
    image.show()
    print(image_to_string(image))

####输出结果#####
TBQL
```




这是111.jpg


![](https://imgconvert.csdnimg.cn/aHR0cDovL3B3ZmdtOWZqby5ia3QuY2xvdWRkbi5jb20vRmotSXZrRE9oTWJkcm9GRy1oT1RET2dCRG1zWg?x-oss-process=image/format,png)

# 35、Python在window平台打包工具pyinstaller

﻿Java 一次编译到处运行，Python没有这么好本事，但是也有一个pyinstaller可以打包exe，在window平台下运行

## pyinstaller

安装`pip install pyinstaller`，参数如下


| 参数          | 含 义                                 |
| ------------- | ------------------------------------- |
| -F            | 只生成一个exe文件                     |
| –distpath     | 指定生成的exe存放的目录               |
| –workpath     | 指定编译中临时文件存放的目录          |
| -i            | 创建一个目录包含：exe文件、依赖文件   |
| -F            | 指定exe图标                           |
| -p            | 指定exe依赖的包、模块                 |
| -d            | 编译为debug模式，获取运行中的日志信息 |
| -clean        | 清理编译时临时文件                    |
| -c            | 使用控制台                            |
| -w            | 使用窗口                              |
| -version-file | 添加exe版本信息                       |

## 计算机小助手例子


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

## 注意点：


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

# 36、上篇 | 教你玩转tkinter窗口





现在极少有人会用上tkinter了，所以真正研究的人也就更少了，还是学下tkinter吧，其实这个东西真他妈简单。




tkinter 是内置的模块，无需安装

## 窗口主体框架

每一个 tkinter 应用的主体框架都可以包含下面这部分. 定义 window 窗口 和 window的一些属性, 然后书写窗口内容, 最后执行window.mainloop让窗口活起来.

```python
import tkinter as tk
window = tk.Tk()
window.title('my window')
window.geometry('200x100')

# 这里是窗口的内容
window.mainloop()

```


![](https://img-blog.csdnimg.cn/20200516171208131.png)

## 窗口内容

这次我们会建立一个用来描述的标签 tk.Label, 比如:

```python
import tkinter as tk
window = tk.Tk()
window.title('my window')
window.geometry('200x100')



l = tk.Label(window, 
    text='OMG! this is TK!',    # 标签的文字
    bg='green',     # 背景颜色
    font=('Arial', 12),     # 字体和字体大小
    width=15, height=2  # 标签长宽
    )
l.pack()    # 固定窗口位置

window.mainloop()

```

![](https://img-blog.csdnimg.cn/20200516171306182.png)

## 控件

上面的Label就是一个控件，还有很多的，如按钮，标签和文本框等，如下图所示

![](https://img-blog.csdnimg.cn/20200516171415379.png)



控件自带的共同属性，如大小，字体和颜色等。可根据控件展现形式选择相应的属性，具体属性如下表：




![](https://img-blog.csdnimg.cn/20200516171433691.png)

## tkinter绑定事件

tkinter绑定事件，就是定义一个函数，然后通过command属性传入函数名，下面通过Button绑定事件，点击就出现Runsen爱学习

```css
from tkinter import *

def p_label():
    global root
    Lb = Label(root, text='Runsen爱学习')
    Lb.pack()

root = Tk()
root.title("应用程序窗口")
B_n = Button(root, text='点我', command=p_label, bg='red')  # command后面不能有任何的标点符号
B_n.pack()
root.mainloop()
```


![](https://img-blog.csdnimg.cn/20200516171815987.png)

## 布局显示

一个窗口都应该有布局，就是pack的时候需要设置side，expand需要扩展吗，fill需要填充吗

```css
from tkinter import *
root = Tk()
root.title("应用程序窗口")
Button(root,text='1').pack(side=LEFT,expand=YES,fill=Y)
Button(root,text='2').pack(side=TOP,expand=YES,fill=BOTH)
Button(root,text='3').pack(side=RIGHT,expand=YES,fill=NONE)
Button(root,text='4').pack(side=LEFT,expand=NO,fill=Y)
Button(root,text='5').pack(side=TOP,expand=YES,fill=BOTH)
Button(root,text='6').pack(side=BOTTOM,expand=YES)
Button(root,text='7').pack(anchor=SE)
root.mainloop()
```

![](https://img-blog.csdnimg.cn/20200516172055242.png)


除了pack还有一个grid，grid将组件布局为表格


下面做一个电话拨号盘GUI

```css
from tkinter import *
root = Tk()
labels = [['1','2','3'], # 文本，布局为网格
          ['4','5','6'],
          ['7','8','9'],
          ['*','0','#']]

for r in range(4): # 行循环
    for c in range(3): # 列循环
        label = Label(root,
                      relief=RAISED, # 设置边框格式
                      padx=10, # 加宽标签
                      text=labels[r][c]) # 标签文本
        label.grid(row=r, column=c) # 将标签放置在r行c列
root.mainloop()
```

![](https://img-blog.csdnimg.cn/20200516172458594.png)

## 制作一个日历


上面教你做一个电话拨号盘GUI，下面能做一个简单的日历吗？


我看你就不会，不是我瞧不起你

![](https://img-blog.csdnimg.cn/20200516173244403.png)


放心，有我这个大佬在。这需要导入calendar模块了，


![](https://img-blog.csdnimg.cn/20200516173605591.png)

```css
import calendar
from tkinter import *
root = Tk()
labels = [['Mon','Tue','Wed','Thu','Fri','Sat','Sun']]

MonthCal = calendar.monthcalendar(2020, 5) 
for i in range(len(MonthCal)):
    labels.append(MonthCal[i])
for r in range(len(MonthCal)+1):
    for c in range(7):
        if labels[r][c] == 0:
            labels[r][c] = ' '
        label = Label(root,          
                      padx=5,
                      pady=5,
                      text=str(labels[r][c]))        
        label.grid(row=r,column=c)
root.mainloop()
```

![](https://img-blog.csdnimg.cn/20200516173714374.png)

## 丰富我们的日历

上面的日历就是一个辣鸡，啥功能都没有，需求很简单，就是来两个按钮实现向上翻，向下翻。


向上翻，向下翻两个按钮就需要清空界面，再把日历加到labels列表中  ，放置日历。好像很简单，其实就是这么简单。

大家想一想，怎么做出来。

我还是给标准实现代码


```css
#@Author： Runsen
import calendar 
from tkinter import *
root = Tk()


def LabelCal(Year, Month):
    # 首行放置“年、月”的位置
    label = Label(root,text=str(Year)+"年")
    label.grid(row=0,column=2)
    label = Label(root,text=str(Month)+"月")
    label.grid(row=0,column=4)
    # labels列表：放置“星期”的标题
    labels = [['Mon','Tue','Wed','Thu','Fri','Sat','Sun']]
    # 用calendar库计算日历
    MonthCal = calendar.monthcalendar(Year, Month)
    # 先把界面清空
    for r in range(7):
        for c in range(7):            
            label = Label(root,
                          width =5,
                          padx=5,
                          pady=5,
                          text=' ')        
            label.grid(row=r+1,column=c)
    # 把日历加到labels列表中     
    for i in range(len(MonthCal)):
        labels.append(MonthCal[i])
    # 放置日历
    for r in range(len(MonthCal)+1):
        for c in range(7):
            if labels[r][c] == 0:
                labels[r][c] = ' '
            label = Label(root,
                          width =5,
                          padx=5,
                          pady=5,
                          text=str(labels[r][c]))        
            label.grid(row=r+1,column=c) # 网格布局


# 默认日期
Year, Month = 2020,5
LabelCal(Year, Month)
        
# button：Enter
def ButtonPrevious():
    global Year, Month
    Month = Month-1
    if Month<1:
        Month = Month+12
        Year = Year-1
    LabelCal(Year, Month)
    
button1 = Button(root, text='Previous', command=ButtonPrevious)
button1.grid(row=len(MonthCal)+3, column=0)


# button：Clear
def ButtonNext():
    global Year, Month
    Month = Month+1
    if Month>12:
        Month = Month-12
        Year = Year+1 
    LabelCal(Year, Month)
    
button2 = Button(root, text='Next', command=ButtonNext)
button2.grid(row=len(MonthCal)+3, column=6)

root.mainloop()
```

运行一波，来一个gif图

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051617494865.gif)





# 37、下篇 | tkinter实现一个翻译软件

@Author : Runsen


下面使用 tkinter实现一个翻译软件，我们用的有道云翻译


我先试下把访问的url搞出来
![](https://img-blog.csdnimg.cn/2020051618303574.png)


![](https://img-blog.csdnimg.cn/20200516183545919.png)
你可以查看这些参数，都是请求的参数，这需要进一步找的，不是我不会，是我写过，看下面的文章


[JS逆向有道云翻译](https://maoli.blog.csdn.net/article/details/103609133)




有道翻译的网址原本不是代码中所展现的，但是这个是有道最原始的`url = 'http://fanyi.youdao.com/translate?smartresult=dict&smartresult=rule'`



现在的url估计是担心别人爬的多，所以就加了一些不必要的参数。因为是零基础专栏，就用最原始的url。


给出代码吧


```python
# -*- coding：utf-8 -*-
# time ：2019/5/2 23:44
# author: 毛利
import requests
from tkinter import *
from tkinter import messagebox
import time
def translation():

    # 接受用户的信息
    content = entry.get()
    if content =='':
        messagebox.showinfo('提示','请输入要翻译的内容')
    else:
        # url = 'http://fanyi.youdao.com/translate_o?smartresult=dict&smartresult=rule'
        url = 'http://fanyi.youdao.com/translate?smartresult=dict&smartresult=rule'
        data  ={
            'i':content,
            'from': 'AUTO',
            'to': 'AUTO',
            'smartresult': 'dict',
            'client': 'fanyideskweb',
            # 时间戳  14位
            # 'salt': '15568459610827',
            # 'sign': '9494fda01d62399b1a3476280a82c990',
            # 时间戳13位
            # 'ts': '1556845961082',
            # 'bv': 'd6c3cd962e29b66abe48fcb8f4dd7f7d',
            'doctype': 'json',
            'version': '2.1',
            'keyfrom': 'fanyi.web',
            'action': 'FY_BY_REALTlME',
        }

        result = requests.post(url,data)
        tarn = result.json()['translateResult'][0][0]['tgt']
        res.set(tarn)
        print(tarn)



# 创建窗口
root = Tk()

# 窗口标题

root.title('翻译软件')

# 窗口大小 小写的x 不是370*100
root.geometry('370x100')
# 窗口位置
root.geometry('+500+300')
# root.geometry('300x100+500+300')

# 标签控件 font = ('微软雅黑',12)
label = Label(root,text ='输入要翻译的文字')

# 定位  pack 包  place 位置
label.grid(row=0,column =0)
# fg = 'red' 字体颜色
label1 = Label(root,text ='翻译之后的结果:')
label1.grid(row =1,column= 0)
# 输入控件
entry = Entry(root,font =('微软雅黑',15))
entry.grid(row=0,column = 1)
# 翻译之后的结果

res = StringVar()
entry1 = Entry(root,font =('微软雅黑',15),textvariable=res)
entry1.grid(row=1,column = 1)

# 点击按钮

button = Button(root,text="翻译",width=10,command = translation)
# sticky 对齐方式 N S E W
button.grid(row=2,column=0,sticky=W)

button1 = Button(root,text  ='退出',width=10,command = root.quit)
button1.grid(row=2,column = 1,sticky=E )
# 消息循环
root.mainloop()

```


![在这里插入图片描述](https://img-blog.csdnimg.cn/2019050310370113.png)

打包 ptyinstaller -F demo.py

# 38、练习、Python**判断一个信用卡号是否合理**





﻿@Author: Runsen

这个一个编程题

一个信用卡号必须是13到16位的整数



1954年，IBM的Hans Luhn提出一种算法，用于验证信用卡号的有效性。

这个算法在确定输入的卡号是否正确，或者这张信用卡是否被扫描仪正确扫描方面是非常有用的。




- **4，指Visa信用卡**  
- **5，指Master万事达卡**
- **37，指American Express 国际信用卡**
- **6，指Discover 信用卡**



遵循这个合法性检测可以生成所有的信用卡号，通常称之为Luhn检测或者Mod 10检测，可以如下描述（为了方便解释，假设卡号4388576018402626：

1.从右到左对偶数位数字翻倍。如果对某个数字翻倍之后的结果是一个两位数，那么就将这两位加在一起得到一位数。


![](https://img-blog.csdnimg.cn/20200330100745345.png)

2.现在将第一步得到的所有一位数相加。



![](https://img-blog.csdnimg.cn/20200330100753832.png)

3.将卡号里从右到左奇数位上的所有数字相加。


![](https://img-blog.csdnimg.cn/20200330100806932.png)







4.将第二步和第三步得到的结果相加。




![](https://img-blog.csdnimg.cn/20200330100818162.png)




5.如果第四步得到的结果能被10整除，那么卡号是合法的；否则，卡号是不合法的。

![](https://img-blog.csdnimg.cn/20200330100831819.png)

例如，号码4388576018402626是不合法的，但是号码4388576018410707是合法的。
编写程序，提示用户输入一个long型整数的信用卡号码，显示这个数字是合法的还是非法的


![](https://img-blog.csdnimg.cn/20200330100841306.png)


## 代码

```python
def isValid(number):
    # 判断是不是合法，就是计算出第四步的结果，如果整除就是合法，我们取模就可以了
    if sumOf0ddPlace(number) % 10 == 0:
    	print("信用卡号的合法")
    else:
    	print("信用卡号的不合法")

def sumOfDoubleEvenPlace(number):
	# 现在将第一步得到的所有一位数相加。这里的number传入的是int类型
	sum = 0 
	for i in str(number)[::2]:
		if int(i)*2 <10:
			sum = sum + int(i)*2
		else:
			for j in str(int(i)*2):
				sum = sum + int(j)
	return sum 

def getDigit(number):
	return sum([int(i) for i in str(number)[1::2]])

def sumOf0ddPlace(number):
	return sumOfDoubleEvenPlace(number) + getDigit(number)



number = input("用户输入一个的信用卡号码，必须是13到16位的整数")
isValid(number)

# 验证
用户输入一个的信用卡号码，必须是13到16位的整数4388576018402626
信用卡号的不合法
用户输入一个的信用卡号码，必须是13到16位的整数4388576018410707
信用卡号的合法
```

## 补充

添加  prefixMatched，判断卡号的前缀是否合法。


4，指visa卡
5，指master卡
37，指American Express卡
6，指Discovery卡



```css
def prefixMatched(number):
    if number[0] == '4' or number[0] == '5' or number[0] == '37':
        print("信用卡前缀的合法")
    elif number[:2] == '37':
        print("信用卡前缀的合法")
    else:
        print("信用卡前缀的不合法")
```





函数6：def getSize(d):   获得信用卡号的长度并将结果返回

```css
def getSize(d):
    return number[:d]
```



函数7：def getPrefix(number, k): 获得信用卡号的第k位'''


```css
def getPrefix(number, k):
    return number[k]
```



# 39、Python对象的深浅拷贝，练习冒泡排序

@Author：By Runsen

## 对象的深浅拷贝

在Python有个重要的东西，就是对象的深浅拷贝。

我们就称为：'==' vs 'is'






- == 比较对象之间的值是否相等
- is 比较的是对象身份是否相等，它们是否同一个对象


我们一般通过id来是否相等来判断是否同一个对象

```python
a = 10
b = 10

a == b
True

id(a)
4427562448

id(b)
4427562448

a is b
True

```


注意a is b == True 只适合和用于-5 到256之间，这个不知道你是否知道，我觉得面试官肯定不知道。

```python
a = 257
b = 257

a == b
True

id(a)
4473417552

id(b)
4473417584

a is b
False

```

下面我们说下，浅拷贝和深拷贝


```python
l1 = [1, 2, 3]
l2 = list(l1)

l2
[1, 2, 3]

l1 == l2
True

l1 is l2
False

s1 = set([1, 2, 3])
s2 = set(s1)

s2
{1, 2, 3}

s1 == s2
True

s1 is s2
False

```

浅拷贝指重新分配一块内存，l2 就是l1的浅拷贝，但是只要是序列的浅拷贝，他们的id就是不一样的。




对于深拷贝，在python中提供了对应的函数copy.copy()

```python
import copy
l1 = [1, 2, 3]
l2 = copy.copy(l1)

t1 = (1, 2, 3)
t2 = tuple(t1)

t1 == t2
True

t1 is t2
True

```

元组（1，2，3）只被创建一次，t1和t2同时指向这个元组，反正你看到copy.copy()就是两个True




这里有一个天天来骗小孩的东西，就是l1变了，l2变不变的问题


我这里在使用的嵌套列表


```python
l1 = [[1, 2], (30, 40)]
l2 = list(l1)

l2
[[1, 2], (30, 40)]

l1.append(100)
l1[0].append(3)

l1
[[1, 2, 3], (30, 40), 100]

l2
[[1, 2, 3], (30, 40)]
```


l2竟然变了，这是为什么。首先初始化一个列表l1，里面的元素是一个列表和元组，然后对l1执行浅拷贝，赋予了l2
，但是l2中的元素和l1指向同一个列表和元组对象，只有列表对象变，你浅拷贝就要跟着我变。

如果你添加一个序列来，我浅拷贝没有指向你新来的对象。我干嘛跟着你变。

l1.append(100)l1的列表新增元素100，不会对l2产生影响，l1和l2是两个不同的对象



**如果我在元组加呢？？？**

```python
l1[1] += (50, 60)

l1
[[1, 2, 3], (30, 40, 50, 60), 100]

l2
[[1, 2, 3], (30, 40)]

```

竟然不会变，说白了只有列表对象变，难道元组不可变你不知道？






深度拷贝，就是你爱怎么变，就去哪里变，我就不变了。



```python
import copy
l1 = [[1, 2], (30, 40)]
l2 = copy.deepcopy(l1)
l1.append(100)
l1[0].append(3)

l1
[[1, 2, 3], (30, 40), 100]

l2 
[[1, 2], (30, 40)]

```

因为此时l1和l2完全独立了，没有任何影响

总结起来其实就是两句话

- 浅拷贝，不可变的不可变，可变的依旧可变
- 深拷贝，都不可变




下面我们练习下冒泡排序

## 冒泡排序

要学习冒泡排序必须知道它的原理：

所谓冒泡，就是将元素两两之间进行比较，谁大就往后移动，直到将最大的元素排到最后面，接着再循环一趟，从头开始进行两两比较，而上一趟已经排好的那个元素就不用进行比较了。（图中排好序的元素标记为黄色柱子）

说得不清楚，我们看看下面的动图就应该明白了







下面，我们就进入代码环节。

![](https://img-blog.csdnimg.cn/20200710225406469.png)

Python实现冒泡排序
现在，我给你一个nums = [3,1,25,6,8,10,15]，要求你用Python将nums实现冒泡排序。

看上去很难入手，其实很简单，我先给出代码

```csharp
nums = [3,1,25,6,8,10,15]
for i in range(len(nums)-1):
    for j in range(len(nums) - i -1):
        if nums[j] > nums[j+1]:
            nums[j],nums[j+1] =  nums[j+1],nums[j]
        print("第"+str(j)+"次内循环"+str(nums))
    print("第"+str(i)+"次外循环"+str(nums))
print("最后的结果"+str(nums))
```

我们先遍历nums，这不就是我们的range(len(nums)-1)，至于为什么是range(len(nums)-1)，其实就是我们的下标从0开始的，len(nums)返回是7，range是左开右闭，但是冒泡排序，我们只需要取到nums[5] = 10 就足够了，所以这里range(len(nums)-1)，取到[3,1,25,6,8,10]。

然后，我们在遍历之后的nums，比如i = 0，我们将j取值范围到len(nums) - i -1，用nums[j] > nums[j+1]判断两两的大小, 每次内循环将最大的移到最右边。

每一次内循环的目的就是将当中最大的移到最右边，而每一次外循环的目的就是当最大的移到最右边后，缩小范围，再寻找最大的数，再把它移到最右边。

我们执行上面的代码的结果如下：

```python
第0次内循环[1, 3, 25, 6, 8, 10, 15]
第1次内循环[1, 3, 25, 6, 8, 10, 15]
第2次内循环[1, 3, 6, 25, 8, 10, 15]
第3次内循环[1, 3, 6, 8, 25, 10, 15]
第4次内循环[1, 3, 6, 8, 10, 25, 15]
第5次内循环[1, 3, 6, 8, 10, 15, 25]
第0次外循环[1, 3, 6, 8, 10, 15, 25]
第0次内循环[1, 3, 6, 8, 10, 15, 25]
第1次内循环[1, 3, 6, 8, 10, 15, 25]
第2次内循环[1, 3, 6, 8, 10, 15, 25]
第3次内循环[1, 3, 6, 8, 10, 15, 25]
第4次内循环[1, 3, 6, 8, 10, 15, 25]
第1次外循环[1, 3, 6, 8, 10, 15, 25]
第0次内循环[1, 3, 6, 8, 10, 15, 25]
第1次内循环[1, 3, 6, 8, 10, 15, 25]
第2次内循环[1, 3, 6, 8, 10, 15, 25]
第3次内循环[1, 3, 6, 8, 10, 15, 25]
第2次外循环[1, 3, 6, 8, 10, 15, 25]
第0次内循环[1, 3, 6, 8, 10, 15, 25]
第1次内循环[1, 3, 6, 8, 10, 15, 25]
第2次内循环[1, 3, 6, 8, 10, 15, 25]
第3次外循环[1, 3, 6, 8, 10, 15, 25]
第0次内循环[1, 3, 6, 8, 10, 15, 25]
第1次内循环[1, 3, 6, 8, 10, 15, 25]
第4次外循环[1, 3, 6, 8, 10, 15, 25]
第0次内循环[1, 3, 6, 8, 10, 15, 25]
第5次外循环[1, 3, 6, 8, 10, 15, 25]
最后的结果[1, 3, 6, 8, 10, 15, 25]

```

我们可以看到，第0次外循环，已经将25放在了最右边，第1次外循环确定把15放到最右边，这样从右往左，从大到小，这就是完整的冒泡排序。







# 40、练习、Python的八皇后

@Author：By Runsen

## 什么是八皇后

**八皇后问题**是一个以国际象棋为背景的问题：如何能够在8×8的国际象棋棋盘上放置八个皇后，使得任何一个皇后都无法直接吃掉其他的皇后。

来自百度百科，皇后的走法是可以横竖斜着走任意格。






![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS80NzBjMGE4NC04NTM4LTQyMzAtYjg2Ny03ZTg2NTk4Y2Q2NzIucG5n?x-oss-process=image/format,png)

国际象棋棋盘是8 * 8的方格，每个方格里放一个棋子。皇后这种棋子可以攻击同一行或者同一列或者斜线（左上左下右上右下四个方向）上的棋子。在一个棋盘上如果要放八个皇后，使得她们互相之间不能攻击（即任意两两之间都不同行不同列不同斜线），求出一种所有布局方式。

好了我们来解决这个八皇后的问题，最常用的就是回溯法

## 回溯法

回溯法（探索与回溯法）是一种选优搜索法，又称为试探法，按选优条件向前搜索，以达到目标。但当探索到某一步时，发现原先选择并不优或达不到目标，就退回一步重新选择，这种走不通就退回再走的技术为回溯法，而满足回溯条件]的某个[状态的点称为“回溯点”。（来自百度百科）

说到底，就是一个一个的试错，在第一行第一个列放皇后，然后在第二行放皇后，一直将整个棋盘放满。如果发现放不了，就回到上一行放皇后的地方，选择其他位置放皇后。


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9kNmVhODUzOC0wYjQ2LTRiMzMtYmJmOS02YWRlZjkwZjUyNmQucG5n?x-oss-process=image/format,png)



回溯法就是不断的试错，有错了就回到上一行放皇后，直到整个棋盘放满。

## 代码

下图是八皇后问题的一个解：


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS8xNGQ2ZGM2Yi01ZTk2LTQxNjMtYjAzMS1mMTAwM2NhNmRkODIucG5n?x-oss-process=image/format,png)

首先定义一个冲突函数，如下，ps是positions 的缩写，表示之前摆放的皇后位置，是一个list，每个元素代表第几列放的，比如上图所有的皇后可以表示为

```
[0,4,7,5,2,6,1,3]
```




![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9mMDY3OWI2NC1iNmEyLTQ0ODItODc0NC03YzdiZWI3NzU2MzUucG5n?x-oss-process=image/format,png)







state 这里理解元组，就是之前放回皇后的位置，nextX表示新皇后要放的横坐标，conflict函数就是检测新皇后放的位置和之前的皇后在位置上是否有冲突，有的话返回True。

```python
def conflict(state, nextX):
    nextY = len(state)
    # 新皇后要放的纵坐标
    # print(state) #不知道可以下面打印下
    for i in range(nextY):
    	#在同一行或者在对角线上 nextY-i=1 就是对角线
        if abs(state[i]-nextX) in (0, nextY-i): 
            return True
    return False
```

再定义一个queens函数， 这里我们用Python的生成器来存储我们的结果

```python
def queens(num,state=()):
    for pos in range(num):
    	# 没有冲突
        if not conflict(state,pos):
        	# 最后一个pos，就是放到了最后一行，就yield储存在queens队列中
            if len(state) ==num-1:  
                yield(pos,)
            # 还没有到最后一行，就放皇后   
            else:
            	# 遍历之前的queens队列中储存的结果，(pos,) 就是当前放皇后，我们不知道是否最后一行，所以不断地递归，直到放到了最后一行
                for result in queens(num, state + (pos,)): 
                    yield (pos, ) + result

print(len(list(queens(8))))
# 92

一共有92中方法
```



![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS80MDg3YTU5OC05MTI3LTQyNmQtOGVmMS02Y2RhNjg1OTBkYjAucG5n?x-oss-process=image/format,png)





`list(queens(8))`就是我们的结果，下面我们定义一个`preetyprint`打印美观先



```python
import random

def preetyprint(solution):      # pilish 输出
    def line(pos, length=len(solution)):
        return'| '*(pos)+'|X'+'| '*(length-pos)
    for pos in solution:
        print (line(pos))
        
preetyprint(random.choice(list(queens(8))))

| | | | | | |X| | 
| | | |X| | | | | 
| |X| | | | | | | 
| | | | | | | |X| 
| | | | | |X| | | 
|X| | | | | | | | 
| | |X| | | | | | 
| | | | |X| | | |
```

## 完整代码

```python
import random

def conflict(state, nextX):
    nextY = len(state)
    # 新皇后要放的纵坐标
    # print(state) #不知道可以下面打印下
    for i in range(nextY):
    #在同一行或者在对角线上 nextY-i=1 就是对角线
        if abs(state[i]-nextX) in (0, nextY-i): 
            return True
    return False

def queens(num,state=()):
    for pos in range(num):
    # 没有冲突
        if not conflict(state,pos):
        # 最后一个pos，就是放到了最后一行，就yield储存在queens队列中
            if len(state) ==num-1:  
                yield(pos,)
            # 还没有到最后一行，就放皇后   
            else:
            # 遍历之前的queens队列中储存的结果，(pos,) 就是当前放皇后，我们不知道是否最后一行，所以不断地递归，直到放到了最后一行
                for result in queens(num, state + (pos,)): 
                    yield (pos, ) + result

 
def preetyprint(solution):      
    def line(pos, length=len(solution)):
        return'| '*(pos)+'|X'+'| '*(length-pos)
    for pos in solution:
        print (line(pos))
        
print(len(list(queens(8))))
       
preetyprint(random.choice(list(queens(8))))



for i in list(queens(8)):
    print(i) 
```



# 41、Python统计模块statistics

﻿@Author：Runsen






官网：  https://docs.python.org/3/library/statistics.html

## Python统计模块statistics

statistics 模块实现了许多常用的统计公式，以便使用 Python 的各种数值类型（int，float，Decimal 和 Fraction）进行高效的计算。






```python
# 计算平均数
import statistics


data = [1,2,3,4,5.6]

print(statistics.mean(data))# 3.12
# 等同于

print(sum(data)/len(data))
```

    3.12
    3.12



```python
# mode 众数
data = [1,2,3,4,5,1]
statistics.mode(data)
```




    1

## median－中位数

- median-low()－中位数(如果项数是偶数，返回小值)
- median-high()－中位数(如果项数是偶数，返回大值)
- median-grouped() - j将数字排序好再选择中位数



```python
print(statistics.median([1, 3, 5, 7]))
print(statistics.median_low([1, 3, 5, 7]))
print(statistics.median_high([1, 3, 5, 7]))
print(statistics.median_grouped([5, 3, 7]))
```

    4.0
    3
    5
    5.0

## 方差

**计算样本方差（sample variance）和样本标准差（sample standard deviation，the square root of the sample variance，也叫均方差）。** 


```python
# variance()－方差
data = [1, 2,  3, 3, 4]
statistics.variance(data)  # 1.3
# stdev－标准差
statistics.stdev(data) # 1.140175425099138
```









```python
# pvariance()－总体方差
statistics.pvariance([1.5, 2.5, 2.5, 2.75, 3.25, 4.75])
```




    0.9739583333333334





```python
### pstdev() -- 返回总体标准差（)。
### pvariance() --返回总体方差（)。

statistics.pstdev(data) # 1.019803902718557
statistics.pvariance(data)# 1.04

```

https://docs.python.org/3/library/statistics.html





# 42、MOOC课程 _ Python中的Scipy模块



这是MOOC课上的Scipy基础

## SciPy的介绍 

在Numpy库的基础上增加了众多的数学、科学以及工程计算中常用 的库函数 


- 线性代数 
- 常微分方程数值求解 
- 信号处理 
- 图像处理 
- 稀疏矩阵 

## SciPy的常数

SciPy的constants模块包含了众多的物理常数：


```python
from scipy import constants
print(constants.c) # 真空中的光速
299792458.0
print(constants.h) # 普朗克常数
6.62607004e-34
```


在字典physical_constants中，以物理常量名为键，对应的值是一个含有三 个元素的元组，查看电子质量的例子：

```python
print(constants.physical_constants['electron mass'])

(9.10938356e-31, 'kg', 1.1e-38)
常数值 单位 误差
```



![](https://img-blog.csdnimg.cn/20190507230820928.png)

```python
# 1英里等于多少米, 1英寸等于多少米, 1克等于多少千克, 1磅等于多少千克
print(C.mile, C.inch,C.gram,C.pound)

1609.3439999999998 0.0254 0.001 0.45359236999999997
```

## optimize模块

optimize模块提供了许多数值优化算法，可以实现

- 非线性方程组求解
- 数据拟合
- 函数最小值
  ![](https://img-blog.csdnimg.cn/20190507230952638.png)

![](https://img-blog.csdnimg.cn/20190507231011629.png)

```python
import numpy as np
from scipy.optimize import leastsq
X = np.array([8.19, 2.72, 6.39, 8.71, 4.7, 2.66, 3.78])
Y = np.array([7.01, 2.78, 6.47, 6.71, 4.1, 4.23, 4.05])
#计算以p为参数的直线和原始数据之间的误差
def f(p):
    k, b = p
    return(Y-(k*X+b))
#leastsq使得f的输出数组的平方和最小，参数初始值为[1,0]
r = leastsq(f, [1,0])
k, b = r[0]
print("k=",k,"b=",b)

k= 0.6134953491930442 b= 1.794092543259387
```

![](https://img-blog.csdnimg.cn/20190507231137418.png)

![](https://img-blog.csdnimg.cn/20190507231154670.png)


```python
from scipy.optimize import fsolve
from math import sin
#f计算方程组的误差,x是一组可能的解
def f(x):
    #转换为标准的浮点数列表
    x0, x1, x2 = x.tolist()
    return[5*x1+3,
           4*x0*x0 - 2*sin(x1*x2),
           x1*x2-1.5]
#[1,1,1]是未知数的初始值
result = fsolve(f, [1,1,1])
#输出方程组的解
print(result)
#输出误差
print(f(result))

[-0.70622057 -0.6        -2.5       ]
[0.0, -9.126033262418787e-14, 5.329070518200751e-15]
```

## 插值-interpolate

# 


- 插值：通过已知的离散数据来求解未知数据的方法，要求
  曲线通过所有的已知数据。
- 拟合：要求曲线函数与已知数据集的误差最小，不要求曲
  线通过所有的已知数据。


 **intepolate模块提供了许多对数据进行插值运算的函数：**

- B样条曲线插值
- 外推
- Spline拟合（UnivariateSpline插值运算）
- 二维插值运算等



![](https://img-blog.csdnimg.cn/20190507231542972.png)
![](https://img-blog.csdnimg.cn/20190507231551681.png)

```python
# 创建数据点集：
import numpy as np
x = np.linspace(0, 10, 11)
y = np.sin(x)
import pylab as pl
pl.plot(x,y,'ro')
pl.show()
```

![](https://img-blog.csdnimg.cn/20190507231833418.png)
**B样条曲线插值-举例**
![](https://img-blog.csdnimg.cn/20190507232206654.png)
![](https://img-blog.csdnimg.cn/20190507232229935.png)

```python
import numpy as np
from scipy import interpolate
import pylab as pl
#创建数据点集并绘制
x = np.linspace(0, 10, 11)
y = np.sin(x)
pl.plot(x,y,'ro')
#建立插值数据点
xnew = np.linspace(0, 10, 101)
for kind in ['nearest', 'zero','linear','quadratic']:
    #根据kind创建插值对象interp1d
    f = interpolate.interp1d(x, y, kind = kind)
    ynew = f(xnew)#计算插值结果
    pl.plot(xnew, ynew, label = str(kind))
pl.legend(loc = 'lower right')
pl.show()
```

![](https://img-blog.csdnimg.cn/20190507232107790.pn)


![](https://img-blog.csdnimg.cn/2019050723464798.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234650759.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234654748.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723465825.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234701218.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234704658.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234708104.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234711667.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723471532.Jpeg)

![](https://img-blog.csdnimg.cn/20190507234727542.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234738729.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234742401.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234745727.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234808467.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234812407.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234820974.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234827194.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723483554.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234838989.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234842351.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234853398.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234917869.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234922406.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234934928.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235034101.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234946502.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235113899.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235140760.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723514621.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235226486.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235212116.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235235835.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235239996.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235334260.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235342238.Jpeg)

![](https://img-blog.csdnimg.cn/20190507235349850.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235354452.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235358306.Jpeg)

# 43、去年pandas的笔记

@Author：Runsen





# 

pandas 是基于NumPy 的一种工具，该工具是为了解决数据分析任务而创建的。Pandas 纳入了大量库和一些标准的数据模型，提供了高效地操作大型数据集所需的工具。pandas提供了大量能使我们快速便捷地处理数据的函数和方法。你很快就会发现，它是使Python成为强大而高效的数据分析环境的重要因素之一。

## 1、pandas数据结构的介绍

* Series：一维数组，与Numpy中的一维array类似。二者与Python基本的数据结构List也很相近。Series如今能保存不同种数据类型，字符串、boolean值、数字等都能保存在Series中。
* Time- Series：以时间为索引的Series。
* DataFrame：二维的表格型数据结构。很多功能与R中的data.frame类似。可以将DataFrame理解为Series的容器。
* Panel ：三维的数组，可以理解为DataFrame的容器。

## 2、Series的操作

### 2.1 对象创建

```python
import pandas as pd
import numpy as np
# 直接创建
s = pd.Series(np.random.randn(5), index=['a','b','c','d','e'])
print(s) 
# 字典（dict）类型数据创建
s = pd.Series( {'a':10, 'b':20, 'c':30}, index=['b', 'c', 'a', 'd'])

OUT:
a   -0.620323
b   -0.189133
c    1.677690
d   -1.480348
e   -0.539061
dtype: float64

OUT:
a    10
b    20
c    30
dtype: int64
```

### 2.2 查看数据




切片、索引、dict操作

 Series既然是一维数组类型的数据结构，那么它支持想数组那样去操作它。通过数组下标索引、切片都可以去操作他，且它的data可以是dict类型的，那么它肯定也就支持字典的索引方式。

```python
import pandas as pd
import numpy as np

s = pd.Series(np.random.randn(5), index=['a','b','c','d','e'])

print(s)

# 下标索引
print('下标索引方式s[0] = : %s' % s[0])

# 字典访问方式
print('字典访问方式s[b] = ：%s' % s['b'])

# 切片操作
print('切片操作s[2:]\n:%s' % s[2:])
print('a' in s)
print('k' in s)
OUT:
a   -0.799676
b   -1.581704
c   -1.240885
d    0.623757
e   -0.234417
dtype: float64

下标索引方式s[0] = : -0.799676067487
字典访问方式s[b] = ：-1.58170351838
切片操作s[2:]:
c   -1.240885
d    0.623757
e   -0.234417
True
False
```

### 2.3 Series的算术操作

```python
import pandas as pd
import numpy as np

s1 = pd.Series(np.random.randn(3), index=['a','b','c'])

s2 = pd.Series(np.random.randn(3), index=['a','b','c'])
print(s1+s2)
print(s1-s2)
print(s1*s2)
print(s1/s2)
OUT:
a    0.236514
b   -0.132153
c    0.203186
dtype: float64

a    0.305397
b   -1.474441
c   -1.697982
dtype: float64

a   -0.009332
b   -0.539128
c   -0.710465
dtype: float64

a   -7.867120
b   -1.196907
c   -0.786252
dtype: float64
```

## 3、dataframe的操作

### 3.1 对象创建



```python
In [70]:  data = {'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada'],'year': [2000, 2001, 20
    ...: 02, 2001, 2002],'pop': [1.5, 1.7, 3.6, 2.4, 2.9]}
In [71]: data
Out[71]: 
{'pop': [1.5, 1.7, 3.6, 2.4, 2.9],
 'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada'],
 'year': [2000, 2001, 2002, 2001, 2002]}
# 建立DataFrame对象
In [72]: frame1 = DataFrame(data)
# 红色部分为自动生成的索引
In [73]: frame1
Out[73]: 
   pop   state  year
0  1.5    Ohio  2000
1  1.7    Ohio  2001
2  3.6    Ohio  2002
3  2.4  Nevada  2001
4  2.9  Nevada  2002

>>> lista = [1,2,5,7]
>>> listb = ['a','b','c','d']
>>> df = pd.DataFrame({'col1':lista,'col2':listb})
>>> df
   col1 col2
0     1    a
1     2    b
2     5    c
3     7    d
```

### 3.2 选择数据





```python
In [1]: import numpy as np
   ...: import pandas as
   ...: df = pd.DataFrame

In [2]: df
Out[2]:
    a   b   c
0   0   2   4
1   6   8  10
2  12  14  16
3  18  20  22
4  24  26  28
5  30  32  34
6  36  38  40
7  42  44  46
8  48  50  52
9  54  56  58

In [3]: df.loc[0,'c']
Out[3]: 4

In [4]: df.loc[1:4,['a','c']]
Out[4]:
    a   c
1   6  10
2  12  16
3  18  22
4  24  28
In [5]: df.iloc[0,2]
Out[5]: 4

In [6]: df.iloc[1:4,[0,2]]
Out[6]:
    a   c
1   6  10
2  12  16
3  18  22
```

### 3.3 函数应用

```python
frame = pd.DataFrame(np.random.randn(4, 3), columns=list('bde'),
                     index=['Utah', 'Ohio', 'Texas', 'Oregon'])
frame
np.abs(frame)

OUT：
            b	     d            e
Utah	0.204708	0.478943	0.519439
Ohio	0.555730	1.965781	1.393406
Texas	0.092908	0.281746	0.769023
Oregon	1.246435	1.007189	1.296221


f = lambda x: x.max() - x.min()
frame.apply(f)
OUT：
b    1.802165
d    1.684034
e    2.689627
dtype: float64

def f(x):
    return pd.Series([x.min(), x.max()], index=['min', 'max'])
frame.apply(f)

            b	d	      e
Utah	-0.20	0.48	-0.52
Ohio	-0.56	1.97	1.39
Texas	0.09	0.28	0.77
Oregon	1.25	1.01	-1.30
```

### 3.4 统计概述和计算

```python
df = pd.DataFrame([[1.4, np.nan], [7.1, -4.5],
                   [np.nan, np.nan], [0.75, -1.3]],
                  index=['a', 'b', 'c', 'd'],
                  columns=['one', 'two'])
df
OUT:
    one     two
a	1.40	NaN
b	7.10	-4.5
c	NaN     NaN
d	0.75	-1.3


df.info()
df.describe()


<class 'pandas.core.frame.DataFrame'>
Index: 4 entries, a to d
Data columns (total 2 columns):
one    3 non-null float64
two    2 non-null float64
dtypes: float64(2)
memory usage: 256.0+ bytes

OUT：
          one          two
count	3.000000	2.000000
mean	3.083333	-2.900000
std	3.493685	2.262742
min	0.750000	-4.500000
25%	1.075000	-3.700000
50%	1.400000	-2.900000
75%	4.250000	-2.100000
max	7.100000	-1.300000
```

### 3.5 数据读取

```python
data = pd.read_csv('./dataset/HR.csv')
data.info()

out：
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 14999 entries, 0 to 14998
Data columns (total 10 columns):
satisfaction_level       14999 non-null float64
last_evaluation          14999 non-null float64
number_project           14999 non-null int64
average_montly_hours     14999 non-null int64
time_spend_company       14999 non-null int64
Work_accident            14999 non-null int64
left                     14999 non-null int64
promotion_last_5years    14999 non-null int64
sales                    14999 non-null object
salary                   14999 non-null object
dtypes: float64(2), int64(6), object(2)
memory usage: 1.1+ MB

data = pd.read_csv('./dataset/movielens/movies.dat', header=None, names=['name', 'types'], sep='::', engine='python')
data.head()
OUT：
                name	types
1	Toy Story (1995)	Animation|Children's|Comedy
2	Jumanji (1995)	Adventure|Children's|Fantasy
3	Grumpier Old Men (1995)	Comedy|Romance
4	Waiting to Exhale (1995)	Comedy|Drama
5	Father of the Bride Part II (1995)	Comedy


data = pd.read_excel('./dataset/my_excel.xlsx', sheet_name=1)
data.head()
ouput:
        date	H1	H2	H3
0	2014-06-01	1	2	3
1	2014-06-02	2	3	4
2	2014-06-03	3	4	5
3	2014-06-04	4	5	6
```

## 4、Time- Series的操作















```python
ts = pd.DataFrame(np.random.randn(1000,4),index=pd.date_range('20180101',periods=1000),columns=list('abcd'))
ts = ts.cumsum()
ts.plot(figsize = (12,8))
plt.show()
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190313200310360.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)



# 44、Python中的statsmodels模块

﻿

@Author：Runsen

## statsmodels入门

这个非常简单的案例研究旨在让您快速上手 statsmodels。从原始数据开始，我们将展示估计统计模型和绘制诊断图所需的步骤。我们只使用由statsmodels它或它pandas和patsy 依赖项提供的函数。

来源：http://www.statsmodels.org/stable/gettingstarted.html



```python
import statsmodels.api as sm
import pandas
from patsy import dmatrices # patsy用于描述统计模型和使用类似公式构建设计矩阵R
#下载了Guerry数据集，这是一组历史数据，用于支持Andre-Michel Guerry在1833年 关于法国道德统计的论文。

df = sm.datasets.get_rdataset("Guerry", "HistData").data
```


```python
df.head()
```



![](https://img-blog.csdnimg.cn/20200717085206962.png)




```python
df.columns
```




    Index(['dept', 'Region', 'Department', 'Crime_pers', 'Crime_prop', 'Literacy',
           'Donations', 'Infants', 'Suicides', 'MainCity', 'Wealth', 'Commerce',
           'Clergy', 'Crime_parents', 'Infanticide', 'Donation_clergy', 'Lottery',
           'Desertion', 'Instruction', 'Prostitutes', 'Distance', 'Area',
           'Pop1831'],
          dtype='object')




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 86 entries, 0 to 85
    Data columns (total 23 columns):
    dept               86 non-null int64
    Region             85 non-null object
    Department         86 non-null object
    Crime_pers         86 non-null int64
    Crime_prop         86 non-null int64
    Literacy           86 non-null int64
    Donations          86 non-null int64
    Infants            86 non-null int64
    Suicides           86 non-null int64
    MainCity           86 non-null object
    Wealth             86 non-null int64
    Commerce           86 non-null int64
    Clergy             86 non-null int64
    Crime_parents      86 non-null int64
    Infanticide        86 non-null int64
    Donation_clergy    86 non-null int64
    Lottery            86 non-null int64
    Desertion          86 non-null int64
    Instruction        86 non-null int64
    Prostitutes        86 non-null int64
    Distance           86 non-null float64
    Area               86 non-null int64
    Pop1831            86 non-null float64
    dtypes: float64(2), int64(18), object(3)
    memory usage: 15.5+ KB



```python
# 在地区Region  85 non-null object有缺失值
df = df.dropna()
```

法国86个省的识字率是否与19世纪20年代皇家彩票的人均赌注有关。

我们需要控制每个部门的财富水平，在回归方程的右侧包含一系列虚拟变量，以控制由于区域效应而导致的未观察到的异质性。


**使用普通最小二乘回归（OLS）估计模型。**






```python
# 使用patsy的dmatrices函数来创建设计矩阵
#  y 是一个 N×1关于人均彩票投注数据的一栏（彩票）。X 是 N×7带有截距， 识字和财富变量，以及4个区域二进制变量
y, X = dmatrices('Lottery ~ Literacy + Wealth + Region', data=df, return_type='dataframe')

```


```python
y[:3]

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }


    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }


</style>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Lottery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>41.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>38.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>66.0</td>
    </tr>
  </tbody>
</table>

</div>




```python
X[:3]

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }


    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }


</style>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Intercept</th>
      <th>Region[T.E]</th>
      <th>Region[T.N]</th>
      <th>Region[T.S]</th>
      <th>Region[T.W]</th>
      <th>Literacy</th>
      <th>Wealth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>37.0</td>
      <td>73.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>51.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>13.0</td>
      <td>61.0</td>
    </tr>
  </tbody>
</table>

</div>




```python
# 模型拟合和总结
mod = sm.OLS(y, X)    # Describe model

res = mod.fit()       # Fit model

print(res.summary())   # Summarize model

```

                                OLS Regression Results                            
    ==============================================================================
    Dep. Variable:                Lottery   R-squared:                       0.338
    Model:                            OLS   Adj. R-squared:                  0.287
    Method:                 Least Squares   F-statistic:                     6.636
    Date:                Thu, 09 May 2019   Prob (F-statistic):           1.07e-05
    Time:                        18:02:22   Log-Likelihood:                -375.30
    No. Observations:                  85   AIC:                             764.6
    Df Residuals:                      78   BIC:                             781.7
    Df Model:                           6                                         
    Covariance Type:            nonrobust                                         
    ===============================================================================
                      coef    std err          t      P>|t|      [0.025      0.975]
    -------------------------------------------------------------------------------
    Intercept      38.6517      9.456      4.087      0.000      19.826      57.478
    Region[T.E]   -15.4278      9.727     -1.586      0.117     -34.793       3.938
    Region[T.N]   -10.0170      9.260     -1.082      0.283     -28.453       8.419
    Region[T.S]    -4.5483      7.279     -0.625      0.534     -19.039       9.943
    Region[T.W]   -10.0913      7.196     -1.402      0.165     -24.418       4.235
    Literacy       -0.1858      0.210     -0.886      0.378      -0.603       0.232
    Wealth          0.4515      0.103      4.390      0.000       0.247       0.656
    ==============================================================================
    Omnibus:                        3.049   Durbin-Watson:                   1.785
    Prob(Omnibus):                  0.218   Jarque-Bera (JB):                2.694
    Skew:                          -0.340   Prob(JB):                        0.260
    Kurtosis:                       2.454   Cond. No.                         371.
    ==============================================================================
    
    Warnings:
    [1] Standard Errors assume that the covariance matrix of the errors is correctly specified.




```python
res.params

```




    Intercept      38.651655
    Region[T.E]   -15.427785
    Region[T.N]   -10.016961
    Region[T.S]    -4.548257
    Region[T.W]   -10.091276
    Literacy       -0.185819
    Wealth          0.451475
    dtype: float64





```python
# 应用Rainbow测试线性度
print(sm.stats.linear_rainbow(res))#第一个数字是F统计量，第二个数字是p值。
sm.graphics.plot_partregress('Lottery', 'Wealth', ['Region', 'Literacy'],
                          data=df, obs_labels=False)

```

    (0.847233997615691, 0.6997965543621644)








![](https://img-blog.csdnimg.cn/20190509180722494.png)

对于statsmodels确实是一个值得学习的机器学习库

参考：http://www.statsmodels.org/stable/gettingstarted.html

# 45、和我一起看看，国外的Python考试到底是怎么样（上篇）

﻿@Author ： By Runsen
@Written Date：2020/05/20

## 前言

我是在4月底帮别人考试的，然后别人发过来去年的考试题的。我看了下，全是英文，原来是留学生啊。


走，我带你们看看国外的Python考试题到底是什么辣鸡东西？



![](https://img-blog.csdnimg.cn/20200520093613896.png)

看了下，好像我英语不行，但也知道满分是70，什么辣鸡玩意，一脸懵逼

## 第一题


![](https://img-blog.csdnimg.cn/20200520093834495.png)




就是要我定义samPlaces函数方法，主要这个是需要O（n)的时间复杂度，对于我这老油条来说，就是一个切菜的东西，直接用字典，Leetcode第一题的两数相加就是这个玩意。难度0，切菜级别




```css
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/4/23
'''
'''
输出两个列表的相同的索引
'''
def samPlaces(s1,s2):
    if len(s1) != len(s2):
        return []
    my_dict = {}
    my_index = []
    for index,item in enumerate(s1):
        my_dict[item] = index
    for i in s2:
        if i in my_dict.keys():
            my_index.append(my_dict[i])
    return my_index
if __name__ == '__main__':
    print(samPlaces([1,7,9],[1,3,9]))
```

## 第二题

![](https://img-blog.csdnimg.cn/20200520100505451.png)


![](https://img-blog.csdnimg.cn/20200520100522829.png)

![](https://img-blog.csdnimg.cn/2020052010092650.png)

![](https://img-blog.csdnimg.cn/20200520101007795.png)
二题看的我就是一个煞笔，一个InputOuput.py 就是读取文件的，第二Quicsort.py就是快速排序的。第三个是一个字符串开头和结尾字符要相同。4+3+5+4+4=20分


第一个问我Manipulation.py输出什么，这不是当我傻逼，如果单词前后字母都相同，直接del，沙比。


答案是

```css
['cat', 'elephant']
[]
```

第二题，我去，这么简单，太简单了，送分的


```css
begin
this
is
a
test
end
```

第三题，用一个函数main（）编写一个程序，就是读取，再排序，再去除单词前后字母都相同，然后将结果字符串写入名为cookedData.txt文件


```css
def readFromFile(filename):
    lst = []
    fp = open(filename,"r")
    item = fp.readline().strip()
    while item != '':
        lst.append(item)
        item = fp.readline().strip()
    fp.close()

    return lst

def writeTofile(contents,filename):
    fp = open(filename,"w")
    fp.write("begin\n")
    for item in contents:
        fp.write(item + " ")
    fp.write("\nend")
    fp.close()

def sort(lis):
    if len(lis) < 2:
        return lis
    less, equal ,greater = [],[],[]
    pval = lis[0]
    for i in lis:
        if i < pval :
            less.append(i)
        elif i > pval:
            greater.append(i)
        else:
            equal.append(i)
    return sort(less) + equal + sort(greater)

def modifylist(values):
    i=0
    while i <  len(values):
        if values[i][0] == values[i][-1] or (" " in values[i]):
           del values [i]
        else:
            i +=1
            
if __name__ == '__main__':
    # ['for loop', 'link list', 'return', 'CISC', 'binary rearch tree', 'variable']
    data = readFromFile("rawData.txt")
    # ['CISC', 'binary rearch tree', 'for loop', 'link list', 'return', 'variable']
    sort_data = sort(data)
    modifylist(sort_data)
    print(sort_data)  # ['return', 'variable']
    writeTofile(sort_data,"cookedData.txt")


```

第四题，都是切菜切菜

```css
# cookedData.txt
begin
return variable 
end
```




第五题，将在快速排序中按降序（从最大值到最小值）排序，辣鸡，简单，大于变小于，小于变大于。

```css
def sort(lis):
    if len(lis) < 2:
        return lis
    less, equal ,greater = [],[],[]
    pval = lis[0]
    for i in lis:
        if i > pval :
            less.append(i)
        elif i < pval:
            greater.append(i)
        else:
            equal.append(i)
    return sort(less) + equal + sort(greater)
if __name__ == '__main__':
    print(sort([17,-28,11,9,15,-2]))
    # [17, 15, 11, 9, -2, -28]
```

## 第三题



填空题选择题， 我看看。好像挺难的。
![](https://img-blog.csdnimg.cn/20200520110048350.png)

![](https://img-blog.csdnimg.cn/20200520110103721.png)

第一题，如果在未排序的列表上使用二分搜索，下面对的是哪个？


A，程序崩了？你才崩了
B、永远找不到要查找的值。这么绝对，比如[2,1,3,5,4]，我要找3，不就打脸了吗？
C、有时搜索能成功，不用说了，就是你
D、时间复杂度发生改变，程度不变，你时间复杂度变个毛

我觉得就是C，送分，切菜


第二题、使用二分搜索来按升序搜索数字列表，但有些数字出现了不止一次。以下哪个是正确的？


A、搜索始终找到第一个发生
B、搜索始终找到最后一个发生
C、搜索有时找到第一个，有时找到最后一个
D、时间复杂度发生改变

如果是[1,1,2,3,5,6,] 找1，是[1,2,3,4,5,5,] 找4，所以搜索找到的位置不能明确，二分查找在最坏情况下是在排除到只剩下最后一个值之后得到结果，二分查找的时间复杂度O(log2n)，如果出现相同的数字，时间复杂度应该发生改变，答案我觉得是D


第三题、冒泡排序，对以下列表进行排序数值：[17，5,12,13,16,3]，显示冒泡排的第一次迭代后的列表


[练习、Python实现冒泡排序（三十九）](https://maoli.blog.csdn.net/article/details/105119302)

我这篇搞定了，辣鸡东西，一个外循环，切菜送分

```css
[5,12,13,16,3,17]
```

第四题，选择排序，插入排序，冒泡排序选一个，


![](https://img-blog.csdnimg.cn/20200520111951448.png)



摆明选择，这他妈的简单一笔

第五题


在合并排序中，将列表重复拆分，然后将排序列表重新合并在一起。显示这两者的合并结果列表：[4，7,9,12]，[1,4,6,8,15]   合并成 [1, 4.，6，7，8，9，12，15,。需要代码实现，

这有点难度，但是也是很基础的排序。就是切菜，辣鸡




```css
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/4/25
'''
def merge(a, b):
    '''
    合并排序：两个已经排序好的
    '''
    c = []
    h = j = 0
    # 谁小加谁
    while j < len(a) and h < len(b):
        if a[j] < b[h]:
            c.append(a[j])
            j += 1
        # 相同也没事
        else:
            c.append(b[h])
            h += 1
    # 有的时候 j 直接达到了len(a)，那么直接append b剩下的
    if j == len(a):
        for i in b[h:]:
            c.append(i)
    if h == len(b):
        for i in a[j:]:
            c.append(i)
    return c

if __name__ == '__main__':
    print(merge([4,7,9,12],[1,4,6,8,15]))
    # [1, 4, 4, 6, 7, 8, 9, 12, 15]
```

## 第四题

![](https://img-blog.csdnimg.cn/20200520112531575.png)

![](https://img-blog.csdnimg.cn/20200520113620386.png)
我还以为什么东西，练习时间复杂度，切菜


第一题

![](https://img-blog.csdnimg.cn/20200520113655623.png)



时间复杂度$O(N^2)$



第二题



![](https://img-blog.csdnimg.cn/20200520114051865.png)

取整除等于用`//=`来进行表示。一样的道理


一个堆排序的样子，时间复杂度$O(N*log_2N)$

第三题
![](https://img-blog.csdnimg.cn/20200520114608591.png)

时间复杂度$O(N)$

第四题




![](https://img-blog.csdnimg.cn/20200520114748294.png)

时间复杂度$O(N^2)$



我没有答案的，就是自己瞎逼逼的，先到这，有点长了

# 46、和我一起看看，国外的Python考试到底是怎么样（下篇）



@Author: Runsen
@Date：2020/5/21

## 第五题


看题，看Runsen怎么解决国外Python考试。
![](https://img-blog.csdnimg.cn/202005212231099.png)


第一题，就是代入法，送分


len一开始是5，然后m等于2，取整除，这样就是 c+ab+de

然后再将ab，de运行一次


ab：2整除是1，得到b，a ，


de：2整除是1，得到e，d ，

答案就是cbaed


我不信，就写代码测试一下

```css
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/21
'''
def fn(a):
    if len(a) <2:
        return  a
    m = len(a) //2
    print(a[m],a[:m],a[m+1:])
    return a[m] + fn(a[:m]) + fn(a[m+1:])

if __name__ == '__main__':
    print(fn('abcde'))

c ab de
b a 
e d 
cbaed
```

和想得一样，简单

![](https://img-blog.csdnimg.cn/20200521223123412.png)

继续代入，其中lo =0，hi=4，m=2.，num[2] = 15，这样就是[1, 2, 15, 4, 5]




fn([1,2,15,4,5],0,1)  ，继续代入m=0，s=3，num[0] =3，就是[3, 2, 15, 4, 5]



```css
# 错误的想法
这是这是把本身的fn运行，在fn还有两个fn。继续代入，fn([3,2,15,4,5],0,0)，其中m=2.，num[0] = 3，无变化。fn([3,2,15,4,5],1,5)，其中m=3，num[0] = 3



这样就是[1, 2, 15, 4, 5]


```





**我终于知道了，这里考的是函数的嵌套**


这题，我真的不会，一个函数再调用两次，直接打印看看，结果是[3, 2, 15, 9, 5]，此题不会，



```css
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/21
'''

def fn(nums,lo,hi):
    if hi < lo:
        return
    m = (lo +hi )//2
    s = 0
    for i in range(lo,hi+1):
        s += nums[i]
    nums[m] = s
    print(nums,lo,m)
    fn(nums,lo , m-1)
    print(nums)
    fn(nums,m+1 , hi)

if __name__ == '__main__':
    test = [1, 2, 3, 4, 5]
    fn(test, 0, len(test)-1)
    print(test)




[1, 2, 15, 4, 5] 0 2
[3

, 2, 15, 4, 5] 0 0
[3, 2, 15, 4, 5]
[3, 2, 15, 4, 5] 1 1
[3, 2, 15, 4, 5]
[3, 2, 15, 4, 5]
[3, 2, 15, 9, 5] 3 3
[3, 2, 15, 9, 5]
[3, 2, 15, 9, 5] 4 4
[3, 2, 15, 9, 5]
[3, 2, 15, 9, 5]

```



![](https://img-blog.csdnimg.cn/20200521223141986.png)








![](https://img-blog.csdnimg.cn/20200521223200423.png)

runsen一开始看这题就是蒙的，然后发现了规律$a[n+1]=a[n]+3^n$


这里还要求递归计算，不能超过四行代码，简单搞定



```css
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/22
'''

def tulip(n):
    if n == 0:
        return 1
    else:
        return tulip(n-1) + 3**n

def main():
    n = int(input('Enter a value for n:'))
    for i in range(n+1):
        print(tulip(i))
main()

Enter a value for n:5
1
4
13
40
121
364
```

## 第六题



第一题
![](https://img-blog.csdnimg.cn/20200522162910746.png)


第一题。问当代码在上面显示的链表上执行时，会打印什么？




小白先看这个
![](https://img-blog.csdnimg.cn/20200522163538501.png)

count=0，ptr  20
count=1，ptr  30

然后2跳出循环，答案到30，也是就10,20,30]，送分






![](https://img-blog.csdnimg.cn/20200522163746415.png)


第二题，这就是傻逼做的，答案[14,18,12,13]。解答没有







![](https://img-blog.csdnimg.cn/20200522164021974.png)


第三题，我的结果是[5,4,9,4]

![](https://img-blog.csdnimg.cn/20200522164348195.png)


考链表的时间复杂度，链表中的元素都会两个属性，一个是元素的值，另一个是指针，此指针标记了下一个元素的地址，每一个数据都会保存下一个数据的内存的地址，通过此地址可以找到下一个数据，任意位置插入元素和删除元素效率较高，时间复杂度为O(1)。随机访问效率低，时间复杂度为0(N)



![](https://img-blog.csdnimg.cn/20200522165427407.png)
我的答案



第一个尾节点加入节点的时间复杂度$O(1)$


第二个确定链表长度的时间复杂度$O(n)$


第三个将链表中的前10个值相加的时间复杂度为$O(1)$

第四个对于已排序的链接列表，搜索不在列表中的值的时间复杂性为$O(n)$

## 第七题




![](https://img-blog.csdnimg.cn/20200522165627577.png)

第一题显示列表值在下面的树中的位置，以形成二叉搜索树。假设节点是按照在原始列表中的出现顺序插入的，从44开始，然后是60，然后是62，依此类推。

取中间作根节点，下图就我的答案






![](https://img-blog.csdnimg.cn/20200522170413407.png)








![](https://img-blog.csdnimg.cn/20200522170727592.png)

第二题。指出树是否表示二叉搜索树（BST），如果树不是二叉搜索树，为什么


二叉搜索树：任意节点的键值一定大于其左子树中的每一个节点的键值，并小于其右子树中的每一个节点的键值。








第一个不是，这里错了

![](https://img-blog.csdnimg.cn/20200522171407902.png)


第二个是


第三个不是，因为不是二叉树


至此，这份70分的考卷结束了。我还要一份，继续。

# 47、第二份国外的Python考试（上篇）

@Author：Runsen
@Date：2020/5/26




之前撸了一份国外的Python考试题目，那个留学生还有一份，我接着继续撸。走，看看国外的Python考试题到底是什么东西？




![](https://img-blog.csdnimg.cn/20200524163744996.png)

满分55分，之前的是70，不知道什么回事，撸就对了。

## 第一题


![](https://img-blog.csdnimg.cn/20200526182922726.png)


第一题很明显就是一个时间复杂度的题目，一个快速排序，一个链表查找，一个冒泡排序，一个链表插入，一个二叉搜索，一个访问Python列表中的单个元素。







![](https://img-blog.csdnimg.cn/20200527094912912.png)

快速排序$Onlogn)$，链表查找$On)$，冒泡排序$On^2)$，链表插入$O(1)$，二叉搜索$O(Logn)$
访问Python列表中的单个元素$O(1)$。



Python列表做元素的遍历、删除、插入等操作，对应的时间复杂度为O(n)；访问某个索引的元素、尾部添加元素或删除元素这些操作比较适合做，对应的时间复杂度为O(1)。




![](https://img-blog.csdnimg.cn/20200527100100585.png)

答案我不知道，没有标准答案。





![](https://img-blog.csdnimg.cn/20200527100151854.png)

第二题是指出函数的时间复杂性


三个循环，但是结尾是一个n//4，应该是$O(nlogn)$，因为`for i in range(10)`这个是$O(1)$



![](https://img-blog.csdnimg.cn/20200527101032924.png)


二个循环，应该是$O(n^2)$

## 第二题


![](https://img-blog.csdnimg.cn/20200527101155993.png)

打印出什么，2*fizbin(6,10)，然后就是4*fizbin(3,5)，答案就是4。



![](https://img-blog.csdnimg.cn/20200527101439234.png)

一开始mid等于2，left = mysteryFun([1,0]) =  mysteryFun([1]) +mysteryFun([0]) = 1


right =  mysteryFun([2，3]) =  mysteryFun([2]) +mysteryFun([3]) = 4+9=13

答案14。


如果mysteryFun([0,1])，运行3次。









![](https://img-blog.csdnimg.cn/20200527102542313.png)


写一个函数应该返回一个由列表中所有字符串组成的字符串，这些字符串以一个空格分隔的给定字符开头，用字符决定排序的列表。


难度一般，


```css
def alliterationMaker(alist,char):
    # 对alist的开头不是char的去除
    for i in alist:
        if i[0] != char:
            alist.pop(alist.index(i))
    alist.sort()
    return alist

if __name__ == '__main__':
    print(alliterationMaker(["big","cow","bug","bit","table","black","bear"],"b"))
    
['bear', 'big', 'bit', 'black', 'bug']
```

## 第三题

![](https://img-blog.csdnimg.cn/20200527104040275.png)


就是把从大到小，6，5，4，2，2，然后再全部加一，7，6，5，3，3.再反转，3，3，5，6，7


![](https://img-blog.csdnimg.cn/2020052710452826.png)


答案8，7，6，25

## 第四题

![](https://img-blog.csdnimg.cn/20200527105249730.png)

二叉树的遍历是指从二叉树的根结点出发，按照某种次序依次访问二叉树中的所有结点，使得每个结点被访问一次，且仅被访问一次，分别有前序遍历，中序遍历，后序遍历


前序遍历通俗的说就是从二叉树的根结点出发，当第一次到达结点时就输出结点数据，按照先向左在向右的方向访问。

中序遍历就是从二叉树的根结点出发，当第二次到达结点时就输出结点数据，按照先向左在向右的方向访问。

后序遍历就是从二叉树的根结点出发，当第三次到达结点时就输出结点数据，按照先向左在向右的方向访问。

![](https://img-blog.csdnimg.cn/20190528215926380.png)

选项A就是后序遍历 正确
选项B就是前序遍历 但是错误
选项C就是前序遍历 正确
选项D什么遍历都不是，错误
选项E什么遍历都不是，错误
![](https://img-blog.csdnimg.cn/20200527110144387.png)

当输入是上面显示的树时，显示以下代码打印的内容。

这个真的不知道写什么，就是不断地分解子树，打印出来







# 48、第二份国外的Python考试（下篇）

﻿@Author：Runsen
@Date：2020/5/26

## 第五题


![](https://img-blog.csdnimg.cn/20200527111432148.png)

归并排序和快速排序在最佳情况下都具有$O（n logn）$时间复杂性。然而，其中一个算法的最坏情况复杂度为$O(n^2)$。说明哪些算法的时间复杂度为$O(n^2)$，并简要解释为什么


答案是快速排序
![](https://img-blog.csdnimg.cn/20200527111040603.png)


 快速排序具有最好的平均性能（average behavior），但最坏性能（worst case behavior）和插入排序

相同，也是$O(n^2)$。比如一个序列5,4,3,2,1，要排为1,2,3,4,5。按照快速排序方法，每次只会有一个数据进入正确顺序，不能把数据分成大小相当的两份，很明显，]时间复杂度就成了O(n^2)。






第二题

![](https://img-blog.csdnimg.cn/20200527111409799.png)


在对冒泡排序、选择排序和插入排序的外部循环进行三次迭代之后，下面使用哪种排序


第一个很明显选择排序，选择排序在未排序序列中找到最小（大）元素，存放到排序序列的起始位置。



第三个很明显冒泡排序，


那么第二个很明显插入排序




![](https://img-blog.csdnimg.cn/20200527112109255.png)

第三题，其实就是一个二分查找，只不过变成了查找对应的字符串，变汤不变药，问题就是当count等于2时候，那么对应的mid，higth，low。



第一，len(collection) = 10，一开始mid等于4，然后不对，直接low等于5，count等于1，接着mid等于7，不对，直接low等于8，count等于2，

因此答案是mid等于7，higth等于9，low等于8。

## 最后一题

![](https://img-blog.csdnimg.cn/20200527122433768.png)


（20分）你被委托写一个简单的游戏卡游戏称为考试扑克。这场比赛是用一套标准的扑克牌进行的。在您的游戏中，卡片将被表示为（等级，套装）元组的列表。注意数字11-13代表杰克、王后、国王，而我代表王牌。西装（黑桃钻石、红桃和梅花）用一个字母表示。我们将把这些卡片存储在一个叫做deck的全局抖动结构中。您可以假设在您的程序中定义了以下内容


SCDH就是扑克牌的四种类别，一共有52张扑克牌





玩家最初获得5张牌。然后，他们还有三个（可选）回合，目标是实现以下其中一个



其中通俗的来说，就是现在你有五张牌，打牌的时候，怎么可以出五张牌，顺子可以打出去，三带二可以打出去，还有就是锄大地的同一种花色可以打出去。最后，通过五张牌的总和作为得分。你可以换牌。







![](https://img-blog.csdnimg.cn/20200527122502815.png)

![](https://img-blog.csdnimg.cn/20200527123008596.png)







![](https://img-blog.csdnimg.cn/20200527123654834.png)


这个代码写了我快一个小时，真的很多细节注意

```css
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/21
'''
import random
# 定义一副未洗的牌[0, 1....51]
porks = [i for i in range(52)]
# 定义花色
# 方片D(Diamonds) 梅花C(Clubs)  红桃H(heart)  黑桃S(spade)
suits = ['D', 'C', 'H', 'S']
# 定义编号
ranks = ['1', '2', '3', '4', '5', '6', '7', '8',
         '9', '10', '11', '12', '13']
s = 0
def get_porks(mylist):
    # 随机生成一牌，但是要求不能在之前的出现
    pork = random.choice(ranks) +  random.choice(suits)
    if pork in mylist:
        # 出现重新生成一牌
        return get_porks(mylist)
    else:
        return pork

def get_five_porks():
    mylist = []
    for i in range(52):
        # 随机得到0-51整数随机数
        randomIndex = random.randint(0, 51)
        # 交换
        porks[i], porks[randomIndex] = porks[randomIndex], porks[i]
    for i in range(5):
        suit = suits[porks[i] // 13]
        rank = ranks[porks[i] % 13]
        mylist.append(str(rank + suit))
    return mylist

def change_porks(mylist):
    # 需不需要换牌

    global s
    print(mylist,s)
    Change = input("Change some cards：y or n： ")
    if Change == "y":
        keep = input("Indicate which cards you wish to keep ：")
        for index,i in enumerate(keep):
            if i == '0':
                # 换牌
                pork = get_porks(mylist)
                print(pork)
                mylist.insert(index, pork)
                # 在删除之后的下一个
                mylist.pop(index+1)
        print("You now have："+ str(mylist))
        change_porks(mylist)
    else:
        # 计算分数
        for i in mylist:
            print(i)
            s += int(i[:-1])
        print("Your total score is now：" +str(s))
        return s


def teststraightchecker():
    global s
    mylist = get_five_porks()
    print("Here is your first hand：" + str(mylist))
    change_porks(mylist)
    choice = input("Would you like to play again (y or n) ：")
    if choice == 'y':
        teststraightchecker()
    else:
        print("Thank you for playing")

if __name__ == '__main__':
    teststraightchecker()
```


![](https://img-blog.csdnimg.cn/20200527214817516.png)

```css
Here is your first hand：['11D', '13H', '3H', '6C', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11001
You now have：['11D', '13H', '3S', '7D', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11001
You now have：['11D', '13H', '11H', '8S', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11101
You now have：['11D', '13H', '11H', '6H', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11100
You now have：['11D', '13H', '11H', '13C', '6C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11110
You now have：['11D', '13H', '11H', '13C', '13S']
Change some cards：y or n： n
Your total score is now：61
Would you like to play again (y or n) ：n
Thank you for playing
```

# 49、Mysql的命令总结和PyMysql

﻿@Author：Runsen

@Date：2019/2/27





## 了解MySQL

MySQL是一个**关系型**数据库管理系统，由瑞典MySQL AB 公司开发，目前属于 Oracle 旗下产品。MySQL 是最流行的关系型数据库管理系统之一，在 WEB 应用方面，MySQL是最好的 RDBMS (Relational Database Management System，关系数据库管理系统) 应用软件。
MySQL是一种关系数据库管理系统，关系数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。
MySQL所使用的 SQL 语言是用于访问数据库的最常用标准化语言。MySQL 软件采用了双授权政策，分为社区版和商业版，由于其体积小、速度快、总体拥有成本低，尤其是开放源码这一特点，一般中小型网站的开发都选择 MySQL 作为网站数据库。

## MySql安装

### 安装和配置

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

### 启动MySQL服务

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

## MySQLl命令

**MySQL进入与退出**   

	- mysql –uusername -ppassword （进入）
	- exit  (退出）


![](https://img-blog.csdnimg.cn/20190227220439691.jpg)

**库级操作语句**

	- 显示所有的库：show databases;
	- 创建库：create database [if not exists] db_name; 
	- 删除库：drop database [if exists] db_name;
	- 进入数据库：use db_name;


![](https://img-blog.csdnimg.cn/20190227220941236.jpg)

**表级操作语句**

	- 显示所有的表：show tables;
	- 创建表：create table [if not exists]  tb_name (create definition…);
	- 显示创建表的信息：show create table tb_name;
	- 删除表：drop table tb_name;


![](https://img-blog.csdnimg.cn/20190227222358297.jpg)

* 注意：语句结束符：**每个语句都以 ; 或者 \G 结束**

**插入数据**

	- 全字段插入： INSERT INTO tb_name VALUE (all_values); 一般只用这种



​	
![](https://img-blog.csdnimg.cn/20190227223014419.jpg)

**查询数据**

	- SELECT field_names FROM tb_name;
	- SELECT * FROM tb_name;
	- SELECT field_names FROM tb_name WHERE conditions; 


![](https://img-blog.csdnimg.cn/20190227223616269.png)

**修改数据**

	- 修改所有数据：UPDATE  tb_name  SET field_1=value_1 ；
	- 修改多个： UPDATE  tb_name  SET field_1=value_1, field_2=value_2 …; 
	- 修改满足条件的数据： UPDATE  tb_name  SET field_1=value_1  WHERE  conditions; 


![](https://img-blog.csdnimg.cn/20190227224457869.jpg)

**删除数据**

	- 删除表中所有数据：DELETE  FROM  tb_name;
	- 删除表中满足条件的数据： DELETE  FROM  tb_name  WHERE  conditions;


![](https://img-blog.csdnimg.cn/20190227224858367.jpg)

**数值类型**

![](https://img-blog.csdnimg.cn/20190227220245409.png)

**字符类**

![](https://img-blog.csdnimg.cn/20190227220327863.png)

## Python连接Mysql


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



# 50、Redis数据库学习

@Author：Runsen
@Date：2019/03/19

## Redis

Redis是一个开源的使用ANSI C语言编写、支持网络、可基于内存亦可持久化的日志型、Key-Value数据库，并提供多种语言的API。从2010年3月15日起，Redis的开发工作由VMware主持。从2013年5月开始，Redis的开发由Pivotal赞助。

Redis特性

- Redis支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。
- Redis不仅仅支持简单的key-value类型的数据，同时还把value分为list，set，zset，hash等数据结构存储。
- 因为Redis交换数据快，所以在服务器中常用来存储一些需要频繁调取的数据，提高效率。

## redis安装




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

## Redis数据模型


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

### 全局key操作

对5 个数据类型都使用的命令

```shell
查看所有的key：keys *
删除键值对：del key
改名：rename  key  new_key
设置过期时间：expire key seconds
```

### String类型

strings是redis最基本的数据类型，一个key对应一个value

```shell
设置数据：set  key  value
查看数据：get  key
追加数据：append  key  value
删除数据：del key;
```

### List类型

```shell
添加数据：rpush key value [value…]
lpush key value [value…]     头部添加数据

查看数据：lrange key start stop
lindex key index      查看某个数据 

修改数据：lset key index value
删除数据：rpop key
lpop key 头部删除数据 

```

### Hash类型

```shell
添加数据：hset key field value 
查看域值：hget key field
hgetall key  查看所有的field和value
查看所有的value：hvals key
查看所有的field：hkeys key

```

### Set类型

```shell
添加数据：sadd key member [member …]
查看数据：smembers key
随机删除：spop key
指定删除：srem key member [member …]

```

### Sorted Set类型

```shell
添加数据： zadd key score member [score2 member2 …] 
查看数据： zrange key start stop 
zrangebyscore key min max 通过scores值查看
删除数据：zrem key member [member …]
通过索引删除多个数据：zremrangebyrank key min max
zremrangebyscore key min max  -- 通过scores值删除

```



**flushall 删除所有数据**

# 51、学会MongoDB数据库

﻿@Author：Runsen
@Date：2019/03/19

## MongoDB简介

安装

```csharp
sudo apt-get install mongodb
```

`MongoDB`是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。它支持的数据结构非常松散，是类似`json`的`bson`格式，因此可以存储比较复杂的数据类型。`Mongo`最大的特点是它支持的查询语言非常强大，其语法有点类似于面向对象的查询语言，几乎可以实现类似关系数据库单表查询的绝大部分功能，而且还支持对数据建立索引。

将数据存储为一个文档，文档类似与Json格式，

```
{
    name:"毛利",
    age:18，
    address: {city:"东莞"， country:"china"}
}
```

## MongoDB数据模型

![](https://img-blog.csdnimg.cn/20190319104459695.png)
 **如何进入和退出mongo**
![](https://img-blog.csdnimg.cn/20190319104516430.png)

### 库级操作语句



- 显示所有库： `show dbs`
- 切换/创建数据库：` use 数据库名称 `
- 查看所在库： `db`
- 删除库：`db.dropDatabase()  `


### 集合操作语句

- 显示当前数据库的集合：` show collections`
- 创建集合： `db.createCollection(name)`

![](https://img-blog.csdnimg.cn/20190319104539962.png)

- 删除集合：` db.集合名称.drop()`


## 文档操作

### 添加文档（数据）

`db.集合名称.insert(document)`

每一条数据，就是一个`document`，就是一条`json`

例：` db.student.insert({name:'毛利', age:18})`

> 注意点：

添加文档时，如果不指定_id参数
MongoDB会为文档分配一个唯一的ObjectId

给定 `_id`
例： `db.student.insert({'_id':1, name:'毛利', age:18})`	

- 添加多条文档

```
db.student.insert([
    {name:'毛利, sex:'男', age:18},
    {name:’毛利的爸爸', sex:'男', age:47},
    {name:’毛利的姐姐', sex:'女', age:23},
    {name:’毛利的妈妈‘, sex:’女', age:44},
])
```


### 查询文档（数据）

`db.集合名称.find([conditions])`

查看集合中全部数据： `db.student.find()`

格式化显示： `db.student.find().pretty() `

查看满足条件的数据： `db.student.find({name:'毛利'})`


### 条件


- and条件  `{$and:[{expression1}, {expression1}, ...]   }`


- or条件 `{$or:[{expression1}, {expression1}, ...]   }`





`db.student.find({$or:[{$and:[{sex:'女'}, {age:23}]},{$and:[{sex:'男'}, {age:{$gte:18}}]}]})`


![](https://img-blog.csdnimg.cn/20190319104553439.png)

### 修改文档（数据）


`db.集合名称.update(<query>, <update>, {multi:<boolean>})`

- 修改一条数据： `db.student.update({sex:'男'}, {age:20})`

把表中的男的`age`改为`20`

- 指定属性修改：` { $set: {age:20} } `


`db.student.update({name:'毛利'}, {$set: {age:666, sex: '不告诉你'}} )`

把毛利的`age`改为`666`，`sex`改为不告诉你

- 更新集合中所有满足条件的文档： `{ multi: true } `

```
db.student.update({sex:'男'}, {$set:{sex:'女'}}, { multi:true} )
```

把所有按的改为女的


### 删除文档（数据）


`db.集合名称.remove(<query>,  {justOne:<boolean>})`


- 删除集合中所有的文档：
  `db.student.remove({})`
- 删除集合中满足条件的所有文档
  `db.student.remove({sex: '男'})`
- 只删除集合中满足条件的第一条文档： `{ justOne: true } `


```db.student.remove({sex:'男'}, { justOne:true} )```




##  在Python程序中操作MongoDB


可以通过pip安装pymongo来实现对MongoDB的操作。`pip3 install pymongo`

```Shell
>>> from pymongo import MongoClient
>>> client = MongoClient('mongodb://192.168.92.92:27017') 
>>> db = client.school
>>> for student in db.students.find():
...     print('姓名:', student['name'])
```


# 52、ViM的使用

@Author：Runsen

@Date：2020/04/03






##  linux介绍


![](https://img-blog.csdnimg.cn/20190318121644669.png)

Linux是一套免费使用和自由传播的类Unix操作系统，是一个基于POSIX和UNIX的多用户、多任务、支持多线程和多CPU的操作系统。它能运行主要的UNIX工具软件、应用程序和网络协议。它支持32位和64位硬件。Linux继承了Unix以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。

## Linux系统发行版本

1. [Redhat](https://www.redhat.com/en)
2. [Ubuntu](https://www.ubuntu.com/)
3. [CentOS](https://www.centos.org/)
4. [Fedora](https://getfedora.org/)
5. [Debian](https://www.debian.org/)
6. [openSUSE](https://www.opensuse.org/)


##  Linux常用命令




| 基本必知 | 作用         | 示例                                                 |
| -------- | ------------ | ---------------------------------------------------- |
| cd       | 切换工作目录 | cd ~ 回到主目录 cd .. 回到上级路径 cd - 回到上次路径 |
| pwd      | 显示工作路径 | pwd                                                  |
| ls       | 显示文件列表 | ls                                                   |
| mkdir    | 创建文件夹   | mkdir test                                           |
| rmdir    | 删除文件夹   | rmdir test                                           |
| cp       | 复制         | cp a.txt b.txt                                       |
| mv       | 移动和重命名 | mv b.txt ../                                         |
| cat      | 查看文件内容 | cat a.txt                                            |
| touch    | 创建文件     | touch  c.txt                                         |
| rm       | 删除文件     | rm c.txt                                             |
| help     | 帮助         | help cd                                              |



## Vim编辑py文件





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




# 53、Linux基础命令，用户管理和文件系统总结（上篇）

﻿@Author：Runsen

@Date：2020/5/27



这次内容是总结极客时间的Linux课程的知识点。耗时一天







## 基础命令

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


## 用户管理

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

## 文件系统

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



# 54、Linux网络管理，软件安装，进程管理总结（中篇）
﻿@Author ：By Runsen




今天的笔记主要是关于Linux操作系统基础的相关知识。






## 1、⽹络管理

### 1.1 网络状态查看 

在Linux中经常使用ifconfig，route和netstat查看网络状态，它们就是. net-tools工具，下面我来使用下。


![](https://img-blog.csdnimg.cn/20200429184929377.png)

![](https://img-blog.csdnimg.cn/20200429185022370.png)


我就说下ifconfig和route


在我们的linux中有很多网卡接口，比如eth0第一块网卡网络接口，eno1板载⽹网卡， ens33 PCI-E⽹网卡 。CentOS 7 使⽤用了⼀致性⽹络设备命名，以上都不匹配，则使⽤ eth0



```shell
[root@node01 ~]# ifconfig eth0
eth0: error fetching interface information: Device not found
[root@node01 ~]# ifconfig ens33
ens33: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.92.90  netmask 255.255.255.0  broadcast 192.168.92.255
        inet6 fe80::b889:1772:c306:ef8f  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:07:43:5a  txqueuelen 1000  (Ethernet)
        RX packets 910  bytes 954985 (932.6 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 450  bytes 38942 (38.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

### 1.2 网络配置文件


ifcfg-eth0，/etc/hosts

在配置hadoop，elasticsearch集群的时候需要在/etc/hosts配置集群IP和主机名，有时候你ping不了百度，可能域名解析不了，需要在/etc/sysconfig/network-scripts/ifcfg-eth0配置


```shell
[root@node01 ~]# vim /etc/sysconfig/network
#########
HOSTNAME=node01
[root@node01 ~]# vim /etc/hosts
#########
192.168.92.90 node01
192.168.92.91 node02
192.168.92.92 node03

[root@node01 ~]# 配置DNS，域名解析服务
[root@node01 ~]# vim /etc/sysconfig/network-scripts/ifcfg-eth0
DNS1=202.106.0.20
DNS2=8.8.8.8
```





### 1.3 ⽹络故障排除命令


第一，ping百度：查看目标机器的网络是否可通

```shell
maoli@ubuntu:~$ ping baidu.com
PING baidu.com (220.181.38.148) 56(84) bytes of data.
64 bytes from 220.181.38.148: icmp_seq=1 ttl=128 time=49.6 ms
64 bytes from 220.181.38.148: icmp_seq=2 ttl=128 time=48.2 ms
^C
--- baidu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 48.223/48.948/49.673/0.725 ms
```





traceroute




nslookup：nslookup www.baidu.com     Server即为域名对应的ip


```shell
maoli@ubuntu:~$ nslookup www.baidu.com
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
www.baidu.com	canonical name = www.a.shifen.com.
Name:	www.a.shifen.com
Address: 182.61.200.6
Name:	www.a.shifen.com
Address: 182.61.200.7
```



telnet：如果ip是可达的，但是服务仍有然有问题，则可以通过telnet去查看服务端口状态


tcpdump：

tcpdump -i any -n port 80 # 抓取所有网卡（any）80端口数据包，并且以ip形式显示（-n）

```shell
maoli@ubuntu:~$ sudo tcpdump -i any -n port 80 -n
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 262144 bytes
10:28:11.003675 IP 192.168.92.1.53951 > 192.168.92.135.80: Flags [S], seq 185886164, win 64240, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
10:28:11.003875 IP 192.168.92.135.80 > 192.168.92.1.53951: Flags [S.], seq 2863640054, ack 185886165, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
10:28:11.004114 IP 192.168.92.1.53951 > 192.168.92.135.80: Flags [.], ack 1, win 4106, length 0
10:28:11.010472 IP 192.168.92.1.53951 > 192.168.92.135.80: Flags [P.], seq 1:476, ack 1, win 4106, length 475: HTTP: GET /sqli-labs/ HTTP/1.1
```


tcpdump -i any -n host 10.0.0.1 and port 80# 抓取所有网卡的80端口和10.0.0.1之间的数据包，并且以ip形式显示



netstat 查看服务监听端口状态是否正确
    -n 显示ip地址
    -t tcp协议
    -p 显示端口对应的进程
    -l tcp的监听状态（listen）
    -ntpl 查看端口开放情况

```shell
maoli@ubuntu:~$ sudo netstat -ntlp
激活Internet连接 (仅服务器)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1111/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      14200/cupsd     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1148/mysqld     
tcp        0      0 127.0.0.1:6379          0.0.0.0:*               LISTEN      1165/redis-server 1
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1285/dnsmasq    
tcp6       0      0 :::22                   :::*                    LISTEN      1111/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      14200/cupsd     
tcp6       0      0 :::9000                 :::*                    LISTEN      2234/docker-proxy
tcp6       0      0 :::80                   :::*                    LISTEN      1842/apache2 
```

### 1.4 ⽹络服务管理


⽹络服务管理程序分为两种，分别为SysV和systemd。现在Systemd已经基本取代了SysV的Init。

<table>
<thead>
<tr>
<th>命令用途</th>
<th>SysVInit命令</th>
<th>Systemd命令</th>
</tr>
</thead>
<tbody>
<tr>
<td>服务启动</td>
<td>service 服务名 start</td>
<td>systemd start 服务名.service (.service可省略，后同）</td>
</tr>
<tr>
<td>服务停止</td>
<td>service 服务名 stop</td>
<td>systemctl stop 服务名</td>
</tr>
<tr>
<td>服务重启</td>
<td>service 服务名 restart</td>
<td>systemctl restart 服务名</td>
</tr>
<tr>
<td>服务重新加载</td>
<td>service 服务名 reload</td>
<td>systemctl reload 服务名</td>
</tr>
<tr>
<td>服务状态确认</td>
<td>service 服务名 status</td>
<td>systemctl status 服务名</td>
</tr>
<tr>
<td>服务开机启动设定</td>
<td>chkconfig 服务名 on</td>
<td>systemctl enable 服务名</td>
</tr>
<tr>
<td>取消服务开机启动设定</td>
<td>chkconfig service off</td>
<td>systemctl disable 服务名</td>
</tr>
<tr>
<td>确认服务开机启动设定状态</td>
<td>chkconfig 服务名</td>
<td>systemctl is-enabled 服务名</td>
</tr>
<tr>
<td>加载服务配置文件</td>
<td>chkconfig 服务名 -add</td>
<td>systemctl deamon-reload</td>
</tr>
<tr>
<td>关机</td>
<td>halt</td>
<td>systemctl halt</td>
</tr>
<tr>
<td>关机（电源）</td>
<td>poweroff</td>
<td>systemctl poweroff</td>
</tr>
<tr>
<td>重启</td>
<td>reboot</td>
<td>systemctl reboot</td>
</tr>
<tr>
<td>休眠</td>
<td>pm-hibernate</td>
<td>systemctl hibernate</td>
</tr>
<tr>
<td>挂起</td>
<td>pm-suspend</td>
<td>systemctl suspend</td>
</tr>
</tbody>
</table>


### 1.5 设置静态ip

在搭建任何集群，都是要设置静态ip的。

```shell
[root@node01]# vim /etc/sysconfig/network-scripts/ifcfg-ens33

################
BOOTPROTO=static
ONBOOT="yes"
# 网关地址根据系统的网络而定
GATEWAY=192.168.92.2
# 设置的静态ip
IPADDR=192.168.92.92
NETMASK=255.255.255.0
# 配置DNS服务器
DNS1=8.8.8.8
DNS2=8.8.4.4

```

## 2. 软件安装


### 2.1 rpm安装


在 Linux 操作系统下，几乎所有的软件均通过RPM 进行安装、卸载及管理等操作。RPM 的全称为Redhat Package Manager ，是由Redhat 公司提出的，用于管理Linux 下软件包的软件，主要用于CentOS、RedHat等linux系统，软件安装包格式为 rpm。


比如一个vim的rpm叫：vim-common-7.4.10-5.el7.x86_64.rpm 。vim-common是软件名称，7.4.10-5软件版本，el7Red Hat Enterprise Linux 指的是centos7系统版本，x86_64指的是系统平台x86

rpm 命令常⽤参数，-q 查询软件包，-i 安装软件包和-e 卸载软件包


### 2.2 yum 包管理器

yum（全称 Yellow dog Updater, Modified）是一个前端软件包管理器，基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系。


下载阿里云的yum源到了/etc/yum.repos.d中


备份yum源

```shell
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

下载新的CentOS-Base.repo 到/etc/yum.repos.d/，这里指的是centos7

```shell
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
# 运行yum makecache生成缓存
yum clean all
yum makecache

```


这时候可以查看yum的base


```shell
[root@node01 ~]# vim /etc/yum.repos.d/CentOS-Base.repo 
[base]
name=CentOS-$releasever - Base - mirrors.aliyun.com
failovermethod=priority
baseurl=http://mirrors.aliyun.com/centos/$releasever/os/$basearch/
        http://mirrors.aliyuncs.com/centos/$releasever/os/$basearch/
        http://mirrors.cloud.aliyuncs.com/centos/$releasever/os/$basearch/
gpgcheck=1
gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7

```


由于yum中有的mirror速度是非常慢的。对此，我可以下载fastestmirror插件。

```shell
[root@node01 ~]# yum install yum-fastestmirror -y
[root@node01 ~]# cat  /etc/yum/pluginconf.d/fastestmirror.conf
[main]
enabled=1
verbose=0
always_print_best_host = true
socket_timeout=3
#  Relative paths are relative to the cachedir (and so works for users as well
# as root).
hostfilepath=timedhosts.txt
maxhostfileage=10
maxthreads=15
#exclude=.gov, facebook
#include_only=.nl,.de,.uk,.ie

```

yum常用命令install 安装软件包，remove 卸载软件包，list| grouplist 查看软件包，update 升级软件包







### 2.3 apt安装

Ubuntu的高级打包工具（APT，Advanced Packaging Tool ），Debian、Ubuntu 使⽤ apt 包管理器，软件安装包格式为 deb。


apt安装一个nginx

```shell
maoli@ubuntu:~$ sudo apt-get install nginx
/usr/sbin/nginx：主程序
/etc/nginx：存放配置文件
/usr/share/nginx：存放静态文件
/var/log/nginx：存放日志

```

### 2.4 make install编译源码安装

源码的安装一般由3个步骤组成：配置(configure)、编译(make)、安装(make install)。

configure文件是一个可执行的脚本文件，它有很多选项，在待安装的源码目录下使用命令./configure –help可以输出详细的选项列表。



其中--prefix选项是配置安装目录，如果不配置该选项，安装后可执行文件默认放在/usr /local/bin，库文件默认放在/usr/local/lib，配置文件默认放在/usr/local/etc，其它的资源文件放在/usr /local/share，比较凌乱。

如果配置了--prefix，如：./configure --prefix=/usr/local/python3

安装后的所有资源文件都会被放在/usr/local/python3目录中，不会分散到其他目录。如果删除直接删除这个文件就可以了。




比如centos7安装Python3.6

```shell
[root@node01 ~]# yum install yum-utils
[root@node01 ~]# yum install openssl-devel -y 
[root@node01 ~]# mkdir -p  /usr/local/python3
[root@node01 ~]# cd /usr/local/python3/
[root@node01 python3]# wget https://www.python.org/ftp/python/3.6.7/Python-3.6.7.tgz
[root@node01 python3]# tar -zxvf Python-3.6.7.tgz
[root@node01 python3]# cd Python-3.6.7
[root@node01 python3.6.7]# ./configure --prefix=/usr/local/python3 --with-ssl 
[root@node01 python3.6.7]# make && make install
Installing collected packages: setuptools, pip
Successfully installed pip-10.0.1 setuptools-39.0.
[root@node01 python3.6.7]# cd ..
[root@node01 Python3]# ln -s /usr/local/python3/bin/python3 /usr/bin/python3
[root@node01 Python3]# ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
[root@node01 Python3]# python3 -V
Python 3.6.7
[root@node01 Python3]# python3
Python 3.6.7 (default, Mar  5 2020, 11:00:15) 
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()

```




## 3. 进程管理

进程 是 Unix 和 Linux 系统中对正在运行中的应用程序的抽象，通过它可以管理和监视程序对内存、处理器时间和 I / O 资源的使用。



### 3.1 杀进程


很多时候需要杀进程，ps -ef可以查看所有的进程，ps -ef|grep 查看具体的任务的进程，


比如查看Mysql进程

```shell
[root@node01 ~]# ps -ef|grep mysql
clouder+   1726      1 38 15:16 ?        00:04:34 /usr/java/jdk1.8.0_241/bin/java -cp .:/usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/java/postgresql-connector-java.jar:lib/* -server -Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties -Dfile.encoding=UTF-8 -Dcmf.root.logger=INFO,LOGFILE -Dcmf.log.dir=/var/log/cloudera-scm-server -Dcmf.log.file=cloudera-scm-server.log -Dcmf.jetty.threshhold=WARN -Dcmf.schema.dir=/opt/cloudera/cm/schema -Djava.awt.headless=true -Djava.net.preferIPv4Stack=true -Dpython.home=/opt/cloudera/cm/python -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:+HeapDumpOnOutOfMemoryError -Xmx2G -XX:MaxPermSize=256m -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/tmp -XX:OnOutOfMemoryError=kill -9 %p com.cloudera.server.cmf.Main
mysql      2745      1  0 15:16 ?        00:00:04 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
root       9864   4959  0 15:28 pts/0    00:00:00 grep --color=auto mysql


```

查找与指定条件匹配的进程 - **pgrep**,，就是其缩写


```shell
[root ~]$ pgrep mysqld
3584

```

查看端口的进程，比如mysql的端口是3306

```shell
[root@node01 ~]# lsof -i:3306
COMMAND  PID         USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
java    1726 cloudera-scm  285u  IPv4  50625      0t0  TCP localhost:58292->localhost:mysql (ESTABLISHED)
mysqld  2745        mysql   27u  IPv6  47164      0t0  TCP *:mysql (LISTEN)
mysqld  2745        mysql   40u  IPv6  54060      0t0  TCP localhost:mysql->localhost:58296 (E

```


杀进程使用kill -9命令，比如 kill -9 1726，就是杀Mysql进程



### 3.2 守护进程




守护进程就是通常说的daemon进程，是linux后台执行的一种进程，不会随着终端的关闭而停止运行，开Linux系统的会自动打开。




不挂断地运行命令。no hangup的缩写，意即“不挂断”。和&联用


```shell
[root@node01 ~]# tail -f /var/log/messages
May  1 16:01:10 node01 kubelet: I0501 16:01:10.344757   26130 server.go:837] Client rotation is on, will bootstrap in background

[root@node01 ~]# ps -ef|grep tail
root      26210  25353  0 16:01 pts/1    00:00:00 tail -f /var/log/messages
root      26555  25310  0 16:01 pts/0    00:00:00 grep --color=auto tail

关闭上面的tail -f /var/log/messages

[root@node01 ~]# ps -ef|grep tail
[root@node01 ~]# ps -ef|grep tail
root      27353  25310  0 16:03 pts/0    00:00:00 grep --color=auto tail


```


nohup和 &连用

```shell
[root@node01 ~]# nohup tail -f /var/log/messages &
[1] 27718
nohup: 忽略输入并把输出追加到"nohup.out"

[root@node01 ~]# ps -ef|grep tail
root      27718  25353  0 16:04 pts/1    00:00:00 tail -f /var/log/messages
root      29444  25310  0 16:07 pts/0    00:00:00 grep --color=auto tail
关闭上面的nohup tail -f /var/log/messages &

[root@node01 ~]# ps -ef|grep tail
root      27718      1  0 16:04 ?        00:00:00 tail -f /var/log/messages
root      29946  25310  0 16:08 pts/0    00:00:00 grep --color=auto tail

```


### 3.3 查看进程 

`- **ps**。`

```shell
[root ~]# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Jun23 ?        00:00:05 /usr/lib/systemd/systemd --switched-root --system --deserialize 21
root         2     0  0 Jun23 ?        00:00:00 [kthreadd]
...
[root ~]# ps -ef | grep mysqld
root      4943  4581  0 22:45 pts/0    00:00:00 grep --color=auto mysqld
mysql    25257     1  0 Jun25 ?        00:00:39 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid

```




# 55、Linux磁盘管理和Shell编程（下篇）

﻿@Author：Runsen
@Date：2020/5/27




## 磁盘管理

Linux磁盘管理常用三个命令为df、du和fdisk。


### 列出文件系统的磁盘使用状况

 列出文件系统的磁盘使用状况 - **df**。

```shell
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

### 磁盘分区表操作

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





### 磁盘分区工具

. 磁盘分区工具 - **parted**。


### 格式化文件系统

格式化文件系统 - **mkfs**。

```Shell
maoli@ubuntu:~$ mkfs -t ext4 -v /dev/sdb
```

- `-t` - 指定文件系统的类型。
- `-c` - 创建文件系统时检查磁盘损坏情况。
- `-v` - 显示详细信息。

###  文件系统检查


文件系统检查 - **fsck**。


### 转换或拷贝文件

转换或拷贝文件 - **dd**。


### 挂载/卸载

挂载/卸载 - **mount** / **umount**。

###  创建/激活/关闭交换分区

创建/激活/关闭交换分区 - **mkswap** / **swapon** / **swapoff**。



参考[菜鸟教程](https://www.runoob.com/linux/linux-filesystem.html)




## Shell

Shell是一个连接用户和操作系统的应用程序，它提供了人机交互的界面（接口），用户通过这个界面访问操作系统内核的服务。Shell脚本是一种为Shell编写的脚本程序，我们可以通过Shell脚本来进行系统管理，同时也可以通过它进行文件操作。


互联网上有大量关于Shell脚本的相关知识，我不打算再此对Shell脚本做一个全面系统的讲解，我们通过下面的代码来感性的认识下Shell脚本就行了。

### 新建Shell脚本

打开文本编辑器(可以使用 vi/vim 命令来创建文件)，新建一个文件 test.sh，扩展名为 sh（sh代表shell）。

```shell
maoli@ubuntu:~$ vim test.sh

#!/bin/bash
echo "Hello World !"
```

输入一个`echo "Hello World !"`，这个语法和php很相似。运行一个sh需用 `chmod +x `脚本具有执行权限


```shell
maoli@ubuntu:~$ chmod +x ./test.sh
maoli@ubuntu:~$ ./test.sh 
Hello World !

```

### 变量

变量名不加美元符号（\$，PHP语言中变量需要）。比如在shell中 定义变量`name = Runsen`，而在php就是`$name = Runsen`


使用一个定义过的变量，只要在变量名前面加美元符号即可，如：`$name`或者`${name}`。变量名外面的花括号是可选的，加不加都行。



变量支持字符串类型，浮点等类型，常见有这 3 个前缀：

- unset：删除变量
- readonly：标记只读变量
- export：指定全局变量

```shell
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



### 预定义变量


预定义变量常用来获取命令行的输入，有下面这些：

```shell
$0 ：脚本文件名
$1-9 ：第 1-9 个命令行参数名
$# ：命令行参数个数
$@ ：所有命令行参数
$* ：所有命令行参数
$? ：前一个命令的退出状态，可用于获取函数返回值
$$ ：执行的进程 ID
```

一个例子：

```shell
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


```shell
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

```shell
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

```shell
if [ $VART -eq 10 ]; then echo "true"; else echo "false";fi

```




###  for 循环


 for 循环和Python没有什么区别，挺简单的

```shell
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


### 打印


printf 命令模仿 C 程序库（library）里的 printf() 程序， 这里补充`-e `开启转义` \c `不换行，其他和Python一样。

```shell
maoli@ubuntu:~$ echo "It is a test"
It is a test
maoli@ubuntu:~$ echo -e "OK! \n"
OK! 

maoli@ubuntu:~$ printf "%-10s %-8s %-4s\n" 姓名 性别 体重kg  
姓名     性别   体重kg
maoli@ubuntu:~$ printf "%-10s %-8s %-4.2f\n" Runsen 男 65
Runsen     男      65.00

```

### test 

Shell中的 test 命令用于检查某个条件是否成立，它可以进行数值、字符和文件三个方面的测试。



| 参数 | 说明           |
| ---- | -------------- |
| -eq  | 等于则为真     |
| -ne  | 不等于则为真   |
| -gt  | 大于则为真     |
| -ge  | 大于等于则为真 |
| -lt  | 小于则为真     |
| -le  | 小于等于则为真 |

比如下判断两个字符串是否相同t

```shell
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



## Shell 函数

shell中函数的定义格式如下：


```shell
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

##  shell实例


### 求和

例子1：输入两个整数m和n，计算从m到n的整数求和的结果。


```shell
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

### 创建文件夹和文件

例子2：自动创建文件夹和指定数量的文件。


```shell
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

# 56、教用Python中的turtle海龟画图（上篇）



@Author：Runsen



在Python中的turtle海龟画图，我相信大家都有了解，我在之前也写过这类的博文，但是我发现真的不行，今天就重写，保留好的地方，添加更多的要点



我觉得没有什么东西可以写，就是需要不断地实践。





## 画一条线


```python
import turtle
t = turtle.Pen()
t.forward(100)
```


t = turtle.Pen()告诉计算机我们使用t表示海龟的钢笔，
forward(distance) ：别名  turtle.fd( distance ) 沿着当前方向前进指定距离，这里的距离的单位是像素。

![](https://img-blog.csdnimg.cn/20200529111800162.png)
黑色的小三角就是我们的小海龟。三角后面的直线，就是小海龟“前进100步”所留下的痕迹


##  画一个正方形


如果一直前进而不转弯，画出的图也会相当单调。这不是我们所希望的，我们需要“转弯语句”。我们可以“向右转90度”，使用“t.right(90)”，或“向左转90度”，使用“t.left(90)”。这里我们选向右转吧。将“t.right(90)”加入代码，运行：


```python
import turtle
t = turtle.Pen()
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
```



![](https://img-blog.csdnimg.cn/20200529112333480.png)



## 画一个三角形




我们使用turtle.setup(400,400)来设置画布的大小，设置一个400 * 400的窗口大小。
t.left(120)以箭头的方向向左旋转120角度。

```python
import turtle
turtle.setup(400,400)
t = turtle.Pen()
t.forward(100)
t.left(120)
t.forward(100)
t.left(120)
t.forward(100)
t.left(120)
```

![](https://img-blog.csdnimg.cn/20200529112754795.png)

## 画一个圆



t.circle(50)，就是画一个半径为50的圆。


```python
import turtle
turtle.setup(400,400)
t = turtle.Pen()
t.circle(50)
turtle.done()
```



![](https://img-blog.csdnimg.cn/20200529113224314.png)

turtle.done()就是画完的时候停下来，不要马上关闭。


## 绘制梯形




```python
import turtle
turtle.up()
turtle.fillcolor('yellow')
turtle.begin_fill()
turtle.goto(100,-100)
turtle.down()
turtle.goto(200,-100)
turtle.goto(250,-200)
turtle.goto(50,-200)
turtle.goto(100,-100)
turtle.end_fill()
turtle.done()


```

此梯形绘制在第四象限，所以梯形形每个顶点的坐标中，x坐标为正,y坐标为负。四个点的坐标分别选择为(100,-100)、(200,-100)、(250,-200)、(50,-200)。goto也是画的意思，goto（x，y）就是以x和y坐标定位画线。down就是停下来。end_fill就是给封闭图形添加颜色。
![](https://img-blog.csdnimg.cn/20200529113621144.png)

## 画一个星星

星星就是四个圆弧组成，转弯是180度

```python
import turtle
turtle.setup(800, 600)  # 创建绘图窗口

for i in range(4):   # 循环四次
    turtle.circle(90,90)   # 顺时针画一个半径90，90度对应的圆弧 顺时针是正
    turtle.right(180)       # 右转180度

turtle.done()
```

![](https://img-blog.csdnimg.cn/20200529114831673.gif)

## 画一个五角星

五角星是边数最少多角形。最简单的画法是先画一个正五边形，把各角用直线相连并擦去原来的五边形或者延长原五边形的各边直到它们相交，从而得到一个大的五角星。



```python
import turtle
 turtle.color('black','red')
 turtle.begin_fill()
 for i in range(5):
     turtle.forward(100)
     turtle.right(144)
 turtle.end_fill()
```




![](https://img-blog.csdnimg.cn/20200529115402257.png)

## 画一个图案

```python
import turtle
t = turtle.Pen()
for x in range(100):
    t.forward(x)
    t.left(90)
turtle.done()

```



![](https://img-blog.csdnimg.cn/20200529115602232.gif)

## 方法总结



```
turtle.fd(d)、
turtle.forward(d)：以当前方向，往前行进d像素。
turtle.bk(d)、
turtle.backword(d)：保持当前方向不变，往后退行d像素。
turtle.circle(r,angle,steps=)：从当前位置以r为半径圆的angle角度旋转。
turtle.seth(angle)：以x轴方向为起点将方向偏转为angle度，逆时针为正。只改变行进方向但不行进。
turtle.left(angle)：在当前行进方向的基础上，向左旋转angle度。
turtle.right(angle)：在当前行进方向的基础上，向右旋转angle度。
```





# 57、教用Python中的turtle海龟画图（下篇）

﻿@Author：Runsen


在Python中的turtle海龟画图，我相信大家都有了解，我在之前也写过这类的博文，但是我发现真的不行，今天就重写，保留好的地方，添加更多的要点

我觉得没有什么东西可以写，就是需要不断地实践。



## 画一个朵花

```csharp
import turtle
t = turtle.Pen()
def draw_leaf():
    for i in range(2):
        for j in range(15):
            t.forward(5)
            t.right(6)
        t.right(90)
t.goto(0,-150)
t.left(90)
t.forward(50)
draw_leaf()
t.forward(150)
for i in range(6):
    draw_leaf()
    t.right(60)
t.down()
```

上图是画一朵花的程序，使用了函数来定义drawleaf，每一掰叶子由两条弧线组成，每一条弧线重复画15次，每次前进5步，右转6度。

看不懂看下步骤


![](https://img-blog.csdnimg.cn/20200529120443382.png)


这朵花由4部分组成，一个向上长50步的直线，一片叶子，长150步的直线和6片叶子组成的花。



![](https://img-blog.csdnimg.cn/20200529120855841.gif)


最后给叶子填充颜色，给花朵填充颜色。



```csharp
import turtle
t = turtle.Pen()
def draw_leaf():
    for i in range(2):
        for j in range(15):
            t.forward(5)
            t.right(6)
        t.right(90)
t.goto(0,-150)
t.left(90)
t.forward(50)
t.fillcolor("green")
t.begin_fill()
draw_leaf()
t.end_fill()
t.forward(50)
t.right(270)
t.fillcolor("green")
t.begin_fill()
draw_leaf()
t.end_fill()
t.right(90)
t.forward(130)
t.fillcolor("red")
t.begin_fill()
for i in range(6):
    draw_leaf()
    t.right(60)
t.end_fill()
t.down()
```





![](https://img-blog.csdnimg.cn/20200529121458717.gif)



## 酷炫的图形


```csharp
import turtle

for i in range(360):
   turtle.rt(1)
   turtle.circle(100,None,4)
turtle.exitonclick()
```

![](https://img-blog.csdnimg.cn/20200529122206413.gif)

## 画时钟

![](https://img-blog.csdnimg.cn/20190419230504599.png)
![](https://img-blog.csdnimg.cn/20190419230608390.png?0)
![](https://img-blog.csdnimg.cn/20190419230646596.png)

```
# -*- coding：utf-8 -*-
# time ：2019/4/19 22:53
# author: 毛利

import turtle
import datetime
# 移动一段距离
def skip(distance):
    """
    移动乌龟一段距离，不留痕迹
    :param distance: 像素
    :return:
    """
    turtle.penup()
    turtle.forward(distance)
    turtle.pendown()

def draw_clock():
    # 先画表盘
    # 先画点
    # 移动一段距离，画一个点，然后退回
    # 转动6°，再移动一段距离，画一个点，然后退回
    # 循环 60次
    # 让乌龟的方向默认向上
    turtle.reset()
    turtle.hideturtle()
    for i in range(60):

        skip(160)
        # 根据 5格一个时钟
        if i % 5 == 0:
            turtle.pensize(7)
            # 画时钟
            turtle.forward(20)
            if i == 0:
                turtle.write(12, align='center', font=('Courier', 14, 'bold'))
            elif i == 25 or i == 30 or i == 35:
                skip(25)
                turtle.write(int(i/5), align='center', font=('Courier', 14, 'bold'))
                skip(-25)

            else:
                turtle.write(int(i/5), align='center', font=('Courier', 14, 'bold'))
            skip(-20)
        else:
            turtle.pensize(1)
            turtle.dot()
        skip(-160)
        turtle.right(6)


def get_week(t):
    week = ['星期一', '星期二', '星期三', '星期四', '星期五', '星期六', '星期日']
    return week[t.weekday()]


def create_hand(length, name):
    turtle.reset()
    skip(-length * 0.1)
    turtle.begin_poly()
    turtle.forward(length * 1.1)
    turtle.end_poly()
    # 注册
    turtle.register_shape(name, turtle.get_poly())
    hand = turtle.Turtle()
    hand.shape(name)
    hand.shapesize(1, 1, 3)
    return hand

def run():
    # 不停的获取时间
    t = datetime.datetime.today()
    bob.forward(65)
    bob.write(get_week(t), align='center', font=('Courier', 14, 'bold'))
    bob.back(130)
    bob.write(t.strftime('%Y-%m-%d'), align='center', font=('Courier', 14, 'bold'))
    bob.home()
    # 指针移动
    second = t.second + t.microsecond * 0.000001
    minute = t.minute + second/60
    hour = t.hour + minute/60
    turtle.tracer(True)
    second_hand.setheading(6*second)
    minute_hand.setheading(6*minute)
    hour_hand.setheading(30*hour)
    turtle.ontimer(run, 200)
if __name__ == '__main__':
    # 画秒针,分针，时针
    turtle.mode('logo')
    turtle.hideturtle()
    global second_hand, minute_hand, hour_hand, bob

    second_hand = create_hand(135, 'second_hand')
    minute_hand = create_hand(125, 'minute_hand')
    hour_hand = create_hand(90, 'hour_hand')
    # 创建一个新的turtle对象，去循环的操作
    bob = turtle.Turtle()
    bob.hideturtle()
    bob.penup()

    turtle.tracer(False)
    draw_clock()
    run()

    turtle.mainloop()

```

![](https://img-blog.csdnimg.cn/20190419230020836.gif)

对于urtle海龟画图，没必要研究这么深，就是小孩子的玩意，学习下，以后教下儿子就可以了。


# 58、Python中的正则表达式
@Author：Runsen







## 正则表达式

正则表达式是一个特殊的字符序列，由普通字符和元字符组成。元字符能帮助你方便的检查一个字符串是否与某种模式匹配。

正则表达式应用的场景也非常多。常见的比如：搜索引擎的搜索、爬虫结果的匹配、文本数据的提取等等都会用到，所以掌握甚至精通正则表达式是一个硬性技能，非常必要。

Python中则提供了强大的正则表达式处理模块，即 re 模块， 为Python的内置模块。

下面，我带大家来一个入门demo例子，代码如下：

```python
import re
reg_string = "hello9527python@wangcai.@!:xiaoqiang"
reg = "hello"
result = re.findall(reg,reg_string)
print(result)
```

这里reg_string就是我们的普通字符，reg就是我们的元字符。

我们使用 re 模块中的findall函数，进行匹配，返回的结果是列表数据类型。
![](https://img-blog.csdnimg.cn/20200529153902631.png)

我们使用正则表达式，就是为了在很长的字符串中，找到我们需要的字符串片段。


## 元字符


Python中常见元字符及其含义如下：

| 元字符 | 含义                       |
| ------ | -------------------------- |
| .      | 匹配除换行符以外的任意字符 |
| \w     | 匹配数字字母下划线汉字     |
| \s     | 匹配任意空白符             |
| \d     | 匹配所有的数字             |
| \b     | 匹配单词的开始或结束       |
| ^      | 匹配字符串的开始           |
| $      | 匹配字符串的开始结束       |

下面，我们具体使用下Python中的常见的元字符。



我们还是使用上次的例子，这次我们需要在reg_string匹配出我们的数字，只需要将reg换成\d，代码如下图所示。

![](https://img-blog.csdnimg.cn/2020052915403186.png)
比如，我们在之前的reg的hello前面加上一个^，意味着我们 匹配字符串的开始的hello，那么结果就是一个，就是我们开头的hello。




如果，我们把reg换成\w，代码如下图所示。


![](https://img-blog.csdnimg.cn/20200529154055218.png)


这样就是匹配数字字母下划线，包括我们的汉字。



## 反义代码


Python中常见反义代码 及其含义如下：

| 反义代码 | 含义                                 |
| -------- | ------------------------------------ |
| \W       | 匹配任意不是数字字母下划线汉字的字符 |
| \S       | 匹配任意不是空白符的字符             |
| \D       | 匹配非数字                           |
| \B       | 匹配不是单词的开始或结束             |
| [^a]     | 匹配除了a以外的任意字符              |
| [^abcd]  | 匹配除了abcd以外的任意字符           |


其实，记忆很简单，我们是不是知道\d匹配数字，那么\d的大写\D就是匹配非数字，元字符[a]匹配a任意字符，那么[^a]就是匹配除了a以外的任意字符。

下面是具体例子

```
>>> import re
>>> reg_string = "hello9527python@wangcai.@!:xiaoqiang"
>>> reg = "\D"
>>> re.findall(reg,reg_string)
['h', 'e', 'l', 'l', 'o', 'p', 'y', 't', 'h', 'o', 'n', '@', 'w', 'a', 'n', 'g', 'c', 'a', 'i', '.', '@', '!', ':', 'x', 'i', 'a', 'o', 'q', 'i', 'a', 'n', 'g']
>>> reg = "[^a-p]"
['9', '5', '2', '7', 'y', 't', '@', 'w', '.', '@', '!', ':', 'x', 'q']
```

## 限定符


什么是限定符？就是限定我们匹配的个数的东西。

Python中常见限定符 及其含义如下：

| 限定符 | 含义                |
| ------ | ------------------- |
| *      | 重复零次或多次      |
| +      | 重复一次或多次      |
| ？     | 重复零次或一次      |
| {n}    | 重复n次             |
| {n,}   | 重复n次或更多次     |
| {n,m}  | 重复n次到m次 {1，3} |



我们还是用我们之前的reg_string，这次我们限定了元字符为\d{4}，也就是我们的匹配的数字必须是4个。

![](https://img-blog.csdnimg.cn/20200529154430919.png)


下面，我们来提高难度，匹配字母和数字，限定个数为4个。

这样我们可以使用[0-9a-z]{4}，作为我们的元字符，[0-9a-z]代表了0到9的十个数字和a到z的小写26个英文字母。[0-9a-z]{4}限定了个数为4个。

我们打印输出下。


![](https://img-blog.csdnimg.cn/20200529154456336.png)


如果遇到了不是在[0-9a-z]范围内，就会跳过，直到后面的4个都是在[0-9a-z]范围内就打印输出。

## 匹配ip地址

在互联网中，一台主机只有一个IP地址。IP地址用于在TCP/IP通信协议中标记每台计算机的地址，通常用于十进制来表示，如192.168.1.100。

在window系统中，我们可以通过ipconfig查看我们的ip。在linux系统中，我们可以通过ifconfig查看我们的ip。

我们的ip字符串是这样子的：`ip = "this is ip:192.168.1.123 :172.138.2.15"`

下面要求使用正则表达式，将ip匹配出来。

其实，我们主要编写元字符。比如：`reg = "\d{3}.\d+.\d+.\d+"，`因为第一个数字必须是三位数开头，我们可以设定`\d{3}`固定起来。

![](https://img-blog.csdnimg.cn/20200529155054271.png)
我们除了可以使用findall，还可以使用search，我们把元字符`reg = "(\d{1,3}.){3}\d{1,3}"`。

这元字符中的`\d{1,3}`.指定是我们ip前三个数字，后面加`{3}`就是重复3次。`\d{1,3}`指的就是我们ip最后一个数字。

但是search和findall是有区别的，search只能匹配第一个，我们需要使用列表取出第一个，而findall匹配所有。



![](https://img-blog.csdnimg.cn/20200529155110473.png)

## 组匹配


什么是组匹配，比如说这里边我有一个字符串`s = this is phone:13888888888 and this is my postcode:012345`，我需要你把手机号和验证码匹配出来。

因为，我们要匹配两个，而已每个的元字符都是不一样的。所以，我们需要分组匹配。

正则表达式的括号表示分组匹配，括号中的模式可以用来匹配分组的内容。

于是我们的元字符就变成：`reg = this is phone:(\d{11}) and this is my postcode:(\d{6})`

我们一般使用search进行分组匹配，上次我是不是说过search需要使用列表取出来，这里的组匹配也是一样，不过这里用的是`group()`方法。`group(1)`代表了我们的手机号，`group(2)`代表了我们的验证码，而`group(0)`代表了我们的手机号和验证码，代码如下图所示。


![](https://img-blog.csdnimg.cn/2020052915461790.png)

在正则表达式中，除了findall和search用法，还有一个match用法。

match用法只匹配开头的，也是需要group()取出来，下图match的例子。



![](https://img-blog.csdnimg.cn/20200529154646890.png)
这是的re.I是忽略大小写的意思。


## 贪婪与非贪婪

贪婪与非贪婪模式影响的是被量词修饰的子表达式的匹配行为，贪婪模式在整个表达式匹配成功的前提下，尽可能多的匹配，而非贪婪模式在整个表达式匹配成功的前提下，尽可能少的匹配。

贪婪和非贪婪有几个非常重要的操作符。

| 操作符 | 含义             |
| ------ | ---------------- |
| *      | 重复零次或更多次 |
| +      | 重复一次或更多次 |
| ？     | 重复零次或一次   |

比如说这里边我有一个字符串`reg_string = pythonnnnnnnnnpythonHelloPytho`，我们先使用贪婪的模式下的元字符：`reg = "python*"`
![](https://img-blog.csdnimg.cn/20200529154755550.png)

贪婪模式下的`reg = "python*"`，意味着n重复零次或更多次。所以我们看到了第一关结果的`pythonnnnnnnnn`尽可能多的匹配。

下面使用非贪婪的模式下的元字符：`reg = "python*?"`,`reg = "python+?"`,`reg = "python??"`。

![](https://img-blog.csdnimg.cn/20200529154811523.png)
非贪婪模式下的`reg = "python*"`，意味着`n`零次或一次，所以我们没有看到`pythonnnnnnnnn`的结果。




## 手机号码验证


首先，我们要知道我们的手机号码是什么开头的？

移动手机号码开头有16个号段：134、135、136、137、138、139、147、150、151、152、157、158、159、182、187、188。

联通手机号码开头有7种号段：130、131、132、155、156、185、186。

电信手机号码开头有4个号段：133、153、180、189。


![](https://img-blog.csdnimg.cn/20200529155221294.png)

这样我们就可以在开头做事情了，先判断开头是不是上面的号段，` regex = "^((13[0-9])|(14[5|7])|(15([0-3]|[5-9]))|(18[0,5-9]))\d{8}$"`，就是我们的元字符，代码如下：

```python
import re

def checkCellphone(cellphone):
    regex = "^((13[0-9])|(14[5|7])|(15([0-3]|[5-9]))|(18[0,5-9]))\d{8}$"
    result = re.findall(regex,cellphone)
    if result:
        print("匹配成功")
        return True
    else:
        print("匹配失败")
        return False
cellphone = '13717378202'
checkCellphone(cellphone)


#匹配成功
#True
```


## 匹配邮箱合法性

下面，我们进行一个作业，就是来匹配我们的邮箱号码。

![](https://img-blog.csdnimg.cn/20200529155327327.png)


作业的答案如下：


```python
import re

def checkEmail(email):

    regex_1 = '^(\w+)@sina.com$'
    regex_2 = '^(\w+)@sina.com.cn$'
    regex_3 = '^(\w+)@163.com$'
    regex_4 = '^(\w+)@126.com$'
    regex_5 = '^[1-9][0,9]{4,}+@qq.com$'
    regex = [regex_1 ,regex_2 ,regex_3, regex_4, regex_5]
    for i in  regex:
        result = re.findall(i,email)
        if result:
            print("匹配成功")
            return True
        else:
            print("匹配失败")
            return False
email = 'sdjflsdjkl@sina.com'
checkEmail(email)
```



## 正则表达式测试工具



打开开源中国提供的正则表达式测试工具 http://tool.oschina.net/regex/，输入待匹配的文本，然后选择常用的正则表达式，就可以得出相应的匹配结果了。

例如，输入下面这段待匹配的文本：



```
Hello, my phone number is 123455678 and email is runsen@qq.com, and my website is https://blog.csdn.net/weixin_44510615.
```

这段字符串中包含了一个电话号码和一个电子邮件，接下来就尝试用正则表达式提取出来，如图所示。

![](https://img-blog.csdnimg.cn/20200529155805263.png)

在网页右侧选择 “匹配 Email 地址”，就可以看到下方出现了文本中的 E-mail。如果选择 “匹配网址 URL”，就可以看到下方出现了文本中的 URL。是不是非常神奇？


![](https://img-blog.csdnimg.cn/20200529155827219.png)

![](https://img-blog.csdnimg.cn/20200529155916486.png)





# 59、Python中的网络通信Socket


﻿@Author：Runsen







今天，我要写的是Python中的网络通信Socket，写之前，先去[菜鸟教程](https://www.runoob.com/python/python-socket.html)看看，偷窥学习一下Socket通讯的基本方式。





## TCP

我是化工专业的，TCP/IP这些怎么能不知道？在了解Socket前，我先给装个逼，介绍下TCP/IP。


计算机与网络设备两情侣要谈恋爱，相互通信，那么双方就必须有规则。基于相同的方法，不同的硬件、操作系统之间的通信，都需要一种规则。而我们就把这种规则称为协议(protocol)。


TCP/IP 是互联网相关各类协议族的总称。TCP/IP是指TCP和IP这两种协议。TCP/IP是在IP协议的通信过程中，使用到的协议族的统称。



## 七层


TCP/IP协议族按层次分别为 应用层，传输层，网络层，数据链路层，物理层。可以按照不同的模型分4层或者是7层。

将TCP/IP分为5层，越靠下越接近硬件。

应用层，应用程序收到传输层的数据后，接下来就是要进行解读，解读必须要先规定好格式，而应用层就是规定应用程序的数据格式，主要协议有HTTP等。

传输层，该层为两台主机上的应用程序提供端到端的通信，传输层有两个传输协议为TCP（传输控制协议）和UDP（用户数据报协议），TCP是一个可靠的面向连接的协议，UDP是不可靠或者说无连接的协议。

网络层，决定如何将数据从发送方到接收方，是建立主机到主机的通信。

数据链路层，控制网络层与物理层之间的通信，主要功能是保证物理线路上进行可靠的数据传递。

物理层，该层负责物理传输，与链路有关，也与传输的介质有关。



![](https://img-blog.csdnimg.cn/2020052916170248.png)



![](https://img-blog.csdnimg.cn/20200529161811896.png)




![](https://img-blog.csdnimg.cn/20200529161821652.png)

别看我很牛逼，其实都是抄百度百科的，图片都是网络的，出自《图解HTTP》书籍的


## 三次握手，四次挥手

TCP三次握手，四次挥手，Runsen也不会怎么说，就把网上最通俗的图放在下面 了，还是别看我很牛逼，牛逼的是做图的大佬。



![](https://img-blog.csdnimg.cn/20200529162029248.png)
三次握手示意图：



![](https://img-blog.csdnimg.cn/2020052916222474.png)

三次握手过程：


第一次握手是在建立连接，客户端发送连接请求报文段，把标有SYN的数据包发给服务器端即为接收端。

第二次握手是服务器端即接收端收到客户端的SYN的报文段，同时发送标有SYN/ACK的数据包。

第三次握手是客户端收到服务器端的SYN/ACK的数据包后，向服务器端发送标有ACK的数据包。




四次握手其实就是把第二步变成了两步，所以就成了[四次握手」。




![](https://img-blog.csdnimg.cn/20200529162851493.png)


## Socket

我是来偷窥Python中的网络通信Socket，不小心偷窥到了一个非常不错的Socket好图



![](https://img-blog.csdnimg.cn/20200529161222362.png)

## 实现简单的通讯程序

服务端，server.py


```python
#导入socket模块
import socket
#创建套接字 或使用server = socket.socket()
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
#定义绑定的ip和端口，用元组定义
ip_port = ('127.0.0.1', 8888)
#绑定监听:bind(address),在AF_INET下,以元组（ip,port）的形式表示地址
server.bind(ip_port)
#设置最大连接数，默认为1
server.listen(5)
#不断接受连接：one by one
while True:
    print("等待数据连接中……")
    #接受客服端数据请求
    conn, address = server.accept()
    '''
    向客服端返回信息
    (注意：python3.x以上，网络数据的发送接收都是byte类型，
    发送接收String类型数据时需要对数据进行编码(发送：messages.enconde()；接收后转为String类型:messages.deconde())，pyhon2.x则直接发送数据无须编码)
    '''
    messages = "连接成功！"
    conn.send(messages.encode())
    #计数信息条数
    count = 0
    #一个连接中，不断的接受客户端发来的数据
    while True:
        data = conn.recv(1024)
        #打印客户端发来的数据信息
        print(data.decode())
        #判断是否退出当前连接,等在下一个连接
        if data == b'exit':
          break
        #处理客户端数据（如：响应请求等）
        count = count + 1
        string = "第" + str(count) + "条信息：" + data.decode()
        conn.send(string.encode())
        #主动关闭连接
    conn.close()
```


客户端，client.py



```python
import socket

#创建套接字
client = socket.socket()
#访问的服务器的ip和端口，用元组定义
ip_port = ("127.0.0.1", 8888)
#连接服务器主机
client.connect(ip_port)
#同一链接中，不断向服务器发生数据或请求
while True:
    #接收服务器发送或响应的数据
    data = client.recv(1024)
    #打印接收的数据；python3.x以上数据要编码(发送：data.enconde()；接收后转为String类型:data.deconde())
    print(data.decode())
    messages = input("请输入发生或请求的数据(exit退出)：")
    client.send(messages.encode())
    if messages == 'exit':
        break
    '''
    #接收服务器发送或响应的数据
    data = client.recv(1024)
    #打印接收的数据；python3.x以上数据要编码，发送enconde()；接收deconde()
    print(data.decode())
    '''
#关闭连接
client.close()
```

![](https://img-blog.csdnimg.cn/20200529173904180.png)

## 多线程通信

TCP服务器与多个TCP客户端同时进行连续通信，只需要通过threading创建多线程任务handle_client就可以了。




```python
import socket
import threading
import random


def handle_client():
    # 接受客户端请求链接
    client, address = server.accept()
    print("[*] Accept connection from: %s:%d" % (address[0], address[1]))
    messages = "Hello World!"
    client.send(messages.encode())
    # 连续与当前连接的客户端通信
    while True:
        # 接受客户端数据
        request = (client.recv(1024)).decode()
        # 判断是否结束通信
        if request == 'exit':
            break
        print("[*] Received from %s:%d : %s" % (address[0], address[1], request))
        # 发送响应信息给客户端
        client.send((str(random.randint(1, 1000)) + "：" + "ACK!").encode())
    # 关闭当前连接
    client.close()


if __name__ == "__main__":
    # 创建套接字
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 定义绑定ip和端口
    ip = '127.0.0.1'
    port = 8888
    # 绑定监听
    server.bind((ip, port))
    # 设置最大连接数，默认为1
    server.listen(5)
    print("[*] Listening on %s:%d" % (ip, port))
    # 循环开启线程，接受多个客户端的链接通信
    while True:
        # 创建一个线程
        client_handler = threading.Thread(target=handle_client)
        # 开启线程
        client_handler.start()

```

![](https://img-blog.csdnimg.cn/20200529175334353.png)


python3.x以上，网络数据messages的发送接收都是byte类型，若要发送接收String类型数据时需要通过messages.enconde()对数据进行编码，接收后通过messages.deconde()转为String类型。pyhon2.x则直接发送数据无须编码。

代码来自：https://www.imooc.com/learn/1031





# 60、网络通信Socket模块实现文件传输
﻿@Author：Runsen


我预计写零基础学Python写到一百篇，这是第六十篇，还剩四十篇


实现的效果如下的Gif所示，就是网络通信Socket模块实现文件传输。

![](https://img-blog.csdnimg.cn/20200530234705789.gif)


## 服务端


首先需要获取本机ip，这里服务端采用多线程的方法，就是定义一个函数，然后用threading创建任务。客户端连接成功，接收客户端的请求信息，就是下载的文件名。所以需要判断，有输出文件字节数。然后在问用户是不是要下载，得到信息就使用 while True: 读文件的内容，再一个send。就是这么简单，看代码是不是就是这么回事。



```python
import socket
import os
import threading

# 获取本机ip
def get_host_ip():
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        s.connect(('8.8.8.8', 80))
        ip = s.getsockname()[0]
    finally:
        s.close()

    return ip

# 处理客户端请求下载文件的操作（从主线程提出来的代码）
def deal_client_request(ip_port, service_client_socket):
    # 连接成功后，输出“客户端连接成功”和客户端的ip和端口
    print("客户端连接成功", ip_port)
    # 接收客户端的请求信息【recv】
    file_name = service_client_socket.recv(1024)
    # 解码
    file_name_data = file_name.decode("utf-8")
    # 判断文件是否存在
    if os.path.exists(file_name_data):
        #输出文件字节数
        fsize = os.path.getsize(file_name_data)
        #转化为兆单位
        fmb = fsize/float(1024*1024)
        #要传输的文件信息
        senddata = "文件名：%s  文件大小：%.2fMB"%(file_name_data,fmb)
        #发送和打印文件信息【send】
        service_client_socket.send(senddata.encode("utf-8"))
        print("请求文件名：%s  文件大小：%.2f MB"%(file_name_data,fmb))
        #接受客户是否需要下载【recv】
        options = service_client_socket.recv(1024)
        if options.decode("utf-8") == "y":
            # 打开文件
            with open(file_name_data, "rb") as f:
                #　计算总数据包数目
                nums = fsize/1024
                #　当前传输的数据包数目
                cnum = 0

                while True:
                    file_data = f.read(1024)
                    cnum = cnum + 1
                    #progress = cnum/nums*100

                    #print("当前已下载：%.2f%%"%progress,end = "\r")
                    if file_data:
                        # 只要读取到数据，就向客户端进行发送【send】
                        service_client_socket.send(file_data)
                    # 数据读完，退出循环
                    else:
                        print("请求的文件数据发送完成")
                        break
        else:
            print("下载取消！")
    else:
        print("下载的文件不存在！")
    # 关闭服务当前客户端的套接字【close】
    service_client_socket.close()


if __name__ == '__main__':
    # 获取本机ip
    print("TCP文件传输服务器，本机IP:" + get_host_ip())
    
    # 把工作目录切换到data目录下
    os.chdir("./data")
    # 创建套接字【socket】
    tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 绑定端口号【bind】
    tcp_server_socket.bind(("", 3356))
    # 设置监听，将主动套接字变为被动套接字【listen】
    tcp_server_socket.listen(128)

    # 循环调用【accept】，可以支持多个客户端同时连接，和多个客户端同时下载文件
    while True:
        service_client_socket, ip_port = tcp_server_socket.accept()
        # 连接成功后打印套接字号
        #print(id(service_client_socket))

        # 创建子线程
        sub_thread = threading.Thread(target=deal_client_request, args=(ip_port, service_client_socket))
        # 启动子线程
        sub_thread.start()
```






## 客户端

客户端更简单，连接服务端，发送下载文件的请求，定义一个写入的文件夹，就是小儿科东西。不写了，看代码。



```python
# -*- coding:utf-8 -*-
# 多任务文件下载器客户端
import socket
import os

if __name__ == '__main__':
    # 创建套接字【socket】
    tcp_client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 和服务端连接【connect】
    server_ip = input("输入服务器IP：")
    tcp_client_socket.connect((server_ip, 3356))
    # 发送下载文件的请求
    file_name = input("请输入要下载的文件名：")
    # 编码
    file_name_data = file_name.encode("utf-8")
    # 发送文件下载请求数据【send】
    tcp_client_socket.send(file_name_data)
    # 接收要下载的文件信息【recv】
    file_info = tcp_client_socket.recv(1024)
    # 文件信息解码
    info_decode = file_info.decode("utf-8")
    print(info_decode)
    #获取文件大小
    fileszie = float(info_decode.split('：')[2].split('MB')[0])
    fileszie2 = fileszie*1024
    # 是否下载？输入ｙ　确认　输入ｑ 取消
    opts = input("是否下载？(y 确认　q 取消)")
    if opts == 'q':
        print("下载取消！程序退出")
    else:
        print("正在下载　>>>>>>")
        #向服务器确认正在下载【send】
        tcp_client_socket.send(b'y')

        recvpath = "./receive/"
        if not os.path.exists(recvpath):
            os.mkdir(recvpath) 
        
        # 把数据写入到文件里
        with open(recvpath + file_name, "wb") as file:
            #目前接收到的数据包数目
            cnum = 0

            while True:
                # 循环接收文件数据【recv】
                file_data = tcp_client_socket.recv(1024)
                # 接收到数据
                if file_data:
                    # 写入数据
                    file.write(file_data)
                    cnum = cnum+1
                    #progress =cnum/fileszie2*100
                    #print("当前已下载：%.2f%%"%progress,end = "\r")
                # 接收完成
                else:
                    print("下载结束！")
                    break
    # 关闭套接字【close】
    tcp_client_socket.close()
```
# 61、Python中的smtplib和email实现邮件发送


﻿![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9mOGM0YjhmZC0zZGY5LTQ0NDktOGVhMi1lMWJhNjE5MGY3MTEucG5n?x-oss-process=image/format,png)




@Author ：  Runsen




在Python中分别有两个库实现发送邮件，分别是smtplib和email。


smtplib是用来发送邮件用的，email是用来构建邮件内容的。




下面是具体使用：


```python
import smtplib
 
server = smtplib.SMTP()
server.connect(host, port)


#连接（connect）指定的服务器，host是指定连接的邮箱服务器，通过搜索“xx邮箱服务器地址”，就可以找到
#例如QQ邮箱的SMTP服务器地址是：smtp.qq.com。port是端口，一般情况下SMTP默认端口号为25

server.login(username, password)
#username:登录邮箱的用户名
#password：授权码
server.sendmail(sender, to_addr, msg.as_string())

#from_addr：邮件发送地址，就是上面的username
#to_addr：邮件收件人地址
#msg.as_string()：为一个字符串类型 ，as_string()是将发送的信息msg变为字符串类型。
server.quit()
#退出服务器，结束SMTP会话
```

备注：SMTP 协议是由源服务器到目的地服务器传送邮件的一组规则。



email 模块：也就是用来写邮件内容的模块。这个内容可以是纯文本、HTML内容、图片、附件等多种形式。



```python
import email
from email.mime.text import MIMEText
#纯文本或HTML页面
from email.mime.image import MIMEImage
#内容形式为图片
from email.mime.multipart import MIMEMultipart
#多形式组合，可包含文本和附件
 
#MIMEText方法：
# MIMEText(msg,type,chartset)
# msg：文本内容，可自定义
# type：文本类型，默认为plain（纯文本）
# chartset：文本编码，中文为“utf-8”
```



## 测试Demo


这是我把自己的username和password省略了

```python
# 测试
import smtplib
from email.mime.textimport MIMEText
 
username='你的@qq.com'
password='XXXXXXXXX'
sender='发给谁@qq.com'
to_addr='run24118cajie@163.com'
msg=MIMEText('你好这是用python发的一封邮件','plain','utf-8')
 
server =smtplib.SMTP()
server.connect('smtp.qq.com', 25)
server.login(username,password)
server.sendmail(sender,to_addr, msg.as_string())
server.quit()
```

发送成功


![](https://img-blog.csdnimg.cn/20190505234114734.png)

## 标准发邮件的格式


```python
# 首先，主送、抄送就是两个用逗号分割的字符串，subject是标题，正文是context，支持html。
from email import encoders
from email.header import Header
from email.mime.text import MIMEText
from email.mime.base import MIMEBase
from email.mime.multipart import MIMEMultipart
import smtplib
import os

from_addr = 'xxxxx@qq.com'
password = 'xxxxx'
smtp_server = 'smtp.qq.com'
def sendmail(to_addr, cc_addr, subject, content, attach_full_path):
    # create a message
    msg = MIMEMultipart()
    msg['From'] = from_addr
    msg['To'] = to_addr
    msg['Cc'] = cc_addr
    msg['Subject'] = Header(subject, 'utf-8').encode()
    # 正文:
    msg.attach(MIMEText(content, 'html', 'utf-8'))
    # 附件
    (filepath, file) = os.path.split(attach_full_path)
    with open(attach_full_path + '', 'rb') as f:
        # 设置附件的MIME和文件名:
        mime = MIMEBase('application', 'octet-stream', filename=file)
        # 加上必要的头信息:
        mime.add_header('Content-Disposition', 'attachment', filename=file)
        # 把附件的内容读进来:
        mime.set_payload(f.read())
        # 用Base64编码:
        encoders.encode_base64(mime)
        # 添加到MIMEMultipart:
        msg.attach(mime)
    # 发送邮件
    server = smtplib.SMTP(smtp_server, 25)
    server.set_debuglevel(1)
    server.starttls()
    server.login(from_addr, password)
    server.sendmail(from_addr, to_addr.split(',') + cc_addr.split(','), msg.as_string())
    server.quit()
  
```

# 62、多线程真的比单线程快？那是因为你不知道Python中的全局解释器锁GIL


@Author：Runsen










今日，我决定继续更新Python教程，介绍的是Python 中的全局解释器锁GIL。已经到了六十二，还剩下区区三十八篇。长得帅就是我的动力，不对，明明就是太穷了才是我的动力。



## 多线程比单线程快？


在Python中，可以通过多进程、多线程和多协程来实现多任务。这个不清楚，看看我之前的文章，难道多线程比单线程快？


你竟然敢质疑我，我太开心了。我得用一个例子证明我自己得观点。

```python
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/6/4
'''

import threading, time
def my_counter():
    i = 0
    for _ in range(100000000):
        i = i+1
    return True

def main1():
    thread_ary = {}
    start_time = time.time()
    for tid in range(2):
        t = threading.Thread(target=my_counter)
        t.start()
        t.join()  # 第一次循环的时候join方法引起主线程阻塞，但第二个线程并没有启动，所以两个线程是顺序执行的

    print("单线程顺序执行total_time: {}".format(time.time() - start_time))

def main2():
    thread_ary = {}
    start_time = time.time()
    for tid in range(2):
        t = threading.Thread(target=my_counter)
        t.start()
        thread_ary[tid] = t

    for i in range(2):
        thread_ary[i].join()  # 两个线程均已启动，所以两个线程是并发的

    print("多线程执行total_time: {}".format(time.time() - start_time))

if __name__ == "__main__":
    main1()
    main2()
```

运行结果

```
单线程顺序执行total_time: 17.754502773284912
多线程执行total_time: 20.01178550720215
```

我怕你说我乱得出来得结果，我还是截个图看清楚点


![](https://img-blog.csdnimg.cn/20200604114813483.png)

没错， Python 的线程失效了，没有起到并行计算的作用。



Python 的线程，的确封装了底层的操作系统线程，在 Linux 系统里是 Pthread（全称为 POSIX Thread），而在 Windows 系统里是 Windows Thread。另外，Python 的线程，也完全受操作系统管理，比如协调何时执行、管理内存资源、管理中断等等。所以，虽然 Python 的线程和 C++ 的线程本质上是不同的



## GIL并不是Python的特性

GIL 的概念用简单的一句话来解释，就是**「任一时刻，无论线程多少，单一 CPython 解释器只能执行一条字节码」**。这个定义需要注意的点：

首先需要明确的一点是**GIL并不是Python的特性**，它是在实现Python解析器(CPython)时所引入的一个概念。


C++是一套语言（语法）标准，但是可以用不同的编译器来编译成可执行代码。有名的编译器例如GCC，INTEL C++，Visual C++等。

Python也一样，同样一段代码可以通过CPython，PyPy，Psyco等不同的Python执行环境来执行。


**其他 Python 解释器不一定有 GIL**。例如 Jython (JVM) 和 IronPython (CLR) 没有 GIL，而 CPython，PyPy 有 GIL；


因为CPython是大部分环境下默认的Python执行环境。所以在很多人的概念里CPython就是Python，也就想当然的把GIL归结为Python语言的缺陷。所以这里要先明确一点：**GIL并不是Python的特性，Python完全可以不依赖于GIL**






## GIL本质就是一把互斥锁

GIL本质就是一把互斥锁，既然是互斥锁，所有互斥锁的本质都一样，都是将并发运行变成串行，以此来控制同一时间内共享数据只能被一个任务所修改，进而保证数据安全。

可以肯定的一点是：保护不同的数据的安全，就应该加不同的锁。





 GIL 是工作原理：下面这张图，就是一个 GIL 在 Python 程序的工作示例。其中，Thread 1、2、3 轮流执行，每一个线程在开始执行时，都会锁住 GIL，以阻止别的线程执行；同样的，每一个线程执行完一段后，会释放 GIL，以允许别的线程开始利用资源。

![](https://img-blog.csdnimg.cn/20200604115658938.png)


细心的你可能会发现一个问题：为什么 Python 线程会去主动释放 GIL 呢？毕竟，如果仅仅是要求 Python 

CPython 使用引用计数来管理内存，所有 Python 脚本中创建的实例，都会有一个引用计数，来记录有多少个指针指向它。当引用计数只有 0 时，则会自动释放内存。

```
import sys
a = []
b = a
print(sys.getrefcount(a))
>>> 3
```


这个例子中，a 的引用计数是 3，因为有 a、b 和作为参数传递的 getrefcount 这三个地方，都引用了一个空列表。这样一来，如果有两个 Python 线程同时引用了 a，就会造成引用计数的 race condition，引用计数可能最终只增加 1，这样就会造成内存被污染。因为第一个线程结束时，会把引用计数减少 1，这时可能达到条件释放内存，当第二个线程再试图访问 a 时，就找不到有效的内存了。


## 计算密集型


我们先来看一个简单的计算密集型示例：

```python
import time
COUNT = 50_000_000

def count_down():
   global COUNT
   while COUNT > 0:
       COUNT -= 1

s = time.perf_counter()
count_down()
c = time.perf_counter() - s
print('time taken in seconds - >:', c)

# time taken in seconds - >: 9.2957003

```


这个是单线程， 时间是9s， 下面我们用两个线程看看结果又如何：

```python
import time
from threading import Thread

COUNT = 50_000_000

def count_down():
   global COUNT
   while COUNT > 0:
       COUNT -= 1

s = time.perf_counter()
t1 = Thread(target=count_down)
t2 = Thread(target=count_down)
t1.start()
t2.start()
t1.join()
t2.join()
c = time.perf_counter() - s
print('time taken in seconds - >:', c)

# time taken in seconds - >: 17.110625

```

其实结果一点也不奇怪， 我们程序主要的操作就是在计算， cpu没有等待， 而改为多线程后， 增加了线程后， 在线程之间频繁的切换，增大了时间开销， 时间当然会增加了。




**对于io密集型工作（爬虫），多线程可以大幅提高代码效率。对CPU计算密集型（数据分析），多线程的效率可能比单线程还略低。**

# 63、面试最常见的问题：Python的垃圾回收机制到底是怎么样的？

@Author：Runsen










今日，我决定继续更新Python教程，介绍的是Python的垃圾回收机制。已经到了六十三，还剩下区区三十七篇。长得帅就是我的动力，不对，明明就是太穷了才是我的动力。
![](https://img-blog.csdnimg.cn/2020060418232457.png)





参考：[极客时间Python专栏](https://time.geekbang.org/column/article/104265)


在这篇文章，带着这个问题来一直往下看：怎么知道一个对象，是否永远都不能被调用了呢？



## 引用计数

在一些代码中，如果存在一些变量但是没有用，会造成内存空间，因此叫做垃圾，所以要回收。

引用计数也是一种最直观，最简单的垃圾收集技术。原理非常简单，每一个对象都包含了两个头部信息，一个是类型标志符，标识这个对象的类型；另一个是计数器，记录当前指向该对象的引用数目，表示这个对象被多少个变量名所引用。



用来记录对象被引用的次数，每当对象被创建或者被引用时将该对象的引用次数加一，当对象的引用被销毁时该对象的引用次数减一，当对象的引用次数减到零时说明程序中已经没有任何对象持有该对象的引用，换言之就是在以后的程序运行中不会再次使用到该对象了，那么其所占用的空间也就可以被释放了了。


下面是查看引用计数的方法，

```python
print(sys.getrefcount())
```

注意调用getrefcount()函数会临时增加一次引用计数，得到的结果比预期的多一次。

我们通过一些例子来看下，可以使python对象的引用计数增加或减少的场景，代码来自专栏。



```python
import sys
a = []
# 两次引用，一次来自 a，一次来自 getrefcount
print(sys.getrefcount(a))
def func(a):
    # 四次引用，a，python 的函数调用栈，函数参数，和 getrefcount
    print(sys.getrefcount(a))

func(a)
# 两次引用，一次来自 a，一次来自 getrefcount，函数 func 调用已经不存在
print(sys.getrefcount(a))

########## 输出 ##########
2
4
2
```

我认为这个代码是这篇文章最容易看懂的代码

## 内存空间

我们来看看下面的例子。代码来自专栏





```python
import os
import psutil


# 显示当前 python 程序占用的内存大小
def show_memory_info(hint):
    pid = os.getpid()
    p = psutil.Process(pid)

    info = p.memory_full_info()
    memory = info.uss / 1024. / 1024
    print('{} memory used: {} MB'.format(hint, memory))


def func():
    show_memory_info('initial')
    a = [i for i in range(10000000)]
    show_memory_info('after a created')

func()
show_memory_info('finished')

########## 输出 ##########

initial memory used: 20.82421875 MB
after a created memory used: 408.125 MB
finished memory used: 21.10546875 MB
```


如果代码运行遇到psutil.AccessDenied: psutil.AccessDenied (pid=14204)，解决的方法就是用管理员身份打开。


函数 show_memory_info用来获取程序占用的内存空间大小，在 func函数中创建一个包含一百万个整数的列表。从打印结果我们可以看出，创建完列表之后程序耗用的内存空间上升到了 408.125  MB。而当函数 foo 调用完毕之后内存消耗又恢复正常。

这是因为我们在函数 func中创建的 list 变量是局部变量，其作用域是当前函数内部，一旦函数执行完毕，局部变量的引用会被自动销毁，即其引用次数会变为零，所占用的内存空间也会被回收。（代码来自专栏，但是领悟来自于Runsen）


```python
def func():
    show_memory_info('initial')
    a = [i for i in derange(10000000)]
    show_memory_info('after a created')
    return a

a = func()
show_memory_info('finished')

########## 输出 ##########
initial memory used: 20.8515625 MB
after a created memory used: 408.1484375 MB
finished memory used: 408.1484375 MB
```


稍加改造之后，即使 func函数调用结束其所消耗的内存也未被释放。

主要是因为我们将函数 func内部产生的列表返回并在主程序中接收之后，这样就会导致该列表的引用依然存在，该对象后续仍有可能被使用到，垃圾回收便不会回收该对象。



## 计数增加和减少

下面引用计数增加的场景：

- 对象被创建并赋值给某个变量，比如：a = 'ABC'
- 变量间的相互引用（相当于变量指向了同一个对象），比如：b=a
- 变量作为参数传到函数中。比如：ref_method(a)，
- 将对象放到某个容器对象中(列表、元组、字典)。比如：c = [1, a, 'abc']

引用计数减少的场景：

- 当一个变量离开了作用域，比如：函数执行完成时，执行方法前后的引用计数保持不变，这就是因为方法执行完后，对象的引用计数也会减少，如果在方法内打印，则能看到引用计数增加的效果。
- 对象的引用变量被销毁时，比如del a 或者 del b。注意如果del a，再去获取a的引用计数会直接报错。
- 对象被从容器对象中移除，比如：c.remove(a)
- 直接将整个容器销毁，比如：del c
- - 对象的引用被赋值给其他对象，相当于变量不指向之前的对象，而是指向了一个新的对象，这种情况，引用计数肯定会发生改变。(排除两个对象默认引用计一致的场景)。


```python
import sys

def ref_method(str):
    print(sys.getrefcount(str))
    print("我调用了{}".format(str))
    print('方法执行完了')

def ref_count():
    # 引用计数增加的场景
    print('测试引用计数增加')
    a = 'ABC'
    print(sys.getrefcount(a))
    b = a
    print(sys.getrefcount(a))
    ref_method(a)
    print(sys.getrefcount(a))
    c = [1, a, 'abc']
    print(sys.getrefcount(a))

    # 引用计数减少的场景
    print('测试引用计数减少')
    del b
    print(sys.getrefcount(a))
    c.remove(a)
    print(sys.getrefcount(a))
    del c
    print(sys.getrefcount(a))
    a = 783
    print(sys.getrefcount(a))

if __name__ == '__main__':
    ref_count()

测试引用计数增加
7
8
10
我调用了ABC
方法执行完了
8
9
测试引用计数减少
8
7
7
4
```




## 释放内存



python给我们提供了手动释放内存的方法 gc.collect()



```python
import gc
import os
import psutil
# 显示当前 python 程序占用的内存大小
def show_memory_info(hint):
    pid = os.getpid()
    p = psutil.Process(pid)

    info = p.memory_full_info()
    memory = info.uss / 1024. / 1024
    print('{} memory used: {} MB'.format(hint, memory))



def func():
    show_memory_info('initial')
    a = [i for i in range(10000000)]
    b = [i for i in range(10000000)]
    show_memory_info('after a, b created')
    a.append(b)
    b.append(a)

func()
gc.collect()
show_memory_info('finished')

########## 输出 ##########
initial memory used: 26.16796875 MB
after a, b created memory used: 802.03515625 MB
finished memory used: 27.5 MB
```

# 64、开始刷Leetcode之旅（Python版本）





﻿@Author：Runsen





从大一写Python文章，到现在其都有上百篇，现在到了六十四，我觉得这个时候应该去刷题了，其实很多学Python的都不是专科的，都是给培训机构宣传牛逼，其实在编程语言中，Python是最简单，最没有难度的编程语言。我在之后的文章都更新数据结构和Leetcode。都用Python解决的方法。其实Leetcode上的一部分题我都基本刷过，那么我就开始吧。






## 注册Leetcode账号


目前Leetcod有国际和中文的两个版本，下图就是我的中文版本，刷的不够，其实我也挺菜的。这个是中文的网址：https://leetcode-cn.com/problemset/all/
![](https://img-blog.csdnimg.cn/20200605154056199.png)

下图就是我的国际版本，其实我主要在国际版混日子，刷了100多题，其实我很菜的。这是它的官网，https://leetcode.com。
![](https://img-blog.csdnimg.cn/20200605154019683.png)


不同点，非中国区的人多点，做完了也可以参考下老外是用什么思路做的，挺好的。所以你比要到非中国区，看看老外是怎么干的。



## Pycharm装Leetcode插件


直接打开Pycharm，依次点击File-Settings-Plugins-Maketplace ，然后在搜索框输入leetcode，就会显示我们的leetcode editor插件,点击Install，跳出的界面点检accept,之后等待安装好就行了


我这个是安装好的了。
![](https://img-blog.csdnimg.cn/20200605155930517.png)

如果你用vscode也是一样，给我装vscode插件。

![](https://img-blog.csdnimg.cn/20200605160057766.png)

因为，我习惯Python用Pycharm，Java用IDEA，前端用vscode。所以这Runsen使用Pycharm。



然后就是登陆我的Leetcode账号。

![](https://img-blog.csdnimg.cn/20200605160401821.png)

然后就是登录你的账号。

![](https://img-blog.csdnimg.cn/20200605160506779.png)



点击右下角，选择刷新或者加载按钮，就可以获取到leetcode中题库了，根据颜色可以区分题目的难易程度:
绿色-中等；
黄色-简单;
红色-困难


![](https://img-blog.csdnimg.cn/20200605160638614.png)

更详细的使用说明参考文档:https://github.com/shuzijun/leetcode-editor


## 怎么刷Leetcode

### 以前菜鸡的我做法

以前Runsen的做法：

1. 打开leetcode
2. 启动Pycharm
3. 开始思考，冷静分析
4. 打开leetcode官网的评论区答案，寻找跟我一样的菜逼
5. 满意离开评论区


上面其实都是像之前的我，都是菜鸡，其实现在我还是菜鸡。

### 分类归纳/总结

刷Leetcode，必须分类归纳/总结

（1）、数组和相关题型

对于算法题，还是有很多种题型需要去总结的，如果你懂这个题型，以后遇到类似的题，相信很快就能做出来的。有哪些题型可以总结呢？答是非常多，例如：

（1）、给你一个非负数的数组，求最大子数组和的长度

这算是一个题型，关于这个题型，有很多种变形、拓展，这里建议一起归纳总结，例如：

（2）、刚才给的数组是非负数的，现在变一下，给的数组是可正可负。

还能继续拓展吗？答是可以的，例如：

（3）、给你个矩阵（即二维数组），求最大子矩阵和的面积

还有吗？有，例如刚才是求最大和，现在我改成求最大乘积。

我其实是想告诉你，对于前期的学习，我建议分类刷题，总结题型，像我上面举的这些例子，遇到相似的，就直接可以秒杀了，因为这类题，没啥边界或者规律。


关于题型的，还是很多的，我这里无法一一给你列举，只能靠你刷题的过程中，进行分类、总结。不过我可以给你推荐一些资料，后面推荐。下面我在说一些题型吧。


### 三分学七分练

三分学七分练，这是我从极客时间的覃超，前Facebook工程师，传授的方法。


![](https://img-blog.csdnimg.cn/20200605161852501.png)



俗话说：学钢琴，三分学，七分练。其中练习是最为重要的一个环节，想学好钢琴必须得时常练习且多多益善。



所以刷Leetcode的最大的弊端都是：缺乏练习。



## 两数相加

那么我们就开始干他，Leetcode中的Hello World就是两数相加。


这个题是我2018年遇见了，现在2020年半，两年多时间。


```python
#给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。 
#
# 你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。 
#
# 示例: 
#
# 给定 nums = [2, 7, 11, 15], target = 9
#
#因为 nums[0] + nums[1] = 2 + 7 = 9
#所以返回 [0, 1]
# 
# Related Topics 数组 哈希表

```


其实这一题真的很简单，无非就是将“昂贵”的时间复杂度转换成“廉价”的空间复杂度，把双重遍历，变成一次遍历。

这里最佳的方法就是使用字典。下面是我去年的代码，就是三种的解决方法。


列表解法

```
def twoSum_1( nums, target):
    result = []
    for i in range (len(nums)):
        onenum = nums[i]
        twonum = target - onenum
        if twonum in nums:
            j = nums.index(twonum)
            if i != j:
                result.append(i)
                result.append(j)
                return result
```

字典解法

```
def twoSum_2(nums,target):
    dict={}
    for i in range(len(nums)):
        m = nums[i]
        if target-m in dict:
            return [dict[target-m],i]
        dict[m] = i
```

字典推导式

```
def twosum_3(nums,target):
    l = len(nums)
    dict = {nums[i]:i for i in range(l)}
    print(dict)
    for j in range(l):
        a = nums[j]
        b = target - a
        if b in dict and j != dict[b]:
            return [j,dict[b]]
```



## 关于学习课程



在之前深入Leetcode，学了下面的课程

![](https://img-blog.csdnimg.cn/2020060516351882.png)
![](https://img-blog.csdnimg.cn/20200605163542636.png)


![](https://img-blog.csdnimg.cn/20200605163457240.png)


因此下面的文章主要是总结回顾之前学到东西，只有不断地反复学习，才有新的突破

# 65、Leetcode数组系列（上篇）






@Author：Runsen



从大一写Python文章，到现在其都有上百篇，现在到了六十五，今日主要写的是数据结构中的数组 Array 






## 数组 Array 


在平时使用最多的恐怕就是数组了吧，它是使用最广泛的一种数据结构，它是相同数据类型（可以是基本类型也可以是自定义类型）的元素按一定顺序排列的集合，它们在内存中按照这个先后顺序连续存放在一起。有一维数组，二维数组，多维数组。 通俗的理解就是我们一般把一群羊或者一群牛放在一个圈里面，这个圈就相当于数组容器，每一个羊相当于一个元素。


![](https://img-blog.csdnimg.cn/20190315151507193.jpg)

- 查询 Access: O(1) 
- 插入 Insert: 平均 O(n)
- 删除 Delete: 平均 O(n)




优点：

1. 有序 
2. 可以进行下标操作，随机访问效率很高，时间复杂度可以达到O(1)
3. 添加速度快
   缺点： 
4. 删除，删除第一个，删除最后一个，选择一个位置删除这些都不方便操作 
5. 在数组起始位置处，插入数据和删除数据效率低，时间复杂度平均 O(n)
6. 内存空间要求高，必须有足够的连续的内存空间 




这是争哥的春节天天练，那时我太菜了。 没搞。
![](https://img-blog.csdnimg.cn/20200605164322651.png)




##  三数之和

leetcode 三数之和，这是Leecode的第十五道题目。

https://leetcode-cn.com/problems/3sum/Majority 

```python
#给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有满足条件且不重复的三元组。 
#
# 注意：答案中不可以包含重复的三元组。 

# 示例： 
#
# 给定数组 nums = [-1, 0, 1, 2, -1, -4]，
#
#满足要求的三元组集合为：
#[
#  [-1, 0, 1],
#  [-1, -1, 2]
#]
#注意：答案中不可以包含重复的三元组。
```


三数之和就当两数来干，两次遍历，判断第三个数在不在，就是时间复杂度$O(n^2)$。

```python
def threeSum(nums):
    result = []
    nums.sort()
    a = len(nums)
    for i in range(a - 1):
        for j in range(i + 1, a):
            if -(nums[i] + nums[j]) in nums[j + 1:]:
                array = [nums[i], nums[j], -(nums[i] + nums[j])]
                if array not in result:
                    result.append(array)
    return result
nums = [-1, 0, 1, 2, -1, -4]
print(threeSum([-1, 0, 1, 2, -1, -4]))
```

但是会超出时间，其实三数之和用的不是这样子的，做法是双指针。

![](https://img-blog.csdnimg.cn/20200605170142310.png)



我们可以先把这个数组进行从小到大的排序，因为排序的复杂度$O(NlogN) $是远远小于$n^2$的，排序后，你会发现，由于三数之和是等于零，那么如果当前这个元素是大于零的话，而且，这个数组是按照从小到大排序的话，那么当前这个元素作为起点的集合是为空的，因为后面的元素都是比这个元素大的元素，是不可相加等于零。

由此我们可以节省一些复杂度，当然，我们进行排序的时候，是要经历一些复杂度的，但这远远小于n的平方，所以我们这个做法还是比较快的。

然后我们在确定起点之后，通过双指针去遍历其他两个元素。

看不懂看下面的图片
![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWMubGVldGNvZGUtY24uY29tL2UzZmE1OWNiZjNhYzEyMDBhMjZhNDM1ZDAwZTg3MmY3OGVjOTQwYWZkNGVlMTk3N2IwNGMxZjRkY2E0NWMxNGUtMi5naWY)


```python
def threeSum(nums):
    nums.sort()
    # [-4, -1, -1, 0, 1, 2]
    res_list = []
    # 头部循环查找
    for i in range(len(nums)):
        if i == 0 or nums[i] > nums[i - 1]:
            # 最左端
            l = i + 1
            # 最右端
            r = len(nums) - 1
            while l < r:  # 正在查找
                three_sum = nums[i] + nums[l] + nums[r]
                if three_sum == 0:
                    res_list.append([nums[i], nums[l], nums[r]])
                    l += 1  # 右移一位
                    r -= 1  # 左移一位
                    while l < r and nums[l] == nums[l - 1]:
                        # 从左往右，相同数值直接跳过
                        l += 1
                    while r > l and nums[r] == nums[r + 1]:
                        # 从右往左，相同数值直接跳过
                        r -= 1
                elif three_sum > 0:
                    # 大于零，右边数值大，左移
                    r -= 1
                else:
                    # 小于零，左边数值小，右移
                    l += 1
    return res_list
```



![](https://img-blog.csdnimg.cn/20200605171410159.png)


## 求众数

题目来源于 LeetCode 上第 169 号问题：求众数（求数组中超过一半的数字）。题目难度为 Easy

```python
#给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。 
#
# 你可以假设数组是非空的，并且给定的数组总是存在多数元素。 
# 示例 1: 
#
# 输入: [3,2,3]
#输出: 3 
#
# 示例 2: 
#
# 输入: [2,2,1,1,1,2,2]
#输出: 2
# 
# Related Topics 位运算 数组 分治算法
```


方法：遍历整个数组，出现次数比其他数字加起来出现次数还多的元素返回。


最简单的方法就排序，取出 ⌊ n/2 ⌋ 的元素

```python
def majorityElement(self, nums):
    nums.sort()
    return nums[int(len(nums) / 2)]
```





![](https://img-blog.csdnimg.cn/20200605172827746.png)




然后一种计数的方法，用字典来储存起来。



```python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        num = {}
        for i in nums:
            if i in num:
                num[i] += 1
            else:
                num[i] = 1
        return max(num.items(),key = lambda x:x[1])[0]
```




![](https://img-blog.csdnimg.cn/20200605174037717.png)

还可以直接使用collections

```python
import collections

def majorityElement(self, nums):
     return  collections.Counter(nums).most_common()[0][0]
```


![](https://img-blog.csdnimg.cn/20200605174535675.png)





## 求缺失的第一个正数

题目来源于 LeetCode 上第 41 号问题：求缺失的第一个正数



中文版：https://leetcode-cn.com/problems/first-missing-positive/


```python
#给你一个未排序的整数数组，请你找出其中没有出现的最小的正整数。 
# 示例 1: 
#
# 输入: [1,2,0]
#输出: 3
#
# 示例 2: 
#
# 输入: [3,4,-1,1]
#输出: 2
# 
# 示例 3: 
#
# 输入: [7,8,9,11,12]
#输出: 1
# 提示： 
#
# 你的算法的时间复杂度应为O(n)，并且只能使用常数级别的额外空间。 
# Related Topics 数组

```


这道题的难度在于时间和空间的限制。

若没有时间的限制，可以直接排序后遍历查找。

若没有空间的限制，可以创建辅助空间后记录。

最简单的做法就是出现就+1。

题目的要求是找到没有出现过的最小正整数，最小的正整数是1，如果1没出现过，那么答案就是1，否则，自增1，继续看2是否在列表中。

```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        res = 1
        while res in nums:
            res += 1
        return res


```

![](https://img-blog.csdnimg.cn/20200605181200362.png)



把数组里 所有>=1的元素 放在它该放的位置！
哪里是该放的位置? ：放在值减一的位置
例如，数组［4 1 5 -1 2］。
4应该放在下标为3(4-1)的位置，交换后
［-1 1 5 4 2］
1应该放在下标为0(1-0)的位置，交换后
［1 -1 5 4 2］
以此类推
［1 -1 2 4 5］
［1 2 -1 4 5］
最后遍历，第三个位置(下标为2) 本来应放3，但此时是-1，所以返回3，答案就是3。

```python
 class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        n=len(nums)
        res_list=[-1] * n
        # print(res_list)
        for i in range(n):
        	#  要判断这个数是否可以被交换
            if nums[i] >=1 and nums[i]<=n:
                res_list[nums[i]-1] =nums[i]
        # print(res_list)
        for i in range(n):
            if res_list[i] != i+1:
                return i+1
        return n+1

```


![](https://img-blog.csdnimg.cn/20200605183017232.png)


# 66、Leetcode数组系列（中篇）



﻿@Author：Runsen




今日，我决定继续更新Python教程，今天就见识下刷Leetcode的快乐。


![](https://img-blog.csdnimg.cn/20200610160923281.png)




Runsen先打开Pycharm，





## 剑指 Offer 系列 面试题03.：数组中重复的数字

先来一个简单的，见面礼。题目来源于 LeetCode 上的剑指 Offer 系列 面试题03. 数组中重复的数字。

题目链接：https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/



```go
#找出数组中重复的数字。 
#在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。 
#
# 示例 1： 
#
# 输入：
#[2, 3, 1, 0, 2, 5, 3]
#输出：2 或 3 
#
# 限制： 
# 2 <= n <= 100000 
# Related Topics 数组 哈希表

```


先进行数据的排序，然后看相邻元素是否有相同的，有直接return。 不过很慢，时间O(nlogn)了，空间O(1)，但是代码很简单。

```python
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/6/10
'''
def findRepeatNumber(nums):
    nums.sort()
    for i in range(len(nums) -1):
        if nums[i]  ==  nums[i+1]:
            return nums[i]
nums = [2, 3, 1, 0, 2, 5, 3]
print(findRepeatNumber(nums))
2
```

如果用哈希表，就是字典，遍历整个数组,当这个数字没有出现过字典的时候将其加入进去,如果在哈希表中则直接返回即可。时间复杂度O(n)，空间复杂度O(n)



```python
def findRepeatNumber1(nums):
    dict = {}
    for i in nums:
        if i not  in dict:
            dict[i] = 0
        else:
            return i
nums = [2, 3, 1, 0, 2, 5, 3]
print(findRepeatNumber1(nums))
2
```


![](https://img-blog.csdnimg.cn/20200610163602581.png)



## LeetCode 第 5 题：最长回文子串

题目链接：https://leetcode-cn.com/problems/longest-palindromic-substring/




```python
#给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。 
#
# 示例 1： 
#
# 输入: "babad"
#输出: "bab"
#注意: "aba" 也是一个有效答案。
# 示例 2： 
#
# 输入: "cbbd"
#输出: "bb"

```

定义一个判读回文子串的方法
遍历字符串比较回文子串的长度

比如说字符串abacd，反过来是dcaba，它俩的最长公共子串是aba，也就是最长回文子串。

但是这个思路是错误的，比如说字符串aacxycaa，反转之后是aacyxcaa，最长公共子串是aac，但是最长回文子串应该是aa。


算法一：枚举s所有子串，满足回文的同时，满足最长
结果：$O（N^3）$，同学请你出门右转

算法二：遍历s的每个字符，（奇数）以该字符为中心，向左向右同时遍历，（偶数）以两个字符为中心，向左向右同时遍历，当不满足回文时停止，最终筛选最长回文串
结果：$O（N^2）$，嗯，还可以，那你完整写出来吧

算法三：Manacher算法，为最长回文子串而生，O（N），了解一下就放弃。

回文中心的两侧互为镜像。因此，回文可以从他的中心展开，并且只有2n-1个这样的中心(一个元素为中心的情况有n个，两个元素为中心的情况有n-1个)。

```python
# 回文的长度是奇数还是偶数的情况，如果是奇数形回文，就以当前字符为中心左右两边寻找，例如回文"bab"；如果是偶数形回文，需要两个字符，并且这两个字符是相等的，则需要以当前字符和其相邻的字符为中心向左右两边寻找，例如回文"abba"。
def longestPalindrome(s):
    res = ""
    for i in range(len(s)):
        # 奇数形回文, like "aba"
        tmp = helper(s, i, i)
        if len(tmp) > len(res):
            res = tmp
        # 偶数形回文, like "abba"
        tmp = helper(s, i, i + 1)
        if len(tmp) > len(res):
            res = tmp
    return res

def helper(s, l, r):
    # 中心扩散
    while l >= 0 and r < len(s) and s[l] == s[r]:
        l -= 1
        r += 1
    return s[l + 1:r]


if __name__ == '__main__':
    longestPalindrome('abasfggttg')
```

![](https://img-blog.csdnimg.cn/20200610172358702.png)


##  LeetCode 第 53 题：最大子序和

```python
#给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。 
#
# 示例: 
#
# 输入: [-2,1,-3,4,-1,2,1,-5,4],
#输出: 6
#解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```


定义当前子序和以及最大子序和为数组的一个元素；

遍历整数数组，比较当前子序和的值及当前遍历的值，取较大值重置赋值给当前子序和 cur_sum；

同时比较当前子序和及最大子序和的值，取较大值重置赋值给最大子序和 max_sum；

遍历结束，返回最大子序和的值 max_sum。



```python
def maxSubArray( nums):
    '''查找连续子数组的最大和
    '''
    # 比较当前子序和，最大子序和，返回最大值
    # 定义当前子序和以及最大子序和为第一个元素
    cur_sum = max_sum = nums[0]
    # 遍历整数数组
    for x in range(1, len(nums)):
        # 比较当前值和当前子序和的值，取较大值
        cur_sum = max(nums[x], cur_sum + nums[x])
        # 比较当前值和定义的最大子序和值，将最大值重置赋值给 max_sum
        max_sum = max(cur_sum, max_sum)
    return max_sum
print(maxSubArray([-2,1,-3,4,-1,2,1,-5,4]))
6
```




##  LeetCode 第88题 :合并两个有序数组


```python
#给你两个有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。 
# 初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。 
# 你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。 
# 输入:
#nums1 = [1,2,3,0,0,0], m = 3
#nums2 = [2,5,6],       n = 3
#
#输出: [1,2,2,3,5,6] 




```


合并两个列表再排序，简单。

```python
def merge(nums1, nums2):
    nums1[:] =  sorted(nums1[:m] + nums2[:n])

```


![](https://img-blog.csdnimg.cn/20200610175523332.png)


因为本身就是有序，通过 双指针法 达到$O(n + m)$的时间复杂度。


最直接的算法实现是将指针p1 置为 nums1的开头， p2为 nums2的开头，在每一步将最小值放入输出数组中。



由于 nums1 是用于输出的数组，需要将nums1中的前m个元素放在其他地方，也就需要 $O(m)$的空间复杂度。



```python
def merge(nums1,m, nums2,n):
    # Make a copy of nums1.
    nums1_copy = nums1[:m]
    nums1[:] = []

    # Two get pointers for nums1_copy and nums2.
    p1 = 0
    p2 = 0

    # Compare elements from nums1_copy and nums2
    # and add the smallest one into nums1.
    while p1 < m and p2 < n:
        if nums1_copy[p1] < nums2[p2]:
            nums1.append(nums1_copy[p1])
            p1 += 1
        else:
            nums1.append(nums2[p2])
            p2 += 1

    # if there are still elements to add
    if p1 < m:
        nums1[p1 + p2:] = nums1_copy[p1:]
    if p2 < n:
        nums1[p1 + p2:] = nums2[p2:]
    return nums1

nums1 = [1,2,3,0,0,0]
nums2 = [2,5,6]
print(merge(nums1,3,nums2,3))
[1, 2, 2, 3, 5, 6]


```









##  LeetCode 第118题 :杨辉三角



```python
#给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。 
# 在杨辉三角中，每个数是它左上方和右上方的数的和。 
#
# 示例: 
#
# 输入: 5
#输出:
#[
#     [1],
#    [1,1],
#   [1,2,1],
#  [1,3,3,1],
# [1,4,6,4,1]
#] 
# Related Topics 数组

```

第一行第二行都是1，每行第一个和最后一个都为1，假设任意一个位置的数x，索引坐标是(m,n)，则x就是该数 正上方的数 和 左上方那个数 之和。即(m-1,n),(m-1,n-1)两数和。




```python
def generate(numRows):
    if numRows == 0: return []
    triangle = [[1]]
    if numRows == 1: return triangle
    for i in range(1, numRows):
        tmp = [1]
        for j in range(1, i):
            tmp.append(triangle[i - 1][j - 1] + triangle[i - 1][j])
        tmp.append(1)
        triangle.append(tmp)
    return triangle
print(generate(5))
[[1], [1, 1], [1, 2, 1], [1, 3, 3, 1], [1, 4, 6, 4, 1]]


```



![](https://img-blog.csdnimg.cn/20200610182259721.png)


如果本文对你有帮助，大家可以点赞转发一波，有错误大家可以评论指出，感谢！

# 67、Leetcode数组系列（下篇）

@Author：Runsen







今日，我决定继续更新Python教程，今天就见识下刷Leetcode的快乐。


![](https://img-blog.csdnimg.cn/20200610160923281.png)




Runsen先打开Pycharm，开始继续嗨起来



## 剑指 Offer 系列 面试题11 - 旋转数组的最小数字

先来一个简单的，见面礼。题目来源于 LeetCode 上的面试题11：旋转数组的最小数字


题目链接：https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/



```python
#把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。 
# 示例 1： 
# 输入：[3,4,5,1,2]
#输出：1
# 示例 2： 
# 输入：[2,2,2,0,1]
#输出：0
# 注意：本题与主站 154 题相同：https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array-ii/ 
# Related Topics 二分查找
```


初看题目最直观的解法并不难，直接寻找，我们不难写出如下代码。

```python
class Solution:
    def minArray(self, numbers: List[int]) -> int:
        return min(numbers)
```


时间复杂度$O(n)$,空间复杂度$O(1)$。因此这样是不行的
![](https://img-blog.csdnimg.cn/20200613121328523.png)

考的是：二分查找。二分法的分析我们知道，数组可以分为前后两个递增数组

- 当`numbers[mid] > numbers[high]`时，说明最小值在mid的右边，缩小范围`low = mid + 1`
- 当`numbers[mid] == numbers[high]`时，我们不知道最小值的范围，但是可以肯定的是去除`numbers[high]`是没有影响的,缩小范围`high -= 1`
- 当`numbers[mid] < numbers[high]`时，我们知道最小值的不是`numbers[mid]]`就是在mid的左边，缩小范围high = mid



```python
class Solution:
    def minArray(self, numbers: List[int]) -> int:
        l, r = 0, len(numbers) - 1
        while l < r:
            mid = (l + r) // 2
            if numbers[mid] > numbers[r]:
                l = mid + 1
            elif numbers[mid] < numbers[r]:
                r = mid
            else:
                r -= 1
        return numbers[l]


```

![](https://img-blog.csdnimg.cn/20200613122819300.png)



## 面试题53 - II. 0～n-1中缺失的数字


```java
#一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。 
# 示例 1: 
# 输入: [0,1,3]
#输出: 2
# 示例 2: 
# 输入: [0,1,2,3,4,5,6,7,9]
#输出: 8 
# 限制： 
# 1 <= 数组长度 <= 10000 
# Related Topics 数组 二分查找
```

对于有序数组或者多部分有序数组的查找问题99.999999%都是用二分查找，这道题其实考察的是二分查找的两个常见拓展之一，即查找目标序列的左边界，另一个常见拓展是查找目标序列的右边界。

```java
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        i, j = 0, len(nums) - 1
        while i <= j:
            m = (i + j) // 2
            if nums[m] == m: 
            	i = m + 1
            else: 
            	j = m - 1
        return i
```


![](https://img-blog.csdnimg.cn/2020061912141170.png)






## LeetCode 第 66题：加一

 

```java
#给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。 
# 最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。 
# 你可以假设除了整数 0 之外，这个整数不会以零开头。 
# 示例 1: 
# 输入: [1,2,3]
#输出: [1,2,4]
#解释: 输入数组表示数字 123。

# 示例 2: 
# 输入: [4,3,2,1]
#输出: [4,3,2,2]
#解释: 输入数组表示数字 4321。
```




一次for循环解决问题，从数组尾部遍历，如果遇到数字不是9就+1，并返回。如果是9，则将当前数字置0，并进入下一轮循环

考虑特殊情况：9999，此时需要检查最后一次for循环的数字是不是0，即digits[0]是否为0，如果是0，则遇到了特殊情况。此时需要在数组最前面加一个数字1，然后返回即可


```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        for i in range(len(digits)-1, -1, -1):
            if digits[i] < 9:
                digits[i] += 1
                return digits
            digits[i] = 0
        return [1] + digits
```

先将数字列表数组转化为数字或者字符串，然后+1，最后将数字转化为数组，并返回

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        ##先变成一个整的数字，然后做加法，然后转换成str,再转int加到新的list中
        nums_str = ""
        for i in digits:
            nums_str =nums_str+str(i)
    
        nums_int = int(nums_str)+1
        res = []
        for i in str(nums_int):
            res.append(int(i))
        return res

		 # a = [i * 10 ** index for index, i in enumerate(digits[::-1])]
		 # num = sum(a) + 1
		 # print(num)
		 # return [int(x) for x in str(num)]

```

## 面试题53 - I. 在排序数组中查找数字的次数 I

```java
#统计一个数字在排序数组中出现的次数。 
# 示例 1: 
# 输入: nums = [5,7,7,8,8,10], target = 8
#输出: 2 
# 示例 2: 
# 输入: nums = [5,7,7,8,8,10], target = 6
#输出: 0 
# 限制： 
# 0 <= 数组长度 <= 50000 
# 注意：本题与主站 34 题相同（仅返回值不同）：https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/ 
# Related Topics 数组 二分查找

```






python：首先为了达到目的，我们看使用python最容易实现的操作

```java
 if len(nums) ==0:
    return 0
 else:
    return nums.count(target)

```


![](https://img-blog.csdnimg.cn/20200619122355415.png)
更好的(根据二分法思想)实现下所示：


```java
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # 双指针
        l = 0
        r = len(nums) - 1
        while l <= r:
            if nums[l] < target:
                l += 1
            elif nums[r] > target:
                r -= 1
            elif nums[l] == nums[r] == target:
                return r - l + 1
        return 0



```



![](https://img-blog.csdnimg.cn/20200619121957229.png)




## leetcode977：有序数组的平方

```java
#给定一个按非递减顺序排序的整数数组 A，返回每个数字的平方组成的新数组，要求也按非递减顺序排序。 
# 示例 1： 
# 输入：[-4,-1,0,3,10]
#输出：[0,1,9,16,100]
# 示例 2： 
# 输入：[-7,-3,2,3,11]
#输出：[4,9,9,49,121]
# 提示： 
# 1 <= A.length <= 10000 
# -10000 <= A[i] <= 10000 
# A 已按非递减顺序排序。 
# Related Topics 数组 双指针

```




利用python中的列表生成式生成求平方后的数组，利用python中的排序函数sorted()对求平方后的数组进行排序。

```java
return sorted([k**2 for k in A])


```

时间复杂度：利用列表生成式生成求平方后的数组，时间复杂度为$O(N)$,python中排序用的是蒂姆排序算法，时间复杂度为$O(NlogN)$，所以该算法的时间复杂为$O(NlogN)$。



空间复杂度：$O(N)$。利用列表生成式生成求平方后数组的时间复杂度为$O(N)$，蒂姆排序空间复杂度为$O(N)$,所以该算法空间复杂度为$O(N)$。



下面就是常见的双指针做法

```java
class Solution:
    def sortedSquares(self, A: List[it]) -> List[int]:
        left,right,result = 0, len(A) - 1,[]
        while left <= right:
            if abs(A[left]) > abs(A[right]):
                result.insert(0, pow(A[left],2))
                left += 1
            else:
                result.insert(0, pow(A[right],2))
                right -= 1
        return result

```



# 68、Python | Leetcode链表系列（上篇）





﻿@Author：Runsen







今日，我决定继续更新Python教程，今天就开始了六十八、Python | Leetcode链表系列（上篇）。






## 链表 Linked List

链表由许多结点(也可以叫节点或元素)组成，每一个结点有两个域，左边部份叫值域 data，用于存放用户数据；右边叫指针域 next，一般是存储着到下一个元素的指针。head结点(头节点)，head是一个特殊的结节，head结点永远指向第一个结点，tail结点(尾节点)，tail结点也是一个特殊的结点，tail结点永远指向最后一个节点，tail.next = None。



![](https://img-blog.csdnimg.cn/20200619154620950.png)

## 节点结构



![](https://img-blog.csdnimg.cn/20200619154648533.png)
上面四个节点 abcd 组成一个链表，每一个节点都包含 data 和 next，尾节点的 next 指向 None。



链表中的元素都会两个属性，一个是元素的值，另一个是指针，此指针标记了下一个元素的地址，每一个数据都会保存下一个数据的内存的地址，通过此地址可以找到下一个数据，任意位置插入元素和删除元素效率较高，时间复杂度为O(1)。

要需要访问某个位置的数据，需要从第一个数据开始找起，依次往后遍历，直到找到待查询的位置，故可能在查找某个元素时，时间复杂度达到O(N)






优点：
1.任意位置插入元素和删除元素的速度快，时间复杂度为O(1) 
2.内存利用率高，不会浪费内存 
缺点： 

1. 随机访问效率低，时间复杂度为0(N) 



## 双链表 Doubly Linked List

双向链表也叫双链表，是链表的一种，它的每个数据结点中都有两个指针，分别指向直接后继和直接前驱。所以，从双向链表中的任意一个结点开始，都可以很方便地访问它的前驱结点和后继结点。


![](https://img-blog.csdnimg.cn/2019031515160942.jpg)




## 代码实现


下面以class类创建节点， 每个节点包含当前节点所要存的数据data，和指向下一节点的指针。

节点类的定义很简单，节点只有两个属性，data 和 next，next指向下一个节点。定义完节点类后，可以创建节点，但是还需要将节点连接在一起，构成链表才可以。



```python
class Node:
    '''定义节点类'''
    def __init__(self, data):
        self.data = data    #值域，存储数据
        self.next = None    #指针域，存储下一元素的地址

#定义四个节点
a = Node(86)
b = Node(19)
c = Node(4)
d = Node(12)
#最简单的方法将四个节点连接
a.next = b
b.next = c
c.next = d
head = a
#依次输出节点的值
while head is not None:
    print(head.data)
    head = head.next
#输出为 86 19 4 12
```

## 链表的实现


定义一个链表类来实现链表，同时可以定义对链表的简单操作，比如对链表进行添加节点，移除节点，插入节点等方法。





```python
class LinkedList:
    '''定义链表类'''
    def __init__(self):    #不需要参数，返回值是空链表
        self.head = None   #头节点
        self.tail = None   #尾节点
```



定义类方法，判断链表是否为空。

```java
def is_empty(self):    
    '''判断链表是否为空'''
    return self.head is None
```

定义类方法，向链表末尾新的节点。

```java
def append(self, data):    
    '''向链表里添加节点'''
    node = Node(data)      #创建一个节点实例
    if self.head is None:  #判断链表是否为空
         self.head = node   #如果是空链表，添加一个节点，头节点就是尾节点
         self.tail = node
     else:
         self.tail.next = node  #tail为尾节点，在尾节点添加新节点，尾节点的指针域
         self.tail = node       #指向下一节点，这时新的尾节点就是node节点
```

定义类方法，实现遍历链表元素。

```java
def iter(self):            
    '''遍历链表,函数返回的是一个生成器'''
    if not self.head:    #遍历从链表的头节点开始，如果不是，返回
        return
    current = self.head  #将head节点赋值给current,当前节点
    yield current.data   #包含yield语句的函数都被称为生成器。
    while current.next:
        current = current.next
        yield current.data

```

定义类方法，实现在链表指定位置插入新的节点。

```java
def insert(self, index, vaule):    
    '''在链表的指定索引插入一个新的节点'''
    current = self.head
    current_index = 0        #head节点的索引为0
    if self.head is None:    #如果链表为空
        raise Exception("The list is an empty list")
    while current_index < index -1:  #通过while循环找到指定索引的节点
        current = current.next
        if current is None:  #判断是否为尾节点
            raise Exception('......')
        current_index += 1
    node = Node(vaule)       #新建节点
    node.next = current.next #node的指针域指向原节点的下一节点
    current.next = node      #原节点的下一节点指向node
    if node.next is None:
        self.tail = node
```

要向 a 和 b节点之间插入一个新的节点 e ，需要将 `e.next = a.next `，之后再将 `a.next = e`，这是插入一个新的节点的关键。

定义类方法，实现移除链表指定索引的节点。

```java
def remove(self, index):
    '''移除链表指定索引元素'''
    current = self.head
    current_index = 0
    if self.head is None:  # 空链表时
        raise Exception('The list is an empty list')
    while current_index < index-1:
        current = current.next
        if current is None:
            raise Exception('list length less than index')
        current_index += 1
    if index == 0:   # 当删除第一个节点时
        self.head = current.next
        current = current.next
        return
    if self.head is self.tail:   # 当只有一个节点的链表时
        self.head = None
        self.tail = None
        return 
    current.next = current.next.next
    if current.next is None:  # 当删除的节点是链表最后一个节点时
        self.tail = current

```

定义类方法，返回链表的长度(节点的数量)。

```java
def size(self):
    '''返回链表长度'''
    current = self.head
    count = 0
    if current is None:
        return 'The list is an empty list'
    while current is not None:
        count += 1
        current = current.next
    return count

```


最后，来实现一下链表的一些简单操作。

```python
if __name__ == '__main__':
    l = LinkedList()    #创建一个链表对象，空链表
    for i in range(10): #向链表里添加节点
        l.append(i)
    print(list(l.iter()))   #遍历链表元素
    #输出为[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    l.insert(2, 10)    #在索引2处插入10
    print(list(l.iter()))   #遍历链表元素
    #输出为[0, 1, 10, 2, 3, 4, 5, 6, 7, 8, 9]
    l.remove(0)       #移除索引为0的节点
    print(list(l.iter()))   #遍历链表元素
    #输出为[1, 2, 3, 4, 5, 6, 7, 8, 9]
    print(l.size())   #输出链表的长度 输出为10

```


## LeetCode 第 2题：两数相加  



```java
#给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。 
# 如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。 
# 您可以假设除了数字 0 之外，这两个数都不会以 0 开头。 
# 示例： 
# 输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
#输出：7 -> 0 -> 8
#原因：342 + 465 = 807
# 
# Related Topics 链表 数学

```




思路一：将链表转化列表，反转列表 用join方法拼接数字 切片[::-1]，将sum转化成链表res


```python
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        # 将链表转化列表
        val1, val2 = [l1.val], [l2.val]

        while l1.next:
            val1.append(l1.next.val)
            l1 = l1.next

        while l2.next:
            val2.append(l2.next.val)
            l2 = l2.next

        # 反转列表 用join方法拼接数字 切片[::-1]


        num_1 = ''.join([str(i) for i in val1[::-1]])
        num_2 = ''.join([str(i) for i in val2[::-1]])

        sums =  str(int(num_1) + int(num_2))[::-1]

        # 将sum转化成链表res

        # 头节点
        res  = head = ListNode(int(sums[0]))

        for i in range(1, len(sums)):
            # 拼接
            head.next = ListNode(int(sums[i]))
            head = head.next
        return res



```




![](https://img-blog.csdnimg.cn/20200619160926309.png)


思路二：将结果保存在一个新的链表中，使用两个指针，一个指向头节点，用于返回结果，另一个指向当前节点，用于计算并保存结果。遍历两个输入链表，逐位进行相加，若某一个链表遍历到了结尾，则取 0 参与运算。每一位的数字为两个数字对应位以及进位之和除 10 的余数，而该位是否有进位则是这个和除 10 的商。



优化：不需要将整个数的和求出，只需要每一位对应相加，

![](https://img-blog.csdnimg.cn/20200619160405934.png)


```python
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
       # 判断0还是1
        res = 0
        root = n = ListNode(0)
    
        while l1 or l2 or res:
            v1 = v2 = 0
            if l1:
                v1 = l1.val
                l1 = l1.next
            if l2:
                v2 = l2.val
                l2 = l2.next
            # divmod() 函数把除数和余数运算结果结合起来，返回一个包含商和余数的元组(a // b, a % b)。
            res, val = divmod(v1 + v2 + res, 10)
            n.next = ListNode(val)
            n = n.next
            
        return root.next

```


![](https://img-blog.csdnimg.cn/20200619161524801.png)


# 69、Python | Leetcode链表系列（中篇）

﻿@Author：Runsen





今日，我决定继续更新Python教程，今天就开始了六十九、Python | Leetcode链表系列（中篇）。









## LeetCode  第21题：合并两个有序链表

```java
#将两个升序链表合并为一个新的 升序 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 
# 示例： 
#
# 输入：1->2->4, 1->3->4
#输出：1->1->2->3->4->4
# 
# Related Topics 链表
```


这个解决的方法使用递归，如果L1为空就返回L2，L2为空返回L1，L1的val<=L2的val，那么继续递归

```java
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution(object):
	def mergeTwoLists(self, l1, l2):
		"""
		:type l1: ListNode
		:type l2: ListNode
		:rtype: ListNode
		"""
		#递归的结束点就是L1或者L2为空就返回
		#如果L1为空就返回L2，L2为空返回L1
		# if not (l1 and l2):
			# return l1 if l1 else l2
		if not l1:
            return l2
        elif not l2:
            return l1
		#L1的val<=L2的val，那么继续递归
		#当前L1的next指向一个递归函数
		#意思是L1的下一个和L2哪个大，就作为当前L1的next
	    elif l1.val<=l2.val:
			l1.next = self.mergeTwoLists(l1.next,l2)
			return l1
		else:
			l2.next = self.mergeTwoLists(l1,l2.next)
			return l2

```





![](https://img-blog.csdnimg.cn/20200628114647839.png)


## LeetCode 第 23 题：合并 k 个排序链表

```java
#合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。 
# 示例: 
# 输入:
#[
#  1->4->5,
#  1->3->4,
#  2->6
#]
#输出: 1->1->2->3->4->4->5->6 
# Related Topics 堆 链表 分治算法
```


第1种法就是常规思路，直接将所有的元素取出，然后排个序，再重组就达到了目的。


遍历所有链表，将所有节点的值放到一个数组中。将这个数组排序，然后遍历所有元素得到正确顺序的值。用遍历得到的值，创建一个新的有序链表。


时间复杂度：$O(N\log N)$ ，其中 N 是节点的总数目



空间复杂度：$O(N)$。

排序花费$O(N)$空间（这取决于你选择的算法）。
创建一个新的链表花费 $O(N)$的空间。

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode :
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        self.nodes = []
        head = point = ListNode(0)
        for l in lists:
            while l:
                self.nodes.append(l.val)
                l = l.next
        for x in sorted(self.nodes):
            point.next = ListNode(x)
            point = point.next
        return head.next
```




时间复杂度：$O(N \log k)$，这里 N 是这 k 个链表的结点总数，每一次从一个优先队列中选出一个最小结点的时间复杂度是 $O(logk)$，故时间复杂度为	$O(N \log k)$。
空间复杂度：$O(k)$，使用优先队列需要 k 个空间，“穿针引线”需要常数个空间，因此空间复杂度为 $O(k)$。











## LeetCode 第 141 题：判断链表中是否有环



![](https://img-blog.csdnimg.cn/20191122154610446.png)


> 你能用 O(1)（即，常量）内存解决此问题吗？ 

遍历整个数组, 给出的数据包含在集合中则说明有环, 返回 True; 若遍历完毕, 则说明无环, 返回 False，如果用列表也是一样。

**暴力解法**

```python
class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        """
        暴力法：通过遍历链表，用set来存储访问的节点，如果在set出现一样的节点，说明有坏，时间复杂度O(n)
        :type head: ListNode
        :rtype: bool
        """
        st = set()
        while head:
            if head in st:
                return True
            st.add(head )
            head = head.next
        return False


		# 下面是列表
        l = []
        while head:
            if head in l:
                return True
            else:
                l.append(head)
                head = head.next
        return False
        
```





![](https://img-blog.csdnimg.cn/20200628121724978.png)

暴力的时间空间复杂度都是O(n)






题目要求用 $O(1)$空间复杂度


这道题考的是**快慢指针** $O(1)$空间复杂度






通过使用具有 不同速度 的快、慢两个指针遍历链表，空间复杂度可以被降低至$O(1)$。慢指针每次移动一步，而快指针每次移动两步。

如果列表中不存在环，最终快指针将会最先到达尾部，此时我们可以返回 false。



进阶的要求是以 O(1) 的空间复杂度实现, 想象这样一个场景, 你和一个朋友一起散步, 你每次移动两步, 朋友每次一步, 如为单向定长道路, 你必然先到达重点. 若是环绕操场,则你们终将相遇.





```java
class Solution(object):
    def hasCycle(self, head):
        slow = fast = head
        while slow and fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False
```



## LeetCode 第 206 题：反转链表





```java
#反转一个单链表。 
# 示例: 
# 输入: 1->2->3->4->5->NULL
#输出: 5->4->3->2->1->NULL 
# 进阶: 
#你可以迭代或递归地反转链表。你能否用两种方法解决这道题？ 
# Related Topics 链表
```

将当前节点的next指针指向前驱的节点，需要有2个指针来记录，一个记录当前节点，一个记录前驱节点，循环5次直到列表结束，三个简单复制语句

```python
class Solution:
    def reverseList(self, head):
        cur, prev = head, None
        while cur:
            cur.next, prev, cur = prev, cur, cur.next
        return prev
```
# 70、Python | Leetcode链表系列（下篇）

﻿@Author：Runsen







今日，我决定继续更新Python教程，今天就开始了七十、Python | Leetcode链表系列（下篇）。









## LeetCode  第24题：两两交换链表的节点


```java
#给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。 
#
# 你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。
# 示例: 
#
# 给定 1->2->3->4, 你应该返回 2->1->4->3.
# 
# Related Topics 链表
```


思路：a,b,pre记录三个指针，相邻两个，相邻两个元素前面的一个，第一步将节点 2 指向节点 1，然后再将节点 1 指向节点三。这一步交换完毕后链表变为 2->1->3->4。在进行下一次交换，将节点 4 指向节点 3，节点3指向none 但是还要注意节点 1 的指向，节点 1 要指向节点 4。




```java
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
	def swapPairs(self,head):
	    pre, pre.next = self, head
	    while pre.next and pre.next.next:
	        a = pre.next
	        b = a.next
	        pre.next,b.next ,a.next = b,a,b.next
	        pre = a
	        
	    return  self.next
```



![](https://img-blog.csdnimg.cn/2020070308012239.png)

## LeetCode  第83题：删除排序链表中的重复元素





```java
#给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。 
# 示例 1: 
# 输入: 1->1->2
#输出: 1->2
# 示例 2: 
# 输入: 1->1->2->3->3
#输出: 1->2->3 
# Related Topics 链表
```


如果遇到cur.val和cur.next.val重复,让cur.next=cur.next.next


```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        h = head
        while head and head.next:
            if head.val == head.next.val:
                head.next = head.next.next
            else:
                head = head.next
                
        return h

class Solution:
    def deleteDuplicates(self, head):
        cur = root = head
        while head:
            if head.val != cur.val:
                cur.next = cur = head
            head = cur.next = head.next
        return root
```





![](https://img-blog.csdnimg.cn/20200703081419328.png)


## LeetCode 第148题： 排序链表（重要）





```java
#在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序。
# 示例 1:
# 输入: 4->2->1->3
#输出: 1->2->3->4
# 示例 2: 
#
# 输入: -1->5->3->4->0
#输出: -1->0->3->4->5 
# Related Topics 排序 链表
```



题目要求时间空间复杂度分别为$O(nlogn)$和$O(1)$，根据时间复杂度我们自然想到二分法，从而联想到归并排序；

利用归并的思想，递归地将当前链表分为两段，然后merge，分两段的方法是使用 fast-slow 法，用两个指针，一个每次走两步，一个走一步，直到快的走到了末尾，然后慢的所在位置就是中间位置，这样就分成了两段。

归并排序分为两步，1.找到待排序链表的中间节点（使用快慢指针法，leetcode 876题）2.合并两个有序链表（leetcode 21题），因此本题相当于结合这两步来实现链表排序。

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
class Solution:
    def sortList(self, head: ListNode) -> ListNode:
        # if not head or not head.next:#
        if head == None or head.next == None:
            return head 
        slow  = head#快慢指针法找到链表中点
        fast = head
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        right = slow.next
        # print(right.val)
        slow.next = None #这一句的原因是 需要对中点前的链表进行割断处理

        l1 = self.sortList(head)#递归保证l1和l2为有序链表
        l2 = self.sortList(right)
        return self.mergeTwoLists(l1,l2)
	# 合并两个有序链表
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1 and not l2:
            return None
        if not l1:
            return l2
        if not l2:
            return l1
        head = head1 = ListNode(0)
        while l1 and l2:
            if l1.val <= l2.val:
                head.next = l1
                l1 = l1.next
            else:
                head.next = l2
                l2 = l2.next
            head = head.next
        if not l1 : head.next = l2
        if not l2 : head.next = l1
        return head1.next
```

下面是测试代码

```java
if __name__ == "__main__":
    n1 = ListNode(4)
    n2 = ListNode(7)
    n3 = ListNode(6)
    n4 = ListNode(9)
    n5 = ListNode(12)
    m=n1
    n1.next=n2
    n2.next=n3
    n3.next=n4
    n4.next=n5
    print('原链表的节点：')    
    while m:
        print('节点%d的值:'%(m.val),m.val)
        m=m.next
    print('\n排序之后的节点：')

    s=Solution()
    s.sortList(n1)
    while n1:
        print('节点%d的值:'%(n1.val),n1.val)
        n1=n1.next
#result
原链表的节点：
节点4的值: 4
节点7的值: 7
节点6的值: 6
节点9的值: 9
节点12的值: 12

排序之后的节点：
节点4的值: 4
节点6的值: 6
节点7的值: 7
节点9的值: 9
节点12的值: 12
```


![](https://img-blog.csdnimg.cn/20200703082922110.png)

## LeetCode 第 876题： 链表的中间结点（重要）

```java
# 输入：[1,2,3,4,5]
#输出：此列表中的结点 3 (序列化形式：[3,4,5])
#返回的结点值为 3 。 (测评系统对该结点序列化表述是 [3,4,5])。
#注意，我们返回了一个 ListNode 类型的对象 ans，这样：
#ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, 以及 ans.next.next.next = NULL.
# 示例 2： 
# 输入：[1,2,3,4,5,6]
#输出：此列表中的结点 4 (序列化形式：[4,5,6])
#由于该列表有两个中间结点，值分别为 3 和 4，我们返回第二个结点。
# 提示： 
# 给定链表的结点数介于 1 和 100 之间。 
# Related Topics 链表
```

**思路**

- 遍历两次。第一次遍历求导链表长度，找出中间结点的长度值，第二层遍历找到中间结点并返回；
- 快慢指针法。慢指针每次走一步，快指针每次走两步，快指针走到链表末尾时，慢指针刚好走到链表中间。方法２时间复杂度更低，只需遍历一次。

```java
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    def middleNode(self, head: ListNode) -> ListNode:
        slow = head
        fast = head
        while  fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        return slow

```



![](https://img-blog.csdnimg.cn/20200703083340934.png)

# 71、Python | Leetcode字符串系列（上篇）
﻿@Author：Runsen




今日，我决定继续更新Python教程，今天就开始了七十一、Python | Leetcode字符串系列（上篇）。




## 字符串

首先我们先去[Leetcode字符串官网](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9sZWV0Y29kZS1jbi5jb20vZXhwbG9yZS9mZWF0dXJlZC9jYXJkL2FycmF5LWFuZC1zdHJpbmcvMjAwL2ludHJvZHVjdGlvbi10by1zdHJpbmcvNzc3Lw?x-oss-process=image/format,png)，查看字符串相操作。




维基百科：字符串是由零个或多个字符组成的有限序列。一般记为 s = a1a2...an。它是编程语言中表示文本的数据类型。使用 `名称[下标] `来得到一个字符



在某些语言（如 C ++）中，字符串是可变的。 也就是说，你可以像在数组中那样修改字符串。
在其他一些语言（如 Java、Python）中，字符串是不可变的。



## LeetCode 第3题：无重复字符的最长子串

该题目会涉及到一个概念“滑动窗口”。

```java
# 示例 1:
# 输入: "abcabcbb"
# 输出: 3
#解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
# 示例 2:
# 输入: "bbbbb"
#输出: 1
#解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
# 示例 3
# 输入: "pwwkew"
#输出: 3
#解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
#     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
# Related Topics 哈希表 双指针 字符串 Sliding Window

```


下面我们看看，“滑动窗口”如何进行字符串处理。结合题目中的例子“abcabcbb”这个字符串，我们来看看如何找它的无重复最长子串。

首先，我们定义窗口的两端：begin和end，分别表示要找的子串的开头和结尾。
![](https://img-blog.csdnimg.cn/20200703085538169.png)


开始的时候，begin和end都指向0的位置即‘a’，然后end不断后移（窗口变宽），当遇到第二个‘a’时（遇见重复字符）就得到一个子串，其长度就是end和begin位置的差。

如何判断是否遇到了重复字符‘a’呢？需要一个字典作为辅助数据结构，把end从头开始遇到的每个字符及其索引位置都放到字典里面，end每次移动到新字符就查一下字典即可




```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        # 定义两个变量res和start,res用于存储最长子字符串的长度，start存储无重复子串左边的起始位置。
        '''
        然后创建一个哈希表，遍历整个字符串，如果字符串没有在哈希表中出现，说明没有遇到过该字符，则此时计算最长无重复子串，当哈希表中的值小于left，说明left位置更新了，需要重新计算最长无重复子串。每次在哈希表中将当前字符串对应的赋值加1。
        :param s:
        :return:
        '''
        d, res, start = {}, 0, 0
        for i, ch in enumerate(s):
            if ch in d:
                start = max(start, d[ch] + 1)
            res = max(res, i - start + 1)
            d[ch] = i
        print(res)
        return res

```



![](https://img-blog.csdnimg.cn/20200703085314693.png)



下面也是一个做法

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if s == '':
            return 0
        res = 1
        i = 0
        for j in range(1,len(s)):
            if s[j] not in s[i:j]:
                res = max(res,j+1-i)
            else:
                i += s[i:j].index(s[j]) + 1
        return res

```

## LeetCode 第8题：字符串转换整数 (atoi)



```python
#请你来实现一个 atoi 函数，使其能将字符串转换成整数。 
# 首先，该函数会根据需要丢弃无用的开头空格字符，直到寻找到第一个非空格的字符为止。接下来的转化规则如下： 
# 如果第一个非空字符为正或者负号时，则将该符号与之后面尽可能多的连续数字字符组合起来，形成一个有符号整数。 
# 假如第一个非空字符是数字，则直接将其与之后连续的数字字符组合起来，形成一个整数。 
# 该字符串在有效的整数部分之后也可能会存在多余的字符，那么这些字符可以被忽略，它们对函数不应该造成影响。 
# 注意：假如该字符串中的第一个非空格字符不是一个有效整数字符、字符串为空或字符串仅包含空白字符时，则你的函数不需要进行转换，即无法进行有效转换。 
# 在任何情况下，若函数不能进行有效的转换时，请返回 0 。 
# 提示： 
# 本题中的空白字符只包括空格字符 ' ' 。 
# 假设我们的环境只能存储 32 位大小的有符号整数，那么其数值范围为 [−231, 231 − 1]。如果数值超过这个范围，请返回 INT_MAX (231 − 1) 或 INT_MIN (−231) 。 
# 示例 1: 
# 输入: "42"
#输出: 42
# 示例 2: 
#
# 输入: "   -42"
#输出: -42
#解释: 第一个非空白字符为 '-', 它是一个负号。
#     我们尽可能将负号与后面所有连续出现的数字组合起来，最后得到 -42 。
# 示例 3: 
# 输入: "4193 with words"
#输出: 4193
#解释: 转换截止于数字 '3' ，因为它的下一个字符不为数字。
# 示例 4: 
# 输入: "words and 987"
#输出: 0
#解释: 第一个非空字符是 'w', 但它不是数字或正、负号。
#     因此无法执行有效的转换。 
#
# 示例 5: 
# 输入: "-91283472332"
#输出: -2147483648
#解释: 数字 "-91283472332" 超过 32 位有符号整数范围。 
#     因此返回 INT_MIN (−231) 。
# Related Topics 数学 字符串

```

最快的方法就是正则，re.find可以返回包含所有匹配字符串的列表，列表中只有一个字符串用于此问题，因为我们使用^来匹配开头。所以我们可以使用解压缩列表来获取它。[‘abc’] == ‘abc’

```python
class Solution:
    def myAtoi(self, s: str) -> int:
        return max(min(int(*re.findall('^[\+\-]?\d+', s.lstrip())), 2**31 - 1), -2**31)

class Solution:
    def myAtoi(self, str: str) -> int:
        str = str.strip()
        if len(str) == 0: return 0
        strlist = list(str.split(' ')[0])
        for i in range(1,len(strlist)):
            if strlist[i] < '0' or strlist[i] > '9':
                strlist[i] = ' '
                break
        str = ''.join(strlist).split(' ')[0]
        try:
            ret = int(str)
        except:
            return 0

        if ret > 2147483647: return 2147483647
        elif ret < -2147483648: return -2147483648
        else: return ret

```


## LeetCode 第17题：电话号码的字母组合

```java
'''
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。
给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。
示例:
输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
tb = ['abc', 'def', 'ghi', 'jkl', 'mno', 'pqrs', 'tuv', 'wxyz']
'''

```

![](https://img-blog.csdnimg.cn/20200703094427404.png)


```java
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        phone= {
            '2':['a','b','c'],
            '3':['d','e','f'],
            '4':['g','h','i'],
            '5':['j','k','l'],
            '6':['m','n','o'],
            '7':['p','q','r','s'],
            '8':['t','u','v'],
            '9':['w','x','y','z']
        }
        def backtrack(combination,next_digits):
            if len(next_digits) == 0:
                return output.append(combination)
            else:
                for letter in phone[next_digits[0]]:
                    backtrack(combination+letter,next_digits[1:])
                
                
        output = []
        if digits:
            backtrack('',digits)
        return output


class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        conversion={'2':'abc','3':'def','4':'ghi','5':'jkl','6':'mno','7':'pqrs','8':'tuv','9':'wxyz'}
        if len(digits)==0:
            return [] 
        product=['']
        for k in digits:
            product=[i+j for i in product for j in conversion[k]]
        return product

```



## LeetCode 第20题：有效的括号



```java
'''
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。
有效字符串需满足：
    左括号必须用相同类型的右括号闭合。
    左括号必须以正确的顺序闭合。
    注意空字符串可被认为是有效字符串。
输入: "{[]}"
输出: true
'''

def isValid(s):
    """
    :type s: str
    :rtype: bool
    """
    stack = []
    paren_map ={')':'(',']':'[','}':'{'}
    for c in s:
        if c not in paren_map:
            stack.append(c)
        elif not stack or paren_map[c] !=stack.pop():
            return False
    return not stack
s = input('输入括号字符:')
print(isValid(s))

```

也可以利用python种的replace函数将成对的可匹配括号用空字符代替 ，之后依次进行 ，若是有效的括号 ，必然经过有限次循环后 ，字符串为空 ，则最后判断字符串是否为空即可。思路简单 ，实现也很容易 ：

![](https://img-blog.csdnimg.cn/20200703095225329.png)


## LeetCode 第125题：验证回文串

```java
#给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。 
# 说明：本题中，我们将空字符串定义为有效的回文串。 
# 示例 1: 
# 输入: "A man, a plan, a canal: Panama"
#输出: true
# 示例 2: 
# 输入: "race a car"
#输出: false
# Related Topics 双指针 字符串

```


用正则表达式，将除字母、数字以外的字符全部去掉，然后判断是否对称

```java
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = re.sub(r'[^a-z0-9]', '', s.strip().lower())
        return s == s[::-1]


```


让字符串字母都变成小写，然后只保留字母和数字，翻转，比较得到结果



```java
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = ''.join(filter(str.isalnum, s.lower()))
        return s == s[::-1]

```


![](https://img-blog.csdnimg.cn/20200703095729397.png)
# 72、Python | Leetcode字符串系列（下篇）
﻿@Author：Runsen







今日，我决定继续更新Python教程，今天就开始了七十二、Python | Leetcode字符串系列（下篇）。




## LeetCode 第14题：最长公共前缀



```java
#编写一个函数来查找字符串数组中的最长公共前缀。 
# 如果不存在公共前缀，返回空字符串 ""。 
# 示例 1: 
# 输入: ["flower","flow","flight"]
#输出: "fl"
# 示例 2: 
# 输入: ["dog","racecar","car"]
#输出: ""
#解释: 输入不存在公共前缀。
# 说明: 
# 所有输入只包含小写字母 a-z 。 
# Related Topics 字符串
```






解题思路：使用 zip 根据字符串下标合并成数组，判断合并后数组里元素是否都相同




```java
class Solution(object):
    def longestCommonPrefix(self, strs):
        ans = ''
        for i in zip(*strs):
            if len(set(i)) == 1:
                ans += i[0]
            else:
                break
        return ans
```







## LeetCode 第28题：实现 strStr()


```java
#实现 strStr() 函数。 
# 给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回 -1。 
# 示例 1: 
# 输入: haystack = "hello", needle = "ll"
#输出: 2
# 示例 2: 
# 输入: haystack = "aaaaa", needle = "bba"
#输出: -1
# 说明: 
# 当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。 
# 对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及 Java的 indexOf() 定义相符。 
# Related Topics 双指针 字符串
```

通过index进行needle数据查询，当不存在是index会报错，直接将其输出-1即可



```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if needle in haystack:         
            num = haystack.index(needle)
        else:
            return -1
        return num
```



## LeetCode 第67题： 二进制求和



```java
#给你两个二进制字符串，返回它们的和（用二进制表示）。 
# 输入为 非空 字符串且只包含数字 1 和 0。 
# 示例 1: 
# 输入: a = "11", b = "1"
#输出: "100" 
# 示例 2: 
# 输入: a = "1010", b = "1011"
#输出: "10101" 
# 提示： 
# 每个字符串仅由字符 '0' 或 '1' 组成。 
# 1 <= a.length, b.length <= 10^4 
# 字符串如果不是 "0" ，就都不含前导零。 
# Related Topics 数学 字符串
```

用python在十进制与二进制之间进行转换，求和转化返回。



```java
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        atmp = eval('0b' + a) #a对应的10进制数
        btmp = eval('0b' + b) #b对应的10进制数
        sumtmp = atmp + btmp #a+b对应的10进制数
        res = bin(sumtmp)  #10进制数转化为二进制数字符串
        return res[2:]   #返回结果字符串
```





位运算模拟二进制加法运算。异或运算的特点是a和b不一样才为1，与运算的特点是a和b同为1时才为1，否则为0，刚好可以逐步记录进位。

![](https://img-blog.csdnimg.cn/20200703101705855.png)


```java
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        atmp = eval('0b' + a)
        btmp = eval('0b' + b)
        while btmp:
            ans = (atmp ^ btmp)
            btmp = (atmp & btmp) << 1
            atmp = ans
        return bin(atmp)[2:]
```

## LeetCode 第344题： 反转字符串

```java
#编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 char[] 的形式给出。 
# 不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用 O(1) 的额外空间解决这一问题。 
# 你可以假设数组中的所有字符都是 ASCII 码表中的可打印字符。 
# 示例 1： 
# 输入：["h","e","l","l","o"]
#输出：["o","l","l","e","h"]
# 示例 2： 
# 输入：["H","a","n","n","a","h"]
#输出：["h","a","n","n","a","H"] 
# Related Topics 双指针 字符串
```

双指针思想，左右交换



```java
 class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        i,j=0,len(s)-1
        while i<=j:
            s[i],s[j]=s[j],s[i]
            i+=1
            j-=1


class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        s.reverse()


```


## LeetCode 第557题：  反转字符串中的单词 III

```java
#给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。 
# 示例 1: 
#输入: "Let's take LeetCode contest"
#输出: "s'teL ekat edoCteeL tsetnoc" 
# 注意：在字符串中，每个单词由单个空格分隔，并且字符串中不会有任何额外的空格。 
# Related Topics 字符串

```


将字符串分割成单词列表 然后把每个单词反转切片

```java
class Solution(object):
    def reverseWords(self, s):
        return " ".join(word[::-1] for word in s.split(" "))

```



先反转单词列表 再反转字符串

以字符串` “I love drag queen” `为例：

`s.split(" ") `将字符串分割成单词列表:


`['I', 'love', 'drag', 'queen']`


`s.split(" ")[::-1] `将单词列表反转:


`['queen', 'drag', 'love', 'I']`

`" ".join(s.split(" ")[::-1]) `将单词列表转换为字符串，以空格分隔:


`"queen drag love I"`


`" ".join(s.split(" ")[::-1])[::-1] `将字符串反转：


`”I evol gard neeuq“`

```java
class Solution(object):
    def reverseWords(self, s):
        return " ".join(s.split(" ")[::-1])[::-1]

```

# 73、Python | Leetcode数字系列（上篇）

﻿@Author：Runsen







今日，我决定继续更新Python教程，今天就开始了七十三、Python | Leetcode数字系列（上篇）。

这一部分是比较简单的，就当作Python编写代码的练习题。

## LeetCode 第9题： 回文数

```java
#判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。 
# 示例 1: 
# 输入: 121
#输出: true
# 示例 2: 
# 输入: -121
#输出: false
#解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
# 示例 3: 
# 输入: 10
#输出: false
#解释: 从右向左读, 为 01 。因此它不是一个回文数。
# 进阶: 
# 你能不将整数转为字符串来解决这个问题吗？ 
# Related Topics 数学
```


最好理解的一种解法就是先将 整数转为字符串 ，然后将只需要循环每个字符进行判断对应元素是否相等即可。可以的话，还可以`return str(x) == str(x)[::-1]`简单粗暴。
`


```java
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if not x:
            return True
        str_x = str(x)
        n = len(str_x)
        for i in range(n-1):
            if str_x[i] != str_x[n-1-i]:
                return False
        return True
```


不将整数转为字符串，那么算出对应的回文数在比较欧克。

```java
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0: # 如果为负数，直接返回 false
            return False
        num = x
        cur = 0
        while num !=0:
            cur = cur*10 + num%10
            num //=10
        return cur == x # 最后比较 数值反转前后是否相等
```


## LeetCode 第12题：整数转罗马数字


```java
#罗马数字包含以下七种字符： I， V， X， L，C，D 和 M。 
# 字符          数值
#I             1
#V             5
#X             10
#L             50
#C             100
#D             500
#M             1000 
# 例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做 XXVII, 即为 XX + V + II 。 
# 通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况： 
# I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。 
# X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
# C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。 
# 给定一个整数，将其转为罗马数字。输入确保在 1 到 3999 的范围内。 
# 示例 1: 
# 输入: 3
#输出: "III" 
# 示例 2: 
# 输入: 4
#输出: "IV" 
# 示例 3: 
# 输入: 9
#输出: "IX"
# 示例 4: 
# 输入: 58
#输出: "LVIII"
#解释: L = 50, V = 5, III = 3.
# 示例 5: 
# 输入: 1994
#输出: "MCMXCIV"
#解释: M = 1000, CM = 900, XC = 90, IV = 4. 
# Related Topics 数学 字符串
```

使用哈希表解决.哈希表键为整数，值为罗马数字，且键从大到小排列；遍历整个哈希表，判断当前数值是否大于等于此刻的键：若能，则s加上整除的个数乘以值；若不能，则遍历下一个。






```java
class Solution:
    def intToRoman(self, num: int) -> str:
        d = {1000: 'M', 900: 'CM', 500: 'D', 400: 'CD', 100: 'C', 90: 'XC', 50: 'L', 40: 'XL', 10: 'X', 9: 'IX', 5: 'V', 4: 'IV', 1: 'I'}
        res = ''
        for k in d:
            while num >= k:
                res += d[k]
                num -= k
        return res
```



## LeetCode 第13题：整数转罗马数字


```java
#罗马数字包含以下七种字符: I， V， X， L，C，D 和 M。 
# 字符          数值
#I             1
#V             5
#X             10
#L             50
#C             100
#D             500
#M             1000 
# 例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做 XXVII, 即为 XX + V + II 。 
# 通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况： 
# I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。 
# X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
# C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。 
# 给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。 
# 示例 1: 
# 输入: "III"
#输出: 3 
# 示例 2: 
# 输入: "IV"
#输出: 4 
# 示例 3: 
# 输入: "IX"
#输出: 9 
# 示例 4: 
# 输入: "LVIII"
#输出: 58
#解释: L = 50, V= 5, III = 3.
# 示例 5: 
# 输入: "MCMXCIV"
#输出: 1994
#解释: M = 1000, CM = 900, XC = 90, IV = 4. 
# Related Topics 数学 字符串
```


思路：

- 创建hashMap字典表映射罗马数字和整数。
- .如果当前字符代表的值不小于其右边，就加上该值；否则就减去该值。

```java
class Solution:
    def romanToInt(self, s: str) -> int:
        a = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        ans=0
        for i in range(len(s)):
            if i<len(s)-1 and a[s[i]]<a[s[i+1]]:
                ans-=a[s[i]]
            else:
                ans+=a[s[i]]
        return ans
```

## LeetCode 第29题： 两数相除

```java
#给定两个整数，被除数 dividend 和除数 divisor。将两数相除，要求不使用乘法、除法和 mod 运算符。 
# 返回被除数 dividend 除以除数 divisor 得到的商。 
# 整数除法的结果应当截去（truncate）其小数部分，例如：truncate(8.345) = 8 以及 truncate(-2.7335) = -2 
# 示例 1: 
# 输入: dividend = 10, divisor = 3
#输出: 3
#解释: 10/3 = truncate(3.33333..) = truncate(3) = 3 
# 示例 2: 
# 输入: dividend = 7, divisor = -3
#输出: -2
#解释: 7/-3 = truncate(-2.33333..) = -2 
# 提示： 
# 被除数和除数均为 32 位有符号整数。 
# 除数不为 0。 
# 假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−231, 231 − 1]。本题中，如果除法结果溢出，则返回 231 − 1。 
# Related Topics 数学 二分查找
```



乘除取余都不让用，那就位运算走起. 那问题是，如何设计位运算？`商*除数+余数=被除数`，这个式子大家肯定都清楚 在本题中， 余数是可以忽略的，当然， 余数肯定是小于 除数的 那么我们就可以理解为：商就是 被除数减去N多个 除数，直到 `被除数-N个除数变得小于 `除数最终就是 N这个 商了。



让我们先回顾一下小学时，怎么通过列竖式的方法计算两个整数的除法，以 45/2 为例：




![](https://img-blog.csdnimg.cn/20200703155803356.png)
仔细观察不难发现，这种算法是把除法化归成移位和减法两种运算方法。对于 10 进制数，移位运算就是乘（左移）除（右移）10，而我们都知道计算机中的移位运算是乘（左移）除（右移）2，因为计算机是通过二进制的方法存储数的。这样，类比十进制，二进制的除法（仍以 45/2 为例）可以写作（注意，这里我们并没有用到乘除法）

![](https://img-blog.csdnimg.cn/20200703155822378.png)


下面就是代码实现了

```java
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        # 使用异或判断符号
        sign = (dividend>0)^(divisor>0)
        # 方便起见全部使用正数来做除法，最后加上符号
        dividend = abs(dividend)
        divisor = abs(divisor)
        count = 0

        while dividend >= divisor:
            divisor <<= 1
            count += 1
        result = 0

        while count > 0:
            count -= 1
            divisor >>= 1
            if divisor <= dividend:
                dividend = dividend-divisor
                result += 1<<count
        if sign:
            result = -result

        return result if -(1<<31)<=result<=(1<<31)-1 else (1<<31)-1

```

## LeetCode 第50题： Pow(x, n)



```java
#实现 pow(x, n) ，即计算 x 的 n 次幂函数。 
# 示例 1: 
# 输入: 2.00000, 10
#输出: 1024.00000
# 示例 2: 
# 输入: 2.10000, 3
#输出: 9.26100
# 示例 3: 
# 输入: 2.00000, -2
#输出: 0.25000
#解释: 2-2 = 1/22 = 1/4 = 0.25 
# 说明: 
# -100.0 < x < 100.0 
# n 是 32 位有符号整数，其数值范围是 [−231, 231 − 1] 。 
# Related Topics 数学 二分查找

```

主要是注意n的正负，这个题比较简单了，直接递归调用就行。

- 如果 n 是负数，那么相当于求$ (1/x)^(-n)。
- n 是正数 且 奇数，那么结果需要单独乘以 x
- 如果 n 是正数 且 偶数，求(x^2)^(n/2)，一直递归下去即可。

```java
class Solution(object):
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if n == 0:
            return 1
        if n < 0:
            x = 1 / x
            n = -n
        if n % 2:
            return x * self.myPow(x, n - 1)
        return self.myPow(x * x, n / 2)

```



使用迭代的方法，这个方法叫做二分求幂。


```java
class Solution:
    def myPow(self, x: float, n: int) -> float:
        if n == 0:
            return 1
        if n < 0:
            x = 1 / x
            n = -n
        p = 1
        while n > 1:
            if n % 2 == 0:
                x = x * x
                n /= 2
            else:
                p *= x
                n -= 1
        p *= x        
        return p

```
# 74、Python | Leetcode数字系列（下篇）
﻿@Author：Runsen


今日，我决定继续更新Python教程，今天就开始了七十四、Python | Leetcode数字系列（下篇）。

这一部分也是比较简单的，就当作Python编写代码的练习题。



##  LeetCode 第 69题：x 的平方根


```cpp
#实现 int sqrt(int x) 函数。 
# 计算并返回 x 的平方根，其中 x 是非负整数。 
# 由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。 
# 示例 1: 
# 输入: 4
#输出: 2
# 示例 2: 
# 输入: 8
#输出: 2
#说明: 8 的平方根是 2.82842..., 
#     由于返回类型是整数，小数部分将被舍去。
# Related Topics 数学 二分查找
```


这个题目的话，使用二分查找，left是1，high是数字x。就是一个二分查找，不懂二分查找的自己去搜索。每次去计算mid*mid与数字x的大小，如果比x大，那么就令high去等于mid-1;比x小，就令low等于mid+1;等于x,那么直接返回mid;


```python
class Solution:
    def mySqrt(self, x: int) -> int:
        l, r = 0, x
        while l <= r:
            mid = l + (r-l)//2
            if mid * mid <= x < (mid+1)*(mid+1):
                return mid
            elif x < mid * mid:
                r = mid
            else:
                l = mid + 1
```


还有一种方法是牛顿法, 利用一阶线性近似快速寻找最优点.。


$X_{k+1}=\frac{X_k-Y_k}{{f}'(X_k)}=\frac{1}{2}(X_k+\frac{a}{X_k})$

```cpp
class Solution:
    def mySqrt(self, x: int) -> int:
        if x < 2:
            return x
        r0 = x
        r1 = (r0 + x / r0) / 2
        while abs(r0 - r1) >= 1:
            r0 = r1
            r1 = (r1 + x / r1) / 2
        return int(r1)
```

##  LeetCode 第 169题：多数元素






```cpp
#给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。
# 你可以假设数组是非空的，并且给定的数组总是存在多数元素。
# 示例 1: 
# 输入: [3,2,3]
#输出: 3 
# 示例 2: 
# 输入: [2,2,1,1,1,2,2]
#输出: 2
# 
# Related Topics 位运算 数组 分治算法
```

利用集合的计数功能找到出现最多的元素并记录下来



```cpp
import collections
class Solution(object):
    def majorityElement(self, nums):
        k=collections.Counter(nums)
        [(i,j)]=k.most_common(1)
        return i 
        # return sorted(nums)[len(nums)//2]

#哈希表
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        d = {}
        for i in nums:
            d[i] = d.get(i,0) + 1 
            if d[i] >len(nums)/2:
                return i
```


## LeetCode 第 171题：Excel表列序号





```cpp
#给定一个Excel表格中的列名称，返回其相应的列序号。 
# 例如， 
#     A -> 1
#    B -> 2
#    C -> 3
#    ...
#    Z -> 26
#    AA -> 27
#    AB -> 28 
#    ...
# 示例 1: 
# 输入: "A"
#输出: 1
# 示例 2: 
# 输入: "AB"
#输出: 28
# 示例 3: 
# 输入: "ZY"
#输出: 701 
# Related Topics 数学
```

这是26进制转换为10进制问题，有两点：

- 就是进制转换的时候，最高位代表的是26的几次方以及其他的位	
- 谁乘这个26的几次方，这个通过A-B算出该为的数值。

```cpp
class Solution:
    def titleToNumber(self, s: str) -> int:
        dct = {"A": 1, "B": 2, "C": 3, "D": 4, "E": 5, "F": 6, "G": 7, "H": 8, "I": 9, 
               "J": 10, "K": 11, "L": 12, "M": 13, "N": 14, "O": 15, "P": 16, "Q": 17, 
               "R": 18, "S": 19, "T": 20, "U": 21, "V": 22, "W": 23, "X": 24, "Y": 25, "Z": 26}
        return sum([26**i*dct[j] for i, j in enumerate(s[::-1])])
```

将大写字母转成数字（差64），再按位置乘以26的次方（26个字母），累加。（相当于26进制数转十进制）也是一种做法。。

```cpp
class Solution:
    def titleToNumber(self, s: str) -> int:
        # return ord("A")  # A = 65
        return sum( [(ord(s[i])-64) * 26 ** (len(s)-1-i) for i in range(len(s))]) 
```


## LeetCode 第 231题： 2的幂


```cpp
#给定一个整数，编写一个函数来判断它是否是 2 的幂次方。 
# 示例 1: 
# 输入: 1
#输出: true
#解释: 2^0 = 1 
# 示例 2: 
# 输入: 16
#输出: true
#解释: 2^4 = 16 
# 示例 3: 
# 输入: 218
#输出: false 
# Related Topics 位运算 数学

```




若 $n = 2^x$,，且 $x$为自然数（即 n为 2 的幂），则一定满足以下条件：
恒有 `n&(n - 1) == 0`，这是因为：n 二进制最高位为 1，其余所有位为 0；n - 1 二进制最高位为 0，其余所有位为 1；一定满足 n > 0。因此，通过` n > 0 `且 `n & (n - 1) == 0 `即可判定是否满足$n = 2^x$



2^x	|n|n - 1	|n & (n - 1)
--|--|--|--
$2^0$|0001|0000	|(0001) & (0000) == 0
$2^1$|0010|0001	|(0010) & (0001) == 0
$2^2$|0100|0011	|(0100) & (0011) == 0
$2^3$|1000|0111	|(1000) & (0111) == 0


```cpp
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        return n > 0 and n & (n - 1) == 0

```


## LeetCode 第 279题： 完全平方数





```cpp
#给定正整数 n，找到若干个完全平方数（比如 1, 4, 9, 16, ...）使得它们的和等于 n。你需要让组成和的完全平方数的个数最少。 
# 示例 1: 
# 输入: n = 12
#输出: 3 
#解释: 12 = 4 + 4 + 4. 
# 示例 2: 
# 输入: n = 13
#输出: 2
#解释: 13 = 4 + 9. 
# Related Topics 广度优先搜索 数学 动态规划

```


下面是动态规划的做法：


动态规划：因为要求完全平方数个数最少，设i的最少完全平方数为dp[i]，用j表示完全平方数。那么dp[i]=dp[i-j]+1，因此可以使用动态规划。
问题的关键是n是由哪几个完全平方数组成最小，比如12：可以是dp[8]+dp[4]，也可以是dp[3]+dp[9],用square构建完全平方数列表，用j在里面循环输出dp[i]最小值。
代码




状态DP：dp[i]:组成和为i的完全平方数的最少个数。
状态转移：dp[i] = min(dp[i],dp[i-j*j]+1)
初始化：最坏的结果是:i=1+1+...+1,故初始化为：[i for i in range(n+1)]

动态规划代码简洁， 但时间长

```cpp
def numSquares(self, n: int) -> int:
     #动态规划
     dp = [i for i in range(n+1)]
     
     for i in range(2,n+1):
         for j in range(int(i**0.5)+1):
             dp[i] = min(dp[i], dp[i-j*j]+1)
     return dp[n]]

```


还有一种方法是广度优先搜索，就是BFS 算法。这个算法在以后再说。
# 75、Python | Leetcode哈希表系列

﻿@Author：Runsen





今日，我决定继续更新Python教程，今天就开始了七十五、Python | Leetcode哈希表系列。




## 哈希表

哈希表（散列表）的思想是将关键字 Key 映射到存放记录的散列表中从而进行快速访问，其中映射函数 f(key) 称为哈希函数（散列函数），依据哈希函数建立的查找表称为哈希表。

Hash，音译为哈希，是把任意长度的输入（又叫做预映射pre-image）通过散列算法变换成固定长度的输出，该输出就是散列值。这种转换是一种压缩映射，也就是，散列值的空间通常远小于输入的空间，不同的输入可能会散列成相同的输出，所以不可能从散列值来确定唯一的输入值。简单的说就是一种将任意长度的消息压缩到某一固定长度的消息摘要的函数。


假如班级里面有50个学生，都有各自的名字，我们想把学生的名字放在一个表上，同时便于很快的查找，你会毫无想到数组，但是查找的复杂度是`O(n)`,所以哈希表就是为了解决这问题，将查找的复杂度达到 `O(1)`

![](https://img-blog.csdnimg.cn/20190319091629943.png)




假如有个学生的名字叫做`lies`,通过hash函数，得到下标`9` ，将`lies`的ASCII码加起来 `429%30 =9` ,这样的过程就是`hash`函数。

但是又没有可能出现`hash`碰撞，就是出现了一样的`hash`值，当然有可能


![](https://img-blog.csdnimg.cn/20190319091548415.png)


假如有个人的名字叫做`foes`,那么如何查找呢？当然是将数据储存成链表，用链表的方式来查找。



其实，哈希表就是一个具备映射关系的表，我们可以通过映射关系由键找到值。下面是一个简单的哈希表：

```cpp
class Map:
    def __init__(self):
        self.items =[None]*100
    def hash(self,a):
        return a*1+0
    def put(self,k,v):
        self.items[hash(k)] = v
    def get(self,k):
        hashcode=hash(k)
        return self.items[hashcode]

```


这个哈希函数十分简单，但简单不妨碍它成为一个哈希函数，事实上，它叫直接定址法，是一个线性函数：$hash(k)= a*k+b$

直接定址法的优点很明显，就是它不会产生重复的hash值。但由于它与键值本身有关系，所以当键值分布很散的时候，会浪费大量的存储空间。所以一般是不会用到直接定址法的。




![](https://img-blog.csdnimg.cn/20200703231235952.png)

## LeetCode 第 136题：只出现一次的数字



```cpp
#给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。 
# 说明： 
# 你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？ 
# 示例 1: 
# 输入: [2,2,1]
#输出: 1
# 示例 2: 
# 输入: [4,1,2,1,2]
#输出: 4 
# Related Topics 位运算 哈希表

```


下面一行代码不做解释。

```cpp
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return sum(set(nums))*2-sum(nums)


```

一遍遍历，用哈希表计数；再遍历，返回个数是1的数。`{}`用于创建空字典，空集合用`set()`
dict的.get(a,b)中取出字典中键为a的值，如果不存在这样的键，则返回b。



```cpp
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        dic = {}
        for i in nums:
            dic[i] = dic.get(i,0)+1
            
        for i in nums:
            if dic.get(i)==1:
                return i

```


## LeetCode 第 217题：存在重复元素



```cpp
#给定一个整数数组，判断是否存在重复元素。 
# 如果任意一值在数组中出现至少两次，函数返回 true 。如果数组中每个元素都不相同，则返回 false 。 
# 示例 1: 
# 输入: [1,2,3,1]
#输出: true 
# 示例 2: 
# 输入: [1,2,3,4]
#输出: false 
# 示例 3: 
# 输入: [1,1,1,3,3,4,3,2,4,2]
#输出: true 
# Related Topics 数组 哈希表

```

下面代码不解释

```cpp
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        if len(set(nums)) == len(nums):
            return False
        else: 
            return True

```

初试化哈希表`dic = {}`。遍历数组：若i不在hash中，则令`dic[i] = 1`为key，1为value（随便什么都可以）。若已存在，则返回True。


```cpp
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        dic = {}
        for i in nums:
            if dic.get(i):
                return True
            dic[i] = 1
        return False

```


## 剑指 Offer 50. 第一个只出现一次的字符



```cpp
#在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。 
# 示例: 
# s = "abaccdeff"
#返回 "b"
#s = "" 
#返回 " "
# 限制： 
# 0 <= s 的长度 <= 50000 
# Related Topics 哈希表

```


遍历字符串 s ，使用哈希表统计 “各字符数量是否 > 1 ”。
再遍历字符串 s ，在哈希表中找到首个 “数量为 1的字符”，并返回。


```cpp
class Solution:
    def firstUniqChar(self, s: str) -> str:
        dicts={}
        for i in s:
            dicts[i]=dicts.get(i,0)+1
        for i in s:
            if dicts[i]==1:
                return i
        return ' '

```

# 76、Python | Leetcode二分查找和分治算法系列
﻿@Author：Runsen


今日，我决定继续更新Python教程，今天就开始了七十六、Python | Leetcode二分查找系列。




## 分治算法


分治法是把一个复杂的问题分成两个或更多的相同或相似的子问题，再把子问题分成更小的子问题
直到最后子问题可以简单的直接求解，原问题的解即子问题的解的合并。（百度百科）



利用分治策略求解时，所需时间取决于分解后子问题的个数、子问题的规模大小等因素，而二分法，由于其划分的简单和均匀的特点，是经常采用的一种有效的方法，例如二分法检索。

分治算法的基本思想：是将一个规模为N的问题分解为K个规模较小的子问题，这些子问题相互独立且与原问题性质相同。求出子问题的解，就可得到原问题的解。即一种分目标完成程序算法，简单问题可用二分法完成。

分治法所能解决的问题一般具有以下几个特征：

- 原问题于分解成的小问题具有相同的模式
- 原问题分解成的小问题可以独立求解，子问题之间没有相关性
- 具有分解终止条件，当问题足够小时，可以之间求解
- 分解出的子问题的解可以合并为该问题的解

基本步骤

- 分解，将要解决的问题划分成若干规模较小的同类问题；
- 求解，当子问题划分得足够小时，用较简单的方法解决；
- 合并，按原问题的要求，将子问题的解逐层合并构成原问题的解。

## 分治算法例子

给你一个装有1 6个硬币的袋子。1 6个硬币中有一个是伪造的，并且那个伪造的硬币比真的硬币要轻一些。你的任务是找出这个伪造的硬币。为了帮助你完成这一任务，将提供一台可用来比较两组硬币重量的仪器，利用这台仪器，可以知道两组硬币的重量是否相同。

把1 6硬币的例子看成一个大的问题。第一步，把这一问题分成两个小问题。随机选择8个硬币作为第一组称为A组，剩下的8个硬币作为第二组称为B组。这样，就把1 6个硬币的问题分成两个8硬币的问题来解决。第二步，判断A和B组中是否有伪币。可以利用仪器来比较A组硬币和B组硬币的重量。假如两组硬币重量相等，则可以判断伪币不存在。假如两组硬币重量不相等，则存在伪币，并且可以判断它位于较轻的那一组硬币中。最后，在第三步中，用第二步的结果得出原先1 6个硬币问题的答案。若仅仅判断硬币是否存在，则第三步非常简单。无论A组还是B组中有伪币，都可以推断这1 6个硬币中存在伪币。因此，仅仅通过一次重量的比较，就可以判断伪币是否存在。最终通过四次就可以找到。


## 二分法查找



算法：当数据量很大适宜采用该方法。采用二分法查找时，数据需是“有序”不重复的。二分法查找本质上就是分治算法。

基本思想：假设数据是按升序排序的，对于给定值 x，从序列的中间位置开始比较，如果当前位置值等于 x，则查找成功；若 x 小于当前位置值，则在数列的前半段中查找；若 x 大于当前位置值则在数列的后半段中继续查找，直到找到为止。

二分法查找就是查找一个数组元素的下标。定义两个变量，一个`low`，一个`high`，则`mid=(low+high)/2`。

算法核心中有三种情况：

- 如果`value==arr[mid]`，中间值正好要查找的值，则返回下标，`return mid`;

- .如果value<arr[mid]，要找的值的小于中间的值，则再往数组的小端找，`high=mid-1`;

- .如果value>arr[mid]，要找的值大于中间的值，则再往数组的大端找，`low=mid+1`;


下面代码就是二分查找的Python代码表述。我注释写清楚了。


```cpp
题目：给定n个元素，这些元素是有序的（假定为升序），使用二分法从中查找特定的元素。
要求：输入n个元素，输入某一个特定的值m，首先对n个元素进行排序（排序算法任选），输出m值的位置序号。

def binary_search(list, num):
    left = 0
    right = len(list) - 1  # 注意1 low和high用于跟踪在其中查找的列表部分
    while left <= right:  # 注意2 只有服务还没有缩小到只有一个元素，就不停的检查
        mid = (left + right) // 2
        if list[mid] == num:
            return mid
        elif list[mid] > num:
            right = mid - 1  # 注意3 猜的数字大了
        elif list[mid] < num:
            left = mid + 1   # 注意4 猜的数字小了
    return mid


A = [1, 4, 2, 5, 3, 7, 8]
num = 5
A = sorted(A)  # python 内置排序是快速排序
print(A)
print(binary_search(A, num))
```

在不存在重复元素的有序数组中，查找值等于给定值的元素。最简单的二分查找写起来确实不难，但是，二分查找的变形问题就没那么好写了。

## 二分查找的变形问题


![](https://img-blog.csdnimg.cn/20200704103152347.png)

上图是王争专栏的内容。那么我们就开始干活吧。


## LeetCode 第 704题：标准的二分查找

```cpp
给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。
示例 1:
输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4
示例 2:
输入: nums = [-1,0,3,5,9,12], target = 2
输出: -1
解释: 2 不存在 nums 中因此返回 -1
提示：
你可以假设 nums 中的所有元素是不重复的。
n 将在 [1, 10000]之间。
nums 的每个元素都将在 [-9999, 9999]之间。
```


这个代码不说了，就是一个标准的二分法。

```cpp
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # 确定查找的上下界
        low, high = 0, len(nums) - 1
        while low <= high:  # 当low == high时还剩下最后一个值需要进行检验
            mid = (low + high) // 2
            if nums[mid] < target:
                low = mid + 1  # +1是因为mid已经验证过不符合条件，新的区间又mid+1开始
            elif nums[mid] > target:
                high = mid - 1 # 这里+1同上面原因相同
            else:
                return mid
        return -1  # 执行结束但是没有找到
```



下面找到排序数组中target第一次出现的位置为例，也是二分最常见的变形。查找第一个等于给定值的元素

```cpp
nums= [1,2,2,3,3,3,4,4,5], target=4, return 6
确定返回值类型和查找范围
返回的是target在数组中的位置，即index。
查找范围：[start=0, end=len(nums)-1]

def findFirstIndex(nums, target):
    n = len(nums)
    if (nums is None or n == 0):
        return -1

    start = 0
    end = n - 1

    while (start + 1 < end):
        # 相邻就退出
        mid = start + (end - start) // 2
        if nums[mid] == target:
            end = mid
        elif nums[mid] > target:
            end = mid
        else:
            start = mid

    if nums[start] == target:
        return start

    if nums[end] == target:
        return end

    return -1

print(findFirstIndex(nums=[1, 2, 2, 3, 3, 3, 4, 4, 5], target=4))
6
```





##  LeetCode 第 34题：在排序数组中查找元素的第一个和最后一个位置


查找第一个等于给定值的元素和查找最后一个等于给定值的元素

```cpp
#给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。 
# 你的算法时间复杂度必须是 O(log n) 级别。 
# 如果数组中不存在目标值，返回 [-1, -1]
# 示例 1:
# 输入: nums = [5,7,7,8,8,10], target = 8
#输出: [3,4] 
# 示例 2: 
# 输入: nums = [5,7,7,8,8,10], target = 6
#输出: [-1,-1] 
# Related Topics 数组 二分查找
```


变形一：查找第一个等于给定值的元素
与原题区别在于，当a[mid] == value时，还需要确认是不是第一个值等于给定值的元素。

当遍历到数组第一个数，或者左边值不同时，必定是第一个，直接返回（此处同时做了溢出校验）

当不是第一个元素时，从右到左收缩区间，继续二分查找。




变形二：查找最后一个等于给定值的元素
类比变形一，变形一查找的第一个，此处查找的最后一个元素。即需要确认是不是最后一个值等于给定值的元素。

当遍历到数组最后一位，或者右边元素值不等时，必定是最后一个，返回下标。

如果不是最后一个元素，从左到右收缩区间，继续二分查找。






```cpp
class Solution:
    def searchrightRange(self,nums: List[int],target: int) ->int:
        lefts,rights = 0,len(nums)-1
        while   lefts <= rights:
            mid = (lefts+rights)//2
            if  nums[mid] > target:
                rights = mid-1
            elif    nums[mid] < target:
                lefts = mid+1
            else:
                lefts = mid+1
        if  lefts-1 >= 0 and nums[lefts-1] == target:
            return  lefts-1
        else:
            return  -1 
    def searchleftRange(self,nums: List[int],target: int) ->int:
        lefts,rights = 0,len(nums)-1
        while   lefts <= rights:
            mid = (lefts+rights)//2
            if  nums[mid] > target:
                rights = mid-1
            elif  nums[mid] < target:
                lefts = mid+1
            else:
                rights = mid-1
        if  rights+1 < len(nums) and nums[rights+1] == target:
            return  rights+1
        else:
            return  -1
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        if  len(nums) == 0:
            return  [-1,-1]
        rights = self.searchrightRange(nums,target)
        lefts = self.searchleftRange(nums,target)
        return  [lefts,rights]
```

## 查找排序数组中，第一个大于等于目标值的下标（数组中可能不存在目标值）



```cpp
'''
查找第一个大于等于给定值的元素
* 如序列：3，4，6，7，19 查找第一个大于5的元素，即为6
* 第一个大于给定值，则说明上一个小于给定值，依次判断
'''
def bsearch(a,n):
    low = 0
    high = len(a) -1
    while(low<=high):
        mid = low + ((high-low) >>1)
        if a[mid] >= n:
            if mid == 0 or a[mid - 1] < n:
                return mid
            else:
                high = mid - 1
        else:
            low = mid +1
    return -1
print(bsearch([3,4,6,7,19],5))
2
```


## 查找排序数组中，最后一个小于等于目标值的下标（数组中可能不存在目标值）


```cpp
'''
查找第一个小于给定值的元素
* 如序列：3，4，6，7，19 查找第一个小于5的元素，即为4
* 第一个大于给定值，则说明上一个小于给定值，依次判断
'''
def bsearch(a,n):
    low = 0
    high = len(a) -1
    while(low<=high):
        mid = low + ((high-low) >>1)
        if a[mid] > n:
            high = mid - 1
        else:
            if mid == n-1 or a[mid + 1] > n:
                return mid
            else:
                low = mid +1
    return -1
print(bsearch([3,4,6,7,19],5))

1
```

四个变种到此结束，Runsen原创，耗时两个小时
# 77、Python | Leetcode栈和队列系列
﻿@Author：Runsen




今日，我决定继续更新Python教程，今天就开始了七十七、Python | Leetcode栈和队列系列。


## 栈

栈 (Stack)是一种后进先出(last in first off，LIFO)的数据结构。线性表是用数组来实现的，对于栈这种只能一头插入删除的线性表来说，用数组下标为0（栈底不变，只需要跟踪栈顶的变化即可）的一端作为栈底比较合适。




![](https://img-blog.csdnimg.cn/20200705084744639.png)



列表封装的这些方法，实现栈这个常用的数据结构比较容易。栈是一种只能在列表一端进出的特殊列表，pop方法正好完美实现：


```cpp
In [1]: stack=[1,3,5]

In [2]: stack.append(0) # push元素0到尾端，不需要指定索引

In [3]: stack
Out[3]: [1, 3, 5, 0]

In [4]: stack.pop() # pop元素，不需指定索引，此时移出尾端元素
Out[4]: 0

In [5]: stack
Out[5]: [1, 3, 5]
```


由此可见Python的列表当做栈用，完全没有问题，push 和 pop 操作的时间复杂度都为 O(1)



## 队列



队列(Queue)则是一种先进先出 (fisrt in first out，FIFO)的结构.。使用顺序表存储队列时，队列元素的出队是在队头，即下标为0的地方，当有元素出队时，出队元素后面的所有元素都需要向前移动，保证队列的队头始终处在下标为0的位置，此时会大大增加时间复杂度。




![](https://img-blog.csdnimg.cn/20200705084819139.png)


使用列表模拟队列，需要借助Python的collections模块中的双端队列deque实现。如下模拟队列的先进先出，后进后出：






```cpp
In [1]: from collections import deque

In [2]: queue = [1,3,5]

In [3]: deq = deque(queue)

In [4]: deq.append(0) 

In [5]: deq
Out[5]: deque([1, 3, 5, 0]) # 后进插入到队列尾部

In [6]: deq.popleft()  
Out[6]: 1

In [7]: deq
Out[7]: deque([3, 5, 0])# 先进的先出
```


## LeetCode 第 155题：最小栈


```cpp
#设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。 
# push(x) —— 将元素 x 推入栈中。 
# pop() —— 删除栈顶的元素。 
# top() —— 获取栈顶元素。 
# getMin() —— 检索栈中的最小元素。 
# 示例: 
# 输入：
#["MinStack","push","push","push","getMin","pop","top","getMin"]
#[[],[-2],[0],[-3],[],[],[],[]]
#输出：
#[null,null,null,null,-3,null,0,-2]
#解释：
#MinStack minStack = new MinStack();
#minStack.push(-2);
#minStack.push(0);
#minStack.push(-3);
#minStack.getMin();   --> 返回 -3.
#minStack.pop();
#minStack.top();      --> 返回 0.
#minStack.getMin();   --> 返回 -2.
# 提示： 
# pop、top 和 getMin 操作总是在 非空栈 上调用。 
# Related Topics 栈 设计
```


在本题中，我们考虑使用辅助栈与数据栈同步的做法来处理。

题目中提示，pop、top 和 getMin 操作总是在 非空栈 上调用。那么我们先定义一个数据栈来实现这些功能。

题目中还要求能在常数时间内检索到最小元素的栈。在这里，我们使用辅助栈，实现辅助栈中的栈顶一直保持当前的最小值，这样就能够实现常数时间复杂度的操作。


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9hc3NldHMubGVldGNvZGUtY24uY29tL3NvbHV0aW9uLXN0YXRpYy8xNTUvMTU1X2ZpZzEuZ2lm)





```cpp
class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.data = []
        self.tmp = []


    def push(self, x: int) -> None:
        # 入栈时，同时考虑数据栈和辅助栈
        self.data.append(x)
        # 如果辅助栈为空时，或者元素比辅助栈的最顶元素小或相等时，将该元素入栈
        # 否则，将辅助栈内最顶元素再次入栈
        if len(self.tmp) == 0 or x <= self.tmp[-1]:
            self.tmp.append(x)
        else:
            self.tmp.append(self.tmp[-1])

    def pop(self) -> None:
        # if self.data:
        #     self.data.pop()
        #     self.tmp.pop()
        # 题目要求这里是在非空栈，所以不做判断
        # 如果需判断，可如上
        self.data.pop()
        self.tmp.pop()

    def top(self) -> int:
        # 需判断同 pop()
        return self.data[-1]


    def getMin(self) -> int:
        # 需判断同 pop()
        return self.tmp[-1]

# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```


## LeetCode 第 225题：用队列实现栈

```cpp
#使用队列实现栈的下列操作： 
# push(x) -- 元素 x 入栈 
# pop() -- 移除栈顶元素 
# top() -- 获取栈顶元素 
# empty() -- 返回栈是否为空 
# 注意: 
# 你只能使用队列的基本操作-- 也就是 push to back, peek/pop from front, size, 和 is empty 这些操作是合法的。 
# 你所使用的语言也许不支持队列。 你可以使用 list 或者 deque（双端队列）来模拟一个队列 , 只要是标准的队列操作即可。 
# 你可以假设所有操作都是有效的（例如, 对一个空的栈不会调用 pop 或者 top 操作）。 
# Related Topics 栈 设计
```


根据题意，我们只能使用队列的基本操作，队列因为是先进先出，要实现先进后出的栈，常见的解法方法是使用两个队列。

假设有q1，q2两个队列，我们初始化队列。


```cpp
from collections import deque
class MyStack:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.q1 = deque()
        self.q2 = deque()
```

![](https://img-blog.csdnimg.cn/20200705091105422.png)

压入栈时，加入到q1的末尾，那么q1末尾的元素就是栈顶元素


```cpp
def push(self, x: int) -> None:
    """
    Push element x onto stack.
    """
    self.q1.append(x)
```


![](https://img-blog.csdnimg.cn/20200705091145560.png)
我们需要弹出栈顶元素，也就是q1最后的元素，队列只能是先进先出，我们得用q2把q1出队的元素装着，最后一个出队元素就是栈顶元素。



```cpp
def pop(self) -> int:
    """
    Removes the element on top of the stack and returns that element.
    """
    while len(self.q1) > 1:
        self.q2.append(self.q1.popleft())
    tmp = self.q1.popleft()
    self.q2,self.q1 = self.q1, self.q2
    return tmp
```

判断是否为空，只需要判断q1




```cpp
def empty(self) -> bool:
    """
    Returns whether the stack is empty.
    """
    return not bool(self.q1)

```

取栈顶元素。这里其实可以优化，我们可以在pop时保留一个变量，不过记得在pop时需要加入栈顶元素。



```cpp
def top(self) -> int:
    ans = self.pop()
    self.q1.append(ans)
    return ans

```

下面就是完整代码

```cpp
from collections import deque
class MyStack:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.q1 = deque()
        self.q2 = deque()


    def push(self, x: int) -> None:
        """
        Push element x onto stack.
        """
        self.q1.append(x)


    def pop(self) -> int:
        """
        Removes the element on top of the stack and returns that element.
        """
        while len(self.q1) > 1:
            self.q2.append(self.q1.popleft())
        tmp = self.q1.popleft()
        self.q2,self.q1 = self.q1, self.q2
        return tmp


    def top(self) -> int:
        """
        Get the top element.
        """
        ans = self.pop()
        self.q1.append(ans)
        return ans


    def empty(self) -> bool:
        """
        Returns whether the stack is empty.
        """
        return not bool(self.q1)



# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()


```





##  LeetCode 第232题：用栈实现队列

```cpp
#使用栈实现队列的下列操作：
# push(x) -- 将一个元素放入队列的尾部。 
# pop() -- 从队列首部移除元素。 
# peek() -- 返回队列首部的元素。 
# empty() -- 返回队列是否为空。
# 示例:
# MyQueue queue = new MyQueue();
#queue.push(1);
#queue.push(2);  
#queue.peek();  // 返回 1
#queue.pop();   // 返回 1
#queue.empty(); // 返回 false
# 说明:
# 你只能使用标准的栈操作 -- 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。 
# 你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。 
# 假设所有操作都是有效的 （例如，一个空的队列不会调用 pop 或者 peek 操作）。
# Related Topics 栈 设计

```



使用list表示一个栈，只能使用栈的相关方法，如append()，pop()，s[-1]，分别是栈顶追加元素,删除栈顶元素,取出栈顶元素.。


```cpp
class MyQueue:
    def __init__(self):
        self.s = []
    def push(self, x: int) -> None:
        self.s.append(x)
    def pop(self) -> int:    
        return self.s.pop(0)
    def peek(self) -> int:
        return self.s[0]
    def empty(self) -> bool:
        return not bool(self.s)

```



当然如果使用两个栈，入队操作即追加元素，都在栈s1中操作。

出队操作首先判断缓存栈s2是否有元素，有的话直接取出s2栈顶元素；若s2为空并且s1中有元素，将s1中元素全部转移到s2中，再取出s2栈顶元素，即可模拟队列出队操作；本例中没有出现s2和s1都为空的情况。



```cpp
class MyQueue:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.s1 = []
        self.s2 = []
        
    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        self.s1.append(x)

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        if self.s2:
            return self.s2.pop()
        else:
            if  self.s1 :
                while self.s1:
                    self.s2.append(self.s1.pop())
                return self.s2.pop()

    def peek(self) -> int:
        """
        Get the front element.
        """
        if self.s2:
            return self.s2[-1]
        else:
            if  self.s1 :
                while self.s1:
                    self.s2.append(self.s1.pop())
                return self.s2[-1]

    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        if self.s1 or self.s2:
            return False
        else:
            return True

# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()

```
# 78、Python | Leetcode位运算系列
﻿@Author：Runsen






今日，我决定继续更新Python教程，今天就开始了七十八、Python | Leetcode位运算系列。



位运算，计算机内所有的数都以二进制存储，位运算是对二进制位的操作

## 按位“与”运算

按位“与”运算的运算符是：&。首先我声明一个变量i等于11，j等于2，然后我们计算i和j的按位“与”运算，也就是11&2，得到的结果是2.‘


![](https://img-blog.csdnimg.cn/2020070510172472.png)
个2是怎么来的，首先我们要把这个11和这个2全部转换成二进制，我们从上图看出11的二进制是0b1011，2的二进制是0b10。0b这个它就是一个二进制的标识位，就是告诉我们这个是二进制。

按照位“与”运算的原则，如果两个值相应的位置都为1也就是上下都为1的时候，那么该结果就是1，如果有一个不是1，那么就是0


```cpp
1011
0010
----
0010
```

所以，1011和0010的按位“与”运算就是0010,然后将二进制的0010转化为十进制，就是我们的结果2。


## 按位“或”运算

下面，我们介绍按位“或”运算。按位“或”运算的运算符是：|。我们同样计算11和2的按位“或”运算，得到的结果是11。


![](https://img-blog.csdnimg.cn/20200705101810801.png)

这个结果2到底是怎么样来进行运算的？11的二进制是1011，而2的二进制是0010。

按照位“或”运算的原则，如果两个值相应的位置有一个是1,那么该结果就是1，也就是如果都是0，该结果就是0



```cpp
1011
0010
----
1011
```



所以，1011和0010的按位“与”运算就是1011,然后将二进制的1011转化为十进制，就是我们的结果11。



## 按位“异或”运算


下面，我们介绍按位“异或”运算。按位“异或”运算的运算符是：^。我们同样计算11和2的 按位“异或”运算，得到的结果是9。

![](https://img-blog.csdnimg.cn/2020070510192190.png)


这个结果9到底是怎么样来进行运算的？11的二进制是1011，而2的二进制是0010。

按位“异或”运算的原则，如果两个值相应的位置相同1,那么该结果就是0，也就是如果都是0或者都是1，该结果就是0.同样只有是1和0，那些结果就是1


```cpp
1011
0010
----
1001
```

所以，1011和0010的按位“异或”运算就是1001,然后将二进制的1001转化为十进制，就是我们的结果9。




## 按位取反运算

下面，我们介绍按位取反运算。按位“异或”运算的运算符是：~。我们计算11的按位取反运算，得到的结果是-12。

![](https://img-blog.csdnimg.cn/20200705101955555.png)

这个结果-12到底是怎么样来进行运算的？按位取反的计算结论是：~n = -(n+1)

因此，11的按位取反运算 ：~11=-(11+1)=-12


## 左移运算符


下面，我们介绍左移运算符。左移运算符是：<<。我们计算11的左移2位的运算，得到的结果是44。
![](https://img-blog.csdnimg.cn/2020070510202930.png)

这个结果44到底是怎么样来进行运算的？左移2位，就是1011往左移动2位，然后用0来补充，变成了101100。本来在这里向左边移动，其实是后边舍弃掉2位

```cpp
1011
----
101
```


所以，1011的右移2位的”运算就是101100,然后将二进制的101100转化为十进制，就是我们的结果44。



## 右移运算符

下面，我们介绍右移运算符。右移运算符是：>>。我们计算11的右移2位的运算，得到的结果是2。

![](https://img-blog.csdnimg.cn/2020070510212065.png)





这个结果2到底是怎么样来进行运算的？右移2位，就是1011往右移动2位，然后右边的11直接去除，变成了10。本来在这里向右边移动，其实是后边删除位数。


```cpp
1011
----
10
```

所以，1011和的左移2位的”运算就是10,然后将二进制的10转化为十进制，就是我们的结果2。下表就是总结。





| 符号 | 意义       | 示例 |
| ---- | ---------- | ---- |
| ~    | 逻辑非运算 | ~a   |
| &    | 逻辑与运算 | a&b  |
| \|   | 逻辑或运算 | a\|b |
| <<   | 位左移运算 | a<<2 |
| >>   | 位右移运算 | a>>2 |


## 判断奇数还是偶数

通常判断奇数还是偶数我们想到的办法就是除以2，看余数是否为0。
Python代码如下：

```cpp
def isodd(x):
    return True if (x % 2 <> 0) else False
```

如何使用位运算呢？

我们只需要使用&运算，与1进行&，如果为1，那么该数为奇数；如果为0，那么该数是偶数，Python代码如下：

```cpp
def isodd(x):
    return True if (x & 1) else False
```

## 左移一位相当于乘以2，右移一位相当于除以2


在面试的过程中，通常会遇到的一个问题是写二分查找代码。
二分查找的代码如下：

```cpp
def binary_search(list, item):
    '''
    :param list: 有序列表
    :param item: 要查找的元素
    :return: item在list中的索引，若不在list中返回None
    '''
    low = 0
    high = len(list) - 1
    while low <= high:
        midpoint = (low + high) // 2
        if list[midpoint] == item:
            return midpoint
        elif list[midpoint] < item:
            low = midpoint + 1
        elif list[midpoint] > item:
            high = midpoint - 1
    return None
```

其中有一步是需要取最小小标和最大下标的中间值，若使用位运算符，midpoint = (low + high) >> 1，面试官肯定会对你刮目相看。

## 数值交换

数值交换的代码相信大家都非常熟悉了，因为似乎是从学编程语言的最开始就一直用：

```cpp
temp = b
b = a
a = temp
# a,b =b,a

```

但是怎么使用位运算来完成此功能呢？

```cpp
a ^= b
b ^= a
a ^= b

```

确实比较难理解，原理是什么呢？
第一行，a = a ^ b，很容易理解；
第二行， b = b ^ a = b ^ a ^ b，由于 b ^ b = 0，所以 b = a ^ 0，即 b = a;
第三行， a = a ^ b ,由于a在第一步重新赋值，所以，a =  a ^ b ^ a = b，完成了数值交换。

下面就是位运算常见用法总结

**判断x的奇偶数**

```cpp
x % 2 == 1 // 常规写法
x & 1 == 1 // 为真奇数，为假偶数

```





**计算中位数**


```cpp
mid = (left + right) / 2  // 常规写法
mid  = (left + right) >> 1 // 位运算

```

**交换两个数**


```cpp
a ^= b
b ^= a
a ^= b

```


## LeetCode 第 78题：子集

```cpp
#给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。 
# 说明：解集不能包含重复的子集。 
# 示例: 
# 输入: nums = [1,2,3]
#输出:
#[
#  [3],
#  [1],
#  [2],
#  [1,2,3],
#  [1,3],
#  [2,3],
#  [1,2],
#  []
#] 
# Related Topics 位运算 数组 回溯算法

```

既然这道题让我们求的是所有的子集，那么我们可以从子集的特点入手。我们之前学过，一个含有n个元素的子集的数量是$2^n$。

使用位运算，对每一位为1的表示这一位的数字存在，例如对于输入[1,2,3] 编码i=001，表示只含有3，编码i=101.表示含有1,3



```cpp
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        ret = []
        n = len(nums)
        # 遍历所有的状态
        # 1左移n位相当于2的n次方
        for s in range(1 << n):
            cur = []
            # 通过位运算找到每一位是0还是1
            for i in range(n):
                # 判断s状态在2的i次方上，也就是第i位上是0还是1
                if s & (1 << i):
                    cur.append(nums[i])
            ret.append(cur[:])
        return ret

```
# 79、Python | Leetcode 二叉树系列（上篇）

@Author：Runsen




今日，我决定继续更新Python教程，今天就开始了七十九、Python | Leetcode 二叉树系列（上篇）。作为一名 Python 程序员，如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。








## 树

树形结构本身具有递归的性质(在其后的编程中体现的淋漓尽致)；树是一种非常重要的非线性结构。

![](https://img-blog.csdnimg.cn/20190528213911826.png)

看下图，A 节点就是 B 节点的父节点，B 节点是 A 节点的子节点.。B、C、D 这三个节点的父节点是同一个节点A，，没有父节点的叫做根节点，也就是 E 。


![](https://img-blog.csdnimg.cn/20190528214008172.png)

没有子节点的节点叫作叶子节点或者叶节点，图中的G，H，I，J，K，L




关于“树”，还有三个比较相似的概念：高度（Height）、深度（Depth），层（level）

![](https://img-blog.csdnimg.cn/20190528214548574.png)

![](https://img-blog.csdnimg.cn/20190528214558681.png)

## 二叉树（binary Tree）

二叉树是n(n>=0)个结点的有限集合，该集合或者为空集（称为空二叉树），或者由一个根结点和两棵互不相交的、分别称为根结点的左子树和右子树组成。


![](https://img-blog.csdnimg.cn/2019052821483629.png)

上图中，有两个二叉树，分别是 编号2和 3。

编号2又是满二叉树

满二叉树：在一棵二叉树中。如果所有分支结点都存在左子树和右子树，并且所有叶子都在同一层上，这样的二叉树称为满二叉树。

满二叉树的特点有：


- 叶子只能出现在最下一层。出现在其它层就不可能达成平衡。
- 非叶子结点的度一定是2。
- 在同样深度的二叉树中，满二叉树的结点个数最多，叶子数最多。



编号3是完全二叉树

**对一颗具有n个结点的二叉树按层编号，如果编号为i(1<=i<=n)的结点与同样深度的满二叉树中编号为i的结点在二叉树中位置完全相同，则这棵二叉树称为完全二叉树。**


就是保证叶子节点的上面层都要达到最大，最低下两层，最后一层的叶子节点都靠左排列


![](https://img-blog.csdnimg.cn/20190528215115835.png)

存储二叉树的方法就是链表和数组，下图是通过链表的方法存储二叉树
![](https://img-blog.csdnimg.cn/20190528215507935.png)
通过数组的方法也可以存储二叉树

![](https://img-blog.csdnimg.cn/20190528215553943.png)

对于非完全二叉树，其实用数组的方法会浪费存储空间

![](https://img-blog.csdnimg.cn/20190528215743499.png)

二叉树具备以下数学性质：

- 在二叉树的第i层上至多有$2^(i-1)$个结点（i>0）
- 深度为k的二叉树至多有$2^k - 1$个结点（k>0）
- 对于任意一棵二叉树，如果其叶结点数为N0，而度数为2的结点总数为N2，则$N0=N2+1$;
- 具有n个结点的完全二叉树的深度必为 $log2(n+1)$




## 二叉树的遍历

二叉树的遍历是指从二叉树的根结点出发，按照某种次序依次访问二叉树中的所有结点，使得每个结点被访问一次，且仅被访问一次。




- 中序遍历：先左子树，再根节点，最后右子树
- 前序遍历：先根节点，再左子树，最后右子树
- 后序遍历：先左子树，再右子树，最后根节点。

前序遍历通俗的说就是从二叉树的根结点出发，当第一次到达结点时就输出结点数据，按照先向左在向右的方向访问。

中序遍历就是从二叉树的根结点出发，当第二次到达结点时就输出结点数据，按照先向左在向右的方向访问。

后序遍历就是从二叉树的根结点出发，当第三次到达结点时就输出结点数据，按照先向左在向右的方向访问。



![](https://img-blog.csdnimg.cn/20190528215926380.png)




删除共有三种情况

- 被删除的节点是叶子节点，这时候只要把这个节点删除，再把指向这个节点的父节点指针置为空就行

- 被删除的节点有左子树，或者有右子树，而且只有其中一个，那么只要把当前删除节点的父节点指向被删除节点的左子树或者右子树就行。

- 如果要删除的节点有两个子节点，需要找到这个节点的右子树的最小节点，把它替换到要删除的节点上，然后再删除掉这个最小节点，因为最小节点肯定没有左子节点

![](https://img-blog.csdnimg.cn/20190528221128581.png)

## 实现二叉树


上面就是二叉树全部内容，下面用Pytho代码具体实现二叉树。







按下来就是编程实现了，请动手自己实现一把。

先实现一个 node 类：

```cpp
class Node(object):
    def __init__(self, item):
        self.item = item
        self.left = None
        self.right = None

    def __str__(self):
        return str(self.item)
```


这里的 `__str__` 方法是为了方便打印。在 print 一个 Node 类时会打印` __str__ `的返回值,例如：print(Node(5)) 就会打印出字符串 5 。

实现一个二叉树类：



```cpp
class Tree(object):
    def __init__(self):
        # 根节点定义为 root 永不删除，做为哨兵使用。
        self.root = Node('root')

    def add(self, item):
        node = Node(item)
        if self.root is None:
            self.root = node
        else:
            q = [self.root]

            while True:
                pop_node = q.pop(0)
                if pop_node.left is None:
                    pop_node.left = node
                    return
                elif pop_node.right is None:
                    pop_node.right = node
                    return
                else:
                    q.append(pop_node.left)
                    q.append(pop_node.right)

    def get_parent(self, item):
        '''
        找到 Item 的父节点
        '''
        if self.root.item == item:
            return None  # 根节点没有父节点
        tmp = [self.root]
        while tmp:
            pop_node = tmp.pop(0)
            if pop_node.left and pop_node.left.item == item:
                return pop_node
            if pop_node.right and pop_node.right.item == item:
                return pop_node
            if pop_node.left is not None:
                tmp.append(pop_node.left)
            if pop_node.right is not None:
                tmp.append(pop_node.right)
        return None

    def delete(self, item):
        '''
        从二叉树中删除一个元素
        先获取 待删除节点 item 的父节点
        如果父节点不为空，
            判断 item 的左右子树
            如果左子树为空，那么判断 item 是父节点的左孩子，还是右孩子，如果是左孩子，将父节点的左指针指向 item 的右子树，反之将父节点的右指针指向 item 的右子树
            如果右子树为空，那么判断 item 是父节点的左孩子，还是右孩子，如果是左孩子，将父节点的左指针指向 item 的左子树，反之将父节点的右指针指向 item 的左子树
            如果左右子树均不为空，寻找右子树中的最左叶子节点 x ，将 x 替代要删除的节点。
        删除成功，返回 True
        删除失败, 返回 False

        '''
        if self.root is None:  # 如果根为空，就什么也不做
            return False

        parent = self.get_parent(item)
        if parent:
            del_node = parent.left if parent.left.item == item else parent.right  # 待删除节点
            if del_node.left is None:
                if parent.left.item == item:
                    parent.left = del_node.right
                else:
                    parent.right = del_node.right
                del del_node
                return True
            elif del_node.right is None:
                if parent.left.item == item:
                    parent.left = del_node.left
                else:
                    parent.right = del_node.left
                del del_node
                return True
            else:  # 左右子树都不为空
                tmp_pre = del_node
                tmp_next = del_node.right
                if tmp_next.left is None:
                    # 替代
                    tmp_pre.right = tmp_next.right
                    tmp_next.left = del_node.left
                    tmp_next.right = del_node.right

                else:
                    while tmp_next.left:  # 让tmp指向右子树的最后一个叶子
                        tmp_pre = tmp_next
                        tmp_next = tmp_next.left
                    # 替代
                    tmp_pre.left = tmp_next.right
                    tmp_next.left = del_node.left
                    tmp_next.right = del_node.right
                if parent.left.item == item:
                    parent.left = tmp_next
                else:
                    parent.right = tmp_next
                del del_node
                return True
        else:
            return False

    def traverse(self):  # 层次遍历
        if self.root is None:
            return None
        q = [self.root]
        res = [self.root.item]
        while q != []:
            pop_node = q.pop(0)
            if pop_node.left is not None:
                q.append(pop_node.left)
                res.append(pop_node.left.item)

            if pop_node.right is not None:
                q.append(pop_node.right)
                res.append(pop_node.right.item)
        return res

    def preorder(self, root):  # 先序遍历
        if root is None:
            return []
        result = [root.item]
        left_item = self.preorder(root.left)
        right_item = self.preorder(root.right)
        return result + left_item + right_item

    def inorder(self, root):  # 中序序遍历
        if root is None:
            return []
        result = [root.item]
        left_item = self.inorder(root.left)
        right_item = self.inorder(root.right)
        return left_item + result + right_item

    def postorder(self, root):  # 后序遍历
        if root is None:
            return []
        result = [root.item]
        left_item = self.postorder(root.left)
        right_item = self.postorder(root.right)
        return left_item + right_item + result
```

运行测试：

```cpp
if __name__ == '__main__':
    t = Tree()
    for i in range(10):
        t.add(i)
    print('层序遍历:', t.traverse())
    print('先序遍历:', t.preorder(t.root))
    print('中序遍历:', t.inorder(t.root))
    print('后序遍历:', t.postorder(t.root))

    for i in range(10):
        print(i, " 的父亲", t.get_parent(i))

    for i in range(0, 15, 3):
        print(f"删除 {i}", '成功' if t.delete(i) else '失败')
        print('层序遍历:', t.traverse())
        print('先序遍历:', t.preorder(t.root))
        print('中序遍历:', t.inorder(t.root))
        print('后序遍历:', t.postorder(t.root))
```

执行结果如下：


```cpp
层序遍历: ['root', 0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
先序遍历: ['root', 0, 2, 6, 7, 3, 8, 9, 1, 4, 5]
中序遍历: [6, 2, 7, 0, 8, 3, 9, 'root', 4, 1, 5]
后序遍历: [6, 7, 2, 8, 9, 3, 0, 4, 5, 1, 'root']
0  的父亲 root
1  的父亲 root
2  的父亲 0
3  的父亲 0
4  的父亲 1
5  的父亲 1
6  的父亲 2
7  的父亲 2
8  的父亲 3
9  的父亲 3
删除 0 成功
层序遍历: ['root', 8, 1, 2, 3, 4, 5, 6, 7, 9]
先序遍历: ['root', 8, 2, 6, 7, 3, 9, 1, 4, 5]
中序遍历: [6, 2, 7, 8, 3, 9, 'root', 4, 1, 5]
后序遍历: [6, 7, 2, 9, 3, 8, 4, 5, 1, 'root']
删除 3 成功
层序遍历: ['root', 8, 1, 2, 9, 4, 5, 6, 7]
先序遍历: ['root', 8, 2, 6, 7, 9, 1, 4, 5]
中序遍历: [6, 2, 7, 8, 9, 'root', 4, 1, 5]
后序遍历: [6, 7, 2, 9, 8, 4, 5, 1, 'root']
删除 6 成功
层序遍历: ['root', 8, 1, 2, 9, 4, 5, 7]
先序遍历: ['root', 8, 2, 7, 9, 1, 4, 5]
中序遍历: [2, 7, 8, 9, 'root', 4, 1, 5]
后序遍历: [7, 2, 9, 8, 4, 5, 1, 'root']
删除 9 成功
层序遍历: ['root', 8, 1, 2, 4, 5, 7]
先序遍历: ['root', 8, 2, 7, 1, 4, 5]
中序遍历: [2, 7, 8, 'root', 4, 1, 5]
后序遍历: [7, 2, 8, 4, 5, 1, 'root']
删除 12 失败
层序遍历: ['root', 8, 1, 2, 4, 5, 7]
先序遍历: ['root', 8, 2, 7, 1, 4, 5]
中序遍历: [2, 7, 8, 'root', 4, 1, 5]
后序遍历: [7, 2, 8, 4, 5, 1, 'root']
```



Binarytree是一个Python库，它通过一个简单的API生成二叉树，可以进行检查和操作。Github：https://github.com/joowani/binarytree/releases。


![](https://img-blog.csdnimg.cn/20200705112838888.png)

# 80、Python _ Leetcode 二叉树系列（中篇）
@Author：Runsen


今日，我决定继续更新Python教程，今天就开始了八十、Python | Leetcode 二叉树系列（中篇）。作为一名 Python 程序员，如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。





## LeetCode 第 102题：二叉树的层次遍历

```cpp
#给你一个二叉树，请你返回其按 层序遍历 得到的节点值。 （即逐层地，从左到右访问所有节点）。 
# 示例： 
#二叉树：[3,9,20,null,null,15,7], 
#     3
#   / \
#  9  20
#    /  \
#   15   7
# 返回其层次遍历结果： 
# [
#  [3],
#  [9,20],
#  [15,7]
#]
# Related Topics 树 广度优先搜索
```


  对于这道二叉树题目，我们要遍历每一层的每一个节点，可以考虑分别用BFS（广度优先搜索）和DFS（深度优先搜索）来解决，下面先简单介绍BFS，后续文章继续深入。





 BFS对二叉树按照层进行搜索，搜索逻辑如下图所示： 


![](https://img-blog.csdnimg.cn/20200706111902741.png)


 根据我们熟悉的BFS搜索方法，运用队列来实现，把每个没有搜索到的点依次放入队列，然后再弹出队列的头部元素作为当前遍历节点，并进行记录。接下来对此节点的所有相邻节点进行搜索，将所有有效且未被访问过的节点压入队列中。



```cpp
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
from collections import deque

class Solution(object):
    def levelOrder(self, root):
        res = []
        if root is None:
            return res
        q = deque([root])
        res.append([root.val])
        while q:
            size = len(q)
            level = []
            for i in range(size):
                node = q.popleft()
                if node.left != None:
                    q.append(node.left)
                    level.append(node.left.val)
                if node.right != None:
                    q.append(node.right)
                    level.append(node.right.val)
            if level:
                res.append(level)
        return res

```






## LeetCode 第 104题：二叉树的最大深度


```cpp
#给定一个二叉树，找出其最大深度。 
# 二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。 
# 说明: 叶子节点是指没有子节点的节点。 
# 示例： 
#给定二叉树 [3,9,20,null,null,15,7]， 
#     3
#   / \
#  9  20
#    /  \
#   15   7 
# 返回它的最大深度 3 。 
# Related Topics 树 深度优先搜索
```

看到该题目，首先想到的是使用递归来实现，递归的基本条件是访问到根节点（左右子树为空）；递归条件是访问左子树或右子树；中间处理逻辑是将子树深度+1，即为最终深度。

```cpp
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
	# 简化的递归
	def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        return max(self.maxDepth(root.left), self.maxDepth(root.right))+1
	def maxDepth(self, root: TreeNode) -> int:  
		if not root: return 0 
		# 分别得到左右子树的最大深度
		left = self.maxDepth(root.left)    
		right = self.maxDepth(root.right)    
		return max(left, right) +1
```




## LeetCode 第 107题：二叉树的层次遍历 II



```cpp
#给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历） 
#
# 例如： 
#给定二叉树 [3,9,20,null,null,15,7], 
#     3
#   / \
#  9  20
#    /  \
#   15   7
# 返回其自底向上的层次遍历为： 
# [
#  [15,7],
#  [9,20],
#  [3]
#]
# Related Topics 树 广度优先搜索

```




和LeetCode 第 102题：二叉树的层次遍历完全一样，就是最后的结果改为`return res[::-1]`

```cpp
class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        res = []
        if root is None:
            return res
        q = deque([root])
        res.append([root.val])
        while q:
            size = len(q)
            level = []
            for i in range(size):
                node = q.popleft()
                if node.left != None:
                    q.append(node.left)
                    level.append(node.left.val)
                if node.right != None:
                    q.append(node.right)
                    level.append(node.right.val)
            if level:
                res.append(level)
        return res[::-1]
```





## LeetCode 第 110题：平衡二叉树



```cpp
#给定一个二叉树，判断它是否是高度平衡的二叉树。 
# 本题中，一棵高度平衡二叉树定义为： 
# 一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。 
# 示例 1: 
# 给定二叉树 [3,9,20,null,null,15,7] 
#
#     3
#   / \
#  9  20
#    /  \
#   15   7 
# 返回 true 。 
#示例 2: 
# 给定二叉树 [1,2,2,3,3,null,null,4,4] 
#
#        1
#      / \
#     2   2
#    / \
#   3   3
#  / \
# 4   4
# 返回 false 。 
# Related Topics 树 深度优先搜索
```


定义一个获取当前节点高度的方法, 可以参考上面：二叉树的最大深度

左右两个子树的高度差的绝对值超过1，则为false

如果当前节点的左右子树满足高度差的绝对值不超过1，则需要继续判断其左右子树分别是否是平衡二叉树。


对于每个节点，左子树和右子树都是平衡树，并且得到左子树和右子树的高度，只要高度差小于1，则为true。



```cpp
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        if not root: return True
        return abs(self.depth(root.left) - self.depth(root.right)) <= 1 and \
            self.isBalanced(root.left) and self.isBalanced(root.right)

    def depth(self, root):
        if not root: return 0
        return max(self.depth(root.left), self.depth(root.right)) + 
```

但是时间复杂度却是$O(n^2)$，可以采用DFS（深度优先搜索）



- 对二叉树做深度优先遍历DFS，递归过程中：
- 终止条件：当DFS越过叶子节点时，返回高度0；
- 返回值：从底至顶，返回以每个节点root为根节点的子树最大高度(左右子树中最大的高度值加1max(left,right) + 1)；

- 当我们发现有一例 左/右子树高度差 ＞ 1 的情况时，代表此树不是平衡树，返回-1；

- 当发现不是平衡树时，后面的高度计算都没有意义了，因此一路返回-1，避免后续多余计算。
  最差情况是对树做一遍完整DFS，时间复杂度为 O(N)。





```cpp
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        return self.depth(root) != -1

    def depth(self, root):
        if not root: return 0
        left = self.depth(root.left)
        if left == -1: return -1
        right = self.depth(root.right)
        if right == -1: return -1
        return max(left, right) + 1 if abs(left - right) < 2 else -1J

```
# 81、Python | Leetcode 二叉树系列（下篇）


@Author：Runsen






今日，我决定继续更新Python教程，今天就开始了八十一、Python | Leetcode 二叉树系列（下篇）。作为一名 Python 程序员，如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。




##  LeetCode 第 94题：二叉树的中序遍历



```cpp
#给定一个二叉树，返回它的中序 遍历。 
# 示例: 
# 输入: [1,null,2,3]
#   1
#    \
#     2
#    /
#   3
#输出: [1,3,2] 
# 进阶: 递归算法很简单，你可以通过迭代算法完成吗？ 
# Related Topics 栈 树 哈希表

```


递归：中序遍历的顺序是左根右。使用递归解题，条件是：当前节点为空则返回；递归条件是遍历其左右子节点。先访问左子节点，接着将当前节点的值添加到结果数组，然后访问右子节点。



栈的题解：首先访问左子树，将左子树存入栈中，每次将栈顶元素存入结果，如果右子树为空，取出栈顶元素，如果当前元素为栈顶元素右子树，一直弹出至当前元素不为栈顶元素右子树(此处说明访问右子树，根节点已经被访问过，弹出即可)。如果节点右子树不为空，访问右子树，继续循环遍历左子树，存入栈中。






```cpp
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        def helper(root):
            if not root:
                return 
            helper(root.left)
            res.append(root.val)
            helper(root.right)
        helper(root)
        return res

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        res = []  #结果列表
        stack = []  #辅助栈
        cur = root  #当前节点
        while stack or cur:
            while cur:  #一直遍历到最后一层
                res.append(cur.val)  
                stack.append(cur)
                cur = cur.left
            top = stack.pop()  #此时该节点的左子树已经全部遍历完
            cur = top.right  #对右子树遍历
        return res

```


##  LeetCode 第 98题：验证二叉搜索树



```cpp
#给定一个二叉树，判断其是否是一个有效的二叉搜索树。 
# 假设一个二叉搜索树具有如下特征： 
# 节点的左子树只包含小于当前节点的数。 
# 节点的右子树只包含大于当前节点的数。 
# 所有左子树和右子树自身必须也是二叉搜索树。 
# 示例 1: 
# 输入:
#    2
#   / \
#  1   3
#输出: true
# 示例 2: 
# 输入:
#    5
#   / \
#  1   4
#     / \
#    3   6
#输出: false
#解释: 输入为: [5,1,4,null,null,3,6]。
#     根节点的值为 5 ，但是其右子节点值为 4 。
# Related Topics 树 深度优先搜索

```


做这题，需要了解二叉搜索树的特点：

- 当前节点的左子树的所有节点的值都应该小于当前节点的值；
- 当前节点的右子树的所有节点的值都应该大于当前节点的值

为了简便，我们可以这么做：

在之前中介绍过二叉搜索树一个很重要的定义就是，对一棵二叉搜索树进行中序遍历(左->根->右)，遍历所得的节点序列是一个升序排列的序列。所以我们可以利用二叉搜索树的这个性质，来判断一个二叉搜索树是否合法，就是上面那题的变形。





![](https://img-blog.csdnimg.cn/20200706125032900.png)

```cpp
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:      
        #中序遍历，观察到中序遍历的顺序是左->中->右,也就是按照从小到大的顺序，因此这样思考题目就很好解了,按照中序遍历，将值依次存入列表中。最后判断
        if not root:
            return True
        result = []
        def middle_traversal(root):
            if root.left:
                middle_traversal(root.left)
            result.append(root.val)
            if root.right:
                middle_traversal(root.right)
        middle_traversal(root)
        return result == sorted(result) and len(set(result)) == len(result)

# 下面是栈的题解
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        stack, preNum = [], float("-inf")
        while len(stack) > 0 or root:
            if root:
                stack.append(root)
                root = root.left
            else:
                root = stack.pop()
                if root.val <= preNum:
                    return False
                preNum = root.val
                root = root.right
        return True

```




##  LeetCode 第 105题：从前序与中序遍历序列构造二叉树




```cpp
#根据一棵树的前序遍历与中序遍历构造二叉树。 
# 注意: 
#你可以假设树中没有重复的元素。 
# 例如，给出
# 前序遍历 preorder = [3,9,20,15,7]
#中序遍历 inorder = [9,3,15,20,7] 
# 返回如下的二叉树： 
#
#     3
#   / \
#  9  20
#    /  \
#   15   7 
# Related Topics 树 深度优先搜索 数组

```



二叉树前序遍历：

- 先遍历根节点
- 再递归遍历左子树
- 最后递归遍历右子树

二叉树中序遍历：

- 先递归遍历左子树
- 再遍历根节点
- 最后递归遍历右子树

二叉树后序遍历：

- 先递归遍历左子树
- 再递归遍历右子树
- 最后遍历根节点

前序遍历和中序遍历二者之间的联系，二者相同的纽带为根节点，因此我们可以通过在前序遍历中定位到根节点，然后从中序遍历中根节点找到对应的index，从而可以知道左右子树分别的节点数目


```cpp
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        if not preorder or not inorder:
            return None
        root = TreeNode(preorder[0])
        index = inorder.index(preorder[0])
        root.left = self.buildTree(preorder[1:index+1], inorder[:index])
        root.right = self.buildTree(preorder[index+1:], inorder[index+1:])
        return root

```

##  LeetCode 第 106题：从中序与后序遍历序列构造二叉树


```cpp
#根据一棵树的中序遍历与后序遍历构造二叉树。 
# 注意: 
#你可以假设树中没有重复的元素。
# 例如，给出 
# 中序遍历 inorder = [9,3,15,20,7]
#后序遍历 postorder = [9,15,7,20,3] 
# 返回如下的二叉树： 
#     3
#   / \
#  9  20
#    /  \
#   15   7
# Related Topics 树 深度优先搜索 数组

```

道理和上面的一样，从后序遍历中定位到根节点，然后从中序遍历中根节点找到对应的index，从而可以知道左右子树分别的节点数目。

```cpp
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> TreeNode:
        # 实际上inorder 和 postorder一定是同时为空的，因此你无论判断哪个都行
        if not inorder:
            return None
        root = TreeNode(postorder[-1])
        i = inorder.index(root.val)
        root.left = self.buildTree(inorder[:i], postorder[:i])
        root.right = self.buildTree(inorder[i+1:], postorder[i:-1])
        return root

```

# 82、Python |  Leetcode贪心算法系列

@Author：Runsen


今日，我决定继续更新Python教程，今天就开始了八十二、Python | Leetcode贪心算法系列。



## 贪心算法

贪心算法（又称贪婪算法）是指，在对问题求解时，总是做出在当前看来是最好的选择。也就是说，不从整体最优上加以考虑，他所做出的是在某种意义上的局部最优解。

假设我们有一个100kg的背包，可以装飞中物品，如何将所装的物品总价值最大

![](https://img-blog.csdnimg.cn/20190530163620439.png)

**答案 ：20kg 黑豆 ，30kg 绿豆 ，50kg 红豆**


贪心算法的基本思路是从问题的某一个初始解出发一步一步地进行，根据某个优化测度，每一步都要确保能获得局部最优解。每一步只考虑一个数据，他的选取应该满足局部优化的条件。若下一个数据和部分最优解连在一起不再是可行解时，就不把该数据添加到部分解中，直到把所有数据枚举完，或者不能再添加算法停止

贪心算法的解题步骤


- 建立数学模型来描述问题；
- 把求解的问题分成若干个子问题；
- 对每一子问题求解，得到子问题的局部最优解；
- 把子问题的解局部最优解合成原来解问题的一个解。



在比如，有一个有权图，从顶点S开始，照样一条到顶点T的最短路径


贪心算法的解决思路

每次选择一条跟当前相连的权最小的边，直到找出顶点T。

求出的最短路径S ->A->E->T，路径长度1+4+4 =9
![](https://img-blog.csdnimg.cn/20190530163946940.png)
但是贪心选择的方法，求的路径并不是最短路径  S- >B ->D->T 才是最短路径

因为前面的选择会影响后面的选择，导致每一步的选择都很糟糕，最终无法得到全局最优解

生活中常见的贪心算法就是钱币付钱


肯定先用最大的100来付钱，如果不够，就用50，最后剩下的用1元来补齐

1.贪婪算法可以寻找局部最优解，并尝试与这种方式获得全局最优解

2.得到的可能是近似最优解，但也可能便是最优解(区间调度问题，最短路径问题(广度优先、狄克斯特拉))

3.对于完全NP问题，目前并没有快速得到最优解的解决方案

4.面临NP完全问题，最佳的做法就是使用近似算法

5.贪婪算法(近似算法)在大部分情况下易于实现，并且效率不错



举个简单的例子，比如给定某个数字的金额（如 250）与 100, 50, 10, 5, 1 这些纸币（不限量），怎么能用最少张的纸币来兑换这张金额呢，显然每次兑换应该先从大额的纸币兑换起，第一次选 100， 第二次还是选 100， 第三次选第二大的 50 元，每次都选小于剩余金额中的最大面额的纸币，这样得出的解一定是全局最优解！时间复杂度无疑是线性的。



## 最大和的连续子数组


我不知道这题是不是Leetcode，但出现的频率很高。好像是牛课的，反正是一个面试题。

```csharp
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
示例:
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组[4,-1,2,1] 的和最大，为 6。
```



第一时间想到的当然是暴力解决，基本思路就是遍历一遍，用两个变量，一个记录最大的和，一个记录当前的和。后面发现可以用贪心算法来解比较简单其基本思路是正在访问的节点值+此节点之前的最大值如果大于当前节点，则更新最大值为和，否则更新最大值为当前节点。


```csharp
nums=[-2,1,-3,4,-1,2,1,-5,4]
tmp = nums[0]
max_ = tmp
n = len(nums)
for i in range(1,n):
    # 当当前序列加上此时的元素的值大于tmp的值，说明最大序列和可能出现在后续序列中，记录此时的最大值
   if tmp + nums[i]>nums[i]:
       max_ = max(max_, tmp+nums[i])
       tmp = tmp + nums[i]
   else:
       #当tmp(当前和)小于下一个元素时，当前最长序列到此为止。以该元素为起点继续找最大子序列,
        # 并记录此时的最大值
       max_ = max(max_, tmp, tmp+nums[i],  nums[i])
       tmp = nums[i]
print(max_)
```

贪心算法的代码

```csharp
nums=[-2,1,-3,4,-1,2,1,-5,4]
lenth = len(nums)
cur_sum=max_sum = nums[0]
for i in range(1,lenth):
	cur_sum = max(cur_sum+nums[i],  nums[i])
	max_sum = max(cur_sum, max_sum)
print(max_sum)
```

我们再看一个场景，这是一个求得最优解的贪心算法例子。

场景：一名收银员，需要找零 88元。怎么找零，所需要的纸/硬币的数量最少。

思路：依次找最大的纸币， 例如：找零88元， ¥88 = ¥50 + ¥20 + ¥10 + ¥5 + ¥1 * 3


```csharp
# arr的每一位：分别对应100块、50块、20块、10块、5块、1块纸币。
arr = [0,0,0,0,0,0]

def change(money):
    while money >= 1:
        if money >= 100:
            money -= 100
            arr[0] += 1
        elif money >= 50:
            money -= 50
            arr[1] += 1
        elif money >= 20:
            money -= 20
            arr[2] += 1
        elif money >= 10:
            money -= 10
            arr[3] += 1
        elif money >= 5:
            money -= 5
            arr[4] += 1
        elif money >= 1:
            money -= 1
            arr[5] += 1

change(88)
print(arr)
```


![](https://img-blog.csdnimg.cn/20200706223658121.png)


## LeetCode 第 55题：跳跃游戏



```csharp
#给定一个非负整数数组，你最初位于数组的第一个位置。 
# 数组中的每个元素代表你在该位置可以跳跃的最大长度。 
# 判断你是否能够到达最后一个位置。 
# 示例 1:
# 输入: [2,3,1,1,4]
#输出: true
#解释: 我们可以先跳 1 步，从位置 0 到达 位置 1, 然后再从位置 1 跳 3 步到达最后一个位置。
# 示例 2: 
# 输入: [3,2,1,0,4]
#输出: false
#解释: 无论怎样，你总会到达索引为 3 的位置。但该位置的最大跳跃长度是 0 ， 所以你永远不可能到达最后一个位置。
# Related Topics 贪心算法 数组
```


从第i个位置，最远可跳nums[i]步：nums=[2,3,1,1,4,...];我们假设从第i个位置，最远可跳至第index[i]个位置，则index[i] = i + nums[i];

若从第0个位置最远可跳至第i个位置；则从第0个位置也一定可以跳至：第1个位置、第2个位置、...、第i-1个位置。从第0个位置，应该跳至第1、第2、...、第i-1个位置中的哪一个呢？

应该调至第1、2、...、i-1、i位置中，又可向前跳至最远位置（即index[1]、index[2]、...、index[i-1] 和 index[i] 最大的那个）（贪心算法的思想）

**算法步骤：**

- 求从第i个位置最远可跳至第index[i]位置；

- 根据从第i位置最远可跳nums[i]步：index[i] = nums[i] + i;

- 初始化：设置变量i代表当前所处的位置，初始化为0；设置变量max_index代表从第0位置至第i位置的这个过程中，最远可到达的位置，初始化为index[0]。
- 利用i扫描index数组，直到i到达index数组尾部或i超过max_index，扫描过程中，更新max_index.

- 若最终 i 为数组长度，则返回true，否则返回false。



```csharp
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        farthest = nums[0]
        for i in range(len(nums)):
            if i <= farthest:
                farthest = max(i+nums[i], farthest)
        return len(nums)-1 <= farthest
```


## LeetCode 第 122题： 买卖股票的最佳时机 II




```csharp
#给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。 
# 设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。 
# 注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。 
# 示例 1: 
# 输入: [7,1,5,3,6,4]
#输出: 7
#解释: 在第 2 天（股票价格 = 1）的时候买入，在第 3 天（股票价格 = 5）的时候卖出, 这笔交易所能获得利润 = 5-1 = 4 。
#     随后，在第 4 天（股票价格 = 3）的时候买入，在第 5 天（股票价格 = 6）的时候卖出, 这笔交易所能获得利润 = 6-3 = 3 。
# 示例 2: 
# 输入: [1,2,3,4,5]
#输出: 4
#解释: 在第 1 天（股票价格 = 1）的时候买入，在第 5 天 （股票价格 = 5）的时候卖出, 这笔交易所能获得利润 = 5-1 = 4 。
#     注意你不能在第 1 天和第 2 天接连购买股票，之后再将它们卖出。
#     因为这样属于同时参与了多笔交易，你必须在再次购买前出售掉之前的股票。
# 示例 3: 
# 输入: [7,6,4,3,1]
#输出: 0
#解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。 
# 提示： 
# 1 <= prices.length <= 3 * 10 ^ 4 
# 0 <= prices[i] <= 10 ^ 4 
# Related Topics 贪心算法 数组
```

 虽然题目看似复杂, 但真正完成的时候你会发现这道题是纸老虎。于是题目的思路就是遍历整个数组, 预测 i+1 个交易日比 i 高即可卖出, 累加利润; 否则跳过这个交易日. 什么?你觉得不可能这么简单? 事实就是这么简单!



```csharp
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        # return sum([max(prices[i+1] - prices[i],0) for i in range(len(prices)-1)])
        return sum([prices[i+1]-prices[i] if prices[i+1]-prices[i] > 0 else 0 for i in range(len(prices)-1)])
        # return sum([y - x for x, y in zip(prices[:-1], prices[1:]) if x < y])
```

# 83、Python _ Leetcode双指针系列


@Author：Runsen



今天高考，当年我就是一个辣鸡，现在还是一个辣鸡，祝高考的个个清华北大。辣鸡的我决定继续更新Python教程，今天就开始了八十三、Python | Leetcode双指针系列。


## 双指针

双指针是一种解决问题的技巧或者思维方式，指在访问一个序列中的数据时使用两个指针进行扫描，两个指针可以是同向的，也可以是反向的；我们的关注点可以是这两个指针指向的两个元素本身，也可以是两个指针中间的区域。二分法的思想基于这种左右指针的实现



##  LeetCode 第 15题：三数之和


```csharp
#给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有满足条件且不重复的三元组。
# 注意：答案中不可以包含重复的三元组。 
# 示例： 
# 给定数组 nums = [-1, 0, 1, 2, -1, -4]，
#
#满足要求的三元组集合为：
#[
#  [-1, 0, 1],
#  [-1, -1, 2]
#]
# 
# Related Topics 数组 双指针
#leetcode submit region begin(Prohibit modification and deletion)
```


使用排序 + 双指针方法解决;

- 首先进行数组排序，时间复杂度 O(nlogn)
- 对数组nums进行遍历，每遍历一个值利用其下标 i，形成一个固定值 nums[i]
- 如果 nums[i] 大于0， 则三数之和必然无法等于0，直接结束循环
- 如果 nums[i] == nums[i-1]，则说明该数字重复，会导致结果重复，所以应该跳过
- 再使用前指针指向 start = i + 1处，后指针指向end = nums.length - 1，也就是结尾处
- 根据 sum = nums[i] + nums[start] + nums[end]结果，判断 sum 与 0 的大小关系，满足则添加进入结果，此时 start++; end-- 如果 sum < 0，则start++, 如果 sum > 0, 则 end--
- sum === 0 的时候还要考虑结果重复的情况
- nums[start] == nums[start+1] 则会导致结果重复，应该跳过，start++
- nums[end] == nums[end-1] 则会导致结果重复，应该跳过，end--










```csharp
class Solution:
    def threeSum(nums):
    nums.sort()
    # [-4, -1, -1, 0, 1, 2]
    res_list = []
    # 头部循环查找
    for i in range(len(nums)):
        if i == 0 or nums[i] > nums[i - 1]:
            # 最左端
            l = i + 1
            # 最右端
            r = len(nums) - 1
            while l < r:  # 正在查找
                three_sum = nums[i] + nums[l] + nums[r]
                if three_sum == 0:
                    res_list.append([nums[i], nums[l], nums[r]])
                    l += 1  # 右移一位
                    r -= 1  # 左移一位
                    while l < r and nums[l] == nums[l - 1]:
                        # 从左往右，相同数值直接跳过
                        l += 1
                    while r > l and nums[r] == nums[r + 1]:
                        # 从右往左，相同数值直接跳过
                        r -= 1
                elif three_sum > 0:
                    # 大于零，右边数值大，左移
                    r -= 1
                else:
                    # 小于零，左边数值小，右移
                    l += 1
    return res_list
```







##  LeetCode 第 16题：三数最近相加

```csharp
#给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。 
# 示例： 
# 输入：nums = [-1,2,1,-4], target = 1
#输出：2
#解释：与 target 最接近的和是 2 (-1 + 2 + 1 = 2) 。
# 提示： 
# 3 <= nums.length <= 10^3 
# -10^3 <= nums[i] <= 10^3 
# -10^4 <= target <= 10^4 
# Related Topics 数组 双指针
```


本题目因为要计算三个数，如果靠暴力枚举的话时间复杂度会到O(n^3)，需要降低时间复杂度

- 首先进行数组排序，时间复杂度O(nlogn)
- 在数组nums中，进行遍历，每遍历一个值利用其下标i，形成一个固定值nums[i]
- 再使用前指针指向`j= i + 1`处，后指针指向`k= nums.length - 1`处，也就是结尾处
- 根据 `sum = nums[i] + nums[start] + nums[end] `的结果，判断sum与目标target的距离，如果更近则更新结果ans
- 同时判断sum与target的大小关系，因为数组有序，如果sum > target 则` k--`，如果sum < target 则 `j++`，如果sum == target 则说明距离为0直接返回结果
- 整个遍历过程，固定值为n次，双指针为n次，时间复杂度为O(n^2)
- 总时间复杂度：$O(nlogn) + O(n^2) = O(n^2)$


```csharp
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        if not nums: return 0
        if len(nums) < 3: return sum(nums)

        ans = float('inf')
        nums.sort()
        for i in range(len(nums)):
            # 优化点 1
            if i > 0 and nums[i] == nums[i-1]: continue
            
            # 新的 t
            t = target - nums[i]
            j, k = i + 1, len(nums) - 1
            while j < k:
                # 优化点 2
                if t == nums[j] + nums[k]: return target

                # 当前 j、k更接近target
                if abs(t - nums[j] - nums[k]) < abs(target - ans):
                    ans = nums[i] + nums[j] + nums[k]
                # 移动j | k
                if t > nums[j] + nums[k]:
                    j += 1
                else:
                    k -= 1
        return ans
```

##  LeetCode 第 27题：移除元素





```csharp
#给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。
# 不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。
# 元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。
# 示例 1:
# 给定 nums = [3,2,2,3], val = 3,
#函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。
#你不需要考虑数组中超出新长度后面的元素。
# 示例 2:
# 给定 nums = [0,1,2,2,3,0,4,2], val = 2,
#函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。
#注意这五个元素可为任意顺序。
#你不需要考虑数组中超出新长度后面的元素。
# 说明:
# 为什么返回数值是整数，但输出的答案是数组呢?
# 请注意，输入数组是以「引用」方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。
# 你可以想象内部操作如下:
# // nums 是以“引用”方式传递的。也就是说，不对实参作任何拷贝
#int len = removeElement(nums, val);
#// 在函数里修改输入数组对于调用者是可见的。
#// 根据你的函数返回的长度, 它会打印出数组中 该长度范围内 的所有元素。
#for (int i = 0; i < len; i++) {
#    print(nums[i]);
#}
# 
# Related Topics 数组 双指针
```



首先讲讲自己做题的思路，用Python做比较简单，遍历数组，如果当前值不等于val，就赋值给数组的第i个位置，i+1。



```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i = 0
        for num in nums:
            if num != val:
                nums[i] = num
                i += 1
        return i
```



官方的解法二就是双指针，在数组需要剔除的元素很少的情况下，上述方法显得有些没必要。比如数组为[1,2,3,5,4],要剔除的数是4时，没必要将前面4个数字遍历一遍。





- i, j 分别指向数组的首尾下标。
- 从 i 开始往后扫描，如果遇到 nums[i] == val 就把它跟 j 交换，j左移一位。直到 i <= j 表示扫描完毕退出



```csharp
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i, j = 0, len(nums)-1
        while i <= j:
            if nums[i] == val:
                nums[i], nums[j] = nums[j], nums[i]
                j -= 1
            else:
                i += 1
        return i
```


# 84、Python | Leetcode回溯算法系列

@Author：Runsen

@Date：2020/7/7



今天高考，当年我就是一个辣鸡，现在还是一个辣鸡，祝高考的个个清华北大。辣鸡的我决定继续更新Python教程，今天就开始了八十四、Python | Leetcode回溯算法系列。




## 回溯算法

 回溯算法(Backtracking Algorithm)，实际上一个类似枚举的搜索尝试过程，主要是在搜索尝试过程中寻找问题的解，当发现已不满足求解条件时，就“回溯”返回，尝试别的路径。(上述定义来自百度百科)


基本思想是：从一条路往前走，能进则进，不能进则退回来，换一条路再试。

回溯算法实际上一个类似枚举的搜索尝试过程，主要是在搜索尝试过程中寻找问题的解，当发现已不满足求解条件时，就“回溯”返回，尝试别的路径。

回溯法是一种选优搜索法，按选优条件向前搜索，以达到目标。但当探索到某一步时，发现原先选择并不优或达不到目标，就退回一步重新选择，这种走不通就退回再走的技术为回溯法，而满足回溯条件的某个状态的点称为“回溯点”。许多复杂的，规模较大的问题都可以使用回溯法，有“通用解题方法”的美称。


回溯算法也叫试探法，它是一种系统地搜索问题的解的方法。

八皇后问题就是回溯算法的典型


假设有一个8X8的棋盘，要放8个棋子（皇后）每个棋子所在行，列，对角线不能有棋子
![](https://img-blog.csdnimg.cn/20190530172548385.png)

第一步按照第一行放一个皇后，然后第二行符合要求放第2个皇后，如果没有位置符合要求，那么就要改变第一个皇后的位置，重新放第2个皇后的位置，直到找到符合条件的位置就可以了。




我们首先将问题简化为四皇后问题，并用回溯法来找到他们的解。目的是在4x4的棋盘上，使得4个皇后不能在同行同列以及同斜线上。

首先尝试将皇后放入第一个格子，被涂黑的地方是不能放皇后





![](https://img-blog.csdnimg.cn/20200707143146449.png)


第二行的皇后只能放在第三格或第四格，比方我们放第三格，则：


![](https://img-blog.csdnimg.cn/20200707143203747.png)


可以看到再难以放下第三个皇后，此时我们就要用到回溯算法了。我们把第二个皇后更改位置，此时我们能放下第三枚皇后了。


![](https://img-blog.csdnimg.cn/2020070714322287.png)


虽然是能放置第三个皇后，但是第四个皇后又无路可走了。返回上层调用（3号皇后），而3号也别无可去，继续回溯上层调用（2号），2号已然无路可去，继续回溯上层（1号），于是1号皇后改变位置如下，继续回溯。


![](https://img-blog.csdnimg.cn/20200707143235395.png)


上述就是回溯算法的过程，根据这个算法，最终能够把四位皇后放在4x4的棋盘里。也能用同样的方法解决了八皇后问题甚至N皇后问题。



## Leetcode第51题，面试题 08.12：八皇后

```csharp
#设计一种算法，打印 N 皇后在 N × N 棋盘上的各种摆法，其中每个皇后都不同行、不同列，也不在对角线上。这里的“对角线”指的是所有的对角线，不只是平分整个棋盘的那两条对角线。 
# 注意：本题相对原题做了扩展 
# 示例: 
#  输入：4
# 输出：[[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
# 解释: 4 皇后问题存在如下两个不同的解法。
#[
# [".Q..",  // 解法 1
#  "...Q",
#  "Q...",
#  "..Q."],
#
# ["..Q.",  // 解法 2
#  "Q...",
#  "...Q",
#  ".Q.."]
#]
# 
# Related Topics 回溯算法
```

在此之前写过，因此不写题解，具体代码如下。



```csharp
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        res = []
        s = "." * n
        def backtrack(i, tmp,col,z_diagonal,f_diagonal):
            if i == n:
                res.append(tmp)
                return 
            for j in range(n):
                if j not in col and i + j not in  z_diagonal and i - j not in f_diagonal:
                    backtrack(i+1,tmp + [s[:j] + "Q" + s[j+1:]], col | {j}, z_diagonal |{i + j} , f_diagonal |{i - j}  ) 
            
        backtrack(0,[],set(),set(),set())    
        return res
```


## Leetcode第46题，全排列

```csharp
#给定一个 没有重复 数字的序列，返回其所有可能的全排列。 
# 示例: 
# 输入: [1,2,3]
#输出:
#[
#  [1,2,3],
#  [1,3,2],
#  [2,1,3],
#  [2,3,1],
#  [3,1,2],
#  [3,2,1]
#] 
# Related Topics 回溯算法
```


具体来说，假设我们已经填到第index个位置，那么nums[] 数组中[0, index - 1]是已填过的数的集合，[index - 1, length - 1] 是待填的数的集合。我们肯定是尝试用[0, index - 1]里的数去填第index个数，假设待填的数的下标为i，那么填完以后我们将第i个数和第index个数交换，即能使得在填第index + 1个数的时候nums[] 数组的[0, index]部分为已填过的数，[index + 1, n - 1]为待填的数，回溯的时候交换回来即能完成撤销操作。



具体来说，假设我们已经填到第index个位置，那么nums[] 数组中[0, index - 1]是已填过的数的集合，[index - 1, length - 1] 是待填的数的集合。我们肯定是尝试用[0, index - 1]里的数去填第index个数，假设待填的数的下标为i，那么填完以后我们将第i个数和第index个数交换，即能使得在填第index + 1个数的时候nums[] 数组的[0, index]部分为已填过的数，[index + 1, n - 1]为待填的数，回溯的时候交换回来即能完成撤销操作。



![](https://img-blog.csdnimg.cn/20200707150459893.png)


```csharp
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        """itertools库内置了这个函数"""
        return itertools.permutations(nums)
    
    def permute2(self, nums: List[int]) -> List[List[int]]:
        """自己写回溯法"""
        res = []
        def _backtrace(nums, pre_list):
            if len(nums) <= 0:
                res.append(pre_list)
            else:
                for i in nums:
                    # 注意copy一份新的调用，否则无法正常循环
                    p_list = pre_list.copy()
                    p_list.append(i)
                    left_nums = nums.copy()
                    left_nums.remove(i)
                    _backtrace(left_nums, p_list)
        _backtrace(nums, [])
        return res

class Solution:
    def __init__(self):
        self.res = []

    def permute(self, nums: List[int]) -> List[List[int]]:
        self.back_trace(nums, [])
        return self.res

    def back_trace(self, nums, tmp):
        if not nums:
            self.res.append(tmp)
        else:
            for i in range(len(nums)):
                self.back_trace(nums[:i] + nums[i + 1:], tmp + [nums[i]])


```

## Leetcode第39题，组合总和

```csharp
#给定一个无重复元素的数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。 
# candidates 中的数字可以无限制重复被选取。 
# 说明： 
# 所有数字（包括 target）都是正整数。 
# 解集不能包含重复的组合。 
# 示例 1: 
# 输入: candidates = [2,3,6,7], target = 7,
#所求解集为:
#[
#  [7],
#  [2,2,3]
#]
# 示例 2: 
# 输入: candidates = [2,3,5], target = 8,
#所求解集为:
#[
#  [2,2,2,2],
#  [2,3,3],
#  [3,5]
#] 
# Related Topics 数组 回溯算法

```

首先对candidates排序

若candidates为空，则返回[]

回溯函数helper()，传入参数：下一加和索引i，当前已加和数组tmp，下一目标target

若target==0，说明当前和满足条件，将当前加和数组tmp加入res，并return。


 因为已经将candidates排序，所以当下一目标小于下一待加和数时，return。

并且当下一待加和索引`i==n`时，return。为了防止数组越界，将条件i==n放在target<candidates[i]之前，进行截断。



因为可重复调用元素，所以helper(i,tmp+[candidates[i],target-candidates[i]]继续重复调用自身。


调用数组中下一元素，寻找新答案。helper(i+1,tmp,target])。执行helper(0,[],target)并返回resres





```csharp
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        if(not candidates):
            return []
        n=len(candidates)
        res=[]
        candidates.sort()
        def helper(i,tmp,target):
            if(target==0):
                res.append(tmp)
                return
            if(i==n or target<candidates[i]):
                return
            helper(i,tmp+[candidates[i]],target-candidates[i])
            helper(i+1,tmp,target)
        helper(0,[],target)
        return res
```
# 85、Python | Leetcode数据结构之图和动态规划算法系列

@Author：Runsen

@Date：2020/7/7

今天高考，当年我就是一个辣鸡，现在还是一个辣鸡，祝高考的个个清华北大。辣鸡的我决定继续更新Python教程，今天就开始了八十五、Python | Leetcode数据结构之图和动态规划算法系列。

如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。


## 图



在计算机科学中，一个图就是一些顶点的集合，这些顶点通过一系列边结对（连接）。顶点用圆圈表示，边就是这些圆圈之间的连线。顶点之间通过边连接。
![](https://img-blog.csdnimg.cn/20190529212733348.png)

一个图G = (V, E)由以下元素组成。

-  V：一组顶点 

-  E：一组边，连接V中的顶点 

## 度

表示一个顶点又多少条边


- 入度 表示又多少条变指向这个顶点
- 出度 表示这个顶点指出多少条边

## 邻接矩阵





在邻接矩阵实现中，由行和列都表示顶点，由两个顶点所决定的矩阵对应元素表示这里两个顶点是否相连、如果相连这个值表示的是相连边的权重。
![](https://img-blog.csdnimg.cn/2019052921325674.png)

- 无向图： 顶点 i 和顶点 j 之间有边，就将$A[i][j]$和$A[j][i]$ 标记为1  
- 有向图 如果 顶点i和顶点 j之间 ，有一条箭头从i指向 j 将$A[i][j]$ 标记为1 
- 有权图，数组存储相应的权重


还有 稀疏图。 稀疏图就是顶点多，但是每个顶点边并不多

应用：微信号几亿的用户，对应到图上就好几亿的顶点，但是每个用户的好友并不会很多，最多5000，如果用邻接矩阵来存储，那么存储空间都被浪费了


## 邻接表

![](https://img-blog.csdnimg.cn/20190529214855933.png)

邻接矩阵存储比较浪费时间，但是使用起来比较节省时间。相反邻接表存储起来比较节省空间，但是使用就比较浪费时间。

上图是否存在一条从顶点2到顶点4的边，就要遍历顶点2对应的链表



## 动态规划算法Dynamic Programming


先来看看生活中经常遇到的事吧——假设您是个土豪，身上带了足够的1、5、10、20、50、100元面值的钞票。现在您的目标是凑出某个金额w，需要用到尽量少的钞票。


依据生活经验，我们显然可以采取这样的策略：能用100的就尽量用100的，否则尽量用50的……依次类推。在这种策略下，666=6×100+1×50+1×10+1×5+1×1，共使用了10张钞票。


这种策略称为“贪心”：假设我们面对的局面是“需要凑出w”，贪心策略会尽快让w变得更小。能让w少100就尽量让它少100，这样我们接下来面对的局面就是凑出w-100。长期的生活经验表明，贪心策略是正确的。

但是，如果我们换一组钞票的面值，贪心策略就也许不成立了。如果一个奇葩国家的钞票面额分别是1、5、11，那么我们在凑出15的时候，贪心策略会出错：

15=1×11+4×1    （贪心策略使用了5张钞票）
15=3×5               （正确的策略，只用3张钞票）




再从一个简单的例子分析：
有 5 个物品，重量分别是 w = [1, 2, 3, 4, 5]；
对应的价值是 v = [1, 2, 4, 2, 5]；
背包容量 C = 10。


![](https://img-blog.csdnimg.cn/20200707155455779.png)


暴力法：对所有选择的组合，算出每一种情况的总价值，比较即可得出答案。


递归法：对于每个物品都有选与不选的决策，即原问题可以分解成两个子问题的比较。

假设有一个计算总价值的函数 F(n, c)，上述五个物品编号 i 为 1 ~ 5，c 是背包容量。
对于上例，第五个物品选择与否，通过比较两种子情况得到的价值大小来决定：

F(5, 10) = Max(F(4, 10) , F(4, 5) + 5)

故原问题有：

F(i, c) = Max( F(i-1, c), F(i-1, c - wi) + vi)

当然，如果背包剩余容量不足以容纳下一个物品，则再将 i-1。


![](https://img-blog.csdnimg.cn/2020070715560131.png)



动态规划：在递归的基础上储存已经求出的值。
当子问题重复出现时直接获取储存中的结果。
用一个 c*i 的二维数组储存——




![](https://img-blog.csdnimg.cn/20200707155644115.png)










##  Leetcode第64题：最小路径和


```csharp
#给定一个包含非负整数的 m x n 网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。 
#
# 说明：每次只能向下或者向右移动一步。 
#
# 示例: 
#
# 输入:
#[
#  [1,3,1],
#  [1,5,1],
#  [4,2,1]
#]
#输出: 7
#解释: 因为路径 1→3→1→1→1 的总和最小。
# 
# Related Topics 数组 动态规划
```

本题dp实现采用数组实现，因为只能向右或者向下移动，要走到走到在第ｉ行第ｊ列的网格，必须是从第ｉ-1行第ｊ列的网格或者第ｉ行第ｊ-1列的网格移动过来，假设二维数组`dp[i][j]`表示在第ｉ行第ｊ列的网格上的最小数字总和



初始化dp所有的元素均为0，在网格的第一行和第一列的所有路径和应该都是固定的，因为都是向右或者向下移动

而当位置(i,j)处时，dp[i][j] = min(dp[i-1][j] +grid[i][j]，dp[i][j-1]++grid[i][j])，另外，二维数组是额外的辅助空间，如果将直接将原数组grid来存储dp数组的结果，边遍历边更新，对grid进行原地修改，可降低空间复杂度，如下．



```csharp
from typing import List
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m = len(grid)
        n =len(grid[0])        
        #在网格的第一行和第一列的所有路径和应该都是固定的，直接向右或者向下移动相加
        for i in range(1,m):
            grid[i][0] += grid[i-1][0]
        for j in range(1,n):
            grid[0][j] += grid[0][j-1]            
        #非第一行和非第一列：
        for i in range(1,m):
            for j in range(1,n):
                grid[i][j]= min(grid[i-1][j] + grid[i][j], grid[i][j-1] + grid[i][j] )
        return grid[-1][-1]


if __name__ == "__main__":
    s=Solution()
    t=[[1,3,1],
      [1,5,1],
      [4,2,1]]
    print(s.minPathSum(t))
# result
7
```







## Leetcode第70题：爬楼梯


```csharp
#假设你正在爬楼梯。需要 n 阶你才能到达楼顶。 
# 每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？ 
# 注意：给定 n 是一个正整数。 
# 示例 1： 
# 输入： 2
#输出： 2
#解释： 有两种方法可以爬到楼顶。
#1.  1 阶 + 1 阶
#2.  2 阶 
# 示例 2： 
# 输入： 3
#输出： 3
#解释： 有三种方法可以爬到楼顶。
#1.  1 阶 + 1 阶 + 1 阶
#2.  1 阶 + 2 阶
#3.  2 阶 + 1 阶
# Related Topics 动态规划
```


动态规划：第一个想法就是利用递推公式求解方法数。
分析这个题目：

- 1 阶，f(1) = 1 种方案
- 2 阶，f(2) = 2 种方案
- 3 阶，f(3) = 3 种方案
- 4 阶，f(4) = 5 种方案

- n 阶，f(n) = f(n-1) + f(n-2) 种方案

即，该问题可以转换为斐波那契数列问题


优化空间复杂度：其实每次计算 f(i) 的值，都只用了离它最近的两个值，而没有用数组中其他的值。

也就是说我们根本不需要用一个数组来存放，只需要用两个变量来存放每次更新后最新得到的两个值即可。


```csharp
class Solution:
    def climbStairs(self, n: int) -> int:
        # 这里我们用prev curr分别存放离当前台阶数最近的两个台阶数对应的方法数。
        curr = prev = 1
        for _ in range(n-1):
            curr, prev = curr + prev, curr
        return curr


class Solution:
    def climbStairs(self, n, s1 = 0, s2 = 1):
        return n and self.climbStairs(n - 1, s2, s1 + s2) or s2
```




## Leetcode第322题： 零钱兑换

```csharp
#给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 -1。 
# 示例 1: 
# 输入: coins = [1, 2, 5], amount = 11
#输出: 3 
#解释: 11 = 5 + 5 + 1 
# 示例 2: 
# 输入: coins = [2], amount = 3
#输出: -1 
# 说明: 
#你可以认为每种硬币的数量是无限的。 
# Related Topics 动态规划
```




动态规划问题的一般形式就是求最值，求最值就是穷举所有的可能性。

```csharp

```

假设输入不同面额的硬币 coins = [coin1, coin2, coin3] , 总金额 amount


采用贪心算法做法： 对于 [1,2,5] 组成 11 块，排序[5,2,1]



- 取第一个5, 更新amout 为 11 - 5 = 6 继续更新 为 6 - 5 = 1 (退出

- 取第二个2   1 < 2 退出

- 取最后一个元素，也就是1


- amout 为 0 退出


因此结果是 3，但是贪心算法也有可能出错。 就拿这道题目来说，
它也是不正确的！ 比如 coins = [1, 5, 11] amout = 15, 因此这种做法有时候不靠谱，我们还是采用靠谱的做法。


因此需要dp算法，
用dp[i] 来表示组成i块钱，需要最少的硬币数，那么第j个硬币我可以选择不拿 这个时候， 硬币数 = dp[i]

第j个硬币我可以选择拿 这个时候， 硬币数 = dp[i - coins[j]] + 1

和背包问题不同， 硬币是可以拿任意个

对于每一个 dp[i] 我们都选择遍历一遍 coin， 不断更新 dp[i]。


这算是一道比较经典的动态规划题目了吧。关键是确定状态转移方程，如果当前组合dp[i]的个数小于另一i-1个组合+某一硬币的组合，则需要更新该值，所以可以得到状态转移方程如下：

```csharp
dp[i] = min(dp[i],dp[i-coin]+1)
```

那么就可以很容易地写出题解。


```csharp
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [amount + 1] * (amount + 1)
        dp[0] = 0

        for i in range(1, amount + 1):
            for j in range(len(coins)):
                if i >= coins[j]:
                    dp[i] = min(dp[i], dp[i - coins[j]] + 1)

        return -1 if dp[-1] == amount + 1 else dp[-1]
```

# 86、Python | Leetcode深度和广度优先搜索算法系列
@Author：Runsen

@Date：2020/7/8





今天高考，当年我就是一个辣鸡，现在还是一个辣鸡，祝高考的个个清华北大。辣鸡的我决定继续更新Python教程，今天就开始了八十六、Python | Leetcode深度和广度优先搜索算法系列。

如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。



## 深度优先算法（DFS）

 不断地沿着顶点的深度方向进行遍历，该算法的空间复杂度与数据结构深度成正比。

深度优先算法：

（1）访问初始顶点v并标记顶点v已访问。
（2）查找顶点v的第一个邻接顶点w。
（3）若顶点v的邻接顶点w存在，则继续执行；否则回溯到v，再找v的另外一个未访问过的邻接点。
（4）若顶点w尚未被访问，则访问顶点w并标记顶点w为已访问。
（5）继续查找顶点w的下一个邻接顶点wi，如果v取值wi转到步骤（3）。直到连通图中所有顶点全部访问过为止。


## 广度优先算法（BFS）

  先访问完当前顶点的所有邻接点，然后再访问下一层的所有节点，该算法适用于解决最短、最小路径等问题，但是构建广度优先算法需要维护自己的队列。


（1）顶点v入队列。
（2）当队列非空时则继续执行，否则算法结束。
（3）出队列取得队头顶点v；访问顶点v并标记顶点v已被访问。
（4）查找顶点v的第一个邻接顶点col。
（5）若v的邻接顶点col未被访问过的，则col入队列。
（6）继续查找顶点v的另一个新的邻接顶点col，转到步骤（5）。直到顶点v的所有未被访问过的邻接点处理完。转到步骤（2）。





## Leetcode第111题： 二叉树的最小深度




```csharp
#给定一个二叉树，找出其最小深度。 
# 最小深度是从根节点到最近叶子节点的最短路径上的节点数量。 
# 说明: 叶子节点是指没有子节点的节点。 
# 示例: 
# 给定二叉树 [3,9,20,null,null,15,7], 
#
#     3
#   / \
#  9  20
#    /  \
#   15   7 
#
# 返回它的最小深度 2. 
# Related Topics 树 深度优先搜索 广度优先搜索
```

最小深度的定义：它是从根节点到最近叶子节点的最短路径上的节点数量。这种情况下，由于节点 1 没有右子树，那么右子树的深度为 0，左子树的深度为 1，但是却不能说它的左右子树的最小深度为 0，因为右子树不存在，即节点 1 没有右叶子节点，不满足条件。


比如二叉树 [1, 2] 的最小深度为 2，而不是 1。


![](https://img-blog.csdnimg.cn/2020070822093271.png)


对于一个节点，如果是叶子节点，则返回其深度；如果只有左子树，则递归得到左子树的最小深度；如果只有右子树，则递归得到右子树的最小深度；如果左右孩子节点都有，则递归得到两个子树的深度，并且取最小值。

```csharp
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def minDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root:
            return 0
        return self.get_min_depth(root, 0)

    def get_min_depth(self, node, depth):
        # 分为四种情况：叶子节点，只有左孩子的节点，只有右孩子的节点，两个孩子都有的节点
        if not node.left and not node.right:
            return depth+1
        if node.left and node.right:
            return min(self.get_min_depth(node.left, depth+1), self.get_min_depth(node.right, depth+1))
        if node.left:
            return self.get_min_depth(node.left, depth+1)
        if node.right:
            return self.get_min_depth(node.right, depth+1)
```

上面的是递归的做法

BFS，当遇到第一个叶子节点的时候，该节点深度就是最小深度。



```csharp
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root: return 0
        queue = [(1, root)]
        while queue:
            depth, node = queue.pop(0)
            if not node.left and not node.right:
                return depth
            if node.left:
                queue.append((depth + 1, node.left))
            if node.right:
                queue.append((depth + 1, node.right))
```



DFS，需要把所有的叶子节点的深度进行比较，才可以得到最终的最小深度。


```csharp
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root: return 0
        stack = [(1, root)]
        min_depth = float('inf')
        while stack:
            depth, node = stack.pop()
            if not node.left and not node.right:
                min_depth = min(min_depth, depth)
            if node.right:
                stack.append((depth + 1, node.right))
            if node.left:
                stack.append((depth + 1, node.left))       
        return min_depth 
```



## Leetcode第112题： 路径总和



```csharp
#给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。
# 说明: 叶子节点是指没有子节点的节点。
# 示例: 
#给定如下二叉树，以及目标和 sum = 22， 
#
#               5
#             / \
#            4   8
#           /   / \
#          11  13  4
#         /  \      \
#        7    2      1
# 返回 true, 因为存在目标和为 22 的根节点到叶子节点的路径 5->4->11->2。 
# Related Topics 树 深度优先搜索
```

方法一：递归（DFS，深度优先搜索）




```csharp
class Solution:
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        # 二叉树 root 为 null
        if not root:
            return False
        # 无左右子树
        if not root.left and not root.right:
            return sum == root.val
        return self.hasPathSum(root.left, sum - root.val) or self.hasPathSum(root.right, sum - root.val)
```


方法二：广度优先搜索（BFS）


collection 为 Python 的内建集合版块，collection.deque 为双端队列，可以从两端添加（append）和弹出（pop）元素，且时间复杂度为 O(1)，耗时小于 list 的 insert 和 pop 操作的 O(N)。


```csharp
d = deque([1, 2, 3, 4, 5]
## 两端添加元素
d.append(6)                 # deque([1, 2, 3, 4, 5, 6])
d.appendleft(0)             # deque([0, 1, 2, 3, 4, 5, 6])
## 两端按序拓展元素
d.extend([7, 8])            # deque([0, 1, 2, 3, 4, 5, 6, 7, 8])
d.extendleft([-1, -2])      # deque([-2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8])
## 指定位置插入元素
d.insert(0, -3)             # deque([-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8])
## 两端弹出元素
d.pop()                     # deque([-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7])
d.popleft()                 # deque([-2, -1, 0, 1, 2, 3, 4, 5, 6, 7])
## 删除从左到右找到的首个指定元素
d.remove(-1)                # deque([-2, 0, 1, 2, 3, 4, 5, 6, 7])
## 指定元素计数
d.count(3)                  # 1
## 返回从左到右找到的首个指定元素的索引
d.index(5)                  # 6
## 逆序排列
d.reverse()                 # deque([7, 6, 5, 4, 3, 2, 1, 0, -2])
## 元素双向循环指定步数
d.rotate(2)                 # deque([0, -2, 7, 6, 5, 4, 3, 2, 1])
d.rotate(-2)                # deque([7, 6, 5, 4, 3, 2, 1, 0, -2])
```


时间复杂度：O(N)
空间复杂度：O(H)，H 为树的高度，最坏情况下，树成链状，为 O(N)。



```csharp
class Solution:
    import collections
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        if not root:
            return False
        que_node = collections.deque([root])        # 结点队列
        que_val = collections.deque([root.val])     # 结点值队列
        while que_node:
            now = que_node.popleft()                # 当前结点
            temp = que_val.popleft()                # 临时存储值
            if not now.left and not now.right:
                if temp == sum:
                    return True
                continue
            if now.left:
                que_node.append(now.left)
                que_val.append(now.left.val + temp)
            if now.right:
                que_node.append(now.right)
                que_val.append(now.right.val + temp)
        return False
```

# 87、Python | 十大排序算法系列（上篇）


﻿@Author：Runsen


辣鸡的我决定继续更新Python教程，今天就开始了八十七、Python | 十大排序算法系列（上篇）。还有不到区区的十三篇，我快完成了。

如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。



关于排序就是下面的十大排序算法

![](https://img-blog.csdnimg.cn/20200708224346201.png)



## 冒泡排序


python实现冒泡排序的核心思想是通过从列表一端迭代循环元素，再通过一个循环让这个元素之后的元素相邻两个比较，从而依次将最大值移动到最末端，如下图示意。

![](https://img-blog.csdnimg.cn/20200710225605314.png)

Python冒泡排序的代码实现。




```csharp
def bubble_sort(nums):
    for i in range(len(nums) - 1):
        for j in range(len(nums) - i - 1):
            if nums[j] > nums[j + 1]:
                nums[j], nums[j + 1] = nums[j + 1], nums[j]
    return nums
```

## 选择排序

排序算法：首先搜索整个列表，找到最小项的位置，如果该位置不是列表的第1项，就交换这两个位置的元素。然后从列表的第2个元素开始，重复上述过程，直到算法达到整个过程的最后一个位置，图形解释如下


下面使用55、23、87、62、16数列从小到大的排序过程来说明选择排序法的演算流程。原始数据如图：


1、首先找到此数列中最小值后，与数列中的第一个元素交换，如下图所示。

![](https://img-blog.csdnimg.cn/20200710225916995.png)


从第二个值开始找，找到剩余数列中（不含第一个填充为绿色的数字）的最小值，再和第二个值交换，如下图所示。

![](https://img-blog.csdnimg.cn/20200710230000474.png)


从第三个值开始找，找到此数列中（不含第一、二个的最小值），再和第三个值交换，如下图


![](https://img-blog.csdnimg.cn/20200710230017145.png)



从第四个值开始找，找到剩余数列的最小值，再和第四个值交换，排序完成，如下图。


![](https://img-blog.csdnimg.cn/20200710230038146.png)


Python选择排序的代码实现。

```csharp
def selectionSort(x):
   i = 0
   while i < len(x) - 1:
       minindex = i
       j = i + 1
       while j < len(x) :        
           if x[minindex] > x[j]:
               minindex = j
           j+= 1
       if minindex != i:
           swap(x,i,minindex)    
       i+= 1
   return x
```

## 插入排序

插入排序的实现思路顾名思义，就是不断地在一个已经是有序的数组中，寻找合适位置并插入新元素。

从后往前依次进行比较，如果待插入元素大于当前元素，则将待插入元素插入到当前元素的后一位，如果待插入元素小于当前元素，则将当前元素后移一位。不断重复该过程直至到数组的最后一位

![](https://img-blog.csdnimg.cn/20200710230139430.png)


Python插入排序的代码实现。


```csharp
def insertion_sort(a):
    length = len(a)
    if length <=1:
        return 
    for i in range(1,length):
        j = i-1
        value = a[i]
        while j >=0:
            if a[j]<value:
                a[j+1] = value
                break
            else:
                a[j+1] = a[j]
                if j == 0:
                    a[j] = value 
            j -=1
        print(a)
    return a
```

## 希尔排序

希尔排序的基本思想是：把记录按步长 gap 分组，对每组记录采用直接插入排序方法进行排序。

随着步长逐渐减小，所分成的组包含的记录越来越多，当步长的值减小到 1 时，整个数据合成为一组，构成一组有序记录，则完成排序。



我们画个图来说明一下


![](https://img-blog.csdnimg.cn/20200710231113715.png)
上面的排序其实和冒泡排序很像，只不过冒泡排序是每次都是间隔为1相邻的两个之间进行比较，但希尔排序是间隔为step，还是有一定区别的。

Python 希尔排序的代码实现。





```csharp
def shell_sort(list):
    n = len(list)
    gap = n // 2
    while gap >= 1:
        for j in range(gap, n):
            i = j
            while( i - gap ) >= 0:
                if list[i] < list[ i - gap ]:
                    list[i], list[ i - gap ] = list[ i - gap ], list[i]
                    i -= gap
                else:
                    break
        gap //= 2
        
if __name__ == '__main__':
    alist = [54, 26, 93, 17, 77, 31, 44, 55, 20]
    print("原列表为：%s" % alist)
    shell_sort(alist)
    print("新列表为：%s" % alist)
```

## 归并排序

 归并排序的基本思想：将待排序序列`R[0…n-1]`看成是`n`个长度为1的有序序列，将相邻的有序表成对归并，得到n/2个长度为2的有序表；将这些有序序列再次归并，得到`n/4`个长度为4的有序序列；如此反复进行下去，最后得到一个长度为n的有序序列。

![](https://img-blog.csdnimg.cn/2020071023152225.png)




归并排序其实要做两件事：

（1）“分解”——将序列每次折半划分。

（2）“合并”——将划分后的序列段两两合并后排序。







![](https://img-blog.csdnimg.cn/20200710231610643.gif)

Python 归并排序的代码实现。


```csharp
def merge(left, right):
    i = 0
    j = 0
    temp = []
    while i <= len(left) - 1 and j <= len(right) - 1:
        if left[i] <= right[j]:
            temp.append(left[i])
            i += 1
        else:
            temp.append(right[j])
            j += 1
    temp += left[i:] + right[j:]
    return temp

print(merge([1,3,4],[2,3,3])) 
```
# 88、Python | 十大排序算法系列（下篇）
﻿@Author：Runsen











辣鸡的我决定继续更新Python教程，今天就开始了八十八、Python | 十大排序算法系列（下篇）。还有不到区区的十二篇，我就完成了。

如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。



关于排序就是下面的十大排序算法

![](https://img-blog.csdnimg.cn/20200708224346201.png)




## 快速排序

快速排序的基本思想是：通过一趟排序将要排序的数据分割成独立的两部分：分割点左边都是比它小的数，右边都是比它大的数。


如果要排序数组中下标从 p 到 r 之间的一组数据，我们选择 p 到 r 之间的任意一个数据作为 pivot（分区点）。

我们遍历 p 到 r 之间的数据，将小于 pivot 的放到左边，将大于 pivot 的放到右边，将 pivot 放到中间。经过这一步骤之后，数组 p 到 r 之间的数据就被分成了三个部分，前面 p 到 q-1 之间都是小于 pivot 的，中间是 pivot，后面的 q+1 到 r 之间是大于 pivot 的。
![](https://img-blog.csdnimg.cn/20200710234816330.png)



我们通过实例来具体讲解一下：










![](https://img-blog.csdnimg.cn/20200710235338355.png)

上图来自王争算法专栏。


Python快速排序的代码实现。




```csharp
def quicksort(array):
  if len(array) < 2:
    # 基本情况下，具有0或1个元素的数组是已经“排序”的
    return array
  else:
    # 递归情况
    pivot = array[0]
    # 小于基准值的所有元素的子数组
    less = [i for i in array[1:] if i <= pivot]
    # 大于基准值的所有元素的子数组
    greater = [i for i in array[1:] if i > pivot]
    return quicksort(less) + [pivot] + quicksort(greater)

print(quicksort([10, 5, 2, 3]))
```

## 堆排序

**「堆」**首先是一个完全二叉树，**「堆」**分为**「大顶堆」**和**「小顶堆」**。
**「大顶堆」** ：每个节点的值大于或等于其左右孩子节点的值，称为大顶堆。
**「小顶堆」**：同理就是每个节点的值小于或等于其左右孩子节点的值。



![](https://img-blog.csdnimg.cn/20200710235739330.png)

下图就是堆排序的过程，来自五分钟学算法。

![](https://img-blog.csdnimg.cn/20200710235932234.gif)

排序动画过程解释

- 首先，将所有的数字存储在堆中

- 按大顶堆构建堆，其中大顶堆的一个特性是数据将被从大到小取出，将取出的数字按照相反的顺序进行排列，数字就完成了排序

- 在这里数字 5 先入堆

- 数字 2 入堆

- 数字 7 入堆， 7 此时是最后一个节点，与最后一个非叶子节点（也就是数字 5 ）进行比较，由于 7 大于 5 ，所以 7 和 5 交互

- 按照上述的操作将所有数字入堆，然后从左到右，从上到下进行调整，构造出大顶堆

- 入堆完成之后，将堆顶元素取出，将末尾元素置于堆顶，重新调整结构，使其满足堆定义

- 堆顶元素数字 7 取出，末尾元素数字 4 置于堆顶，为了维护好大顶堆的定义，最后一个非叶子节点数字 5 与 4 比较，而后交换两个数字的位置
- 反复执行调整+交换步骤，直到整个序列有序



Python提供了创建和使用堆的方法，所以我们不必自己单独为了实现它们去写代码了:

- heappush(list, item)：向堆中添加一个元素，然后对其重新排序，使其保持堆状态。可用于空列表。
- heappop(list)：删除第一个（最小的）元素并返回该元素。此操作之后，堆仍然是一个堆，因此我们不必调用heapify()。
- heapify(list)：将给定的列表变成一个堆。



Python堆排序的代码实现。


```csharp
from heapq import heappop, heappush

def heap_sort(array):
    heap = []
    for element in array:
        heappush(heap, element)

    ordered = []

    # While we have elements left in the heap
    while heap:
        ordered.append(heappop(heap))

    return ordered

array = [13, 21, 15, 5, 26, 4, 17, 18, 24, 2]
print(heap_sort(array))
```

## 计数排序

计数排序使用一个辅助数组，遍历待排序的数据，待排序数据的值就是辅助数组的索引，辅助数组索引对应的位置保存这个待排序数据出现的次数。最后从辅助数组中取出待排序的数据，放到排序后的数组中。



![](https://img-blog.csdnimg.cn/20200711104651596.gif)


Python计数排序的代码实现。


```csharp
def count_sort(s):
    """计数排序"""
    # 找到最大最小值
    min_num = min(s)
    max_num = max(s)
    # 计数列表
    count_list = [0]*(max_num-min_num+1)
    # 计数
    for i in s:
        count_list[i-min_num] += 1
    s.clear()
    # 填回
    for ind,i in enumerate(count_list):
        while i != 0:
            s.append(ind+min_num)
            i -= 1

if __name__ == '__main__':
    a = [3,6,8,4,2,6,7,3]
    count_sort(a)
    print(a)
```

## 桶排序

桶排序就是把最大值和最小值之间的数进行瓜分，例如分成 10 个区间，10个区间对应10个桶，我们把各元素放到对应区间的桶中去，再对每个桶中的数进行排序，可以采用归并排序，也可以采用快速排序之类的。







下图就是桶排序的过程，来自五分钟学算法。


![](https://img-blog.csdnimg.cn/20200711105628161.gif)



Python桶排序的代码实现。

```csharp
import random
def bucket_sort(arr):
    """桶排序"""
    min_num = min(arr)
    max_num = max(arr)
    # 桶的大小
    bucket_range = (max_num-min_num) / len(arr)
    # 桶数组
    count_list = [ [] for i in range(len(arr) + 1)]
    # 向桶数组填数
    for i in arr:
        count_list[int((i-min_num)//bucket_range)].append(i)
    arr.clear()
    # 回填，这里桶内部排序直接调用了sorted 快速排序
    for i in count_list:
        for j in sorted(i):
            arr.append(j)
            
if __name__ == '__main__':
    arr = [random.randint(0,100) for _ in range(10)]
    print("原始数据：", arr)
    bucket_sort(arr)
    print("桶排序结果：", arr)
            

原始数据： [73, 93, 48, 26, 92, 25, 7, 63, 70, 57]
桶排序结果： [7, 25, 26, 48, 57, 63, 70, 73, 92, 93]
```


## 基数排序

基数排序：通过元素的部分要素，将要排序的元素分配至某些“桶”中，以此达到排序的作用。比如为整数排序，依次用整数的个位、十位...来排序（LSD低位优先）；或者高位到低位依次排序（MSD高位优先）。






下图就是桶排序的过程，来自基数排序。

![](https://img-blog.csdnimg.cn/20200711111015314.gif)


- 首先创建编号 0 ， 1 ，2 ，3 ，4 ，5 ， 6 ，7 ，8 ，9  这 10 个桶

- 遍历整个数列，查看数字的个位数，按照先后顺序存放在对应编号的桶中

- 比如 321 个位数 为 1 ，存放在编号 1 桶中

- 数字 1 个位数 为  1 ，存放在编号  1  桶中，同时存放在 321 上面

- 遍历完整个数列的个位数，将数字存放在桶中后，按照编号顺序取出数字，先放入桶中的数字先取出

- 然后依次遍历整个数列的十位数，按照上述个位数的操作整理数列

- 依次遍历整个数列的百位数，按照上述个位数的操作整理数列

- 这样就完成了 基数排序





Python 基数排序的代码实现。












```csharp
def radix_sort(ls):
    i = 0             # 记录当前正在排哪一位，最低位为1
    max_num = max(ls)  # 最大值
    j = len(str(max_num))  # 记录最大值的位数
    while i < j:
        bucket_list =[[] for q in range(10)] #初始化桶数组
        for x in ls:
            bucket_list[int(x / (10**i)) % 10].append(x) # 找到位置放入桶数组
        ls.clear()
        for x in bucket_list:   # 放回原序列
            for y in x:
                ls.append(y)
        i += 1
    return ls

if __name__ == '__main__':
    list1 = [34, 231, 74, 5, 98, 34, 18, 88, 147, 51, 65, 75, 144, 89]
    sort_list = radix_sort(list1)
    print(sort_list)
    
# 第一次按个位排序放入桶中是：  
[[], [231, 51], [], [], [34, 74, 34, 144], [5, 65, 75], [], [147], [98, 18, 88], [89]]
# 第二次按十位排序：
[[5], [18], [], [231, 34, 34], [144, 147], [51], [65], [74, 75], [88, 89], [98]]
# 第三次按百位排序：
[[5, 18, 34, 34, 51, 65, 74, 75, 88, 89, 98], [144, 147], [231], [], [], [], [], [], [], []]
```
# 89、Python的GUI系列 _ 使用PyQt5 快速构建一个GUI 应用


@Author：Runsen


在很早之前就学过了PyQt5 ，我决定在更新了几篇PyQt5 。之前写的PyQt5 博客基本覆盖于此。这篇是第八十九篇、Python的GUI系列 | 使用PyQt5 快速构建一个GUI 应用。离收官还有十一篇。






## Pyqt5的安装




安装 pyqt5

`pip install pyqt5`


如果出现了运行出现了 No module named 'PyQt5.sip'

解决方法 ：

` pip install --user pyqt5==5.10.1`

将pyqt5退了版本



## 添加外部设置工具


安装成功后，这个时候，我们在pycharm中添加外部设置工具。


## 配置QtDesigner

步骤如下：File -> Settings -> Tools -> External Tools -> 


![](https://img-blog.csdnimg.cn/2020071115410494.png)




Name填入QtDesigner（方便后续使用，名称无所谓）。


program ：自己的designer的位置，如`F:\anaconda\Library\bin\designer.exe`


![](https://img-blog.csdnimg.cn/20200711214134921.png)


##  配置PyUIC 


然后添加PyUIC（UI转换工具），PyUIC的Program为Python.exe，在Python的安装目录下面的Scripts目录下，Working directory同理设为我们的工作目录，Arguments则填入如下代码：




```csharp
-m PyQt5.uic.pyuic $FileName$ -o $FileNameWithoutExtension$.py
```







至于工作目录填写`项目的路径`，也可以填` $FileDir$`。
![](https://img-blog.csdnimg.cn/20200711220533733.png)

## 配置pyrcc


最后添加pyrcc用于PyQt5的资源文件转码。具体配置与上述内容相同，Arguments填入：


```csharp
-mPyQt5.uic.pyuic  $FileName$ -o$FileNameWithoutExtension$.py
```


至于工作目录填写`项目的路径`，也可以填` $FileDir$`。




![](https://img-blog.csdnimg.cn/20200711220639251.png)





`


点击Apply保存配置。配置完成之后，PyCharm中会加入3个工具。



![](https://img-blog.csdnimg.cn/20200711215316346.png)

## QtDesigner设计第一个QT应用



下面打开QtDesigner界面，点击QtDesigner则打开QtDesigner的界面。


![](https://img-blog.csdnimg.cn/20200711215406810.png)


刚打开Qt Designer，则弹出如下图所示的窗口。


![](https://img-blog.csdnimg.cn/20200711215455451.png)


创建新的Form给出了5个模板，其中Widget与Main Window最为常用。这里我们选择创建一个Main Window。


![](https://img-blog.csdnimg.cn/20200711215603979.png)

我们什么也不干，直接保存就可以了。
![](https://img-blog.csdnimg.cn/202007112159561.png)


##  将一个.ui 文件生成一个.py文件

将demo.ui 文件打开其实是一个xml网页代码


![](https://img-blog.csdnimg.cn/20190421142300673.png)




在命令行

![](https://img-blog.csdnimg.cn/20190421142826586.png)

![](https://img-blog.csdnimg.cn/20190421142838791.png)



![](https://img-blog.csdnimg.cn/20200711220210231.png)


这样就会生成一个py文件。

![](https://img-blog.csdnimg.cn/20200711221046862.png)

但是直接运行是没有启动的，因为没有使用QApplication和QWidget两个类。这两个类都在PyQt5.QtWidgets。





```python
from PyQt5 import QtCore, QtGui, QtWidgets
class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(800, 600)
        self.centralwidget = QtWidgets.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")
        MainWindow.setCentralWidget(self.centralwidget)
        self.menubar = QtWidgets.QMenuBar(MainWindow)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 800, 23))
        self.menubar.setObjectName("menubar")
        MainWindow.setMenuBar(self.menubar)
        self.statusbar = QtWidgets.QStatusBar(MainWindow)
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)

        self.retranslateUi(MainWindow)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def retranslateUi(self, MainWindow):
        _translate = QtCore.QCoreApplication.translate
        MainWindow.setWindowTitle(_translate("MainWindow", "MainWindow"))

import sys
from PyQt5.QtWidgets import QApplication,QMainWindow
if __name__ == '__main__':
    app = QApplication(sys.argv)
    mainWindow = QMainWindow()
    ui = Ui_MainWindow()
    # 向主窗口上添加控件
    ui.setupUi(mainWindow)
    mainWindow.show()
    sys.exit(app.exec_())

```

运行上面的代码，效果如下所。这就是我们的第一个QT的GUI 应用


![](https://img-blog.csdnimg.cn/20200711221338872.png)
# 90、Python的GUI系列 _ QtDesigner进行界面设计
﻿@Author：Runsen


在很早之前就学过了PyQt5 ，我决定在更新了几篇PyQt5 。之前写的PyQt5 博客基本覆盖于此。这篇是九十篇、Python的GUI系列 | QtDesigner进行界面设计。离收官还有十篇。


## ui设计

如果只关注功能，做ui不难。难的是如何将ui做得漂亮，这不只是技术问题，还考验布局、配色、美工等一系列专业知识。在尝试了下美化控件的一些操作后，我果断放弃了，技术是个无底洞，还是关注最直接的需求吧
![](https://img-blog.csdnimg.cn/20200711222633690.png)



## 布局

PyQt5的界面布局主要有两种方法：绝对定位和局部类。在PyQt5中有四种布局方式：水平布局、垂直布局、网格布局、表单布局。还有两种布局方法：addLayout和addWidget，其中addLayout用于在布局中插入子布局，addWidget用于在布局中插入控件。

- 垂直布局：控件默认按照从上到下的顺序进行纵向添加。
 - 水平布局：控件默认按照从左到右的顺序进行横向添加。
- 栅格布局：将窗口分为若干行(row)和列(column)。
- 表单布局：控件以两列的形式布局在窗口中，左边为标签，右边为输入控件。


### 绝对布局

![](https://img-blog.csdnimg.cn/20200711222910671.png)

使用QWidget的move、setGeometry等方法，直接设置其在窗口中的位置。


下面就是一个绝对布局的代码

```csharp
import sys
from PyQt5.QtWidgets import *
class AbsoluteLayout(QWidget) :
    def __init__(self):
        super(AbsoluteLayout,self).__init__()
        self.setWindowTitle("绝对布局")
        self.label1 = QLabel('欢迎',self)
        self.label1.move(15,20)
        self.label2 = QLabel('学习',self)
        self.label2.move(35,40)
        self.label3 = QLabel('PyQt5',self)
        self.label3.move(55,80)
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = AbsoluteLayout()
    main.show()
    sys.exit(app.exec_())
```





###   水平盒布局

![](https://img-blog.csdnimg.cn/20200711224644654.png)
下面就是一个  水平盒布局的代码


```csharp
import sys
from PyQt5.QtWidgets import *
class HBoxLayout(QWidget) :
    def __init__(self):
        super(HBoxLayout,self).__init__()
        self.setWindowTitle("水平盒布局")
        hlayout = QHBoxLayout()
        hlayout.addWidget(QPushButton('按钮1'))
        hlayout.addWidget(QPushButton('按钮2'))
        hlayout.addWidget(QPushButton('按钮3'))
        hlayout.setSpacing(40)
        self.setLayout(hlayout)
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = HBoxLayout()
    main.show()
    sys.exit(app.exec_())
```


### 垂直盒布局

![](https://img-blog.csdnimg.cn/20200711225018350.png)


下面就是一个垂直盒布局的代码

```csharp
import sys
from PyQt5.QtWidgets import *
class VBoxLayout(QWidget) :
    def __init__(self):
        super(VBoxLayout,self).__init__()
        self.setWindowTitle("垂直盒布局")
        layout = QVBoxLayout()
        layout.addWidget(QPushButton('按钮1'))
        layout.addWidget(QPushButton('按钮2'))
        layout.addWidget(QPushButton('按钮3'))
        self.setLayout(layout)
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = VBoxLayout()
    main.show()
    sys.exit(app.exec_())
```

上面的QHBoxLayout 水平布局和QVBoxLayout 垂直布局都是盒子布局


代码方面

- stretch（伸缩量），只适用于QBoxLayout布局方式，控件和窗口会随着伸缩量的变大而增加
- alignment，指定对齐方式
- addLayout(self, QLayout, stretch=0)
- 在窗口的右边添加布局，使用stretch（伸缩量）进行伸缩，默认为0
- addWidget(self, QWidget, stretch, Qt.Alignment) 在布局中添加控件。

### 栅格布局

![](https://img-blog.csdnimg.cn/20200712225433344.png)

下面就是一个栅格布局的代码




```csharp
import sys
from PyQt5.QtWidgets import *
class Calc(QWidget) :
    def __init__(self):
        super(Calc,self).__init__()
        self.setWindowTitle("栅格布局")

        grid = QGridLayout()
        self.setLayout(grid)
        names = ['Cls','Back','','Close',
                 '7','8','9','/',
                 '4','5','6','*',
                 '1','2','3','-',
                 '0','.','=','+']
        positions = [(i,j) for i in range(5) for j in range(4)]
        print(positions)
        for position,name in zip(positions,names):
            if name == '':
                continue
            button = QPushButton(name)
            grid.addWidget(button,*position)
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = Calc()
    main.show()
    sys.exit(app.exec_())
```

![](https://img-blog.csdnimg.cn/2020071222550552.png)

QGridLayout 栅格布局



代码方法：

- addLayout(QLayout, row, column, Qt.Alignment)，在栅格布局的行(row)、列(column)位置添加新的布局，并设置对齐方式
- addLayout(QLayout, row, column, rowSpan, columnSpan, Qt.Alignment)，在栅格布局中新的布局，从行(row)、列(column)开始，占据rowSpan行、columnSpan列
- addWidget(QWidget, row, column, Qt.Alignment)，在栅格布局的行(row)、列(column)中添加窗口控件，
- addWidget(QWidget, fromRow, fromColumn, rowSpan, columnSpan, Qt.Alignment)，在栅格布局中添加窗口控件，从行(row)、列(column)开始，占据rowSpan行、columnSpan列
- setRowStretch(row, stretch)，在行(row)处添加伸缩量
- setColumnStretch(column, stretch)，在列(column)处添加伸缩量




### 表单布局


![](https://img-blog.csdnimg.cn/20200712230244485.png)


下面就是一个表单布局的代码










```csharp
import sys
from PyQt5.QtWidgets import *
class GridForm(QWidget) :
    def __init__(self):
        super(GridForm,self).__init__()
        self.setWindowTitle("栅格布局：表单设计")
        titleLabel = QLabel('标题')
        authorLabel = QLabel('作者')
        contentLabel = QLabel('内容')
        titleEdit = QLineEdit()
        authorEdit = QLineEdit()
        contentEdit = QTextEdit()
        grid = QGridLayout()
        grid.setSpacing(10)
        grid.addWidget(titleLabel,1,0)
        grid.addWidget(titleEdit,1,1)
        grid.addWidget(authorLabel,2,0)
        grid.addWidget(authorEdit,2,1)
        grid.addWidget(contentLabel,3,0)
        grid.addWidget(contentEdit,3,1,5,1)
        self.setLayout(grid)
        self.resize(350,300)

if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = GridForm()
    main.show()
    sys.exit(app.exec_())
```


![](https://img-blog.csdnimg.cn/20200712225742858.png)

其他布局对齐方式：


| 参数                   | 描述             |
| ---------------------- | ---------------- |
| QtCore.Qt.AlignLeft    | 水平方向居左对齐 |
| QtCore.Qt.AlignRight   | 水平方向居右对齐 |
| QtCore.Qt.AlignCenter  | 水平方向居中对齐 |
| QtCore.Qt.AlignJustify | 水平方向两端对齐 |
| QtCore.Qt.AlignTop     | 垂直方向靠上对齐 |
| QtCore.Qt.AlignBottom  | 垂直方向靠下对齐 |
| QtCore.Qt.AlignVCenter | 垂直方向居中对齐 |




### 菜单栏 Menu



```csharp
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtGui import *
from PyQt5.QtCore import *
class Menu(QMainWindow) :
    def __init__(self):
        super(Menu,self).__init__()
        bar = self.menuBar()  # 获取菜单栏
        file = bar.addMenu("文件")
        file.addAction("新建")
        save = QAction("保存",self)
        save.setShortcut("Ctrl + S")
        file.addAction(save)
        save.triggered.connect(self.process)
        edit = bar.addMenu("Edit")
        edit.addAction("copy")
        edit.addAction("paste")
        quit = QAction("退出",self)
        file.addAction(quit)
    def process(self):
        print(self.sender().text())
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = Menu()
    main.show()
    sys.exit(app.exec_())

```

![](https://img-blog.csdnimg.cn/20190511165209533.png)

### 工具栏

```csharp
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtGui import *
from PyQt5.QtCore import *
class Toolbar(QMainWindow) :
    def __init__(self):
        super(Toolbar,self).__init__()
        self.initUI()
    def initUI(self):
        self.setWindowTitle("工具栏例子")
        self.resize(300,200)
        tb1 = self.addToolBar("File")
        new = QAction(QIcon('./images/new.png'),"new",self)
        tb1.addAction(new)
        open = QAction(QIcon('./images/open.png'),"open",self)
        tb1.addAction(open)
        save = QAction(QIcon('./images/save.png'),"save",self)
        tb1.addAction(save)
        tb2 = self.addToolBar("File1")
        new1 = QAction(QIcon('./images/new.png'),"新建",self)
        tb2.addAction(new1)
        tb2.setToolButtonStyle(Qt.ToolButtonTextUnderIcon)
        tb1.actionTriggered.connect(self.toolbtnpressed)
        tb2.actionTriggered.connect(self.toolbtnpressed)
    def toolbtnpressed(self,a):
        print("按下的工具栏按钮是",a.text())
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = Toolbar()
    main.show()
    sys.exit(app.exec_())

```

![](https://img-blog.csdnimg.cn/20200712231738397.png)

# 91、Python的GUI系列 _ QT组件篇
﻿@Author：Runsen



在很早之前就学过了PyQt5 ，我决定在更新了几篇PyQt5 。之前写的PyQt5 博客基本覆盖于此。这篇九十一、Python的GUI系列 | QT组件篇。离收官还有九篇。

官方文档：https://riverbankcomputing.com/static/Docs/PyQt5/




## 主窗口


主窗口：一共有3种窗口

- QMainWindow：可以包含菜单栏、工具栏、状态栏和标题栏，是最常见的窗口形式

- QDialog：是对话窗口的基类。没有菜单栏、工具栏、状态栏。

- QWidget：不确定窗口的用途，就使用QWidget。






## 文本控件


```csharp
from PyQt5.QtWidgets import *
import sys
class QTextEditDemo(QWidget) :
    def __init__(self):
        super(QTextEditDemo,self).__init__()
        self.initUI()
    def initUI(self):
        self.setWindowTitle('QTextEdit控件演示')
        self.resize(300,320)
        self.textEdit = QTextEdit()
        self.buttonText = QPushButton('显示文本')
        self.buttonHTML = QPushButton('显示HTML')
        self.buttonToText = QPushButton('获取文本')
        self.buttonToHTML = QPushButton('获取HTML')
        layout = QVBoxLayout()
        layout.addWidget(self.textEdit)
        layout.addWidget(self.buttonText)
        layout.addWidget(self.buttonToText)
        layout.addWidget(self.buttonHTML)
        layout.addWidget(self.buttonToHTML)
        self.setLayout(layout)
        self.buttonText.clicked.connect(self.onClick_ButtonText)
        self.buttonHTML.clicked.connect(self.onClick_ButtonHTML)
        self.buttonToText.clicked.connect(self.onClick_ButtonToText)
        self.buttonToHTML.clicked.connect(self.onClick_ButtonToHTML)
    def onClick_ButtonText(self):
        self.textEdit.setPlainText('Hello World，世界你好吗？')
    def onClick_ButtonToText(self):
        print(self.textEdit.toPlainText())
    def onClick_ButtonHTML(self):
        self.textEdit.setHtml('<font color="blue" size="5">Hello World</font>')
    def onClick_ButtonToHTML(self):
        print(self.textEdit.toHtml())
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = QTextEditDemo()
    main.show()
    sys.exit(app.exec_())

```

![](https://img-blog.csdnimg.cn/20200713113035579.png)

##  文本输入框



```csharp
# QLineEdit控件与回显模式
from PyQt5.QtWidgets import *
import sys
class QLineEditEchoMode(QWidget) :
    def __init__(self):
        super(QLineEditEchoMode,self).__init__()
        self.initUI()
    def initUI(self):
        self.setWindowTitle('文本输入框的回显模式')
        formLayout = QFormLayout()
        normalLineEdit = QLineEdit()
        noEchoLineEdit = QLineEdit()
        passwordLineEdit = QLineEdit()
        passwordEchoOnEditLineEdit = QLineEdit()
        formLayout.addRow("Normal",normalLineEdit)
        formLayout.addRow("NoEcho", noEchoLineEdit)
        formLayout.addRow("Password",passwordLineEdit)
        formLayout.addRow("PasswordEchoOnEdit",passwordEchoOnEditLineEdit)
        normalLineEdit.setPlaceholderText("Normal")
        noEchoLineEdit.setPlaceholderText("NoEcho")
        passwordLineEdit.setPlaceholderText("Password")
        passwordEchoOnEditLineEdit.setPlaceholderText("PasswordEchoOnEdit")
        normalLineEdit.setEchoMode(QLineEdit.Normal)
        noEchoLineEdit.setEchoMode(QLineEdit.NoEcho)
        passwordLineEdit.setEchoMode(QLineEdit.Password)
        passwordEchoOnEditLineEdit.setEchoMode(QLineEdit.PasswordEchoOnEdit)
        self.setLayout(formLayout)
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = QLineEditEchoMode()
    main.show()
    sys.exit(app.exec_())


```

![](https://img-blog.csdnimg.cn/20200713112725795.png)


## 按钮控件





```csharp
#按钮控件（QPushButton）
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *
class QPushButtonDemo(QDialog) :
    def __init__(self):
        super(QPushButtonDemo,self).__init__()
        self.initUI()
    def initUI(self):
        self.setWindowTitle('QPushButton Demo')
        layout = QVBoxLayout()
        self.button1 = QPushButton('第1个按钮')
        self.button1.setText('First Button1')
        self.button1.setCheckable(True)
        self.button1.toggle()
        self.button1.clicked.connect(self.buttonState)
        self.button1.clicked.connect(lambda :self.whichButton(self.button1))
        layout.addWidget(self.button1)
        # 在文本前面显示图像
        self.button2 = QPushButton('图像按钮')
        self.button2.setIcon(QIcon(QPixmap('./images/python.png')))
        self.button2.clicked.connect(lambda:self.whichButton(self.button2))
        layout.addWidget(self.button2)
        self.button3 = QPushButton('不可用的按钮')
        self.button3.setEnabled(False)
        layout.addWidget(self.button3)
        self.button4 = QPushButton('&MyButton')
        self.button4.setDefault(True)
        self.button4.clicked.connect(lambda:self.whichButton(self.button4))
        layout.addWidget(self.button4)
        self.setLayout(layout)
        self.resize(400,300)
    def buttonState(self):
        if self.button1.isChecked():
            print('按钮1已经被选中')
        else:
            print('按钮1未被选中')
    def whichButton(self,btn):
        print('被单击的按钮是<' + btn.text() + '>')
if __name__ == '__main__':
    app = QApplication(sys.argv)
    main = QPushButtonDemo()
    main.show()
    sys.exit(app.exec_())


```

![](https://img-blog.csdnimg.cn/20200713112843181.png)




## 完成计算器Demo




```csharp
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/7/13
'''
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QToolTip, QLineEdit, QMessageBox, QDesktopWidget, QTextEdit
from PyQt5.QtGui import  QFont
from PyQt5.QtCore import QCoreApplication
class Calculater(QWidget):
    def __init__(self):
        super().__init__()
        self.setUI()

    def setUI(self):
        QToolTip.setFont(QFont('SansSerif', 10))
        Font = QFont('SansSerif', 18)
        self.resize(500, 400)
        self.move(100, 100)
        self.setWindowTitle("Calculater")
        self.center()
        self.line = QLineEdit(self)
        self.line.resize(480, 80)
        self.line.move(10, 10)
        self.line.setFont(Font)

        self.Text = QTextEdit(self)
        self.Text.resize(480, 280)
        self.Text.move(10, 110)
        self.Text.setFont(Font)
        self.Text.setText(str(0))

        self.line.textChanged.connect(self.calculate)
        self.show()

    def calculate(self):
        s = self.line.text()
        if len(s) == 0:
            self.Text.setText(str(0))
            return False
        s = s.replace('^', '**')  # 使得能够接受^这样的用法
        try:
            ans = eval(s)
        except:
            return False
        else:
            self.Text.setText(str(ans))

    def center(self):
        qr = self.frameGeometry()
        cp = QDesktopWidget().availableGeometry().center()
        qr.moveCenter(cp)
        self.move(qr.topLeft())

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Calculater()
    sys.exit(app.exec_())
```



![](https://img-blog.csdnimg.cn/20200713112553900.gif)

# 92、Python爬取深圳租房信息小案例
﻿@Author：Runsen




今天介绍的是Python中的爬虫小例子，离收官还有八篇。


## 1、前言


在某日夏天的夜晚、突然有妹子加我微信，原来竟然叫我帮忙写作业。




![](https://img-blog.csdnimg.cn/20200628124023811.png)



对于，我这个屌丝来说，还是花个半小时帮忙搞定下。爬取的网站又是链家网，你看我直接不是早已写成博客了吗？

![](https://img-blog.csdnimg.cn/20200628124340804.png)


我想对链家网说：链家网求你不要再害大家爬你的，真的让广大学生都是讨厌你。

爬取的链接是：https://sz.lianjia.com/zufang/

![](https://img-blog.csdnimg.cn/20200628124603502.png)

什么租房经纪人成交数据有吗？我看老师都是傻傻的不知道乱搞一通。难为是我啊？没有的东西爬了毛？


## 2、明确爬取的信息

在链家网的租房信息中，有如下的信息，我都圈出来了。
![](https://img-blog.csdnimg.cn/2020062812485470.png)

明确爬取的信息，分别有整租，我就叫类型算了。新城花园就叫名称， 面积就是101，朝向南，

3室1厅1卫就叫房间数，价格每个月1800，真贵。反正我这种穷人要不起。





## 3、 Requests访问链接


Requests库就是发请求的库，需要加上请求头，这样就不用禁止了。


根据每个页面的网址发现就是换了一个pg参数。比如，第一页的网址是`https://sz.lianjia.com/zufang/pg0`，

那么第二页就是`https://sz.lianjia.com/zufang/pg1`，那么就是傻瓜式构造。我们爬它个100页，代码如下。





```java
for i in range(1, 101):
     page_url = 'https://sz.lianjia.com/zufang/pg{}'.format(i)
     res = requests.get(page_url, headers=headers)
```

## 4、 xpath解析内容

返回的页面就需要解析，我经常用的说xpath，至于bs4赶紧忘记算了。



具体解析过程如下图所示。


![](https://img-blog.csdnimg.cn/20200628183147843.png)



## 5、保存数据

我们选择用csv来保存数据，通过`with open('demo.csv', 'a+') as f`进行创建csv，然后通过`f.write`进行写入爬取的数据。


最终保存数据如下图所示。
![](https://img-blog.csdnimg.cn/20200628183414740.png)


## 6、全部代码



```python
'''
@Author： Runsen
@微信公众号： Python之王
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/6/27
'''
import requests
from lxml import etree

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/77.0.3865.90 Safari/537.36'
}
with open('demo.csv', 'a+') as f:
    f.write(
        '类型' + ',' + '名称' + ',' + '地点' + ',' + '面积' + ',' + '朝向' + ',' + '房间数' + ',' + '价格' + '\n')
    for i in range(1, 101):
        page_url = 'https://sz.lianjia.com/zufang/pg{}'.format(i)

        res = requests.get(page_url, headers=headers)
        # 这里千万不要判断res的状态码200
        page = etree.HTML(res.text)
        content = page.xpath("//a[@class='content__list--item--aside']/@title")

        where1 = page.xpath("//p[@class='content__list--item--des']/a[1]/text()")
        where2 = page.xpath("//p[@class='content__list--item--des']/a[2]/text()")
        where3 = page.xpath("//p[@class='content__list--item--des']/a[3]/text()")
        squares = page.xpath("//p[@class='content__list--item--des']/text()[5]")
        decorates = page.xpath("//p[@class='content__list--item--des']/text()[6]")
        nums = page.xpath("//p[@class='content__list--item--des']/text()[7]")
        Prices = page.xpath("//span[@class='content__list--item-price']/em/text()")
        for j,w1,w2 , w3,s,d, n, Price in zip(content, where1, where2,where3, squares, decorates,nums,Prices):
            type = j.replace("·", " ").split(" ")[0]
            name = j.replace("·", " ").split(" ")[1]
            location = w1+ w2 + w3
            square = s.replace("\n", "").replace(" ", "")
            decorate =d.replace(" ", "")
            num = n.replace("\n", "").replace(" ", "")
            price = Price+ "元/月"
            print("正在写入 :" + type + ',' + name + ',' + location + ',' + square + ',' + decorate + ',' + num + ',' + price +  '\n')
            f.write(type + ',' + name + ',' + location + ',' + square + ',' + decorate + ',' + num + ',' + price +  '\n')
```

# 93、Python使用百度云接口API实现截图，文字识别和语音合成


@Author：Runsen


在实际的业务中，难免会跟第三方系统进行数据的交互与传递，其实就是写接口API的。今天就开始第九十三篇、Python使用百度云接口API实现截图，文字识别和语音合成




## 接口RESTful API


随着微信以及各种数据平台的兴起，大家对跟这些平台对接的需求越来越多。目前，包括以上平台在内的一些主流公共平台都会以一种 REST 架构原则，向大众提供对接的接口。这种符合 REST 风格的接口，就称为 RESTful API。




比如注册百度云帐号，打开百度云平台：https://login.bce.baidu.com/reg.html?tpl=bceplat&from=portal进行账号注册


记住:    AppID，API Key，Secret Key

上面三个就是用户的接口。






## 安装keyboard

下面我们实现Python使用百度云接口API实现截图，文字识别的功能。需要安装keyboard。

keyboard是一个监控键盘输入的库


安装：`pip install keyborad`


执行下面的代码就是可以截图了。

```python
import keyboard
import time
from PIL import ImageGrab
def screen():
    print('开始截图')
    # 使用微信的截图热键
    keyboard.wait(hotkey='alt+a')
    # 保存
    keyboard.wait(hotkey='enter')
    # 图片保存需要时间
    time.sleep(0.5)
    # 读取剪切板的图片
    image = ImageGrab.grabclipboard()
    # 保存图片
    image.save('screen.jpg')
    print('图片保存完成')
screen()
```

当在键盘敲ctrl+a来得到图片


![](https://img-blog.csdnimg.cn/20190502231944769.png)

截取的图片

![](https://img-blog.csdnimg.cn/20190502232009661.png)


## 文字识别

下面我使用百度云来进行识别

为什么用百度云，因为百度的技术，阿里的运营，腾讯的产品。技术当然选百度云，而且识别效果比较高。




![](https://img-blog.csdnimg.cn/20190502232210590.png)



![](https://img-blog.csdnimg.cn/20190502232100232.png)


要安装百度的接口：[官方的教程](https://cloud.baidu.com/doc/OCR/OCR-Python-SDK.html#.E6.8E.A5.E5.8F.A3.E8.AF.B4.E6.98.8E)：https://cloud.baidu.com/doc/OCR/OCR-Python-SDK.html#.E6.8E.A5.E5.8F.A3.E8.AF.B4.E6.98.8E


下面就是教程的模板。

```python
from aip import AipOcr

""" 你的 APPID AK SK """
APP_ID = ''
API_KEY = ''
SECRET_KEY = ''

client = AipOcr(APP_ID, API_KEY, SECRET_KEY)



"""读取图片"""

def get_file_content(filepath):
    with open(filepath,'rb') as f:
        return f.read()



def get_img_content(img):

    image_content=''
    content = client.basicAccurate(image=img)
    # print(content)
    for words in content['words_result']:
        print(words)  # 字典
        image_content += words['words']
    print(image_content)
    
```

![](https://img-blog.csdnimg.cn/20190502232738379.png)

下面就是将截图整合到其中，封装全代码。

```python
# -*- coding：utf-8 -*-
# time ：2019/5/2 23:02
# author: 毛利


import keyboard
import time
from PIL import ImageGrab
def screen():
    print('开始截图')
    # 使用微信的截图热键
    keyboard.wait(hotkey='alt+a')
    # 保存
    keyboard.wait(hotkey='enter')
    # 图片保存需要时间
    time.sleep(0.5)
    # 读取剪切板的图片
    image = ImageGrab.grabclipboard()
    # 保存图片
    image.save('screen.jpg')

# 使用百度云中的文字识别
from aip import AipOcr

""" 你的 APPID AK SK """
APP_ID = ''   #你的账号的id
API_KEY = ''
SECRET_KEY = ''

client = AipOcr(APP_ID, API_KEY, SECRET_KEY)



"""读取图片"""

def get_file_content(filepath):
    with open(filepath,'rb') as f:
        return f.read()



def get_img_content(img):

    image_content=''
    content = client.basicAccurate(image=img)
    # print(content)
    for words in content['words_result']:
        # print(words)  # 字典
        image_content += words['words']
    print(image_content)

if __name__ == '__main__':
    screen()
    img = get_file_content('screen.jpg')
    get_img_content(img)
```




下面就是具体的使用：
![](https://img-blog.csdnimg.cn/20190502233844342.png)



![](https://img-blog.csdnimg.cn/20190502233919839.png)




## 语言合成



百度AP开发平台（ai.baidu.com）,注册成功之后，点击控制台，进入到百度云-管理中心。就可以创建应用了。
我这里创建了一个带有语音接口的应用：[官方教程](https://ai.baidu.com/docs#/ASR-Online-Python-SDK/top)


https://ai.baidu.com/docs#/ASR-Online-Python-SDK/top

![](https://img-blog.csdnimg.cn/20200713115655335.png)


![](https://img-blog.csdnimg.cn/20200713115719836.png)


具体代码如下。


```csharp
from aip import AipSpeech
app_id = ""
api_key = ""
secret_key = ""
client = AipSpeech(app_id, api_key, secret_key)
result = client.synthesis("好好学习，天天向上爱", "zh", 1, {
    "vol": 9,
    "spd": 6,
    "pit": 7,
    "per": 4,
})
with open("audio.mp3", "wb") as f:
    f.write(result)

```

![](https://img-blog.csdnimg.cn/20200713115750256.png)

音频的内容就是好好学习，天天向上


就是这么简单，不知道你学会了没有。

# 94、一文带你玩转简单的flask

﻿@Author：Runsen

## Flask介绍

Flask是一个基于Python开发并且依赖jinja2模板和Werkzeug WSGI服务的一个微型框架，对于Werkzeug本质是Socket服务端，其用于接收http请求并对请求进行预处理，然后触发Flask框架，开发人员基于Flask框架提供的功能对请求进行相应的处理，并返回给用户，如果要返回给用户复杂的内容时，需要借助jinja2模板来实现对模板的处理，即：将模板和数据进行渲染，将渲染后的字符串返回给用户浏览器。


优点：

- 有非常齐全的官方文档，上手非常方便

- 有非常好的拓展机制和第三方的拓展环境，工作中常见的软件都有对应的拓展，自己动手实现拓展也很容易

微型框架的形式给了开发者更大的选择空间

## Flask安装

虚拟环境搭建

```csharp
virtualenv --no-site-packages flaskenv
```

激活windows下虚拟环境

```csharp
cd Scripts
activate
```

执行
`pip install flask`

快速入门

```csharp
import flask # 导入flask

app = flask.Flask(__name__) # 实例化

@app.route('/')# 装饰器实现路由
def helo():
    return '你好，我是Flask!'

if __name__ == '__main__':
    app.run()
```

```csharp
Serving Flask app "main" (lazy loading)
Environment: production
WARNING: Do not use the development server in a production environment.
Use a production WSGI server instead.
Debug mode: off
Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191017090936933.png)

### url参数快递

```csharp
import flask

app = flask.Flask(__name__)

@app.route('/')
@app.route('/hello') # 实现url地址
def helo():
    return '你好，我是Flask!'

if __name__ == '__main__':
    app.run()
```


一个函数可以有多个url的装饰器来修饰

```csharp
import flask

html_txt = """
<!DOCTYPE html>
<html>
    <body>
        <h2>收到GET请求</h2>
        <form method='post'>
        <input type='submit' value='发送POST请求' />
        </form>
    </body>
</html>
"""

app = flask.Flask(__name__)

@app.route('/hello',methods=['GET','POST'])
def helo():
    if flask.request.method == 'GET':
        return html_txt
    else:
        return '收到POST请求，我是Flask!'

if __name__ == '__main__':
    app.run()
```


![](https://img-blog.csdnimg.cn/20191017091055715.png)

### 两种请求映射同一函数

```csharp
import flask

html_txt = """
<!DOCTYPE html>
<html>
    <body>
        <h2>收到GET请求</h2>
        <form method='post'>
        <input type='submit' value='发送POST请求' />
        </form>
    </body>
</html>
"""

app = flask.Flask(__name__)

@app.route('/hello',methods=['GET','POST'])
def helo():
    if flask.request.method == 'GET':
        return html_txt
    else:
        return '收到POST请求，我是Flask!'

if __name__ == '__main__':
    app.run()
```


![](https://img-blog.csdnimg.cn/20191017091158155.png)

```csharp
请求url传递的参数

import flask

app = flask.Flask(__name__)

@app.route('/hello/<name>')
def helo(name):
    return "你好," + name + '!'

if __name__ == '__main__':
    app.run()
```


![](https://img-blog.csdnimg.cn/20191017091248476.png)


**获取get请求参数的基本方式调用flask.request.args的get方法**

获得post请求使用flask.

```csharp
import flask

html_txt = """
<!DOCTYPE html>
<html>
    <body>
        <h2>收到GET请求</h2>
        <form method='post'>
        <input type='text' name='name' placeholder='请输入你的姓名' />
        <input type='submit' value='发送POST请求' />
        </form>
    </body>
</html>
"""

app = flask.Flask(__name__)

@app.route('/hello',methods=['GET','POST'])
def helo():
    if flask.request.method == 'GET':
        return html_txt
    else:
        name = 'name' in flask.request.form and flask.request.form['name']
        if name:
            return '你是：' + name + '!'
        else:
            return '你没有输入姓名！'

if __name__ == '__main__':
    app.run(debug=True)

```

## 使用cookie和session

### 使用cookie

```python
import flask

html_txt = """
<!DOCTYPE html>
<html>
    <body>
        <h2>收到GET请求</h2>
        <a href='/get_info'>获取cookie信息</a>
    </body>
</html>
"""

app = flask.Flask(__name__)

@app.route('/set_info/<name>')
def set_cks(name):
    name = name if name else 'anonymous'
    resp = flask.make_response(html_txt)
    resp.set_cookie('name',name)
    return resp

@app.route('/get_info')
def get_cks():
    name = flask.request.cookies.get('name')
    return '获取的cookie信息是:' + name

if __name__ == '__main__':
    app.run(debug=True)

```

### 使用session

```python
import flask

html_txt = """
<!DOCTYPE html>
<html>
    <body>
        <h2>收到GET请求</h2>
        <a href='/get_info'>获取会话信息</a>
    </body>
</html>
"""

app = flask.Flask(__name__)

@app.route('/set_info/<name>')
def set_cks(name):
    name = name if name else 'anonymous'
    flask.session['name'] = name
    return html_txt

@app.route('/get_info')
def get_cks():
    name = 'name' in flask.session and flask.session['name']
    if name:
        return '获取的会话信息是:' + name
    else:
        return '没有相应会话信息。'

if __name__ == '__main__':
    app.secret_key = 'dfadff#$#5dgfddgssgfgsfgr4$T^%^'
    app.run(debug=True)

```

![](https://img-blog.csdnimg.cn/20191017091428178.png)

## 渲染模板

```python
import flask

app = flask.Flask(__name__)

@app.route('/hello')
def helo():
    return flask.render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)

```

![](https://img-blog.csdnimg.cn/20191017091452374.png)## 实战练习（实现文件上传）

```python
import flask

app = flask.Flask(__name__)

@app.route('/upload',methods=['GET','POST'])
def upload():
    if flask.request.method == 'GET':
        return flask.render_template('upload.html')
    else:
        file = flask.request.files['file']
        if file:
            file.save(file.filename)
            return '上传成功！'

if __name__ == '__main__':
    app.run(debug=True)

```


![](https://img-blog.csdnimg.cn/20191017091550412.png)



代码：https://github.com/MaoliRUNsen/maoli/tree/master/flask%E5%85%A5%E9%97%A8

# 95、轻松搞定Python中的Excel办公自动化系列
﻿@Author：Runsen


这篇是九十五篇、轻松搞定Python办公自动化系列。离收官还有五篇。




python针对excel有很多的第三方库可以用，比如openpyxl，xlwings、xlsxwriter、xlrd、xlwt、pandas、xlsxwriter、win32com、xlutils等等。

## openpyxl

我主要介绍openpyxl库的几类常见方法。


```csharp
from openpyxl import load_workbook
wb = load_workbook("学生表.xlsx")
#打开工作表两种方式：
#方式一：通过工作表名称打开工作表
sheet=wb["sheet1"]
#方式二：获取活跃的工作表
sheet=wb.active    #['sheet1']
#获取所有的工作表
wb.sheetnames    #['sheet1']
#修改工作表名称
sheet.title="students"    
#获取工作表名称
sheet.title    #students
# 获取单元格（指定行，指定列）
sheet.cell(2,3)    #<Cell 'students'.C2>
#方式一
sheet.cell(2,3).value    #60
#方式二
sheet["C2"].value    #60
# 往单元格（指定行，指定列）中写入值
#方式一
sheet.cell(2,4).value="及格"
#方式二
sheet["D3"]="及格"
#方式三
sheet.cell(4,4,"良好")
#保存工作簿
wb.save("学生表.xlsx")
```


![](https://img-blog.csdnimg.cn/20200714113548360.png)

## xlrd&xlwt&xlutils 

xlrd&xlwt&xlutils 顾明思意是由以下三个库组成：

- xlrd：用于读取 Excel 文件；
- xlwt：用于写入 Excel 文件；
- xlutils：用于操作 Excel 文件的实用工具，比如复制、分割、筛选等；



接下来我们就从写入 Excel 开始，话不多说直接看代码如下：


```csharp
# 导入 xlwt 库
import xlwt

# 创建 xls 文件对象
wb = xlwt.Workbook()

# 新增两个表单页
sh1 = wb.add_sheet('成绩')
sh2 = wb.add_sheet('汇总')

# 然后按照位置来添加数据,第一个参数是行，第二个参数是列
# 写入第一个sheet
sh1.write(0, 0, '姓名')
sh1.write(0, 1, '成绩')
sh1.write(1, 0, '张三')
sh1.write(1, 1, 88)
sh1.write(2, 0, '李四')
sh1.write(2, 1, 99.5)

# 写入第二个sheet
sh2.write(0, 0, '总分')
sh2.write(1, 0, 187.5)

# 最后保存文件即可
wb.save('test.xls')
```




![](https://img-blog.csdnimg.cn/20200714114209451.png)

![](https://img-blog.csdnimg.cn/20200714114230563.png)

读取 Excel 其实也不难，请看如下代码：

```csharp
# 导入 xlrd 库
import xlrd

# 打开刚才我们写入的 test_w.xls 文件
wb = xlrd.open_workbook("test.xls")

# 获取并打印 sheet 数量
print( "sheet 数量:", wb.nsheets)

# 获取并打印 sheet 名称
print( "sheet 名称:", wb.sheet_names())

# 根据 sheet 索引获取内容
sh1 = wb.sheet_by_index(0)
# 或者
# 也可根据 sheet 名称获取内容
# sh = wb.sheet_by_name('成绩')

# 获取并打印该 sheet 行数和列数
print( u"sheet %s 共 %d 行 %d 列" % (sh1.name, sh1.nrows, sh1.ncols))

# 获取并打印某个单元格的值
print( "第一行第二列的值为:", sh1.cell_value(0, 1))

# 获取整行或整列的值
rows = sh1.row_values(0) # 获取第一行内容
cols = sh1.col_values(1) # 获取第二列内容

# 打印获取的行列值
print( "第一行的值为:", rows)
print( "第二列的值为:", cols)

# 获取单元格内容的数据类型
print( "第二行第一列的值类型为:", sh1.cell(1, 0).ctype)

# 遍历所有表单内容
for sh in wb.sheets():
    for r in range(sh.nrows):
        # 输出指定行
        print( sh.row(r))
```

修改时就需要用到 xlutils 中的方法了。直接上代码，来看下最简单的修改操作：

```csharp
# 导入相应模块
import xlrd
from xlutils.copy import copy

# 打开 excel 文件
readbook = xlrd.open_workbook("test.xls")

# 复制一份
wb = copy(readbook)

# 选取第一个表单
sh1 = wb.get_sheet(0)

# 在第四行新增写入数据
sh1.write(3, 0, '王亮')
sh1.write(3, 1, 59)


# 保存
wb.save('test.xls')
```


![](https://img-blog.csdnimg.cn/20200714114349468.png)




## 合并文件夹中的多个Excel文件

一两个直接用excel不合并表的功能简单的要死！上百个用代码。数据涉及到隐私，这里不说了。就是很多个excel。


```csharp
import os
import xlwt
import xlrd
import xlutils.copy
import time
"""
需求：
    1. 将上千个Excel表合并成一个表里
    2. 不管你用什么方法，实现效果就行
思路分析：
    1. 创建一个空表名叫"总表"，表格形式须和合并表的一样
    2. 获取需要合并文件夹中的所有excel表的名字（文件名)
    3. 开始遍历excel表
    4. 先读取数据，然后写入事先创建好总表中
    5. 当读取完下一个待合并表的数据，然后准备写入到总表时，必须先获取到总表的行数，不然之前的数据将会被覆盖掉。
    6. 遍历结束，保存总表的数据
项目运行：
    1. 将所有需要合并的表放到一个文件夹中，名叫excels
    2. autoMerge.py文件和excels文件夹同级
    3. 运行该.py文件，会在把合并表放到destDir夹中
"""

# 1.总表初始化(不友好，还需要自行写好表头列表，对非程序员不友好)
def initExcel(path,excelTitle,excel_sheet_Name):
    """
    :param path: 合并总表的路径
    :param excelTitle: 总表的表头
    :param excel_sheet_Name: 合并总表的sheet名称
    :return: 返回总表是否初始化成功
    """
    try:
        # 创建一个工作簿
        book = xlwt.Workbook(encoding="utf-8")
        # 创建表单
        sheet = book.add_sheet(excel_sheet_Name)
        # 写入表头
        for i in range(0,len(excelTitle)):
            sheet.write(0, i, excelTitle[i])
        book.save(path)
        return True
    except Exception as e:
        return False

# 1.1 总表初始化(用来解决上面的问题)
def initExcel2(destExcel_path, sourceExcel_path,total_sheet_name):
    """
    :param destExcel_path: 合并总表excel的路径
    :param sourceExcel_path: 需要合并excel的路径
    :param total_sheet_name: 合并总表后sheet的名字
    :return: 返回False or True
    """
    try:
        # 创建一个工作簿
        book = xlwt.Workbook(encoding="utf-8")
        # 创建表单,并给表单起个名字
        sheet = book.add_sheet(total_sheet_name)
        # 获取待需合并excel的所有文件
        excel_name_list = get_All_Excelname(sourceExcel_path)
        # 一个待合并execl的路径
        excel_path = sourceExcel_path + "/" + excel_name_list[0]
        # 获取excel的sheet
        excel_sheet = get_excel_sheet(excel_path)
        # 获取excel的表头数据
        excel_title_list = excel_sheet.row_values(0)
        # 写入表头
        for i in range(0,len(excel_title_list)):
            sheet.write(0, i, excel_title_list[i])
        book.save(destExcel_path)
        return True
    except Exception as e:
        return False

# 2.获取需要合并的所有的excel文件名
def get_All_Excelname(path):
    """

    :param path: 待合并excel文件的路径
    :return:
    """
    excelName_list = os.listdir(path)
    # print(excelName_list)
    return excelName_list


# 返回excel表的sheet对象
def get_excel_sheet(path):
    # 打开指定路径的excle表
    book = xlrd.open_workbook(path)
    # 获取excle中的表单
    sheet = book.sheet_by_index(0)
    # 返回sheet对象
    return sheet

# 返回总表的wtbook,sheet对象
def get_total_excel_sheet(path):
    """

    :param path: 存放总表的path
    :return:
    """
    book = xlrd.open_workbook(path, formatting_info=True)
    wtbook = xlutils.copy.copy(book)
    wtsheet = wtbook.get_sheet(0)
    return wtbook,wtsheet



# 4. 开始遍历(合并excel表)
def writeExcel(destExcel_path,source_path,excelName_list):
    """

    :param destExcel_path: 合并总表存放的路径
    :param source_path: 需要合并excel的路径
    :param excelName_list: 需要合并excel表的文件名称
    :return:
    """
    # 用来记录总表中的行数
    total_excel_row = 1
    # 获取总表的book,sheet
    total_book,total_sheet = get_total_excel_sheet(destExcel_path)
    for excelName in excelName_list:
        # 文件路径
        excelPath = source_path + excelName
        # 获取表的sheet对象
        sheet = get_excel_sheet(excelPath)
        # 获取行数
        n_rows = sheet.nrows
        # 开始遍历读取数据，并写入数据
        for row_index in range(1,n_rows):
            # 获取一行的数据，列表形式
            row_data_list = sheet.row_values(row_index)
            # 将数据写入到总表中
            for j in range(0,len(row_data_list)):
                total_sheet.write(total_excel_row,j,str(row_data_list[j]))
            # 每写一行，总表行数加1
            total_excel_row = total_excel_row + 1
    total_book.save(destExcel_path)
    print("数据合并已完成")
    print("合并后的数据共有%d条" % (total_excel_row - 1))

# 创建文件夹
def makeDir(path):
    """
    :param path: 传入需要创建文件夹的路径
    :return:
    """
    if not os.path.exists(path):
        os.mkdir(path)

def main():
    # 待需合并的excel文件夹路径
    source_excel_path = "./excels/"
    # 存放合并后的excel表文件夹路径
    dest_dir = "./destDir"
    # 创建文件夹
    makeDir(dest_dir)
    # 合并excel表名
    total_excel_name = "总表.xls"
    # 合并表存放路径
    total_excel_path = dest_dir + "/" + total_excel_name
    # 合并总表中的sheet的名字
    total_excel_sheet_name = "汇总表"
    # 初始化表
    flag = initExcel2(total_excel_path,source_excel_path,total_excel_sheet_name)
    if flag:
        excelName_list = get_All_Excelname("./excels")
        # 打印有多少个excel表
        print("总共有%d个excel表需要合并" %len(excelName_list))
        # 写数据
        writeExcel(total_excel_path,source_excel_path, excelName_list)
    else:
        print("初始化表失败")


if __name__ == '__main__':
    main()
    time.sleep(3)
```

# 96、轻松搞定Python中的PPT办公自动化系列

﻿@Author：Runsen


这篇是九十六、轻松搞定Python中的PPT办公自动化系列。离收官还有四篇。


##  安装python-pptx

python-pptx就是为了进行PPT的操作而生，下面大致介绍一下这个python库。安装就是`pip install python-pptx`。下面以两个例子大致了解一下这个库中某些函数的用法。第一个例子用来讲述向幻灯片中增加基本内容；

```csharp
from pptx import Presentation # 导入库

prs = Presentation() # 创建PPT文档

# 对幻灯片进行布局
title_slide_layout = prs.slide_layouts[0] 
slide = prs.slides.add_slide(title_slide_layout)
title = slide.shapes.title
subtitle = slide.placeholders[1]

# 各各部分添加内容
title.text = "Hello, World!"
subtitle.text = "我是python-pptx!"

prs.save('增加内容.pptx') # 保存PPT文档
```


![](https://img-blog.csdnimg.cn/20200714121431696.png)



第二个例子用来介绍向幻灯片中增加一个表格，代码如下。


```csharp
from pptx import Presentation
from pptx.util import Inches

prs = Presentation()
title_only_slide_layout = prs.slide_layouts[5]
slide = prs.slides.add_slide(title_only_slide_layout)
shapes = slide.shapes

shapes.title.text = '增加一个表格'

rows = cols = 3
left = top = Inches(2.0)
width = Inches(6.0)
height = Inches(0.8)

table = shapes.add_table(rows, cols, left, top, width, height).table

# 设置表格列宽
table.columns[0].width = Inches(2.0)
table.columns[1].width = Inches(2.0)
table.columns[2].width = Inches(2.0)

# 表格头
table.cell(0, 0).text = '姓名'
table.cell(0, 1).text = '年龄'

# 添加表格内容
table.cell(1, 0).text = '张三'
table.cell(1, 1).text = '42'

table.cell(2,0).text = '李四'
table.cell(2,1).text = '24'

prs.save('增加表格.pptx') # 保存PPT
```

![](https://img-blog.csdnimg.cn/20200714121544672.png)


python-pptx学习网站：https://python-pptx.readthedocs.io/en/latest/

## 将一个PPT文件中的所有文字批量导出


有时，我们需要将一个PPT文件中的所有文字批量导出，以便查看，或者复制什么的。一页一页PPT去复制粘贴，会很不方便。下面我们就来试试用Python搞定这个吧。


使用的文件是我化工专业的设备材料选择的东西。
![](https://img-blog.csdnimg.cn/20200714122326305.png)

下面的代码已经将名字改为`测试.pptx`

```csharp
#提取所有文本字符
from pptx import Presentation
data = []
prs = Presentation('测试.pptx')
for slide in prs.slides: #遍历每页PPT
    for shape in slide.shapes: #遍历PPT中的每个形状
        if shape.has_text_frame: #判断该是否包含文本，保证有文本才提取
            for paragraph in shape.text_frame.paragraphs: #按文本框中的段落提取
                data.append(paragraph.text) #提取一个段落的文本，就存到列表data中

#写入文本文件
TxtFile = open('测试.txt', 'w',encoding='utf-8')
for i in data:
    TxtFile.write(i+'\n') #写入并换行，以保证正确分段
TxtFile.close() #保存

#写入word文件
import docx
doc=docx.Document()#创建一个word文件对象
for i in data:
    doc.add_paragraph(i) #增加一个段落，并将列表中的一个字符串写入word文件
doc.save('测试.docx')#保存
```

![](https://img-blog.csdnimg.cn/20200714125031419.png)


# 97、轻松搞定Python中的PDF办公自动化系列

﻿@Author：Runsen


这篇是九十七、轻松搞定Python中的PDF办公自动化系列。离收官还有三篇。


## pdfminer3k


PDF的基本操作主要是读取、创建，合并等操作。使用Python的第三方包pdfminer3k读写合并PDF文件变得非常简单。这里不推荐使用PyPDF2，因为现在完全不维护的样子。


安装 pdfminer3k

```csharp
pip install pdfminer3k
```

## 读取PDF

我是使用的是我的专业课程设计 `化工原理课程换热器设计.pdf `，具体内容如下。

![](https://img-blog.csdnimg.cn/20200715100841782.png)



还有的是PyPDF2 是不能读取中文的，只能提取英文字符串。因此我建议使用pdfminer来读取中文。下面代码就是提取PDF的文字到txt文件中。

```csharp
from pdfminer.pdfinterp import PDFResourceManager, process_pdf
from pdfminer.converter import TextConverter
from pdfminer.layout import LAParams
from io import StringIO


def convert_pdf(path):
    rsrcmgr = PDFResourceManager()
    retstr = StringIO()
    laparams = LAParams()
    device = TextConverter(rsrcmgr, retstr, laparams=laparams)
    fp = open(path, 'rb')
    process_pdf(rsrcmgr, device, fp)

    fp.close()
    device.close()
    out = retstr.getvalue()
    retstr.close()
    return out


a = convert_pdf('化工原理课程换热器设计.pdf')
with open("a.txt" ,'w',encoding='utf-8') as f:
    f.write(a)

```


![](https://img-blog.csdnimg.cn/20200715102714360.png)
# 98、轻松搞定Python中的Markdown系列

﻿@Author：Runsen



这篇是九十八、轻松搞定Python中的Markdown系列。离收官还有二篇。





## tomd

本文是介绍tomd工具，大家可以去看[其](https://github.com/gaojiuli/tomd/)README的中文翻译。

安装


```csharp
pip install tomd
```

这个tomd应该是一个人开发的。直接看官方的示例，这里不罗嗦了，其实很简单的。




## 将md批量转为docx


将markdown快速转为word格式，可以使用小工具pandoc, 非常好用, 这个是我在文本编辑器Typora导出功能发现的。





比如我有一个名为Python资料.md的文件, 我只需在命令行运行

```csharp
pandoc Python资料.md -o Python资料.docx
```

pandoc支持相互转换的格式, 多的惊人!




但是如果用命令，那么一个一个的就是傻逼式行为，我就拿之前的文章做一个小示例。

![](https://img-blog.csdnimg.cn/20200715190539619.png)


下面就是简化的操作的代码。

```csharp
import os

# 当前目录下所有文件的名字
all_files_name = os.listdir()

# 保存所有md文件的名字
all_md_files = []

# 获取目录下的md文件, 并保存
for file_name in all_files_name:
    try:
        if file_name[-3:] == ".md":
            all_md_files.append(file_name)
    except Exception as e:
        print(e)
# 将md文件批量装换为docx
for md_file in all_md_files:
    try:
        tmp_doc_name = md_file[0: -3] + ".docx"
        new_command = "pandoc "+ md_file + " -o " + tmp_doc_name
        result = os.popen(new_command).readlines()
        if len(result) == 0:
            print(md_file, "转换成功")
    except Exception as e:
        print(e)
```


运行结果
![](https://img-blog.csdnimg.cn/20200715191111381.png)

下面就是结果图



![](https://img-blog.csdnimg.cn/20200715191122461.png)




最后补充下关于Markdown的操作



- \#：此为Markdown中的标题语法，但是只支持到四级标题。
- -：此为Markdown中的无须项目符号语法，笔者在此保留并进行拓展，和标题类似，可以键入多个减号来实现多级项目符号，最多三级。
- **：此为Markdown中的粗体语法，笔者在此保留并简化，规定此语法只能在正文段落中使用。
- $：此为Markdown中的Latex公式语法，笔者在此保留，为了便于添加到Word中，此处将公式转化为图片。
- !:此为Markdown中的图片语法的简化写法


在此也向读者安利一个Markdown文本编辑器Typora，非常好用！不是打广告。
# 99、Python所学经验分享
﻿@Author：Runsen







这是倒数第二篇，Python所学经验分享。





## 关于我

某不知名 辣鸡大学的大三学生，读的是化工专业。目前学分绩点可是2.08。我基本是专业排名中靠后的。作为一个曾经高考落榜的人，我并不是什么大神。



python 那极为简洁与优美的语法给了当时的我极大的震撼，时至今日，写 py 代码对我而言依然是一种带有艺术意味的享受。

大一的时候，学习过一个学期的c语言，我相信大部分人都学过，期末考试过后就基本没有再用过。


我最初学python是应该是大一下，python特别容易入门，而且应用广泛，然后就培训机构迷惑了，大二傻傻的去培训了，其实经过培训，掌握了方法。于是我当机立断，打开百度就去搜索python和Java基础教程了，在自学中感觉很快乐。


我在整个学习Python的过程中，会看别人的博客和书，书面上出的Python相关的书我基本都看过。还有就是去看python标准库的代码，剩下的就是有勇气给开源社区提一些issue和pr。 





## 书籍推荐


 给大家推荐的只有两本书

一本是《Python3基础教程》，大一下就是看这本东西。这本书浅显易懂，很全面，目前很多东西我还是不懂，这本书的作者实力很强。



![](https://img-blog.csdnimg.cn/20200716095234479.png)

第二本是《Python3标准库》，Python就是导包侠，那些Python大佬基本就比你会导包而已。你比他们会更多的库，然后开发自己库，让别人学你的库，那么你就是大佬了。


![](https://img-blog.csdnimg.cn/20200716095520902.png)


**下面分享所学经验**



## 经验一：有个小目标


让我们定一个小目标：怎么学习Py了，先定个小目标吧：在Pycharm上运行python，点亮一个灯。



记得在2018年暑假的时候，我在自己电脑对面的墙上贴了四个大字“暑假计划”。每一次抬头都能看到这四个字。我知道这四个字背后代表着什么，那是我给自己定的一个小目标。

暑假要求搞PR，思维导图，日语水平提高。从坚持到有效坚持的意识转变，能力就会有很大的提高。

我相信成长率的存在。每一个小事，每个步的计划都能体现出从小白到菜鸟的变化。



## 经验二：一个教程多看几遍，多看几个教程


我第一个看的就是菜鸟教程，的确很符合它的名字，难度确实很符合菜鸟的标准，但是风格和教科书别无二致，毕竟那是我就是一个菜鸟。





下面给大家推荐一个Python资源。有位名叫骆昊 (jackfrued) 的资深程序员，为大家规划了一条从“从新手到大师”的百天之路。

从全方位熟悉语言，到Python的进阶用法，再到天南地北的实战攻略：只要沿着这条路走下去，就都会遇到的。




![](https://img-blog.csdnimg.cn/20200716103901755.png)

学Python善用搜索引擎获得自己想要的答案，学会看报错信息;一开始学习的时候，往往会忽视这一点。











## 经验三：学Python就是导包侠

python目前很火，因为它确实是目前上面上最适合做机器学习，大数据分析，人工智能的语言，毕竟库多。




Python这玩意脚本语言入门的确不难，现成的包也一堆基本就是拿来就用，但只是入个门，自学真的绰绰有余


众所周知我等写python的人都是调包侠，怎么可能比得上无敌的c和cpp呢。


python又慢语法又low，不配称为编程语言，可长期以来被开发者们吹的漫天飞，同时饱受其他语言开发者的调侃和诟病以及鄙视。


cpp语法高深莫测，自己的代码别人想读懂是难上加难，在大大增加安全性的同时，还显示出编程这项工作的高技术性，难度性，故深受程序员们的喜爱。

本人误入歧途学习python，最近正在努力转cpp和Java，希望能早日走上正轨。



## 经验四：持续写博客记录

决定开始写博客之前，我也看到过一些技术大牛在文章里面建议大家现在就开始写博客，说这是一个很好的总结学到的东西的方式，以及博客写多了就会越写越顺手，难的是开始的过程。



我觉得很有道理，加上我在大二培训的时候，也被师傅逼着写博客，也学了很多知识，其实这100篇教程很多是那是开始的。


开始写博客之后，就会发现这是一件很快乐的事情。能够把学到的知识总结下来，让别人看懂，会带来一种成就感。看着自己的文章数越来越多，能够感受到自己的进步，能让自己学习时更有动力。






## 经验五：混IT，只会Python未来没戏




现在铺天盖地宣传python，我觉得是因为教Python比较容易。一看这广告把python吹得天花乱坠的，不学python都要变成21世纪的文盲了，别人学了python工作效率蹭蹭的往上提。



在我看来这就是在贩卖焦虑，你仔细想想，培训班几个月出来的是国家要的人工智能人才吗？会python的人，工作效率就能提高了么？


理想的确很美好，但现实也是真的现实，你敲代码改bug补充所需编程知识的时间可能比你手动去完成这些工作还要费心费力，更别提以后使用场景变更，还得重写代码。

这些广告说辞里面最靠谱的可能就是“初次编程选Python,零基础易上手”，但是学完python就可以找到一份月薪20k、30k的工作了么？


“你要悄悄学Python，然后惊艳全世界”

广告铺天盖地的来，从来没听过“你要悄悄学c＃，惊艳全世界”的吧，至少可以分析出来。

派森简单易学，用处广，卖课很挣钱。


因此，Python只能做第二编程语言来搞，第一我选用Java。


# 100、完结篇

不知不觉，Runsen已经完成100篇，应该是从大二算起，已经一年多。

微信：RunsenLiu












