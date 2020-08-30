

@Author：Runsen
@[TOC]



#  collections 


计数器（counter）以字典的形式返回序列中各个字符出现的次数，值为key，次数为value


Counter是对字典类型的补充，用于追踪值得出现次数 ps:具备字典的所有功能 + 自己的功能


```python
import collections

counter_test = collections.Counter("asfafjhadgkhjkgfjhgfjhaghdg")
print(counter_test)
```

 Counter({'h': 5, 'g': 5, 'a': 4, 'f': 4, 'j': 4, 'd': 2, 'k': 2, 's': 1})
    

数量从大到小排列，获取前N个元素 


```python
# most_common(N)数量从大到小排列，获取前N个元素 
counter_test.most_common(3)
```




[('h', 5), ('g', 5), ('a', 4)]



列出所有不同的元素并排序
```python
# sorted()列出所有不同的元素并排序 
sorted(counter_test)
```



['a', 'd', 'f', 'g', 'h', 'j', 'k', 's']


转换成字符串 

```python
# 转换成字符串 
''.join(sorted(counter_test.elements())) 
```




'aaaaddffffggggghhhhhjjjjkks'




```python
# 取得元素重复次数的值
counter_test['a']
```

4



 update()更新计数器
 
```python
# update()更新计数器，其实就是增加；如果原来没有，则新建，如果有则加一
d = collections.Counter('simsalabim') 
counter_test.update(d) 
print(counter_test) 
```

 Counter({'a': 6, 'h': 5, 'g': 5, 'f': 4, 'j': 4, 's': 3, 'd': 2, 'k': 2, 'i': 2, 'm': 2, 'l': 1, 'b': 1})
    


```python
# elements()取得计数器中的所有元素，注：此处非所有元素集合，而是包含所有元素集合的迭代器 
counter_test = collections.Counter('abcabc') 
sorted(counter_test.elements()) 
```




['a', 'a', 'b', 'b', 'c', 'c']




```python
# subtract()相减，原来的计数器中的每一个元素的数量减去后添加的元素的数量 

counter_test = collections.Counter('which') 
print(counter_test)
counter_test.subtract('watch') 
print(counter_test)
```

Counter({'h': 2, 'w': 1, 'i': 1, 'c': 1})
Counter({'h': 1, 'i': 1, 'w': 0, 'c': 0, 'a': -1, 't': -1})
    

# 有序字典（orderedDict)  



```python
from collections import OrderedDict 
dic = OrderedDict() 
dic['k1'] = 'v1' 
dic['k2'] = 'v2' 
dic['k3'] = 'v3' 
print(dic) 
```

OrderedDict([('k1', 'v1'), ('k2', 'v2'), ('k3', 'v3')])
    


```python
# 得字典所有的键 
print(dic.keys())
```

odict_keys(['k1', 'k2', 'k3'])
    


```python
# 取得字典所有值 
print(dic.values())
```

odict_values(['v1', 'v2', 'v3'])
    


```python
# items() 方法以列表返回可遍历的(键, 值) 元组数组 
print(dic.items())
```

odict_items([('k1', 'v1'), ('k2', 'v2'), ('k3', 'v3')])
    


```python
#pop()方法，删除指定的键值 
dic.pop('k1')  
print(dic) 

```

OrderedDict([('k2', 'v2'), ('k3', 'v3')])
    


```python
#item()方法，默认删除字典最后一个元素 
dic.popitem() 
print(dic) 
```

OrderedDict([('k2', 'v2')])
    


```python
# move_to_end('k')方法将指定键值一道最后
dic.move_to_end('k2') 
print(dic)
```

 OrderedDict([('k2', 'v2')])
    


```python
# update()更新字典 
dic.update({'k1':'v1111','k10':'v10'}) 
print(dic) 
```

OrderedDict([('k2', 'v2'), ('k1', 'v1111'), ('k10', 'v10')])
    

#  默认字典（defaultdict） 


```python
#导入collections模块
import collections
my_dict = collections.defaultdict(list)
my_dict['k1'].append('v1')
print(my_dict)
```

defaultdict(<class 'list'>, {'k1': ['v1']})
    


```python
# 练习：元素分类
# 有如下值集合 [11,22,33,44,55,66,77,88,99,90...]，
# 将所有大于 66 的值保存至字典的第一个key中，将小于 66 的值保存至第二个key的值中。
# 即： {'k1': 大于66 , 'k2': 小于66}

### 1、不用默认指点的写法要判断字典中是否已有{'k1':[]}
all_list = [11,22,33,44,55,66,77,88,99,90,]
dic = {}
for i in all_list:
    if i > 66:
        if "k1" in dic.keys():
            dic['k1'].append(i)
        else:
            dic['k1'] = [i,]
    else:
        if "k2" in dic.keys():
            dic['k2'].append(i)
        else:
            dic['k2'] = [i,]

print(dic)

### 2、默认字典
all_list = [11,22,33,44,55,66,77,88,99,90,]
dic = collections.defaultdict(list)
for i in all_list:
    if i > 66:
        dic['k1'].append(i)
    else:
        dic['k2'].append(i)
print(dic)

```

{'k2': [11, 22, 33, 44, 55, 66], 'k1': [77, 88, 99, 90]}
defaultdict(<class 'list'>, {'k2': [11, 22, 33, 44, 55, 66], 'k1': [77, 88, 99, 90]})



# 可命名元组（namedtuple)


```python
### 根据nametuple可以创建一个包含tuple所有功能以及其他功能的类型。 

from collections import namedtuple #创建(给元组命名) 
Mytuple = namedtuple('Mytuple',['x','y','z']) 
obj = Mytuple(11,22,33) #通过x,y,z取得元组的值 
print(obj.x )
print(obj.y )
print(obj.z )
```

  11
  22
  33
    

# 双向队列（deque) 



```python
from collections import deque #创建双向队列 
d = deque() 
d.append('1') 
d.append('2')

# append()向队列中插入数据（从右边插入） 
d.append('3') 
print(d) 

```

deque(['1', '2', '3'])
    


```python
# appendleft()向队列中插入数据（从左边插入） 
d.appendleft('4') 
print(d) 
```

deque(['4', '1', '2', '3'])
    


```python

## clear()清空队列 
d.clear() 
print(d) 
```

deque([])



```python

# count()计数 
d.append('1') 
print(d) 
d.count('1') 
```

deque(['1'])

1




```python
# extend()从右边向队列添加额外元素 
d.extend(['qq','ww','ee']) 
print(d) 


```

deque(['1', 'qq', 'ww', 'ee'])
    


```python

## extendleft()从左边向队列添加元素 
d.extendleft(['qq','ww','ee']) 
print(d) 



```

deque(['ee', 'ww', 'qq', '1', 'qq', 'ww', 'ee'])



```python
# index()取得元素下标 
d.index('1') 



```




3




```python
# insert()指定位置插入元素 
d.insert(1,'nn') 
print(d) 


```

deque(['ee', 'nn', 'ww', 'qq', '1', 'qq', 'ww', 'ee'])



```python
# pop()从右边移除一个元素 
d.pop() 

print(d) 
deque(['1','nn'])


```

deque(['ee', 'nn', 'ww', 'qq', '1', 'qq', 'ww'])





deque(['1', 'nn'])




```python
# popleft()从左边移除一个元素 
d.popleft() 
print(d) 


```

deque(['nn', 'ww', 'qq', '1', 'qq', 'ww'])
    


```python
# remove()移除指定元素 
d.remove('1') 
print(d) 
deque(['2'])


```

  deque(['nn', 'ww', 'qq', 'qq', 'ww'])





  deque(['2'])




```python
# reverse()反转队列 
print(d) 
d.reverse() 
print(d) 
deque(['2','1'])

```

  deque(['nn', 'ww', 'qq', 'qq', 'ww'])
  deque(['ww', 'qq', 'qq', 'ww', 'nn'])
  deque(['2', '1'])




```python

## rotate()将右边指定的元素个数移到队列左边 
d.append('4') 
d.append('5') 
d.append('6') 
print(d) 
d.rotate(3) 
print(d) 


```

  deque(['ww', 'qq', 'qq', 'ww', 'nn', '4', '5', '6'])
  deque(['4', '5', '6', 'ww', 'qq', 'qq', 'ww', 'nn'])


#  单向队列（先进先出 FIFO ）



```python
import queue # 创建单向队列 
>>> q = queue.Queue()

1.添加元素 
>>> q.put('11') 
>>> q.put('22')

2.qsize()获取队列中元素个数 
>>> q.qsize() 
2

3.get()取得元素（先进先出) 
>>> q.get() 
11 
>>> q.get() 
22
```
