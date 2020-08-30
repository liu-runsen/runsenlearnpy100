

@Author：By Runsen

@Date：2019年07月13日




之前写的，最近决定把之前的回顾，写详细。


@[toc]
# 1、匿名函数

匿名函数不需要显示地定义函数名，使用【lambda + 参数 +表达式】的方式

## 1.1 lambda 函数
lambda 函数的形式




```python
lambda argument1, argument2,... argumentN : expression

```

套入函数，使用lambda 

```python
square = lambda x: x**2
square(3)

9

```
lambda 返回的一个函数对象



注意：lambda 和def 的区别

lambda 是一个表达式，def 是一个语句


```python
[(lambda x: x*x)(x) for x in range(10)]
# 输出
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

```
lambda 可以用作函数的参数，def 不能
```python
l = [(1, 20), (3, 0), (9, 10), (2, -1)]
l.sort(key=lambda x: x[1]) # 按列表中元祖的第二个元素排序
print(l)
# 输出
[(2, -1), (3, 0), (9, 10), (1, 20)]

```


lambda 是只有一行的简单表达式

```python
squared = map(lambda x: x**2, [1, 2, 3, 4, 5])

```
如果不用lambda ，你用def就需要多写好多行
```python
def square(x):
    return x**2

squared = map(square, [1, 2, 3, 4, 5])

```

在tkinter 中实现的简单功能

```python
from tkinter import Button, mainloop
button = Button(
    text='This is a button',
    command=lambda: print('being pressed')) # 点击时调用 lambda 函数
button.pack()
mainloop()

```
![](https://img-blog.csdnimg.cn/20190602104359313.png)

主要你按压就出现being pressed


你用def就是下面的样子

```python
from tkinter import Button, mainloop

def print_message():
    print('being pressed')

button = Button(
    text='This is a button',
    command=print_message) # 点击时调用 lambda 函数
button.pack()
mainloop()

```
使用def 要写好多行，多定义一个函数




## 1.2 函数式编程

函数式编程是指代码每一块都是不可变的，都是由纯函数的组成


这里的纯函数 值函数本身相互独立，对于相同的输入都有相同的输出


传入一个列表将列表的元素变为原来的2倍
```python
def multiply_2(l):
    for index in range(0, len(l)):
        l[index] *= 2
    return l

```
这段代码不是纯函数的形式，因为我多次调用，每次得到的结果不一样

```python
def multiply_2_pure(l):
    new_list = []
    for item in l:
        new_list.append(item * 2)
    return new_list

```
纯函数的形式，应该在函数里面定义一个新的列表




# 2、其他函数 


对于纯函数python 提供了几个函数



## 2.1 map 


map 函数的形式

```python
（ function ，iterable ）
```
第一个参数是函数的对象，第二个是一个可迭代对象






```python
l = [1, 2, 3, 4, 5]
new_list = map(lambda x: x * 2, l) 
list(new_list)
# [2， 4， 6， 8， 10]
```

## 2.2 filter


filter通常对一个集合做g过滤的操作

```python
l = [1, 2, 3, 4, 5]
new_list = filter(lambda x: x % 2 == 0, l)
list(new_list)
 # [2, 4]
```

## 2.3 reduce

reduce通常对一个集合做累积的操作
 
```python
import functools

l = [1, 2, 3, 4, 5]
product = functools.reduce(lambda x, y: x * y, l) 
product
# 1*2*3*4*5 = 120
```


# 3、思考题



## 3.1 如何根据值来排序
```python
d = {'mike': 10, 'lucy': 2, 'ben': 30}


sorted(d.items(),key=lambda x:x[1],reverse=True)
```

注意 reduce在3中已经放进functools模块中了
```python
>>> map(lambda x: x ** 2, [1, 2, 3, 4, 5])
<map object at 0x000001CAD42A8CF8>
>>> filter(lambda x: x % 2 ==0, [1,2,3,4,5])
<filter object at 0x000001CAD42A8C88>
>>> reduce(lambda x,y: x*y,[1,2,3,4,5])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'reduce' is not defined
>>> from functools import reduce
>>> reduce(lambda x,y: x*y,[1,2,3,4,5])
120
map,filter返回的只是一个对象，reduce在3中已经放进fucntools模块中了
```

