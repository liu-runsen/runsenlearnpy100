
@Author：Runsen

@Date：2020/6/4


作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://blog.csdn.net/weixin_44510615/article/details/106162925)





今日，我决定继续更新Python教程，介绍的是Python的垃圾回收机制。已经到了六十三，还剩下区区三十七篇。长得帅就是我的动力，不对，明明就是太穷了才是我的动力。
![](https://img-blog.csdnimg.cn/2020060418232457.png)


@[toc]



参考：[极客时间Python专栏](https://time.geekbang.org/column/article/104265)


在这篇文章，带着这个问题来一直往下看：怎么知道一个对象，是否永远都不能被调用了呢？



# 引用计数
在一些代码中，如果存在一些变量但是没有用，会造成内存空间，因此叫做垃圾，所以要回收。

引用计数也是一种最直观，最简单的垃圾收集技术。原理非常简单，每一个对象都包含了两个头部信息，一个是类型标志符，标识这个对象的类型；另一个是计数器，记录当前指向该对象的引用数目，表示这个对象被多少个变量名所引用。



用来记录对象被引用的次数，每当对象被创建或者被引用时将该对象的引用次数加一，当对象的引用被销毁时该对象的引用次数减一，当对象的引用次数减到零时说明程序中已经没有任何对象持有该对象的引用，换言之就是在以后的程序运行中不会再次使用到该对象了，那么其所占用的空间也就可以被释放了了。


下面是查看引用计数的方法，

```python
print(sys.getrefcount())
```

注意调用getrefcount()函数会临时增加一次引用计数，得到的结果比预期的多一次。

我们通过一些例子来看下，可以使python对象的引用计数增加或减少的场景，代码来自专栏。



```python
import sys
a = []
# 两次引用，一次来自 a，一次来自 getrefcount
print(sys.getrefcount(a))
def func(a):
    # 四次引用，a，python 的函数调用栈，函数参数，和 getrefcount
    print(sys.getrefcount(a))

func(a)
# 两次引用，一次来自 a，一次来自 getrefcount，函数 func 调用已经不存在
print(sys.getrefcount(a))

########## 输出 ##########
2
4
2
```
我认为这个代码是这篇文章最容易看懂的代码

# 内存空间
我们来看看下面的例子。代码来自专栏





```python
import os
import psutil


# 显示当前 python 程序占用的内存大小
def show_memory_info(hint):
    pid = os.getpid()
    p = psutil.Process(pid)

    info = p.memory_full_info()
    memory = info.uss / 1024. / 1024
    print('{} memory used: {} MB'.format(hint, memory))


def func():
    show_memory_info('initial')
    a = [i for i in range(10000000)]
    show_memory_info('after a created')

func()
show_memory_info('finished')

########## 输出 ##########

initial memory used: 20.82421875 MB
after a created memory used: 408.125 MB
finished memory used: 21.10546875 MB
```


如果代码运行遇到psutil.AccessDenied: psutil.AccessDenied (pid=14204)，解决的方法就是用管理员身份打开。


函数 show_memory_info用来获取程序占用的内存空间大小，在 func函数中创建一个包含一百万个整数的列表。从打印结果我们可以看出，创建完列表之后程序耗用的内存空间上升到了 408.125  MB。而当函数 foo 调用完毕之后内存消耗又恢复正常。

这是因为我们在函数 func中创建的 list 变量是局部变量，其作用域是当前函数内部，一旦函数执行完毕，局部变量的引用会被自动销毁，即其引用次数会变为零，所占用的内存空间也会被回收。（代码来自专栏，但是领悟来自于Runsen）


```python

def func():
    show_memory_info('initial')
    a = [i for i in derange(10000000)]
    show_memory_info('after a created')
    return a

a = func()
show_memory_info('finished')

########## 输出 ##########
initial memory used: 20.8515625 MB
after a created memory used: 408.1484375 MB
finished memory used: 408.1484375 MB
```


稍加改造之后，即使 func函数调用结束其所消耗的内存也未被释放。

主要是因为我们将函数 func内部产生的列表返回并在主程序中接收之后，这样就会导致该列表的引用依然存在，该对象后续仍有可能被使用到，垃圾回收便不会回收该对象。



# 计数增加和减少
下面引用计数增加的场景：

- 对象被创建并赋值给某个变量，比如：a = 'ABC'
- 变量间的相互引用（相当于变量指向了同一个对象），比如：b=a
- 变量作为参数传到函数中。比如：ref_method(a)，
- 将对象放到某个容器对象中(列表、元组、字典)。比如：c = [1, a, 'abc']

引用计数减少的场景：

- 当一个变量离开了作用域，比如：函数执行完成时，执行方法前后的引用计数保持不变，这就是因为方法执行完后，对象的引用计数也会减少，如果在方法内打印，则能看到引用计数增加的效果。
- 对象的引用变量被销毁时，比如del a 或者 del b。注意如果del a，再去获取a的引用计数会直接报错。
- 对象被从容器对象中移除，比如：c.remove(a)
- 直接将整个容器销毁，比如：del c
- - 对象的引用被赋值给其他对象，相当于变量不指向之前的对象，而是指向了一个新的对象，这种情况，引用计数肯定会发生改变。(排除两个对象默认引用计一致的场景)。


```python
import sys

def ref_method(str):
    print(sys.getrefcount(str))
    print("我调用了{}".format(str))
    print('方法执行完了')

def ref_count():
    # 引用计数增加的场景
    print('测试引用计数增加')
    a = 'ABC'
    print(sys.getrefcount(a))
    b = a
    print(sys.getrefcount(a))
    ref_method(a)
    print(sys.getrefcount(a))
    c = [1, a, 'abc']
    print(sys.getrefcount(a))

    # 引用计数减少的场景
    print('测试引用计数减少')
    del b
    print(sys.getrefcount(a))
    c.remove(a)
    print(sys.getrefcount(a))
    del c
    print(sys.getrefcount(a))
    a = 783
    print(sys.getrefcount(a))

if __name__ == '__main__':
    ref_count()

测试引用计数增加
7
8
10
我调用了ABC
方法执行完了
8
9
测试引用计数减少
8
7
7
4
```




# 释放内存



python给我们提供了手动释放内存的方法 gc.collect()



```python

import gc
import os
import psutil
# 显示当前 python 程序占用的内存大小
def show_memory_info(hint):
    pid = os.getpid()
    p = psutil.Process(pid)

    info = p.memory_full_info()
    memory = info.uss / 1024. / 1024
    print('{} memory used: {} MB'.format(hint, memory))



def func():
    show_memory_info('initial')
    a = [i for i in range(10000000)]
    b = [i for i in range(10000000)]
    show_memory_info('after a, b created')
    a.append(b)
    b.append(a)

func()
gc.collect()
show_memory_info('finished')

########## 输出 ##########
initial memory used: 26.16796875 MB
after a, b created memory used: 802.03515625 MB
finished memory used: 27.5 MB
```




