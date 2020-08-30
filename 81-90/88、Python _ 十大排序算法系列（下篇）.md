@Author：Runsen
@Date：2020/7/10


> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)




辣鸡的我决定继续更新Python教程，今天就开始了八十八、Python | 十大排序算法系列（下篇）。还有不到区区的十二篇，我就完成了。

如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。



关于排序就是下面的十大排序算法

![](https://img-blog.csdnimg.cn/20200708224346201.png)


@[toc]


# 快速排序

快速排序的基本思想是：通过一趟排序将要排序的数据分割成独立的两部分：分割点左边都是比它小的数，右边都是比它大的数。


如果要排序数组中下标从 p 到 r 之间的一组数据，我们选择 p 到 r 之间的任意一个数据作为 pivot（分区点）。

我们遍历 p 到 r 之间的数据，将小于 pivot 的放到左边，将大于 pivot 的放到右边，将 pivot 放到中间。经过这一步骤之后，数组 p 到 r 之间的数据就被分成了三个部分，前面 p 到 q-1 之间都是小于 pivot 的，中间是 pivot，后面的 q+1 到 r 之间是大于 pivot 的。
![](https://img-blog.csdnimg.cn/20200710234816330.png)



我们通过实例来具体讲解一下：










![](https://img-blog.csdnimg.cn/20200710235338355.png)

上图来自王争算法专栏。


Python快速排序的代码实现。




```csharp
def quicksort(array):
  if len(array) < 2:
    # 基本情况下，具有0或1个元素的数组是已经“排序”的
    return array
  else:
    # 递归情况
    pivot = array[0]
    # 小于基准值的所有元素的子数组
    less = [i for i in array[1:] if i <= pivot]
    # 大于基准值的所有元素的子数组
    greater = [i for i in array[1:] if i > pivot]
    return quicksort(less) + [pivot] + quicksort(greater)

print(quicksort([10, 5, 2, 3]))
```
# 堆排序

**「堆」**首先是一个完全二叉树，**「堆」**分为**「大顶堆」**和**「小顶堆」**。
**「大顶堆」** ：每个节点的值大于或等于其左右孩子节点的值，称为大顶堆。
**「小顶堆」**：同理就是每个节点的值小于或等于其左右孩子节点的值。



![](https://img-blog.csdnimg.cn/20200710235739330.png)

下图就是堆排序的过程，来自五分钟学算法。

![](https://img-blog.csdnimg.cn/20200710235932234.gif)

排序动画过程解释

- 首先，将所有的数字存储在堆中

- 按大顶堆构建堆，其中大顶堆的一个特性是数据将被从大到小取出，将取出的数字按照相反的顺序进行排列，数字就完成了排序

- 在这里数字 5 先入堆

- 数字 2 入堆

- 数字 7 入堆， 7 此时是最后一个节点，与最后一个非叶子节点（也就是数字 5 ）进行比较，由于 7 大于 5 ，所以 7 和 5 交互

- 按照上述的操作将所有数字入堆，然后从左到右，从上到下进行调整，构造出大顶堆

- 入堆完成之后，将堆顶元素取出，将末尾元素置于堆顶，重新调整结构，使其满足堆定义

- 堆顶元素数字 7 取出，末尾元素数字 4 置于堆顶，为了维护好大顶堆的定义，最后一个非叶子节点数字 5 与 4 比较，而后交换两个数字的位置
- 反复执行调整+交换步骤，直到整个序列有序



Python提供了创建和使用堆的方法，所以我们不必自己单独为了实现它们去写代码了:

- heappush(list, item)：向堆中添加一个元素，然后对其重新排序，使其保持堆状态。可用于空列表。
- heappop(list)：删除第一个（最小的）元素并返回该元素。此操作之后，堆仍然是一个堆，因此我们不必调用heapify()。
- heapify(list)：将给定的列表变成一个堆。



Python堆排序的代码实现。


```csharp
from heapq import heappop, heappush

def heap_sort(array):
    heap = []
    for element in array:
        heappush(heap, element)

    ordered = []

    # While we have elements left in the heap
    while heap:
        ordered.append(heappop(heap))

    return ordered

array = [13, 21, 15, 5, 26, 4, 17, 18, 24, 2]
print(heap_sort(array))
```
# 计数排序

计数排序使用一个辅助数组，遍历待排序的数据，待排序数据的值就是辅助数组的索引，辅助数组索引对应的位置保存这个待排序数据出现的次数。最后从辅助数组中取出待排序的数据，放到排序后的数组中。



![](https://img-blog.csdnimg.cn/20200711104651596.gif)


Python计数排序的代码实现。


```csharp
def count_sort(s):
    """计数排序"""
    # 找到最大最小值
    min_num = min(s)
    max_num = max(s)
    # 计数列表
    count_list = [0]*(max_num-min_num+1)
    # 计数
    for i in s:
        count_list[i-min_num] += 1
    s.clear()
    # 填回
    for ind,i in enumerate(count_list):
        while i != 0:
            s.append(ind+min_num)
            i -= 1

if __name__ == '__main__':
    a = [3,6,8,4,2,6,7,3]
    count_sort(a)
    print(a)
```
# 桶排序

桶排序就是把最大值和最小值之间的数进行瓜分，例如分成 10 个区间，10个区间对应10个桶，我们把各元素放到对应区间的桶中去，再对每个桶中的数进行排序，可以采用归并排序，也可以采用快速排序之类的。







下图就是桶排序的过程，来自五分钟学算法。


![在这里插入图片描述](https://img-blog.csdnimg.cn/20200711105628161.gif)



Python桶排序的代码实现。

```csharp
import random
def bucket_sort(arr):
    """桶排序"""
    min_num = min(arr)
    max_num = max(arr)
    # 桶的大小
    bucket_range = (max_num-min_num) / len(arr)
    # 桶数组
    count_list = [ [] for i in range(len(arr) + 1)]
    # 向桶数组填数
    for i in arr:
        count_list[int((i-min_num)//bucket_range)].append(i)
    arr.clear()
    # 回填，这里桶内部排序直接调用了sorted 快速排序
    for i in count_list:
        for j in sorted(i):
            arr.append(j)
            
if __name__ == '__main__':
    arr = [random.randint(0,100) for _ in range(10)]
    print("原始数据：", arr)
    bucket_sort(arr)
    print("桶排序结果：", arr)
            

原始数据： [73, 93, 48, 26, 92, 25, 7, 63, 70, 57]
桶排序结果： [7, 25, 26, 48, 57, 63, 70, 73, 92, 93]
```


# 基数排序

基数排序：通过元素的部分要素，将要排序的元素分配至某些“桶”中，以此达到排序的作用。比如为整数排序，依次用整数的个位、十位...来排序（LSD低位优先）；或者高位到低位依次排序（MSD高位优先）。






下图就是桶排序的过程，来自基数排序。

![](https://img-blog.csdnimg.cn/20200711111015314.gif)


- 首先创建编号 0 ， 1 ，2 ，3 ，4 ，5 ， 6 ，7 ，8 ，9  这 10 个桶

- 遍历整个数列，查看数字的个位数，按照先后顺序存放在对应编号的桶中

- 比如 321 个位数 为 1 ，存放在编号 1 桶中

- 数字 1 个位数 为  1 ，存放在编号  1  桶中，同时存放在 321 上面

- 遍历完整个数列的个位数，将数字存放在桶中后，按照编号顺序取出数字，先放入桶中的数字先取出

- 然后依次遍历整个数列的十位数，按照上述个位数的操作整理数列

- 依次遍历整个数列的百位数，按照上述个位数的操作整理数列

- 这样就完成了 基数排序





Python 基数排序的代码实现。












```csharp
def radix_sort(ls):
    i = 0             # 记录当前正在排哪一位，最低位为1
    max_num = max(ls)  # 最大值
    j = len(str(max_num))  # 记录最大值的位数
    while i < j:
        bucket_list =[[] for q in range(10)] #初始化桶数组
        for x in ls:
            bucket_list[int(x / (10**i)) % 10].append(x) # 找到位置放入桶数组
        ls.clear()
        for x in bucket_list:   # 放回原序列
            for y in x:
                ls.append(y)
        i += 1
    return ls

if __name__ == '__main__':
    list1 = [34, 231, 74, 5, 98, 34, 18, 88, 147, 51, 65, 75, 144, 89]
    sort_list = radix_sort(list1)
    print(sort_list)
    
# 第一次按个位排序放入桶中是：  
[[], [231, 51], [], [], [34, 74, 34, 144], [5, 65, 75], [], [147], [98, 18, 88], [89]]
# 第二次按十位排序：
[[5], [18], [], [231, 34, 34], [144, 147], [51], [65], [74, 75], [88, 89], [98]]
# 第三次按百位排序：
[[5, 18, 34, 34, 51, 65, 74, 75, 88, 89, 98], [144, 147], [231], [], [], [], [], [], [], []]
```

