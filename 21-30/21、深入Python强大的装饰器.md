

@Author：By Runsen

@Date：2019年07月11日

@[toc]
# 1、装饰器

## 1.1 装饰器入门


装饰器，顾名思义，就是用来“装饰”的。比如@Runsen就是一个装饰器，其中"Runsen"是你的装饰器的名字。它能装饰的东西有：函数、类。





先看两段代码，在这里my_decorator就是一个装饰器，其实装饰器就是一个函数来的函数
```python
def my_decorator(func):
    def wrapper():
        print('wrapper of decorator')
        func()
    return wrapper

def greet():
    print('hello world')

greet = my_decorator(greet)
greet()

# 输出
wrapper of decorator
hello world
```


my_decorator函数传入greet函数名方法，中间有一个wrapper内函数方法，  return wrapper说明要执行wrapper内函数，wrapper内函数，执行greet函数名方法


greet = my_decorator(greet)这个代码可以用装饰器来替代，在greet上面加一个@my_decorator，直接执行greet()



```python
def my_decorator(func):
    def wrapper():
        print('wrapper of decorator')
        func()
    return wrapper

@my_decorator
def greet():
    print('hello world')

greet()

wrapper of decorator
hello world
```


装饰器就是继承了 my_decorator函数，因此先调用my_decorator中的wrapper打印出
wrapper of decorator，然后func()被调用，指的就是 greet(),所以在打印出hello world



## 1.2 带参数的装饰器

有时候函数需要传入参数，这时候用*args, **kwargs接受就可以了。

```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print('wrapper of decorator')
        func(*args, **kwargs)
    return wrapper
    
def repeat(num):
    def my_decorator(func):
        def wrapper(*args, **kwargs):
            for i in range(num):
                print('wrapper of decorator')
                func(*args, **kwargs)
        return wrapper
    return my_decorator


@repeat(4)
def greet(message):
    print(message)

greet('hello world')

# 输出：
wrapper of decorator
hello world
wrapper of decorator
hello world
wrapper of decorator
hello world
wrapper of decorator
hello world


```


但是自定义参数的装饰器将改变函数本身的元信息，即函数不再是本身的函数
```python
**greet.__name__
## 输出
'wrapper'

help(greet)
# 输出
Help on function wrapper in module __main__:

wrapper(*args, **kwargs)
```

这时，需要使用内置模块functools.wrap会保留原函数的元信

在源代码中@functools.wraps也是这么来的


```python
import functools

def my_decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('wrapper of decorator')
        func(*args, **kwargs)
    return wrapper
    
@my_decorator
def greet(message):
    print(message)

greet.__name__

# 输出
'greet'

```

# 2、装饰器进阶
## 2.1  类装饰器
类装饰器主要依赖函数__call__	，每当调用一个类的实例，函数__call__就会执行一次



```python
class Count:
    def __init__(self, func):
        self.func = func
        self.num_calls = 0

    def __call__(self, *args, **kwargs):
        self.num_calls += 1
        print('num of calls is: {}'.format(self.num_calls))
        return self.func(*args, **kwargs)

@Count
def example():
    print("hello world")

example()

# 输出
num of calls is: 1
hello world

example()

# 输出
num of calls is: 2
hello world
```




## 2.2 装饰器的嵌套

如果一个函数上面有多个装饰器，叫做装饰器的嵌套


从下到上
```python
@decorator1
@decorator2
@decorator3
def func():
    ...

```

那么相当于，从里到外

```python
decorator1(decorator2(decorator3(func)))


import functools

def my_decorator1(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('execute decorator1')
        func(*args, **kwargs)
    return wrapper


def my_decorator2(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('execute decorator2')
        func(*args, **kwargs)
    return wrapper


@my_decorator1
@my_decorator2
def greet(message):
    print(message)


greet('hello world')

# 输出
execute decorator1
execute decorator2
hello world

```



# 3、装饰器用法实例




## 3.1 身份认证


```python
import functools

def authenticate(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        request = args[0]
        if check_user_logged_in(request): # 如果用户处于登录状态
            return func(*args, **kwargs) # 执行函数 post_comment() 
        else:
            raise Exception('Authentication failed')
    return wrapper
    
@authenticate
def post_comment(request, ...)
    ...
 

```
## 3.2 日志记录


```python
import time
import functools

def log_execution_time(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.perf_counter()
        res = func(*args, **kwargs)
        end = time.perf_counter()
        print('{} took {} ms'.format(func.__name__, (end - start) * 1000))
        return res
    return wrapper
    
@log_execution_time
def calculate_similarity(items):
    ...

```
## 3.3 输入合理性


```python
import functools

def validation_check(input):
    @functools.wraps(func)
    def wrapper(*args, **kwargs): 
        ... # 检查输入是否合法
    
@validation_check
def neural_network_training(param1, param2, ...):
    ...

```

所谓的装饰器，其实就是通过装饰器函数，来修改函数的一些功能，使得原函数不需要修改


代码来源：极客时间Python专栏
