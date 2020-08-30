@Author：Runsen
@Date：2020/7/3

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十一、Python | Leetcode字符串系列（上篇）。



@[toc]

# 字符串
首先我们先去[Leetcode字符串官网](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9sZWV0Y29kZS1jbi5jb20vZXhwbG9yZS9mZWF0dXJlZC9jYXJkL2FycmF5LWFuZC1zdHJpbmcvMjAwL2ludHJvZHVjdGlvbi10by1zdHJpbmcvNzc3Lw?x-oss-process=image/format,png)，查看字符串相操作。




维基百科：字符串是由零个或多个字符组成的有限序列。一般记为 s = a1a2...an。它是编程语言中表示文本的数据类型。使用 `名称[下标] `来得到一个字符



在某些语言（如 C ++）中，字符串是可变的。 也就是说，你可以像在数组中那样修改字符串。
在其他一些语言（如 Java、Python）中，字符串是不可变的。



# LeetCode 第3题：无重复字符的最长子串

该题目会涉及到一个概念“滑动窗口”。
```java
# 示例 1:
# 输入: "abcabcbb"
# 输出: 3
#解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
# 示例 2:
# 输入: "bbbbb"
#输出: 1
#解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
# 示例 3
# 输入: "pwwkew"
#输出: 3
#解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
#     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
# Related Topics 哈希表 双指针 字符串 Sliding Window
```


下面我们看看，“滑动窗口”如何进行字符串处理。结合题目中的例子“abcabcbb”这个字符串，我们来看看如何找它的无重复最长子串。

首先，我们定义窗口的两端：begin和end，分别表示要找的子串的开头和结尾。
![](https://img-blog.csdnimg.cn/20200703085538169.png)


开始的时候，begin和end都指向0的位置即‘a’，然后end不断后移（窗口变宽），当遇到第二个‘a’时（遇见重复字符）就得到一个子串，其长度就是end和begin位置的差。

如何判断是否遇到了重复字符‘a’呢？需要一个字典作为辅助数据结构，把end从头开始遇到的每个字符及其索引位置都放到字典里面，end每次移动到新字符就查一下字典即可




```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        # 定义两个变量res和start,res用于存储最长子字符串的长度，start存储无重复子串左边的起始位置。
        '''
        然后创建一个哈希表，遍历整个字符串，如果字符串没有在哈希表中出现，说明没有遇到过该字符，则此时计算最长无重复子串，当哈希表中的值小于left，说明left位置更新了，需要重新计算最长无重复子串。每次在哈希表中将当前字符串对应的赋值加1。
        :param s:
        :return:
        '''
        d, res, start = {}, 0, 0
        for i, ch in enumerate(s):
            if ch in d:
                start = max(start, d[ch] + 1)
            res = max(res, i - start + 1)
            d[ch] = i
        print(res)
        return res
```



![](https://img-blog.csdnimg.cn/20200703085314693.png)



下面也是一个做法
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if s == '':
            return 0
        res = 1
        i = 0
        for j in range(1,len(s)):
            if s[j] not in s[i:j]:
                res = max(res,j+1-i)
            else:
                i += s[i:j].index(s[j]) + 1
        return res
```

# LeetCode 第8题：字符串转换整数 (atoi)



```python
#请你来实现一个 atoi 函数，使其能将字符串转换成整数。 
# 首先，该函数会根据需要丢弃无用的开头空格字符，直到寻找到第一个非空格的字符为止。接下来的转化规则如下： 
# 如果第一个非空字符为正或者负号时，则将该符号与之后面尽可能多的连续数字字符组合起来，形成一个有符号整数。 
# 假如第一个非空字符是数字，则直接将其与之后连续的数字字符组合起来，形成一个整数。 
# 该字符串在有效的整数部分之后也可能会存在多余的字符，那么这些字符可以被忽略，它们对函数不应该造成影响。 
# 注意：假如该字符串中的第一个非空格字符不是一个有效整数字符、字符串为空或字符串仅包含空白字符时，则你的函数不需要进行转换，即无法进行有效转换。 
# 在任何情况下，若函数不能进行有效的转换时，请返回 0 。 
# 提示： 
# 本题中的空白字符只包括空格字符 ' ' 。 
# 假设我们的环境只能存储 32 位大小的有符号整数，那么其数值范围为 [−231, 231 − 1]。如果数值超过这个范围，请返回 INT_MAX (231 − 1) 或 INT_MIN (−231) 。 
# 示例 1: 
# 输入: "42"
#输出: 42
# 示例 2: 
#
# 输入: "   -42"
#输出: -42
#解释: 第一个非空白字符为 '-', 它是一个负号。
#     我们尽可能将负号与后面所有连续出现的数字组合起来，最后得到 -42 。
# 示例 3: 
# 输入: "4193 with words"
#输出: 4193
#解释: 转换截止于数字 '3' ，因为它的下一个字符不为数字。
# 示例 4: 
# 输入: "words and 987"
#输出: 0
#解释: 第一个非空字符是 'w', 但它不是数字或正、负号。
#     因此无法执行有效的转换。 
#
# 示例 5: 
# 输入: "-91283472332"
#输出: -2147483648
#解释: 数字 "-91283472332" 超过 32 位有符号整数范围。 
#     因此返回 INT_MIN (−231) 。
# Related Topics 数学 字符串
```
最快的方法就是正则，re.find可以返回包含所有匹配字符串的列表，列表中只有一个字符串用于此问题，因为我们使用^来匹配开头。所以我们可以使用解压缩列表来获取它。[‘abc’] == ‘abc’

```python
class Solution:
    def myAtoi(self, s: str) -> int:
        return max(min(int(*re.findall('^[\+\-]?\d+', s.lstrip())), 2**31 - 1), -2**31)

class Solution:
    def myAtoi(self, str: str) -> int:
        str = str.strip()
        if len(str) == 0: return 0
        strlist = list(str.split(' ')[0])
        for i in range(1,len(strlist)):
            if strlist[i] < '0' or strlist[i] > '9':
                strlist[i] = ' '
                break
        str = ''.join(strlist).split(' ')[0]
        try:
            ret = int(str)
        except:
            return 0

        if ret > 2147483647: return 2147483647
        elif ret < -2147483648: return -2147483648
        else: return ret
```


# LeetCode 第17题：电话号码的字母组合

```java
'''
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。
给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。
示例:
输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
tb = ['abc', 'def', 'ghi', 'jkl', 'mno', 'pqrs', 'tuv', 'wxyz']
'''
```
![](https://img-blog.csdnimg.cn/20200703094427404.png)


```java
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        phone= {
            '2':['a','b','c'],
            '3':['d','e','f'],
            '4':['g','h','i'],
            '5':['j','k','l'],
            '6':['m','n','o'],
            '7':['p','q','r','s'],
            '8':['t','u','v'],
            '9':['w','x','y','z']
        }
        def backtrack(combination,next_digits):
            if len(next_digits) == 0:
                return output.append(combination)
            else:
                for letter in phone[next_digits[0]]:
                    backtrack(combination+letter,next_digits[1:])
                
                
        output = []
        if digits:
            backtrack('',digits)
        return output


class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        conversion={'2':'abc','3':'def','4':'ghi','5':'jkl','6':'mno','7':'pqrs','8':'tuv','9':'wxyz'}
        if len(digits)==0:
            return [] 
        product=['']
        for k in digits:
            product=[i+j for i in product for j in conversion[k]]
        return product
```



# LeetCode 第20题：有效的括号



```java
'''
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。
有效字符串需满足：
    左括号必须用相同类型的右括号闭合。
    左括号必须以正确的顺序闭合。
    注意空字符串可被认为是有效字符串。
输入: "{[]}"
输出: true
'''

def isValid(s):
    """
    :type s: str
    :rtype: bool
    """
    stack = []
    paren_map ={')':'(',']':'[','}':'{'}
    for c in s:
        if c not in paren_map:
            stack.append(c)
        elif not stack or paren_map[c] !=stack.pop():
            return False
    return not stack
s = input('输入括号字符:')
print(isValid(s))
```
也可以利用python种的replace函数将成对的可匹配括号用空字符代替 ，之后依次进行 ，若是有效的括号 ，必然经过有限次循环后 ，字符串为空 ，则最后判断字符串是否为空即可。思路简单 ，实现也很容易 ：

![](https://img-blog.csdnimg.cn/20200703095225329.png)


# LeetCode 第125题：验证回文串

```java
#给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。 
# 说明：本题中，我们将空字符串定义为有效的回文串。 
# 示例 1: 
# 输入: "A man, a plan, a canal: Panama"
#输出: true
# 示例 2: 
# 输入: "race a car"
#输出: false
# Related Topics 双指针 字符串
```


用正则表达式，将除字母、数字以外的字符全部去掉，然后判断是否对称

```java
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = re.sub(r'[^a-z0-9]', '', s.strip().lower())
        return s == s[::-1]

```


让字符串字母都变成小写，然后只保留字母和数字，翻转，比较得到结果



```java
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = ''.join(filter(str.isalnum, s.lower()))
        return s == s[::-1]
```


![](https://img-blog.csdnimg.cn/20200703095729397.png)
