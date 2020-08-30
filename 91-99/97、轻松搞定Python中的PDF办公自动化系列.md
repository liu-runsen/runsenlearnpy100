@Author：Runsen
@Date：2020/7/15

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾
> （作者：Runsen ）

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)



这篇是九十七、轻松搞定Python中的PDF办公自动化系列。离收官还有三篇。

@[toc]

# pdfminer3k


PDF的基本操作主要是读取、创建，合并等操作。使用Python的第三方包pdfminer3k读写合并PDF文件变得非常简单。这里不推荐使用PyPDF2，因为现在完全不维护的样子。


安装 pdfminer3k
```csharp
pip install pdfminer3k
```

# 读取PDF

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







