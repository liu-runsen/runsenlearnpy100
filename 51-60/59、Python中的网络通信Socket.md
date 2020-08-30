@Author：Runsen
@Date：2020/5/29



作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。


我预计写零基础学Python写到一百篇，这是第五十九篇。


今天，我要写的是Python中的网络通信Socket，写之前，先去[菜鸟教程](https://www.runoob.com/python/python-socket.html)看看，偷窥学习一下Socket通讯的基本方式。




@[TOC]

# TCP

我是化工专业的，TCP/IP这些怎么能不知道？在了解Socket前，我先给装个逼，介绍下TCP/IP。


计算机与网络设备两情侣要谈恋爱，相互通信，那么双方就必须有规则。基于相同的方法，不同的硬件、操作系统之间的通信，都需要一种规则。而我们就把这种规则称为协议(protocol)。


TCP/IP 是互联网相关各类协议族的总称。TCP/IP是指TCP和IP这两种协议。TCP/IP是在IP协议的通信过程中，使用到的协议族的统称。



# 七层


TCP/IP协议族按层次分别为 应用层，传输层，网络层，数据链路层，物理层。可以按照不同的模型分4层或者是7层。

将TCP/IP分为5层，越靠下越接近硬件。

应用层，应用程序收到传输层的数据后，接下来就是要进行解读，解读必须要先规定好格式，而应用层就是规定应用程序的数据格式，主要协议有HTTP等。

传输层，该层为两台主机上的应用程序提供端到端的通信，传输层有两个传输协议为TCP（传输控制协议）和UDP（用户数据报协议），TCP是一个可靠的面向连接的协议，UDP是不可靠或者说无连接的协议。

网络层，决定如何将数据从发送方到接收方，是建立主机到主机的通信。

数据链路层，控制网络层与物理层之间的通信，主要功能是保证物理线路上进行可靠的数据传递。

物理层，该层负责物理传输，与链路有关，也与传输的介质有关。



![](https://img-blog.csdnimg.cn/2020052916170248.png)



![](https://img-blog.csdnimg.cn/20200529161811896.png)




![](https://img-blog.csdnimg.cn/20200529161821652.png)

别看我很牛逼，其实都是抄百度百科的，图片都是网络的，出自《图解HTTP》书籍的


# 三次握手，四次挥手

TCP三次握手，四次挥手，Runsen也不会怎么说，就把网上最通俗的图放在下面 了，还是别看我很牛逼，牛逼的是做图的大佬。



![](https://img-blog.csdnimg.cn/20200529162029248.png)
三次握手示意图：



![](https://img-blog.csdnimg.cn/2020052916222474.png)

三次握手过程：


第一次握手是在建立连接，客户端发送连接请求报文段，把标有SYN的数据包发给服务器端即为接收端。

第二次握手是服务器端即接收端收到客户端的SYN的报文段，同时发送标有SYN/ACK的数据包。

第三次握手是客户端收到服务器端的SYN/ACK的数据包后，向服务器端发送标有ACK的数据包。




四次握手其实就是把第二步变成了两步，所以就成了[四次握手」。




![](https://img-blog.csdnimg.cn/20200529162851493.png)


# Socket

我是来偷窥Python中的网络通信Socket，不小心偷窥到了一个非常不错的Socket好图



![](https://img-blog.csdnimg.cn/20200529161222362.png)

# 实现简单的通讯程序
服务端，server.py


```css
#导入socket模块
import socket
#创建套接字 或使用server = socket.socket()
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
#定义绑定的ip和端口，用元组定义
ip_port = ('127.0.0.1', 8888)
#绑定监听:bind(address),在AF_INET下,以元组（ip,port）的形式表示地址
server.bind(ip_port)
#设置最大连接数，默认为1
server.listen(5)
#不断接受连接：one by one
while True:
    print("等待数据连接中……")
    #接受客服端数据请求
    conn, address = server.accept()
    '''
    向客服端返回信息
    (注意：python3.x以上，网络数据的发送接收都是byte类型，
    发送接收String类型数据时需要对数据进行编码(发送：messages.enconde()；接收后转为String类型:messages.deconde())，pyhon2.x则直接发送数据无须编码)
    '''
    messages = "连接成功！"
    conn.send(messages.encode())
    #计数信息条数
    count = 0
    #一个连接中，不断的接受客户端发来的数据
    while True:
        data = conn.recv(1024)
        #打印客户端发来的数据信息
        print(data.decode())
        #判断是否退出当前连接,等在下一个连接
        if data == b'exit':
          break
        #处理客户端数据（如：响应请求等）
        count = count + 1
        string = "第" + str(count) + "条信息：" + data.decode()
        conn.send(string.encode())
        #主动关闭连接
    conn.close()
```


客户端，client.py



```css
import socket

#创建套接字
client = socket.socket()
#访问的服务器的ip和端口，用元组定义
ip_port = ("127.0.0.1", 8888)
#连接服务器主机
client.connect(ip_port)
#同一链接中，不断向服务器发生数据或请求
while True:
    #接收服务器发送或响应的数据
    data = client.recv(1024)
    #打印接收的数据；python3.x以上数据要编码(发送：data.enconde()；接收后转为String类型:data.deconde())
    print(data.decode())
    messages = input("请输入发生或请求的数据(exit退出)：")
    client.send(messages.encode())
    if messages == 'exit':
        break
    '''
    #接收服务器发送或响应的数据
    data = client.recv(1024)
    #打印接收的数据；python3.x以上数据要编码，发送enconde()；接收deconde()
    print(data.decode())
    '''
#关闭连接
client.close()
```

![](https://img-blog.csdnimg.cn/20200529173904180.png)

# 多线程通信
TCP服务器与多个TCP客户端同时进行连续通信，只需要通过threading创建多线程任务handle_client就可以了。




```css
import socket
import threading
import random


def handle_client():
    # 接受客户端请求链接
    client, address = server.accept()
    print("[*] Accept connection from: %s:%d" % (address[0], address[1]))
    messages = "Hello World!"
    client.send(messages.encode())
    # 连续与当前连接的客户端通信
    while True:
        # 接受客户端数据
        request = (client.recv(1024)).decode()
        # 判断是否结束通信
        if request == 'exit':
            break
        print("[*] Received from %s:%d : %s" % (address[0], address[1], request))
        # 发送响应信息给客户端
        client.send((str(random.randint(1, 1000)) + "：" + "ACK!").encode())
    # 关闭当前连接
    client.close()


if __name__ == "__main__":
    # 创建套接字
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 定义绑定ip和端口
    ip = '127.0.0.1'
    port = 8888
    # 绑定监听
    server.bind((ip, port))
    # 设置最大连接数，默认为1
    server.listen(5)
    print("[*] Listening on %s:%d" % (ip, port))
    # 循环开启线程，接受多个客户端的链接通信
    while True:
        # 创建一个线程
        client_handler = threading.Thread(target=handle_client)
        # 开启线程
        client_handler.start()

```
![](https://img-blog.csdnimg.cn/20200529175334353.png)


python3.x以上，网络数据messages的发送接收都是byte类型，若要发送接收String类型数据时需要通过messages.enconde()对数据进行编码，接收后通过messages.deconde()转为String类型。pyhon2.x则直接发送数据无须编码。



代码来自：https://www.imooc.com/learn/1031
