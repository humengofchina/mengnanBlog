---
title: sql语言的引入
comments: true
date: 2023-10-05 22:04:58
categories:
- sql语言的引入
- mysql安装及配置
tags:
- 学习
- MySQL数据库
---
# 2023-7-1-MySQL数据库-MySQL安装配置

![](https://cdn.pixabay.com/photo/2023/09/29/07/49/grassland-8283155_1280.jpg)

<!-- more -->
原文链接：【[点击这里](https://mp.weixin.qq.com/s?__biz=MzkxODQ0Njg4OA==&mid=2247484729&idx=1&sn=f690d8280b491a34d237cb36edfb799b&chksm=c1b0737ef6c7fa68d91864d505ad4b6b2173b3dc0972e28a9b83c81d82460098334b8011111a&token=1886811740&lang=zh_CN#rd)】

#### 一、学习回顾：

前面简单介绍了数据库的种类，用途，规范。下面来看MySQL的安装。

#### 三、准备工作：

Windows电脑，网络，动手动脑。

#### 四、安装步骤：

1、打开浏览器，粘贴转到以下链接

MySQL下载：https://downloads.mysql.com/archives/community /

2、选择如图所示的版本，点击download下载即可

3、下载完成后，移动到桌面，并且解压当前路径，然后将解压后的文件移动到你的磁盘中，只要记得住路径（路径不要有中文），C盘D盘都可以，我这里是E盘。最后压缩包可以删除。（跨盘移动是复制，桌面上的解压后文件可以删除）

4、Too simple！安装完成！

#### 五、配置MySQL：（详细见视频1）

1、配置环境变量

\# 把bin路径配置在环境变量（前面安装creo时配置过环境变量，这个应该很熟悉吧！）

粘贴bin的路径后，碰到页面就点确定即可。

2、初始化数据库命令：（需要用管理员权限的cmd）

```sql
mysqld --initialize-insecure --user=mysql
```

3、启动服务端命令：

```sql
mysqld
```

4、连接MySQL命令：

```sql
mysql -u root -p
```

5、重置密码命令：

```sql
mysqladmin -uroot -p原密码 password 123
```

6、忘记密码操作及其命令：

```sql

# 忘记密码
mysqld --skip-grant-tables # 跳过授权验证启动服务端
mysql -uroot -p #跳过验证启动的服务端，可以免密码登陆
update mysql.user set
authentication_string=password('123') where
user='root'and host = 'localhost'; # 修改密码
flush privileges; # 刷新权限

tasklist | findstr mysql # 查看占⽤mysql程序的进程
netstat -ano | findstr 3306 # 查看占⽤3306端⼝的进程
taskkill /F /PID 进程ID # 杀掉该进程
mysqld # 启动正常的服务端

```

7、添加MySQL服务命令：

```sql
mysqld -install # 添加服务
mysqld -remove # 移除服务
net start mysql # 启动服务
net stop mysql # 停⽌服务
```

8、统一字符编码命令：（见视频2)

```sql

# 在mysql根⽬录新建my.cnf⽂件，做如下配置：
[mysqld]
character-set-server=utf8
collation-server=utf8_general_ci
[client]
default-character-set=utf8
[mysql]
default-character-set=utf8
# 修改完配置⽂件之后，需要重启mysql服务
net stop mysql
net start mysql
```

#### 六、文章结束，明天学习——MySQL数据库—库的创建



