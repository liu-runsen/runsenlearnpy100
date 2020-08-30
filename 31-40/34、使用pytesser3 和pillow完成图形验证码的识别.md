

@Author: Runsen


@[TOC]



# 灰度化


像素点是最小的图片单元，一张图片由很多像素点构成，一个像素点的颜色是由RGB三个值来表现的，所以一个像素点对应三个颜色向量矩阵，我们对图像的处理就是对这个像素点的操作。

图片的灰度化，就是让像素点矩阵中的每一个像素点满足 R=G=B，此时这个值叫做灰度值，白色为0，黑色为255
灰度转化一般公式为：


`R=G=B = 处理前的 RX0.3 + GX0.59 + B*0.11`


```
from PIL import Image
image = Image.open('code.jpg')
im = image.convert('L')
```


# 二值化


图像的二值化，就是将图像的像素点矩阵中的每个像素点的灰度值设置为0（黑色）或255（白色），从而实现二值化，将整个图像呈现出明显的只有黑和白的视觉效果。

二值化原理是利用设定的一个阈值来判断图像像素是0还是255， 一般小于阈值的像素点变为0， 大于的变成255

这个临界灰度值就被称为阈值，阈值的设置很重要，阈值过大或过小都会对图片造成损坏

选择阈值的原则是：既要尽可能保存图片信息，又要尽可能减少背景和噪声的干扰


常用阈值选择的方法是：


- 灰度平局值法： 取127 （0~255的中数， （0+255）/2 = 127）

- 平均值法：

计算像素点矩阵中的所有像素点的灰度值的平均值avg
        
- 迭代法：

选择一个近似阈值作为估计值的初始值，然后进行分割图像，根据产生的子图像的特征来选取新的阈值，在利用新的阈值分割图像，经过多次循环，使得错误分割的图像像素点降到最小。


# 降噪
经过了二值化处理，整个图片像素就被分为了两个值0和255.

如果一个像素点是图片或者干扰因素的一部分，那么她的灰度值一定是0（黑色），如果一个点是背景，其灰度值应该是255，白色

所以对于孤立的噪点，他的周围应该都是白色，或者大多数点都是白色的，所以在判断的时候条件应该放宽，一个点是黑色并且相邻的点为白色的点的个数大于一个固定的值，那么这个点就是噪点。

我们根据一个点A的RGB值，与周围的8个点的RBG值比较，设定一个值N（0 <N <8），当A的RGB值与周围8个点的RGB相等或者小于N时，此点为噪点


下面是用比较古老的`pytesser3`识别验证码

pytesser3 的安装
`pip install pytesser3`

先安装`Tesseract` ，下载好后

将Tesseract.exe 和 `testdata` 复制到 `pytesser3`文件中
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190331224106775.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)

将pytesser3包下面__init__文件内tesseract_exe_name的值设置为为你的tesseract.exe的路径



![在这里插入图片描述](https://img-blog.csdnimg.cn/20190331224114649.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190331224118834.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)

```python
# -*- coding：utf-8 -*-
# time ：2019/3/30 22:03
# author: 毛利
from pytesser3 import image_to_string
from PIL import Image

def binazing(image):
    '''
    对图片进行灰度和二值化
    :param image:
    :return:
    '''
    image = image.convert('L')
    w,h = image.size
    # print(w,h)
    ### 二值化
    pixdata = image.load()
    for i in range(h):
        for j in range(w):

            if pixdata[j,i] > 170:
                pixdata[j,i] = 255
            else:
                pixdata[j, i] = 0
    return image

def depoint(image):
    '''
    对图片进行降噪
    :param image:
    :return:
    '''
    pixdata = image.load()
    w,h = image.size
    for y in range(1,h-1):
        for x in range(1,w-1):
            count = 0
            if pixdata[x,y-1] >245:
                count =count +1
            if pixdata[x,y+1] >245:
                count =count +1
            if pixdata[x-1,y] >245:
                count =count +1
            if pixdata[x+1,y] >245:
                count =count +1
            if pixdata[x-1, y - 1] > 245:
                count = count + 1
            if pixdata[x+1, y + 1] > 245:
                count = count + 1
            if pixdata[x - 1, y+1] > 245:
                count = count + 1
            if pixdata[x + 1, y-1] > 245:
                count = count + 1
            if count>4:
                pixdata[x,y] =255
    return image

if __name__ == '__main__':
    image = Image.open('111.jpg')
    image = binazing(image)
    image = depoint(image)
    image.show()
    print(image_to_string(image))

####输出结果#####
TBQL
```




这是111.jpg


![](https://imgconvert.csdnimg.cn/aHR0cDovL3B3ZmdtOWZqby5ia3QuY2xvdWRkbi5jb20vRmotSXZrRE9oTWJkcm9GRy1oT1RET2dCRG1zWg?x-oss-process=image/format,png)
