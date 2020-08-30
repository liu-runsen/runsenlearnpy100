@Author ： By Runsen



搭建Jupyter Notebook环境（二）

@[toc]



# 1、Jupyter notebook历史

Jupyter 创始人 Fernando Pérez 的说法，他最初的梦想是做一个综合 Ju （Julia）、Py （Python）和 R 三种科学运算语言的计算工具平台，所以将其命名为 Ju-Py-te-R。发展到现在，Jupyter 已经成为一个几乎支持所有语言，能够把软件代码、计算输出、解释文档、多媒体资源整合在一起的多功能科学运算平台。

在Pycham中只能运行一共py文件，而在Jupyter notebook可以运行一行代码就可以了。

# 2 、环境搭建

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



# 3、 conda常见命令

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





# 4、虚拟环境搭建

   在创建的虚拟环境上运行jupyter notebook,但发现在notebook中的python其实并没有运行在指定的虚拟环境引擎上，只需要安装nb_conda_kernels插件即可解决，注意是在base环境下安装，而不是虚拟环境

```clike
(base) conda install nb_conda_kernels
```

安装成功后，在kernel -> change kernel中即可切换到指定的虚拟环境

![](https://img-blog.csdnimg.cn/20200510224404138.png)
你可以可以新建Notebook的时候设置kernel 



![](https://img-blog.csdnimg.cn/20200510224300139.png)


# 5、 修改jupyter notebook的打开路径




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



# 6、 pip 和conda的区别





conda可以让你同时管理安装处理有关的python任务和跟python无关任务，即pip可以允许在任何环境中安装 python包，conda允许你在conda环境中安装任何语言包（包括C语言或者python）。


conda使用一个新的包格式，你不能交替使用conda和pip，

因为pip不能安装和解析conda的包格式。可以使用这两个工具，但是它们是不能交互的。



conda安装库是在一个地方，而且需要根据Python的环境和依赖库而定，比如numpy的版本有的过高，导致安装这个库使用的时候报错。


pip安装就是根据Python的版本而定，有的时候conda安装不了，可以采用pip安装。



