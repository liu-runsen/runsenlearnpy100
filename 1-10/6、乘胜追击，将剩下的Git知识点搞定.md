
@Author ： By Runsen
@Author ： 2020/5/15




先上图回顾回顾
![](https://img-blog.csdnimg.cn/20190801172352872.png)
![](https://img-blog.csdnimg.cn/20190801172403911.png)


@[TOC]


# 1、对比文件


![](https://img-blog.csdnimg.cn/2020051519080911.png)

我先通过git log 查看以前的信息。对比文件的命名很简单


```css
git diff HEAD HEAD^ -- 文件名
```

HEAD表示当前的版本，HEAD^ 表示上一个版本。
![](https://img-blog.csdnimg.cn/20200515190922878.png)


# 2、文件删除


删除没有添加进版本库中的工作区中的文件，那直接删除不用做任何操作。

如果已添加进工作区但没有提交的文件，先要先撤回工作区


比如，现在我写了一个`文件添加到版本库.txt`。


![](https://img-blog.csdnimg.cn/20200515191245233.png)



先提交下，git status 查看状态，绿色就是在版本库。



![](https://img-blog.csdnimg.cn/2020051519143026.png)
现在就是使用



```css
git reset HEAD

 ```


就可以撤销了，不行git status 查看状态，红色就是在工作区。






![](https://img-blog.csdnimg.cn/20200515191748504.png)


如果我已提交到版本库，突然间我发现写错了代码，老板看了，肯定扣我工资 ，不行，我赶紧要回来。



![](https://img-blog.csdnimg.cn/20200515192532376.png?)


去码云看看，发现存在了。现在怎么把这个文件撤回呢？

![](https://img-blog.csdnimg.cn/20200515192615841.png)


有人说，我直接去Github码云上删除，恩，是一种办法，而且是一个猪办法



![](https://img-blog.csdnimg.cn/20200515193131734.png)
如果项目不是在你的账号创建的，就没资格用客户端删东西。




答案就是回滚，再提交，只需要执行：



```css
git revert HEAD
git push
```


![](https://img-blog.csdnimg.cn/20200515193748656.png)




这时候就没有了
![](https://img-blog.csdnimg.cn/20200515193809887.png)

# 3、创建分支

正常的开发项目中都是多人协作，每个人的任务一般不会一天就完成，如果把没有完成的代码提交到远程仓库会影响被人工作。git提供了分支的功能就不用担心了，可以创建一个自己的分支，在上面干活，想提交就提交，等到工作完成再一次性合并到原来的分支。



新建git仓库时会默认创建一个分支master，它叫主分支。一般情况我们不会直接在主分支上干活，它主要用来发布版本。


我创建一个开发分支develop



```css
git branch develop
```


再切换到develop分支

```css
git checkout develop

```

‘
![](https://img-blog.csdnimg.cn/20200515194148130.png)

使用git branch命令查看当前分支。-b参数表示创建并切换。



如果想创建的时候，直接切换，直接-b参数


```css
git checkout-b  develop 

```


# 4、合并分支



创建好develop分支，菜比的我，24小时之后开发完毕，提交：


![](https://img-blog.csdnimg.cn/20200515194525171.png)




```css
$ git add .
$ git commit -m '24小时之后开发完毕'

```


![](https://img-blog.csdnimg.cn/20200515194625617.png)

现在切换到master


```css
$ git checkout master
Switched to branch 'master'
```


查看工作区，你会发现刚才写的文件没有了，不要惊慌，因为那个提交是在develop分支上，现在Runsne把develop分支的工作合并到master分支上：


![](https://img-blog.csdnimg.cn/20200515194803519.png)





```css
git merge develop
```





![](https://img-blog.csdnimg.cn/20200515194857226.png)



这个时候就出现了
![](https://img-blog.csdnimg.cn/20200515194917844.png)



# 5、删除分支




合并完之后你也可以删除掉develop分支：

```css
$ git branch -d develop
Deleted branch develop (was 25942c9)).
$ git branch
* master
```







![](https://img-blog.csdnimg.cn/20200515195109608.png)







OK搞定，把之前的Git文章全部删除


![](https://img-blog.csdnimg.cn/20200515195234117.png)
