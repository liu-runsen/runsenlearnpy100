
@Author：Runsen
@Date：2020/5/26

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


之前撸了一份国外的Python考试题目，那个留学生还有一份，我接着继续撸。走，看看国外的Python考试题到底是什么东西？


@[toc]

![](https://img-blog.csdnimg.cn/20200524163744996.png)

满分55分，之前的是70，不知道什么回事，撸就对了。



# 第一题


![](https://img-blog.csdnimg.cn/20200526182922726.png)


第一题很明显就是一个时间复杂度的题目，一个快速排序，一个链表查找，一个冒泡排序，一个链表插入，一个二叉搜索，一个访问Python列表中的单个元素。







![](https://img-blog.csdnimg.cn/20200527094912912.png)

快速排序$Onlogn)$，链表查找$On)$，冒泡排序$On^2)$，链表插入$O(1)$，二叉搜索$O(Logn)$
访问Python列表中的单个元素$O(1)$。



Python列表做元素的遍历、删除、插入等操作，对应的时间复杂度为O(n)；访问某个索引的元素、尾部添加元素或删除元素这些操作比较适合做，对应的时间复杂度为O(1)。




![](https://img-blog.csdnimg.cn/20200527100100585.png)

答案我不知道，没有标准答案。





![](https://img-blog.csdnimg.cn/20200527100151854.png)

第二题是指出函数的时间复杂性


三个循环，但是结尾是一个n//4，应该是$O(nlogn)$，因为`for i in range(10)`这个是$O(1)$



![](https://img-blog.csdnimg.cn/20200527101032924.png)


二个循环，应该是$O(n^2)$


# 第二题


![](https://img-blog.csdnimg.cn/20200527101155993.png)

打印出什么，2*fizbin(6,10)，然后就是4*fizbin(3,5)，答案就是4。



![](https://img-blog.csdnimg.cn/20200527101439234.png)

一开始mid等于2，left = mysteryFun([1,0]) =  mysteryFun([1]) +mysteryFun([0]) = 1


right =  mysteryFun([2，3]) =  mysteryFun([2]) +mysteryFun([3]) = 4+9=13

答案14。


如果mysteryFun([0,1])，运行3次。









![](https://img-blog.csdnimg.cn/20200527102542313.png)


写一个函数应该返回一个由列表中所有字符串组成的字符串，这些字符串以一个空格分隔的给定字符开头，用字符决定排序的列表。


难度一般，


```css
def alliterationMaker(alist,char):
    # 对alist的开头不是char的去除
    for i in alist:
        if i[0] != char:
            alist.pop(alist.index(i))
    alist.sort()
    return alist

if __name__ == '__main__':
    print(alliterationMaker(["big","cow","bug","bit","table","black","bear"],"b"))
    
['bear', 'big', 'bit', 'black', 'bug']
```
# 第三题

![](https://img-blog.csdnimg.cn/20200527104040275.png)


就是把从大到小，6，5，4，2，2，然后再全部加一，7，6，5，3，3.再反转，3，3，5，6，7


![](https://img-blog.csdnimg.cn/2020052710452826.png)


答案8，7，6，25


# 第四题
![](https://img-blog.csdnimg.cn/20200527105249730.png)

二叉树的遍历是指从二叉树的根结点出发，按照某种次序依次访问二叉树中的所有结点，使得每个结点被访问一次，且仅被访问一次，分别有前序遍历，中序遍历，后序遍历


前序遍历通俗的说就是从二叉树的根结点出发，当第一次到达结点时就输出结点数据，按照先向左在向右的方向访问。

中序遍历就是从二叉树的根结点出发，当第二次到达结点时就输出结点数据，按照先向左在向右的方向访问。

后序遍历就是从二叉树的根结点出发，当第三次到达结点时就输出结点数据，按照先向左在向右的方向访问。

![](https://img-blog.csdnimg.cn/20190528215926380.png)

选项A就是后序遍历 正确
选项B就是前序遍历 但是错误
选项C就是前序遍历 正确
选项D什么遍历都不是，错误
选项E什么遍历都不是，错误
![](https://img-blog.csdnimg.cn/20200527110144387.png)

当输入是上面显示的树时，显示以下代码打印的内容。


这个真的不知道写什么，就是不断地分解子树，打印出来
