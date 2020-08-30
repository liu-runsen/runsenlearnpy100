


@Author：Runsen
@[toc]


# 什么是json


JSON(JavaScript Object Notation, JS 对象简谱) 是一种轻量级的数据交换格式。


它基于 ECMAScript (欧洲计算机协会制定的js规范)的一个子集，采用完全独立于编程语言的文本格式来存储和表示数据。简洁和清晰的层次结构使得 JSON 成为理想的数据交换语言。 易于人阅读和编写，同时也易于机器解析和生成，并有效地提升网络传输效率。

# JS对象
```python
var teacher_1 = {
    name: ‘Runsen’,
    age: 18,
    feature : [‘高’, ‘富’,  ‘帅’]
}
```

# JSON字符串
```python
{
    “name”: “Runsen”,
    “age”: 18,
    “ feature “ : [‘高’, ‘富’,  ‘帅’]
}
```
# Python字典
```python
{
    ‘name’: ‘Runsen’,
    ‘age’: 18
    ‘feature’ : [‘高’, ‘富’,  ‘帅’]
}
```
注意点：
- 字符串必须用双引号（即：””）来包括
- 值可以是字符串、数字、true、false、null、列表，或字典。




![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS8wYjY2OTcxNC02ZDg3LTQyOTItYjBiZC02OWQ4MGVhZTQxNmEucG5n?x-oss-process=image/format,png)

# Json模块API

常用json就知道，json模块提供了四个常用的方法：dumps、dump、loads、load，用于字符串 和 python数据类型间进行转换。


- json.dumps(obj)    --> 将python数据转化为json

Indent实现缩进，ensure_ascii 是否用ascii解析 

- json.loads(s)      -->将json数据转换为python的数据

- json.dump(obj, fp)  -->转换为json并保存到文件中

- json.load(fp) -->  从文件中读取json，并转化为python数据

# Json模块使用


```python
import json
my_dict = {'a':'1','b':'2','c':'3','d':'4'}
print(type(my_dict))
a = json.dumps(my_dict)
print(a)
print(type(a))
b=json.loads(a)
print(b)
print(type(b))
OUT：
<class 'dict'>
{"a": "1", "b": "2", "c": "3", "d": "4"}
<class 'str'> #json的字符串
{'a': '1', 'b': '2', 'c': '3', 'd': '4'}
<class 'dict'>
——————————
>>> import json
>>> print (json.dumps('中国'))
"\u4e2d\u56fd"
>>> print(json.dumps('中国', ensure_ascii=False))
"中国"
——————————
#json.dump() 和 json.load() 来编码和解码JSON数据,用于处理文件。

import json
my_dict = {'a':'1','b':'2','c':'3','d':'4'}
json.dump(my_dict,open('a.txt','w'))
print(json.load(open('a.txt','r')))
OUT:
会生成一个“a.txt"文件
{'a': '1', 'b': '2', 'c': '3', 'd': '4'}
```


