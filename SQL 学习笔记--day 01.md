# SQL 学习笔记

## 一、SQL语句分类

* DQL：

  数据查询语言（凡是带有select关键字的都是数据查询语句）

  `select`

* DML：

  数据操作语言（凡是对表当中的数据进行增删改，都是数据操作语句）

  `insert` 	`delete`  	`update` 

* DDL：

  数据定义语言（凡是带有`create` 、`drop` 、`alter` 的都是DDL）

  DDL主要操作的是表的结构，不是表中的数据

* TCL：

  事务控制语言，包括：

  ​	事务提交：`commit` 

  ​	事物回滚：`rollback` 

* DCL：

  数据控制语言

  例如：授权——`grant` ，撤销权限——`revoke` ...

## 二、进入MySQL步骤

1、`net start mysql` 开启MySQL服务

2、`mysql -u root -p` MySQL登录验证，然后输入密码

３、`show databases;` 查看本地的数据库

4、`use database_name;` 进入某一个数据库

5、`show tables;` 查看当前数据库中有哪些表

6、`create database_name` 创建新的数据库

## 三、查看表中数据

所有SQL语句以分号结尾，不区分大小写

* 查询所有字段 `select * from 表名;` 

* 查询单个字段 `select 字段名 from 表名;`

* 查询多个字段，用逗号隔开 `select 字段名1, 字段名2, 字段名3 from 表名;`

* 不看表中的数据，只看表的结构：

  `desc table_name;` 

### 1、条件查询

查询出符合条件的数据

语法格式：

​	`select 字段一, 字段二, 字段三`

​	`from 表名`

​	`where 条件;` 

如，一个名为`test_table`表中有`id`, `money` 两项字段

* `select id, money from test_table where money >= 1000;`

  查询表中`money`大于等于1000 的数据

* `select id, money from test_table where money between 500 and 5000;`

  查询表中`money`在区间500到5000的数据

* `select id, money from test_table where money is not null;`

  查询表中`money`不为空的数据

* `select id, money from test_table where money >= 1000 and id > 2;`

  查询表中`money`大于1000 且 id 大于2的数据

* `select id, money from test_table where money >= 1000 or id > 2;`

  查询表中`money`大于1000 或 id 大于2 的数据

* `select id, money from test_table where money in (10, 20, 30);`

  查询表中`money`在10，20，30中的数据

### 2、like 模糊查询

支持 `%` 或 `_` 匹配

`%`  ：匹配任意多个字符

`_` ：匹配任意一个字符

`select * from test_table where money '%1%';`

找出表中`money`含有数字1的数据

`select * from test_table where money '%\_%';`

找出表中`money`含有下划线的数据（用转义字符）

### 3、排序

`select * from test_table order by money;`

查询所有数据，并按照`money`升序排列（默认升序排列，asc）

`select * from test_table order by money desc;`

加上`desc`，降序排列

### 4、多个字段排序

`select * from test_table order by money asc, id desc;`

按照`money`的升序排列，如果`money`一样，则按照`id`的降序排列