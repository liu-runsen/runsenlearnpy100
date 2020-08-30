@Author：Runsen
@Date：2020/6/19

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了六十八、Python | Leetcode链表系列（上篇）。



@[toc]



# 链表 Linked List

链表由许多结点(也可以叫节点或元素)组成，每一个结点有两个域，左边部份叫值域 data，用于存放用户数据；右边叫指针域 next，一般是存储着到下一个元素的指针。head结点(头节点)，head是一个特殊的结节，head结点永远指向第一个结点，tail结点(尾节点)，tail结点也是一个特殊的结点，tail结点永远指向最后一个节点，tail.next = None。



![](https://img-blog.csdnimg.cn/20200619154620950.png)

节点结构



![](https://img-blog.csdnimg.cn/20200619154648533.png)
上面四个节点 abcd 组成一个链表，每一个节点都包含 data 和 next，尾节点的 next 指向 None。



链表中的元素都会两个属性，一个是元素的值，另一个是指针，此指针标记了下一个元素的地址，每一个数据都会保存下一个数据的内存的地址，通过此地址可以找到下一个数据，任意位置插入元素和删除元素效率较高，时间复杂度为O(1)。

要需要访问某个位置的数据，需要从第一个数据开始找起，依次往后遍历，直到找到待查询的位置，故可能在查找某个元素时，时间复杂度达到O(N)






优点：
1.任意位置插入元素和删除元素的速度快，时间复杂度为O(1) 
2.内存利用率高，不会浪费内存 
缺点： 
1. 随机访问效率低，时间复杂度为0(N) 



# 双链表 Doubly Linked List
双向链表也叫双链表，是链表的一种，它的每个数据结点中都有两个指针，分别指向直接后继和直接前驱。所以，从双向链表中的任意一个结点开始，都可以很方便地访问它的前驱结点和后继结点。


![](https://img-blog.csdnimg.cn/2019031515160942.jpg)




# 代码实现


下面以class类创建节点， 每个节点包含当前节点所要存的数据data，和指向下一节点的指针。

节点类的定义很简单，节点只有两个属性，data 和 next，next指向下一个节点。定义完节点类后，可以创建节点，但是还需要将节点连接在一起，构成链表才可以。



```python
class Node:
    '''定义节点类'''
    def __init__(self, data):
        self.data = data    #值域，存储数据
        self.next = None    #指针域，存储下一元素的地址

#定义四个节点
a = Node(86)
b = Node(19)
c = Node(4)
d = Node(12)
#最简单的方法将四个节点连接
a.next = b
b.next = c
c.next = d
head = a
#依次输出节点的值
while head is not None:
    print(head.data)
    head = head.next
#输出为 86 19 4 12
```

# 链表的实现


定义一个链表类来实现链表，同时可以定义对链表的简单操作，比如对链表进行添加节点，移除节点，插入节点等方法。





```python
class LinkedList:
    '''定义链表类'''
    def __init__(self):    #不需要参数，返回值是空链表
        self.head = None   #头节点
        self.tail = None   #尾节点
```



定义类方法，判断链表是否为空。

```java
def is_empty(self):    
    '''判断链表是否为空'''
    return self.head is None
```

定义类方法，向链表末尾新的节点。

```java
def append(self, data):    
    '''向链表里添加节点'''
    node = Node(data)      #创建一个节点实例
    if self.head is None:  #判断链表是否为空
         self.head = node   #如果是空链表，添加一个节点，头节点就是尾节点
         self.tail = node
     else:
         self.tail.next = node  #tail为尾节点，在尾节点添加新节点，尾节点的指针域
         self.tail = node       #指向下一节点，这时新的尾节点就是node节点
```

定义类方法，实现遍历链表元素。

```java
def iter(self):            
    '''遍历链表,函数返回的是一个生成器'''
    if not self.head:    #遍历从链表的头节点开始，如果不是，返回
        return
    current = self.head  #将head节点赋值给current,当前节点
    yield current.data   #包含yield语句的函数都被称为生成器。
    while current.next:
        current = current.next
        yield current.data

```

定义类方法，实现在链表指定位置插入新的节点。

```java
def insert(self, index, vaule):    
    '''在链表的指定索引插入一个新的节点'''
    current = self.head
    current_index = 0        #head节点的索引为0
    if self.head is None:    #如果链表为空
        raise Exception("The list is an empty list")
    while current_index < index -1:  #通过while循环找到指定索引的节点
        current = current.next
        if current is None:  #判断是否为尾节点
            raise Exception('......')
        current_index += 1
    node = Node(vaule)       #新建节点
    node.next = current.next #node的指针域指向原节点的下一节点
    current.next = node      #原节点的下一节点指向node
    if node.next is None:
        self.tail = node
```

要向 a 和 b节点之间插入一个新的节点 e ，需要将 `e.next = a.next `，之后再将 `a.next = e`，这是插入一个新的节点的关键。

定义类方法，实现移除链表指定索引的节点。

```java
def remove(self, index):
    '''移除链表指定索引元素'''
    current = self.head
    current_index = 0
    if self.head is None:  # 空链表时
        raise Exception('The list is an empty list')
    while current_index < index-1:
        current = current.next
        if current is None:
            raise Exception('list length less than index')
        current_index += 1
    if index == 0:   # 当删除第一个节点时
        self.head = current.next
        current = current.next
        return
    if self.head is self.tail:   # 当只有一个节点的链表时
        self.head = None
        self.tail = None
        return 
    current.next = current.next.next
    if current.next is None:  # 当删除的节点是链表最后一个节点时
        self.tail = current

```

定义类方法，返回链表的长度(节点的数量)。

```java
def size(self):
    '''返回链表长度'''
    current = self.head
    count = 0
    if current is None:
        return 'The list is an empty list'
    while current is not None:
        count += 1
        current = current.next
    return count

```


最后，来实现一下链表的一些简单操作。

```python
if __name__ == '__main__':
    l = LinkedList()    #创建一个链表对象，空链表
    for i in range(10): #向链表里添加节点
        l.append(i)
    print(list(l.iter()))   #遍历链表元素
    #输出为[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    l.insert(2, 10)    #在索引2处插入10
    print(list(l.iter()))   #遍历链表元素
    #输出为[0, 1, 10, 2, 3, 4, 5, 6, 7, 8, 9]
    l.remove(0)       #移除索引为0的节点
    print(list(l.iter()))   #遍历链表元素
    #输出为[1, 2, 3, 4, 5, 6, 7, 8, 9]
    print(l.size())   #输出链表的长度 输出为10
```


# LeetCode 第 2题：两数相加  



```java
#给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。 
# 如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。 
# 您可以假设除了数字 0 之外，这两个数都不会以 0 开头。 
# 示例： 
# 输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
#输出：7 -> 0 -> 8
#原因：342 + 465 = 807
# 
# Related Topics 链表 数学
```




思路一：将链表转化列表，反转列表 用join方法拼接数字 切片[::-1]，将sum转化成链表res


```python
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        # 将链表转化列表
        val1, val2 = [l1.val], [l2.val]

        while l1.next:
            val1.append(l1.next.val)
            l1 = l1.next

        while l2.next:
            val2.append(l2.next.val)
            l2 = l2.next

        # 反转列表 用join方法拼接数字 切片[::-1]


        num_1 = ''.join([str(i) for i in val1[::-1]])
        num_2 = ''.join([str(i) for i in val2[::-1]])

        sums =  str(int(num_1) + int(num_2))[::-1]

        # 将sum转化成链表res

        # 头节点
        res  = head = ListNode(int(sums[0]))

        for i in range(1, len(sums)):
            # 拼接
            head.next = ListNode(int(sums[i]))
            head = head.next
        return res


```




![](https://img-blog.csdnimg.cn/20200619160926309.png)


思路二：将结果保存在一个新的链表中，使用两个指针，一个指向头节点，用于返回结果，另一个指向当前节点，用于计算并保存结果。遍历两个输入链表，逐位进行相加，若某一个链表遍历到了结尾，则取 0 参与运算。每一位的数字为两个数字对应位以及进位之和除 10 的余数，而该位是否有进位则是这个和除 10 的商。



优化：不需要将整个数的和求出，只需要每一位对应相加，

![](https://img-blog.csdnimg.cn/20200619160405934.png)


```python
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
       # 判断0还是1
        res = 0
        root = n = ListNode(0)
    
        while l1 or l2 or res:
            v1 = v2 = 0
            if l1:
                v1 = l1.val
                l1 = l1.next
            if l2:
                v2 = l2.val
                l2 = l2.next
            # divmod() 函数把除数和余数运算结果结合起来，返回一个包含商和余数的元组(a // b, a % b)。
            res, val = divmod(v1 + v2 + res, 10)
            n.next = ListNode(val)
            n = n.next
            
        return root.next
```


![](https://img-blog.csdnimg.cn/20200619161524801.png)


