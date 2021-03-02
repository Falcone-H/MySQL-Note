# SQL 学习笔记

## 表的创建

```mysql
create table 表名(
	字段名1 数据类型,
	字段名2 数据类型,
	字段名3 数据类型
);
```

## （常见）数据类型

* `varchar`可变长字符串，会根据实际的数据长度动态分配空间。
* `char`定长字符串
* `int`整数型
* `bigint`长整型
* `float`单精度浮点型
* `double`双精度浮点型
* `date`短日期类型
* `datetime`长日期类型
* `clob`字符大对象，最多存储4G的字符串
* `blob`二进制大对象，专门用来存储图片、声音、视频等流媒体数据，需使用IO流

## 删除表

`drop table 表名;`

`drop table if exists 表名;`

## 查看表中的字段

`desc 表名;`

## 插入数据

```mysql
insert into 表名
(字段名1， 字段名2， 字段名3)
values
(值1， 值2， 值3);
```

字段名和值要一一对应。



或者

```mysql
insert into 表名
values
(值1, 值2, 值3);
```

如果省略字段名，则等同于需要给所有的字段赋值

## 插入日期

* `str_to_date`：将字符串`varchar`类型转换成`date`类型

  语法格式：

  `str_to_date('字符串日期', '日期格式');`

  如果输入的字符串日期格式符合`%Y-%m-%d`，那么`str_to_date`也可以省略不写

* `date_format`：将date类型转换成具有一定格式的`varchar`字符串类型

  语法格式：

  `date_format('字符串日期'，‘日期格式’);`

  

## MySQL的日期格式

```mysql
%Y	年
%m	月
%d	日
%h	时
%i	分
%s	秒
```

短日期默认格式：

`%Y-%m-%d`

长日期默认格式：

`%Y-%m-%d %h:%i:%s`

可以通过`now()`获取当前时间

## 修改数据

```mysql
update 表名
set 
字段名1 = 值1,
字段名2 = 值2,
字段名3 = 值3
where 条件;
```

如果不设置条件，会导致所有数据都被更新

## 删除数据

```mysql
delete from 表名
where 条件;
```

如果不设置条件，会导致所有数据都被删除


