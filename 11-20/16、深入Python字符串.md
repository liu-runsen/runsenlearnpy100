
@Author ：Runsen

 Python字符串总结


@[TOC]

# 什么字符串
字符串是由独立字符组成的一个序列，通常包含在单引号（‘ ’），双引号（”“）

三引号（''' '''）


```python
s1 = 'hello'
s2 = "hello"
s3 = """hello"""
s1 == s2 == s3
True

```
三引号字符串常用于函数的注释

```python
def calculate_similarity(item1, item2):
    """
    Calculate similarity between two items
    Args:
        item1: 1st item
        item2: 2nd item
    Returns:
      similarity score between item1 and item2
    """

```

# 转义字符

用 \ 开头的字符串，来表示一些特定意义的字符

```python
s = 'a\nb\tc'
print(s)
a
b	  c

len(s)
5
```

代码中的'\n'，表示一个字符——换行符；'\t'也表示一个字符，四个空格


字符 a，换行，字符 b，然后制表符，最后打印字符 c
最后打印的输出横跨了两行，但是整个字符串 s 仍然只有 5 


# 常用操作

```python
name = 'jason'
name[0]
'j'
name[1:3]
'as'


for char in name:
    print(char)   
j
a
s
o
n


```
注意python的字符串是不可变的


```python
s = 'hello'
s[0] = 'H'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment

```

只能通过船创建新的字符串
```python
s = 'H' + s[1:]
s = s.replace('h', 'H')

```


在java 中有可变的字符串，StringBuilder  ，每次改变字符串，无需创建新的字符串，时间复杂度为O（1） 

但是在python中如果想要改变字符串，往往需要O（n)的时间复杂度，n是新字符串的长度


#  拼接字符串

```python
str1 += str2  # 表示 str1 = str1 + str2

# 这个时间复杂度是多少
s = ''
for n in range(0, 100000):
    s += str(n)

```
在python2中总的时间复杂度就为 O(1) + O(2) + … + O(n) = O（n^2)

但是在python3中 str1 += str2 首先会检测str1 是否有其他的引用

所以在python3中时间复杂度是O（n）





```python
l = []
for n in range(0, 100000):
    l.append(str(n))
l = ' '.join(l) 

```
由于列表的 append 操作是 O(1) 复杂度，时间复杂度为 n*O(1)=O(n)。



# split分割
```python
def query_data(namespace, table):
    """
    given namespace and table, query database to get corresponding
    data         
    """

path = 'hive://ads/training_table'
namespace = path.split('//')[1].split('/')[0] # 返回'ads'
table = path.split('//')[1].split('/')[1] # 返回 'training_table'
data = query_data(namespace, table) 

```
- string.strip(str)，表示去掉首尾的 str 
- tring.lstrip(str)，表示只去掉开头的 str
- string.rstrip(str)，表示只去掉尾部的 str


在读入文件时候，如果开头和结尾都含有空字符，就采用strip函数
```python
s = ' my name is jason '
s.strip()
'my name is jason'

```
# 格式化


format
```python
print('no data available for person with id: {}, name: {}'.format(id, name))
```



```python
print('no data available for person with id: %s, name: %s' % (id, name))

```
**%s 表示字符串型，%d 表示整型**




**两种字符串拼接操作，哪个更好**
```python
s = ''
for n in range(0, 100000):
    s += str(n)

```

```python
l = []
for n in range(0, 100000):
    l.append(str(n))
    
s = ' '.join(l)

```
对于上面的两种拼接操作，计算运行时间



```python
# 第一个 +=
import time
start_time  =time.perf_counter()
s = ''
for n in range(0,1000000):
    s += str(n)
end_time = time.perf_counter()
# 5.7604558070000005
print(end_time - start_time)
# 第二个 join
import time
start_time  =time.perf_counter()
s = []
for n in range(0,1000000):
    s.append(str(n))
''.join(s)
end_time = time.perf_counter()
# 0.622547053
print(end_time - start_time)



# 第三个 map
import time
start_time = time.perf_counter()
s = ''.join(map(str, range(0, 1000000)))
end_time = time.perf_counter()
# 0.403433529
print(end_time - start_time)

```


结果：
- 对于数据量大的map好过join，join好过 +=


- 对于数据量小的map 好过 += 好过join


![](https://img-blog.csdnimg.cn/2019052315133017.png)
