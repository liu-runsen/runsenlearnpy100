
现在极少有人会用上tkinter了，所以真正研究的人也就更少了，还是学下tkinter吧，其实这个东西真他妈简单。




tkinter 是内置的模块，无需安装








# 窗口主体框架
每一个 tkinter 应用的主体框架都可以包含下面这部分. 定义 window 窗口 和 window的一些属性, 然后书写窗口内容, 最后执行window.mainloop让窗口活起来.
```python
import tkinter as tk
window = tk.Tk()
window.title('my window')
window.geometry('200x100')

# 这里是窗口的内容
window.mainloop()

```


![](https://img-blog.csdnimg.cn/20200516171208131.png)
# 窗口内容

这次我们会建立一个用来描述的标签 tk.Label, 比如:

```python
import tkinter as tk
window = tk.Tk()
window.title('my window')
window.geometry('200x100')



l = tk.Label(window, 
    text='OMG! this is TK!',    # 标签的文字
    bg='green',     # 背景颜色
    font=('Arial', 12),     # 字体和字体大小
    width=15, height=2  # 标签长宽
    )
l.pack()    # 固定窗口位置

window.mainloop()

```

![](https://img-blog.csdnimg.cn/20200516171306182.png)




# 控件
上面的Label就是一个控件，还有很多的，如按钮，标签和文本框等，如下图所示

![](https://img-blog.csdnimg.cn/20200516171415379.png)



控件自带的共同属性，如大小，字体和颜色等。可根据控件展现形式选择相应的属性，具体属性如下表：




![](https://img-blog.csdnimg.cn/20200516171433691.png)




# tkinter绑定事件
tkinter绑定事件，就是定义一个函数，然后通过command属性传入函数名，下面通过Button绑定事件，点击就出现Runsen爱学习

```css

from tkinter import *

def p_label():
    global root
    Lb = Label(root, text='Runsen爱学习')
    Lb.pack()

root = Tk()
root.title("应用程序窗口")
B_n = Button(root, text='点我', command=p_label, bg='red')  # command后面不能有任何的标点符号
B_n.pack()
root.mainloop()
```


![](https://img-blog.csdnimg.cn/20200516171815987.png)





# 布局显示

一个窗口都应该有布局，就是pack的时候需要设置side，expand需要扩展吗，fill需要填充吗

```css
from tkinter import *
root = Tk()
root.title("应用程序窗口")
Button(root,text='1').pack(side=LEFT,expand=YES,fill=Y)
Button(root,text='2').pack(side=TOP,expand=YES,fill=BOTH)
Button(root,text='3').pack(side=RIGHT,expand=YES,fill=NONE)
Button(root,text='4').pack(side=LEFT,expand=NO,fill=Y)
Button(root,text='5').pack(side=TOP,expand=YES,fill=BOTH)
Button(root,text='6').pack(side=BOTTOM,expand=YES)
Button(root,text='7').pack(anchor=SE)
root.mainloop()
```
![](https://img-blog.csdnimg.cn/20200516172055242.png)


除了pack还有一个grid，grid将组件布局为表格


下面做一个电话拨号盘GUI

```css
from tkinter import *
root = Tk()
labels = [['1','2','3'], # 文本，布局为网格
          ['4','5','6'],
          ['7','8','9'],
          ['*','0','#']]

for r in range(4): # 行循环
    for c in range(3): # 列循环
        label = Label(root,
                      relief=RAISED, # 设置边框格式
                      padx=10, # 加宽标签
                      text=labels[r][c]) # 标签文本
        label.grid(row=r, column=c) # 将标签放置在r行c列
root.mainloop()
```

![](https://img-blog.csdnimg.cn/20200516172458594.png)






# 制作一个日历


上面教你做一个电话拨号盘GUI，下面能做一个简单的日历吗？


我看你就不会，不是我瞧不起你

![](https://img-blog.csdnimg.cn/20200516173244403.png)


放心，有我这个大佬在。这需要导入calendar模块了，


![](https://img-blog.csdnimg.cn/20200516173605591.png)
```css
import calendar
from tkinter import *
root = Tk()
labels = [['Mon','Tue','Wed','Thu','Fri','Sat','Sun']]

MonthCal = calendar.monthcalendar(2020, 5) 
for i in range(len(MonthCal)):
    labels.append(MonthCal[i])
for r in range(len(MonthCal)+1):
    for c in range(7):
        if labels[r][c] == 0:
            labels[r][c] = ' '
        label = Label(root,          
                      padx=5,
                      pady=5,
                      text=str(labels[r][c]))        
        label.grid(row=r,column=c)
root.mainloop()
```

![](https://img-blog.csdnimg.cn/20200516173714374.png)




# 丰富我们的日历
上面的日历就是一个辣鸡，啥功能都没有，需求很简单，就是来两个按钮实现向上翻，向下翻。


向上翻，向下翻两个按钮就需要清空界面，再把日历加到labels列表中  ，放置日历。好像很简单，其实就是这么简单。

大家想一想，怎么做出来。

我还是给标准实现代码


```css
#@Author： Runsen
import calendar 
from tkinter import *
root = Tk()


def LabelCal(Year, Month):
    # 首行放置“年、月”的位置
    label = Label(root,text=str(Year)+"年")
    label.grid(row=0,column=2)
    label = Label(root,text=str(Month)+"月")
    label.grid(row=0,column=4)
    # labels列表：放置“星期”的标题
    labels = [['Mon','Tue','Wed','Thu','Fri','Sat','Sun']]
    # 用calendar库计算日历
    MonthCal = calendar.monthcalendar(Year, Month)
    # 先把界面清空
    for r in range(7):
        for c in range(7):            
            label = Label(root,
                          width =5,
                          padx=5,
                          pady=5,
                          text=' ')        
            label.grid(row=r+1,column=c)
    # 把日历加到labels列表中     
    for i in range(len(MonthCal)):
        labels.append(MonthCal[i])
    # 放置日历
    for r in range(len(MonthCal)+1):
        for c in range(7):
            if labels[r][c] == 0:
                labels[r][c] = ' '
            label = Label(root,
                          width =5,
                          padx=5,
                          pady=5,
                          text=str(labels[r][c]))        
            label.grid(row=r+1,column=c) # 网格布局


# 默认日期
Year, Month = 2020,5
LabelCal(Year, Month)
        
# button：Enter
def ButtonPrevious():
    global Year, Month
    Month = Month-1
    if Month<1:
        Month = Month+12
        Year = Year-1
    LabelCal(Year, Month)
    
button1 = Button(root, text='Previous', command=ButtonPrevious)
button1.grid(row=len(MonthCal)+3, column=0)


# button：Clear
def ButtonNext():
    global Year, Month
    Month = Month+1
    if Month>12:
        Month = Month-12
        Year = Year+1 
    LabelCal(Year, Month)
    
button2 = Button(root, text='Next', command=ButtonNext)
button2.grid(row=len(MonthCal)+3, column=6)

root.mainloop()
```
运行一波，来一个gif图

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051617494865.gif)




