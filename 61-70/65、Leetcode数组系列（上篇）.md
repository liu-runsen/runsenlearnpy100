
@Author：Runsen

@Date：2020/6/5

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

从大一写Python文章，到现在其都有上百篇，现在到了六十五，今日主要写的是数据结构中的数组 Array 


@[TOC]




# 数组 Array 


在平时使用最多的恐怕就是数组了吧，它是使用最广泛的一种数据结构，它是相同数据类型（可以是基本类型也可以是自定义类型）的元素按一定顺序排列的集合，它们在内存中按照这个先后顺序连续存放在一起。有一维数组，二维数组，多维数组。 通俗的理解就是我们一般把一群羊或者一群牛放在一个圈里面，这个圈就相当于数组容器，每一个羊相当于一个元素。


![](https://img-blog.csdnimg.cn/20190315151507193.jpg)
- 查询 Access: O(1) 
- 插入 Insert: 平均 O(n)
- 删除 Delete: 平均 O(n)




优点：
1. 有序 
2. 可以进行下标操作，随机访问效率很高，时间复杂度可以达到O(1)
3. 添加速度快
缺点： 
1. 删除，删除第一个，删除最后一个，选择一个位置删除这些都不方便操作 
2. 在数组起始位置处，插入数据和删除数据效率低，时间复杂度平均 O(n)
3. 内存空间要求高，必须有足够的连续的内存空间 



# 题目

这是争哥的春节天天练，那时我太菜了。 没搞。
![](https://img-blog.csdnimg.cn/20200605164322651.png)




#  三数之和
leetcode 三数之和，这是Leecode的第十五道题目。

https://leetcode-cn.com/problems/3sum/Majority 

```python
#给你一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有满足条件且不重复的三元组。 
#
# 注意：答案中不可以包含重复的三元组。 

# 示例： 
#
# 给定数组 nums = [-1, 0, 1, 2, -1, -4]，
#
#满足要求的三元组集合为：
#[
#  [-1, 0, 1],
#  [-1, -1, 2]
#]
注意：答案中不可以包含重复的三元组。
```


三数之和就当两数来干，两次遍历，判断第三个数在不在，就是时间复杂度$O(n^2)$。

```python
def threeSum(nums):
    result = []
    nums.sort()
    a = len(nums)
    for i in range(a - 1):
        for j in range(i + 1, a):
            if -(nums[i] + nums[j]) in nums[j + 1:]:
                array = [nums[i], nums[j], -(nums[i] + nums[j])]
                if array not in result:
                    result.append(array)
    return result
nums = [-1, 0, 1, 2, -1, -4]
print(threeSum([-1, 0, 1, 2, -1, -4]))
```

但是会超出时间，其实三数之和用的不是这样子的，做法是双指针。

![](https://img-blog.csdnimg.cn/20200605170142310.png)



我们可以先把这个数组进行从小到大的排序，因为排序的复杂度$O(NlogN) $是远远小于$n^2$的，排序后，你会发现，由于三数之和是等于零，那么如果当前这个元素是大于零的话，而且，这个数组是按照从小到大排序的话，那么当前这个元素作为起点的集合是为空的，因为后面的元素都是比这个元素大的元素，是不可相加等于零。

由此我们可以节省一些复杂度，当然，我们进行排序的时候，是要经历一些复杂度的，但这远远小于n的平方，所以我们这个做法还是比较快的。

然后我们在确定起点之后，通过双指针去遍历其他两个元素。

看不懂看下面的图片
![在这里插入图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9waWMubGVldGNvZGUtY24uY29tL2UzZmE1OWNiZjNhYzEyMDBhMjZhNDM1ZDAwZTg3MmY3OGVjOTQwYWZkNGVlMTk3N2IwNGMxZjRkY2E0NWMxNGUtMi5naWY)


```python
def threeSum(nums):
    nums.sort()
    # [-4, -1, -1, 0, 1, 2]
    res_list = []
    # 头部循环查找
    for i in range(len(nums)):
        if i == 0 or nums[i] > nums[i - 1]:
            # 最左端
            l = i + 1
            # 最右端
            r = len(nums) - 1
            while l < r:  # 正在查找
                three_sum = nums[i] + nums[l] + nums[r]
                if three_sum == 0:
                    res_list.append([nums[i], nums[l], nums[r]])
                    l += 1  # 右移一位
                    r -= 1  # 左移一位
                    while l < r and nums[l] == nums[l - 1]:
                        # 从左往右，相同数值直接跳过
                        l += 1
                    while r > l and nums[r] == nums[r + 1]:
                        # 从右往左，相同数值直接跳过
                        r -= 1
                elif three_sum > 0:
                    # 大于零，右边数值大，左移
                    r -= 1
                else:
                    # 小于零，左边数值小，右移
                    l += 1
    return res_list
```



![](https://img-blog.csdnimg.cn/20200605171410159.png)


# 求众数

题目来源于 LeetCode 上第 169 号问题：求众数（求数组中超过一半的数字）。题目难度为 Easy

```python
#给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。 
#
# 你可以假设数组是非空的，并且给定的数组总是存在多数元素。 
# 示例 1: 
#
# 输入: [3,2,3]
#输出: 3 
#
# 示例 2: 
#
# 输入: [2,2,1,1,1,2,2]
#输出: 2
# 
# Related Topics 位运算 数组 分治算法
```


方法：遍历整个数组，出现次数比其他数字加起来出现次数还多的元素返回。


最简单的方法就排序，取出 ⌊ n/2 ⌋ 的元素

```python
def majorityElement(self, nums):
    nums.sort()
    return nums[int(len(nums) / 2)]
```





![](https://img-blog.csdnimg.cn/20200605172827746.png)




然后一种计数的方法，用字典来储存起来。



```python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        num = {}
        for i in nums:
            if i in num:
                num[i] += 1
            else:
                num[i] = 1
        return max(num.items(),key = lambda x:x[1])[0]
```




![](https://img-blog.csdnimg.cn/20200605174037717.png)

还可以直接使用collections
```python
import collections

def majorityElement(self, nums):
     return  collections.Counter(nums).most_common()[0][0]
```


![](https://img-blog.csdnimg.cn/20200605174535675.png)





# 求缺失的第一个正数
题目来源于 LeetCode 上第 41 号问题：求缺失的第一个正数



中文版：https://leetcode-cn.com/problems/first-missing-positive/


```python
#给你一个未排序的整数数组，请你找出其中没有出现的最小的正整数。 
# 示例 1: 
#
# 输入: [1,2,0]
#输出: 3
#
# 示例 2: 
#
# 输入: [3,4,-1,1]
#输出: 2
# 
# 示例 3: 
#
# 输入: [7,8,9,11,12]
#输出: 1
# 提示： 
#
# 你的算法的时间复杂度应为O(n)，并且只能使用常数级别的额外空间。 
# Related Topics 数组

```


这道题的难度在于时间和空间的限制。

若没有时间的限制，可以直接排序后遍历查找。

若没有空间的限制，可以创建辅助空间后记录。

最简单的做法就是出现就+1。

题目的要求是找到没有出现过的最小正整数，最小的正整数是1，如果1没出现过，那么答案就是1，否则，自增1，继续看2是否在列表中。

```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        res = 1
        while res in nums:
            res += 1
        return res

```

![](https://img-blog.csdnimg.cn/20200605181200362.png)



把数组里 所有>=1的元素 放在它该放的位置！
哪里是该放的位置? ：放在值减一的位置
例如，数组［4 1 5 -1 2］。
4应该放在下标为3(4-1)的位置，交换后
［-1 1 5 4 2］
1应该放在下标为0(1-0)的位置，交换后
［1 -1 5 4 2］
以此类推
［1 -1 2 4 5］
［1 2 -1 4 5］
最后遍历，第三个位置(下标为2) 本来应放3，但此时是-1，所以返回3，答案就是3。

```python
 class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        n=len(nums)
        res_list=[-1] * n
        # print(res_list)
        for i in range(n):
        	#  要判断这个数是否可以被交换
            if nums[i] >=1 and nums[i]<=n:
                res_list[nums[i]-1] =nums[i]
        # print(res_list)
        for i in range(n):
            if res_list[i] != i+1:
                return i+1
        return n+1
```


![](https://img-blog.csdnimg.cn/20200605183017232.png)
