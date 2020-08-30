@Author：Runsen
@Date：2020/6/8

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就见识下刷Leetcode的快乐。


![](https://img-blog.csdnimg.cn/20200610160923281.png)



@[toc]

Runsen先打开Pycharm，





# 剑指 Offer 系列 面试题03.：数组中重复的数字

先来一个简单的，见面礼。题目来源于 LeetCode 上的剑指 Offer 系列 面试题03. 数组中重复的数字。

题目链接：https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/



```go
#找出数组中重复的数字。 
#在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。 
#
# 示例 1： 
#
# 输入：
#[2, 3, 1, 0, 2, 5, 3]
#输出：2 或 3 
#
# 限制： 
# 2 <= n <= 100000 
# Related Topics 数组 哈希表

```


先进行数据的排序，然后看相邻元素是否有相同的，有直接return。 不过很慢，时间O(nlogn)了，空间O(1)，但是代码很简单。

```python
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/6/10
'''
def findRepeatNumber(nums):
    nums.sort()
    for i in range(len(nums) -1):
        if nums[i]  ==  nums[i+1]:
            return nums[i]
nums = [2, 3, 1, 0, 2, 5, 3]
print(findRepeatNumber(nums))
2
```

如果用哈希表，就是字典，遍历整个数组,当这个数字没有出现过字典的时候将其加入进去,如果在哈希表中则直接返回即可。时间复杂度O(n)，空间复杂度O(n)



```python
def findRepeatNumber1(nums):
    dict = {}
    for i in nums:
        if i not  in dict:
            dict[i] = 0
        else:
            return i
nums = [2, 3, 1, 0, 2, 5, 3]
print(findRepeatNumber1(nums))
2
```


![](https://img-blog.csdnimg.cn/20200610163602581.png)



# LeetCode 第 5 题：最长回文子串

题目链接：https://leetcode-cn.com/problems/longest-palindromic-substring/




```python
#给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。 
#
# 示例 1： 
#
# 输入: "babad"
#输出: "bab"
#注意: "aba" 也是一个有效答案。
# 示例 2： 
#
# 输入: "cbbd"
#输出: "bb"

```

定义一个判读回文子串的方法
遍历字符串比较回文子串的长度

比如说字符串abacd，反过来是dcaba，它俩的最长公共子串是aba，也就是最长回文子串。

但是这个思路是错误的，比如说字符串aacxycaa，反转之后是aacyxcaa，最长公共子串是aac，但是最长回文子串应该是aa。


算法一：枚举s所有子串，满足回文的同时，满足最长
结果：$O（N^3）$，同学请你出门右转

算法二：遍历s的每个字符，（奇数）以该字符为中心，向左向右同时遍历，（偶数）以两个字符为中心，向左向右同时遍历，当不满足回文时停止，最终筛选最长回文串
结果：$O（N^2）$，嗯，还可以，那你完整写出来吧

算法三：Manacher算法，为最长回文子串而生，O（N），了解一下就放弃。

回文中心的两侧互为镜像。因此，回文可以从他的中心展开，并且只有2n-1个这样的中心(一个元素为中心的情况有n个，两个元素为中心的情况有n-1个)。

```python
# 回文的长度是奇数还是偶数的情况，如果是奇数形回文，就以当前字符为中心左右两边寻找，例如回文"bab"；如果是偶数形回文，需要两个字符，并且这两个字符是相等的，则需要以当前字符和其相邻的字符为中心向左右两边寻找，例如回文"abba"。
def longestPalindrome(s):
    res = ""
    for i in range(len(s)):
        # 奇数形回文, like "aba"
        tmp = helper(s, i, i)
        if len(tmp) > len(res):
            res = tmp
        # 偶数形回文, like "abba"
        tmp = helper(s, i, i + 1)
        if len(tmp) > len(res):
            res = tmp
    return res

def helper(s, l, r):
    # 中心扩散
    while l >= 0 and r < len(s) and s[l] == s[r]:
        l -= 1
        r += 1
    return s[l + 1:r]


if __name__ == '__main__':
    longestPalindrome('abasfggttg')
```

![](https://img-blog.csdnimg.cn/20200610172358702.png)


#  LeetCode 第 53 题：最大子序和

```python
#给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。 
#
# 示例: 
#
# 输入: [-2,1,-3,4,-1,2,1,-5,4],
#输出: 6
#解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```


定义当前子序和以及最大子序和为数组的一个元素；

遍历整数数组，比较当前子序和的值及当前遍历的值，取较大值重置赋值给当前子序和 cur_sum；

同时比较当前子序和及最大子序和的值，取较大值重置赋值给最大子序和 max_sum；

遍历结束，返回最大子序和的值 max_sum。



```python
def maxSubArray( nums):
    '''查找连续子数组的最大和
    '''
    # 比较当前子序和，最大子序和，返回最大值
    # 定义当前子序和以及最大子序和为第一个元素
    cur_sum = max_sum = nums[0]
    # 遍历整数数组
    for x in range(1, len(nums)):
        # 比较当前值和当前子序和的值，取较大值
        cur_sum = max(nums[x], cur_sum + nums[x])
        # 比较当前值和定义的最大子序和值，将最大值重置赋值给 max_sum
        max_sum = max(cur_sum, max_sum)
    return max_sum
print(maxSubArray([-2,1,-3,4,-1,2,1,-5,4]))
6
```




#  LeetCode 第88题 :合并两个有序数组


```python
#给你两个有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。 
# 初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。 
# 你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。 
# 输入:
#nums1 = [1,2,3,0,0,0], m = 3
#nums2 = [2,5,6],       n = 3
#
#输出: [1,2,2,3,5,6] 




```


合并两个列表再排序，简单。

```python
def merge(nums1, nums2):
    nums1[:] =  sorted(nums1[:m] + nums2[:n])
```


![](https://img-blog.csdnimg.cn/20200610175523332.png)


因为本身就是有序，通过 双指针法 达到$O(n + m)$的时间复杂度。


最直接的算法实现是将指针p1 置为 nums1的开头， p2为 nums2的开头，在每一步将最小值放入输出数组中。



由于 nums1 是用于输出的数组，需要将nums1中的前m个元素放在其他地方，也就需要 $O(m)$的空间复杂度。



```python
def merge(nums1,m, nums2,n):
    # Make a copy of nums1.
    nums1_copy = nums1[:m]
    nums1[:] = []

    # Two get pointers for nums1_copy and nums2.
    p1 = 0
    p2 = 0

    # Compare elements from nums1_copy and nums2
    # and add the smallest one into nums1.
    while p1 < m and p2 < n:
        if nums1_copy[p1] < nums2[p2]:
            nums1.append(nums1_copy[p1])
            p1 += 1
        else:
            nums1.append(nums2[p2])
            p2 += 1

    # if there are still elements to add
    if p1 < m:
        nums1[p1 + p2:] = nums1_copy[p1:]
    if p2 < n:
        nums1[p1 + p2:] = nums2[p2:]
    return nums1

nums1 = [1,2,3,0,0,0]
nums2 = [2,5,6]
print(merge(nums1,3,nums2,3))
[1, 2, 2, 3, 5, 6]

```









#  LeetCode 第118题 :杨辉三角



```python
#给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。 
# 在杨辉三角中，每个数是它左上方和右上方的数的和。 
#
# 示例: 
#
# 输入: 5
#输出:
#[
#     [1],
#    [1,1],
#   [1,2,1],
#  [1,3,3,1],
# [1,4,6,4,1]
#] 
# Related Topics 数组
```

第一行第二行都是1，每行第一个和最后一个都为1，假设任意一个位置的数x，索引坐标是(m,n)，则x就是该数 正上方的数 和 左上方那个数 之和。即(m-1,n),(m-1,n-1)两数和。




```python
def generate(numRows):
    if numRows == 0: return []
    triangle = [[1]]
    if numRows == 1: return triangle
    for i in range(1, numRows):
        tmp = [1]
        for j in range(1, i):
            tmp.append(triangle[i - 1][j - 1] + triangle[i - 1][j])
        tmp.append(1)
        triangle.append(tmp)
    return triangle
print(generate(5))
[[1], [1, 1], [1, 2, 1], [1, 3, 3, 1], [1, 4, 6, 4, 1]]

```



![](https://img-blog.csdnimg.cn/20200610182259721.png)


如果本文对你有帮助，大家可以点赞转发一波，有错误大家可以评论指出，感谢！



