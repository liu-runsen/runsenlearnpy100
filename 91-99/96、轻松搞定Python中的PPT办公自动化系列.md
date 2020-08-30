@Author：Runsen
@Date：2020/7/14

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾
> （作者：Runsen ）

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)



这篇是九十六、轻松搞定Python中的PPT办公自动化系列。离收官还有四篇。

@[toc]


#  安装python-pptx

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

# 将一个PPT文件中的所有文字批量导出


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
