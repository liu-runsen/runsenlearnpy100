@Author：Runsen
@Date：2020/7/3

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十三、Python | Leetcode数字系列（上篇）。

这一部分是比较简单的，就当作Python编写代码的练习题

@[toc]
# LeetCode 第9题： 回文数

```java
#判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。 
# 示例 1: 
# 输入: 121
#输出: true
# 示例 2: 
# 输入: -121
#输出: false
#解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
# 示例 3: 
# 输入: 10
#输出: false
#解释: 从右向左读, 为 01 。因此它不是一个回文数。
# 进阶: 
# 你能不将整数转为字符串来解决这个问题吗？ 
# Related Topics 数学
```


最好理解的一种解法就是先将 整数转为字符串 ，然后将只需要循环每个字符进行判断对应元素是否相等即可。可以的话，还可以`return str(x) == str(x)[::-1]`简单粗暴。
`


```java
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if not x:
            return True
        str_x = str(x)
        n = len(str_x)
        for i in range(n-1):
            if str_x[i] != str_x[n-1-i]:
                return False
        return True
```


不将整数转为字符串，那么算出对应的回文数在比较欧克。
```java
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0: # 如果为负数，直接返回 false
            return False
        num = x
        cur = 0
        while num !=0:
            cur = cur*10 + num%10
            num //=10
        return cur == x # 最后比较 数值反转前后是否相等
```


# LeetCode 第12题：整数转罗马数字


```java
#罗马数字包含以下七种字符： I， V， X， L，C，D 和 M。 
# 字符          数值
#I             1
#V             5
#X             10
#L             50
#C             100
#D             500
#M             1000 
# 例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做 XXVII, 即为 XX + V + II 。 
# 通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况： 
# I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。 
# X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
# C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。 
# 给定一个整数，将其转为罗马数字。输入确保在 1 到 3999 的范围内。 
# 示例 1: 
# 输入: 3
#输出: "III" 
# 示例 2: 
# 输入: 4
#输出: "IV" 
# 示例 3: 
# 输入: 9
#输出: "IX"
# 示例 4: 
# 输入: 58
#输出: "LVIII"
#解释: L = 50, V = 5, III = 3.
# 示例 5: 
# 输入: 1994
#输出: "MCMXCIV"
#解释: M = 1000, CM = 900, XC = 90, IV = 4. 
# Related Topics 数学 字符串
```

使用哈希表解决.哈希表键为整数，值为罗马数字，且键从大到小排列；遍历整个哈希表，判断当前数值是否大于等于此刻的键：若能，则s加上整除的个数乘以值；若不能，则遍历下一个。






```java
class Solution:
    def intToRoman(self, num: int) -> str:
        d = {1000: 'M', 900: 'CM', 500: 'D', 400: 'CD', 100: 'C', 90: 'XC', 50: 'L', 40: 'XL', 10: 'X', 9: 'IX', 5: 'V', 4: 'IV', 1: 'I'}
        res = ''
        for k in d:
            while num >= k:
                res += d[k]
                num -= k
        return res
```



# LeetCode 第13题：整数转罗马数字


```java
#罗马数字包含以下七种字符: I， V， X， L，C，D 和 M。 
# 字符          数值
#I             1
#V             5
#X             10
#L             50
#C             100
#D             500
#M             1000 
# 例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做 XXVII, 即为 XX + V + II 。 
# 通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况： 
# I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。 
# X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
# C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。 
# 给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。 
# 示例 1: 
# 输入: "III"
#输出: 3 
# 示例 2: 
# 输入: "IV"
#输出: 4 
# 示例 3: 
# 输入: "IX"
#输出: 9 
# 示例 4: 
# 输入: "LVIII"
#输出: 58
#解释: L = 50, V= 5, III = 3.
# 示例 5: 
# 输入: "MCMXCIV"
#输出: 1994
#解释: M = 1000, CM = 900, XC = 90, IV = 4. 
# Related Topics 数学 字符串
```


思路：
- 创建hashMap字典表映射罗马数字和整数。
- .如果当前字符代表的值不小于其右边，就加上该值；否则就减去该值。

```java
class Solution:
    def romanToInt(self, s: str) -> int:
        a = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        ans=0
        for i in range(len(s)):
            if i<len(s)-1 and a[s[i]]<a[s[i+1]]:
                ans-=a[s[i]]
            else:
                ans+=a[s[i]]
        return ans
```

# LeetCode 第29题： 两数相除

```java
#给定两个整数，被除数 dividend 和除数 divisor。将两数相除，要求不使用乘法、除法和 mod 运算符。 
# 返回被除数 dividend 除以除数 divisor 得到的商。 
# 整数除法的结果应当截去（truncate）其小数部分，例如：truncate(8.345) = 8 以及 truncate(-2.7335) = -2 
# 示例 1: 
# 输入: dividend = 10, divisor = 3
#输出: 3
#解释: 10/3 = truncate(3.33333..) = truncate(3) = 3 
# 示例 2: 
# 输入: dividend = 7, divisor = -3
#输出: -2
#解释: 7/-3 = truncate(-2.33333..) = -2 
# 提示： 
# 被除数和除数均为 32 位有符号整数。 
# 除数不为 0。 
# 假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−231, 231 − 1]。本题中，如果除法结果溢出，则返回 231 − 1。 
# Related Topics 数学 二分查找
```



乘除取余都不让用，那就位运算走起. 那问题是，如何设计位运算？`商*除数+余数=被除数`，这个式子大家肯定都清楚 在本题中， 余数是可以忽略的，当然， 余数肯定是小于 除数的 那么我们就可以理解为：商就是 被除数减去N多个 除数，直到 `被除数-N个除数变得小于 `除数最终就是 N这个 商了。



让我们先回顾一下小学时，怎么通过列竖式的方法计算两个整数的除法，以 45/2 为例：




![](https://img-blog.csdnimg.cn/20200703155803356.png)
仔细观察不难发现，这种算法是把除法化归成移位和减法两种运算方法。对于 10 进制数，移位运算就是乘（左移）除（右移）10，而我们都知道计算机中的移位运算是乘（左移）除（右移）2，因为计算机是通过二进制的方法存储数的。这样，类比十进制，二进制的除法（仍以 45/2 为例）可以写作（注意，这里我们并没有用到乘除法）

![](https://img-blog.csdnimg.cn/20200703155822378.png)


下面就是代码实现了

```java
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        # 使用异或判断符号
        sign = (dividend>0)^(divisor>0)
        # 方便起见全部使用正数来做除法，最后加上符号
        dividend = abs(dividend)
        divisor = abs(divisor)
        count = 0

        while dividend >= divisor:
            divisor <<= 1
            count += 1
        result = 0

        while count > 0:
            count -= 1
            divisor >>= 1
            if divisor <= dividend:
                dividend = dividend-divisor
                result += 1<<count
        if sign:
            result = -result

        return result if -(1<<31)<=result<=(1<<31)-1 else (1<<31)-1
```

# LeetCode 第50题： Pow(x, n)



```java
#实现 pow(x, n) ，即计算 x 的 n 次幂函数。 
# 示例 1: 
# 输入: 2.00000, 10
#输出: 1024.00000
# 示例 2: 
# 输入: 2.10000, 3
#输出: 9.26100
# 示例 3: 
# 输入: 2.00000, -2
#输出: 0.25000
#解释: 2-2 = 1/22 = 1/4 = 0.25 
# 说明: 
# -100.0 < x < 100.0 
# n 是 32 位有符号整数，其数值范围是 [−231, 231 − 1] 。 
# Related Topics 数学 二分查找
```

主要是注意n的正负，这个题比较简单了，直接递归调用就行。

- 如果 n 是负数，那么相当于求$ (1/x)^(-n)。
- n 是正数 且 奇数，那么结果需要单独乘以 x
- 如果 n 是正数 且 偶数，求(x^2)^(n/2)，一直递归下去即可。

```java
class Solution(object):
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if n == 0:
            return 1
        if n < 0:
            x = 1 / x
            n = -n
        if n % 2:
            return x * self.myPow(x, n - 1)
        return self.myPow(x * x, n / 2)
```



使用迭代的方法，这个方法叫做二分求幂。


```java
class Solution:
    def myPow(self, x: float, n: int) -> float:
        if n == 0:
            return 1
        if n < 0:
            x = 1 / x
            n = -n
        p = 1
        while n > 1:
            if n % 2 == 0:
                x = x * x
                n /= 2
            else:
                p *= x
                n -= 1
        p *= x        
        return p
```

