@Author：Runsen
@Date：2020/7/13


> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)



在很早之前就学过了PyQt5 ，我决定在更新了几篇PyQt5 。之前写的PyQt5 博客基本覆盖于此。这篇九十一、Python的GUI系列 | QT组件篇。离收官还有九篇。

官方文档：https://riverbankcomputing.com/static/Docs/PyQt5/

@[toc]



# 主窗口


主窗口：一共有3种窗口

- QMainWindow：可以包含菜单栏、工具栏、状态栏和标题栏，是最常见的窗口形式

- QDialog：是对话窗口的基类。没有菜单栏、工具栏、状态栏。

- QWidget：不确定窗口的用途，就使用QWidget。






# 文本控件


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

#  文本输入框


、

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


# 按钮控件





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




# 完成计算器Demo




```csharp
'''
@Author： Runsen
@微信公众号： 润森笔记
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
