@Author：Runsen
@Date：2020/7/3

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十五、Python | Leetcode哈希表系列。

@[toc]



# 哈希表

哈希表（散列表）的思想是将关键字 Key 映射到存放记录的散列表中从而进行快速访问，其中映射函数 f(key) 称为哈希函数（散列函数），依据哈希函数建立的查找表称为哈希表。

Hash，音译为哈希，是把任意长度的输入（又叫做预映射pre-image）通过散列算法变换成固定长度的输出，该输出就是散列值。这种转换是一种压缩映射，也就是，散列值的空间通常远小于输入的空间，不同的输入可能会散列成相同的输出，所以不可能从散列值来确定唯一的输入值。简单的说就是一种将任意长度的消息压缩到某一固定长度的消息摘要的函数。


假如班级里面有50个学生，都有各自的名字，我们想把学生的名字放在一个表上，同时便于很快的查找，你会毫无想到数组，但是查找的复杂度是`O(n)`,所以哈希表就是为了解决这问题，将查找的复杂度达到 `O(1)`

![](https://img-blog.csdnimg.cn/20190319091629943.png)




假如有个学生的名字叫做`lies`,通过hash函数，得到下标`9` ，将`lies`的ASCII码加起来 `429%30 =9` ,这样的过程就是`hash`函数。

但是又没有可能出现`hash`碰撞，就是出现了一样的`hash`值，当然有可能


![](https://img-blog.csdnimg.cn/20190319091548415.png)


假如有个人的名字叫做`foes`,那么如何查找呢？当然是将数据储存成链表，用链表的方式来查找。



其实，哈希表就是一个具备映射关系的表，我们可以通过映射关系由键找到值。下面是一个简单的哈希表：

```cpp
class Map:
    def __init__(self):
        self.items =[None]*100
    def hash(self,a):
        return a*1+0
    def put(self,k,v):
        self.items[hash(k)] = v
    def get(self,k):
        hashcode=hash(k)
        return self.items[hashcode]
```


这个哈希函数十分简单，但简单不妨碍它成为一个哈希函数，事实上，它叫直接定址法，是一个线性函数：$hash(k)= a*k+b$

直接定址法的优点很明显，就是它不会产生重复的hash值。但由于它与键值本身有关系，所以当键值分布很散的时候，会浪费大量的存储空间。所以一般是不会用到直接定址法的。




![](https://img-blog.csdnimg.cn/20200703231235952.png)

# LeetCode 第 136题：只出现一次的数字



```cpp
#给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。 
# 说明： 
# 你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？ 
# 示例 1: 
# 输入: [2,2,1]
#输出: 1
# 示例 2: 
# 输入: [4,1,2,1,2]
#输出: 4 
# Related Topics 位运算 哈希表
```


下面一行代码不做解释。
```cpp
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return sum(set(nums))*2-sum(nums)

```
一遍遍历，用哈希表计数；再遍历，返回个数是1的数。`{}`用于创建空字典，空集合用`set()`
dict的.get(a,b)中取出字典中键为a的值，如果不存在这样的键，则返回b。



```cpp
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        dic = {}
        for i in nums:
            dic[i] = dic.get(i,0)+1
            
        for i in nums:
            if dic.get(i)==1:
                return i
```


# LeetCode 第 217题：存在重复元素



```cpp
#给定一个整数数组，判断是否存在重复元素。 
# 如果任意一值在数组中出现至少两次，函数返回 true 。如果数组中每个元素都不相同，则返回 false 。 
# 示例 1: 
# 输入: [1,2,3,1]
#输出: true 
# 示例 2: 
# 输入: [1,2,3,4]
#输出: false 
# 示例 3: 
# 输入: [1,1,1,3,3,4,3,2,4,2]
#输出: true 
# Related Topics 数组 哈希表
```

下面代码不解释
```cpp
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        if len(set(nums)) == len(nums):
            return False
        else: 
            return True
```

初试化哈希表`dic = {}`。遍历数组：若i不在hash中，则令`dic[i] = 1`为key，1为value（随便什么都可以）。若已存在，则返回True。


```cpp
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        dic = {}
        for i in nums:
            if dic.get(i):
                return True
            dic[i] = 1
        return False
```


# 剑指 Offer 50. 第一个只出现一次的字符



```cpp
#在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。 
# 示例: 
# s = "abaccdeff"
#返回 "b"
#s = "" 
#返回 " "
# 限制： 
# 0 <= s 的长度 <= 50000 
# Related Topics 哈希表
```


遍历字符串 s ，使用哈希表统计 “各字符数量是否 > 1 ”。
再遍历字符串 s ，在哈希表中找到首个 “数量为 1的字符”，并返回。


```cpp
class Solution:
    def firstUniqChar(self, s: str) -> str:
        dicts={}
        for i in s:
            dicts[i]=dicts.get(i,0)+1
        for i in s:
            if dicts[i]==1:
                return i
        return ' '
```

