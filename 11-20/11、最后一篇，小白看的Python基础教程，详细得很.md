

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS80ZTZmMDNiYy1hODk1LTRjYmUtYmNkYy0wNTBmNmEzNmQyZmUucG5n?x-oss-process=image/format,png)




@Author：Runsen


作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。



往期回顾：
[第一篇、小白看的 Python 基础教程，详细得很（八）](https://maoli.blog.csdn.net/article/details/105242372)



[第二篇、小白看的 Python 基础教程，详细得很（九）](https://maoli.blog.csdn.net/article/details/105242405)


[第三篇、小白看的 Python 基础教程，详细得很（十）](https://maoli.blog.csdn.net/article/details/105242296)







@[TOC]







# 13、Python标准库


Python标准库是随Pthon附带安装的，包含了大量极其有用的模块。


我们主要了解下sys和os就够了。


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS80ZTZmMDNiYy1hODk1LTRjYmUtYmNkYy0wNTBmNmEzNmQyZmUucG5n?x-oss-process=image/format,png)


##  13.1 sys模块　　

sys模块主要是针对与Python解释器相关的变量和方法，不是主机操作系统。



```python
sys.argv    #获取命令行参数列表，第一个元素是程序本身
sys.exit(n) #退出Python程序，exit(0)表示正常退出。当参数非0时，会引发一个SystemExit异常，可以在程序中捕获该异常
sys.version #获取Python解释程器的版本信息
sys.maxsize #最大的Int值，64位平台是2**63 - 1
sys.path    #返回模块的搜索路径，初始化时使用PYTHONPATH环境变量的值
sys.platform    #返回操作系统平台名称
sys.stdin   #输入相关
sys.stdout  #输出相关
sys.stderr  #错误相关
sys.exc_info()  #返回异常信息三元元组
sys.getdefaultencoding()    #获取系统当前编码，默认为utf-8
sys.setdefaultencoding()    #设置系统的默认编码
sys.getfilesystemencoding() #获取文件系统使用编码方式，默认是utf-8
sys.modules #以字典的形式返回所有当前Python环境中已经导入的模块
sys.builtin_module_names    #返回一个列表，包含所有已经编译到Python解释器里的模块的名字
sys.copyright   #当前Python的版权信息
sys.flags   #命令行标识状态信息列表。只读。
sys.getrefcount(object) #返回对象的引用数量
sys.getrecursionlimit() #返回Python最大递归深度，默认1000
sys.getsizeof(object[, default])    #返回对象的大小
sys.getswitchinterval() #返回线程切换时间间隔，默认0.005秒
sys.setswitchinterval(interval) #设置线程切换的时间间隔，单位秒
sys.getwindowsversion() #返回当前windwos系统的版本信息
sys.hash_info   #返回Python默认的哈希方法的参数
sys.implementation  #当前正在运行的Python解释器的具体实现，比如CPython
sys.thread_info #当前线程信息
```


上面是sys模块所有语法，我们看看就够了，了解下sys.argv和sys.path就足够了



sys.argv是一个脚本执行参数列表，列表的第一个元素是脚本名称，从第二个元素开始才是真正的参数。


```python
# test.py
import sys

for index, arg in enumerate(sys.argv):
    print("第%d个参数是： %s" % (index, arg))

#输出
第0个参数是： test.py
第1个参数是： 1
第2个参数是： 2
第3个参数是： 3
第4个参数是： 4 
```


argv：获取程序外部向程序传递的参数



```python
#  script.py

import sys
print(sys.argv[0])
print(sys.argv[1])
```
运行：

```python
# python script.py argv1
sys.py
argv1
```



sys.path


path是一个目录列表，供Python从中查找模块。在Python启动时，sys.path根据内建规则和PYTHONPATH变量进行初始化。sys.path的第一个元素通常是个空字符串，表示当前目录。
```python
>>> sys.path
['', 'C:\\Python36\\Lib\\idlelib', 'C:\\Python36\\python36.zip', 'C:\\Python36\\DLLs', 'C:\\Python36\\lib', 'C:\\Python36', 'C:\\Python36\\lib\\site-packages']
```

sys.path本质上是一个列表，可以进行append、insert、pop、remove等各种列表相关的操作，但通常都进行append操作，添加自己想要的查找路径。


sys.stdin、sys.stdout、sys.stderr


- stdin用于所有的交互式输入（包括input()函数）。
- stdout用于print()的打印输出或者input()函数的提示符。
- stderr用于解释器自己的提示信息和错误信息。

简而言之，这三个属性就是操作系统的标准输入、输出和错误流，它们返回的都是一个“文件类型”对象，支持read()、write()和flush()等操作。



```python
>>> import sys
>>> s = sys.stdin.readline()        
i don't like python
>>> s
'i don't like python\n'
>>> sys.stdout.write(s)
i don't like python 
20
```





python3中sys.stdin与input的区别：

input()方法和stdin()类似，不同的是input()括号内可以直接填写说明文字。

```python
s = input('Please input something！')

print('Please input something！',)  # 逗号表示不换行
s = sys.stdin.readline()[:-1]  # -1 抛弃输入流中的'\n' 换行符
```


当我们print(obj)的时候，事实上是调用了sys.stdout.write(obj+'\n')，将内容打印到控制台（默认是显示器），然后追加一个换行符。以下两行等价：



```python
sys.stdout.write('hello'+'\n') 
print('hello')
```







## 13.2 os模块　　

该模块包含普遍的操作系统功能
- os.name字符串指示你正在使用的平台。比如对于Windows，它是'nt'，而对于Linux/Unix用户，它是'posix'

- 	os.getcwd()函数得到当前工作目录，即当前Python脚本工作的目录路径
- os.getenv()和os.putenv()函数分别用来读取和设置环境变量
-	os.listdir()返回指定目录下的所有文件和目录名
- 	os.remove()函数用来删除一个文件
- 	os.system()函数用来运行shell命令
-	os.linesep字符串给出当前平台使用的行终止符。例如，Windows使用'\r\n'，Linux使用'\n'而Mac使用'\r'
- 	os.sep 操作系统特定的路径分割符
-	os.path.split()函数返回一个路径的目录名和文件名
-	os.path.isfile()和os.path.isdir()函数分别检验给出的路径是一个文件还是目录
-	os.path.existe()函数用来检验给出的路径是否真地存在

# 14、类中的特别方法


 
 
名称|	说明
--|--
__init__(self,...)	|这个方法在新建对象恰好要被返回使用之前被调用。
__del__(self)	|恰好在对象要被删除之前调用。
__str__(self)	|在我们对对象使用print语句或是使用str()的时候调用。
__getitem__(self,key)|	使用x[key]索引操作符的时候调用。
__len__(self)	|对序列对象使用内建的len()函数的时候调用。



下面的类中定义了上表中的方法：
```python
class Array:
    __list = []

    def __init__(self):
        print "constructor"

    def __del__(self):
        print "destructor"

    def __str__(self):
        return "this self-defined array class"

    def __getitem__(self, key):
        return self.__list[key]

    def __len__(self):
        return len(self.__list)

    def Add(self, value):
        self.__list.append(value)

    def Remove(self, index):
        del self.__list[index]

    def DisplayItems(self):
        print "show all items----"
        for item in self.__list:
            print item

arr = Array()   #constructor
print(arr)    #this self-defined array class
print(len(arr))   #0
arr.Add(1)
arr.Add(2)
arr.Add(3)
print(len(arr))   #3
print(arr[0])   #1
arr.DisplayItems()
#show all items----
#1
#2
#3
arr.Remove(1)
arr.DisplayItems()
#show all items----
#1
#3
#destructor
```




#  15、列表推导式


 
通过列表综合，可以从一个已有的列表导出一个新的列表。

```python
list1 = [1, 2, 3, 4, 5]
list2 = [i*2 for i in list1 if i > 3]

print(list1)  #[1, 2, 3, 4, 5]
print(list2)  #[8, 10]
```


# 16、 *和**args区别




当函数接收元组或字典形式的参数的时候，有一种特殊的方法，使用*和**前缀。

该方法在函数需要获取可变数量的参数的时候特别有用。
　


由于在args变量前有*前缀，所有多余的函数参数都会作为一个元组存储在args中。如果使用的是**前缀，多余的参数则会被认为是一个字典的键/值对。


 *args接受元组
 
**args接受字典
 


```python
def powersum(power, *args):
    total = 0
    for i in args:
        total += pow(i, power)
    return total

print (powersum(2, 1, 2, 3))  

#14 1^2+2^2+3^2 = 14


def displaydic(**args):
    for key,value in args.items():
        print( "key:%s;value:%s" % (key, value))

displaydic(a="one", b="two", c="three")


#key:a;value:one
#key:c;value:three
#key:b;value:two
```


# 17、lambda函数

lambda语句被用来创建新的函数对象，并在运行时返回它们。lambda需要一个参数，后面仅跟单个表达式作为函数体，而表达式的值被这个


新建的函数返回。 注意，print语句也不能用在lambda形式中，只能使用表达式。
```python
func = lambda s: s * 3
print(func("Runsen "))  # Runsen Runsen Runsen


func2 = lambda a, b: a * b

print(func2(2, 3))  #6
```


# 18、exec/eval



exec语句用来执行储存在字符串或文件中的Python语句


eval语句用来计算存储在字符串中的有效Python表达式。




```python　　　　
cmd = "print 'hello world'"
exec cmd   #hello world

expression = "10 * 2 + 5"
print(eval(expression))    #25
```


exec还批量创建变量，这个大家可能忽视



```python
for i in range(8):
    exec('v' + str(i) + ' = ' + str(i))
    print('v' + str(i) + ':', eval('v' + str(i)))
    
v0: 0
v1: 1
v2: 2
v3: 3
v4: 4
v5: 5
v6: 6
v7: 7
    
```



# 19、assert


assert语句用来断言某个条件是真的，并且在它非真的时候引发一个错误--AssertionError。
```python
>>> assert True     # 条件为 true 正常执行
>>> assert False    # 条件为 false 触发异常
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError
```


assert一般和try except连用
```python
flag = True

assert flag == True

try:
    assert flag == False
except AssertionError:
    print ("failed")
else:
    print ("pass")
    
    
failed
```

# 20、repr





repr函数用来取得对象的规范字符串表示。

注意，在大多数时候有eval(repr(object)) == object。

可以通过定义类的__repr__方法来控制对象在被repr函数调用的时候返回的内容。

```python
arr = [1, 2, 3]
print(arr)    #[1, 2, 3]
print(repr(arr))    #[1, 2, 3]
```



其实Python就是这么简单，学Python就是看官方文档，看demo，代码跟做英语阅读似的，多看官方文档，然后调下第三方库，实现需求就行了。






