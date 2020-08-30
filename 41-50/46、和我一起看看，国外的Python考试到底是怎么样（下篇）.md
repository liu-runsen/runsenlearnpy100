[四十五、国外的Python考试（上篇）](https://blog.csdn.net/weixin_44510615/article/details/106228702)


@Author: Runsen
@Date：2020/5/21


上次，我看了Python考试，前面就是送分玩意，70先拿了50，这还是不及格，虽然我天天挂科，但是有尊严的。跟着我学Python，Java就对了。

@[TOC]




# 第五题


看题，看Runsen怎么解决国外Python考试。
![](https://img-blog.csdnimg.cn/202005212231099.png)


第一题，就是代入法，送分


len一开始是5，然后m等于2，取整除，这样就是 c+ab+de

然后再将ab，de运行一次


ab：2整除是1，得到b，a ，


de：2整除是1，得到e，d ，

答案就是cbaed


我不信，就写代码测试一下

```css
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/21
'''
def fn(a):
    if len(a) <2:
        return  a
    m = len(a) //2
    print(a[m],a[:m],a[m+1:])
    return a[m] + fn(a[:m]) + fn(a[m+1:])

if __name__ == '__main__':
    print(fn('abcde'))

c ab de
b a 
e d 
cbaed
```

和想得一样，简单

![](https://img-blog.csdnimg.cn/20200521223123412.png)

继续代入，其中lo =0，hi=4，m=2.，num[2] = 15，这样就是[1, 2, 15, 4, 5]




fn([1,2,15,4,5],0,1)  ，继续代入m=0，s=3，num[0] =3，就是[3, 2, 15, 4, 5]



```css
# 错误的想法
这是这是把本身的fn运行，在fn还有两个fn。继续代入，fn([3,2,15,4,5],0,0)，其中m=2.，num[0] = 3，无变化。fn([3,2,15,4,5],1,5)，其中m=3，num[0] = 3



这样就是[1, 2, 15, 4, 5]


```





**我终于知道了，这里考的是函数的嵌套**


这题，我真的不会，一个函数再调用两次，直接打印看看，结果是[3, 2, 15, 9, 5]，此题不会，



```css
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/21
'''

def fn(nums,lo,hi):
    if hi < lo:
        return
    m = (lo +hi )//2
    s = 0
    for i in range(lo,hi+1):
        s += nums[i]
    nums[m] = s
    print(nums,lo,m)
    fn(nums,lo , m-1)
    print(nums)
    fn(nums,m+1 , hi)

if __name__ == '__main__':
    test = [1, 2, 3, 4, 5]
    fn(test, 0, len(test)-1)
    print(test)




[1, 2, 15, 4, 5] 0 2
[3

, 2, 15, 4, 5] 0 0
[3, 2, 15, 4, 5]
[3, 2, 15, 4, 5] 1 1
[3, 2, 15, 4, 5]
[3, 2, 15, 4, 5]
[3, 2, 15, 9, 5] 3 3
[3, 2, 15, 9, 5]
[3, 2, 15, 9, 5] 4 4
[3, 2, 15, 9, 5]
[3, 2, 15, 9, 5]

```



![](https://img-blog.csdnimg.cn/20200521223141986.png)








![](https://img-blog.csdnimg.cn/20200521223200423.png)

runsen一开始看这题就是蒙的，然后发现了规律$a[n+1]=a[n]+3^n$


这里还要求递归计算，不能超过四行代码，简单搞定



```css
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/22
'''

def tulip(n):
    if n == 0:
        return 1
    else:
        return tulip(n-1) + 3**n

def main():
    n = int(input('Enter a value for n:'))
    for i in range(n+1):
        print(tulip(i))
main()

Enter a value for n:5
1
4
13
40
121
364
```

# 第六题



第一题
![](https://img-blog.csdnimg.cn/20200522162910746.png)


第一题。问当代码在上面显示的链表上执行时，会打印什么？




小白先看这个
![](https://img-blog.csdnimg.cn/20200522163538501.png)

count=0，ptr  20
count=1，ptr  30

然后2跳出循环，答案到30，也是就10,20,30]，送分






![](https://img-blog.csdnimg.cn/20200522163746415.png)


第二题，这就是傻逼做的，答案[14,18,12,13]。解答没有







![](https://img-blog.csdnimg.cn/20200522164021974.png)


第三题，我的结果是[5,4,9,4]

![](https://img-blog.csdnimg.cn/20200522164348195.png)


考链表的时间复杂度，链表中的元素都会两个属性，一个是元素的值，另一个是指针，此指针标记了下一个元素的地址，每一个数据都会保存下一个数据的内存的地址，通过此地址可以找到下一个数据，任意位置插入元素和删除元素效率较高，时间复杂度为O(1)。随机访问效率低，时间复杂度为0(N)



![](https://img-blog.csdnimg.cn/20200522165427407.png)
我的答案



第一个尾节点加入节点的时间复杂度$O(1)$


第二个确定链表长度的时间复杂度$O(n)$


第三个将链表中的前10个值相加的时间复杂度为$O(1)$

第四个对于已排序的链接列表，搜索不在列表中的值的时间复杂性为$O(n)$


# 第七题




![](https://img-blog.csdnimg.cn/20200522165627577.png)

第一题显示列表值在下面的树中的位置，以形成二叉搜索树。假设节点是按照在原始列表中的出现顺序插入的，从44开始，然后是60，然后是62，依此类推。

取中间作根节点，下图就我的答案






![](https://img-blog.csdnimg.cn/20200522170413407.png)








![](https://img-blog.csdnimg.cn/20200522170727592.png)

第二题。指出树是否表示二叉搜索树（BST），如果树不是二叉搜索树，为什么


二叉搜索树：任意节点的键值一定大于其左子树中的每一个节点的键值，并小于其右子树中的每一个节点的键值。



看我的二叉树

[二叉树（上）](https://maoli.blog.csdn.net/article/details/90648081)


第一个不是，这里错了

![](https://img-blog.csdnimg.cn/20200522171407902.png)


第二个是


第三个不是，因为不是二叉树


至此，这份70分的考卷结束了。我还要一份，继续。
