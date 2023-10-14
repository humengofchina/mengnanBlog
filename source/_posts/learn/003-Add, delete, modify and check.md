---
title: 库、表、记录的语法
comments: true
date: 2023-10-14 08:38:58
categories:
- sql语言的引入
- mysql的库、表、记录
tags:
- 学习
- MySQL数据库
---
# 2023-7-2-MySQL数据库-库表记录的增删改查

![](https://cdn.pixabay.com/photo/2017/02/15/20/33/floral-2069810_1280.png)

<!-- more -->

和微信公众号文章不同之处在于，本文章只有笔记（没有具体的操作步骤）

微信公众号原文【[2023-7-2-MySQL数据库-库的增删改查](https://mp.weixin.qq.com/s?__biz=MzkxODQ0Njg4OA==&mid=2247484747&idx=1&sn=dc395e2c7e2fc41f332033fe8a8f1dc8&chksm=c1b0730cf6c7fa1a964d77b9da1f0b3ec76657c87a08f4587c453ea6d9cdffd8f683e7639115&token=1886811740&lang=zh_CN#rd)】【[2023-7-3-MySQL数据库-表和记录](https://mp.weixin.qq.com/s?__biz=MzkxODQ0Njg4OA==&mid=2247484761&idx=1&sn=6456b11d7d60d3baf3f369c8e16cd2ff&chksm=c1b0731ef6c7fa0843a16acca4622ecbe7fd1f30d96cd46267f2f675b5d05d793c6e50bb8565&token=1886811740&lang=zh_CN#rd)】

**一、学习回顾**

忘记密码时跳过验证修改密码的步骤及跳过验证直接修改密码：

```mysql
# 忘记密码
mysqld --skip-grant-tables # 跳过授权验证启动服务端
mysql -uroot -p #跳过验证启动的服务端，可以免密码登陆
update mysql.user set authentication_string=password('123') where user='root'and host = 'localhost'; # 修改密码
flush privileges; # 刷新权限

tasklist | findstr mysql # 查看占⽤mysql程序的进程
netstat -ano | findstr 3306 # 查看占⽤3306端⼝的进程
taskkill /F /PID 进程ID # 杀掉该进程
mysqld # 启动正常的服务端
```

具体操作在微信公众号文章内【[点击这里](https://mp.weixin.qq.com/s?__biz=MzkxODQ0Njg4OA==&mid=2247484747&idx=1&sn=dc395e2c7e2fc41f332033fe8a8f1dc8&chksm=c1b0730cf6c7fa1a964d77b9da1f0b3ec76657c87a08f4587c453ea6d9cdffd8f683e7639115&token=1886811740&lang=zh_CN#rd)】

**二、学习记录**

1、简单SQL语句基础：

```mysql
1、MySQL的注意事项：
-- 每一条SQL语句都是以分号结尾的 即 ；和c语言一样
-- SQL语句的单行注释是-- ，而python的单行注释是#号。
-- SQL的多行注释是/*注释内容*/ 和Java语言一样，而Python的多行注释是'''注释内容'''

2、MySQL中概念部分：
库 ——> 文件夹
表 ——> 文件夹内的文件
记录——> 文件内的一行行数据

3、简单命令：
show databases;  -- 查看所有数据库
\s -- 查看字符编码及其他信息
\c 或者快捷键 ctrl c -- 清除当前输入语句（写错了，跳出去，重新写）
exit; 或者 quit; --退出连接（后面分号可有可无）
help -- 帮助命令，获得更多命令（help后面跟不懂的命令，可以得到解释）
```

操作库语法命令：

```mysql
-- 增
create database db1 charset=utf8; -- 创建数据库db1（db1是数据库的名称，可自定义命名）
-- 删
drop database db1;  --删除数据库（网上经常说的删库跑路就是这个）
-- 改
数据库没有什么可以改的，只有改字符编码
alter database db1 charset=gbk; -- 修改db1数据库的字符编码为gbk
-- 查
show databases; -- 查询所有数据库
show create database db1; -- 查询db1这一个数据库

-----------------------------------------------------这是分割线

-- 增
create database if not exists db1 charset=utf8; -- db1不存在就会创建，存在也不会报错
-- 删
drop database if exists db1;  --db1存在就删除，不存在也不会报错
```

操作表的语法命令   ：

```mysq
-- 前面说，表对应的是文件，那么文件应该放在文件夹里面吧！即表在库下面。
use db1;  -- 切换到db1数据库
select database();  -- 查看当前所在数据库

-- 增
create table movies (age int, name char )charset=utf8;  -- 创建表（创建表头，且规定表头数据类型）并指定字符编码为utf8
-- 删
drop table movies;  -- 删除movies这个表
-- 改
alter table movies modify name char(4);  --修改字段类型
alter table movies change name Name char(16); --修改小写的字段名name为大写开头的Name字段名，且修改字段类型
-- 查
show tables;  -- 查看当前库下所有的表
show create table movies;  -- 查看创建的movies表
describe movies;  -- 查看表的结构 （可以简写为desc movies;)
```

操作记录的语法命令：

```mysq
-- 增
insert into movies values(18 ,'mengnan' );  -- 插入一条记录
insert into movies values(18 ,'mengnan'),(17 ,'zh'); -- 插入多条记录 
-- 删
delete form movies;  -- 删除movies的所有记录
delete form movies where name='mengnan'; -- 删除movies的mengnan的所有记录
-- 改
update movies set name='zh' where age=18;  -- 将age=18的mengnan改为zh（不写条件所有的name都会改为zh）
-- 查
select * from movies;  --查movies这个表的所有数据（当进入公司后，数据会非常大，尽量不要用这个命令）
select age ,Name from movies;  --查询movies这个表中的age和Name字段
```

#### 三、原文链接：

[2023-7-2-MySQL数据库-库的增删改查 (qq.com)](https://mp.weixin.qq.com/s?__biz=MzkxODQ0Njg4OA==&mid=2247484747&idx=1&sn=dc395e2c7e2fc41f332033fe8a8f1dc8&chksm=c1b0730cf6c7fa1a964d77b9da1f0b3ec76657c87a08f4587c453ea6d9cdffd8f683e7639115&token=1886811740&lang=zh_CN#rd)

[2023-7-3-MySQL数据库-表和记录 (qq.com)](https://mp.weixin.qq.com/s?__biz=MzkxODQ0Njg4OA==&mid=2247484761&idx=1&sn=6456b11d7d60d3baf3f369c8e16cd2ff&chksm=c1b0731ef6c7fa0843a16acca4622ecbe7fd1f30d96cd46267f2f675b5d05d793c6e50bb8565&token=1886811740&lang=zh_CN#rd)


