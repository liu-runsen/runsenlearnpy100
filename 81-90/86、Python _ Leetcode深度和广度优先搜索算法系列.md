
@Author：Runsen
@Date：2020/7/8


> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今天高考，当年我就是一个辣鸡，现在还是一个辣鸡，祝高考的个个清华北大
。辣鸡的我决定继续更新Python教程，今天就开始了八十六、Python | Leetcode深度和广度优先搜索算法系列。

如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。

@[toc]


# 深度优先算法（DFS）

 不断地沿着顶点的深度方向进行遍历，该算法的空间复杂度与数据结构深度成正比。

深度优先算法：

（1）访问初始顶点v并标记顶点v已访问。
（2）查找顶点v的第一个邻接顶点w。
（3）若顶点v的邻接顶点w存在，则继续执行；否则回溯到v，再找v的另外一个未访问过的邻接点。
（4）若顶点w尚未被访问，则访问顶点w并标记顶点w为已访问。
（5）继续查找顶点w的下一个邻接顶点wi，如果v取值wi转到步骤（3）。直到连通图中所有顶点全部访问过为止。


# 广度优先算法（BFS）

  先访问完当前顶点的所有邻接点，然后再访问下一层的所有节点，该算法适用于解决最短、最小路径等问题，但是构建广度优先算法需要维护自己的队列。


（1）顶点v入队列。
（2）当队列非空时则继续执行，否则算法结束。
（3）出队列取得队头顶点v；访问顶点v并标记顶点v已被访问。
（4）查找顶点v的第一个邻接顶点col。
（5）若v的邻接顶点col未被访问过的，则col入队列。
（6）继续查找顶点v的另一个新的邻接顶点col，转到步骤（5）。直到顶点v的所有未被访问过的邻接点处理完。转到步骤（2）。





# Leetcode第111题： 二叉树的最小深度




```csharp
#给定一个二叉树，找出其最小深度。 
# 最小深度是从根节点到最近叶子节点的最短路径上的节点数量。 
# 说明: 叶子节点是指没有子节点的节点。 
# 示例: 
# 给定二叉树 [3,9,20,null,null,15,7], 
#
#     3
#   / \
#  9  20
#    /  \
#   15   7 
#
# 返回它的最小深度 2. 
# Related Topics 树 深度优先搜索 广度优先搜索
```
最小深度的定义：它是从根节点到最近叶子节点的最短路径上的节点数量。这种情况下，由于节点 1 没有右子树，那么右子树的深度为 0，左子树的深度为 1，但是却不能说它的左右子树的最小深度为 0，因为右子树不存在，即节点 1 没有右叶子节点，不满足条件。


比如二叉树 [1, 2] 的最小深度为 2，而不是 1。


![](https://img-blog.csdnimg.cn/2020070822093271.png)


对于一个节点，如果是叶子节点，则返回其深度；如果只有左子树，则递归得到左子树的最小深度；如果只有右子树，则递归得到右子树的最小深度；如果左右孩子节点都有，则递归得到两个子树的深度，并且取最小值。

```csharp
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def minDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root:
            return 0
        return self.get_min_depth(root, 0)

    def get_min_depth(self, node, depth):
        # 分为四种情况：叶子节点，只有左孩子的节点，只有右孩子的节点，两个孩子都有的节点
        if not node.left and not node.right:
            return depth+1
        if node.left and node.right:
            return min(self.get_min_depth(node.left, depth+1), self.get_min_depth(node.right, depth+1))
        if node.left:
            return self.get_min_depth(node.left, depth+1)
        if node.right:
            return self.get_min_depth(node.right, depth+1)
```

上面的是递归的做法

BFS，当遇到第一个叶子节点的时候，该节点深度就是最小深度。



```csharp
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root: return 0
        queue = [(1, root)]
        while queue:
            depth, node = queue.pop(0)
            if not node.left and not node.right:
                return depth
            if node.left:
                queue.append((depth + 1, node.left))
            if node.right:
                queue.append((depth + 1, node.right))
```



DFS，需要把所有的叶子节点的深度进行比较，才可以得到最终的最小深度。


```csharp
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root: return 0
        stack = [(1, root)]
        min_depth = float('inf')
        while stack:
            depth, node = stack.pop()
            if not node.left and not node.right:
                min_depth = min(min_depth, depth)
            if node.right:
                stack.append((depth + 1, node.right))
            if node.left:
                stack.append((depth + 1, node.left))       
        return min_depth 
```
# 

# Leetcode第112题： 路径总和



```csharp
#给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。
# 说明: 叶子节点是指没有子节点的节点。
# 示例: 
#给定如下二叉树，以及目标和 sum = 22， 
#
#               5
#             / \
#            4   8
#           /   / \
#          11  13  4
#         /  \      \
#        7    2      1
# 返回 true, 因为存在目标和为 22 的根节点到叶子节点的路径 5->4->11->2。 
# Related Topics 树 深度优先搜索
```
方法一：递归（DFS，深度优先搜索）




```csharp
class Solution:
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        # 二叉树 root 为 null
        if not root:
            return False
        # 无左右子树
        if not root.left and not root.right:
            return sum == root.val
        return self.hasPathSum(root.left, sum - root.val) or self.hasPathSum(root.right, sum - root.val)
```


方法二：广度优先搜索（BFS）


collection 为 Python 的内建集合版块，collection.deque 为双端队列，可以从两端添加（append）和弹出（pop）元素，且时间复杂度为 O(1)，耗时小于 list 的 insert 和 pop 操作的 O(N)。


```csharp
d = deque([1, 2, 3, 4, 5]
## 两端添加元素
d.append(6)                 # deque([1, 2, 3, 4, 5, 6])
d.appendleft(0)             # deque([0, 1, 2, 3, 4, 5, 6])
## 两端按序拓展元素
d.extend([7, 8])            # deque([0, 1, 2, 3, 4, 5, 6, 7, 8])
d.extendleft([-1, -2])      # deque([-2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8])
## 指定位置插入元素
d.insert(0, -3)             # deque([-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8])
## 两端弹出元素
d.pop()                     # deque([-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7])
d.popleft()                 # deque([-2, -1, 0, 1, 2, 3, 4, 5, 6, 7])
## 删除从左到右找到的首个指定元素
d.remove(-1)                # deque([-2, 0, 1, 2, 3, 4, 5, 6, 7])
## 指定元素计数
d.count(3)                  # 1
## 返回从左到右找到的首个指定元素的索引
d.index(5)                  # 6
## 逆序排列
d.reverse()                 # deque([7, 6, 5, 4, 3, 2, 1, 0, -2])
## 元素双向循环指定步数
d.rotate(2)                 # deque([0, -2, 7, 6, 5, 4, 3, 2, 1])
d.rotate(-2)                # deque([7, 6, 5, 4, 3, 2, 1, 0, -2])
```


时间复杂度：O(N)
空间复杂度：O(H)，H 为树的高度，最坏情况下，树成链状，为 O(N)。



```csharp
class Solution:
    import collections
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        if not root:
            return False
        que_node = collections.deque([root])        # 结点队列
        que_val = collections.deque([root.val])     # 结点值队列
        while que_node:
            now = que_node.popleft()                # 当前结点
            temp = que_val.popleft()                # 临时存储值
            if not now.left and not now.right:
                if temp == sum:
                    return True
                continue
            if now.left:
                que_node.append(now.left)
                que_val.append(now.left.val + temp)
            if now.right:
                que_node.append(now.right)
                que_val.append(now.right.val + temp)
        return False
```

