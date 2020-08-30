
@Author：Runsen
@Date：2020/6/19

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就见识下刷Leetcode的快乐。


![](https://img-blog.csdnimg.cn/20200610160923281.png)



@[toc]

Runsen先打开Pycharm，开始继续嗨起来



# 剑指 Offer 系列 面试题11 - 旋转数组的最小数字

先来一个简单的，见面礼。题目来源于 LeetCode 上的面试题11：旋转数组的最小数字


题目链接：https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/



```python
#把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。 
# 示例 1： 
# 输入：[3,4,5,1,2]
#输出：1
# 示例 2： 
# 输入：[2,2,2,0,1]
#输出：0
# 注意：本题与主站 154 题相同：https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array-ii/ 
# Related Topics 二分查找
```


初看题目最直观的解法并不难，直接寻找，我们不难写出如下代码。

```python
class Solution:
    def minArray(self, numbers: List[int]) -> int:
        return min(numbers)
```


时间复杂度$O(n)$,空间复杂度$O(1)$。因此这样是不行的
![](https://img-blog.csdnimg.cn/20200613121328523.png)

考的是：二分查找。二分法的分析我们知道，数组可以分为前后两个递增数组
- 当`numbers[mid] > numbers[high]`时，说明最小值在mid的右边，缩小范围`low = mid + 1`
- 当`numbers[mid] == numbers[high]`时，我们不知道最小值的范围，但是可以肯定的是去除`numbers[high]`是没有影响的,缩小范围`high -= 1`
- 当`numbers[mid] < numbers[high]`时，我们知道最小值的不是`numbers[mid]]`就是在mid的左边，缩小范围high = mid



```python
class Solution:
    def minArray(self, numbers: List[int]) -> int:
        l, r = 0, len(numbers) - 1
        while l < r:
            mid = (l + r) // 2
            if numbers[mid] > numbers[r]:
                l = mid + 1
            elif numbers[mid] < numbers[r]:
                r = mid
            else:
                r -= 1
        return numbers[l]


```
![](https://img-blog.csdnimg.cn/20200613122819300.png)



# 面试题53 - II. 0～n-1中缺失的数字


```java
#一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。 
# 示例 1: 
# 输入: [0,1,3]
#输出: 2
# 示例 2: 
# 输入: [0,1,2,3,4,5,6,7,9]
#输出: 8 
# 限制： 
# 1 <= 数组长度 <= 10000 
# Related Topics 数组 二分查找
```

对于有序数组或者多部分有序数组的查找问题99.999999%都是用二分查找，这道题其实考察的是二分查找的两个常见拓展之一，即查找目标序列的左边界，另一个常见拓展是查找目标序列的右边界。

```java
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        i, j = 0, len(nums) - 1
        while i <= j:
            m = (i + j) // 2
            if nums[m] == m: 
            	i = m + 1
            else: 
            	j = m - 1
        return i
```


![](https://img-blog.csdnimg.cn/2020061912141170.png)






# LeetCode 第 66题：加一

 

```java
#给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。 
# 最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。 
# 你可以假设除了整数 0 之外，这个整数不会以零开头。 
# 示例 1: 
# 输入: [1,2,3]
#输出: [1,2,4]
#解释: 输入数组表示数字 123。

# 示例 2: 
# 输入: [4,3,2,1]
#输出: [4,3,2,2]
#解释: 输入数组表示数字 4321。
```




一次for循环解决问题，从数组尾部遍历，如果遇到数字不是9就+1，并返回。如果是9，则将当前数字置0，并进入下一轮循环

考虑特殊情况：9999，此时需要检查最后一次for循环的数字是不是0，即digits[0]是否为0，如果是0，则遇到了特殊情况。此时需要在数组最前面加一个数字1，然后返回即可


```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        for i in range(len(digits)-1, -1, -1):
            if digits[i] < 9:
                digits[i] += 1
                return digits
            digits[i] = 0
        return [1] + digits
```

先将数字列表数组转化为数字或者字符串，然后+1，最后将数字转化为数组，并返回

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        ##先变成一个整的数字，然后做加法，然后转换成str,再转int加到新的list中
        nums_str = ""
        for i in digits:
            nums_str =nums_str+str(i)
    
        nums_int = int(nums_str)+1
        res = []
        for i in str(nums_int):
            res.append(int(i))
        return res

		 # a = [i * 10 ** index for index, i in enumerate(digits[::-1])]
		 # num = sum(a) + 1
		 # print(num)
		 # return [int(x) for x in str(num)]

```

# 面试题53 - I. 在排序数组中查找数字的次数 I

```java
#统计一个数字在排序数组中出现的次数。 
# 示例 1: 
# 输入: nums = [5,7,7,8,8,10], target = 8
#输出: 2 
# 示例 2: 
# 输入: nums = [5,7,7,8,8,10], target = 6
#输出: 0 
# 限制： 
# 0 <= 数组长度 <= 50000 
# 注意：本题与主站 34 题相同（仅返回值不同）：https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/ 
# Related Topics 数组 二分查找
```






python：首先为了达到目的，我们看使用python最容易实现的操作

```java
 if len(nums) ==0:
    return 0
 else:
    return nums.count(target)
```


![](https://img-blog.csdnimg.cn/20200619122355415.png)
更好的(根据二分法思想)实现下所示：


```java
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # 双指针
        l = 0
        r = len(nums) - 1
        while l <= r:
            if nums[l] < target:
                l += 1
            elif nums[r] > target:
                r -= 1
            elif nums[l] == nums[r] == target:
                return r - l + 1
        return 0


```



![](https://img-blog.csdnimg.cn/20200619121957229.png)




# leetcode977：有序数组的平方

```java
#给定一个按非递减顺序排序的整数数组 A，返回每个数字的平方组成的新数组，要求也按非递减顺序排序。 
# 示例 1： 
# 输入：[-4,-1,0,3,10]
#输出：[0,1,9,16,100]
# 示例 2： 
# 输入：[-7,-3,2,3,11]
#输出：[4,9,9,49,121]
# 提示： 
# 1 <= A.length <= 10000 
# -10000 <= A[i] <= 10000 
# A 已按非递减顺序排序。 
# Related Topics 数组 双指针
```




利用python中的列表生成式生成求平方后的数组，利用python中的排序函数sorted()对求平方后的数组进行排序。

```java
return sorted([k**2 for k in A])

```

时间复杂度：利用列表生成式生成求平方后的数组，时间复杂度为$O(N)$,python中排序用的是蒂姆排序算法，时间复杂度为$O(NlogN)$，所以该算法的时间复杂为$O(NlogN)$。



空间复杂度：$O(N)$。利用列表生成式生成求平方后数组的时间复杂度为$O(N)$，蒂姆排序空间复杂度为$O(N)$,所以该算法空间复杂度为$O(N)$。



下面就是常见的双指针做法

```java
class Solution:
    def sortedSquares(self, A: List[it]) -> List[int]:
        left,right,result = 0, len(A) - 1,[]
        while left <= right:
            if abs(A[left]) > abs(A[right]):
                result.insert(0, pow(A[left],2))
                left += 1
            else:
                result.insert(0, pow(A[right],2))
                right -= 1
        return result
```

