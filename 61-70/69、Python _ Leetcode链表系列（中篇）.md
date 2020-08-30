@Author：Runsen
@Date：2020/6/19

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了六十九、Python | Leetcode链表系列（中篇）。



@[toc]






# LeetCode  第21题：合并两个有序链表

```java
#将两个升序链表合并为一个新的 升序 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 
# 示例： 
#
# 输入：1->2->4, 1->3->4
#输出：1->1->2->3->4->4
# 
# Related Topics 链表
```


这个解决的方法使用递归，如果L1为空就返回L2，L2为空返回L1，L1的val<=L2的val，那么继续递归
```java
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution(object):
	def mergeTwoLists(self, l1, l2):
		"""
		:type l1: ListNode
		:type l2: ListNode
		:rtype: ListNode
		"""
		#递归的结束点就是L1或者L2为空就返回
		#如果L1为空就返回L2，L2为空返回L1
		# if not (l1 and l2):
			# return l1 if l1 else l2
		if not l1:
            return l2
        elif not l2:
            return l1
		#L1的val<=L2的val，那么继续递归
		#当前L1的next指向一个递归函数
		#意思是L1的下一个和L2哪个大，就作为当前L1的next
	    elif l1.val<=l2.val:
			l1.next = self.mergeTwoLists(l1.next,l2)
			return l1
		else:
			l2.next = self.mergeTwoLists(l1,l2.next)
			return l2

```





![](https://img-blog.csdnimg.cn/20200628114647839.png)


# LeetCode 第 23 题：合并 k 个排序链表
```java
#合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。 
# 示例: 
# 输入:
#[
#  1->4->5,
#  1->3->4,
#  2->6
#]
#输出: 1->1->2->3->4->4->5->6 
# Related Topics 堆 链表 分治算法
```


第1种法就是常规思路，直接将所有的元素取出，然后排个序，再重组就达到了目的。


遍历所有链表，将所有节点的值放到一个数组中。将这个数组排序，然后遍历所有元素得到正确顺序的值。用遍历得到的值，创建一个新的有序链表。


时间复杂度：$O(N\log N)$ ，其中 N 是节点的总数目



空间复杂度：$O(N)$。

排序花费$O(N)$空间（这取决于你选择的算法）。
创建一个新的链表花费 $O(N)$的空间。

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode :
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        self.nodes = []
        head = point = ListNode(0)
        for l in lists:
            while l:
                self.nodes.append(l.val)
                l = l.next
        for x in sorted(self.nodes):
            point.next = ListNode(x)
            point = point.next
        return head.next
```




时间复杂度：$O(N \log k)$，这里 N 是这 k 个链表的结点总数，每一次从一个优先队列中选出一个最小结点的时间复杂度是 $O(logk)$，故时间复杂度为	$O(N \log k)$。
空间复杂度：$O(k)$，使用优先队列需要 k 个空间，“穿针引线”需要常数个空间，因此空间复杂度为 $O(k)$。











# LeetCode 第 141 题：判断链表中是否有环



![](https://img-blog.csdnimg.cn/20191122154610446.png)
 

> 你能用 O(1)（即，常量）内存解决此问题吗？ 

遍历整个数组, 给出的数据包含在集合中则说明有环, 返回 True; 若遍历完毕, 则说明无环, 返回 False，如果用列表也是一样。

**暴力解法**

```python
class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        """
        暴力法：通过遍历链表，用set来存储访问的节点，如果在set出现一样的节点，说明有坏，时间复杂度O(n)
        :type head: ListNode
        :rtype: bool
        """
        st = set()
        while head:
            if head in st:
                return True
            st.add(head )
            head = head.next
        return False


		# 下面是列表
        l = []
        while head:
            if head in l:
                return True
            else:
                l.append(head)
                head = head.next
        return False
        
```





![](https://img-blog.csdnimg.cn/20200628121724978.png)

暴力的时间空间复杂度都是O(n)






题目要求用 $O(1)$空间复杂度


> 这道题考的是**快慢指针** $O(1)$空间复杂度






通过使用具有 不同速度 的快、慢两个指针遍历链表，空间复杂度可以被降低至$O(1)$。慢指针每次移动一步，而快指针每次移动两步。

如果列表中不存在环，最终快指针将会最先到达尾部，此时我们可以返回 false。



进阶的要求是以 O(1) 的空间复杂度实现, 想象这样一个场景, 你和一个朋友一起散步, 你每次移动两步, 朋友每次一步, 如为单向定长道路, 你必然先到达重点. 若是环绕操场,则你们终将相遇.





```java
class Solution(object):
    def hasCycle(self, head):
        slow = fast = head
        while slow and fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False
```



# LeetCode 第 206 题：反转链表





```java
#反转一个单链表。 
# 示例: 
# 输入: 1->2->3->4->5->NULL
#输出: 5->4->3->2->1->NULL 
# 进阶: 
#你可以迭代或递归地反转链表。你能否用两种方法解决这道题？ 
# Related Topics 链表
```

将当前节点的next指针指向前驱的节点，需要有2个指针来记录，一个记录当前节点，一个记录前驱节点，循环5次直到列表结束，三个简单复制语句

```python
class Solution:
    def reverseList(self, head):
        cur, prev = head, None
        while cur:
            cur.next, prev, cur = prev, cur, cur.next
        return prev
```

