@Author：By Runsen

@Date：2019年07月13日

之前写的，最近决定把之前的回顾，写详细。


@[toc]
# 1、 迭代器


## 1.1 容器

首先，在了解迭代器之前，需要知道什么是容器

一切都是对象，对象的抽象就是类，而对象的集合就是容器。

容器，就是有多个对象组成的东西。

比如：列表[0,1,2]，元组(1,2,3),字典{’0:'0','1':"1'}  集合{1,2,3}都是容器

所有的容器都是可迭代对象，也就是可以遍历元素。

可迭代对象：可以被转化为不依赖索引取值的容器，这样的对象就叫做可迭代对象，可以通过__iter__() 来生成不依赖索引取值的容器。


你看下图iter(111)是不是报错了。

![](https://img-blog.csdnimg.cn/20190711224541684.png)






因为111不能遍历，所以iter(111)直接报错。


现在写一个is_iterable判断是不是迭代器

```python
def is_iterable(param):
    try: 
        iter(param) 
        return True
    except TypeError:
        return False

params = [
    1234,
    '1234',
    [1, 2, 3, 4],
    set([1, 2, 3, 4]),
    {1:1, 2:2, 3:3, 4:4},
    (1, 2, 3, 4)
]
    
for param in params:
    print('{} is iterable? {}'.format(param, is_iterable(param)))

########## 输出 ##########

1234 is iterable? False
1234 is iterable? True
[1, 2, 3, 4] is iterable? True
{1, 2, 3, 4} is iterable? True
{1: 1, 2: 2, 3: 3, 4: 4} is iterable? True
(1, 2, 3, 4) is iterable? True

```
只要for i in 可以遍历，都是迭代器





## 1.2 取值

迭代器提供了一个next方法，调用这个方法，得到了容器的下一个对象或者一个stopiteration 的报错  ，没有下一个对象




```python
>>> a = iter("123")
>>> next(a)
'1'
>>> next(a)
'2'
>>> next(a)
'3'
>>> next(a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

但是迭代和枚举不完全一样


迭代你并不知道总量是多少






# 2、生成器





那么什么又是生成器，和迭代器又有什么关系？


**生成器就是一个迭代器的例子**，如果说迭代器是人，那么生成器就人中的一个人。

为什么会出来一个生成器，其实很简单声明一个迭代器很简单,但是很容易造成内存不够



比如下图（i for i in range(1000000000) 通过元组方式生成迭代器



![](https://img-blog.csdnimg.cn/20190711225225435.png)

![](https://img-blog.csdnimg.cn/20190711225452564.png)

[i for i in range(1000000000] 它也是一个迭代器，只不会太大了，跑不起来。于是生成器就出来了。

不信比一比内存和消耗的时间，代码如下。


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
    
def test_iterator():
    show_memory_info('initing iterator')
    list_1 = [i for i in range(100000000)]
    show_memory_info('after iterator initiated')
    print(sum(list_1))
    show_memory_info('after sum called')

def test_generator():
    show_memory_info('initing generator')
    list_2 = (i for i in range(100000000))
    show_memory_info('after generator initiated')
    print(sum(list_2))
    show_memory_info('after sum called')

%time test_iterator()
%time test_generator()

########## 输出 ##########

initing iterator memory used: 48.9765625 MB
after iterator initiated memory used: 3920.30078125 MB
4999999950000000
after sum called memory used: 3920.3046875 MB
Wall time: 17 s
initing generator memory used: 50.359375 MB
after generator initiated memory used: 50.359375 MB
4999999950000000
after sum called memory used: 50.109375 MB
Wall time: 12.5 s

```

对了，生成器还有一个yield关键字，不信，去菜鸟看看，说真的菜鸟教程真心不错。



![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS81YmIyODg1Ni03NjQwLTRhZTEtOGZhYi0yYmQ1MmI4YTNkYmYucG5n?x-oss-process=image/format,png)



yield在scrapy用的多，然后我在其他地方没有见到过。


yield和return也很好区别，return就返回值，结束函数，yield只是保存，不会结束函数。想下，你用scrapy爬错，爬一个就return，不干了，这怎么行。



# 3、 练习

## 3.1 给定一个列表和一个数字，求这个数字的位置

这好像是leetcode哪题，我忘记了。如果使用枚举的方法，也就是遍历，很简单。

```python
# 枚举的方法
def index_normal(L, target):
    result = []
    for i, num in enumerate(L):
        if num == target:
            result.append(i)
    return result

print(index_normal([1, 6, 2, 4, 5, 2, 8, 6, 3, 2], 2))

########## 输出 ##########

[2, 5, 9]

```


使用迭代器，需要用list转变为列表，才能print输出




```python
def index_generator(L, target):
    for i, num in enumerate(L):
        if num == target:
            yield i

print(list(index_generator([1, 6, 2, 4, 5, 2, 8, 6, 3, 2], 2)))

########## 输出 ##########

[2, 5, 9]

```

(1 in iter([1,2,3]))  #   True

```python
b = (i for i in range(5))  # 生成器

print(2 in b)
print(4 in b)
print(3 in b)

########## 输出 ##########

True
True
True


```
## 3.2 判断第一个子列是不是第二个的子序列

这我记得，https://leetcode.com/problems/is-subsequence/








![](https://img-blog.csdnimg.cn/20190713220951609.png)



 在去leetcode国际版找一个大神写的代码少的完美写法，

```python
def is_subsequence(a, b):
    b = iter(b) # 迭代器
    return all(i in b for i in a)

print(is_subsequence([1, 3, 5], [1, 2, 3, 4, 5]))
print(is_subsequence([1, 4, 3], [1, 2, 3, 4, 5]))

########## 输出 ##########

True
False

```

竟然有一个all就可以搞定了。我太菜了，菜得天天抄别人代码。
 
 
![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS81NTMwZTMwZi00NTQzLTQwMTEtYWQzMC1lMDk5YjBkZWVhMWQucG5n?x-oss-process=image/format,png)







## 3.3 验证$1^3+2^3+3^3+……+n^3=(1+2+3+……+n)^2？$


生成器玩法，这个公式好像高中学的，



```python
def generator(k):
    i = 1
    while True:
        yield i ** k
        i += 1

gen_1 = generator(1)
gen_3 = generator(3)
print(gen_1)
print(gen_3)

def get_sum(n):
    sum_1, sum_3 = 0, 0
    for i in range(n):
        next_1 = next(gen_1)
        next_3 = next(gen_3)
        print('next_1 = {}, next_3 = {}'.format(next_1, next_3))
        sum_1 += next_1
        sum_3 += next_3
    print(sum_1 * sum_1, sum_3)

get_sum(8)

########## 输出 ##########

<generator object generator at 0x000001E70651C4F8>
<generator object generator at 0x000001E70651C390>
next_1 = 1, next_3 = 1
next_1 = 2, next_3 = 8
next_1 = 3, next_3 = 27
next_1 = 4, next_3 = 64
next_1 = 5, next_3 = 125
next_1 = 6, next_3 = 216
next_1 = 7, next_3 = 343
next_1 = 8, next_3 = 512
1296 1296

```




经过我三摧残，终于想起来之前的东西。


