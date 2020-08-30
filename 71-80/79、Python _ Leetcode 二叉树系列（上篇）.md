
@Author：Runsen
@Date：2020/7/5

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）





作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)

今日，我决定继续更新Python教程，今天就开始了七十九、Python | Leetcode 二叉树系列（上篇）。作为一名 Python 程序员，如果把基础的数据结构与算法都自己亲自实现一遍，那么你已经比 90% 的 Python 程序员更优秀了。



@[toc]





# 树

树形结构本身具有递归的性质(在其后的编程中体现的淋漓尽致)；树是一种非常重要的非线性结构。

![](https://img-blog.csdnimg.cn/20190528213911826.png)

看下图，A 节点就是 B 节点的父节点，B 节点是 A 节点的子节点.。B、C、D 这三个节点的父节点是同一个节点A，，没有父节点的叫做根节点，也就是 E 。


![](https://img-blog.csdnimg.cn/20190528214008172.png)

没有子节点的节点叫作叶子节点或者叶节点，图中的G，H，I，J，K，L




关于“树”，还有三个比较相似的概念：高度（Height）、深度（Depth），层（level）

![](https://img-blog.csdnimg.cn/20190528214548574.png)

![](https://img-blog.csdnimg.cn/20190528214558681.png)

# 二叉树（binary Tree）

二叉树是n(n>=0)个结点的有限集合，该集合或者为空集（称为空二叉树），或者由一个根结点和两棵互不相交的、分别称为根结点的左子树和右子树组成。


![](https://img-blog.csdnimg.cn/2019052821483629.png)

上图中，有两个二叉树，分别是 编号2和 3。

编号2又是满二叉树

满二叉树：在一棵二叉树中。如果所有分支结点都存在左子树和右子树，并且所有叶子都在同一层上，这样的二叉树称为满二叉树。

满二叉树的特点有：


- 叶子只能出现在最下一层。出现在其它层就不可能达成平衡。
- 非叶子结点的度一定是2。
- 在同样深度的二叉树中，满二叉树的结点个数最多，叶子数最多。



编号3是完全二叉树

**对一颗具有n个结点的二叉树按层编号，如果编号为i(1<=i<=n)的结点与同样深度的满二叉树中编号为i的结点在二叉树中位置完全相同，则这棵二叉树称为完全二叉树。**


就是保证叶子节点的上面层都要达到最大，最低下两层，最后一层的叶子节点都靠左排列


![](https://img-blog.csdnimg.cn/20190528215115835.png)

存储二叉树的方法就是链表和数组，下图是通过链表的方法存储二叉树
![](https://img-blog.csdnimg.cn/20190528215507935.png)
通过数组的方法也可以存储二叉树

![](https://img-blog.csdnimg.cn/20190528215553943.png)

对于非完全二叉树，其实用数组的方法会浪费存储空间

![](https://img-blog.csdnimg.cn/20190528215743499.png)

二叉树具备以下数学性质：
- 在二叉树的第i层上至多有$2^(i-1)$个结点（i>0）
- 深度为k的二叉树至多有$2^k - 1$个结点（k>0）
- 对于任意一棵二叉树，如果其叶结点数为N0，而度数为2的结点总数为N2，则$N0=N2+1$;
- 具有n个结点的完全二叉树的深度必为 $log2(n+1)$




# 二叉树的遍历

二叉树的遍历是指从二叉树的根结点出发，按照某种次序依次访问二叉树中的所有结点，使得每个结点被访问一次，且仅被访问一次。




- 中序遍历：先左子树，再根节点，最后右子树
- 前序遍历：先根节点，再左子树，最后右子树
- 后序遍历：先左子树，再右子树，最后根节点。

前序遍历通俗的说就是从二叉树的根结点出发，当第一次到达结点时就输出结点数据，按照先向左在向右的方向访问。

中序遍历就是从二叉树的根结点出发，当第二次到达结点时就输出结点数据，按照先向左在向右的方向访问。

后序遍历就是从二叉树的根结点出发，当第三次到达结点时就输出结点数据，按照先向左在向右的方向访问。



![](https://img-blog.csdnimg.cn/20190528215926380.png)




删除共有三种情况

- 被删除的节点是叶子节点，这时候只要把这个节点删除，再把指向这个节点的父节点指针置为空就行

-  被删除的节点有左子树，或者有右子树，而且只有其中一个，那么只要把当前删除节点的父节点指向被删除节点的左子树或者右子树就行。

- 如果要删除的节点有两个子节点，需要找到这个节点的右子树的最小节点，把它替换到要删除的节点上，然后再删除掉这个最小节点，因为最小节点肯定没有左子节点

![](https://img-blog.csdnimg.cn/20190528221128581.png)
# 实现二叉树


上面就是二叉树全部内容，下面用Pytho代码具体实现二叉树。







按下来就是编程实现了，请动手自己实现一把。

先实现一个 node 类：

```cpp
class Node(object):
    def __init__(self, item):
        self.item = item
        self.left = None
        self.right = None

    def __str__(self):
        return str(self.item)
```


这里的 `__str__` 方法是为了方便打印。在 print 一个 Node 类时会打印` __str__ `的返回值,例如：print(Node(5)) 就会打印出字符串 5 。

实现一个二叉树类：



```cpp
class Tree(object):
    def __init__(self):
        # 根节点定义为 root 永不删除，做为哨兵使用。
        self.root = Node('root')

    def add(self, item):
        node = Node(item)
        if self.root is None:
            self.root = node
        else:
            q = [self.root]

            while True:
                pop_node = q.pop(0)
                if pop_node.left is None:
                    pop_node.left = node
                    return
                elif pop_node.right is None:
                    pop_node.right = node
                    return
                else:
                    q.append(pop_node.left)
                    q.append(pop_node.right)

    def get_parent(self, item):
        '''
        找到 Item 的父节点
        '''
        if self.root.item == item:
            return None  # 根节点没有父节点
        tmp = [self.root]
        while tmp:
            pop_node = tmp.pop(0)
            if pop_node.left and pop_node.left.item == item:
                return pop_node
            if pop_node.right and pop_node.right.item == item:
                return pop_node
            if pop_node.left is not None:
                tmp.append(pop_node.left)
            if pop_node.right is not None:
                tmp.append(pop_node.right)
        return None

    def delete(self, item):
        '''
        从二叉树中删除一个元素
        先获取 待删除节点 item 的父节点
        如果父节点不为空，
            判断 item 的左右子树
            如果左子树为空，那么判断 item 是父节点的左孩子，还是右孩子，如果是左孩子，将父节点的左指针指向 item 的右子树，反之将父节点的右指针指向 item 的右子树
            如果右子树为空，那么判断 item 是父节点的左孩子，还是右孩子，如果是左孩子，将父节点的左指针指向 item 的左子树，反之将父节点的右指针指向 item 的左子树
            如果左右子树均不为空，寻找右子树中的最左叶子节点 x ，将 x 替代要删除的节点。
        删除成功，返回 True
        删除失败, 返回 False

        '''
        if self.root is None:  # 如果根为空，就什么也不做
            return False

        parent = self.get_parent(item)
        if parent:
            del_node = parent.left if parent.left.item == item else parent.right  # 待删除节点
            if del_node.left is None:
                if parent.left.item == item:
                    parent.left = del_node.right
                else:
                    parent.right = del_node.right
                del del_node
                return True
            elif del_node.right is None:
                if parent.left.item == item:
                    parent.left = del_node.left
                else:
                    parent.right = del_node.left
                del del_node
                return True
            else:  # 左右子树都不为空
                tmp_pre = del_node
                tmp_next = del_node.right
                if tmp_next.left is None:
                    # 替代
                    tmp_pre.right = tmp_next.right
                    tmp_next.left = del_node.left
                    tmp_next.right = del_node.right

                else:
                    while tmp_next.left:  # 让tmp指向右子树的最后一个叶子
                        tmp_pre = tmp_next
                        tmp_next = tmp_next.left
                    # 替代
                    tmp_pre.left = tmp_next.right
                    tmp_next.left = del_node.left
                    tmp_next.right = del_node.right
                if parent.left.item == item:
                    parent.left = tmp_next
                else:
                    parent.right = tmp_next
                del del_node
                return True
        else:
            return False

    def traverse(self):  # 层次遍历
        if self.root is None:
            return None
        q = [self.root]
        res = [self.root.item]
        while q != []:
            pop_node = q.pop(0)
            if pop_node.left is not None:
                q.append(pop_node.left)
                res.append(pop_node.left.item)

            if pop_node.right is not None:
                q.append(pop_node.right)
                res.append(pop_node.right.item)
        return res

    def preorder(self, root):  # 先序遍历
        if root is None:
            return []
        result = [root.item]
        left_item = self.preorder(root.left)
        right_item = self.preorder(root.right)
        return result + left_item + right_item

    def inorder(self, root):  # 中序序遍历
        if root is None:
            return []
        result = [root.item]
        left_item = self.inorder(root.left)
        right_item = self.inorder(root.right)
        return left_item + result + right_item

    def postorder(self, root):  # 后序遍历
        if root is None:
            return []
        result = [root.item]
        left_item = self.postorder(root.left)
        right_item = self.postorder(root.right)
        return left_item + right_item + result
```
运行测试：

```cpp
if __name__ == '__main__':
    t = Tree()
    for i in range(10):
        t.add(i)
    print('层序遍历:', t.traverse())
    print('先序遍历:', t.preorder(t.root))
    print('中序遍历:', t.inorder(t.root))
    print('后序遍历:', t.postorder(t.root))

    for i in range(10):
        print(i, " 的父亲", t.get_parent(i))

    for i in range(0, 15, 3):
        print(f"删除 {i}", '成功' if t.delete(i) else '失败')
        print('层序遍历:', t.traverse())
        print('先序遍历:', t.preorder(t.root))
        print('中序遍历:', t.inorder(t.root))
        print('后序遍历:', t.postorder(t.root))
```
执行结果如下：


```cpp
层序遍历: ['root', 0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
先序遍历: ['root', 0, 2, 6, 7, 3, 8, 9, 1, 4, 5]
中序遍历: [6, 2, 7, 0, 8, 3, 9, 'root', 4, 1, 5]
后序遍历: [6, 7, 2, 8, 9, 3, 0, 4, 5, 1, 'root']
0  的父亲 root
1  的父亲 root
2  的父亲 0
3  的父亲 0
4  的父亲 1
5  的父亲 1
6  的父亲 2
7  的父亲 2
8  的父亲 3
9  的父亲 3
删除 0 成功
层序遍历: ['root', 8, 1, 2, 3, 4, 5, 6, 7, 9]
先序遍历: ['root', 8, 2, 6, 7, 3, 9, 1, 4, 5]
中序遍历: [6, 2, 7, 8, 3, 9, 'root', 4, 1, 5]
后序遍历: [6, 7, 2, 9, 3, 8, 4, 5, 1, 'root']
删除 3 成功
层序遍历: ['root', 8, 1, 2, 9, 4, 5, 6, 7]
先序遍历: ['root', 8, 2, 6, 7, 9, 1, 4, 5]
中序遍历: [6, 2, 7, 8, 9, 'root', 4, 1, 5]
后序遍历: [6, 7, 2, 9, 8, 4, 5, 1, 'root']
删除 6 成功
层序遍历: ['root', 8, 1, 2, 9, 4, 5, 7]
先序遍历: ['root', 8, 2, 7, 9, 1, 4, 5]
中序遍历: [2, 7, 8, 9, 'root', 4, 1, 5]
后序遍历: [7, 2, 9, 8, 4, 5, 1, 'root']
删除 9 成功
层序遍历: ['root', 8, 1, 2, 4, 5, 7]
先序遍历: ['root', 8, 2, 7, 1, 4, 5]
中序遍历: [2, 7, 8, 'root', 4, 1, 5]
后序遍历: [7, 2, 8, 4, 5, 1, 'root']
删除 12 失败
层序遍历: ['root', 8, 1, 2, 4, 5, 7]
先序遍历: ['root', 8, 2, 7, 1, 4, 5]
中序遍历: [2, 7, 8, 'root', 4, 1, 5]
后序遍历: [7, 2, 8, 4, 5, 1, 'root']
```



Binarytree是一个Python库，它通过一个简单的API生成二叉树，可以进行检查和操作。Github：https://github.com/joowani/binarytree/releases。


![](https://img-blog.csdnimg.cn/20200705112838888.png)
