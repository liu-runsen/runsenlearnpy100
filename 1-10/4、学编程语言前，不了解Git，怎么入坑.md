

@Author ： By Runsen

上次教大家搭建好Python的两个IDE，分别是Pycharm和Jupyter

是不是我们正式开始西Python代码呢？
![](https://img-blog.csdnimg.cn/20200511102801436.png)
我的回答是**NO**


怎么了，环境安装好了不是就开始写吗？

这是不对的，学任何编程语言都要看下Git和Github


@[toc]


# 1、了解Git

说到Git，Runsen要说下LInux 的大神，是由伟大的Linux创始人Linus创作




就是这个大神，看不惯微软的window系统，就直接搞Linux。

![](https://img-blog.csdnimg.cn/20200511103241263.png)
我们回到Git。Git是一个分布式版本控制软件，在Git之前有一个SVN的东西，Linus在写LInux内核的时候，使用的是SVN进行代码提交。


Linus用SVN觉得不爽，就是因为SVN不能够分布式版本控制，这也是Git和最核心的区别



我先把git的官方网站的链接给你扔出来：https://git-scm.com/。


走，我们去Git的官方网站学习。



# 2、 版本控制


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



# 3、Git安装




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



# 4、创建本地仓库

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


# 5、配置个人信息

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



# 6、 添加文件



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



# 7、修改文件

按照这个操作流程，修改readme.txt内容如下


```clike
我是Runsen，一个化工的专业的码农
这是一个git学习的项目。
将所有的博客进行汇总整理
然后删除之前Git的博客。
```

然后再次提交，Git add 和Git commit




# 8、错误提交


结果我在提交的时候，发现了commit错误了，这不是第一次提交，而是第二次，其实我是故意的。

辛勤的工作一段时候，我提交了2次了，有2个的版本，怎么查看这些提交记录呢？

git log是 查看历史版本


![](https://img-blog.csdnimg.cn/20200511113628514.png)




从上图中看到，我们需要删除第二次的Commit，如何删除呢，答案就是版本回退





# 9、 版本回退

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

# 10、回到原来版本



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


# 11、正确方法

上面都是演示一些git的常见错误，我们现在是回到了错误提交的commit上，所以还没有解决。



直接用git commit --amend 就可以了，修改本地最近一次已提交的注释

![](https://img-blog.csdnimg.cn/2020051112274258.png)



下面把第一次改为第二次，这是Vim的用法。

![在这里插入图片描](https://img-blog.csdnimg.cn/20200511122658437.png)


你再看看Git log，OK 解决。

![](https://img-blog.csdnimg.cn/20200511122830348.png)


每次在做一些大动作（rebasing）之前，建议备份整个版本库，以防万一。


git的历史记录是不可修改的，也就是说你不能更改任何已经发生的事情。你做的任何操作都只是在原来的操作上修改。也就是说，即使你删除了一个分支，修改了一个提交，或者强制重置，你仍然可以回滚这些操作。



# 12、 总结


今天简单了入了Git的坑，还没完，下面还是要继续把Git搞定，才能开始学习编程语言。





下篇的内容跟下图几张图有关。



![](https://img-blog.csdnimg.cn/20190801172352872.png)
![](https://img-blog.csdnimg.cn/20190801172403911.png)

@Author ： By Runsen



**没有同意，不准转载**
