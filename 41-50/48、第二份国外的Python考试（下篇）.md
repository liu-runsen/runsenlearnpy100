@Author：Runsen
@Date：2020/5/26

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。




@[TOC]

# 第五题


![](https://img-blog.csdnimg.cn/20200527111432148.png)

归并排序和快速排序在最佳情况下都具有$O（n logn）$时间复杂性。然而，其中一个算法的最坏情况复杂度为$O(n^2)$。说明哪些算法的时间复杂度为$O(n^2)$，并简要解释为什么


答案是快速排序
![](https://img-blog.csdnimg.cn/20200527111040603.png)


 快速排序具有最好的平均性能（average behavior），但最坏性能（worst case behavior）和插入排序

相同，也是$O(n^2)$。比如一个序列5,4,3,2,1，要排为1,2,3,4,5。按照快速排序方法，每次只会有一个数据进入正确顺序，不能把数据分成大小相当的两份，很明显，]时间复杂度就成了O(n^2)。






第二题

![](https://img-blog.csdnimg.cn/20200527111409799.png)


在对冒泡排序、选择排序和插入排序的外部循环进行三次迭代之后，下面使用哪种排序


第一个很明显选择排序，选择排序在未排序序列中找到最小（大）元素，存放到排序序列的起始位置。



第三个很明显冒泡排序，


那么第二个很明显插入排序




![](https://img-blog.csdnimg.cn/20200527112109255.png)

第三题，其实就是一个二分查找，只不过变成了查找对应的字符串，变汤不变药，问题就是当count等于2时候，那么对应的mid，higth，low。



第一，len(collection) = 10，一开始mid等于4，然后不对，直接low等于5，count等于1，接着mid等于7，不对，直接low等于8，count等于2，

因此答案是mid等于7，higth等于9，low等于8。




# 最后一题

![](https://img-blog.csdnimg.cn/20200527122433768.png)


（20分）你被委托写一个简单的游戏卡游戏称为考试扑克。这场比赛是用一套标准的扑克牌进行的。在您的游戏中，卡片将被表示为（等级，套装）元组的列表。注意数字11-13代表杰克、王后、国王，而我代表王牌。西装（黑桃钻石、红桃和梅花）用一个字母表示。我们将把这些卡片存储在一个叫做deck的全局抖动结构中。您可以假设在您的程序中定义了以下内容


SCDH就是扑克牌的四种类别，一共有52张扑克牌





玩家最初获得5张牌。然后，他们还有三个（可选）回合，目标是实现以下其中一个



其中通俗的来说，就是现在你有五张牌，打牌的时候，怎么可以出五张牌，顺子可以打出去，三带二可以打出去，还有就是锄大地的同一种花色可以打出去。最后，通过五张牌的总和作为得分。你可以换牌。







![](https://img-blog.csdnimg.cn/20200527122502815.png)

![](https://img-blog.csdnimg.cn/20200527123008596.png)







![](https://img-blog.csdnimg.cn/20200527123654834.png)


这个代码写了我快一个小时，真的很多细节注意
```css
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/5/21
'''
import random
# 定义一副未洗的牌[0, 1....51]
porks = [i for i in range(52)]
# 定义花色
# 方片D(Diamonds) 梅花C(Clubs)  红桃H(heart)  黑桃S(spade)
suits = ['D', 'C', 'H', 'S']
# 定义编号
ranks = ['1', '2', '3', '4', '5', '6', '7', '8',
         '9', '10', '11', '12', '13']
s = 0
def get_porks(mylist):
    # 随机生成一牌，但是要求不能在之前的出现
    pork = random.choice(ranks) +  random.choice(suits)
    if pork in mylist:
        # 出现重新生成一牌
        return get_porks(mylist)
    else:
        return pork

def get_five_porks():
    mylist = []
    for i in range(52):
        # 随机得到0-51整数随机数
        randomIndex = random.randint(0, 51)
        # 交换
        porks[i], porks[randomIndex] = porks[randomIndex], porks[i]
    for i in range(5):
        suit = suits[porks[i] // 13]
        rank = ranks[porks[i] % 13]
        mylist.append(str(rank + suit))
    return mylist

def change_porks(mylist):
    # 需不需要换牌

    global s
    print(mylist,s)
    Change = input("Change some cards：y or n： ")
    if Change == "y":
        keep = input("Indicate which cards you wish to keep ：")
        for index,i in enumerate(keep):
            if i == '0':
                # 换牌
                pork = get_porks(mylist)
                print(pork)
                mylist.insert(index, pork)
                # 在删除之后的下一个
                mylist.pop(index+1)
        print("You now have："+ str(mylist))
        change_porks(mylist)
    else:
        # 计算分数
        for i in mylist:
            print(i)
            s += int(i[:-1])
        print("Your total score is now：" +str(s))
        return s


def teststraightchecker():
    global s
    mylist = get_five_porks()
    print("Here is your first hand：" + str(mylist))
    change_porks(mylist)
    choice = input("Would you like to play again (y or n) ：")
    if choice == 'y':
        teststraightchecker()
    else:
        print("Thank you for playing")

if __name__ == '__main__':
    teststraightchecker()
```


![](https://img-blog.csdnimg.cn/20200527214817516.png)

```css
Here is your first hand：['11D', '13H', '3H', '6C', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11001
You now have：['11D', '13H', '3S', '7D', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11001
You now have：['11D', '13H', '11H', '8S', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11101
You now have：['11D', '13H', '11H', '6H', '12C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11100
You now have：['11D', '13H', '11H', '13C', '6C']
Change some cards：y or n： y
Indicate which cards you wish to keep ：11110
You now have：['11D', '13H', '11H', '13C', '13S']
Change some cards：y or n： n
Your total score is now：61
Would you like to play again (y or n) ：n
Thank you for playing
```

