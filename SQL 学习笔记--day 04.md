# SQL学习笔记

在字段名出现的地方，都可以用表达式来指定对字段名进行一定的计算或处理。

## as 关键字

作用：给表达式取一个别名

```mysql
select col_expression as expr_description

from mytable;
```

as 不仅能用在表达式别名上，普通的属性列，甚至是表，都可以取一个别名

```mysql
select column as better_column_name
from a_long_widgets_table_name as mywidgets
inner join widget_sales
on mywidgers.id = widget_sales.widget_id;
```

## 分组统计

`group by`可以按某个col_name对数据进行分组

`group by`分组结果的数据条数，就是分组数量

```mysql
select FUNC(column_or_expression) as aggregate_description
from mytable
where constraint_expression
group by column;
```

`having`可以对分组之后的数据再做select筛选

```mysql
select group_by_column, FUNC(column_expression) as aggregate_result_alias,
from mytable
where condition
group by column
having group_condition;
```

`having`和`where`语法一样，只不过作用的结果集不同

## 查询顺序

* 完整的`select`查询

```mysql
select distinct column, FUNC(column_or_expression)
from mytable
join another_table
on mytable.column = another_table.column
where constraint_expression
group by column
having constraint_expression
order by column asc/desc
limit count offset count;
```

一个查询语句的执行总是先从数据里按条件选出数据，然后对这些数据再次做一些整理处理，最后按要求返回结果

## 多张表的连接

```mysql
select column
from mytable
join table_one
on condition_one
join table_two
on condition_two
join table_three
on condition_three
```

## 子查询

`select`语句中嵌套`select`语句，被嵌套的`select`语句被称为子查询

```mysql
select
...(select)
from 
...(select)
where
...(select)
```

## union 合并查询结果集

```mysql
select column_one from mytable_one where condition_one
union
select column_two from mytable_two where condition_two
```

`union`可以减少匹配的次数，同时完成两个结果集的拼接，但要求两个结果集的列数相同

## 执行顺序

1. `from`
2. `where`
3. `group by`
4. `having`
5. `select`
6. `order by`
7. `limit`

