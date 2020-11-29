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

