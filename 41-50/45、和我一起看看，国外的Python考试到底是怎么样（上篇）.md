@Author ： By Runsen
@Written Date：2020/05/20


@[TOC]

# 前言

我是在4月底帮别人考试的，然后别人发过来去年的考试题的。我看了下，全是英文，原来是留学生啊。


走，我带你们看看国外的Python考试题到底是什么辣鸡东西？



![](https://img-blog.csdnimg.cn/20200520093613896.png)

看了下，好像我英语不行，但也知道满分是70，什么辣鸡玩意，一脸懵逼



# 第一题


![](https://img-blog.csdnimg.cn/20200520093834495.png)




就是要我定义samPlaces函数方法，主要这个是需要O（n)的时间复杂度，对于我这老油条来说，就是一个切菜的东西，直接用字典，Leetcode第一题的两数相加就是这个玩意。难度0，切菜级别




```css
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/4/23
'''
'''
输出两个列表的相同的索引
'''
def samPlaces(s1,s2):
    if len(s1) != len(s2):
        return []
    my_dict = {}
    my_index = []
    for index,item in enumerate(s1):
        my_dict[item] = index
    for i in s2:
        if i in my_dict.keys() and my_dict[i] == s2.index(i):
            my_index.append(my_dict[i])
    return my_index
if __name__ == '__main__':
    print(samPlaces([1,7,9],[1,3,9]))
```
# 第二题

![](https://img-blog.csdnimg.cn/20200520100505451.png)


![](https://img-blog.csdnimg.cn/20200520100522829.png)

![](https://img-blog.csdnimg.cn/2020052010092650.png)

![](https://img-blog.csdnimg.cn/20200520101007795.png)
二题看的我就是一个煞笔，一个InputOuput.py 就是读取文件的，第二Quicsort.py就是快速排序的。第三个是一个字符串开头和结尾字符要相同。4+3+5+4+4=20分


第一个问我Manipulation.py输出什么，这不是当我傻逼，如果单词前后字母都相同，直接del，沙比。


答案是

```css
['cat', 'elephant']
[]
```
第二题，我去，这么简单，太简单了，送分的


```css
begin
this
is
a
test
end
```
第三题，用一个函数main（）编写一个程序，就是读取，再排序，再去除单词前后字母都相同，然后将结果字符串写入名为cookedData.txt文件


```css
def readFromFile(filename):
    lst = []
    fp = open(filename,"r")
    item = fp.readline().strip()
    while item != '':
        lst.append(item)
        item = fp.readline().strip()
    fp.close()

    return lst

def writeTofile(contents,filename):
    fp = open(filename,"w")
    fp.write("begin\n")
    for item in contents:
        fp.write(item + " ")
    fp.write("\nend")
    fp.close()

def sort(lis):
    if len(lis) < 2:
        return lis
    less, equal ,greater = [],[],[]
    pval = lis[0]
    for i in lis:
        if i < pval :
            less.append(i)
        elif i > pval:
            greater.append(i)
        else:
            equal.append(i)
    return sort(less) + equal + sort(greater)

def modifylist(values):
    i=0
    while i <  len(values):
        if values[i][0] == values[i][-1] or (" " in values[i]):
           del values [i]
        else:
            i +=1
            
if __name__ == '__main__':
    # ['for loop', 'link list', 'return', 'CISC', 'binary rearch tree', 'variable']
    data = readFromFile("rawData.txt")
    # ['CISC', 'binary rearch tree', 'for loop', 'link list', 'return', 'variable']
    sort_data = sort(data)
    modifylist(sort_data)
    print(sort_data)  # ['return', 'variable']
    writeTofile(sort_data,"cookedData.txt")


```

第四题，都是切菜切菜

```css
# cookedData.txt
begin
return variable 
end
```




第五题，将在快速排序中按降序（从最大值到最小值）排序，辣鸡，简单，大于变小于，小于变大于。
```css
def sort(lis):
    if len(lis) < 2:
        return lis
    less, equal ,greater = [],[],[]
    pval = lis[0]
    for i in lis:
        if i > pval :
            less.append(i)
        elif i < pval:
            greater.append(i)
        else:
            equal.append(i)
    return sort(less) + equal + sort(greater)
if __name__ == '__main__':
    print(sort([17,-28,11,9,15,-2]))
    # [17, 15, 11, 9, -2, -28]
```


# 第三题



填空题选择题， 我看看。好像挺难的。
![](https://img-blog.csdnimg.cn/20200520110048350.png)

![](https://img-blog.csdnimg.cn/20200520110103721.png)

第一题，如果在未排序的列表上使用二分搜索，下面对的是哪个？


A，程序崩了？你才崩了
B、永远找不到要查找的值。这么绝对，比如[2,1,3,5,4]，我要找3，不就打脸了吗？
C、有时搜索能成功，不用说了，就是你
D、时间复杂度发生改变，程度不变，你时间复杂度变个毛

我觉得就是C，送分，切菜


第二题、使用二分搜索来按升序搜索数字列表，但有些数字出现了不止一次。以下哪个是正确的？


A、搜索始终找到第一个发生
B、搜索始终找到最后一个发生
C、搜索有时找到第一个，有时找到最后一个
D、时间复杂度发生改变

如果是[1,1,2,3,5,6,] 找1，是[1,2,3,4,5,5,] 找4，所以搜索找到的位置不能明确，二分查找在最坏情况下是在排除到只剩下最后一个值之后得到结果，二分查找的时间复杂度O(log2n)，如果出现相同的数字，时间复杂度应该发生改变，答案我觉得是D


第三题、冒泡排序，对以下列表进行排序数值：[17，5,12,13,16,3]，显示冒泡排的第一次迭代后的列表


[练习、Python实现冒泡排序（三十九）](https://maoli.blog.csdn.net/article/details/105119302)

我这篇搞定了，辣鸡东西，一个外循环，切菜送分

```css
[5,12,13,16,3,17]
```

第四题，选择排序，插入排序，冒泡排序选一个，


![](https://img-blog.csdnimg.cn/20200520111951448.png)



摆明选择，这他妈的简单一笔




第五题


在合并排序中，将列表重复拆分，然后将排序列表重新合并在一起。显示这两者的合并结果列表：[4，7,9,12]，[1,4,6,8,15]   合并成 [1, 4.，6，7，8，9，12，15,。需要代码实现，

这有点难度，但是也是很基础的排序。就是切菜，辣鸡




```css
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/4/25
'''
def merge(a, b):
    '''
    合并排序：两个已经排序好的
    '''
    c = []
    h = j = 0
    # 谁小加谁
    while j < len(a) and h < len(b):
        if a[j] < b[h]:
            c.append(a[j])
            j += 1
        # 相同也没事
        else:
            c.append(b[h])
            h += 1
    # 有的时候 j 直接达到了len(a)，那么直接append b剩下的
    if j == len(a):
        for i in b[h:]:
            c.append(i)
    if h == len(b):
        for i in a[j:]:
            c.append(i)
    return c

if __name__ == '__main__':
    print(merge([4,7,9,12],[1,4,6,8,15]))
    # [1, 4, 4, 6, 7, 8, 9, 12, 15]
```



# 第四题

![](https://img-blog.csdnimg.cn/20200520112531575.png)

![](https://img-blog.csdnimg.cn/20200520113620386.png)
我还以为什么东西，练习时间复杂度，切菜


第一题

![](https://img-blog.csdnimg.cn/20200520113655623.png)



时间复杂度$O(N^2)$



第二题



![](https://img-blog.csdnimg.cn/20200520114051865.png)

取整除等于用`//=`来进行表示。一样的道理


一个堆排序的样子，时间复杂度$O(N*log_2N)$

第三题
![](https://img-blog.csdnimg.cn/20200520114608591.png)

时间复杂度$O(N)$

第四题




![](https://img-blog.csdnimg.cn/20200520114748294.png)

时间复杂度$O(N^2)$



我没有答案的，就是自己瞎逼逼的，先到这，有点长了


