@Author：BY Runsen




@[toc]

# 异常处理
在Python 中的错误和异常是什么？

通常来说，程序中的错误至少包括两种，一种是语法错误，另一种则是异常。所谓语法错误，你应该很清楚，也就是你写的代码不符合编程规范，无法被识别与执行，比如下面这个例子的语法错误

下面的代码无法被识别和执行
```python
if name is not None
    print(name)
```
If 语句漏掉了冒号，不符合 Python 的语法规范，所以程序就会报错invalid syntax。


异常则是指程序的语法正确，也可以被执行，但在执行过程中遇到了错误，抛出了异常
```python
10 / 0
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: integer division or modulo by zero

order * 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'order' is not defined

1 + [1, 2]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'int' and 'list'

```

常见的报错是ZeroDIvision NameError 和 typeError

还有很多其他异常的类型如keyError 字典的键找不到和FileNotFoundError 文件不存在



如何处理异常，通常是用try except来解决
```python
try:
    s = input('please enter two numbers separated by comma: ')
    num1 = int(s.split(',')[0].strip())
    num2 = int(s.split(',')[1].strip())
    ... 
except ValueError as err:
    print('Value Error: {}'.format(err))

print('continue')

```

如果我们输入a,b，程序便会抛出异常invalid literal for int() with base 10:'a'

```python
please enter two numbers separated by comma: a,b
Value Error: invalid literal for int() with base 10: 'a'
continue
```

大型社交网站的后台，需要针对用户发送的请求返回相应记录。用户记录往往储存在 key-value 结构的数据库中，每次有请求过来后，我们拿到用户的 ID，并用 ID 查询数据库中此人的记录，就能返回相应的结果。而数据库返回的原始数据，往往是 json string 的形式，这就需要我们首先对 json string 进行 decode（解码），你可能很容易想到下面的方法：



```python
import json
raw_data = queryDB(uid) # 根据用户的 id，返回相应的信息
data = json.loads(raw_data)

```
上面的代码是不是就足够呢？

json.loads()函数中，如果输入的字符串不符合规范，那么就无法解码，就会抛出异常


因此写之前就应该考虑如何处理异常

```python
try:
    data = json.loads(raw_data)
    ....
except JSONDecodeError as err:
    print('JSONDecodeError: {}'.format(err))

```

