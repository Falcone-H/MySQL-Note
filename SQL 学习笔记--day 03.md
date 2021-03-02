# SQL学习笔记

## 过滤

`distinct`关键字，指定某个或某些属性列唯一返回，会直接删除重复的行

`select distinct column from mytable where conditions;`

## 排序

`order by` 让结果按一个或多个属性列做排序

`select column, another_column from mytable where conditions order by column asc/desc;`

`limit` 和 `offset`通常和`order by `一起用，对结果集排序后，用`limit`来指定只返回多少行结果，用`offset`来指定从哪一行开始返回。

```mysql
select column, another_column
from mytable
where conditions
order by column asc/desc
limit num_limit offset num_offset;
```

## 用JOINs进行多表联合查询

* 主键（primary key）

  一般的关系数据表中，都会有一个属性列设置为主键。主键使唯一标识一条数据的，不会重复。最常见的主键就是`auto-incrementing integer`

我们可以把两个表中具有相同主键ID的数据连接起来，需要用到`JOIN`关键字

```mysql
select column, another_table_column
from mytable
inner join another_table
on mytable.id = another_table.id
where conditions
order by column asc/desc
limit num_limit offset num_offset;
```

通过`on`条件描述关联关系

`inner join`先将两个表数据连接到一起，两个表中如果通过ID互相得不到数据，将会丢弃

## 外连接（outer joins）

`inner join`只保留两个表都存在的数据，会造成数据的丢失。

因此需要更多的连表方式

* 左连接`left join`，不管能不能匹配上，保留原表的所有行
* 右连接`right join`，不管能不能匹配上，保留连接表的所有行
* 全连接`full join`，不管能不能匹配上，保留原表和连接表的所有行

```mysql
select column, another_column
from mytable
inner/left/right/full join another_table
on mytable.id = another_table.matching_id
where conditions
order by column asc/desc
limit num_limit offset num_offset
```





