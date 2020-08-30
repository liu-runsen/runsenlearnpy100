
@Author ： Runsen
@Date：2019/10/16

@[TOC]


# 	多进程和多线程
- 基本概念

> “多任务”就是操作系统可以同时运行多个任务。


单核CPU操作系统轮流让各个任务交替执行，任务1执行0.01秒，切换到任务2执行0.01秒反复执行。表面上看，每个任务都是交替执行的，但是，由于CPU的执行速度实在是太快了，感觉就像所有任务都在同时执行一样。真正的并行执行多任务只能在多核CPU上实现，但是，由于任务数量远远多于CPU的核心数量，所以，操作系统也会自动把很多任务轮流调度到每个核心上执行。
- 并行和并发

> 并行：当系统有一个以上CPU时,则线程的操作有可能非并发。当一个CPU执行一个线程时，另一个CPU可以执行另一个线程，两个线程互不抢占CPU资源，可以同时进行，这种方式我们称之为并行(Parallel)。


> 并发：当有多个线程在操作时,如果系统只有一个CPU,则它根本不可能真正同时进行一个以上的线程，它只能把CPU运行时间划分成若干个时间段,再将时间 段分配给各个线程执行，在一个时间段的线程代码运行时，其它线程处于挂起状。这种方式称为并发(Concurrent)。




# 进程、线程、协程
一个任务就是一个进程（Process），比如打开一个浏览器就是启动一个浏览器进程。
有些进程不止同时干一件事，比如Word，它可以同时进行打字、拼写检查、打印等事情。在一个进程内部，要同时干多件事，就需要同时运行多个“子任务”，我们把进程内的这些“子任务”称为线程（Thread）。一个进程至少有一个线程。

- 进程：每个进程都有自己独立的内存空间，不同进程之间的内存空间不共享。
密集CPU任务，需要充分使用多核CPU资源（服务器，大量的并行计算）时，用多进程。
进程之间的通信有操作系统传递，导致通讯效率低，切换开销大。

- 线程：一个进程可以有多个线程，所有线程共享进程的内存空间，通讯效率高，切换开销小。
共享意味着竞争，导致数据不安全，为了保护内存空间的数据安全，引入"互斥锁"。
一个线程在访问内存空间的时候，其他线程不允许访问，必须等待之前的线程访问结束，才能使用这个内存空间。
密集I/O任务（网络I/O，磁盘I/O，数据库I/O）使用多线程合适。
对于一些要求同时进行并且又要共享某些变量的并发操作，只能用线程，不能用进程。

- 互斥锁：一种安全有序的让多个线程访问内存空间的机制。

- 协程：又称微线程，在单线程上执行多个任务，用函数切换，开销极小。不通过操作系统调度，没有进程、线程的切换开销
多线程请求返回是无序的，哪个线程有数据返回就处理哪个线程，而协程返回的数据是有序的

缺陷：单线程执行，处理密集CPU和本地磁盘IO的时候，性能较低。处理网络I/O性能还是比较高.

- GIL 全局解释器锁：线程的执行权限，在Python的进程里只有一个GIL。
一个线程需要执行任务，必须获取GIL。
好处：直接杜绝了多个线程访问内存空间的安全问题。
坏处：Python的多线程不是真正多线程，不能充分利用多核CPU的资源。
但是，在I/O阻塞的时候，解释器会释放GIL。
# 多进程
- fork—支持linux/unix
os模块封装了常见的系统调用，其中就包括fork
在Unix/Linux操作系统中，提供了一个fork()系统函数，它非常特殊。
编写完毕的代码，在没有运行的时候，称之为程序，正在运行着的代码，就成为进程

- 程序执行os.fork()时，操作系统会创建一个新的进程（子进程），然后复制父进程的所有信息到子进程中
普通的函数调用，调用一次，返回一次，但是fork()调用一次，返回两次，因为操作系统自动把当前进程（称为父进程）复制了一份（称为子进程），然后，分别在父进程和子进程内返回。

- 然后父进程和子进程都会从fork()函数中得到一个返回值，在子进程中这个值一定是0，而父进程中是子进程的 id号
这样做的理由是，一个父进程可以fork出很多子进程，所以，父进程要记下每个子进程的ID，而子进程只需要调用getppid()就可以拿到父进程的ID。
- multiprosessing—跨平台
multiprocessing模块是跨平台版本的多进程模块。
multiprocessing模块提供了一个Process类来代表一个进程对象。


- 	创建子进程
创建子进程时，只需要传入一个执行函数和函数的参数，创建一个Process实例，用start()方法启动。
 join()方法可以等待子进程结束后再继续往下运行，通常用于进程间的同步。
 ```python
def proc(name): #子进程要执行的代码
    print('运行子进程 %s (%s)...' %(name, os.getpid()))  #得到子进程id

p=Process(target=proc,args=('test',)) #传入函数名和参数
print('子进程将要执行...')
p.start()
p.join()
print('子进程结束')
```
Process([group [, target [, name [, args [, kwargs]]]]])
- 	target：表示这个进程实例所调用对象；
- 	args：表示调用对象的位置参数元组；
- 	kwargs：表示调用对象的关键字参数字典；
- 	name：为当前进程实例的别名；
- 	group：大多数情况下用不到；

Process类常用方法：
- 	is_alive()：判断进程实例是否还在执行；
- 	join([timeout])：是否等待进程实例执行结束，或等待多少秒；
-	start()：启动进程实例（创建子进程）；
-	run()：如果没有给定target参数，对这个对象调用start()方法时，就将执行对象中的run()方法；
-	terminate()：不管任务是否完成，立即终止；

Process类常用属性：
- name：当前进程实例别名，默认为Process-N，N为从1开始递增的整数；
- pid：当前进程实例的PID值；

- pool类
如果要启动大量的子进程，可以用进程池的方式批量创建子进程。
初始化Pool时，可以指定一个最大进程数，当有新的请求提交到Pool中时，如果池还没有满，那么就会创建一个新的进程用来执行该请求；但如果池中的进程数已经达到指定的最大值，那么该请求就会等待，直到池中有进程结束，才会创建新的进程来执行
```python
def task(name):
    print('运行子进程%s(%s)'%(name,os.getpid()))
    start=time()
    sleep(random.random()*3)
    end=time()
    print('子进程%s运行 %.2f 秒'%(name,(end-start)))   #子进程01213是同时进行的，某个进程运行完毕后再运行子进程4

if __name__ == '__main__':
    print('父进程%s'%os.getpid())
    p=Pool(4)  #最多同时跑4个子进程，默认大小为cpu核数
    for i in range(5):
        p.apply_async(task,args=(i,))
    p.close()    #调用close之后不能添加新的进程了
    p.join()
    print('所有进程完毕')
```
调用join（）会等待所有子进程执行完毕，调用之前必须先调用close，调用close之后不能添加新的进程了

子进程
很多时候，子进程并不是自身，而是一个外部进程。我们创建了子进程后，还需要控制子进程的输入和输出。
subprocess模块启动一个子进程，控制其输入和输出。
子进程可以通过communicate()方法输入

# 进程间通信
python提供了很多进程间通信的方式，queue用于在多进程间通信，pipe用于两个进程间通信。
- 	Queue
可以使用multiprocessing模块的Queue实现多进程之间的数据传递，Queue本身是一个消息列队程序，是多进程安全的队列。

- Put方法用以插入数据到队列中，它有两个可选参数:blocked和timeout。如果blocked为True(默认值)，并且timeout为正值，该方法会阻塞timeout指定的时间，直到该队列有剩余的空间。如果超时，会抛出Queue.Full异常。如果blocked为False，但该Queue已满，会立即抛出Queue.Full异常。
- Get方法可以从队列读取并且删除一个元素。同样，Get方法有两个可选参数:blocked和timeout。如果blocked为True(默认值)，并且timeout为正值，那么在等待时间内没有取到任何元素，会抛出Queue.Empty异常。如果blocked为False,分两种情况:如果Queue有一个值可用，则立即返回该值;否则，如果队列为空，则立即抛出Queue.Empty异常。

#	Pipe
Pipe常用来在两个进程间进行通信，两个进程分别位于管道的两端。
Pipe方法返回(conn1, conn2)代表一个管道的两个端。
Pipe方法有duplex参数，如果duplex参数为True(默认值)，那么这个管道是全双工模式，也就是说conn1和conn2均可收发。若duplex为False, conn1只负责接收消息，conn2只负责发送消息。
send和recv方法分别是发送和接收消息的方法。例如，在全双工模式下，可以调用connl.send发送消息，connl.recv接收消息。如果没有消息可接收，recv方法会一直阻塞。如果管道已经被关闭，那么recv方法会抛出EOFError

# 多线程（threading）
多任务可以由多进程完成，也可以由一个进程内多线程完成。
多线程运行有如下优点:
- 可以把运行时间长的任务放到后台去处理。
- 用户界面可以更加吸引人，比如用户点击了一个按钮去触发某些事件的处理，可以弹出一个进度条来显示处理的进度。
- 程序的运行速度可能加快。
- 在一些需要等待的任务实现上，如用户输入、文件读写和网络收发数据等，线程就比较有用了。在这种情况下我们可以释放一些珍贵的资源，如内存占用等。



**threading模块一般通过两种方式创建多线程:**
1)	 把一个函数传入并创建Thread实例，然后调用start方法开始执行
2)	直接从threading. Thread继承并创建线程类，然后重写__init__方法和run方法
```python
import threading,time
def loop1():
    print('线程 %s 运行...'%threading.current_thread().name)  #显示子线程实例名字
    n=0
    while n<3:
        n=n+1
        print('%s >>> %s'%(threading.current_thread().name,n))     #current_thread()函数返回当前线程实例
        time.sleep(0.5)
    print('线程 %s 结束...'%threading.current_thread().name)

def loop2():
    print('线程 %s 运行...'%threading.current_thread().name)
    n=0
    while n<2:
        n+=1
        print('%s >>> %s' %(threading.current_thread().name,n))
        time.sleep(0.5)
    print('线程 %s 结束...' % threading.current_thread().name)

if __name__ == '__main__':
    print('---开始---:%s'%time.ctime(),'\n')
    # 显示当前线程，即主线程实例名字
    print('%s 运行'%threading.current_thread().name)
    # 创建子线程，子线程名字在创建时指定，loopthread为子线程的名字，不指定为默认名
    t=threading.Thread(target=loop1,name='子线程1')
    p=threading.Thread(target=loop2,name='子线程2')
    #子线程可以全部start之后再join，即为同步运行，分开执行，为运行完子线程1，再运行子线程2
    t.start()
    t.join()
    p.start()
    p.join()
    while True:
        length=len(threading.enumerate())
        print('当前运行线程数量：%d'%length)
        if length<=1:
            break
    print('thread %s ended'%threading.current_thread().name)
```
任何进程默认就会启动一个线程，该线程称为主线程，主线程又可以启动新的线程， threading模块current_thread()函数返回当前线程的实例。
# 线程同步—lock
多线程和多进程最大的不同在于，多进程中，同一个变量，各自有一份拷贝存在于每个进程中，互不影响，而多线程中，所有变量都由所有线程共享，所以，任何一个变量都可以被任何一个线程修改，因此，线程之间共享数据最大的危险在于多个线程同时改一个变量
```python
t.start()
p.start()
t.join()
p.join()
```
多线程交替运行，每个线程有自己的局部变量，导致赋予全局变量的值会打乱，确保全局变量的值为正确值，要给change_it()上一把锁，其他线程不能同时执行change_it()，只能等待，直到锁被释放后，获得该锁以后才能改。锁只有一个，无论多少线程，同一时刻最多只有一个线程持有该锁，所以，不会造成修改的冲突。
```python
def change_it(n):
    # 先存后取，结果应该为0:
    global balance
    balance = balance + n
    balance = balance - n

def thread(n):
    for i in range(1000):
        #获取锁
        lock.acquire()
        try:
            change_it(n)
        finally:
            #改完释放锁
            lock.release()

if __name__ == '__main__':
    balance=0
    lock=threading.Lock()
    t1 = threading.Thread(target=thread, args=(5,))
    t2 = threading.Thread(target=thread, args=(8,))
    t1.start()
    t2.start()
    t1.join()
    t2.join()
    print(balance)
```
ThreadLocal: 解决参数在一个线程中各个函数之间互相传递的问题。
local_data = threading.local()  #创建全局ThreadLocal对象
local_data为一个ThreadLocal对象，每个thread对其可读写属性，但互不影响。可以把local_school看成全局变量，但每个属性如local_data.data都是线程的局部变量，可以理解为全局变量local_data是一个dict，不但可以用local_data.data，还可以绑定其他变量，如local_data.teacher等等可以任意读写而互不干扰，也不用管理锁的问题，ThreadLocal内部会处理。
ThreadLocal最常用的地方就是为每个线程绑定一个数据库连接，HTTP请求，用户身份信息等，这样一个线程的所有调用到的处理函数都可以非常方便地访问这些资源。

# 协程 (coroutine )
协程又称微线程，纤程，是一种用户级的轻量级线程。
协程拥有自己的寄存器上下文和栈。协程调度切换时，将寄存器上下文和栈保存到其他地方，在切回来的时候，恢复先前保存的寄存器上下文和栈。因此协程能保留上一次调用时的状态，每次过程重入时，就相当于进人上一次调用的状态。
在并发编程中，协程与线程类似，每个协程表示一个执行单元，有自己的本地数据，与其他协程共享全局数据和其他资源。
协程需要用户自己来编写调度逻辑，对于CPU来说，协程其实是单线程，所以CPU不
用去考虑怎么调度、切换上下文，这就省去了CPU的切换开销，所以协程在一定程度上又好于多线程。

Python通过yield提供了对协程的基本支持，但是不完全，第三方gevent库提供了比较完善的协程支持。gevent是一个基于协程的Python网络函数库，使用greenlet在libev事件循环顶部提供了一个有高级别并发性的API。

主要特性：
- 基于libev的快速事件循环，Linux上是epoll机制。
- 基于greenlet的轻量级执行单元。
- API复用了Python标准库里的内容。	
- 支持SSL的协作式sockets.
- 可通过线程池或c-ares实现DNS查询。
- 通过monkey patching功能使得第三方模块变成协作式。


# 分布式进程
在Thread和Process中，应当优选Process，因为Process更稳定，而且，Process可以分布到多台机器上，而Thread最多只能分布到同一台机器的多个CPU上。

Python的multiprocessing模块不但支持多进程，其中managers子模块还支持把多进程分布到多台机器上。一个服务进程可以作为调度者，将任务分布到其他多个进程中，依靠网络通信。






