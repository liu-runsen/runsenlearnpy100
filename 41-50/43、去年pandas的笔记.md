
@Author：Runsen


@[TOC]


# pandas 
pandas 是基于NumPy 的一种工具，该工具是为了解决数据分析任务而创建的。Pandas 纳入了大量库和一些标准的数据模型，提供了高效地操作大型数据集所需的工具。pandas提供了大量能使我们快速便捷地处理数据的函数和方法。你很快就会发现，它是使Python成为强大而高效的数据分析环境的重要因素之一。

# 1.pandas数据结构的介绍
* Series：一维数组，与Numpy中的一维array类似。二者与Python基本的数据结构List也很相近。Series如今能保存不同种数据类型，字符串、boolean值、数字等都能保存在Series中。
* Time- Series：以时间为索引的Series。
* DataFrame：二维的表格型数据结构。很多功能与R中的data.frame类似。可以将DataFrame理解为Series的容器。
* Panel ：三维的数组，可以理解为DataFrame的容器。

 #  2.Series的操作
## 2.1 对象创建

```python
import pandas as pd
import numpy as np
# 直接创建
s = pd.Series(np.random.randn(5), index=['a','b','c','d','e'])
print(s) 
# 字典（dict）类型数据创建
s = pd.Series( {'a':10, 'b':20, 'c':30}, index=['b', 'c', 'a', 'd'])

OUT:
a   -0.620323
b   -0.189133
c    1.677690
d   -1.480348
e   -0.539061
dtype: float64

OUT:
a    10
b    20
c    30
dtype: int64
```

## 2.2 查看数据
   

切片、索引、dict操作
  
 Series既然是一维数组类型的数据结构，那么它支持想数组那样去操作它。通过数组下标索引、切片都可以去操作他，且它的data可以是dict类型的，那么它肯定也就支持字典的索引方式。
```python
import pandas as pd
import numpy as np

s = pd.Series(np.random.randn(5), index=['a','b','c','d','e'])

print(s)

# 下标索引
print('下标索引方式s[0] = : %s' % s[0])

# 字典访问方式
print('字典访问方式s[b] = ：%s' % s['b'])

# 切片操作
print('切片操作s[2:]\n:%s' % s[2:])
print('a' in s)
print('k' in s)
OUT:
a   -0.799676
b   -1.581704
c   -1.240885
d    0.623757
e   -0.234417
dtype: float64

下标索引方式s[0] = : -0.799676067487
字典访问方式s[b] = ：-1.58170351838
切片操作s[2:]:
c   -1.240885
d    0.623757
e   -0.234417
True
False
```
* 2.3 Series的算术操作
```python
import pandas as pd
import numpy as np

s1 = pd.Series(np.random.randn(3), index=['a','b','c'])

s2 = pd.Series(np.random.randn(3), index=['a','b','c'])
print(s1+s2)
print(s1-s2)
print(s1*s2)
print(s1/s2)
OUT:
a    0.236514
b   -0.132153
c    0.203186
dtype: float64

a    0.305397
b   -1.474441
c   -1.697982
dtype: float64

a   -0.009332
b   -0.539128
c   -0.710465
dtype: float64

a   -7.867120
b   -1.196907
c   -0.786252
dtype: float64
```
# 3.dataframe的操作
* 3.1 对象创建
    * 3.1.1字典创建
    * 3.1.1列表创建

```python
In [70]:  data = {'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada'],'year': [2000, 2001, 20
    ...: 02, 2001, 2002],'pop': [1.5, 1.7, 3.6, 2.4, 2.9]}
In [71]: data
Out[71]: 
{'pop': [1.5, 1.7, 3.6, 2.4, 2.9],
 'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada'],
 'year': [2000, 2001, 2002, 2001, 2002]}
# 建立DataFrame对象
In [72]: frame1 = DataFrame(data)
# 红色部分为自动生成的索引
In [73]: frame1
Out[73]: 
   pop   state  year
0  1.5    Ohio  2000
1  1.7    Ohio  2001
2  3.6    Ohio  2002
3  2.4  Nevada  2001
4  2.9  Nevada  2002

>>> lista = [1,2,5,7]
>>> listb = ['a','b','c','d']
>>> df = pd.DataFrame({'col1':lista,'col2':listb})
>>> df
   col1 col2
0     1    a
1     2    b
2     5    c
3     7    d
```
* 3.2 选择数据
    * 3.2.1 loc数值选取
    * 3.2.1 iloc位置选取
```python
In [1]: import numpy as np
   ...: import pandas as
   ...: df = pd.DataFrame

In [2]: df
Out[2]:
    a   b   c
0   0   2   4
1   6   8  10
2  12  14  16
3  18  20  22
4  24  26  28
5  30  32  34
6  36  38  40
7  42  44  46
8  48  50  52
9  54  56  58

In [3]: df.loc[0,'c']
Out[3]: 4

In [4]: df.loc[1:4,['a','c']]
Out[4]:
    a   c
1   6  10
2  12  16
3  18  22
4  24  28
In [5]: df.iloc[0,2]
Out[5]: 4

In [6]: df.iloc[1:4,[0,2]]
Out[6]:
    a   c
1   6  10
2  12  16
3  18  22
```
* 3.3 函数应用
```python
frame = pd.DataFrame(np.random.randn(4, 3), columns=list('bde'),
                     index=['Utah', 'Ohio', 'Texas', 'Oregon'])
frame
np.abs(frame)

OUT：
            b	     d            e
Utah	0.204708	0.478943	0.519439
Ohio	0.555730	1.965781	1.393406
Texas	0.092908	0.281746	0.769023
Oregon	1.246435	1.007189	1.296221


f = lambda x: x.max() - x.min()
frame.apply(f)
OUT：
b    1.802165
d    1.684034
e    2.689627
dtype: float64

def f(x):
    return pd.Series([x.min(), x.max()], index=['min', 'max'])
frame.apply(f)

            b	d	      e
Utah	-0.20	0.48	-0.52
Ohio	-0.56	1.97	1.39
Texas	0.09	0.28	0.77
Oregon	1.25	1.01	-1.30
```


## 3.4 统计概述和计算
```python
df = pd.DataFrame([[1.4, np.nan], [7.1, -4.5],
                   [np.nan, np.nan], [0.75, -1.3]],
                  index=['a', 'b', 'c', 'd'],
                  columns=['one', 'two'])
df
OUT:
    one     two
a	1.40	NaN
b	7.10	-4.5
c	NaN     NaN
d	0.75	-1.3


df.info()
df.describe()


<class 'pandas.core.frame.DataFrame'>
Index: 4 entries, a to d
Data columns (total 2 columns):
one    3 non-null float64
two    2 non-null float64
dtypes: float64(2)
memory usage: 256.0+ bytes

OUT：
          one          two
count	3.000000	2.000000
mean	3.083333	-2.900000
std	3.493685	2.262742
min	0.750000	-4.500000
25%	1.075000	-3.700000
50%	1.400000	-2.900000
75%	4.250000	-2.100000
max	7.100000	-1.300000
```
## 3.5 数据读取
 ###  3.5.1 读取csv
  ### 3.5.2 读取excel

```python
data = pd.read_csv('./dataset/HR.csv')
data.info()

out：
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 14999 entries, 0 to 14998
Data columns (total 10 columns):
satisfaction_level       14999 non-null float64
last_evaluation          14999 non-null float64
number_project           14999 non-null int64
average_montly_hours     14999 non-null int64
time_spend_company       14999 non-null int64
Work_accident            14999 non-null int64
left                     14999 non-null int64
promotion_last_5years    14999 non-null int64
sales                    14999 non-null object
salary                   14999 non-null object
dtypes: float64(2), int64(6), object(2)
memory usage: 1.1+ MB

data = pd.read_csv('./dataset/movielens/movies.dat', header=None, names=['name', 'types'], sep='::', engine='python')
data.head()
OUT：
                name	types
1	Toy Story (1995)	Animation|Children's|Comedy
2	Jumanji (1995)	Adventure|Children's|Fantasy
3	Grumpier Old Men (1995)	Comedy|Romance
4	Waiting to Exhale (1995)	Comedy|Drama
5	Father of the Bride Part II (1995)	Comedy


data = pd.read_excel('./dataset/my_excel.xlsx', sheet_name=1)
data.head()
ouput:
        date	H1	H2	H3
0	2014-06-01	1	2	3
1	2014-06-02	2	3	4
2	2014-06-03	3	4	5
3	2014-06-04	4	5	6
```

# 4. Time- Series的操作
* 生成日期范围：
```python
import pandas as pd
pd.data_range('20190313',periods=10)

OUT:
DatetimeIndex(['2019-03-13', '2019-03-14', '2019-03-15', '2019-03-16',
               '2019-03-17', '2019-03-18', '2019-03-19', '2019-03-20',
               '2019-03-21', '2019-03-22'],
              dtype='datetime64[ns]', freq='D')
```
# 5. 绘图功能
```
ts = pd.DataFrame(np.random.randn(1000,4),index=pd.date_range('20180101',periods=1000),columns=list('abcd'))
ts = ts.cumsum()
ts.plot(figsize = (12,8))
plt.show()
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190313200310360.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)
