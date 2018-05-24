本博文介绍了MongoDB，并详细指引读者在Ubuntu下MongoDB的安装和使用。本教程在Ubuntu14.04下测试通过。 

## 一、MongoDB介绍

MongoDB 是一个是一个基于分布式文件存储的数据库，介于关系数据库和非关系数据库之间，是非关系数据库当中功能最丰富，最像关系数据库的。他支持的数据结构非常松散，是类似json的bson格式，因此可以存储比较复杂的数据类型。Mongo最大的特点是他支持的查询语言非常强大，其语法有点类似于面向对象的查询语言，几乎可以实现类似关系数据库单表查询的绝大部分功能，而且还支持对数据建立索引。

## 二、安装MongoDB

MongoDB安装很简单，无需下载源文件，可以直接用apt-get命令进行安装。 
打开终端，输入以下命令：

```
sudo apt-get install mongodb
```
![image.png](https://upload-images.jianshu.io/upload_images/9135759-3cb41a51c148257b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1.安装完成后，在终端输入以下命令查看MongoDB版本：
```
mongo -version
```
输出版本信息，表明安装成功，截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-8887c3331cd9528f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.启动和关闭mongodb命令如下：
```
service mongodb start
service mongodb stop
```
截图如下：
 ![image.png](https://upload-images.jianshu.io/upload_images/9135759-39cb7f47b78e2337.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.默认设置MongoDB是随Ubuntu启动自动启动的。 
输入以下命令查看是否启动成功：
```
pgrep mongo -l   #注意：-l是英文字母l，不是阿拉伯数字1
```
截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-f7a5306aeaed8158.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
卸载MongoDB
```
sudo apt-get --purge remove mongodb mongodb-clients mongodb-server
```
## 三、使用MongoDB

### shell命令模式

输入`mongo`进入shell命令模式，默认连接的数据库是test数据库，在此之前一定要确保你已经启动了MongoDB，否则会出现错误，启动之后运行成功，如下截图：
![image.png](https://upload-images.jianshu.io/upload_images/9135759-47a98bbf23b2cfc7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
常用操作命令：
数据库相关 
```
show dbs:显示数据库列表 
show collections：显示当前数据库中的集合（类似关系数据库中的表table） 
show users：显示所有用户 
use yourDB：切换当前数据库至yourDB 
db.help() ：显示数据库操作命令 
db.yourCollection.help() ：显示集合操作命令，yourCollection是集合名 
```
MongoDB没有创建数据库的命令，如果你想创建一个“School”的数据库，先运行use School命令，之后做一些操作（如：创建聚集集合db.createCollection('teacher')）,这样就可以创建一个名叫“School”的数据库。
截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-378e2b1d94454111.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 下面以一个School数据库为例，在School数据库中创建两个集合teacher和student，并对student集合中的数据进行增删改查基本操作（集合Collection相当于关系型数据库中的表table）。 
1、切换到School数据库
```
use School #切换到School数据库。MongoDB 无需预创建School数据库，在使用时会自动创建
```
2、创建Collection
```
db.createCollection('teacher') #创建一个聚集集合。MongoDB 其实在插入数据的时候，也会自动创建对应的集合，无需预定义集合
```
截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-81643b44864ee245.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3、插入数据 
与数据库创建类似，插入数据时也会自动创建集合。 
插入数据有两种方式：insert和save。
```
db.student.insert({_id:1, sname: 'zhangsan', sage: 20}) #_id可选
db.student.save({_id:1, sname: 'zhangsan', sage: 22}) #_id可选
```
这两种方式，其插入的数据中_id字段均可不写，会自动生成一个唯一的_id来标识本条数据。而insert和save不同之处在于：在手动插入_id字段时，如果_id已经存在，insert不做操作，save做更新操作；如果不加_id字段，两者作用相同都是插入数据。
截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-f266803fccc124ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

添加的数据其结构是松散的，只要是bson格式均可，列属性均不固定，根据添加的数据为准。先定义数据再插入，就可以一次性插入多条数据，截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-6a2feadc2cbe01c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
运行完以上例子，student 已自动创建，这也说明 MongoDB 不需要预先定义 collection ，在第一次插入数据后，collection 会自动的创建。
截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-d56b0ffb7ecc980a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4、查找数据 
```
db.youCollection.find(criteria, filterDisplay)
 ```
criteria ：查询条件，可选 
filterDisplay：筛选显示部分数据，如显示指定列数据，可选（当选择时，第一个参数不可省略，若查询条件为空，可用{}做占位符，如下例第三句）
```
db.student.find()  #查询所有记录。相当于：select * from student
db.student.find({sname: 'lisi'})  #查询sname='lisi'的记录。相当于： select * from student where sname='lisi'
db.student.find({},{sname:1, sage:1}) #查询指定列sname、sage数据。相当于：select sname,sage from student。sname:1表示返回sname列，默认_id字段也是返回的，可以添加_id:0（意为不返回_id）写成{sname: 1, sage: 1,_id:0}，就不会返回默认的_id字段了
db.student.find({sname: 'zhangsan', sage: 22}) #and 与条件查询。相当于：select * from student where sname = 'zhangsan' and sage = 22
db.student.find({$or: [{sage: 22}, {sage: 25}]}) #or 条件查询。相当于：select * from student where sage = 22 or sage = 25
```
查询操作类似，这里只给出db.student.find({sname: 'lisi'})
查询的截图，如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-75add83f6cda14bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5、修改数据 
```
db.youCollection.update(criteria, objNew, upsert, multi ) 
criteria: update的查询条件，类似sql update查询内where后面的 
objNew : update的对象和一些更新的操作符（如$set）等，也可以理解为sql update查询内set后面的。 
upsert : 如果不存在update的记录，是否插入objNew，true为插入，默认是false，不插入。 
multi: mongodb默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。默认false，只修改匹配到的第一条数据。 
其中criteria和objNew是必选参数，upsert和multi可选参数 
```
举例如下：
```
db.student.update({sname: 'lisi'}, {$set: {sage: 30}}, false, true) #相当于：update student set sage =30 where sname = 'lisi';
```
操作截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-9a33162889a67bd9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
6、删除数据
```
db.student.remove({sname: 'chenliu'}) #相当于：delete from student where sname='chenliu'
```
操作截图如下： 
![image.png](https://upload-images.jianshu.io/upload_images/9135759-bb17d02c7a2f0f8c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

7、退出shell命令模式 
输入exit或者Ctrl+C退出shell命令模式
***
参考MongoDB官方文档：
```
https://docs.mongodb.com/master/tutorial/install-mongodb-on-ubuntu/?_ga=2.38644067.1704633038.1522762185-1747967431.1522762185
```
