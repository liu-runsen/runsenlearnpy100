
@Author：Runsen
@Date：2020/5/27

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

在Python中的turtle海龟画图，我相信大家都有了解，我在之前也写过这类的博文，但是我发现真的不行，今天就重写，保留好的地方，添加更多的要点



我觉得没有什么东西可以写，就是需要不断地实践。


@[TOC]



# 画一条线


```css
import turtle
t = turtle.Pen()
t.forward(100)
```


t = turtle.Pen()告诉计算机我们使用t表示海龟的钢笔，
forward(distance) ：别名  turtle.fd( distance ) 沿着当前方向前进指定距离，这里的距离的单位是像素。

![](https://img-blog.csdnimg.cn/20200529111800162.png)
黑色的小三角就是我们的小海龟。三角后面的直线，就是小海龟“前进100步”所留下的痕迹


# 画一个正方形


如果一直前进而不转弯，画出的图也会相当单调。这不是我们所希望的，我们需要“转弯语句”。我们可以“向右转90度”，使用“t.right(90)”，或“向左转90度”，使用“t.left(90)”。这里我们选向右转吧。将“t.right(90)”加入代码，运行：


```css
import turtle
t = turtle.Pen()
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
```



![](https://img-blog.csdnimg.cn/20200529112333480.png)



# 画一个三角形




我们使用turtle.setup(400,400)来设置画布的大小，设置一个400 * 400的窗口大小。
t.left(120)以箭头的方向向左旋转120角度。

```css
import turtle
turtle.setup(400,400)
t = turtle.Pen()
t.forward(100)
t.left(120)
t.forward(100)
t.left(120)
t.forward(100)
t.left(120)
```

![](https://img-blog.csdnimg.cn/20200529112754795.png)
# 画一个圆



t.circle(50)，就是画一个半径为50的圆。


```css
import turtle
turtle.setup(400,400)
t = turtle.Pen()
t.circle(50)
turtle.done()
```



![](https://img-blog.csdnimg.cn/20200529113224314.png)

turtle.done()就是画完的时候停下来，不要马上关闭。


# 绘制梯形




```css
import turtle
turtle.up()
turtle.fillcolor('yellow')
turtle.begin_fill()
turtle.goto(100,-100)
turtle.down()
turtle.goto(200,-100)
turtle.goto(250,-200)
turtle.goto(50,-200)
turtle.goto(100,-100)
turtle.end_fill()
turtle.done()


```
此梯形绘制在第四象限，所以梯形形每个顶点的坐标中，x坐标为正,y坐标为负。四个点的坐标分别选择为(100,-100)、(200,-100)、(250,-200)、(50,-200)。goto也是画的意思，goto（x，y）就是以x和y坐标定位画线。down就是停下来。end_fill就是给封闭图形添加颜色。
![](https://img-blog.csdnimg.cn/20200529113621144.png)
# 画一个星星

星星就是四个圆弧组成，转弯是180度

```css
import turtle
turtle.setup(800, 600)  # 创建绘图窗口

for i in range(4):   # 循环四次
    turtle.circle(90,90)   # 顺时针画一个半径90，90度对应的圆弧 顺时针是正
    turtle.right(180)       # 右转180度

turtle.done()
```

![](https://img-blog.csdnimg.cn/20200529114831673.gif)

# 画一个五角星
五角星是边数最少多角形。最简单的画法是先画一个正五边形，把各角用直线相连并擦去原来的五边形或者延长原五边形的各边直到它们相交，从而得到一个大的五角星。



```css
import turtle
 turtle.color('black','red')
 turtle.begin_fill()
 for i in range(5):
     turtle.forward(100)
     turtle.right(144)
 turtle.end_fill()
```




![](https://img-blog.csdnimg.cn/20200529115402257.png)

# 画一个图案

```css
import turtle
t = turtle.Pen()
for x in range(100):
    t.forward(x)
    t.left(90)
turtle.done()

```



![](https://img-blog.csdnimg.cn/20200529115602232.gif)
# 方法总结



```css
turtle.fd(d)、
turtle.forward(d)：以当前方向，往前行进d像素。

turtle.bk(d)、
turtle.backword(d)：保持当前方向不变，往后退行d像素。

turtle.circle(r,angle,steps=)：从当前位置以r为半径圆的angle角度旋转。

turtle.seth(angle)：以x轴方向为起点将方向偏转为angle度，逆时针为正。只改变行进方向但不行进。

turtle.left(angle)：在当前行进方向的基础上，向左旋转angle度。

turtle.right(angle)：在当前行进方向的基础上，向右旋转angle度。
```

