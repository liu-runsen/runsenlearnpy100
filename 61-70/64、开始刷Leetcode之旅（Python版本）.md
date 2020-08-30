@Author：Runsen

@Date：2020/6/4

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。



从大一写Python文章，到现在其都有上百篇，现在到了六十四，我觉得这个时候应该去刷题了，其实很多学Python的都不是专科的，都是给培训机构宣传牛逼，其实在编程语言中，Python是最简单，最没有难度的编程语言。我在之后的文章都更新数据结构和Leetcode。都用Python解决的方法。其实Leetcode上的一部分题我都基本刷过，那么我就开始吧。




@[toc]


# 注册Leetcode账号


目前Leetcod有国际和中文的两个版本，下图就是我的中文版本，刷的不够，其实我也挺菜的。这个是中文的网址：https://leetcode-cn.com/problemset/all/
![](https://img-blog.csdnimg.cn/20200605154056199.png)

下图就是我的国际版本，其实我主要在国际版混日子，刷了100多题，其实我很菜的。这是它的官网，https://leetcode.com。
![](https://img-blog.csdnimg.cn/20200605154019683.png)


不同点，非中国区的人多点，做完了也可以参考下老外是用什么思路做的，挺好的。所以你比要到非中国区，看看老外是怎么干的。



# Pycharm装Leetcode插件


直接打开Pycharm，依次点击File-Settings-Plugins-Maketplace ，然后在搜索框输入leetcode，就会显示我们的leetcode editor插件,点击Install，跳出的界面点检accept,之后等待安装好就行了


我这个是安装好的了。
![](https://img-blog.csdnimg.cn/20200605155930517.png)

如果你用vscode也是一样，给我装vscode插件。

![](https://img-blog.csdnimg.cn/20200605160057766.png)

因为，我习惯Python用Pycharm，Java用IDEA，前端用vscode。所以这Runsen使用Pycharm。



然后就是登陆我的Leetcode账号。

![](https://img-blog.csdnimg.cn/20200605160401821.png)

然后就是登录你的账号。

![](https://img-blog.csdnimg.cn/20200605160506779.png)



点击右下角，选择刷新或者加载按钮，就可以获取到leetcode中题库了，根据颜色可以区分题目的难易程度:
绿色-中等；
黄色-简单;
红色-困难


![](https://img-blog.csdnimg.cn/20200605160638614.png)

更详细的使用说明参考文档:https://github.com/shuzijun/leetcode-editor


# 怎么刷Leetcode
## 以前菜鸡的我做法
以前Runsen的做法：
1. 打开leetcode
2. 启动Pycharm
3. 开始思考，冷静分析
4. 打开leetcode官网的评论区答案，寻找跟我一样的菜逼
5. 满意离开评论区


上面其实都是像之前的我，都是菜鸡，其实现在我还是菜鸡。

## 分类归纳/总结
刷Leetcode，必须分类归纳/总结

（1）、数组和相关题型

对于算法题，还是有很多种题型需要去总结的，如果你懂这个题型，以后遇到类似的题，相信很快就能做出来的。有哪些题型可以总结呢？答是非常多，例如：

（1）、给你一个非负数的数组，求最大子数组和的长度

这算是一个题型，关于这个题型，有很多种变形、拓展，这里建议一起归纳总结，例如：

（2）、刚才给的数组是非负数的，现在变一下，给的数组是可正可负。

还能继续拓展吗？答是可以的，例如：

（3）、给你个矩阵（即二维数组），求最大子矩阵和的面积

还有吗？有，例如刚才是求最大和，现在我改成求最大乘积。

我其实是想告诉你，对于前期的学习，我建议分类刷题，总结题型，像我上面举的这些例子，遇到相似的，就直接可以秒杀了，因为这类题，没啥边界或者规律。


关于题型的，还是很多的，我这里无法一一给你列举，只能靠你刷题的过程中，进行分类、总结。不过我可以给你推荐一些资料，后面推荐。下面我在说一些题型吧。


## 三分学七分练

三分学七分练，这是我从极客时间的覃超，前Facebook工程师，传授的方法。


![](https://img-blog.csdnimg.cn/20200605161852501.png)



俗话说：学钢琴，三分学，七分练。其中练习是最为重要的一个环节，想学好钢琴必须得时常练习且多多益善。



所以刷Leetcode的最大的弊端都是：缺乏练习。



# 两数相加

那么我们就开始干他，Leetcode中的Hello World就是两数相加。


这个题是我2018年遇见了，现在2020年半，两年多时间。


```python
#给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。 
#
# 你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。 
#
# 示例: 
#
# 给定 nums = [2, 7, 11, 15], target = 9
#
#因为 nums[0] + nums[1] = 2 + 7 = 9
#所以返回 [0, 1]
# 
# Related Topics 数组 哈希表

```


其实这一题真的很简单，无非就是将“昂贵”的时间复杂度转换成“廉价”的空间复杂度，把双重遍历，变成一次遍历。

这里最佳的方法就是使用字典。下面是我去年的代码，就是三种的解决方法。


列表解法
```
def twoSum_1( nums, target):
    result = []
    for i in range (len(nums)):
        onenum = nums[i]
        twonum = target - onenum
        if twonum in nums:
            j = nums.index(twonum)
            if i != j:
                result.append(i)
                result.append(j)
                return result
```
字典解法
```
def twoSum_2(nums,target):
    dict={}
    for i in range(len(nums)):
        m = nums[i]
        if target-m in dict:
            return [dict[target-m],i]
        dict[m] = i
```
字典推导式
```
def twosum_3(nums,target):
    l = len(nums)
    dict = {nums[i]:i for i in range(l)}
    print(dict)
    for j in range(l):
        a = nums[j]
        b = target - a
        if b in dict and j != dict[b]:
            return [j,dict[b]]
```



# 关于学习课程



在之前深入Leetcode，学了下面的课程

![](https://img-blog.csdnimg.cn/2020060516351882.png)
![](https://img-blog.csdnimg.cn/20200605163542636.png)


![](https://img-blog.csdnimg.cn/20200605163457240.png)


因此下面的文章主要是总结回顾之前学到东西，只有不断地反复学习，才有新的突破












