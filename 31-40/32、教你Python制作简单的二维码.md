@Author：Runsen
@[toc]



# 安装MyQR

cmd 窗口中用 pip 命令安装
```
pip install MyQR
```


这个库提供了两种使用方法，一种是直接使用命令行的方式，另外一种使用import引入

先在最原始的IDE上
```
from MyQR import myqr
myqr.run('1234567')
```

![](https://img-blog.csdnimg.cn/20190425123522141.png)

在看下源码
![](https://img-blog.csdnimg.cn/20190425123316449.png)

位置参数
单词：STR

可选参数
版本：int，从1到40

级别：str，仅限其中一个（l'、'm'、'q'、'h'）

picutre:str，图像的文件名

着色：布尔

constrast:浮动

亮度：浮动

保存“name:str”，输出文件名如“example.png”

save_dir:str，输出目录

![](https://img-blog.csdnimg.cn/20190425131139766.png0)


```
from MyQR import myqr
myqr.run(words='123456',picture='1.jpg',save_name='demo.png',colorized=True)
```

![](https://img-blog.csdnimg.cn/20190425124718125.png)



# 动图

```
from MyQR import myqr
myqr.run(words='https://www.baidu.com',picture='1.gif',save_name='demo1.gif',colorized=True)
```
![](https://img-blog.csdnimg.cn/20190425125335676.gif)


第二种cmd下的方法

参数
```shell
'''
myqr     Words
        [-v {1,2,3,...,40}]
        [-l {L,M,Q,H}]
        [-n output-filename]
        [-d output-directory]
        [-p picture_file]
        [-c]
        [-con contrast]
        [-bri brightness]
'''
```


-v 参数是控制二维码边长的，范围 1至40，数字越大边长越大；

-l 控制纠错水平，范围是L、M、Q、H，从左到右依次升高。默认纠错等级是最高级的H。

-n 控制文件名，格式可以是 .jpg， .png ，.bmp ，.gif ；

-d 控制位置，控制二维码图片的保存位置。

-p 参数可以把原二维码和同目录下另一张图片结合形成新的黑白艺术二维码。

-con 用以调节图片的对比度，1.0 表示原始图片，更小的值表示更低对比度，更大反之。默认为1.0。

-bri 用来调节图片的亮度，其余用法和取值与 -con 相同。


![](https://img-blog.csdnimg.cn/20190425125634355.png)

![](https://img-blog.csdnimg.cn/2019042512570917.png)



![](https://img-blog.csdnimg.cn/20190425125721429.png)


![](https://img-blog.csdnimg.cn/20190425130043254.png)


![](https://img-blog.csdnimg.cn/2019042513010215.gif)

![](https://img-blog.csdnimg.cn/20190425130513425.png)


![](https://img-blog.csdnimg.cn/20190425130523197.png)


# 搜索范冰冰


```python
from MyQR import myqr
myqr.run(words='https://www.baidu.com/s?wd=%E8%8C%83%E5%86%B0%E5%86%B0&rsv_spt=1&rsv_iqid=0xa48f245a0000d799&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf8&tn=baiduhome_pg&rsv_enter=1&rsv_sug3=12&rsv_sug1=10&rsv_sug7=100&rsv_t=b7
a30UsfuYzvKe8JVKCYqvrCF%2FVdbjT%2B0viM0p7fh8j%2BUKcUaEJF%2FTojpsWfmTDc%2FL5s&rsv_sug2
=0&inputT=3459&rsv_sug4=3459&rsv_sug=1',picture='2.png',save_name='demo1.png',colorized=True)
```



![](https://img-blog.csdnimg.cn/20190425132652811.png)


出现的问题：cannot write mode RGBA as JPEG


原因：RGBA意思是红色，绿色，蓝色，Alpha的色彩空间，Alpha指透明度。而JPG不支持透明度，所以要么丢弃Alpha,要么保存为.png文件


```python
from PIL import Image
image = Image.open('2.jpg')
# image = image.convert("RGB") 
image.save("2.png")
```
