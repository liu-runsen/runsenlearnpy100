@Author ： By Runsen


上次大家一些Git的小知识，下面我们先开始Github之旅，再继续学习Git。

![](https://img-blog.csdnimg.cn/20200511154104470.png)











@[toc]




# 1、了解Github


我梦想这有女朋友问我：Git或GitHub到底是什么，它们之间有什么区别？


别睡了，孩子！没钱没身高没样子，简直就是又穷又丑又矮的典型，天天做白日梦？


梦想的女朋友：Git或GitHub到底是什么？

我：Git是一个跟踪代码更改的版本控制系统，而GitHub是一个基于Web的Git版本控制存储库托管服务。它提供了Git的所有分布式版本控制和源代码管理（SCM）功能，并提供了一些自己的特性。对于开发人员而言，这是他们可以在其中存储项目并与志趣相投的人建立联系的地方。您可以将其视为“代码云”。（百度百科）




![](https://img-blog.csdnimg.cn/20200511154654782.png)



其实，Github就是放代码的地方，通过Git来上传提交代码。



# 2、注册Github



百度搜索GitHub或者直接点击https://github.com/进入官网



![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051115501360.png)



注意每一个人都有自己的UserName，所以你创建Github的名字一定要亮，看起来很牛逼。


Email你可以使用国内的邮箱都是可以的，要用常用的，注册一个账号就是一个简单的事，


登录就可以看得自己的仓库和名字。
![](https://img-blog.csdnimg.cn/20200511155805204.png)


# 3、访问不了Github怎么办




访问Github突然上不去了，出现了网页无法正常运行？





![](https://img-blog.csdnimg.cn/20200511160126677.png)


你应该知道Github在外国，当然访问慢了。只要修改hosts，80%可以解决。

打开Dns检测|Dns查询 ，这里推荐站长工具

http://tool.chinaz.com/dns?type=1&host=github.com&ip=

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200511160714439.png)

.把检测列表里的TTL值最小的IP输入到hosts里，并对应写上github官网域名

下面是不同系统的hosts


```clike
Windows 系统位于 C:\Windows\System32\drivers\etc\
Android（安卓）系统hosts位于 /etc/
Mac（苹果电脑）系统hosts位于 /etc/
iPhone（iOS）系统hosts位于 /etc/
Linux系统hosts位于 /etc/
```




我这里使用Notepad++打开的，填写的是以前的hosts

![](https://img-blog.csdnimg.cn/20200511160405188.png)

如果你的Github真的访问不了，那用码云吧，码云是我国开发者为了打破Github垄断，仿照Github诞生的，网址：https://gitee.com/







# 4、了解一些项目页面

现在我找到一个Java项目，找到一个很多人点赞的Java项目，写的应该是教程，




![](https://img-blog.csdnimg.cn/20200511162353692.png)


如果你能够修复bug或自己添加功能 ，请发一个pull request吧！如果你提交了一个pull request，维护者就会将你的分支与已有的分支作比较来决定是否要合并。


不要想得不可能，我记得的有一个6岁的孩子pull request通过了，就是因为在注释中写了一个*号，可以显得更加严谨好看。




# 5、 在码云平台创建项目



虽然主要使用github最主流，但是国内访问速度慢，而且托管私有项目收费，国内一般使用码云gitee，国内访问速度快，-而且托管私有项目免费，- 小公司中使用gitlab或者码云来搭建。大厂有自己的项目托管仓库。






在码云和Github创建项目都是一样的，不管是是使用github还是使用码云，步骤是差不多的，区别是github是全英文的慢一点。这里我以码云为例。







![](https://img-blog.csdnimg.cn/20200511164043356.png)


然后由上往下输入你项目的名字、项目的描述，选择这个项目是不是公开(Public)或是作为私人项目(Private)。





![](https://img-blog.csdnimg.cn/2020051116441760.png)

创建成功后，之后会出现以下界面的信息。




![](https://img-blog.csdnimg.cn/20200511165134582.png)

创建好仓库后，你的仓库会有两个地址，一个是https，一个是ssh。因为使用https需要输入用户名和密码，推荐使用ssh的方式。要使用ssh你需要设置你账户的ssh公钥。
‘








下一步点击下载SSH，复制下来，也就是git@gitee.com:MaoliRUNsen/python_from_novice_to_master.git



远程仓库里已经存在项目文件，你买了台新电脑，需要将项目从远程仓库clone到本地进行工作。



在新电脑新建一个文件夹，再使用git clone git@gitee.com:MaoliRUNsen/python_from_novice_to_master.git克隆下来。
![](https://img-blog.csdnimg.cn/20200511165326630.png)

只要你克隆远程仓库，这样你就可以同步到码云。









# 6、Git创建项目
要把本地仓库和远程仓库联系起来有两种方式， 上面是第一种，另一种是通过Git创建项目


和第一种方式的区别在于先创建仓库，

 ```linux
  git init	# 创建仓库
  git remote add origin git@gitee.com:MaoliRUNsen/python_from_novice_to_master.git
  ```



# 7、推送到远程仓库


当本地工作完成，需要将代码推送到远程仓库，使用`git push`命令

```linux
git push origin master
```

push前需要add和commit


# 8、更新到本地仓库

你的同事和你协同开发，他工作的那部分内容完成了，并且已经推送到远程仓库，你接下来的工作需要依赖他的那部分代码，那么你需要将远程仓库代码拉取到本地仓库，使用`git pull`命令

```linux
git pull origin master
```






# 9、仓库成员管理

终于到了重点的时候，我们在新建项目的时候，只是写了基本设置


![](https://img-blog.csdnimg.cn/202005111719161.png)


仓库是需要管理，其实这也叫做项目管理。我们主要看仓库成员管理和部署公钥管理





| 成员角色         | 权限                                                         |
| ---------------- | ------------------------------------------------------------ |
| 访客（登录用户） | 对于公有仓库：创建 Issue、评论、Clone 和 Pull 仓库、打包下载代码、Fork 仓库、 Fork 仓库提交 Pull Request、下载附件 |
| 报告者           | 继承访客的权限。 私有仓库：不能查看代码、不能下载代码、不能 Push 、不能 Fork 、 不能提交 Pull Request、可下载附件，不能上传附件，不能删除附件 |
| 观察者           | 继承报告者权限 私有仓库：创建 Wiki、可以 Clone 下载代码、可以 Pull、不能 Fork |
| 开发者           | 创建 Issue、评论、Clone 和 Pull 仓库、Fork 仓库、打包下载代码、创建 Pull Request、 创建分支、推送分支、删除分支、创建标签（里程碑）、 创建 Wiki、可上传附件，可删除自己上传的附件，不能删除他人上传的附件、 |
| 管理员           | 创建 Issue、评论、Clone 和 Pull 仓库、打包下载代码、创建 Pull Request、 创建分支、推送分支、删除分支、创建标签（里程碑）、创建 Wiki、 添加仓库成员、强制推送分支、编辑仓库属性、可上传附件，可删除自己或他人上传的附件、 不能转移/清空/删除仓库 |



这里你直接可以邀请用户，注意这个和Fork是不一样的，Fork就是提交修改的请求，需要成员的同意。新建成员就可以同意提交修改的请求。

![](https://img-blog.csdnimg.cn/20200511172334850.png)






# 10、部署公钥管理

公钥是什么，就是管理这个项目的钥匙，一般都是项目成员有的。


SSH协议的Git服务，在使用SSH协议访问仓库仓库之前，需要先配置好账户/仓库的SSH公钥。


你需要用Git的SSH 创建Key，然后把这个key放在这个仓库中，一般针对是仓库不是你托管的，在别人平台，你也是项目的成员。




```clike
YIUYE@DESKTOP-5EEO47M MINGW64 ~
$ ssh-keygen -t rsa -C "2953510364@qq.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/YIUYE/.ssh/id_rsa):
/c/Users/YIUYE/.ssh/id_rsa already exists.
Overwrite (y/n)?

YIUYE@DESKTOP-5EEO47M MINGW64 ~
$ pwd
/c/Users/YIUYE

YIUYE@DESKTOP-5EEO47M MINGW64 ~
$ cd .ssh

YIUYE@DESKTOP-5EEO47M MINGW64 ~/.ssh
$ ls
id_rsa  id_rsa.pub  known_hosts

YIUYE@DESKTOP-5EEO47M MINGW64 ~/.ssh
$ cat id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC/bZaaJ9lO2a9AAuMWVpdsZfIVr4wqBA2vNAsButaNIMAx0OkYrfTloLl138+khQqteZ5b9lZdmiYEuAIS8UlBEdHmNo4LiJrLi4DdqOajpsbbdTmjCc4rlEraKOH2qVOTNEj6E+0oeYnnbQlGcA/nKdVbN8bfcsMWiN82Bjn19dP3LXC4oubRP2jWR/X3KyYcX58z1oltCbaIHtgRs1kFp6srFcU067CSmMulxmFXTalWkRSPq1d/gNWUYpii14YBIFUvwLmJlrUtXBcGZGqZhqu50FjpRcCY0TRV3DqZAR2/KnsRN7VeyuYCDmeXKc+UyNeS3zPFgKS7oyFi60CB 2953510364@qq.com

```


![](https://img-blog.csdnimg.cn/20200511173541967.png)



复制生成后的 ssh key，通过仓库主页 「管理」->「部署公钥管理」->「添加部署公钥」 ，添加生成的 public key 添加到仓库中。








![](https://img-blog.csdnimg.cn/20200511173830397.png)






添加后，在终端（Terminal）中输入

```clike
ssh -T git@gitee.com
```

首次使用需要确认并添加主机到本机SSH可信列表。若返回 Hi XXX! You've successfully authenticated, but Gitee.com does not provide shell access. 内容，则证明添加成功

![](https://img-blog.csdnimg.cn/20200511173932897.png)



部署公钥管理是针对不是你的项目而已，由于项目是我，做这个是没有任何意义的。


# 11、如何白嫖别人的资料

Github上有很多开源免费的资料，很多人为了Star就开源了很多学习资料，在我国都是分享学习资料比较多，比如我搜索Python

![](https://img-blog.csdnimg.cn/20200511174245742.png)



下面就有几千个学习资料，所以学东西最好在Github，然后你就下载下来，学习别人是怎么写代码。


![](https://img-blog.csdnimg.cn/20200511174408224.png)


还有很多人是为了找项目，在原始项目进行二次开发。白嫖的时候，请你注意版权。

# 12、文章推荐


我主要推荐的Github的help官方文档


https://help.github.com/en


![](https://img-blog.csdnimg.cn/20200511174803457.png)



Github就主要看企业的文档和Github的桌面版

![](https://img-blog.csdnimg.cn/20200511174951617.png)



Github的桌面版以后接着写，还有码云的help官方文档：https://gitee.com/help/


![](https://img-blog.csdnimg.cn/20200511175058983.png)
看不懂英文的，翻译也不对，那直接看码云的文档，和Github是基本一样的





@Author ： By Runsen


**未经同意，不准转载**
