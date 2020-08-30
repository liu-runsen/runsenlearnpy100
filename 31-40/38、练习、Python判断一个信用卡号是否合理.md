@Author: Runsen

这个一个编程题

一个信用卡号必须是13到16位的整数



1954年，IBM的Hans Luhn提出一种算法，用于验证信用卡号的有效性。

这个算法在确定输入的卡号是否正确，或者这张信用卡是否被扫描仪正确扫描方面是非常有用的。




- **4，指Visa信用卡**  
- **5，指Master万事达卡**
- **37，指American Express 国际信用卡**
- **6，指Discover 信用卡**



遵循这个合法性检测可以生成所有的信用卡号，通常称之为Luhn检测或者Mod 10检测，可以如下描述（为了方便解释，假设卡号4388576018402626：

1.从右到左对偶数位数字翻倍。如果对某个数字翻倍之后的结果是一个两位数，那么就将这两位加在一起得到一位数。


![](https://img-blog.csdnimg.cn/20200330100745345.png)

2.现在将第一步得到的所有一位数相加。



![](https://img-blog.csdnimg.cn/20200330100753832.png)

3.将卡号里从右到左奇数位上的所有数字相加。


![](https://img-blog.csdnimg.cn/20200330100806932.png)







4.将第二步和第三步得到的结果相加。




![](https://img-blog.csdnimg.cn/20200330100818162.png)




5.如果第四步得到的结果能被10整除，那么卡号是合法的；否则，卡号是不合法的。

![](https://img-blog.csdnimg.cn/20200330100831819.png)

例如，号码4388576018402626是不合法的，但是号码4388576018410707是合法的。
编写程序，提示用户输入一个long型整数的信用卡号码，显示这个数字是合法的还是非法的


![](https://img-blog.csdnimg.cn/20200330100841306.png)


## 代码

```python
def isValid(number):
    # 判断是不是合法，就是计算出第四步的结果，如果整除就是合法，我们取模就可以了
    if sumOf0ddPlace(number) % 10 == 0:
    	print("信用卡号的合法")
    else:
    	print("信用卡号的不合法")

def sumOfDoubleEvenPlace(number):
	# 现在将第一步得到的所有一位数相加。这里的number传入的是int类型
	sum = 0 
	for i in str(number)[::2]:
		if int(i)*2 <10:
			sum = sum + int(i)*2
		else:
			for j in str(int(i)*2):
				sum = sum + int(j)
	return sum 

def getDigit(number):
	return sum([int(i) for i in str(number)[1::2]])

def sumOf0ddPlace(number):
	return sumOfDoubleEvenPlace(number) + getDigit(number)



number = input("用户输入一个的信用卡号码，必须是13到16位的整数")
isValid(number)

# 验证
用户输入一个的信用卡号码，必须是13到16位的整数4388576018402626
信用卡号的不合法
用户输入一个的信用卡号码，必须是13到16位的整数4388576018410707
信用卡号的合法
```







# 补充

添加  prefixMatched，判断卡号的前缀是否合法。


4，指visa卡
5，指master卡
37，指American Express卡
6，指Discovery卡



```css
def prefixMatched(number):
    if number[0] == '4' or number[0] == '5' or number[0] == '37':
        print("信用卡前缀的合法")
    elif number[:2] == '37':
        print("信用卡前缀的合法")
    else:
        print("信用卡前缀的不合法")
```





函数6：def getSize(d):   获得信用卡号的长度并将结果返回

```css
def getSize(d):
    return number[:d]
```



函数7：def getPrefix(number, k): 获得信用卡号的第k位'''


```css
def getPrefix(number, k):
    return number[k]
```

