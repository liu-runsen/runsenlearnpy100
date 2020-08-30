
@Author：Runsen
@Date：2020/7/13

> 人生最重要的不是所站的位置，而是内心所朝的方向。只要我在每篇博文中写得自己体会，修炼身心；在每天的不断重复学习中，耐住寂寞，练就真功，不畏艰难，奋勇前行，不忘初心，砥砺前行，人生定会有所收获，不留遗憾 （作者：Runsen ）

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

前面文章，点击下面链接

[我的Python教程，不断整理，反复学习](https://maoli.blog.csdn.net/article/details/106162925)




在实际的业务中，难免会跟第三方系统进行数据的交互与传递，其实就是写接口API的。今天就开始第九十三篇、Python使用百度云接口API实现截图，文字识别和语音合成


@[toc]


# 接口RESTful API


随着微信以及各种数据平台的兴起，大家对跟这些平台对接的需求越来越多。目前，包括以上平台在内的一些主流公共平台都会以一种 REST 架构原则，向大众提供对接的接口。这种符合 REST 风格的接口，就称为 RESTful API。




比如注册百度云帐号，打开百度云平台：https://login.bce.baidu.com/reg.html?tpl=bceplat&from=portal进行账号注册


记住:    AppID，API Key，Secret Key

上面三个就是用户的接口。






# 安装keyboard
下面我们实现Python使用百度云接口API实现截图，文字识别的功能。需要安装keyboard。

keyboard是一个监控键盘输入的库


安装：`pip install keyborad`


执行下面的代码就是可以截图了。
```python
import keyboard
import time
from PIL import ImageGrab
def screen():
    print('开始截图')
    # 使用微信的截图热键
    keyboard.wait(hotkey='alt+a')
    # 保存
    keyboard.wait(hotkey='enter')
    # 图片保存需要时间
    time.sleep(0.5)
    # 读取剪切板的图片
    image = ImageGrab.grabclipboard()
    # 保存图片
    image.save('screen.jpg')
    print('图片保存完成')
screen()
```
当在键盘敲ctrl+a来得到图片


![](https://img-blog.csdnimg.cn/20190502231944769.png)

截取的图片

![](https://img-blog.csdnimg.cn/20190502232009661.png)


# 文字识别
下面我使用百度云来进行识别

为什么用百度云，因为百度的技术，阿里的运营，腾讯的产品。技术当然选百度云，而且识别效果比较高。




![](https://img-blog.csdnimg.cn/20190502232210590.png)



![](https://img-blog.csdnimg.cn/20190502232100232.png)


要安装百度的接口：[官方的教程](https://cloud.baidu.com/doc/OCR/OCR-Python-SDK.html#.E6.8E.A5.E5.8F.A3.E8.AF.B4.E6.98.8E)：https://cloud.baidu.com/doc/OCR/OCR-Python-SDK.html#.E6.8E.A5.E5.8F.A3.E8.AF.B4.E6.98.8E


下面就是教程的模板。

```python
from aip import AipOcr

""" 你的 APPID AK SK """
APP_ID = ''
API_KEY = ''
SECRET_KEY = ''

client = AipOcr(APP_ID, API_KEY, SECRET_KEY)



"""读取图片"""

def get_file_content(filepath):
    with open(filepath,'rb') as f:
        return f.read()



def get_img_content(img):

    image_content=''
    content = client.basicAccurate(image=img)
    # print(content)
    for words in content['words_result']:
        print(words)  # 字典
        image_content += words['words']
    print(image_content)
    
```

![](https://img-blog.csdnimg.cn/20190502232738379.png)

下面就是将截图整合到其中，封装全代码。
```python
# -*- coding：utf-8 -*-
# time ：2019/5/2 23:02
# author: 毛利


import keyboard
import time
from PIL import ImageGrab
def screen():
    print('开始截图')
    # 使用微信的截图热键
    keyboard.wait(hotkey='alt+a')
    # 保存
    keyboard.wait(hotkey='enter')
    # 图片保存需要时间
    time.sleep(0.5)
    # 读取剪切板的图片
    image = ImageGrab.grabclipboard()
    # 保存图片
    image.save('screen.jpg')

# 使用百度云中的文字识别
from aip import AipOcr

""" 你的 APPID AK SK """
APP_ID = ''   #你的账号的id
API_KEY = ''
SECRET_KEY = ''

client = AipOcr(APP_ID, API_KEY, SECRET_KEY)



"""读取图片"""

def get_file_content(filepath):
    with open(filepath,'rb') as f:
        return f.read()



def get_img_content(img):

    image_content=''
    content = client.basicAccurate(image=img)
    # print(content)
    for words in content['words_result']:
        # print(words)  # 字典
        image_content += words['words']
    print(image_content)

if __name__ == '__main__':
    screen()
    img = get_file_content('screen.jpg')
    get_img_content(img)
```




下面就是具体的使用：
![](https://img-blog.csdnimg.cn/20190502233844342.png)



![](https://img-blog.csdnimg.cn/20190502233919839.png)




# 语言合成



百度AP开发平台（ai.baidu.com）,注册成功之后，点击控制台，进入到百度云-管理中心。就可以创建应用了。
我这里创建了一个带有语音接口的应用：[官方教程](https://ai.baidu.com/docs#/ASR-Online-Python-SDK/top)


https://ai.baidu.com/docs#/ASR-Online-Python-SDK/top

![](https://img-blog.csdnimg.cn/20200713115655335.png)


![](https://img-blog.csdnimg.cn/20200713115719836.png)


具体代码如下。


```csharp
from aip import AipSpeech
app_id = ""
api_key = ""
secret_key = ""
client = AipSpeech(app_id, api_key, secret_key)
result = client.synthesis("好好学习，天天向上爱", "zh", 1, {
    "vol": 9,
    "spd": 6,
    "pit": 7,
    "per": 4,
})
with open("audio.mp3", "wb") as f:
    f.write(result)

```

![](https://img-blog.csdnimg.cn/20200713115750256.png)

音频的内容就是好好学习，天天向上


就是这么简单，不知道你学会了没有。



