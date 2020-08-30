@Author：Runsen
@Date：2020/7/5

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十七、Python | Leetcode栈和队列系列。

@[toc]

# 栈

栈 (Stack)是一种后进先出(last in first off，LIFO)的数据结构。线性表是用数组来实现的，对于栈这种只能一头插入删除的线性表来说，用数组下标为0（栈底不变，只需要跟踪栈顶的变化即可）的一端作为栈底比较合适。




![](https://img-blog.csdnimg.cn/20200705084744639.png)



列表封装的这些方法，实现栈这个常用的数据结构比较容易。栈是一种只能在列表一端进出的特殊列表，pop方法正好完美实现：


```cpp
In [1]: stack=[1,3,5]

In [2]: stack.append(0) # push元素0到尾端，不需要指定索引

In [3]: stack
Out[3]: [1, 3, 5, 0]

In [4]: stack.pop() # pop元素，不需指定索引，此时移出尾端元素
Out[4]: 0

In [5]: stack
Out[5]: [1, 3, 5]
```


由此可见Python的列表当做栈用，完全没有问题，push 和 pop 操作的时间复杂度都为 O(1)



# 队列



队列(Queue)则是一种先进先出 (fisrt in first out，FIFO)的结构.。使用顺序表存储队列时，队列元素的出队是在队头，即下标为0的地方，当有元素出队时，出队元素后面的所有元素都需要向前移动，保证队列的队头始终处在下标为0的位置，此时会大大增加时间复杂度。




![](https://img-blog.csdnimg.cn/20200705084819139.png)


使用列表模拟队列，需要借助Python的collections模块中的双端队列deque实现。如下模拟队列的先进先出，后进后出：






```cpp
In [1]: from collections import deque

In [2]: queue = [1,3,5]

In [3]: deq = deque(queue)

In [4]: deq.append(0) 

In [5]: deq
Out[5]: deque([1, 3, 5, 0]) # 后进插入到队列尾部

In [6]: deq.popleft()  
Out[6]: 1

In [7]: deq
Out[7]: deque([3, 5, 0])# 先进的先出
```


# LeetCode 第 155题：最小栈


```cpp
#设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。 
# push(x) —— 将元素 x 推入栈中。 
# pop() —— 删除栈顶的元素。 
# top() —— 获取栈顶元素。 
# getMin() —— 检索栈中的最小元素。 
# 示例: 
# 输入：
#["MinStack","push","push","push","getMin","pop","top","getMin"]
#[[],[-2],[0],[-3],[],[],[],[]]
#输出：
#[null,null,null,null,-3,null,0,-2]
#解释：
#MinStack minStack = new MinStack();
#minStack.push(-2);
#minStack.push(0);
#minStack.push(-3);
#minStack.getMin();   --> 返回 -3.
#minStack.pop();
#minStack.top();      --> 返回 0.
#minStack.getMin();   --> 返回 -2.
# 提示： 
# pop、top 和 getMin 操作总是在 非空栈 上调用。 
# Related Topics 栈 设计
```


在本题中，我们考虑使用辅助栈与数据栈同步的做法来处理。

题目中提示，pop、top 和 getMin 操作总是在 非空栈 上调用。那么我们先定义一个数据栈来实现这些功能。

题目中还要求能在常数时间内检索到最小元素的栈。在这里，我们使用辅助栈，实现辅助栈中的栈顶一直保持当前的最小值，这样就能够实现常数时间复杂度的操作。


![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9hc3NldHMubGVldGNvZGUtY24uY29tL3NvbHV0aW9uLXN0YXRpYy8xNTUvMTU1X2ZpZzEuZ2lm)





```cpp
class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.data = []
        self.tmp = []


    def push(self, x: int) -> None:
        # 入栈时，同时考虑数据栈和辅助栈
        self.data.append(x)
        # 如果辅助栈为空时，或者元素比辅助栈的最顶元素小或相等时，将该元素入栈
        # 否则，将辅助栈内最顶元素再次入栈
        if len(self.tmp) == 0 or x <= self.tmp[-1]:
            self.tmp.append(x)
        else:
            self.tmp.append(self.tmp[-1])

    def pop(self) -> None:
        # if self.data:
        #     self.data.pop()
        #     self.tmp.pop()
        # 题目要求这里是在非空栈，所以不做判断
        # 如果需判断，可如上
        self.data.pop()
        self.tmp.pop()

    def top(self) -> int:
        # 需判断同 pop()
        return self.data[-1]


    def getMin(self) -> int:
        # 需判断同 pop()
        return self.tmp[-1]

# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```


# LeetCode 第 225题：用队列实现栈

```cpp
#使用队列实现栈的下列操作： 
# push(x) -- 元素 x 入栈 
# pop() -- 移除栈顶元素 
# top() -- 获取栈顶元素 
# empty() -- 返回栈是否为空 
# 注意: 
# 你只能使用队列的基本操作-- 也就是 push to back, peek/pop from front, size, 和 is empty 这些操作是合法的。 
# 你所使用的语言也许不支持队列。 你可以使用 list 或者 deque（双端队列）来模拟一个队列 , 只要是标准的队列操作即可。 
# 你可以假设所有操作都是有效的（例如, 对一个空的栈不会调用 pop 或者 top 操作）。 
# Related Topics 栈 设计
```


根据题意，我们只能使用队列的基本操作，队列因为是先进先出，要实现先进后出的栈，常见的解法方法是使用两个队列。

假设有q1，q2两个队列，我们初始化队列。


```cpp
from collections import deque
class MyStack:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.q1 = deque()
        self.q2 = deque()
```
![](https://img-blog.csdnimg.cn/20200705091105422.png)

压入栈时，加入到q1的末尾，那么q1末尾的元素就是栈顶元素


```cpp
def push(self, x: int) -> None:
    """
    Push element x onto stack.
    """
    self.q1.append(x)
```


![](https://img-blog.csdnimg.cn/20200705091145560.png)
我们需要弹出栈顶元素，也就是q1最后的元素，队列只能是先进先出，我们得用q2把q1出队的元素装着，最后一个出队元素就是栈顶元素。



```cpp
def pop(self) -> int:
    """
    Removes the element on top of the stack and returns that element.
    """
    while len(self.q1) > 1:
        self.q2.append(self.q1.popleft())
    tmp = self.q1.popleft()
    self.q2,self.q1 = self.q1, self.q2
    return tmp
```
判断是否为空，只需要判断q1




```cpp
def empty(self) -> bool:
    """
    Returns whether the stack is empty.
    """
    return not bool(self.q1)
```
取栈顶元素。这里其实可以优化，我们可以在pop时保留一个变量，不过记得在pop时需要加入栈顶元素。



```cpp
def top(self) -> int:
    ans = self.pop()
    self.q1.append(ans)
    return ans
```
下面就是完整代码

```cpp
from collections import deque
class MyStack:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.q1 = deque()
        self.q2 = deque()


    def push(self, x: int) -> None:
        """
        Push element x onto stack.
        """
        self.q1.append(x)


    def pop(self) -> int:
        """
        Removes the element on top of the stack and returns that element.
        """
        while len(self.q1) > 1:
            self.q2.append(self.q1.popleft())
        tmp = self.q1.popleft()
        self.q2,self.q1 = self.q1, self.q2
        return tmp


    def top(self) -> int:
        """
        Get the top element.
        """
        ans = self.pop()
        self.q1.append(ans)
        return ans


    def empty(self) -> bool:
        """
        Returns whether the stack is empty.
        """
        return not bool(self.q1)



# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()

```





#  LeetCode 第232题：用栈实现队列

```cpp
#使用栈实现队列的下列操作：
# push(x) -- 将一个元素放入队列的尾部。 
# pop() -- 从队列首部移除元素。 
# peek() -- 返回队列首部的元素。 
# empty() -- 返回队列是否为空。
# 示例:
# MyQueue queue = new MyQueue();
#queue.push(1);
#queue.push(2);  
#queue.peek();  // 返回 1
#queue.pop();   // 返回 1
#queue.empty(); // 返回 false
# 说明:
# 你只能使用标准的栈操作 -- 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。 
# 你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。 
# 假设所有操作都是有效的 （例如，一个空的队列不会调用 pop 或者 peek 操作）。
# Related Topics 栈 设计
```



使用list表示一个栈，只能使用栈的相关方法，如append()，pop()，s[-1]，分别是栈顶追加元素,删除栈顶元素,取出栈顶元素.。


```cpp
class MyQueue:
    def __init__(self):
        self.s = []
    def push(self, x: int) -> None:
        self.s.append(x)
    def pop(self) -> int:    
        return self.s.pop(0)
    def peek(self) -> int:
        return self.s[0]
    def empty(self) -> bool:
        return not bool(self.s)
```



当然如果使用两个栈，入队操作即追加元素，都在栈s1中操作。

出队操作首先判断缓存栈s2是否有元素，有的话直接取出s2栈顶元素；若s2为空并且s1中有元素，将s1中元素全部转移到s2中，再取出s2栈顶元素，即可模拟队列出队操作；本例中没有出现s2和s1都为空的情况。



```cpp
class MyQueue:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.s1 = []
        self.s2 = []
        
    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        self.s1.append(x)

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        if self.s2:
            return self.s2.pop()
        else:
            if  self.s1 :
                while self.s1:
                    self.s2.append(self.s1.pop())
                return self.s2.pop()

    def peek(self) -> int:
        """
        Get the front element.
        """
        if self.s2:
            return self.s2[-1]
        else:
            if  self.s1 :
                while self.s1:
                    self.s2.append(self.s1.pop())
                return self.s2[-1]

    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        if self.s1 or self.s2:
            return False
        else:
            return True

# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()
```

