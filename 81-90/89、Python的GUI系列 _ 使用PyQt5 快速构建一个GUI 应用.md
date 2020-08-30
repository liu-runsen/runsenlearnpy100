



@Author：Runsen
@Date：2020/7/11


> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)



在很早之前就学过了PyQt5 ，我决定在更新了几篇PyQt5 。之前写的PyQt5 博客基本覆盖于此。这篇是第八十九篇、Python的GUI系列 | 使用PyQt5 快速构建一个GUI 应用。离收官还有十一篇。



@[toc]



# Pyqt5的安装




安装 pyqt5

`pip install pyqt5`


如果出现了运行出现了 No module named 'PyQt5.sip'

解决方法 ：

` pip install --user pyqt5==5.10.1`

将pyqt5退了版本



# 添加外部设置工具


安装成功后，这个时候，我们在pycharm中添加外部设置工具。


## 配置QtDesigner

步骤如下：File -> Settings -> Tools -> External Tools -> 


![](https://img-blog.csdnimg.cn/2020071115410494.png)




Name填入QtDesigner（方便后续使用，名称无所谓）。


program ：自己的designer的位置，如`F:\anaconda\Library\bin\designer.exe`


![](https://img-blog.csdnimg.cn/20200711214134921.png)


##  配置PyUIC 


然后添加PyUIC（UI转换工具），PyUIC的Program为Python.exe，在Python的安装目录下面的Scripts目录下，Working directory同理设为我们的工作目录，Arguments则填入如下代码：




```csharp
-m PyQt5.uic.pyuic $FileName$ -o $FileNameWithoutExtension$.py
```







至于工作目录填写`项目的路径`，也可以填` $FileDir$`。
![](https://img-blog.csdnimg.cn/20200711220533733.png)
## 配置pyrcc


最后添加pyrcc用于PyQt5的资源文件转码。具体配置与上述内容相同，Arguments填入：


```csharp
-mPyQt5.uic.pyuic  $FileName$ -o$FileNameWithoutExtension$.py
```


至于工作目录填写`项目的路径`，也可以填` $FileDir$`。




![](https://img-blog.csdnimg.cn/20200711220639251.png)





`


点击Apply保存配置。配置完成之后，PyCharm中会加入3个工具。



![](https://img-blog.csdnimg.cn/20200711215316346.png)

# QtDesigner设计第一个QT应用



下面打开QtDesigner界面，点击QtDesigner则打开QtDesigner的界面。


![](https://img-blog.csdnimg.cn/20200711215406810.png)


刚打开Qt Designer，则弹出如下图所示的窗口。


![](https://img-blog.csdnimg.cn/20200711215455451.png)


创建新的Form给出了5个模板，其中Widget与Main Window最为常用。这里我们选择创建一个Main Window。


![](https://img-blog.csdnimg.cn/20200711215603979.png)

我们什么也不干，直接保存就可以了。
![](https://img-blog.csdnimg.cn/202007112159561.png)


#  将一个.ui 文件生成一个.py文件

将demo.ui 文件打开其实是一个xml网页代码


![](https://img-blog.csdnimg.cn/20190421142300673.png)




在命令行

![](https://img-blog.csdnimg.cn/20190421142826586.png)

![](https://img-blog.csdnimg.cn/20190421142838791.png)



![](https://img-blog.csdnimg.cn/20200711220210231.png)


这样就会生成一个py文件。

![](https://img-blog.csdnimg.cn/20200711221046862.png)

但是直接运行是没有启动的，因为没有使用QApplication和QWidget两个类。这两个类都在PyQt5.QtWidgets。





```python
from PyQt5 import QtCore, QtGui, QtWidgets
class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(800, 600)
        self.centralwidget = QtWidgets.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")
        MainWindow.setCentralWidget(self.centralwidget)
        self.menubar = QtWidgets.QMenuBar(MainWindow)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 800, 23))
        self.menubar.setObjectName("menubar")
        MainWindow.setMenuBar(self.menubar)
        self.statusbar = QtWidgets.QStatusBar(MainWindow)
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)

        self.retranslateUi(MainWindow)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def retranslateUi(self, MainWindow):
        _translate = QtCore.QCoreApplication.translate
        MainWindow.setWindowTitle(_translate("MainWindow", "MainWindow"))

import sys
from PyQt5.QtWidgets import QApplication,QMainWindow
if __name__ == '__main__':
    app = QApplication(sys.argv)
    mainWindow = QMainWindow()
    ui = Ui_MainWindow()
    # 向主窗口上添加控件
    ui.setupUi(mainWindow)
    mainWindow.show()
    sys.exit(app.exec_())

```
运行上面的代码，效果如下所。这就是我们的第一个QT的GUI 应用


![](https://img-blog.csdnimg.cn/20200711221338872.png)
