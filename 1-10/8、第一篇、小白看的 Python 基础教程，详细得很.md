



本文是第一篇，一共四篇打下Python基础

@Author：Runsen

@Date：Writern By 2019/04/15 and supplied By 2020/3/31

@公众号：Python之王

为了照顾小白，我把之前的博客上的Python基础分享过来。好像是18年的时候，大一的东西。


一共四篇，声明下：Python的入门难度为0，比Java，C++根本不能比，你会英语基本没问题。

本文是第一篇



@[TOC]
# 1、基本概念


## 1.1 四种类型

python中数有四种类型：整数、长整数、浮点数和复数。
　　
- 	整数， 如 1
- 	长整数 是比较大的整数
- 浮点数 如 1.23、3E-2
- 复数 如 1 + 2j、 1.1 + 2.2j

## 1.2 字符串

字符串（字符的序列）
　　
- 	python中单引号和双引号使用完全相同。
- 	使用三引号('''或""")可以指定一个多行字符串。
- 	转义符 `'\'`
- 	自然字符串， 通过在字符串前加r或R。 如` r"this is a line with \n"` 则`\n`会显示，并不是换行。
- 	python允许处理`unicode`字符串，加前缀u或U， 如 `u"this is an unicode string"`。
-   字符串是不可变的。
- 	按字面意义级联字符串，如"this " "is " "string"会被自动转换为this is string。

## 1.3 标识符的命名
标识符的命名


- 	第一个字符必须是字母表中字母或下划线'_'。
- 	标识符的其他的部分有字母、数字和下划线组成。
- 	标识符对大小写敏感。


## 1.4 对象


　python程序中用到的任何“东西”都成为“对象”。

## 1.5 逻辑行和物理行


- 物理行：就是程序员所写代码的所在行。
- 逻辑行：是指源代码经过预编译后，代码所在的那一行。


Python假定每个物理行都对应着一个逻辑行。例如：print( "Hello World" ) 就是一个物理行，Python希望每行只有一个语句，因为这样看起来更加易读。

如果你想要在一个物理行中使用多于一个逻辑行，那么你需要使用分号（; ）来特别地标明这种用法。分号表示一个逻辑行/语句的结束。

例如：
```python
count = 5
print ( "count" )
```
与下面的语句等同：
```python
count = 5；
print ( "count" );
```
当然也可以写成下面这种：
```python
count = 5 ; print ( "count" );
```
甚至可以写成这样：
```python
count = 5 ; print ( "count" )
````

我们使用`\`的换行

```python
print \
("Runsen")

```

## 1.6 缩进
空白在python是非常重要的，行首的空白是最重要的，又称为缩进。行首的空白（空格和制表符）用来决定逻辑行的缩进层次，从而决定语句。


# 2、运算符与表达式
## 2.1 运算符与其用法
|运算符|名称|例子|
|--|---|---|
|+	|两个对象相加	|加法，如3 + 5得到8,字符也可以相加'a' + 'b'得到'ab'|
|-	|一个数减去另一个数	|  5 - 2得到3|
|*|	乘	两个数相乘或是返回一个被重复若干次的字符串| 	2 * 3得到6,'a' * 3得到'aaa'|
|**|	幂	返回x的y次幂	|3 ** 4得到81（即3 * 3 * 3 * 3）
|/	|除	x除以y	| 4/3得到1（整数的除法得到整数结果）。4.0/3或4/3.0得到1.3333
|//	|取整除	返回商的整数部分|	4 // 3.0得到1.0
|%|取模	返回除法的余数|	8%3得到2。-25.5%2.25得到1.5
|<<|	左移，把一个数的二进制左移一定数目，也就是在右边补多少个0，	| 如	2 << 2得到8，二进制10变成1000
|>>|	右移	把一个数的比特向右移一定数目,也就是在右边删除位数|	10>>2得到2，二进制1010变成10，直接删除后面2位
|&	|按位与|	数的按位与	9 & 13得到9，二进制1001&1101，变成1001，两个值相应的位置都为1，那么该结果就是1，不然就是0
|\||	按位或	|数的按位或	5 \| 3得到7。二进制101&11，变成111，如果两个值相应的位置有一个是1,那么该结果就是1，也就是如果都是0，该结果就是0，101和11没有都是0，所以111
|^	|按位异或	| 数的按位异或	5 ^ 3得到6，二进制101&11，变成110，两个值相应的位置相同,那么该结果就是0，也就是如果都是0或者都是1，该结果就是0，101和11，第一个都是1，所以110
|~|	按位翻转	|x的按位翻转是-(x+1)	~5得到6
|<	|小于	返回x是否小于y。|所有比较运算符返回1表示真，返回0表示假。	5 < 3返回0（即False）而3 < 5返回1（即True）。还可以被任意连接：3 < 5 < 7返回True。
|>|	大于	返回x是否大于y	|5 > 3返回True。如果两个操作数需要都是数字
|<=	|小于等于	返回x是否小于等于y|	x = 3; y = 6; x <= y返回True
|>=	|大于等于	返回x是否大于等于y	|x = 4; y = 3; x >= y返回True
|==	|等于	比较对象是否相等|	x = 2; y = 2; x == y返回True
|!=|	不等于	比较两个对象是否不相等	|x = 2; y = 3; x != y返回True。
|not|	布尔“非”	如果x为True，返回False|	x = True; not y返回False。
|or|	布尔“或”	如果x是True，它返回True，否则它返回y的计算值。|	x = True; y = False; x or y返回True|

## 2.2 运算符优先级
.运算符优先级（从低到高）

| 运算符 | 描述 |
|--|--|
|lambda  | Lambda表达式 |
|or  | 	布尔“或” |
|and  |	布尔“与” |
|not x  |布尔“非” |
|in，not in | 成员测试 |
|is，is not	  |同一性测试 |
|<，<=，>，>=，!=，==  |比较 |
|  `| ` |按位或 |
|  ^ |按位异或 |
|  `| ` |按位或 |
|  & |按位与 |
| <<，>> |移位 |
|  +，-	 |加法与减法|
| *，/，% |乘法、除法与取余 |
| +x，-x |正负号 |
|  ~x|按位翻转 |
|  **	|指数 |
|  ~x|按位翻转 |
|  x.attribute|属性参考 |
|  x[index]|下标 |
|  x[index:index]|寻址段 |
|  f(arguments...)|函数调用 |
|  (experession,...)|绑定或元组显示 |
|  [expression,...]	|列表显示 |
|  {key:datum,...}|字典显示 |
|  'expression,...'|字符串 |



## 2.3 输出
python 控制台输出 使用print
```python
print ("abc"  )　　#打印abc并换行
print ("abc%s" % "d"  )　　#打印abcd
print ("abc%sef%s" % ("d", "g")  )　　#打印abcdefg
```
# 3、控制流

## 3.1 if 语句
```python
i = 10
n = int(input("enter a number:"))

if n == i:
    print( "equal")
elif n < i:
    print( "lower")
else:
    print ("higher")
```


## 3.2 while语句
```python
while True:
    pass
else:
    pass
#else语句可选，当while为False时，else语句被执行。 pass是空语句。
```

for 循环 for..in
```python
for i in range(0, 5):
    print (i)
else:
    pass
# 打印0到4
```
注：当for循环结束后执行else语句；
`range(a, b)返回一个序列，从a开始到b为止，但不包括b，range默认步长为1，可以指定步长，range(0,10,2)；`




## 3.3 break语句

终止循环语句，如果从for或while中终止，任何对应循环的else将不执行。

## 3.4 continue语句

continue语句用来调过当前循环的剩余语句，然后继续下一轮循环。

下面就是 break 和 continue 主要的 区别：
- break：跳出整个循环
- continue：跳出本次循环，继续执行下一次循环
希望大家牢记。





# 4、函数

函数通过def定义。def关键字后跟函数的标识符名称，然后跟一对圆括号，括号之内可以包含一些变量名，该行以冒号结尾；接下来是一块语句，即函数体。

```python
def sumOf(a, b):
    return a + b
```
## 4.1  函数形参

函数中的参数名称为‘形参’，调用函数时传递的值为‘实参’


## 4.2 局部变量

在函数内定义的变量与函数外具有相同名称的其他变量没有任何关系，即变量名称对于函数来说是局部的。这称为变量的作用域。

`global语句， 为定义在函数外的变量赋值时使用global语句。`


```python
def func():
    global x
    print( "x is ", x)
    x = 1

x = 3
func()
print(x)
#3
#1 
```




## 4.3 默认参数


通过使用默认参数可以使函数的一些参数是‘可选的’。
```python　　
def say(msg, times =  1):
    print(msg * times)

say("Runsen")
say("Runsen", 3)
```

注意：只有在形参表末尾的那些参数可以有默认参数值，即不能在声明函数形参的时候，先声明有默认值的形参而后声明没有默认值的形参，只是因为赋给形参的值是根据位置而赋值的。
　
## 4.4 关键参数

如果某个函数有很多参数，而现在只想指定其中的部分，那么可以通过命名为这些参数赋值（称为‘关键参数’）。
优点：不必担心参数的顺序，使函数变的更加简单；假设其他参数都有默认值，可以只给我们想要的那些参数赋值。
```python
def func(a, b=2, c=3):
    print ("a is %s, b is %s, c is %s") % (a, b, c)

func(1) #a is 1, b is 2, c is 3
func(1, 5) #a is 1, b is 5, c is 3
func(1, c = 10) #a is 1, b is 2, c is 10
func(c = 20, a = 30) #a is 30, b is 2, c is 20
```
## 4.5 return 语句

　return语句用来从一个函数返回，即跳出函数。可从函数返回一个值。
　没有返回值的return语句等价于return None。None表示没有任何东西的特殊类型。

## 4.5  文档字符串
`__doc__`   (文档字符串)
```python
def func():
    '''This is self-defined function
	Do nothing
	'''
    pass

print(func.__doc__)

#This is self-defined function
#
#Do nothing
```
# 5、模块

模块就是一个包含了所有你定义的函数和变量的文件，模块必须以.py为扩展名。模块可以从其他程序中‘输入’`(import)`以便利用它的功能。



在python程序中导入其他模块使用'import', 所导入的模块必须在sys.path所列的目录中，因为sys.path第一个字符串是空串''即当前目录，所以程序中可导入当前目录的模块。


## 5.1 字节编译的.pyc文件


导入模块比较费时，python做了优化，以便导入模块更快些。一种方法是创建字节编译的文件，这些文件以.pyc为扩展名。

pyc是一种二进制文件，是py文件经编译后产生的一种byte code，而且是跨平台的（平台无关）字节码，是有python虚拟机执行的，类似于


java或.net虚拟机的概念。pyc的内容，是跟python的版本相关的，不同版本编译后的pyc文件是不同的。

## 5.2  from .. import

如果想直接使用其他模块的变量或其他，而不加'模块名+.'前缀，可以使用from .. import。

例如想直接使用sys的argv，from sys import argv 或 from sys import *

## 5.3 模块的__name__


每个模块都有一个名称，py文件对应模块名默认为py文件名，也可在py文件中为__name__赋值；如果是__name__，说明这个模块被用户

(4)  dir()函数
- dir(sys)返回sys模块的名称列表；如果不提供参数，即dir()，则返回当前模块中定义名称列表。

(5)  del

del -> 删除一个变量/名称，del之后，该变量就不能再使用。

# 6、数据结构

python有三种内建的数据结构：列表、元组和字典。

## 6.1 列表

list是处理一组有序项目的数据结构，列表是可变的数据结构。列表的项目包含在方括号[]中，

eg: [1, 2, 3]， 空列表[]。判断列表中是否包含某项可以使用in， 

比如 l = [1, 2, 3]; print 1 in l; #True；

支持索引和切片操作；索引时若超出范围，则IndexError；

使用函数len()查看长度；使用del可以删除列表中的项，eg: del l[0] # 如果超出范围，则IndexError
　　　　
list函数如下：
```python　　　　
append（value）　　---向列表尾添加项value
l = [1, 2, 2]
l.append(3) #[1, 2, 2, 3]

count(value)　　---返回列表中值为value的项的个数
l = [1, 2, 2]
print( l.count(2)) # 2

extend(list2)　　---向列表尾添加列表list2
l = [1, 2, 2]
l1 = [10, 20]
l.extend(l1)
print (l )  #[1, 2, 2, 10, 20]

index(value, [start, [stop]])　　---返回列表中第一个出现的值为value的索引，如果没有，则异常 ValueError

l = [1, 2, 2]
a = 4
try:
    print( l.index(a))
except ValueError, ve:
    print( "there is no %d in list" % a
　　　　insert(i, value))　　---向列表i位置插入项vlaue，如果没有i，则添加到列表尾部

l = [1, 2, 2]

l.insert(1, 100)
print l #[1, 100, 2, 2]

l.insert(100, 1000)
print l #[1, 100, 2, 2, 1000]

pop([i])　　---返回i位置项，并从列表中删除；如果不提供参数，则删除最后一个项；如果提供，但是i超出索引范围，则异常IndexError

l = [0, 1, 2, 3, 4, 5]

print( l.pop()) # 5
print( l) #[0, 1, 2, 3, 4]

print( l.pop(1)) #1
print( l) #[0, 2, 3, 4]

try:
    l.pop(100)
except IndexError, ie:
    print( "index out of range")

remove(value)　　---删除列表中第一次出现的value，如果列表中没有vlaue，则异常ValueError

l = [1, 2, 3, 1, 2, 3]

l.remove(2)
print (l )#[1, 3, 1, 2, 3]

try:
    l.remove(10)
except ValueError, ve:
    print ("there is no 10 in list")

reverse()　　---列表反转

l = [1, 2, 3]
l.reverse()
print (l) #[3, 2, 1]

sort(cmp=None, key=None, reverse=False)　　---列表排序

l5 = [10, 5, 20, 1, 30]
l5.sort()
print( l5) #[1, 5, 10, 20, 30]

l6 = ["bcd", "abc", "cde", "bbb"]
l6.sort(cmp = lambda s1, s2: cmp(s1[0],s2[1]))
print( l6) #['abc', 'bbb', 'bcd', 'cde']

l7 = ["bcd", "abc", "cde", "bbb", "faf"]
l7.sort(key = lambda s: s[1])
print (l7) #['faf', 'abc', 'bbb', 'bcd', 'cde']
```




