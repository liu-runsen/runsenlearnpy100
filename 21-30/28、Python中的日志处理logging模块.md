@Author：Runsen


@[toc]
# 日志

日志是一种可以追踪某些软件运行时所发生事件的方法。软件开发人员可以向他们的代码中调用日志记录相关的方法来表明发生了某些事情。一个事件可以用一个可包含可选变量数据的消息来描述。此外，事件也有重要性的概念，这个重要性也可以被称为严重性级（level）。

![](https://img-blog.csdnimg.cn/20190418234643545.png)





Logging 中几种级别：DEBUG < INFO < WARNING < ERROR < CRITICAL




![](https://img-blog.csdnimg.cn/20190418234723863.png)


![](https://img-blog.csdnimg.cn/20190418234754723.png)


logging模块是python内置的标准模块，主要用于输出运行日志，可以设置输出日志的等级、日志保存路径、日志文件和回滚等；
可以说，logging模块主要由4部分组成：



-  Logger 记录器，提供了应用程序代码能直接使用的接口
-  Handler 处理器，将记录器产生的日志记录发送至合适的目的地，或者说将Logger产生的日志传到指定位置
- Filters 过滤器，对输出的日志进行过滤，它可以决定输出哪些日志记录
-  Formatter 格式化器，控制日志输出的格式，指明了最终输出中日志记录的布局





![](https://img-blog.csdnimg.cn/20190418234825414.png)


# 模块化组件使用
- 创建一个logger（日志处理器）对象
- 定义handler(日志处理器)，决定把日志发到哪里


![](https://img-blog.csdnimg.cn/20190418235053974.png)




- 设置日志级别（level）和输出格式Formatters（日志格式器）
- 把handler添加到对应的logger中去



![](https://img-blog.csdnimg.cn/20190418235206590.png)




