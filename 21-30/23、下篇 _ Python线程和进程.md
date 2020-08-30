

@Author：Runsen

@[TOC]

# 队列

上文锁能解决问题，但是不常见

![](https://img-blog.csdnimg.cn/20190409223407931.png)

导入：

`from queue import Queue`


```
from queue import Queue
from threading import Thread
from random import randint
my_queue = Queue(3)
def f1(my_queus):
    for i in range(3):
        num = randint(0,10)
        print(num)
        my_queue.put(num)
def f2(my_queus):
    for i in range(3):
        num = my_queue.get()
        print(num)
t1 = Thread(target=f1,args=(my_queue,))
t2 = Thread(target=f2,args=(my_queue,))
t1.start()
t2.start()
t1.join()
t2.join()
```



0
5
10
0
5
10、


![](https://img-blog.csdnimg.cn/20190409224419329.png)


# 线程池

![](https://img-blog.csdnimg.cn/20190409224540227.png)

```
from multiprocessing.pool import ThreadPool
import time
def hello(name):
    print('hello,{}'.format(name))
    time.sleep(2)
    print('Bye')
t = ThreadPool(3)
for i in range(3):
    t.apply_async(hello,args=(i,))
t.close()
t.join()
```
OUT：
几乎一起完成
hello,0
hello,1
hello,2
几乎一起完成
Bye
Bye
Bye
![](https://img-blog.csdnimg.cn/2019040922534897.png)

对于进程和线程，可以提高爬虫速度


# 多线程典型例子



```python
# -*- coding：utf-8 -*-
# time ：2019/4/23 10:13
# author: 毛利

import threading
import time
import random
MONEY = 0
gLock = threading.Lock()

def Procuder():
    while True:
        global MONEY
        random_money = random.randint(10,100)
        gLock.acquire()
        MONEY += random_money
        gLock.release()
        print ('生产者%s-生产了%d' % (threading.current_thread,random_money))
        time.sleep(0.5)

def Customer():
    while True:
        global MONEY
        random_money = random.randint(10,100)
        if MONEY > random_money:
            print ('消费者%s-消费了：%d' % (threading.current_thread,random_money))
            gLock.acquire()
            MONEY -= random_money
            gLock.release()
        else:
            print ('需要消费的钱为：%d，余额为：%d，' % (random_money,MONEY))
        time.sleep(0.5)

def p_c_test():
    # 执行3个线程，来当作生产者
    for x in range(3):
        th = threading.Thread(target=Procuder)
        th.start()
    # 执行3个线程，来当作消费者
    for x in range(3):
        th = threading.Thread(target=Customer)
        th.start()

if __name__ == "__main__":
    p_c_test()
```
![](https://img-blog.csdnimg.cn/20190424214132327.png)
