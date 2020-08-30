@Author：Runsen
@Date：2020/7/11


> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)



在很早之前就学过了PyQt5 ，我决定在更新了几篇PyQt5 。之前写的PyQt5 博客基本覆盖于此。这篇是九十篇、Python的GUI系列 | QtDesigner进行界面设计。离收官还有十篇。



@[toc]

# ui设计

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


参数|	描述
--|--
QtCore.Qt.AlignLeft	|水平方向居左对齐
QtCore.Qt.AlignRight	|水平方向居右对齐
QtCore.Qt.AlignCenter|	水平方向居中对齐
QtCore.Qt.AlignJustify|	水平方向两端对齐
QtCore.Qt.AlignTop	|垂直方向靠上对齐
QtCore.Qt.AlignBottom	|垂直方向靠下对齐
QtCore.Qt.AlignVCenter	|垂直方向居中对齐




## 菜单栏 Menu



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
## 工具栏

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



