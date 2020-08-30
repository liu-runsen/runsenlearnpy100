

@Author：Runsen

@Date：2020/6/4


作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://blog.csdn.net/weixin_44510615/article/details/106162925)





今日，我决定继续更新Python教程，介绍的是Python 中的全局解释器锁GIL。已经到了六十二，还剩下区区三十八篇。长得帅就是我的动力，不对，明明就是太穷了才是我的动力。

@[toc]


# 多线程比单线程快？


在Python中，可以通过多进程、多线程和多协程来实现多任务。这个不清楚，看看我之前的文章，难道多线程比单线程快？


你竟然敢质疑我，我太开心了。我得用一个例子证明我自己得观点。

```python
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/6/4
'''

import threading, time
def my_counter():
    i = 0
    for _ in range(100000000):
        i = i+1
    return True

def main1():
    thread_ary = {}
    start_time = time.time()
    for tid in range(2):
        t = threading.Thread(target=my_counter)
        t.start()
        t.join()  # 第一次循环的时候join方法引起主线程阻塞，但第二个线程并没有启动，所以两个线程是顺序执行的

    print("单线程顺序执行total_time: {}".format(time.time() - start_time))

def main2():
    thread_ary = {}
    start_time = time.time()
    for tid in range(2):
        t = threading.Thread(target=my_counter)
        t.start()
        thread_ary[tid] = t

    for i in range(2):
        thread_ary[i].join()  # 两个线程均已启动，所以两个线程是并发的

    print("多线程执行total_time: {}".format(time.time() - start_time))

if __name__ == "__main__":
    main1()
    main2()
```

运行结果

```python
单线程顺序执行total_time: 17.754502773284912
多线程执行total_time: 20.01178550720215
```

我怕你说我乱得出来得结果，我还是截个图看清楚点


![](https://img-blog.csdnimg.cn/20200604114813483.png)

没错， Python 的线程失效了，没有起到并行计算的作用。



Python 的线程，的确封装了底层的操作系统线程，在 Linux 系统里是 Pthread（全称为 POSIX Thread），而在 Windows 系统里是 Windows Thread。另外，Python 的线程，也完全受操作系统管理，比如协调何时执行、管理内存资源、管理中断等等。所以，虽然 Python 的线程和 C++ 的线程本质上是不同的



# GIL并不是Python的特性

GIL 的概念用简单的一句话来解释，就是**「任一时刻，无论线程多少，单一 CPython 解释器只能执行一条字节码」**。这个定义需要注意的点：

首先需要明确的一点是**GIL并不是Python的特性**，它是在实现Python解析器(CPython)时所引入的一个概念。


C++是一套语言（语法）标准，但是可以用不同的编译器来编译成可执行代码。有名的编译器例如GCC，INTEL C++，Visual C++等。

Python也一样，同样一段代码可以通过CPython，PyPy，Psyco等不同的Python执行环境来执行。


**其他 Python 解释器不一定有 GIL**。例如 Jython (JVM) 和 IronPython (CLR) 没有 GIL，而 CPython，PyPy 有 GIL；


因为CPython是大部分环境下默认的Python执行环境。所以在很多人的概念里CPython就是Python，也就想当然的把GIL归结为Python语言的缺陷。所以这里要先明确一点：**GIL并不是Python的特性，Python完全可以不依赖于GIL**






# GIL本质就是一把互斥锁

GIL本质就是一把互斥锁，既然是互斥锁，所有互斥锁的本质都一样，都是将并发运行变成串行，以此来控制同一时间内共享数据只能被一个任务所修改，进而保证数据安全。

可以肯定的一点是：保护不同的数据的安全，就应该加不同的锁。





 GIL 是工作原理：下面这张图，就是一个 GIL 在 Python 程序的工作示例。其中，Thread 1、2、3 轮流执行，每一个线程在开始执行时，都会锁住 GIL，以阻止别的线程执行；同样的，每一个线程执行完一段后，会释放 GIL，以允许别的线程开始利用资源。

![](https://img-blog.csdnimg.cn/20200604115658938.png)


细心的你可能会发现一个问题：为什么 Python 线程会去主动释放 GIL 呢？毕竟，如果仅仅是要求 Python 

CPython 使用引用计数来管理内存，所有 Python 脚本中创建的实例，都会有一个引用计数，来记录有多少个指针指向它。当引用计数只有 0 时，则会自动释放内存。

```python
import sys
a = []
b = a
print(sys.getrefcount(a))
>>> 3
```


这个例子中，a 的引用计数是 3，因为有 a、b 和作为参数传递的 getrefcount 这三个地方，都引用了一个空列表。这样一来，如果有两个 Python 线程同时引用了 a，就会造成引用计数的 race condition，引用计数可能最终只增加 1，这样就会造成内存被污染。因为第一个线程结束时，会把引用计数减少 1，这时可能达到条件释放内存，当第二个线程再试图访问 a 时，就找不到有效的内存了。


# 计算密集型


我们先来看一个简单的计算密集型示例：

```python
import time
COUNT = 50_000_000

def count_down():
   global COUNT
   while COUNT > 0:
       COUNT -= 1

s = time.perf_counter()
count_down()
c = time.perf_counter() - s
print('time taken in seconds - >:', c)

time taken in seconds - >: 9.2957003

```


这个是单线程， 时间是9s， 下面我们用两个线程看看结果又如何：

```python
import time
from threading import Thread

COUNT = 50_000_000

def count_down():
   global COUNT
   while COUNT > 0:
       COUNT -= 1

s = time.perf_counter()
t1 = Thread(target=count_down)
t2 = Thread(target=count_down)
t1.start()
t2.start()
t1.join()
t2.join()
c = time.perf_counter() - s
print('time taken in seconds - >:', c)

time taken in seconds - >: 17.110625

```
其实结果一点也不奇怪， 我们程序主要的操作就是在计算， cpu没有等待， 而改为多线程后， 增加了线程后， 在线程之间频繁的切换，增大了时间开销， 时间当然会增加了。




**对于io密集型工作（爬虫），多线程可以大幅提高代码效率。对CPU计算密集型（数据分析），多线程的效率可能比单线程还略低。**
