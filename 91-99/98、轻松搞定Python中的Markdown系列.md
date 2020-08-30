@Author：Runsen
@Date：2020/7/15

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾
> （作者：Runsen ）

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)


这篇是九十八、轻松搞定Python中的Markdown系列。离收官还有二篇。


@[toc]



# tomd

本文是介绍tomd工具，大家可以去看[其](https://github.com/gaojiuli/tomd/)README的中文翻译。

安装


```csharp
pip install tomd
```

这个tomd应该是一个人开发的。直接看官方的示例，这里不罗嗦了，其实很简单的。




# 将md批量转为docx


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



- #：此为Markdown中的标题语法，但是只支持到四级标题。
- -：此为Markdown中的无须项目符号语法，笔者在此保留并进行拓展，和标题类似，可以键入多个减号来实现多级项目符号，最多三级。
- **：此为Markdown中的粗体语法，笔者在此保留并简化，规定此语法只能在正文段落中使用。
- $：此为Markdown中的Latex公式语法，笔者在此保留，为了便于添加到Word中，此处将公式转化为图片。
- !:此为Markdown中的图片语法的简化写法


在此也向读者安利一个Markdown文本编辑器Typora，非常好用！不是打广告。
