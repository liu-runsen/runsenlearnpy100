

@Author：Runsen
@Date：2020/7/6

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）





作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了八十一、Python | Leetcode 二叉树系列（下篇）。作为一名 Python 程序员，如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。



@[toc]

#  LeetCode 第 94题：二叉树的中序遍历



```cpp
#给定一个二叉树，返回它的中序 遍历。 
# 示例: 
# 输入: [1,null,2,3]
#   1
#    \
#     2
#    /
#   3
#输出: [1,3,2] 
# 进阶: 递归算法很简单，你可以通过迭代算法完成吗？ 
# Related Topics 栈 树 哈希表
```


递归：中序遍历的顺序是左根右。使用递归解题，条件是：当前节点为空则返回；递归条件是遍历其左右子节点。先访问左子节点，接着将当前节点的值添加到结果数组，然后访问右子节点。



栈的题解：首先访问左子树，将左子树存入栈中，每次将栈顶元素存入结果，如果右子树为空，取出栈顶元素，如果当前元素为栈顶元素右子树，一直弹出至当前元素不为栈顶元素右子树(此处说明访问右子树，根节点已经被访问过，弹出即可)。如果节点右子树不为空，访问右子树，继续循环遍历左子树，存入栈中。






```cpp
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        def helper(root):
            if not root:
                return 
            helper(root.left)
            res.append(root.val)
            helper(root.right)
        helper(root)
        return res

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        res = []  #结果列表
        stack = []  #辅助栈
        cur = root  #当前节点
        while stack or cur:
            while cur:  #一直遍历到最后一层
                res.append(cur.val)  
                stack.append(cur)
                cur = cur.left
            top = stack.pop()  #此时该节点的左子树已经全部遍历完
            cur = top.right  #对右子树遍历
        return res
```


#  LeetCode 第 98题：验证二叉搜索树



```cpp
#给定一个二叉树，判断其是否是一个有效的二叉搜索树。 
# 假设一个二叉搜索树具有如下特征： 
# 节点的左子树只包含小于当前节点的数。 
# 节点的右子树只包含大于当前节点的数。 
# 所有左子树和右子树自身必须也是二叉搜索树。 
# 示例 1: 
# 输入:
#    2
#   / \
#  1   3
#输出: true
# 示例 2: 
# 输入:
#    5
#   / \
#  1   4
#     / \
#    3   6
#输出: false
#解释: 输入为: [5,1,4,null,null,3,6]。
#     根节点的值为 5 ，但是其右子节点值为 4 。
# Related Topics 树 深度优先搜索
```


做这题，需要了解二叉搜索树的特点：
- 当前节点的左子树的所有节点的值都应该小于当前节点的值；
- 当前节点的右子树的所有节点的值都应该大于当前节点的值

为了简便，我们可以这么做：

在之前中介绍过二叉搜索树一个很重要的定义就是，对一棵二叉搜索树进行中序遍历(左->根->右)，遍历所得的节点序列是一个升序排列的序列。所以我们可以利用二叉搜索树的这个性质，来判断一个二叉搜索树是否合法，就是上面那题的变形。





![](https://img-blog.csdnimg.cn/20200706125032900.png)

```cpp
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:      
        #中序遍历，观察到中序遍历的顺序是左->中->右,也就是按照从小到大的顺序，因此这样思考题目就很好解了,按照中序遍历，将值依次存入列表中。最后判断
        if not root:
            return True
        result = []
        def middle_traversal(root):
            if root.left:
                middle_traversal(root.left)
            result.append(root.val)
            if root.right:
                middle_traversal(root.right)
        middle_traversal(root)
        return result == sorted(result) and len(set(result)) == len(result)

# 下面是栈的题解
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        stack, preNum = [], float("-inf")
        while len(stack) > 0 or root:
            if root:
                stack.append(root)
                root = root.left
            else:
                root = stack.pop()
                if root.val <= preNum:
                    return False
                preNum = root.val
                root = root.right
        return True
```




#  LeetCode 第 105题：从前序与中序遍历序列构造二叉树




```cpp
#根据一棵树的前序遍历与中序遍历构造二叉树。 
# 注意: 
#你可以假设树中没有重复的元素。 
# 例如，给出
# 前序遍历 preorder = [3,9,20,15,7]
#中序遍历 inorder = [9,3,15,20,7] 
# 返回如下的二叉树： 
#
#     3
#   / \
#  9  20
#    /  \
#   15   7 
# Related Topics 树 深度优先搜索 数组
```



二叉树前序遍历：

- 先遍历根节点
- 再递归遍历左子树
- 最后递归遍历右子树

二叉树中序遍历：

- 先递归遍历左子树
- 再遍历根节点
- 最后递归遍历右子树

二叉树后序遍历：

- 先递归遍历左子树
- 再递归遍历右子树
- 最后遍历根节点

前序遍历和中序遍历二者之间的联系，二者相同的纽带为根节点，因此我们可以通过在前序遍历中定位到根节点，然后从中序遍历中根节点找到对应的index，从而可以知道左右子树分别的节点数目


```cpp
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        if not preorder or not inorder:
            return None
        root = TreeNode(preorder[0])
        index = inorder.index(preorder[0])
        root.left = self.buildTree(preorder[1:index+1], inorder[:index])
        root.right = self.buildTree(preorder[index+1:], inorder[index+1:])
        return root
```
#  LeetCode 第 106题：从中序与后序遍历序列构造二叉树


```cpp
#根据一棵树的中序遍历与后序遍历构造二叉树。 
# 注意: 
#你可以假设树中没有重复的元素。
# 例如，给出 
# 中序遍历 inorder = [9,3,15,20,7]
#后序遍历 postorder = [9,15,7,20,3] 
# 返回如下的二叉树： 
#     3
#   / \
#  9  20
#    /  \
#   15   7
# Related Topics 树 深度优先搜索 数组
```
道理和上面的一样，从后序遍历中定位到根节点，然后从中序遍历中根节点找到对应的index，从而可以知道左右子树分别的节点数目。

```cpp
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> TreeNode:
        # 实际上inorder 和 postorder一定是同时为空的，因此你无论判断哪个都行
        if not inorder:
            return None
        root = TreeNode(postorder[-1])
        i = inorder.index(root.val)
        root.left = self.buildTree(inorder[:i], postorder[:i])
        root.right = self.buildTree(inorder[i+1:], postorder[i:-1])
        return root
```
