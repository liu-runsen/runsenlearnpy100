

@Author ： By Runsen

上次教大家搭建好了Jupyter，并学习了一些conda命令。

如果你是新手，Jupyter不会用，那么我教你盘她
@[toc]



# 1、官方文档

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

# 2、创建一个jupter notebook
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



# 3、 Notebook使用



下面，教大家学习一下Notebook使用
、![](https://img-blog.csdnimg.cn/20200510233001843.png)


现在我们在help中点击Notebook help，来到了官方的教程，建议你还是看一看。

![](https://img-blog.csdnimg.cn/20200510233259224.png)

官方的教程的网页
![](https://img-blog.csdnimg.cn/20200510233449759.png)
# 4、 编辑模式



每一个cell有两种模式：命令模式和编辑模式。



![](https://img-blog.csdnimg.cn/20200510234214589.png)


如下图所示：最左侧是蓝色的条是命令模式，是绿色的条表示编辑模式(此时cell中有光标，可以进行代码编写)。在命令模式下，按下enter或者鼠标单击代码框可以进入编辑模式。在编辑模式下，按下esc或者鼠标单击代码框左侧区域即可进入命令模式。



![](https://img-blog.csdnimg.cn/20200510234332838.png)


在编辑模式下，按住SHIFT+ENTER就可以运行代码了。





# 5、命令模式


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

-  按下Y：退出Markdown模式，回到代码编辑模式



当进入Markdown模式的时候，cell左边的 In【】会消失掉



# 6、Markdown语法


我直接把CSDN上的Markdown给你搬过来。

下面是常见的快捷键

![](https://img-blog.csdnimg.cn/20200510235521475.png)



目录，标题和文本样式

![](https://img-blog.csdnimg.cn/20200510235912274.png)


![](https://img-blog.csdnimg.cn/20200511000002261.png)

我觉得你还是写博客直接看CSDN的帮助文档算了。

#  6、Latex数学公式

Latex我不想写了，直接看我之前的文章

[手把手教你插入数学公式，妈妈再也不用担心我写不了论文了](https://maoli.blog.csdn.net/article/details/105377233)





# 7、Notebook小技巧

这篇文写得不错，总结了Notebook的27个小技巧，文章链接：http://liuchengxu.org/pelican-blog/jupyter-notebook-tips.html。这是原创，大家不要看那些转载的。



# 8、保存文件






我们新建的名字叫ipynb，为什么我喜欢用Jupyter，就是因为可以保存很多类型的文件，比如pdf，html，markdowm，latex。











![](https://img-blog.csdnimg.cn/20200510233632667.png)


# 9、误删了怎么恢复


 直接在一个单元格中输入：history （如图）
就会展示出历史代码（前提是你运行过的，否则不会打印出来）

![](https://img-blog.csdnimg.cn/20200511000624937.png)
# 10、大招
我把大招留在最后，就是你遇到不会的模块怎么办


遇到代码不会怎么办？






![在这里插入图片描述](https://img-blog.csdnimg.cn/20200511001045804.png)



![](https://img-blog.csdnimg.cn/20200511001207980.png)
@Author ： By Runsen

