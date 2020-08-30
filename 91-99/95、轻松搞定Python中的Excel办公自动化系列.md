@Author：Runsen
@Date：2020/7/11

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾  （作者：Runsen ）

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

这篇是九十五篇、九十五、轻松搞定Python办公自动化系列。离收官还有五篇。





@[toc]

# Excel


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




# 合并文件夹中的多个Excel文件

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
# 
