@Author：Runsen
@Date：2020/7/3

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十、Python | Leetcode链表系列（下篇）。



@[toc]






# LeetCode  第24题：两两交换链表的节点


```java
#给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。 
#
# 你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。
# 示例: 
#
# 给定 1->2->3->4, 你应该返回 2->1->4->3.
# 
# Related Topics 链表
```


思路：a,b,pre记录三个指针，相邻两个，相邻两个元素前面的一个，第一步将节点 2 指向节点 1，然后再将节点 1 指向节点三。这一步交换完毕后链表变为 2->1->3->4。在进行下一次交换，将节点 4 指向节点 3，节点3指向none 但是还要注意节点 1 的指向，节点 1 要指向节点 4。



 
```java
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
	def swapPairs(self,head):
	    pre, pre.next = self, head
	    while pre.next and pre.next.next:
	        a = pre.next
	        b = a.next
	        pre.next,b.next ,a.next = b,a,b.next
	        pre = a
	        
	    return  self.next
```



![](https://img-blog.csdnimg.cn/2020070308012239.png)

# LeetCode  第83题：删除排序链表中的重复元素





```java
#给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。 
# 示例 1: 
# 输入: 1->1->2
#输出: 1->2
# 示例 2: 
# 输入: 1->1->2->3->3
#输出: 1->2->3 
# Related Topics 链表
```


如果遇到cur.val和cur.next.val重复,让cur.next=cur.next.next


```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        h = head
        while head and head.next:
            if head.val == head.next.val:
                head.next = head.next.next
            else:
                head = head.next
                
        return h

class Solution:
    def deleteDuplicates(self, head):
        cur = root = head
        while head:
            if head.val != cur.val:
                cur.next = cur = head
            head = cur.next = head.next
        return root
```





![](https://img-blog.csdnimg.cn/20200703081419328.png)


# LeetCode 第148题： 排序链表（重要）





```java
#在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序。
# 示例 1:
# 输入: 4->2->1->3
#输出: 1->2->3->4
# 示例 2: 
#
# 输入: -1->5->3->4->0
#输出: -1->0->3->4->5 
# Related Topics 排序 链表
```



题目要求时间空间复杂度分别为$O(nlogn)$和$O(1)$，根据时间复杂度我们自然想到二分法，从而联想到归并排序；

利用归并的思想，递归地将当前链表分为两段，然后merge，分两段的方法是使用 fast-slow 法，用两个指针，一个每次走两步，一个走一步，直到快的走到了末尾，然后慢的所在位置就是中间位置，这样就分成了两段。

归并排序分为两步，1.找到待排序链表的中间节点（使用快慢指针法，leetcode 876题）2.合并两个有序链表（leetcode 21题），因此本题相当于结合这两步来实现链表排序。

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
class Solution:
    def sortList(self, head: ListNode) -> ListNode:
        # if not head or not head.next:#
        if head == None or head.next == None:
            return head 
        slow  = head#快慢指针法找到链表中点
        fast = head
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        right = slow.next
        # print(right.val)
        slow.next = None #这一句的原因是 需要对中点前的链表进行割断处理

        l1 = self.sortList(head)#递归保证l1和l2为有序链表
        l2 = self.sortList(right)
        return self.mergeTwoLists(l1,l2)
	# 合并两个有序链表
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1 and not l2:
            return None
        if not l1:
            return l2
        if not l2:
            return l1
        head = head1 = ListNode(0)
        while l1 and l2:
            if l1.val <= l2.val:
                head.next = l1
                l1 = l1.next
            else:
                head.next = l2
                l2 = l2.next
            head = head.next
        if not l1 : head.next = l2
        if not l2 : head.next = l1
        return head1.next
```
下面是测试代码

```java
if __name__ == "__main__":
    n1 = ListNode(4)
    n2 = ListNode(7)
    n3 = ListNode(6)
    n4 = ListNode(9)
    n5 = ListNode(12)
    m=n1
    n1.next=n2
    n2.next=n3
    n3.next=n4
    n4.next=n5
    print('原链表的节点：')    
    while m:
        print('节点%d的值:'%(m.val),m.val)
        m=m.next
    print('\n排序之后的节点：')

    s=Solution()
    s.sortList(n1)
    while n1:
        print('节点%d的值:'%(n1.val),n1.val)
        n1=n1.next
#result
原链表的节点：
节点4的值: 4
节点7的值: 7
节点6的值: 6
节点9的值: 9
节点12的值: 12

排序之后的节点：
节点4的值: 4
节点6的值: 6
节点7的值: 7
节点9的值: 9
节点12的值: 12
```


![](https://img-blog.csdnimg.cn/20200703082922110.png)
# LeetCode 第 876题： 链表的中间结点（重要）

```java
# 输入：[1,2,3,4,5]
#输出：此列表中的结点 3 (序列化形式：[3,4,5])
#返回的结点值为 3 。 (测评系统对该结点序列化表述是 [3,4,5])。
#注意，我们返回了一个 ListNode 类型的对象 ans，这样：
#ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, 以及 ans.next.next.next = NULL.
# 示例 2： 
# 输入：[1,2,3,4,5,6]
#输出：此列表中的结点 4 (序列化形式：[4,5,6])
#由于该列表有两个中间结点，值分别为 3 和 4，我们返回第二个结点。
# 提示： 
# 给定链表的结点数介于 1 和 100 之间。 
# Related Topics 链表
```
**思路**
- 遍历两次。第一次遍历求导链表长度，找出中间结点的长度值，第二层遍历找到中间结点并返回；
- 快慢指针法。慢指针每次走一步，快指针每次走两步，快指针走到链表末尾时，慢指针刚好走到链表中间。方法２时间复杂度更低，只需遍历一次。

```java
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    def middleNode(self, head: ListNode) -> ListNode:
        slow = head
        fast = head
        while  fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        return slow
```



![](https://img-blog.csdnimg.cn/20200703083340934.png)
