**启动与停止**

启动

​		net start mysql80

停止

​		net stop mysql80

**客户端连接**

方式一：mysql提供的客户端命令行工具

方式二：系统自带的命令行工具执行指令(需要配置环境变量)

​				mysql [-h 127.0.0.1] [-p 3306] -u root -p

# 1.数据模型

## 关系型数据库

概念：建立在关系模型基础上，由多张相互连接的二维表组成的数据库。

**特点：**

​		使用表存储数据，格式统一，便于维护

​		使用sql语言操作，标准统一，使用方便

# 2.SQL

## SQL通用语法

1. SQL语句可以单行或多行书写，以分号结尾。

2. SQL语句可以使用空格/缩进来增强语句的可读性。

3. MySQL数据库的SQL语句不区分大小写，关键字建议使用大写。

4. 注释：单行注释：-- 注释内容 或 # 注释内容（MySQL特有）

   ​			多行注释：/* 注释内容 */

## SQL分类

| 分类 | 全称                       | 说明                                                   |
| ---- | -------------------------- | ------------------------------------------------------ |
| DDL  | Date Definition Language   | 数据定义语言，用来定义数据库对象（数据库，表，字段）   |
| DML  | Date Manipulation Language | 数据操作语言，用来对数据库表中的数据进行增删改         |
| DQL  | Date Query Language        | 数据查询语言，用来查询数据库中表的记录                 |
| DCL  | Date Control Language      | 数据控制语言，用来创建数据库用户、控制数据库的访问权限 |

### DDL

------

**查询**

​		查询所有数据库

```mysql
SHOW DATABASES;
```

​		查询当前数据库

```mysql
SELECT DATABASE();
```

**创建**

```mysql
CREATE DATABASE [IF NOT EXISTS] 数据库名 [DEFAULT CHARSE 字符集] [COLLATE 排序规则];
-- 如果不存在则创建，存在则无操作
-- 字符集指 utf8，utf8mb4 这种类似，一般省略，因为数据库有默认的字符集
-- 括号括起来的都是可选的
```

**删除**

```mysql
DROP DATABASE [IF EXISTS] 数据库名;
```

**使用**

```mysql
USE 数据库名;
```

------



#### 表操作-查询

**查询当前数据库所有表**

```mysql
SHOW TABLES;
```

**查询表结构**

```mysql
DESC 表名;
```

**查询指定表的建表语句**

```mysql
SHOW CREATE TABLE 表名;
```

------
#### 表操作-创建

```mysql
CREATE TABLE 表名(

​		字段1 字段1类型[COMMENT 字段1注释],

​		字段2 字段2类型[COMMENT 字段2注释],

​		..............................

)[COMMENT 表注释];-- [...]为可选参数，最后一个字段后面没有逗号。
-- 字符串类型为 varchar(..)
```

------




```mysql
mysql> create table user(
    -> id int comment '身份证号',
    -> name varchar(50) comment '姓名',
    -> age int comment '年龄',
    -> gender varchar(1) comment '性别'
    -> )comment '用户表';
```

```mysql
mysql> select database();
+------------+
| database() |
+------------+
| itcast     |
+------------+
```

```mysql
mysql> show tables;
+------------------+
| Tables_in_itcast |
+------------------+
| user             |
+------------------+
```

```mysql
mysql> desc user;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | YES  |     | NULL    |       |
| name   | varchar(50) | YES  |     | NULL    |       |
| age    | int         | YES  |     | NULL    |       |
| gender | varchar(1)  | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
```

```mysql
mysql> show create table user;
+-------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table | Create Table


                                        |

+-------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| user  | CREATE TABLE `user` (
  `id` int DEFAULT NULL COMMENT '身份证号',
  `name` varchar(50) DEFAULT NULL COMMENT '姓名',
  `age` int DEFAULT NULL COMMENT '年龄',
  `gender` varchar(1) DEFAULT NULL COMMENT '性别'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci COMMENT='用户表' |
+-------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
-- charset就是字符集，collate就是排序，--engine是数据引擎
```

------

#### 表操作-数据类型

MySQL中的数据类型有很多，主要分为三类：数值类型、字符串类型、日期时间类型。

##### **数值类型**

![image-20230613135249953](C:/Users/龚曦/AppData/Roaming/Typora/typora-user-images/image-20230613135249953.png)

**有符号和无符号类型范围**

无符号类型是在**数据类型后**加上**UNSIGNED**。

##### **字符串类型**

用的比较多的是char和varchar

| char    | 0-255 bytes   | 定长字符串 |
| ------- | ------------- | ---------- |
| varchar | 0-65535 bytes | 变长字符串 |

char的效率高，varchar相对来说较低，因为要计算空间。

##### **日期时间类型**

| 类型      | 大小 | 范围 | 格式                  | 描述                     |
| --------- | ---- | ---- | --------------------- | ------------------------ |
| DATE      | 3    |      | YYYY--MM-DD           | 日期值                   |
| TIME      | 3    |      | HH:MM:SS              | 时间值或持续时间         |
| YEAR      | 1    |      | YYYY                  | 年份值                   |
| DATETIME  | 8    |      | YYYY--MM--DD HH:MM:SS | 混合日期和时间值         |
| TIMESTAMP | 4    |      | YYYY--MM--DD HH:MM:SS | 混合日期和时间值，时间戳 |

------





#### 表操作-修改

------

**添加字段**

```mysql
ALTER TABLE 表名 ADD 字段名 类型(长度) [COMMENT 注释] [约束];
```

**修改数据类型**

```mysql
ALTER TABLE 表名 MODIFY 字段名 新数据类型(长度);
```

**修改字段名和字段类型**

```mysql
ALTER TABLE 表名 CHANGE 旧字段名 新字段名 类型(长度) [COMMENT 注释] [约束];
```

**删除字段**

```mysql
ALTER TABLE 表名 DROP 字段名;
```

**修改表名**

```mysql
ALTER TABLE 表名 RENAME TO 新表名;
```

------





#### 表操作-删除

------

**删除表**

```mysql
DROP TABLE [IF EXISTS] 表名;
```

**删除指定表，并重新创建该表**

```mysql
TRUNCATE TABLE 表名;-- 删除数据
```

------

### DML

------

添加数据（INSERT)

修改数据（UPDATE)

删除数据(DELETE)

------

#### 添加数据

1.给指定字段添加数据

```mysql
INSERT INTO 表名(字段名1，字段名2，...) VALUES (值1，值2，...);
```

2.给全部字段添加数据

```mysql
INSERT INTO 表名 VALUES (值1，值2，...);-- 和字段顺序一一对应
```

3.批量添加数据

```mysql
INSERT INTO 表名(字段名1，字段名2，...) VALUES(值1，值2，...)，(值1，值2，...);
```

```mysql
INSERT INTO 表名 VALUES(值1，值2，...)，(值1，值2，...);-- 和字段顺序对应
```

**注意**：

- 插入数据时，指定的字段顺序需要与值的顺序是一一对应的。

- 字符串和日期型数据应该包含在引号中。

- 插入的数据大小，应该在字段的规定范围内。

  ------

  

```MySQL
insert into itcast.user(id, name, age, gender) values (1,'张三',18,'男');
insert into itcast.user(id, name, age, gender) values (2,'李四',20,'男'),(3,'王五',23,'男');
select * from itcast.user;
```

1,张三,18,男
2,李四,20,男
3,王五,23,男

------

#### 修改数据

```mysql
UPDATE 表名 SET 字段名1=值1，字段名2=值2，...[WHERE 条件];
```

------

#### 删除数据

```mysql
DELETE FROM 表名 [WHERE 条件];
```

**注意**：

- DELETE语句的条件可以有，也可以没有，如果没有哦条件，则会删除整张表的数据。

- DELETE语句不能删除某一个字段的值(可以使用UPDATE)。

  ------

  

```mysql
update itcast.user set name = '1' where id=1;
```

1,1,18,男
2,李四,20,男
3,王五,23,男

------

```MySQL
delete from itcast.user where age= 18;
```

2,李四,20,男
3,王五,23,男

------

### DQL

------

查询关键字：**SELECT**

#### 基本查询

**1.查询多个字段**

```MySQL
SELECT 字段1，字段2，字段3 ... FROM 表名;
```

```MySQL
SELECT * FROM 表名;-- 不直观，少用
```

**2.设置别名**

```mysql
SELECT 字段1 [AS 别名]，字段2 [AS 别名2] ... FROM 表名;-- as可以省略
```

**3.去除重复记录**

```mysql
SELECT DISTINCT 字段列表 FROM 表名;
```

------

#### 条件查询

**1.语法**

```mysql
SELECT 字段列表 FROM 表名 WHERE 条件列表;
```

**2.条件**

| 比较运算符          | 功能                                            |
| ------------------- | ----------------------------------------------- |
| <> 或 !=            | 不等于                                          |
| BETWEEN ... AND ... | 在某个范围之内(含最小、最大值)  （数字小的在前) |
| IN(...)             | 在in之后的列表中的值，多选一                    |
| LIKE 占位符         | 模糊匹配（_匹配单个字符，%匹配任意个字符）      |
| IS NULL             | 是NULL                                          |
| AND 或 &&           | 并且（多个条件同时成立）                        |
| OR 或 \|\|          | 或者（多个条件任意一个成立）                    |
| NOT 或 ！           | 非，不是                                        |

还有一些 大于，大于等于等等基础的就不罗列了。

```mysql
select * from emp where age=18 or age=20 or age=40;

selcet * from emp where age in(18,20,40);-- 等价
```

```mysql
select * from emp where name like '__';-- 查询名字两个字的所有人

select * from emp where idcard like '%X';-- 查询身份证号末尾为X的人
```

------

#### 聚合函数

将一列数据作为一个整体，进行纵向计算。

------

**常见聚合函数**

| 函数  | 功能     |
| ----- | -------- |
| count | 统计数量 |
| max   | 最大值   |
| min   | 最小值   |
| avg   | 平均值   |
| sum   | 求和     |

------

**语法**

```mysql
SELECT 聚合函数 (字段列表) FROM 表名;
```

**注意：null值不参与所有聚合函数运算**

```mysql
select count(*) from emp;-- 计算有多少行(员工数量)
```

------

#### 分组查询

------

**1.语法**

```mysql
SELECT 字段列表 FROM 表名 [WHERE 条件] GROUP BY 分组字段名 [HAVING 分组后过滤条件];
```

**2.where与having区别**

- 执行时机不同：where是分组之前进行过滤，不满足where条件，不参与分组；而having是分组之后对结果进行过滤。

- 判断条件不同：where不能对聚合函数进行判断，而having可以。

  ------

  

```mysql
select count(*) from emp where age<45 group by workaddress having count(*)>=3

select count(*) work_count from emp where age<45 group by workaddress having work_count>=3-- 等价，区别是使用了别名。意义是查询：年龄小于45，并且根据工作地点分组，获取员工数量大于等于3的工作地点。
```

------

#### 排序查询

------

**1.语法**

```mysql
SELECT 字段列表 FROM 表名 ORDER BY 字段1 排序方式1，字段2 排序方式2;
```

**2.排序方式**

- ASC：升序(默认值)
- DESC：降序

**注意：如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序。**

------



```mysql
select * from emp order by age asc , entrydate asc;-- 先按年龄排序，年龄相同的再按照入职日期排序
```

------

#### 分页查询

------

**1.语法**

```mysql
SELECT 字段列表 FROM 表名 LIMIT 起始索引，查询记录数;
```

**注意**

- 起始索引从0开始，起始索引=（查询页面-1）*每页显示记录数。
- 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT。
- 如果查询的是第一页数据，起始索引可以省略，直接简写为limit 10。

------

**执行顺序**

from-where-group by-having-select-order by-limit

**编写顺序**

select-from-where-group by-having-order by-limit

------

### DCL

------

#### 用户管理

**1.查询用户**

```MySQL
USE mysql;

SELECT * FROM user;
```

**2.创建用户**

```mysql
CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';-- 在哪一个主机上这个用户可以访问mysql
```

**3.修改用户密码**

```mysql
ALTER USER '用户名'@'主机名' IDENTIFIED WITH mysql_native_password BY '新密码';
```

**4.删除用户**

```mysql
DROP USER '用户名'@'主机名';
```

------

#### 权限控制

常用的有以下几种：

|        权限        |        说明        |
| :----------------: | :----------------: |
| ALL，ALL PRIVLEGES |      所有权限      |
|       SELECT       |      查询数据      |
|       INSERT       |      插入数据      |
|       UPDATE       |      修改数据      |
|       DELETE       |      删除数据      |
|       ALTER        |       修改表       |
|        DROP        | 删除数据库/库/视图 |
|       CREATE       |   创建数据库/表    |

**1.查询权限**

```mysql
SHOW GRANTS FOR '用户名'@'主机名';
```

**2.授予权限**

```mysql
GRANT 权限列表 ON 数据库名.表名 TO '用户名'@'主机名';
```

**3.撤销权限**

```mysql
REVOKE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';
```

