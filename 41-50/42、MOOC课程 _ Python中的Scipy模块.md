
这是MOOC课上的Scipy基础


@[toc]
# SciPy的介绍 
在Numpy库的基础上增加了众多的数学、科学以及工程计算中常用 的库函数 


- 线性代数 
- 常微分方程数值求解 
- 信号处理 
-  图像处理 
- 稀疏矩阵 

# SciPy的常数
SciPy的constants模块包含了众多的物理常数：


```python
from scipy import constants
print(constants.c) # 真空中的光速
299792458.0
print(constants.h) # 普朗克常数
6.62607004e-34
```


在字典physical_constants中，以物理常量名为键，对应的值是一个含有三 个元素的元组，查看电子质量的例子：
```python
print(constants.physical_constants['electron mass'])

(9.10938356e-31, 'kg', 1.1e-38)
常数值 单位 误差
```



![](https://img-blog.csdnimg.cn/20190507230820928.png)

```python
# 1英里等于多少米, 1英寸等于多少米, 1克等于多少千克, 1磅等于多少千克
print(C.mile, C.inch,C.gram,C.pound)

1609.3439999999998 0.0254 0.001 0.45359236999999997
```
# optimize模块
optimize模块提供了许多数值优化算法，可以实现
- 非线性方程组求解
- 数据拟合
- 函数最小值
![](https://img-blog.csdnimg.cn/20190507230952638.png)

![](https://img-blog.csdnimg.cn/20190507231011629.png)

```python
import numpy as np
from scipy.optimize import leastsq
X = np.array([8.19, 2.72, 6.39, 8.71, 4.7, 2.66, 3.78])
Y = np.array([7.01, 2.78, 6.47, 6.71, 4.1, 4.23, 4.05])
#计算以p为参数的直线和原始数据之间的误差
def f(p):
    k, b = p
    return(Y-(k*X+b))
#leastsq使得f的输出数组的平方和最小，参数初始值为[1,0]
r = leastsq(f, [1,0])
k, b = r[0]
print("k=",k,"b=",b)

k= 0.6134953491930442 b= 1.794092543259387
```

![](https://img-blog.csdnimg.cn/20190507231137418.png)

![](https://img-blog.csdnimg.cn/20190507231154670.png)


```python
from scipy.optimize import fsolve
from math import sin
#f计算方程组的误差,x是一组可能的解
def f(x):
    #转换为标准的浮点数列表
    x0, x1, x2 = x.tolist()
    return[5*x1+3,
           4*x0*x0 - 2*sin(x1*x2),
           x1*x2-1.5]
#[1,1,1]是未知数的初始值
result = fsolve(f, [1,1,1])
#输出方程组的解
print(result)
#输出误差
print(f(result))

[-0.70622057 -0.6        -2.5       ]
[0.0, -9.126033262418787e-14, 5.329070518200751e-15]
```
# 插值-interpolate

# 插值 V.S. 拟合


- 插值：通过已知的离散数据来求解未知数据的方法，要求
曲线通过所有的已知数据。
- 拟合：要求曲线函数与已知数据集的误差最小，不要求曲
线通过所有的已知数据。


 **intepolate模块提供了许多对数据进行插值运算的函数：**
- B样条曲线插值
- 外推
- Spline拟合（UnivariateSpline插值运算）
- 二维插值运算等



![](https://img-blog.csdnimg.cn/20190507231542972.png)
![](https://img-blog.csdnimg.cn/20190507231551681.png)

```python
# 创建数据点集：
import numpy as np
x = np.linspace(0, 10, 11)
y = np.sin(x)
import pylab as pl
pl.plot(x,y,'ro')
pl.show()
```
![](https://img-blog.csdnimg.cn/20190507231833418.png)
**B样条曲线插值-举例**
![](https://img-blog.csdnimg.cn/20190507232206654.png)
![](https://img-blog.csdnimg.cn/20190507232229935.png)
```python
import numpy as np
from scipy import interpolate
import pylab as pl
#创建数据点集并绘制
x = np.linspace(0, 10, 11)
y = np.sin(x)
pl.plot(x,y,'ro')
#建立插值数据点
xnew = np.linspace(0, 10, 101)
for kind in ['nearest', 'zero','linear','quadratic']:
    #根据kind创建插值对象interp1d
    f = interpolate.interp1d(x, y, kind = kind)
    ynew = f(xnew)#计算插值结果
    pl.plot(xnew, ynew, label = str(kind))
pl.legend(loc = 'lower right')
pl.show()
```
![](https://img-blog.csdnimg.cn/20190507232107790.pn)


![](https://img-blog.csdnimg.cn/2019050723464798.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234650759.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234654748.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723465825.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234701218.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234704658.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234708104.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234711667.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723471532.Jpeg)

![](https://img-blog.csdnimg.cn/20190507234727542.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234738729.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234742401.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234745727.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234808467.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234812407.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234820974.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234827194.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723483554.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234838989.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234842351.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234853398.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234917869.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234922406.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234934928.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235034101.Jpeg)
![](https://img-blog.csdnimg.cn/20190507234946502.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235113899.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235140760.Jpeg)
![](https://img-blog.csdnimg.cn/2019050723514621.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235226486.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235212116.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235235835.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235239996.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235334260.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235342238.Jpeg)

![](https://img-blog.csdnimg.cn/20190507235349850.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235354452.Jpeg)
![](https://img-blog.csdnimg.cn/20190507235358306.Jpeg)
