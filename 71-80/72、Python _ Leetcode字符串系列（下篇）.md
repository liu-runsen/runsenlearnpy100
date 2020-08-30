@Author：Runsen
@Date：2020/7/3

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十二、Python | Leetcode字符串系列（下篇）。



@[toc]

# LeetCode 第14题：最长公共前缀



```java
#编写一个函数来查找字符串数组中的最长公共前缀。 
# 如果不存在公共前缀，返回空字符串 ""。 
# 示例 1: 
# 输入: ["flower","flow","flight"]
#输出: "fl"
# 示例 2: 
# 输入: ["dog","racecar","car"]
#输出: ""
#解释: 输入不存在公共前缀。
# 说明: 
# 所有输入只包含小写字母 a-z 。 
# Related Topics 字符串
```






解题思路：使用 zip 根据字符串下标合并成数组，判断合并后数组里元素是否都相同




```java
class Solution(object):
    def longestCommonPrefix(self, strs):
        ans = ''
        for i in zip(*strs):
            if len(set(i)) == 1:
                ans += i[0]
            else:
                break
        return ans
```







# LeetCode 第28题：实现 strStr()


```java
#实现 strStr() 函数。 
# 给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回 -1。 
# 示例 1: 
# 输入: haystack = "hello", needle = "ll"
#输出: 2
# 示例 2: 
# 输入: haystack = "aaaaa", needle = "bba"
#输出: -1
# 说明: 
# 当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。 
# 对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及 Java的 indexOf() 定义相符。 
# Related Topics 双指针 字符串
```

通过index进行needle数据查询，当不存在是index会报错，直接将其输出-1即可



```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if needle in haystack:         
            num = haystack.index(needle)
        else:
            return -1
        return num
```



# LeetCode 第67题： 二进制求和



```java
#给你两个二进制字符串，返回它们的和（用二进制表示）。 
# 输入为 非空 字符串且只包含数字 1 和 0。 
# 示例 1: 
# 输入: a = "11", b = "1"
#输出: "100" 
# 示例 2: 
# 输入: a = "1010", b = "1011"
#输出: "10101" 
# 提示： 
# 每个字符串仅由字符 '0' 或 '1' 组成。 
# 1 <= a.length, b.length <= 10^4 
# 字符串如果不是 "0" ，就都不含前导零。 
# Related Topics 数学 字符串
```
用python在十进制与二进制之间进行转换，求和转化返回。



```java
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        atmp = eval('0b' + a) #a对应的10进制数
        btmp = eval('0b' + b) #b对应的10进制数
        sumtmp = atmp + btmp #a+b对应的10进制数
        res = bin(sumtmp)  #10进制数转化为二进制数字符串
        return res[2:]   #返回结果字符串
```





位运算模拟二进制加法运算。异或运算的特点是a和b不一样才为1，与运算的特点是a和b同为1时才为1，否则为0，刚好可以逐步记录进位。

![](https://img-blog.csdnimg.cn/20200703101705855.png)


```java
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        atmp = eval('0b' + a)
        btmp = eval('0b' + b)
        while btmp:
            ans = (atmp ^ btmp)
            btmp = (atmp & btmp) << 1
            atmp = ans
        return bin(atmp)[2:]
```
# LeetCode 第344题： 反转字符串

```java
#编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 char[] 的形式给出。 
# 不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用 O(1) 的额外空间解决这一问题。 
# 你可以假设数组中的所有字符都是 ASCII 码表中的可打印字符。 
# 示例 1： 
# 输入：["h","e","l","l","o"]
#输出：["o","l","l","e","h"]
# 示例 2： 
# 输入：["H","a","n","n","a","h"]
#输出：["h","a","n","n","a","H"] 
# Related Topics 双指针 字符串
```
双指针思想，左右交换



```java
 class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        i,j=0,len(s)-1
        while i<=j:
            s[i],s[j]=s[j],s[i]
            i+=1
            j-=1


class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        s.reverse()

```


# LeetCode 第557题：  反转字符串中的单词 III

```java
#给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。 
# 示例 1: 
#输入: "Let's take LeetCode contest"
#输出: "s'teL ekat edoCteeL tsetnoc" 
# 注意：在字符串中，每个单词由单个空格分隔，并且字符串中不会有任何额外的空格。 
# Related Topics 字符串
```


将字符串分割成单词列表 然后把每个单词反转切片

```java
class Solution(object):
    def reverseWords(self, s):
        return " ".join(word[::-1] for word in s.split(" "))
```



先反转单词列表 再反转字符串

以字符串` “I love drag queen” `为例：

`s.split(" ") `将字符串分割成单词列表:


`['I', 'love', 'drag', 'queen']`


`s.split(" ")[::-1] `将单词列表反转:


`['queen', 'drag', 'love', 'I']`

`" ".join(s.split(" ")[::-1]) `将单词列表转换为字符串，以空格分隔:


`"queen drag love I"`


`" ".join(s.split(" ")[::-1])[::-1] `将字符串反转：


`”I evol gard neeuq“`

```java
class Solution(object):
    def reverseWords(self, s):
        return " ".join(s.split(" ")[::-1])[::-1]
```

