@Author：Runsen
@Date：2020/7/10


> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

、辣鸡的我决定继续更新Python教程，今天就开始了八十七、Python | 十大排序算法系列（上篇）。还有不到区区的十三篇，我快完成了。

如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。



关于排序就是下面的十大排序算法

![](https://img-blog.csdnimg.cn/20200708224346201.png)

@[toc]


# 冒泡排序


python实现冒泡排序的核心思想是通过从列表一端迭代循环元素，再通过一个循环让这个元素之后的元素相邻两个比较，从而依次将最大值移动到最末端，如下图示意。

![](https://img-blog.csdnimg.cn/20200710225605314.png)

Python冒泡排序的代码实现。




```csharp
def bubble_sort(nums):
    for i in range(len(nums) - 1):
        for j in range(len(nums) - i - 1):
            if nums[j] > nums[j + 1]:
                nums[j], nums[j + 1] = nums[j + 1], nums[j]
    return nums
```
# 选择排序

排序算法：首先搜索整个列表，找到最小项的位置，如果该位置不是列表的第1项，就交换这两个位置的元素。然后从列表的第2个元素开始，重复上述过程，直到算法达到整个过程的最后一个位置，图形解释如下


下面使用55、23、87、62、16数列从小到大的排序过程来说明选择排序法的演算流程。原始数据如图：


1、首先找到此数列中最小值后，与数列中的第一个元素交换，如下图所示。

![](https://img-blog.csdnimg.cn/20200710225916995.png)


从第二个值开始找，找到剩余数列中（不含第一个填充为绿色的数字）的最小值，再和第二个值交换，如下图所示。

![](https://img-blog.csdnimg.cn/20200710230000474.png)


从第三个值开始找，找到此数列中（不含第一、二个的最小值），再和第三个值交换，如下图


![](https://img-blog.csdnimg.cn/20200710230017145.png)



从第四个值开始找，找到剩余数列的最小值，再和第四个值交换，排序完成，如下图。


![](https://img-blog.csdnimg.cn/20200710230038146.png)


Python选择排序的代码实现。

```csharp
def selectionSort(x):
   i = 0
   while i < len(x) - 1:
       minindex = i
       j = i + 1
       while j < len(x) :        
           if x[minindex] > x[j]:
               minindex = j
           j+= 1
       if minindex != i:
           swap(x,i,minindex)    
       i+= 1
   return x
```

# 插入排序

插入排序的实现思路顾名思义，就是不断地在一个已经是有序的数组中，寻找合适位置并插入新元素。

从后往前依次进行比较，如果待插入元素大于当前元素，则将待插入元素插入到当前元素的后一位，如果待插入元素小于当前元素，则将当前元素后移一位。不断重复该过程直至到数组的最后一位

![](https://img-blog.csdnimg.cn/20200710230139430.png)


Python插入排序的代码实现。


```csharp
def insertion_sort(a):
    length = len(a)
    if length <=1:
        return 
    for i in range(1,length):
        j = i-1
        value = a[i]
        while j >=0:
            if a[j]<value:
                a[j+1] = value
                break
            else:
                a[j+1] = a[j]
                if j == 0:
                    a[j] = value 
            j -=1
        print(a)
    return a
```
# 希尔排序
希尔排序的基本思想是：把记录按步长 gap 分组，对每组记录采用直接插入排序方法进行排序。

随着步长逐渐减小，所分成的组包含的记录越来越多，当步长的值减小到 1 时，整个数据合成为一组，构成一组有序记录，则完成排序。



我们画个图来说明一下


![](https://img-blog.csdnimg.cn/20200710231113715.png)
上面的排序其实和冒泡排序很像，只不过冒泡排序是每次都是间隔为1相邻的两个之间进行比较，但希尔排序是间隔为step，还是有一定区别的。

Python 希尔排序的代码实现。





```csharp
def shell_sort(list):
    n = len(list)
    gap = n // 2
    while gap >= 1:
        for j in range(gap, n):
            i = j
            while( i - gap ) >= 0:
                if list[i] < list[ i - gap ]:
                    list[i], list[ i - gap ] = list[ i - gap ], list[i]
                    i -= gap
                else:
                    break
        gap //= 2
        
if __name__ == '__main__':
    alist = [54, 26, 93, 17, 77, 31, 44, 55, 20]
    print("原列表为：%s" % alist)
    shell_sort(alist)
    print("新列表为：%s" % alist)
```
# 归并排序

 归并排序的基本思想：将待排序序列`R[0…n-1]`看成是`n`个长度为1的有序序列，将相邻的有序表成对归并，得到n/2个长度为2的有序表；将这些有序序列再次归并，得到`n/4`个长度为4的有序序列；如此反复进行下去，最后得到一个长度为n的有序序列。

![](https://img-blog.csdnimg.cn/2020071023152225.png)




归并排序其实要做两件事：

（1）“分解”——将序列每次折半划分。

（2）“合并”——将划分后的序列段两两合并后排序。







![](https://img-blog.csdnimg.cn/20200710231610643.gif)

Python 归并排序的代码实现。


```csharp
def merge(left, right):
    i = 0
    j = 0
    temp = []
    while i <= len(left) - 1 and j <= len(right) - 1:
        if left[i] <= right[j]:
            temp.append(left[i])
            i += 1
        else:
            temp.append(right[j])
            j += 1
    temp += left[i:] + right[j:]
    return temp

print(merge([1,3,4],[2,3,3])) 
```

