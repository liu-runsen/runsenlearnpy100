

@Author：Runsen


@[toc]


# Python读写docx文件


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

