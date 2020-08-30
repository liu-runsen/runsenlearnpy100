@Author ：By Runsen


@[TOC]
# 函数

在Python中的函数就是为了实现某一段功能的代码段，可以重复利用。

就是以后不要重复造轮子，遇到那个场景就用那个函数，就是函数式编程


下面，我定义一个 my_func，传入一个Hello World，再打印一个Hello World
```python
def my_func(message):
    print('Got a message: {}'.format(message))

# 调用函数 my_func()
my_func('Hello World')
# 输出
Got a message: Hello World
```

简单的知识点


- def是函数的声明
- my_func是函数的名称
- message 是函数的参数
- print 是函数的主体部分
- 在函数的最后 可以返回调用结果（return 或yield ），也可以不返回




定义在前，调用在后


```python
def my_sum(a, b):
    return a + b

result = my_sum(3, 5)
print(result)

# 输出
8

```



对于函数的参数可以设定默认值

```python
def func(param = 0):
    ...

```
如果param没有传入，那么参数默认是0，如果传入了参数，就覆盖默认值

# 多态


传入的参数可以接受任何数据类型


比如，列表
```python
print(my_sum([1, 2], [3, 4]))

# 输出
[1, 2, 3, 4]

```
再比如，字符串
```python
print(my_sum('hello ', 'world'))

# 输出
hello world

```
当然，如果参数数据类型不同，而两者无法相加

```
print(my_sum([1, 2], 'hello'))
TypeError: can only concatenate list (not "str") to list

```

同一个函数可以应用到整数，列表，字符串等等的操作称为`多态`。这可不是变态。





# 函数嵌套

函数嵌套就是函数中有函数，就叫嵌套函数了。


```python
def f1():
    print('hello')
    def f2():
        print('world')
    f2()
f1()

# 输出
hello
world

```


函数的嵌套保证了内部函数的调用，内部函数只能被外部函数所调用，不会作用于全局域中。




合理使用函数嵌套，提高运算速度

比如计算5的阶乘。

```python
def factorial(input):
    
    if not isinstance(input, int):
        raise Exception('input must be an integer.')
    if input < 0:
        raise Exception('input must be greater or equal to 0' )
  
    def inner_factorial(input):
        if input <= 1:
            return 1
        return input * inner_factorial(input-1)
    return inner_factorial(input)


print(factorial(5))

120

```
# 函数变量作用域


如果变量是izai函数内部定义的，称为局部变量，只在函数内部有效，当函数执行完毕，局部变量就会被回收。


全局变量就是写在函数外面的。

```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    if value < MIN_VALUE or value > MAX_VALUE:
        raise Exception('validation check fails')

```
这里的MIN_VELUE 和MAX_VALUE就是全局变量，但是我们不能在函数的内部随意改变全局变量的值

```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    ...
    MIN_VALUE += 1
    ...
validation_check(5)
UnboundLocalError: local variable 'MIN_VALUE' referenced before assignment

```


要想改变  必须加上global这个声明


```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    global MIN_VALUE
    ...
    MIN_VALUE += 1
    ...
validation_check(5)

```
global告诉python解析器，函数内部的变量MIN_VALUE就是定义的全局变量，这里输入的是2，这样修改的全局变量的值

```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check(value):
    MIN_VALUE = 3
    ...

```


```python
MIN_VALUE = 1
MAX_VALUE = 10
def validation_check():
    MIN_VALUE = 3
    print(MIN_VALUE)
validation_check()
print(MIN_VALUE)


# 3
# 1
```

对于嵌套函数来说，内部函数无法修改外部函数定义的变量，可以访问，想要修改就要加上 nonolocal 

```python
def outer():
    x = "local"
    def inner():
        nonlocal x # nonlocal 关键字表示这里的 x 就是外部函数 outer 定义的变量 x
        x = 'nonlocal'
        print("inner:", x)
    inner()
    print("outer:", x)
outer()
# 输出
inner: nonlocal
outer: nonlocal

```

不加就不会覆盖
```python
def outer():
    x = "local"
    def inner():
        x = 'nonlocal' # 这里的 x 是 inner 这个函数的局部变量
        print("inner:", x)
    inner()
    print("outer:", x)
outer()
# 输出
inner: nonlocal
outer: local

```
# 闭包


闭包就是在函数里面调用函数，一般用return来执行，return出内部调用的函数名。

计算一个数的n次幂
```python
def nth_power(exponent):
    def exponent_of(base):
        return base ** exponent
    return exponent_of # 返回值是 exponent_of 函数

square = nth_power(2) # 计算一个数的平方
cube = nth_power(3) # 计算一个数的立方 
square
# 输出
<function __main__.nth_power.<locals>.exponent(base)>

cube
# 输出
<function __main__.nth_power.<locals>.exponent(base)>

print(square(2))  # 计算 2 的平方
print(cube(2)) # 计算 2 的立方
# 输出
4 # 2^2
8 # 2^3

```

