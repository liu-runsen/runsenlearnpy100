![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdrci5jbi1iai51ZmlsZW9zLmNvbS9mOGM0YjhmZC0zZGY5LTQ0NDktOGVhMi1lMWJhNjE5MGY3MTEucG5n?x-oss-process=image/format,png)




@Author ： By Runsen




在Python中分别有两个库实现发送邮件，分别是smtplib和email。


smtplib是用来发送邮件用的，email是用来构建邮件内容的。




下面是具体使用：


```python
import smtplib
 
server = smtplib.SMTP()
server.connect(host, port)


#连接（connect）指定的服务器，host是指定连接的邮箱服务器，通过搜索“xx邮箱服务器地址”，就可以找到
#例如QQ邮箱的SMTP服务器地址是：smtp.qq.com。port是端口，一般情况下SMTP默认端口号为25

server.login(username, password)
#username:登录邮箱的用户名
#password：授权码
server.sendmail(sender, to_addr, msg.as_string())

#from_addr：邮件发送地址，就是上面的username
#to_addr：邮件收件人地址
#msg.as_string()：为一个字符串类型 ，as_string()是将发送的信息msg变为字符串类型。
server.quit()
#退出服务器，结束SMTP会话
```

备注：SMTP 协议是由源服务器到目的地服务器传送邮件的一组规则。



email 模块：也就是用来写邮件内容的模块。这个内容可以是纯文本、HTML内容、图片、附件等多种形式。



```python
import email
from email.mime.text import MIMEText
#纯文本或HTML页面
fromemail.mime.image import MIMEImage
#内容形式为图片
fromemail.mime.multipart import MIMEMultipart
#多形式组合，可包含文本和附件
 
MIMEText方法：
MIMEText(msg,type,chartset)
# msg：文本内容，可自定义
# type：文本类型，默认为plain（纯文本）
# chartset：文本编码，中文为“utf-8”
```



# 测试Demo


这是我把自己的username和password省略了

```python
# 测试
import smtplib
from email.mime.textimport MIMEText
 
username='你的@qq.com'
password='XXXXXXXXX'
sender='发给谁@qq.com'
to_addr='run24118cajie@163.com'
msg=MIMEText('你好这是用python发的一封邮件','plain','utf-8')
 
server =smtplib.SMTP()
server.connect('smtp.qq.com', 25)
server.login(username,password)
server.sendmail(sender,to_addr, msg.as_string())
server.quit()
```

发送成功


![](https://img-blog.csdnimg.cn/20190505234114734.png)

# 标准发邮件的格式


```python
# 首先，主送、抄送就是两个用逗号分割的字符串，subject是标题，正文是context，支持html。
from email import encoders
from email.header import Header
from email.mime.text import MIMEText
from email.mime.base import MIMEBase
from email.mime.multipart import MIMEMultipart
import smtplib
import os

from_addr = 'xxxxx@qq.com'
password = 'xxxxx'
smtp_server = 'smtp.qq.com'
def sendmail(to_addr, cc_addr, subject, content, attach_full_path):
    # create a message
    msg = MIMEMultipart()
    msg['From'] = from_addr
    msg['To'] = to_addr
    msg['Cc'] = cc_addr
    msg['Subject'] = Header(subject, 'utf-8').encode()
    # 正文:
    msg.attach(MIMEText(content, 'html', 'utf-8'))
    # 附件
    (filepath, file) = os.path.split(attach_full_path)
    with open(attach_full_path + '', 'rb') as f:
        # 设置附件的MIME和文件名:
        mime = MIMEBase('application', 'octet-stream', filename=file)
        # 加上必要的头信息:
        mime.add_header('Content-Disposition', 'attachment', filename=file)
        # 把附件的内容读进来:
        mime.set_payload(f.read())
        # 用Base64编码:
        encoders.encode_base64(mime)
        # 添加到MIMEMultipart:
        msg.attach(mime)
    # 发送邮件
    server = smtplib.SMTP(smtp_server, 25)
    server.set_debuglevel(1)
    server.starttls()
    server.login(from_addr, password)
    server.sendmail(from_addr, to_addr.split(',') + cc_addr.split(','), msg.as_string())
    server.quit()
  
```
