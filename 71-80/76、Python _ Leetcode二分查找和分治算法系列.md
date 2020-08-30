@Author：Runsen
@Date：2020/7/4

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十六、Python | Leetcode二分查找系列。

@[toc]



# 分治算法


分治法是把一个复杂的问题分成两个或更多的相同或相似的子问题，再把子问题分成更小的子问题
直到最后子问题可以简单的直接求解，原问题的解即子问题的解的合并。（百度百科）



利用分治策略求解时，所需时间取决于分解后子问题的个数、子问题的规模大小等因素，而二分法，由于其划分的简单和均匀的特点，是经常采用的一种有效的方法，例如二分法检索。

分治算法的基本思想：是将一个规模为N的问题分解为K个规模较小的子问题，这些子问题相互独立且与原问题性质相同。求出子问题的解，就可得到原问题的解。即一种分目标完成程序算法，简单问题可用二分法完成。

分治法所能解决的问题一般具有以下几个特征：
- 原问题于分解成的小问题具有相同的模式
- 原问题分解成的小问题可以独立求解，子问题之间没有相关性
- 具有分解终止条件，当问题足够小时，可以之间求解
- 分解出的子问题的解可以合并为该问题的解

基本步骤
- 分解，将要解决的问题划分成若干规模较小的同类问题；
- 求解，当子问题划分得足够小时，用较简单的方法解决；
- 合并，按原问题的要求，将子问题的解逐层合并构成原问题的解。

# 分治算法例子

给你一个装有1 6个硬币的袋子。1 6个硬币中有一个是伪造的，并且那个伪造的硬币比真的硬币要轻一些。你的任务是找出这个伪造的硬币。为了帮助你完成这一任务，将提供一台可用来比较两组硬币重量的仪器，利用这台仪器，可以知道两组硬币的重量是否相同。

把1 6硬币的例子看成一个大的问题。第一步，把这一问题分成两个小问题。随机选择8个硬币作为第一组称为A组，剩下的8个硬币作为第二组称为B组。这样，就把1 6个硬币的问题分成两个8硬币的问题来解决。第二步，判断A和B组中是否有伪币。可以利用仪器来比较A组硬币和B组硬币的重量。假如两组硬币重量相等，则可以判断伪币不存在。假如两组硬币重量不相等，则存在伪币，并且可以判断它位于较轻的那一组硬币中。最后，在第三步中，用第二步的结果得出原先1 6个硬币问题的答案。若仅仅判断硬币是否存在，则第三步非常简单。无论A组还是B组中有伪币，都可以推断这1 6个硬币中存在伪币。因此，仅仅通过一次重量的比较，就可以判断伪币是否存在。最终通过四次就可以找到。


# 二分法查找



算法：当数据量很大适宜采用该方法。采用二分法查找时，数据需是“有序”不重复的。二分法查找本质上就是分治算法。

基本思想：假设数据是按升序排序的，对于给定值 x，从序列的中间位置开始比较，如果当前位置值等于 x，则查找成功；若 x 小于当前位置值，则在数列的前半段中查找；若 x 大于当前位置值则在数列的后半段中继续查找，直到找到为止。

二分法查找就是查找一个数组元素的下标。定义两个变量，一个`low`，一个`high`，则`mid=(low+high)/2`。

算法核心中有三种情况：

- 如果`value==arr[mid]`，中间值正好要查找的值，则返回下标，`return mid`;

- .如果value<arr[mid]，要找的值的小于中间的值，则再往数组的小端找，`high=mid-1`;

- .如果value>arr[mid]，要找的值大于中间的值，则再往数组的大端找，`low=mid+1`;


下面代码就是二分查找的Python代码表述。我注释写清楚了。


```cpp
题目：给定n个元素，这些元素是有序的（假定为升序），使用二分法从中查找特定的元素。
要求：输入n个元素，输入某一个特定的值m，首先对n个元素进行排序（排序算法任选），输出m值的位置序号。

def binary_search(list, num):
    left = 0
    right = len(list) - 1  # 注意1 low和high用于跟踪在其中查找的列表部分
    while left <= right:  # 注意2 只有服务还没有缩小到只有一个元素，就不停的检查
        mid = (left + right) // 2
        if list[mid] == num:
            return mid
        elif list[mid] > num:
            right = mid - 1  # 注意3 猜的数字大了
        elif list[mid] < num:
            left = mid + 1   # 注意4 猜的数字小了
    return mid


A = [1, 4, 2, 5, 3, 7, 8]
num = 5
A = sorted(A)  # python 内置排序是快速排序
print(A)
print(binary_search(A, num))
```

在不存在重复元素的有序数组中，查找值等于给定值的元素。最简单的二分查找写起来确实不难，但是，二分查找的变形问题就没那么好写了。

# 二分查找的变形问题


![](https://img-blog.csdnimg.cn/20200704103152347.png)

上图是王争专栏的内容。那么我们就开始干活吧。


## LeetCode 第 704题：标准的二分查找

```cpp
给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。
示例 1:
输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4
示例 2:
输入: nums = [-1,0,3,5,9,12], target = 2
输出: -1
解释: 2 不存在 nums 中因此返回 -1
提示：
你可以假设 nums 中的所有元素是不重复的。
n 将在 [1, 10000]之间。
nums 的每个元素都将在 [-9999, 9999]之间。
```


这个代码不说了，就是一个标准的二分法。

```cpp
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # 确定查找的上下界
        low, high = 0, len(nums) - 1
        while low <= high:  # 当low == high时还剩下最后一个值需要进行检验
            mid = (low + high) // 2
            if nums[mid] < target:
                low = mid + 1  # +1是因为mid已经验证过不符合条件，新的区间又mid+1开始
            elif nums[mid] > target:
                high = mid - 1 # 这里+1同上面原因相同
            else:
                return mid
        return -1  # 执行结束但是没有找到
```



下面找到排序数组中target第一次出现的位置为例，也是二分最常见的变形。查找第一个等于给定值的元素

```cpp
nums= [1,2,2,3,3,3,4,4,5], target=4, return 6
确定返回值类型和查找范围
返回的是target在数组中的位置，即index。
查找范围：[start=0, end=len(nums)-1]

def findFirstIndex(nums, target):
    n = len(nums)
    if (nums is None or n == 0):
        return -1

    start = 0
    end = n - 1

    while (start + 1 < end):
        # 相邻就退出
        mid = start + (end - start) // 2
        if nums[mid] == target:
            end = mid
        elif nums[mid] > target:
            end = mid
        else:
            start = mid

    if nums[start] == target:
        return start

    if nums[end] == target:
        return end

    return -1

print(findFirstIndex(nums=[1, 2, 2, 3, 3, 3, 4, 4, 5], target=4))
6
```





##  LeetCode 第 34题：在排序数组中查找元素的第一个和最后一个位置


查找第一个等于给定值的元素和查找最后一个等于给定值的元素

```cpp
#给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。 
# 你的算法时间复杂度必须是 O(log n) 级别。 
# 如果数组中不存在目标值，返回 [-1, -1]
# 示例 1:
# 输入: nums = [5,7,7,8,8,10], target = 8
#输出: [3,4] 
# 示例 2: 
# 输入: nums = [5,7,7,8,8,10], target = 6
#输出: [-1,-1] 
# Related Topics 数组 二分查找
```


变形一：查找第一个等于给定值的元素
与原题区别在于，当a[mid] == value时，还需要确认是不是第一个值等于给定值的元素。

当遍历到数组第一个数，或者左边值不同时，必定是第一个，直接返回（此处同时做了溢出校验）

当不是第一个元素时，从右到左收缩区间，继续二分查找。




变形二：查找最后一个等于给定值的元素
类比变形一，变形一查找的第一个，此处查找的最后一个元素。即需要确认是不是最后一个值等于给定值的元素。

当遍历到数组最后一位，或者右边元素值不等时，必定是最后一个，返回下标。

如果不是最后一个元素，从左到右收缩区间，继续二分查找。






```cpp
class Solution:
    def searchrightRange(self,nums: List[int],target: int) ->int:
        lefts,rights = 0,len(nums)-1
        while   lefts <= rights:
            mid = (lefts+rights)//2
            if  nums[mid] > target:
                rights = mid-1
            elif    nums[mid] < target:
                lefts = mid+1
            else:
                lefts = mid+1
        if  lefts-1 >= 0 and nums[lefts-1] == target:
            return  lefts-1
        else:
            return  -1 
    def searchleftRange(self,nums: List[int],target: int) ->int:
        lefts,rights = 0,len(nums)-1
        while   lefts <= rights:
            mid = (lefts+rights)//2
            if  nums[mid] > target:
                rights = mid-1
            elif  nums[mid] < target:
                lefts = mid+1
            else:
                rights = mid-1
        if  rights+1 < len(nums) and nums[rights+1] == target:
            return  rights+1
        else:
            return  -1
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        if  len(nums) == 0:
            return  [-1,-1]
        rights = self.searchrightRange(nums,target)
        lefts = self.searchleftRange(nums,target)
        return  [lefts,rights]
```

## 查找排序数组中，第一个大于等于目标值的下标（数组中可能不存在目标值）



```cpp
'''
查找第一个大于等于给定值的元素
* 如序列：3，4，6，7，19 查找第一个大于5的元素，即为6
* 第一个大于给定值，则说明上一个小于给定值，依次判断
'''
def bsearch(a,n):
    low = 0
    high = len(a) -1
    while(low<=high):
        mid = low + ((high-low) >>1)
        if a[mid] >= n:
            if mid == 0 or a[mid - 1] < n:
                return mid
            else:
                high = mid - 1
        else:
            low = mid +1
    return -1
print(bsearch([3,4,6,7,19],5))
2
```


## 查找排序数组中，最后一个小于等于目标值的下标（数组中可能不存在目标值）


```cpp
'''
查找第一个小于给定值的元素
* 如序列：3，4，6，7，19 查找第一个小于5的元素，即为4
* 第一个大于给定值，则说明上一个小于给定值，依次判断
'''
def bsearch(a,n):
    low = 0
    high = len(a) -1
    while(low<=high):
        mid = low + ((high-low) >>1)
        if a[mid] > n:
            high = mid - 1
        else:
            if mid == n-1 or a[mid + 1] > n:
                return mid
            else:
                low = mid +1
    return -1
print(bsearch([3,4,6,7,19],5))

1
```
四个变种到此结束，Runsen原创，耗时两个小时
