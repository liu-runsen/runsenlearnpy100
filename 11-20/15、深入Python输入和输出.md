

在很多时候，你会想要让你的程序与用户（可能是你自己）交互。你会从用户那里得到输入，然后打印一些结果。我们可以使用iinput和print语句来完成这些功能。


@[TOC]




# input

```python
name = input('your name:')
gender = input('you are a boy?(y/n)')

###### 输入 ######
your name:Jack
you are a boy?

welcome_str = 'Welcome to the matrix {prefix} {name}.'
welcome_dic = {
    'prefix': 'Mr.' if gender == 'y' else 'Mrs',
    'name': name
}

print('authorizing...')
print(welcome_str.format(**welcome_dic))

########## 输出 ##########
authorizing...
Welcome to the matrix Mr. Jack.

```
input函数暂停运行，等待键盘输入，直到按下回车，输入的类型永远时字符串



```python
a = input()
1
b = input()
2

print('a + b = {}'.format(a + b))
########## 输出 ##############
a + b = 12
print('type of a is {}, type of b is {}'.format(type(a), type(b)))
########## 输出 ##############
type of a is <class 'str'>, type of b is <class 'str'>
print('a + b = {}'.format(int(a) + int(b)))
########## 输出 ##############
a + b = 3

```


# 文件输入和输出
生产级别的 Python 代码，大部分 I/O 则来自于文件

这里有个in.text

```python
Mr. Johnson had never been up in an aerophane before and he had read a lot about air accidents, so one day when a friend offered to take him for a ride in his own small phane, Mr. Johnson was very worried about accepting. Finally, however, his friend persuaded him that it was very safe, and Mr. Johnson boarded the plane.

His friend started the engine and began to taxi onto the runway of the airport. Mr. Johnson had heard that the most dangerous part of a flight were the take-off and the landing, so he was extremely frightened and closed his eyes.

After a minute or two he opened them again, looked out of the window of the plane, and said to his friend。

"Look at those people down there. They look as small as ants, don't they?"

"Those are ants," answered his friend. "We're still on the ground."
```
现在
- 读取文件
- 去掉所有标点和换行符，将大写变为小写
- 合并相同的词，统计每个词出现的频率，将词频从大到小排序
- 将结果按行输出文件out.txt

```python
import re

# 你不用太关心这个函数
def parse(text):
    # 使用正则表达式去除标点符号和换行符
    text = re.sub(r'[^\w ]', '', text)

    # 转为小写
    text = text.lower()
    
    # 生成所有单词的列表
    word_list = text.split(' ')
    
    # 去除空白单词
    word_list = filter(None, word_list)
    
    # 生成单词和词频的字典
    word_cnt = {}
    for word in word_list:
        if word not in word_cnt:
            word_cnt[word] = 0
        word_cnt[word] += 1
    
    # 按照词频排序
    sorted_word_cnt = sorted(word_cnt.items(), key=lambda kv: kv[1], reverse=True)
    
    return sorted_word_cnt

with open('in.txt', 'r') as fin:
    text = fin.read()

word_and_freq = parse(text)

with open('out.txt', 'w') as fout:
    for word, freq in word_and_freq:
        fout.write('{} {}\n'.format(word, freq))

########## 输出 (省略较长的中间结果) ##########



```
![](https://img-blog.csdnimg.cn/20190523215923502.png)



但是有个问题，如果文件非常的大容易造成内存奔溃

这个时候给 read 指定参数 size，还可以通过 readline() 函数，每次读取一行，

# json文件读取


```python
import json

params = {
    'symbol': '123456',
    'type': 'limit',
    'price': 123.4,
    'amount': 23
}

params_str = json.dumps(params)

print('after json serialization')
print('type of params_str = {}, params_str = {}'.format(type(params_str), params))

original_params = json.loads(params_str)

print('after json deserialization')
print('type of original_params = {}, original_params = {}'.format(type(original_params), original_params))

########## 输出 ##########

after json serialization
type of params_str = <class 'str'>, params_str = {'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}
after json deserialization
type of original_params = <class 'dict'>, original_params = {'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}

```
json.dumps() 这个函数，接受 Python 的基本数据类型 字典，然后转化string （json的字符串）

json.loads() 这个函数，接受一个合法字符串(json)，然后 转化为字典


**json 的读入**
```python
import json

params = {
    'symbol': '123456',
    'type': 'limit',
    'price': 123.4,
    'amount': 23
}

with open('params.json', 'w') as fout:
    params_str = json.dump(params, fout)

with open('params.json', 'r') as fin:
    original_params = json.load(fin)

print('after json deserialization')
print('type of original_params = {}, original_params = {}'.format(type(original_params), original_params))

########## 输出 ##########

after json deserialization
type of original_params = <class 'dict'>, original_params = {'symbol': '123456', 'type': 'limit', 'price': 123.4, 'amount': 23}

```

