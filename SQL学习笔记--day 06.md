# SQL学习笔记

## 一次插入多条记录

```mysql
insert into 表名
(字段名1, 字段名2, 字段名3)
values
(值1, 值2, 值3),
(值4, 值5, 值6);
```

## 快速创建表

```mysql
create table 表名 as select * from 另一个表名;
```

```mysql
create table 表名 as select 字段名 from 另一个表名 where 条件;
```

相当于用`select`的结果生成一张表

## 将查询结果插入一张表中

```mysql
insert into 表名 select * from 另一个表名;
```

## 快速删除表中数据

原来删除数据语句：

```mysql
delete from 表名 where 条件;
```

这种删除数据方式会比较慢，会删除数据，不会释放空间。优点是支持回滚，可回复数据

```mysql
truncate table 表名;
```

这张删除数据效率比较高，表被一次截断，但不支持回滚。

## 删除表

```mysql
drop table 表名;
```

## 对表进行修改

向表中添加列

```mysql
alter table 表名 add 字段名 字段类型;
```

删除表中的列

```mysql
alter table 表名 drop column 字段名;
```

修改字段类型

```mysql
alter table 表名 modify column 字段名 字段类型
```

## 创建自增字段

```mysql
create table (
字段名1 数据类型 primary key auto_increment,
字段名2 数据类型,
字段名3 数据类型);
```

## 创建表时加入约束

约束的作用：为了保证表中的数据有效

* 非空约束：`not null`
* 唯一性约束：`unique`
* 主键约束：`primary key`
* 外键约束：`foreign key`

使用方法：

```mysql
create table 表名(
字段名 数据类型 约束条件)
```

约束直接加在列后面的，叫做列级约束。

## 使某两个字段合起来具有唯一性

```mysql
create table 表名(
字段名1 数据类型，
字段名2 数据类型，
unique(字段名1, 字段名2));
```

这种约束称为表级约束

not null 只有列级约束，没有表级约束

在MySQL中，如果一个字段同时被`not null`和`unique`约束的话，该字段自动变成主键字段。

主键值是每一行记录的唯一标识

## 外键约束（foreign key）

```mysql
create table 表名(
字段名1 数据类型,
字段名2 数据类型,
foreign key(字段名1) references 另一个表(字段名));
```

子表中的外键引用的父表中的某个字段，不一定是主键，但至少具有unique约束