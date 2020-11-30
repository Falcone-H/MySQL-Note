# SQL 学习笔记 --- Day 02

## 数据处理函数

数据处理函数，又被称为单行处理函数，特点：一个输入对应一个输出。

与单行处理函数相对的，叫做多行处理函数，特点：多个输入对应一个输出

##　常见单行处理函数

* `lower` 转换成小写

  `select lower(money) from test_table;`

* `upper` 转换成大写

  `select upper(money) from test_table;`

* `substr` 取子串，格式：`substr(被截取的字符串，起始下标，截取长度)`

  MySQL的下标从1开始

  `select substr(money, 1, 2) from test_table;`

  `select money from test_table where substr(money, 1, 1) = '1';`

* `length` 长度

  `select length(money) from test_table;`

* `trim` 去除前后空格

  `select * from test_table where money = trim('     1000      ');`

* `concat` 拼接字符串，格式：`concat(字符串1， 字符串2)`
* `format` 设置千分位
* `round` 四舍五入，格式：`round(小数，要保留的小数位数)`
* `rand` 生成随机数
* `ifnull` 将null转换成一个具体值，格式：`ifnull(字段名, 替换值)`
* `case ... when ... then ... when ... then ... else ... end`

## 分组查询

（多行处理函数）

* count 计数

  `select count(money) from test_table;`

* sum 求和

  `select sum(money) from test_table;`

* avg 平均值

  `select avg(money) from test_table;`

* max 最大值

  `select max(money) from test_table;`

* min 最小值

  `select min(money) from test_table;`

### 注意：

分组函数在使用的时候必须先进行分组，然后才能用。如果没有对数据分组，则整张表默认为一组。

分组函数自动忽略NULL，不需要提前对NULL进行处理。

count(*) 和count(具体字段)的区别：

​	count(具体字段) ：表示统计该字段下所有不为NULL的元素的总数

​	count(*) ：表示统计表中的总行数

每一行数据中，总有一个字段不为NULL，意思是表中所有数据都一定有效

分组函数不能直接使用在where子句中