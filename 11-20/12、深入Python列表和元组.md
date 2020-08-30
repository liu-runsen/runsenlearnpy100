


@Author ：Runsen

上面四篇文章总结了Python的基础。


在Pthon中数据结构是非常重要的，所以下面将深入Pyhon数据结构




Python列表和元组总结

@[TOC]

# 什么是列表和元组



列表是动态的，长度大小不固定，可以随意地增加、删减或者改变


而元组是静态的，长度大小固定，无法增加删减或者改变


定义列表和函数

```python
l = [1, 2, 'hello', 'world'] # 列表中同时含有 int 和 string 类型的元素
l
[1, 2, 'hello', 'world']

tup = ('jason', 22) # 元组中同时含有 int 和 string 类型的元素
tup
('jason', 22)

```


对于列表来说，由于其是动态的，我们只需简单地在列表末尾，加入

对于元组来说，实际上就是创建了一个新的元组，然后把原来两个元组的值依次填充.




```python
tup = (1, 2, 3, 4)
new_tup = tup + (5, ) # 创建新的元组 new_tup，并依次填充原元组的值
new _tup
(1, 2, 3, 4, 5)

l = [1, 2, 3, 4]
l.append(5) # 添加元素 5 到原列表的末尾
l
[1, 2, 3, 4, 5]

```
Python 中的列表和元组都支持负数索引，列表和元组都支持切片操作


```python
l = [1, 2, 3, 4]
l[-1]
4

tup = (1, 2, 3, 4)
tup[-1]
4


list = [1, 2, 3, 4]
l[1:3] # 返回列表中索引从 1 到 2 的子列表
[2, 3]

tup = (1, 2, 3, 4)
tup[1:3] # 返回元组中索引从 1 到 2 的子元组
(2, 3) 

```
# 列表和元组常见的内置函数


```python
l = [3, 2, 3, 7, 8, 1]
l.count(3) 
2
l.index(7)
3
l.reverse()
l
[1, 8, 7, 3, 2, 3]
l.sort()
l
[1, 2, 3, 3, 7, 8]

tup = (3, 2, 3, 7, 8, 1)
tup.count(3)
2
tup.index(7)
3
list(reversed(tup))
[1, 8, 7, 3, 2, 3]
sorted(tup)
[1, 2, 3, 3, 7, 8]

```
# 列表和元组存储方式

```python
l = []
l.__sizeof__() // 空列表的存储空间为 40 字节
40
l.append(1)
l.__sizeof__() 
72 // 加入了元素 1 之后，列表为其分配了可以存储 4 个元素的空间 (72 - 40)/8 = 4
l.append(2) 
l.__sizeof__()
72 // 由于之前分配了空间，所以加入元素 2，列表空间不变
l.append(3)
l.__sizeof__() 
72 // 同上
l.append(4)
l.__sizeof__() 
72 // 同上
l.append(5)
l.__sizeof__() 
104 // 加入元素 5 之后，列表的空间不足，所以又额外分配了可以存储 4 个元素的空间

```
元组的初始化速度，要比列表快 5 倍。

```python
python3 -m timeit 'x=(1,2,3,4,5,6)'
20000000 loops, best of 5: 9.97 nsec per loop
python3 -m timeit 'x=[1,2,3,4,5,6]'
5000000 loops, best of 5: 50.1 nsec per loop
```




因此如果存储的数据和数量不变，选择元组


如果存储的数据或数量是可变的，选择列表



下面有两种方法创建列表，哪个初始化更快，运行时间更快。
```python

# 创建空列表
# option A
empty_list = list()

# option B
empty_list = []

```
![](https://img-blog.csdnimg.cn/20190523000342208.png)

测试结果，虽然直接创建元组初始化速度最快，但是由于要用list函数转一道反而不如直接创建列表的速度快。
