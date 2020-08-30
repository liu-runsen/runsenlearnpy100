


本文是第二篇

@Author：Runsen

@Date：Writern By 2019/04/15 and supplied By 2020/3/31

@公众号：Python之王



本系列Python基础教程共四篇，本文是第二篇。

@[TOC]




接着上面[第一篇、小白看的 Python 基础教程，详细得很（八）](https://maoli.blog.csdn.net/article/details/105242372)



##  6.2 元组
 
tuple和list十分相似，但是tuple是不可变的，即不能修改tuple，元组通过圆括号中用逗号分割的项定义。
- 支持索引和切片操作
- 可以使用 in查看一个元素是否在tuple中。
- 空元组()
- 只含有一个元素的元组("a",) #需要加个逗号

优点：tuple比list速度快；对不需要修改的数据进行‘写保护’，可以是代码更安全

`tuple与list可以相互转换，使用内置的函数list()和tuple()。`
```python
l = [1, 2, 3]
print( l )# [1, 2, 3]

t = tuple(l)
print(t) # (1, 2, 3)

l = list(t)
print (l) #[1, 2, 3]
```
元组最通常的用法是用在打印语句，如下例：
```python
name = "Runsen"
age = 20
print( "Name: %s; Age: %d") % (name, age)
# Name: Runsen; Age: 20
```

**函数如下：**

- count(value)　　

返回元组中值为value的元素的个数
```python
t = (1, 2, 3, 1, 2, 3)
print (t.count(2) )# 2
```

- index(value, [start, [stop]])　　

返回列表中第一个出现的值为value的索引，如果没有，则异常 `ValueError`



```python
t = (1, 2, 3, 1, 2, 3)
print( t.index(3) )# 2
try:
    print (t.index(4))
except ValueError as V:
    print(V)  # there is no 4 in tuple
```



## 6.3 字典

字典由键值对组成，键必须是唯一的；

eg: `d = {key1:value1, key2:value2}；`

空字典用{}表示；字典中的键值对是没有顺序的，如果想要一个特定的顺序，那么使用前需要对它们排序；

`d[key] = value`，如果字典中已有`key`，则为其赋值为`value`，否则添加新的键值对`key/value`；

使用`del d[key] `可以删除键值对；判断字典中是否有某键，可以使用in 或 not in；


```python
d = {}
d["1"] = "one"
d["2"] = "two"
d["3"] = "three"

del d["3"]

for key, value in d.items():
    print ("%s --> %s" % (key, value))
#1 --> one
#2 --> two
```
**dict函数如下:**

- clear()　

删除字典中所有元素

```python
d1 = {"1":"one", "2":"two"}
d1.clear()
print (d1 )# {}
```

- copy()　

返回字典的一个副本(浅复制)

```python
d1 = {"1":"one", "2":"two"}
d2 = d1.copy()
print( d2 )#{'1': 'one', '2': 'two'}

print(d1 == d2) # True
print(d1 is d2) # False
```

浅复制值相同，但是对象不同，内存地址不同。



- dict.fromkeys(seq,val=None) 

创建并返回一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值(默认为None)
```python
l = [1, 2, 3]
t = (1, 2, 3)
d3 = {}.fromkeys(l)
print (d3) #{1: None, 2: None, 3: None}

d4 = {}.fromkeys(t, "default")
print(d4) #{1: 'default', 2: 'default', 3: 'default'}
```

- get(key,[default])　　

返回字典dict中键key对应值，如果字典中不存在此键，则返回default的值(default默认值为None)
```python
d5 = {1:"one", 2:"two", 3:"three"}
print (d5.get(1) )#one
print (d5.get(5)) #None
print (d5.get(5, "test") )#test
```
- has_key(key)　　


判断字典中是否有键key
```python
d6 = {1:"one", 2:"two", 3:"three"}
print( d6.has_key(1) ) #True
print (d6.has_key(5))  #False
```
- items()　　


返回一个包含字典中(键, 值)对元组的列表
```python
d7 = {1:"one", 2:"two", 3:"three"}
for item in d7.items():
    print (item)
#(1, 'one')
#(2, 'two')
#(3, 'three')

for key, value in d7.items():
    print ("%s -- %s" % (key, value))
#1 -- one
#2 -- two
#3 -- three
```

- keys()　


返回一个包含字典中所有键的列表
```python
d8 = {1:"one", 2:"two", 3:"three"}

for key in d8.keys():
    print (key)
#1
#2
#3
```
- values()　


返回一个包含字典中所有值的列表
```python
d8 = {1:"one", 2:"two", 3:"three"}
for value in d8.values():
    print( value)
#one
#two
#three
```
- pop(key, [default])　　



若字典中key键存在，删除并返回dict[key]，若不存在，且未给出default值，引发KeyError异常
```python
d9 = {1:"one", 2:"two", 3:"three"}
print (d9.pop(1) )#one
print( d9) #{2: 'two', 3: 'three'}
print( d9.pop(5, None)) #None
try:
    d9.pop(5)  # raise KeyError
except KeyError, ke:
    print ( "KeyError:", ke) #KeyError:5
```
- popitem()　　


删除任意键值对，并返回该键值对，如果字典为空，则产生异常KeyError
```python
d10 = {1:"one", 2:"two", 3:"three"}

print (d10.popitem() ) #(1, 'one')
print (d10)  #{2: 'two', 3: 'three'}
```
- setdefault(key,[default])　　


若字典中有key，则返回vlaue值，若没有key，则加上该key，值为default，默认None
```python
d = {1:"one", 2:"two", 3:"three"}

print (d.setdefault(1))  #one
print (d.setdefault(5))  #None
print( d)  #{1: 'one', 2: 'two', 3: 'three', 5: None}
print (d.setdefault(6, "six")) #six
print (d)  #{1: 'one', 2: 'two', 3: 'three', 5: None, 6: 'six'}
```

- update(dict2)　


把dict2的元素加入到dict中去，键字重复时会覆盖dict中的键值
```python
d = {1:"one", 2:"two", 3:"three"}
d2 = {1:"first", 4:"forth"}

d.update(d2)
print (d)  #{1: 'first', 2: 'two', 3: 'three', 4: 'forth'}
```
- viewitems()　　


返回一个view对象，（key, value）pair的列表，类似于视图。优点是，如果字典发生变化，view会同步发生变化。在
迭代过程中，字典不允许改变，否则会报异常
```python
d = {1:"one", 2:"two", 3:"three"}
for key, value in d.viewitems():
    print ("%s - %s" % (key, value))
#1 - one
#2 - two
#3 - three
```
- viewkeys()　　


返回一个view对象，key的列表
```python
d = {1:"one", 2:"two", 3:"three"}
for key in d.viewkeys():
    print( key)
#1
#2
#3
```
- viewvalues()　

返回一个view对象，value的列表
```python
d = {1:"one", 2:"two", 3:"three"}
for value in d.viewvalues():
    print (value)
#one
#two
#three
```

## 6.4 序列

序列类型是指容器内的元素从0开始的索引顺序访问，一次可以访问一个或者多个元素；列表、元组和字符串都是序列。
序列的三个主要特点是

- 索引操作符和切片操作符
- 索引可以得到特定元素
- 切片可以得到部分序列


**索引操作符和切片操作符**

```python
numbers = ["zero", "one", "two", "three", "four"]
  
print (numbers[1] )# one
print (numbers[-1] )# four
#print( numbers[5]) # raise IndexError
print (numbers[:]) # ['zero', 'one', 'two', 'three', 'four']
print (numbers[3:]) # ['three', 'four']
print (numbers[:2]) # ['zero', 'one']
print (numbers[2:4] )# ['two', 'three']
print (numbers[1:-1] )# ['one', 'two', 'three'] 
```


切片操作符中的第一个数（冒号之前）表示切片开始的位置，第二个数（冒号之后）表示切片到哪里结束。 

如果不指定第一个数，Python就从序列首开始。如果没有指定第二个数，则Python会停止在序列尾。 



注意，返回的序列从开始位置 开始 ，刚好在结束位置之前 结束。即开始位置是包含在序列切片中的，而结束位置被排斥在切片外。 可以用负数做切片。负数用在从序列尾开始计算的位置。


