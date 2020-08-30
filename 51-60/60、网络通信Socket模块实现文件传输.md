@Author：Runsen
@Date：2020/5/29

作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。

我预计写零基础学Python写到一百篇，这是第六十篇，还剩四十篇


实现的效果如下的Gif所示，就是网络通信Socket模块实现文件传输。

![](https://img-blog.csdnimg.cn/20200530234705789.gif)

@[TOC]

# 服务端


首先需要获取本机ip，这里服务端采用多线程的方法，就是定义一个函数，然后用threading创建任务。客户端连接成功，接收客户端的请求信息，就是下载的文件名。所以需要判断，有输出文件字节数。然后在问用户是不是要下载，得到信息就使用 while True: 读文件的内容，再一个send。就是这么简单，看代码是不是就是这么回事。



```css
import socket
import os
import threading

# 获取本机ip
def get_host_ip():
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        s.connect(('8.8.8.8', 80))
        ip = s.getsockname()[0]
    finally:
        s.close()

    return ip

# 处理客户端请求下载文件的操作（从主线程提出来的代码）
def deal_client_request(ip_port, service_client_socket):
    # 连接成功后，输出“客户端连接成功”和客户端的ip和端口
    print("客户端连接成功", ip_port)
    # 接收客户端的请求信息【recv】
    file_name = service_client_socket.recv(1024)
    # 解码
    file_name_data = file_name.decode("utf-8")
    # 判断文件是否存在
    if os.path.exists(file_name_data):
        #输出文件字节数
        fsize = os.path.getsize(file_name_data)
        #转化为兆单位
        fmb = fsize/float(1024*1024)
        #要传输的文件信息
        senddata = "文件名：%s  文件大小：%.2fMB"%(file_name_data,fmb)
        #发送和打印文件信息【send】
        service_client_socket.send(senddata.encode("utf-8"))
        print("请求文件名：%s  文件大小：%.2f MB"%(file_name_data,fmb))
        #接受客户是否需要下载【recv】
        options = service_client_socket.recv(1024)
        if options.decode("utf-8") == "y":
            # 打开文件
            with open(file_name_data, "rb") as f:
                #　计算总数据包数目
                nums = fsize/1024
                #　当前传输的数据包数目
                cnum = 0

                while True:
                    file_data = f.read(1024)
                    cnum = cnum + 1
                    #progress = cnum/nums*100

                    #print("当前已下载：%.2f%%"%progress,end = "\r")
                    if file_data:
                        # 只要读取到数据，就向客户端进行发送【send】
                        service_client_socket.send(file_data)
                    # 数据读完，退出循环
                    else:
                        print("请求的文件数据发送完成")
                        break
        else:
            print("下载取消！")
    else:
        print("下载的文件不存在！")
    # 关闭服务当前客户端的套接字【close】
    service_client_socket.close()


if __name__ == '__main__':
    # 获取本机ip
    print("TCP文件传输服务器，本机IP:" + get_host_ip())
    
    # 把工作目录切换到data目录下
    os.chdir("./data")
    # 创建套接字【socket】
    tcp_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 绑定端口号【bind】
    tcp_server_socket.bind(("", 3356))
    # 设置监听，将主动套接字变为被动套接字【listen】
    tcp_server_socket.listen(128)

    # 循环调用【accept】，可以支持多个客户端同时连接，和多个客户端同时下载文件
    while True:
        service_client_socket, ip_port = tcp_server_socket.accept()
        # 连接成功后打印套接字号
        #print(id(service_client_socket))

        # 创建子线程
        sub_thread = threading.Thread(target=deal_client_request, args=(ip_port, service_client_socket))
        # 启动子线程
        sub_thread.start()
```






# 客户端
客户端更简单，连接服务端，发送下载文件的请求，定义一个写入的文件夹，就是小儿科东西。不写了，看代码。



```css
# -*- coding:utf-8 -*-
# 多任务文件下载器客户端
import socket
import os

if __name__ == '__main__':
    # 创建套接字【socket】
    tcp_client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # 和服务端连接【connect】
    server_ip = input("输入服务器IP：")
    tcp_client_socket.connect((server_ip, 3356))
    # 发送下载文件的请求
    file_name = input("请输入要下载的文件名：")
    # 编码
    file_name_data = file_name.encode("utf-8")
    # 发送文件下载请求数据【send】
    tcp_client_socket.send(file_name_data)
    # 接收要下载的文件信息【recv】
    file_info = tcp_client_socket.recv(1024)
    # 文件信息解码
    info_decode = file_info.decode("utf-8")
    print(info_decode)
    #获取文件大小
    fileszie = float(info_decode.split('：')[2].split('MB')[0])
    fileszie2 = fileszie*1024
    # 是否下载？输入ｙ　确认　输入ｑ 取消
    opts = input("是否下载？(y 确认　q 取消)")
    if opts == 'q':
        print("下载取消！程序退出")
    else:
        print("正在下载　>>>>>>")
        #向服务器确认正在下载【send】
        tcp_client_socket.send(b'y')

        recvpath = "./receive/"
        if not os.path.exists(recvpath):
            os.mkdir(recvpath) 
        
        # 把数据写入到文件里
        with open(recvpath + file_name, "wb") as file:
            #目前接收到的数据包数目
            cnum = 0

            while True:
                # 循环接收文件数据【recv】
                file_data = tcp_client_socket.recv(1024)
                # 接收到数据
                if file_data:
                    # 写入数据
                    file.write(file_data)
                    cnum = cnum+1
                    #progress =cnum/fileszie2*100
                    #print("当前已下载：%.2f%%"%progress,end = "\r")
                # 接收完成
                else:
                    print("下载结束！")
                    break
    # 关闭套接字【close】
    tcp_client_socket.close()
```

