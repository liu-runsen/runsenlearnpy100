@Author：Runsen
@Date：2019/03/19


![](https://img-blog.csdnimg.cn/20200527114711364.png)


作者介绍：Runsen目前大三下学期，专业化学工程与工艺，大学沉迷日语，Python， Java和一系列数据分析软件。导致翘课严重，专业排名中下。.在大学60%的时间，都在CSDN。决定今天比昨天要更加努力。



@[TOC]


# MongoDB简介
安装

```csharp
sudo apt-get install mongodb
```

`MongoDB`是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。它支持的数据结构非常松散，是类似`json`的`bson`格式，因此可以存储比较复杂的数据类型。`Mongo`最大的特点是它支持的查询语言非常强大，其语法有点类似于面向对象的查询语言，几乎可以实现类似关系数据库单表查询的绝大部分功能，而且还支持对数据建立索引。

将数据存储为一个文档，文档类似与Json格式，
```
{
    name:"毛利",
    age:18，
    address: {city:"东莞"， country:"china"}
}
```

# MongoDB数据模型

![](https://img-blog.csdnimg.cn/20190319104459695.png)
 **如何进入和退出mongo**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190319104516430.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)
## 库级操作语句



- 显示所有库： `show dbs`
- 切换/创建数据库：` use 数据库名称 `
- 查看所在库： `db`
- 删除库：`db.dropDatabase()  `


## 集合操作语句

- 显示当前数据库的集合：` show collections`
- 创建集合： `db.createCollection(name)`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190319104539962.png)
- 删除集合：` db.集合名称.drop()`


## 文档操作

### 添加文档（数据）

`db.集合名称.insert(document)`

每一条数据，就是一个`document`，就是一条`json`

例：` db.student.insert({name:'毛利', age:18})`

> 注意点：

添加文档时，如果不指定_id参数
MongoDB会为文档分配一个唯一的ObjectId

给定 `_id`
例： `db.student.insert({'_id':1, name:'毛利', age:18})`	

- 添加多条文档
```
db.student.insert([
    {name:'毛利, sex:'男', age:18},
    {name:’毛利的爸爸', sex:'男', age:47},
    {name:’毛利的姐姐', sex:'女', age:23},
    {name:’毛利的妈妈‘, sex:’女', age:44},
])
```


### 查询文档（数据）

`db.集合名称.find([conditions])`

查看集合中全部数据： `db.student.find()`

格式化显示： `db.student.find().pretty() `

查看满足条件的数据： `db.student.find({name:'毛利'})`


### 条件


- and条件  `{$and:[{expression1}, {expression1}, ...]   }`
 

- or条件 `{$or:[{expression1}, {expression1}, ...]   }`





`db.student.find({$or:[{$and:[{sex:'女'}, {age:23}]},{$and:[{sex:'男'}, {age:{$gte:18}}]}]})`


![在这里插入图片描述](https://img-blog.csdnimg.cn/20190319104553439.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDUxMDYxNQ==,size_16,color_FFFFFF,t_70)

### 修改文档（数据）


`db.集合名称.update(<query>, <update>, {multi:<boolean>})`
- 修改一条数据： `db.student.update({sex:'男'}, {age:20})`

把表中的男的`age`改为`20`
- 指定属性修改：` { $set: {age:20} } `


`db.student.update({name:'毛利'}, {$set: {age:666, sex: '不告诉你'}} )`

把毛利的`age`改为`666`，`sex`改为不告诉你

- 更新集合中所有满足条件的文档： `{ multi: true } `

```
db.student.update({sex:'男'}, {$set:{sex:'女'}}, { multi:true} )
```
把所有按的改为女的


### 删除文档（数据）


`db.集合名称.remove(<query>,  {justOne:<boolean>})`


- 删除集合中所有的文档：
`db.student.remove({})`
- 删除集合中满足条件的所有文档
`db.student.remove({sex: '男'})`
- 只删除集合中满足条件的第一条文档： `{ justOne: true } `


```db.student.remove({sex:'男'}, { justOne:true} )```




##  在Python程序中操作MongoDB


可以通过pip安装pymongo来实现对MongoDB的操作。`pip3 install pymongo`

```Shell
>>> from pymongo import MongoClient
>>> client = MongoClient('mongodb://192.168.92.92:27017') 
>>> db = client.school
>>> for student in db.students.find():
...     print('姓名:', student['name'])
```
