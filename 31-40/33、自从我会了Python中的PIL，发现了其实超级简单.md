PIL全称是Python Image Library，顾名思义，是用来做图像处理的。


@[TOC]
# 了解PIL

`PIL` (Python Image Library) 已经算是 `Python` 处理图片的标准库了，兼具强大的功能和简洁的` API.`
但是`PIL`库的更新非常缓慢， 并且它只支持到`python2.7`，不支持`python3`

由于PIL库更新太慢了，于是于是一群志愿者在PIL库的基础上创建了一个新的分支版本，命名为`Pillow`.

`Pillow`目前最新支持到`python3.6`，它的维护和开发十分活跃，兼容PIL库的绝大多数语法，并且增加了许多新的特性，推荐直接使用`Pillow`

# 概念了解


PIL中所涉及的基本概念有如下几个：
- 通道(bands)
- 尺寸(size)
- 坐标系统(coordinate system)




通道：

每张图片都是由一个或者多个数据通道构成，如果这些通道具有相同的维数和深度，PIL允许将这些通道进行叠加

以RGB图像为例，每张图片都是由三个数据通道叠加构成，分别为R 、G 、B。

对于灰度图像（没有色彩的图片， RGB色彩分量全部相等），只有一个通道。

灰度指的是黑白图像中点的颜色深度，范围一般是0到255， 白色为255，黑色为0

图片尺寸（size）：
指的是图片的宽度和高度

通过size属性可以获取图片的尺寸，它的返回值是一个元祖，元祖里面有两个值，分别是水平和垂直方向上的像素个数

坐标系统：

PIL使用笛卡尔像素坐标系统，图像的左上角为左边的原点（0，0），这就意味着，x轴的数值是从左到右增长的，y轴的数值是从上到下增长的。 

在我们处理图像的时候，常常需要去表示一个矩形的图像区域。Pillow中很多方法都需要传入一个表示矩形区域的元祖

这个元祖包含四个值，分别表示矩形四条边距离x轴或者y轴的距离。顺序是（左，顶，右，底）
例如，一个800x600的像素图像表示为（0， 0， 800， 600）







我们可以用PIL干嘛呢？

第一，可以将两张图片合并在一起


#  Image.blend(image1,image2,alpha)




合成公式为：out=image1(1.0- alpha)+image2alpha

```python
from PIL import Image
im1 = Image.open("1.jpg")
im2 = Image.open("2.jpg")
print(im1.mode,im1.size)  # RGB (500, 300)
print(im2.mode,im2.size)   # RGB (500, 300)
im = Image.blend(im1, im2, 0.5)
im.save('3.jpg')
```

这是1.jpg
![](https://img-blog.csdnimg.cn/20190502220733889.jpg)
这是2.jpg
![](https://img-blog.csdnimg.cn/20190502220739252.jpg)


这是3.jpg



![合成后的图片](https://img-blog.csdnimg.cn/2019050222074462.jpg)

# Composite


当然除了上面的方法还可以使用Composite类
Image.composite(image1,image2, mask) ⇒ image
复合类使用给定的两张图像及mask图像作为透明度，插值出一张新的图像。变量mask图像的模式可以为“1”，“L”或者“RGBA”。所有图像必须有相同的尺寸。


看一波源码，如下图所示


![](https://img-blog.csdnimg.cn/20190502221303486.png)


一波代码开干


```python
from PIL import Image
im1 = Image.open("1.jpg")
im2 = Image.open("2.jpg")
r,g,b = im1.split()
print(b.mode)
print(im1.mode,im1.size)
print(im2.mode,im2.size)
im = Image.composite(im1,im2,mask=b)
im.save('4.jpg')
```
这是4.jpg




![](https://img-blog.csdnimg.cn/20190502222239658.jpg)

# Filter类
im.filter(filter) ⇒ image


返回一个使用给定滤波器处理过的图像的拷贝。在该模块中，预先定义了很多增强滤波器，可以通过filter()函数使用，预定义滤波器包括：

- BLUR
- CONTOUR
- DETAIL
- EDGE_ENHANCE
- EDGE_ENHANCE_MORE
- EMBOSS
- FIND_EDGES
- SMOOTH


再看一波源码，如下图所示



![](https://img-blog.csdnimg.cn/20190502223542859.png)


一波代码开干


```python
from PIL import Image
from PIL import ImageFilter                         ## 调取ImageFilter
img = Image.open("1.jpg")
blu = img.filter(ImageFilter.BLUR)                ##均值滤波
con = img.filter(ImageFilter.CONTOUR)             ##找轮廓
edge = img.filter(ImageFilter.FIND_EDGES)         ##边缘检测
blu.save('均值滤波.jpg')
con.save('找轮廓.jpg')
edge.save('边缘检测.jpg')
```

这是均值滤波.jpg



![](https://img-blog.csdnimg.cn/20190502223351590.jpg)

这是找轮廓.jpg



![](https://img-blog.csdnimg.cn/20190502223356699.jpg)

这是边缘检测.jpg



![](https://img-blog.csdnimg.cn/20190502223400421.jpg)
# PIL所有操作


基本操作

原图
![1.jpg](https://img-blog.csdnimg.cn/20190328222744357.jpg)

```python
# 导入模块
from PIL import Image
# 打开图片
image = Image.open('1.jpg')
image.show()
# 新建图片
newImage= Image.new('RGB', (100, 100), 'red')
newImage.save('new.jpg')
# 获得图像尺寸:
w, h = image.size
print('原本图像大小: %sx%s' % (w, h))
# 缩放到50%:
image.thumbnail((w//2, h//2))
print('缩放后图片的大小: %sx%s' % (w//2, h//2))
# 把缩放后的图像用jpeg格式保存:
image.save('2.jpg', 'jpeg')
# 复制图片
image2 = image.copy()
image2.save("3.jpg")
```
剪切 粘贴，合并图像
```python
# 剪切图片
# 设置要拷贝的区域
box = (0, 0, 100, 100)
image3 = image.crop(box)
image3.save("4.jpg")
# 这个region可以用来后续的操作(region其实就是一个Image对象)
region = image.crop(box)
# 处理复制的矩形选区并粘贴到原图
region = region.transpose(Image.ROTATE_180)
image.paste(region, box)
image.save('5.jpg')
```

旋转和翻转图像
```python
# 保持原图像不变。逆时针旋转。
image.rotate(90).save('6.jpg')
# 水平翻转，
image.transpose(Image.FLIP_LEFT_RIGHT).save('7.jpg')
# 垂直翻转
image.transpose(Image.FLIP_TOP_BOTTOM).save('8.jpg')
```
过滤操作
```python
from PIL import Image, ImageFilter
im = Image.open('1.jpg')
# 高斯模糊
im.filter(ImageFilter.GaussianBlur).save(r'高斯模糊.jpg')
# 普通模糊
im.filter(ImageFilter.BLUR).save(r'普通模糊.jpg')
# 边缘增强
im.filter(ImageFilter.EDGE_ENHANCE).save(r'边缘增强.jpg')
# 找到边缘
im.filter(ImageFilter.FIND_EDGES).save(r'找到边缘.jpg')
# 浮雕
im.filter(ImageFilter.EMBOSS).save(r'浮雕.jpg')
# 轮廓
im.filter(ImageFilter.CONTOUR).save(r'轮廓.jpg')
# 锐化
im.filter(ImageFilter.SHARPEN).save(r'锐化.jpg')
# 平滑
im.filter(ImageFilter.SMOOTH).save(r'平滑.jpg')
# 细节
im.filter(ImageFilter.DETAIL).save(r'细节.jpg')
```

![](https://img-blog.csdnimg.cn/20190328223500732.jpg)
