



本文是第三篇

@Author：Runsen

@Date：Writern By 2019/04/15 and supplied By 2020/3/31

@公众号：Python之王


往期回顾：
[第一篇、小白看的 Python 基础教程，详细得很（八）](https://maoli.blog.csdn.net/article/details/105242372)



[第二篇、小白看的 Python 基础教程，详细得很（九）](https://maoli.blog.csdn.net/article/details/105242405)






上面两个基本搞定了Python中数据结构，下面花一篇讲讲最重要的类。


@[TOC]
# 7、面向对象编程

万物皆是对象，Python当然支持面向对象编程。类和对象是面向对象编程的两个主要方面，类创建一个新的对象，对象是这个类的实例。

对象可以使用类的变量，属于对象或类的变量被称为域；对象也可以使用属于类的函数，这样的函数称为类的方法；域和方法可以合称为类的属性。


域有两种类型
- 属于实例的
- 属于类本身

它们分别被称为实例变量和类变量。



类使用关键字`class`创建，类的域和方法被列在一个缩进块中。

类的方法必须有一个额外的第一个参数，但是在调用时不为这个参数赋值，这个特殊变量指对象本身，按照惯例它的名称是self，类似Java中的this。


在类中下面两个特都方法需要注意：

- `__init__`方法：在类的一个对象被创建时调用该方法；相当于c++中的构造函数，就是当这个类调用了，那么这个__init__ 方法就要执行。

- `__del__`方法：在类的对象被销毁时调用该方法；相当于c++中的析构函数。在使用del删除一个对象时也就调用__del__方法，__del__是最后调用的。

Python中所有的类成员(包括数据成员)都是public的，没有Java的私有类，也就是人人都有调用类，虽然编写变成很简单，
但是资源人人都可以随意分配访问，在项目中确实一个不好的东西。

但是Python 类的却有私有变量和私有方法之说，这个是一个例外，如果使用的数据成员以双下划线为前缀，则为私有变量。

你实例化这个类，访问不了。这是很多人忽略 的


比如：

```python
class public():
    _name = 'protected类型的变量'
    __info = '私有类型的变量'
    def _f(self):
        print("这是一个protected类型的方法")
    def __f2(self):
        print('这是一个私有类型的方法')
    def get(self):
        return(self.__info)
pub = public()
# 先打印可以访问的
print(pub._name)
pub._f()
####结果如下####
protected类型的变量
这是一个protected类型的方法


# 打印下类 私有变量和私有方法
print(pub.__info)
报错：'public' object has no attribute '__info'
pub._f2()
报错：pub._f2()
```
但是私有属性和方法可以在同一个类中被调用
```python
pub.get()
#######
'私有类型的变量'
```


上面是很多人不知道的，下面，我来声明一个Person类


```python　
   
class Person():
    Count = 0
    def __init__(self, name, age):
        Person.Count += 1
        self.name = name
        self.__age = age
    
p = Person("Runsen", 20)

print(p.Count)

# 1 说明我实例化，这个__init__方法就要执行


print(p.name) #Runsen
print (p.__age) 
#AttributeError: Person instance has no attribute '__age'
#私有变量访问不了，报错
```

# 8、继承

面向对象编程 (OOP)，英语全称：Object Oriented Programming，面向对象编程的一个主要功能就是“继承”。继承是指这样一种能力：它可以使用现有类的所有功能，并在无需重新编写原来的类的情况下对这些功能进行扩展。

继承，其实这样理解，就是我写了一个爸爸类和儿子类，爸爸有钱，儿子却没钱，于是儿子决定继承爸爸，调用爸爸的钱（爸爸类的变量和方法）。

继承一个类，基本使用下面的五个方法。

## 8.1 直接调用父类属性方法；

爸爸有钱，儿子却没钱，于是儿子用爸爸的钱
```python
class Father():
    def __init__(self):
        self.money= 1000 
    def action(self):
        print('调用父类的方法')
 
class Son(Father):
    pass
 
son=Son()     # 子类Son 继承父类Father的所有属性和方法
son.action()  # 调用父类属性
输出：调用父类的方法
son.money     # 调用父类属性
输出：1000
```




## 8,2 强制调用父类私有属性方法；

爸爸说，你这个儿子，老是用我的钱，我决定藏私房钱。儿子试试`super()`拿你的私房钱，但是这里需要注意`super()`强制调用父类私有属性方法，就是重写方法，私有变量是不能用supper继承不了，还不可以访问父类中的私有属性方法的变量，就是儿子是拿不了私房钱的。


```python
class Father():
    __money  = 1000 #私有变量是继承不了
    
    def __action(self):  # 父类的私有方法
        money = 1000
        print('调用父类的方法')
 
class Son(Father):
        
    def action(self):
        super()._Father__action()
        print(money) 
        
son=Son()
son.action() 

调用父类的方法
name 'money' is not defined
```



## 8.3 重写父类属性方法；

突然间儿子竟然有钱，决定不用爸爸的钱，用自己的钱，决定重写父类属性方法。

```python
class Father():
    def __init__(self):
        self.money = 0
    
    def action(self):
        print('调用父类的方法')
 
class Son(Father):
    def __init__(self):
        self.money = 1000
      
    def action(self):
        print('子类重写父类的方法')
 
son=Son()     # 子类Son继承父类Father的所有属性和方法
son.action()  # 子类Son调用自身的action方法而不是父类的action方法
son.money     # 自己的1000
```

## 8.4 调用父类的__init__方法

如果爸爸把钱放在`__init__`，儿子有没有可能拿到爸爸的钱，都不是私有变量，就不是私房钱，当然可以拿到


我们先看看如果不用super，能不能拿到。

```python
class Father():
    def __init__(self):
        self.money = 1000
 
class Son(Father):
    def __init__(self):
        pass
    
son=Son()
print(son.money)

# 报错：'Son' object has no attribute 'money'

```

连super不用就像拿钱，太小看你爸爸我了。


```python
class Father():
    def __init__(self):
        self.money = 1000
 
class Son(Father):
    def __init__(self):
        super().__init__()
        #也可以用 Father.__init__(self)  这里面的self一定要加上(上面两个相同)
        
        
son=Son()
print(son.money) 

1000
```


## 8.5 继承父类初始化过程中的参数

有的时候，爸爸需要挣钱和花钱，就是我们初始化过程中的参数，儿子很好奇，决定看看爸爸口袋还要多少钱。

我们这里先写死了earn_money和spend_money

```python
class Father():
    def __init__(self):
        self.earn_money=1000
        self.spend_money= -500
 
class Son(Father):
    def __init__(self):
        super().__init__()
        #也可以用 Father.__init__(self)  这里面的self一定要加上
        
    def add(self):
        return self.earn_money+self.spend_money
        
        
son=Son()
print(son.add())

500
```


儿子发现爸爸钱不够，于是偷偷的拿了点钱过来。

```python
class Father():
    def __init__(self,a,b):
        self.earn_money = a
        self.spend_money= b
    def add(self):
        return self.a + self.b
 
#调用父类初始化参数a,b并增加额外参数c
class Son(Father):
    def __init__(self,a,b,c=1000):  # c固定值
        Father.__init__(self,a,b)  
        self.son_money = c
        
    def add(self):
        return self.earn_money+self.spend_money + self.son_money
        
   
        
son=Son(1000,-500)   # 所以c可以不用显示表达出来
print(son.add())     # 调用子类add函数

1500
```


以上基本涵盖了Python类的继承，调用父类的属性和方法基础内容，可以自己动手写些案例，加深理解。




# 9、输入/输出

程序与用户的交互需要使用输入/输出，主要包括控制台和文件；对于控制台可以使用input和print。input(xxx)输入xxx，
然后读取用户的输入并返回。

```python
In [1]: input()
1
Out[1]: '1'
```


# 10、文件输入/输出

可以使用file类打开一个文件，使用file的read、readline和write来恰当的读写文件。对文件读写能力取决于打开文件时使用的模式，
常用模式

- 读模式("r")
- 写模式("w")
- 追加模式("a")



文件操作之后需要调用close方法来关闭文件。如果用with open就不用slose了。

还有r+，w+，a+


- r：仅仅表示读入
- r+：既可以读取还可以写入
- w: 仅仅表示写入
- w+：既可以读取还可以写入


但r+与w+不同的是，不会把原先存在txt中的东西清空，下面是他们的对比，反正尽量用a+，基本没什么错报出来。


| 描述                 | r+       | w+       | a+                       |
| -------------------- | -------- | -------- | ------------------------ |
| 当前文件不存在时文件 | 抛出异常 | 创建文件 | 创建文件                 |
| 打开后原文件内容     | 保留     | 清空     | 保留                     |
| 初始位置             | 0        | 0        | 文件尾                   |
| 写入位置             | 标记位置 | 标记位置 | **写入时默认跳至文件尾** |


补充个例子吧：



```python
test = '''\
This is a program about file I/O.
Author: Runsen
Date: 2020/3/31
'''
f = open("test.txt", "w") 
f.write(test) 
f.close() 

f = open("test.txt") #默认r
while True:
    line = f.readline()
    if len(line) == 0:  
        break
    print(line)
f.close()

######
This is a program about file I/O.

Author: Runsen

Date: 2020/3/31
```



#  11、存储器
存储器，大家应该不知道。python提供一个标准的模块，成为pickle，使用它可以在一个文件中存储任何python对象，之后可以完整的取出来，这被称为持久地存储对象；还有另外一个模块成为cPickle，它的功能和pickle完全一样，只不过它是用c写的，要比pickle速度快(大约快1000倍)。


```python
import pickle

datafile = "data.data"

mylist = ["Runsen", "is", "20"]

f = open("test.txt", "wb+")
pickle.dump(mylist, f)
f.close()

del mylist

f = open(datafile,'rb+')
mylist = pickle.load(f)

print(mylist)
#["Runsen", "is", "20"]
```



# 12、异常


当程序中出现某些异常的状况时，异常就发生了。

python中可以使用`try ... except `处理。


```python
try:
    print (1/0)
except ZeroDivisionError as e:
    print(e)
except:
    print( "error or exception occurred.")

#integer division or modulo by zero
```




