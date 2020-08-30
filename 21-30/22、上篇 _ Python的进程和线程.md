
@Author: Runsen 


以前的文章

@[TOC]


# 进程和线程

我们打开我们的计算机就会看到进程和线程


![](https://img-blog.csdnimg.cn/20190409220332456.png)


那什么是进程什么是线程

我的理解是进程是指在系统中正在运行的一个应用程序；程序一旦运行就是进程，或者更专业化来说：进程是指程序执行时的一个实例。

线程是进程的一个实体。

进程——资源分配的最小单位，线程——程序执行的最小单位。



我举个例子，**比如打开qq，就是一个线程，有很多个qq上号就是进程**


# python线程和进程的使用

现在讲python线程和进程的使用


 ![](https://img-blog.csdnimg.cn/20190409220401431.png)
 
 
 在Python中线程和进程的使用就是通过Thread这个类。这个类在我们的_thread和threading模块中。
 
![](https://img-blog.csdnimg.cn/201904092204568.png)


我们看一个标准的多线程的例子。


![](https://img-blog.csdnimg.cn/2019040922060320.png)



# 练习

下面我们来练习下， 加深hreading模块的使用。


我写了下面的代码

```python
# -*- coding：utf-8 -*-
# time ：2019/4/9 21:52
# author: Runsen
import threading
import time
def fun1():
    print('hello')
    time.sleep(2)
    print('Bye')
def fun2():
    print('hi')
    time.sleep(2)
    print('OUT')
t1 = threading.Thread(target=fun1)
t2 = threading.Thread(target=fun2)
t1.start()
t2.start()
# t1.join()
# t2.join()
print('主线程完毕')
```

我们先不加join()来阻塞，t1和t2两个线程同时执行，由于位置先打印hello，再打印hi，这个时候都sleep2秒钟，但是他sleep2秒钟，主程序还是在执行，所以下面打印print('主线程完毕')，最后才打印Bye和OUT

```
hello
hi
主线程完毕
Bye
OUT
```


# 线程间变量的共享

![](https://img-blog.csdnimg.cn/20190409221959273.png)





![](https://img-blog.csdnimg.cn/20190409222051749.png)


代码如上图所示，打印的a是1还是2，

答案是 ：2。因为出现了global，线程间变量的共享，在func中的a是全局变量。



下面，我们提高一点点难度，代码如下图所示，还是猜一猜a是啥东西。注意:这里出现了join来阻塞来增加了加和减的操作。





![](https://img-blog.csdnimg.cn/20190409222525518.png)


相信很多人都认为是0，其实这个a的值是变化的，可能这次是0 ，下次是1，还有可能是1000000，a就是在[-1000000，1000000]中的一个随机数。



为什么呢？这是因为虽然他们是同时运行的，但是同时在修改我们的a，那就乱了。这是导致a，for i in range(1000000)，就是遍历了1000000，incr和decr的方法都加上一起了，在这1000000次遍历中，不知道有多少加，多少减，比如，我1000000都是加，没有减，a就是1000000。






如果你就是想出现0，其实加一个互斥锁就可以了。这样你加多少次，我就减多少次，加减的次数不会叠加。因此来了lock的用法。



![](https://img-blog.csdnimg.cn/20190409222743790.png)

这个a怎么运行都是 0。因为我们把这个a锁上了，这样就加1000000次，减1000000次，怎么出来都是我们的0。




