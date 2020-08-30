@Author：Runsen
@Date：2020/6/19

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）




作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。
前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)


今天介绍的是Python中的爬虫小例子，离收官还有八篇。


@[TOC]



# 1、前言


在某日夏天的夜晚、突然有妹子加我微信，原来竟然叫我帮忙写作业。




![](https://img-blog.csdnimg.cn/20200628124023811.png)



对于，我这个屌丝来说，还是花个半小时帮忙搞定下。爬取的网站又是链家网，你看我直接不是早已写成博客了吗？

![](https://img-blog.csdnimg.cn/20200628124340804.png)


我想对链家网说：链家网求你不要再害大家爬你的，真的让广大学生都是讨厌你。

爬取的链接是：https://sz.lianjia.com/zufang/

![](https://img-blog.csdnimg.cn/20200628124603502.png)

什么租房经纪人成交数据有吗？我看老师都是傻傻的不知道乱搞一通。难为是我啊？没有的东西爬了毛？


# 2、明确爬取的信息

在链家网的租房信息中，有如下的信息，我都圈出来了。
![](https://img-blog.csdnimg.cn/2020062812485470.png)

明确爬取的信息，分别有整租，我就叫类型算了。新城花园就叫名称， 面积就是101，朝向南，

3室1厅1卫就叫房间数，价格每个月1800，真贵。反正我这种穷人要不起。





# 3、 Requests访问链接


Requests库就是发请求的库，需要加上请求头，这样就不用禁止了。


根据每个页面的网址发现就是换了一个pg参数。比如，第一页的网址是`https://sz.lianjia.com/zufang/pg0`，

那么第二页就是`https://sz.lianjia.com/zufang/pg1`，那么就是傻瓜式构造。我们爬它个100页，代码如下。





```java
for i in range(1, 101):
     page_url = 'https://sz.lianjia.com/zufang/pg{}'.format(i)
     res = requests.get(page_url, headers=headers)
```

# 4、 xpath解析内容

返回的页面就需要解析，我经常用的说xpath，至于bs4赶紧忘记算了。



具体解析过程如下图所示。


![](https://img-blog.csdnimg.cn/20200628183147843.png)



# 5、保存数据
我们选择用csv来保存数据，通过`with open('demo.csv', 'a+') as f`进行创建csv，然后通过`f.write`进行写入爬取的数据。


最终保存数据如下图所示。
![](https://img-blog.csdnimg.cn/20200628183414740.png)


# 6、全部代码



```python
'''
@Author： Runsen
@微信公众号： 润森笔记
@博客： https://blog.csdn.net/weixin_44510615
@Date： 2020/6/27
'''
import requests
from lxml import etree

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/77.0.3865.90 Safari/537.36'
}
with open('demo.csv', 'a+') as f:
    f.write(
        '类型' + ',' + '名称' + ',' + '地点' + ',' + '面积' + ',' + '朝向' + ',' + '房间数' + ',' + '价格' + '\n')
    for i in range(1, 101):
        page_url = 'https://sz.lianjia.com/zufang/pg{}'.format(i)

        res = requests.get(page_url, headers=headers)
        # 这里千万不要判断res的状态码200
        page = etree.HTML(res.text)
        content = page.xpath("//a[@class='content__list--item--aside']/@title")

        where1 = page.xpath("//p[@class='content__list--item--des']/a[1]/text()")
        where2 = page.xpath("//p[@class='content__list--item--des']/a[2]/text()")
        where3 = page.xpath("//p[@class='content__list--item--des']/a[3]/text()")
        squares = page.xpath("//p[@class='content__list--item--des']/text()[5]")
        decorates = page.xpath("//p[@class='content__list--item--des']/text()[6]")
        nums = page.xpath("//p[@class='content__list--item--des']/text()[7]")
        Prices = page.xpath("//span[@class='content__list--item-price']/em/text()")
        for j,w1,w2 , w3,s,d, n, Price in zip(content, where1, where2,where3, squares, decorates,nums,Prices):
            type = j.replace("·", " ").split(" ")[0]
            name = j.replace("·", " ").split(" ")[1]
            location = w1+ w2 + w3
            square = s.replace("\n", "").replace(" ", "")
            decorate =d.replace(" ", "")
            num = n.replace("\n", "").replace(" ", "")
            price = Price+ "元/月"
            print("正在写入 :" + type + ',' + name + ',' + location + ',' + square + ',' + decorate + ',' + num + ',' + price +  '\n')
            f.write(type + ',' + name + ',' + location + ',' + square + ',' + decorate + ',' + num + ',' + price +  '\n')
```






