







@Author： runsen 

## 协程是实现并发编程的一种方式。



https://docs.python.org/zh-cn/3/library/asyncio.html




一说并发，你肯定想到了多线程 ， 多进程模型，没错，多线程 和 多进程，正是解决并发问题的经典模型之一

但是你了解过协程Coroutine吗？

协程：是单线程下的并发，又称微线程。


就是只有一个线程，如何提高速度，解决并发编程

英文名Coroutine。

协程比线程的单位更小——协程




注意协程这个概念完全是程序员自己想出来的东西，它对于操作系统来说根本不存在。操作系统只有进程和线程。



从一个demo学起

```cpp
import time 

def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    time.sleep(1)
    print("Maoli prints" + str(num) + " OK")

def main(nums):
    for num in nums:
        print_num(num)
%time main([i for i in range(1,6)])


Maoli is printing 1 nows
Maoli prints1 OK
Maoli is printing 2 nows
Maoli prints2 OK
Maoli is printing 3 nows
Maoli prints3 OK
Maoli is printing 4 nows
Maoli prints4 OK
Maoli is printing 5 nows
Maoli prints5 OK
Wall time: 5 s
```


%time 需要在jupyter notebook中运行。



上面代码是从上到下执行的。


下面将上面代码改为协程版

**注意py版本3.7以上**，主要使用的是asyncio

```cpp
import asyncio

async def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    await asyncio.sleep(1)
    print("Maoli prints" + str(num) + " OK")

async def main(nums):
    for num in nums:
        await print_num(num)
%time asyncio.run(main([i for i in range(1,6)]))


Maoli is printing 1 nows
Maoli prints1 OK
Maoli is printing 2 nows
Maoli prints2 OK
Maoli is printing 3 nows
Maoli prints3 OK
Maoli is printing 4 nows
Maoli prints4 OK
Maoli is printing 5 nows
Maoli prints5 OK
Wall time: 5.01 s
```



asyncio.run() 函数用来运行最高层级的入口点 "main()" 函数

await 是同步调用等待一个协程。以下代码段会在等待 1 秒后打印 num，速度上没有发生改变。

需要引入asyncio.create_task才可以


# 可等待对象


如果一个对象可以在 await 语句中使用，那么它就是 可等待 对象

协程中的还一个重要概念，任务（Task）

如果写一个数字是一个任务，那么毛利我要完成5个任务


毛利我写个1-5都这么慢，不行，我要加速写

asyncio.create_task() 函数用来并发运行作为 asyncio 任务 的多个协程。


```cpp
import asyncio

async def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    await asyncio.sleep(1)
    print("Maoli prints" + str(num) + " OK")

async def main(nums):
    tasks = [asyncio.create_task(print_num(num)) for num in nums]
    for task in tasks:
        await task
%time asyncio.run(main([i for i in range(1,6)]))


Maoli is printing 1 nows
Maoli is printing 2 nows
Maoli is printing 3 nows
Maoli is printing 4 nows
Maoli is printing 5 nows
Maoli prints1 OK
Maoli prints3 OK
Maoli prints5 OK
Maoli prints2 OK
Maoli prints4 OK
Wall time: 1.01 s
```



还可以写成`await asyncio.gather(*tasks)`这种方法
```cpp
import asyncio

async def print_num(num):
    print("Maoli is printing " + str(num) + " nows" )
    await asyncio.sleep(1)
    print("Maoli prints" + str(num) + " OK")

async def main(nums):
    tasks = [asyncio.create_task(print_num(num)) for num in nums]
    await asyncio.gather(*tasks)
%time asyncio.run(main([i for i in range(1,6)]))

```



*tasks 解包列表，将列表变成了函数的参数；与之对应的是，  ** dict 将字典变成了函数的参数。



#asyncio 队列

asyncio也是只有在Pytohn3.7才有的东西。


asyncio 队列被设计成与 queue 模块类似。



```cpp
import asyncio
import random

async def consumer(queue, id):
    while True:
        val = await queue.get()
        print('{} get a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def producer(queue, id):
    for i in range(5):
        val = random.randint(1, 10)
        await queue.put(val)
        print('{} put a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def main():
    # 创建队列
    queue = asyncio.Queue()
    # 消费者1号
    consumer_1 = asyncio.create_task(consumer(queue, 'consumer_1'))
    # 消费者2号
    consumer_2 = asyncio.create_task(consumer(queue, 'consumer_2'))
    # 生产者1号
    producer_1 = asyncio.create_task(producer(queue, 'producer_1'))
    # 生产者2号
    producer_2 = asyncio.create_task(producer(queue, 'producer_2'))
    # stop 10秒
    await asyncio.sleep(10)
    consumer_1.cancel()
    consumer_2.cancel()
    
    await asyncio.gather(consumer_1, consumer_2, producer_1, producer_2, return_exceptions=True)

%time asyncio.run(main())

```
协程的写法简洁清晰，只要把 async / await 语法和 create_task 结合来用，就是Python中比较常见的协程

# 典型的例子

 典型的生产者和消费者
```
import asyncio
import random

async def consumer(queue, id):
    while True:
        val = await queue.get()
        print('{} get a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def producer(queue, id):
    for i in range(5):
        val = random.randint(1, 10)
        await queue.put(val)
        print('{} put a val: {}'.format(id, val))
        await asyncio.sleep(1)

async def main():
    queue = asyncio.Queue()

    consumer_1 = asyncio.create_task(consumer(queue, 'consumer_1'))
    consumer_2 = asyncio.create_task(consumer(queue, 'consumer_2'))

    producer_1 = asyncio.create_task(producer(queue, 'producer_1'))
    producer_2 = asyncio.create_task(producer(queue, 'producer_2'))

    await asyncio.sleep(10)
    consumer_1.cancel()
    consumer_2.cancel()
    
    await asyncio.gather(consumer_1, consumer_2, producer_1, producer_2, return_exceptions=True)

%time asyncio.run(main())

########## 输出 ##########

producer_1 put a val: 5
producer_2 put a val: 3
consumer_1 get a val: 5
consumer_2 get a val: 3
producer_1 put a val: 1
producer_2 put a val: 3
consumer_2 get a val: 1
consumer_1 get a val: 3
producer_1 put a val: 6
producer_2 put a val: 10
consumer_1 get a val: 6
consumer_2 get a val: 10
producer_1 put a val: 4
producer_2 put a val: 5
consumer_2 get a val: 4
consumer_1 get a val: 5
producer_1 put a val: 2
producer_2 put a val: 8
consumer_1 get a val: 2
consumer_2 get a val: 8
Wall time: 10 s

```




# 真实的爬虫

```
import requests
from bs4 import BeautifulSoup

def main():
    url = "https://movie.douban.com/cinema/later/beijing/"
    init_page = requests.get(url).content
    init_soup = BeautifulSoup(init_page, 'lxml')

    all_movies = init_soup.find('div', id="showing-soon")
    for each_movie in all_movies.find_all('div', class_="item"):
        all_a_tag = each_movie.find_all('a')
        all_li_tag = each_movie.find_all('li')

        movie_name = all_a_tag[1].text
        url_to_fetch = all_a_tag[1]['href']
        movie_date = all_li_tag[0].text

        response_item = requests.get(url_to_fetch).content
        soup_item = BeautifulSoup(response_item, 'lxml')
        img_tag = soup_item.find('img')

        print('{} {} {}'.format(movie_name, movie_date, img_tag['src']))

%time main()

```

Wall time: 26 s




```
import asyncio
import aiohttp

from bs4 import BeautifulSoup

async def fetch_content(url):
    async with aiohttp.ClientSession(
        connector=aiohttp.TCPConnector(ssl=False)
    ) as session:
        async with session.get(url) as response:
            return await response.text()

async def main():
    url = "https://movie.douban.com/cinema/later/beijing/"
    init_page = await fetch_content(url)
    init_soup = BeautifulSoup(init_page, 'lxml')

    movie_names, urls_to_fetch, movie_dates = [], [], []

    all_movies = init_soup.find('div', id="showing-soon")
    for each_movie in all_movies.find_all('div', class_="item"):
        all_a_tag = each_movie.find_all('a')
        all_li_tag = each_movie.find_all('li')

        movie_names.append(all_a_tag[1].text)
        urls_to_fetch.append(all_a_tag[1]['href'])
        movie_dates.append(all_li_tag[0].text)

    tasks = [fetch_content(url) for url in urls_to_fetch]
    pages = await asyncio.gather(*tasks)

    for movie_name, movie_date, page in zip(movie_names, movie_dates, pages):
        soup_item = BeautifulSoup(page, 'lxml')
        img_tag = soup_item.find('img')

        print('{} {} {}'.format(movie_name, movie_date, img_tag['src']))

%time asyncio.run(main())


```
Wall time: 4.57 s



速度快了5倍
