@Author：Runsen
@Date：2020/7/3

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十四、Python | Leetcode数字系列（下篇）。

这一部分也是比较简单的，就当作Python编写代码的练习题。


@[toc]

#  LeetCode 第 69题：x 的平方根


```cpp
#实现 int sqrt(int x) 函数。 
# 计算并返回 x 的平方根，其中 x 是非负整数。 
# 由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。 
# 示例 1: 
# 输入: 4
#输出: 2
# 示例 2: 
# 输入: 8
#输出: 2
#说明: 8 的平方根是 2.82842..., 
#     由于返回类型是整数，小数部分将被舍去。
# Related Topics 数学 二分查找
```


这个题目的话，使用二分查找，left是1，high是数字x。就是一个二分查找，不懂二分查找的自己去搜索。每次去计算mid*mid与数字x的大小，如果比x大，那么就令high去等于mid-1;比x小，就令low等于mid+1;等于x,那么直接返回mid;


```python
class Solution:
    def mySqrt(self, x: int) -> int:
        l, r = 0, x
        while l <= r:
            mid = l + (r-l)//2
            if mid * mid <= x < (mid+1)*(mid+1):
                return mid
            elif x < mid * mid:
                r = mid
            else:
                l = mid + 1
```


还有一种方法是牛顿法, 利用一阶线性近似快速寻找最优点.。


$X_{k+1}=\frac{X_k-Y_k}{{f}'(X_k)}=\frac{1}{2}(X_k+\frac{a}{X_k})$

```cpp
class Solution:
    def mySqrt(self, x: int) -> int:
        if x < 2:
            return x
        r0 = x
        r1 = (r0 + x / r0) / 2
        while abs(r0 - r1) >= 1:
            r0 = r1
            r1 = (r1 + x / r1) / 2
        return int(r1)
```
#  LeetCode 第 169题：多数元素






```cpp
#给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。
# 你可以假设数组是非空的，并且给定的数组总是存在多数元素。
# 示例 1: 
# 输入: [3,2,3]
#输出: 3 
# 示例 2: 
# 输入: [2,2,1,1,1,2,2]
#输出: 2
# 
# Related Topics 位运算 数组 分治算法
```
利用集合的计数功能找到出现最多的元素并记录下来



```cpp
import collections
class Solution(object):
    def majorityElement(self, nums):
        k=collections.Counter(nums)
        [(i,j)]=k.most_common(1)
        return i 
        # return sorted(nums)[len(nums)//2]

#哈希表
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        d = {}
        for i in nums:
            d[i] = d.get(i,0) + 1 
            if d[i] >len(nums)/2:
                return i
```


# LeetCode 第 171题：Excel表列序号





```cpp
#给定一个Excel表格中的列名称，返回其相应的列序号。 
# 例如， 
#     A -> 1
#    B -> 2
#    C -> 3
#    ...
#    Z -> 26
#    AA -> 27
#    AB -> 28 
#    ...
# 示例 1: 
# 输入: "A"
#输出: 1
# 示例 2: 
# 输入: "AB"
#输出: 28
# 示例 3: 
# 输入: "ZY"
#输出: 701 
# Related Topics 数学
```

这是26进制转换为10进制问题，有两点：
- 就是进制转换的时候，最高位代表的是26的几次方以及其他的位	
- 谁乘这个26的几次方，这个通过A-B算出该为的数值。

```cpp
class Solution:
    def titleToNumber(self, s: str) -> int:
        dct = {"A": 1, "B": 2, "C": 3, "D": 4, "E": 5, "F": 6, "G": 7, "H": 8, "I": 9, 
               "J": 10, "K": 11, "L": 12, "M": 13, "N": 14, "O": 15, "P": 16, "Q": 17, 
               "R": 18, "S": 19, "T": 20, "U": 21, "V": 22, "W": 23, "X": 24, "Y": 25, "Z": 26}
        return sum([26**i*dct[j] for i, j in enumerate(s[::-1])])
```

将大写字母转成数字（差64），再按位置乘以26的次方（26个字母），累加。（相当于26进制数转十进制）也是一种做法。。

```cpp
class Solution:
    def titleToNumber(self, s: str) -> int:
        # return ord("A")  # A = 65
        return sum( [(ord(s[i])-64) * 26 ** (len(s)-1-i) for i in range(len(s))]) 
```


# LeetCode 第 231题： 2的幂


```cpp
#给定一个整数，编写一个函数来判断它是否是 2 的幂次方。 
# 示例 1: 
# 输入: 1
#输出: true
#解释: 2^0 = 1 
# 示例 2: 
# 输入: 16
#输出: true
#解释: 2^4 = 16 
# 示例 3: 
# 输入: 218
#输出: false 
# Related Topics 位运算 数学
```




若 $n = 2^x$,，且 $x$为自然数（即 n为 2 的幂），则一定满足以下条件：
恒有 `n&(n - 1) == 0`，这是因为：n 二进制最高位为 1，其余所有位为 0；n - 1 二进制最高位为 0，其余所有位为 1；一定满足 n > 0。因此，通过` n > 0 `且 `n & (n - 1) == 0 `即可判定是否满足$n = 2^x$
 


2^x	|n|n - 1	|n & (n - 1)
--|--|--|--
$2^0$|0001|0000	|(0001) & (0000) == 0
$2^1$|0010|0001	|(0010) & (0001) == 0
$2^2$|0100|0011	|(0100) & (0011) == 0
$2^3$|1000|0111	|(1000) & (0111) == 0


```cpp
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        return n > 0 and n & (n - 1) == 0
```


# LeetCode 第 279题： 完全平方数





```cpp
#给定正整数 n，找到若干个完全平方数（比如 1, 4, 9, 16, ...）使得它们的和等于 n。你需要让组成和的完全平方数的个数最少。 
# 示例 1: 
# 输入: n = 12
#输出: 3 
#解释: 12 = 4 + 4 + 4. 
# 示例 2: 
# 输入: n = 13
#输出: 2
#解释: 13 = 4 + 9. 
# Related Topics 广度优先搜索 数学 动态规划
```


下面是动态规划的做法：


动态规划：因为要求完全平方数个数最少，设i的最少完全平方数为dp[i]，用j表示完全平方数。那么dp[i]=dp[i-j]+1，因此可以使用动态规划。
问题的关键是n是由哪几个完全平方数组成最小，比如12：可以是dp[8]+dp[4]，也可以是dp[3]+dp[9],用square构建完全平方数列表，用j在里面循环输出dp[i]最小值。
代码




状态DP：dp[i]:组成和为i的完全平方数的最少个数。
状态转移：dp[i] = min(dp[i],dp[i-j*j]+1)
初始化：最坏的结果是:i=1+1+...+1,故初始化为：[i for i in range(n+1)]

动态规划代码简洁， 但时间长

```cpp
def numSquares(self, n: int) -> int:
     #动态规划
     dp = [i for i in range(n+1)]
     
     for i in range(2,n+1):
         for j in range(int(i**0.5)+1):
             dp[i] = min(dp[i], dp[i-j*j]+1)
     return dp[n]]
```


还有一种方法是广度优先搜索，就是BFS 算法。这个算法在以后再说。





