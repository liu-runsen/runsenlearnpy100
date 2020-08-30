@Author：Runsen
@Date：2020/5/27

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

在Python中的turtle海龟画图，我相信大家都有了解，我在之前也写过这类的博文，但是我发现真的不行，今天就重写，保留好的地方，添加更多的要点

我觉得没有什么东西可以写，就是需要不断地实践。

@[TOC]


# 画一个朵花

```csharp
import turtle
t = turtle.Pen()
def draw_leaf():
    for i in range(2):
        for j in range(15):
            t.forward(5)
            t.right(6)
        t.right(90)
t.goto(0,-150)
t.left(90)
t.forward(50)
draw_leaf()
t.forward(150)
for i in range(6):
    draw_leaf()
    t.right(60)
t.down()
```

上图是画一朵花的程序，使用了函数来定义drawleaf，每一掰叶子由两条弧线组成，每一条弧线重复画15次，每次前进5步，右转6度。

看不懂看下步骤


![](https://img-blog.csdnimg.cn/20200529120443382.png)


这朵花由4部分组成，一个向上长50步的直线，一片叶子，长150步的直线和6片叶子组成的花。



![](https://img-blog.csdnimg.cn/20200529120855841.gif)


最后给叶子填充颜色，给花朵填充颜色。



```csharp
import turtle
t = turtle.Pen()
def draw_leaf():
    for i in range(2):
        for j in range(15):
            t.forward(5)
            t.right(6)
        t.right(90)
t.goto(0,-150)
t.left(90)
t.forward(50)
t.fillcolor("green")
t.begin_fill()
draw_leaf()
t.end_fill()
t.forward(50)
t.right(270)
t.fillcolor("green")
t.begin_fill()
draw_leaf()
t.end_fill()
t.right(90)
t.forward(130)
t.fillcolor("red")
t.begin_fill()
for i in range(6):
    draw_leaf()
    t.right(60)
t.end_fill()
t.down()
```





![](https://img-blog.csdnimg.cn/20200529121458717.gif)



# 酷炫的图形


```csharp
import turtle

for i in range(360):
   turtle.rt(1)
   turtle.circle(100,None,4)
turtle.exitonclick()
```

![](https://img-blog.csdnimg.cn/20200529122206413.gif)

# 画时钟

![](https://img-blog.csdnimg.cn/20190419230504599.png)
![](https://img-blog.csdnimg.cn/20190419230608390.png?0)
![](https://img-blog.csdnimg.cn/20190419230646596.png)

```
# -*- coding：utf-8 -*-
# time ：2019/4/19 22:53
# author: 毛利

import turtle
import datetime
# 移动一段距离
def skip(distance):
    """
    移动乌龟一段距离，不留痕迹
    :param distance: 像素
    :return:
    """
    turtle.penup()
    turtle.forward(distance)
    turtle.pendown()

def draw_clock():
    # 先画表盘
    # 先画点
    # 移动一段距离，画一个点，然后退回
    # 转动6°，再移动一段距离，画一个点，然后退回
    # 循环 60次
    # 让乌龟的方向默认向上
    turtle.reset()
    turtle.hideturtle()
    for i in range(60):

        skip(160)
        # 根据 5格一个时钟
        if i % 5 == 0:
            turtle.pensize(7)
            # 画时钟
            turtle.forward(20)
            if i == 0:
                turtle.write(12, align='center', font=('Courier', 14, 'bold'))
            elif i == 25 or i == 30 or i == 35:
                skip(25)
                turtle.write(int(i/5), align='center', font=('Courier', 14, 'bold'))
                skip(-25)

            else:
                turtle.write(int(i/5), align='center', font=('Courier', 14, 'bold'))
            skip(-20)
        else:
            turtle.pensize(1)
            turtle.dot()
        skip(-160)
        turtle.right(6)


def get_week(t):
    week = ['星期一', '星期二', '星期三', '星期四', '星期五', '星期六', '星期日']
    return week[t.weekday()]


def create_hand(length, name):
    turtle.reset()
    skip(-length * 0.1)
    turtle.begin_poly()
    turtle.forward(length * 1.1)
    turtle.end_poly()
    # 注册
    turtle.register_shape(name, turtle.get_poly())
    hand = turtle.Turtle()
    hand.shape(name)
    hand.shapesize(1, 1, 3)
    return hand

def run():
    # 不停的获取时间
    t = datetime.datetime.today()
    bob.forward(65)
    bob.write(get_week(t), align='center', font=('Courier', 14, 'bold'))
    bob.back(130)
    bob.write(t.strftime('%Y-%m-%d'), align='center', font=('Courier', 14, 'bold'))
    bob.home()
    # 指针移动
    second = t.second + t.microsecond * 0.000001
    minute = t.minute + second/60
    hour = t.hour + minute/60
    turtle.tracer(True)
    second_hand.setheading(6*second)
    minute_hand.setheading(6*minute)
    hour_hand.setheading(30*hour)
    turtle.ontimer(run, 200)
if __name__ == '__main__':
    # 画秒针,分针，时针
    turtle.mode('logo')
    turtle.hideturtle()
    global second_hand, minute_hand, hour_hand, bob

    second_hand = create_hand(135, 'second_hand')
    minute_hand = create_hand(125, 'minute_hand')
    hour_hand = create_hand(90, 'hour_hand')
    # 创建一个新的turtle对象，去循环的操作
    bob = turtle.Turtle()
    bob.hideturtle()
    bob.penup()

    turtle.tracer(False)
    draw_clock()
    run()

    turtle.mainloop()

```
![](https://img-blog.csdnimg.cn/20190419230020836.gif)

对于urtle海龟画图，没必要研究这么深，就是小孩子的玩意，学习下，以后教下儿子就可以了。
