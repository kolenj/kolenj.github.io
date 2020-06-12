---
title: SQL常见操作
date: 2018-05-15 19:13:32
tags: 
- sql
 
categories:
- 软件技术

---

#### SQL简介

**SQL 是一门用于访问和处理数据库的标准的(ANSI)结构化查询语言**

* SQL 可分为两个部分：数据操作语言 (DML) 和 数据定义语言 (DDL)
 
    * 1、DML- SQL (结构化查询语言)是用于执行查询的语法，其也包含用于更新、插入和删除记录的语法
     
        * SELECT - 从数据库表中获取数据
        * UPDATE - 更新数据库表中的数据
        * DELETE - 从数据库表中删除数据
        * INSERT INTO - 向数据库表中插入数据
    
    * 2、DDL- SQL 的数据定义语言 (DDL) 部分使我们有能力创建或删除表格。我们也可以定义索引（键），规定表之间的链接，以及施加表间的约束
    
        * CREATE DATABASE - 创建新数据库
        * ALTER DATABASE - 修改数据库
        * CREATE TABLE - 创建新表
        * ALTER TABLE - 变更（改变）数据库表
        * DROP TABLE - 删除表
        * CREATE INDEX - 创建索引（搜索键）
        * DROP INDEX - 删除索引

        （PS：SQL 对大小写不敏感）


#### SQL基础

* 1、基本查询(select)：
    * select * from <表名>                            # 查询所有列(整个表)                           
    * elect 列名称(,列名称...) FROM <表名>            # 查询指定列
    * select distinct 列名 from <表名>                # 关键词 DISTINCT 用于返回唯一不同的值
    
* 2、条件查询(where)：
    * SELECT * FROM <表名> WHERE <条件表达式> 
      (常用的条件表达式逻辑算法：and/or/not/，like 'xx%xx'(%表示任意字符))
      
    * SELECT * FROM 表名 WHERE (列名='xxx' OR 列名='xxx') AND 列名='xxx'

* 3、排序(Order By,默认升序，降序使用desc)
    * SELECT 列名, 列名 FROM Orders ORDER BY 列名 DESC, 列名 ASC
    
* 4、插入数据(insert)
    * INSERT INTO table_name (列名, 列名,...) VALUES (值1, 值2,....)

* 4、更新数据(update)
    * UPDATE 表名 SET 列名 = 新值 WHERE 列名 = 某值
    
* 5、删除数据(delete)
    * DELETE FROM 表名称 WHERE 列名称 = 值


#### SQL高级

**DML**

* 1、SELECT TOP
    * SELECT TOP 10 * FROM 表名                   # 获取前10条记录
    * SELECT TOP 50 PERCENT * FROM 表名           # 获取50%的记录

* 2、Like/通配符
    * %	替代一个或多个字符
	* _仅替代一个字符
    * [charlist]	字符列中的任何单一字符
    * [^charlist]/[!charlist] 不在字符列中的任何单一字符

* 3、In/Between
    * SELECT 列名(s) FROM 表名 WHERE 列名 IN (value1,value2,...)
    * SELECT 列名(s) FROM 表名 WHERE 列名 (NOT) BETWEEN value1(包括) AND value2(不包括)
      (操作符 BETWEEN ... AND 会选取介于两个值之间的数据范围。这些值可以是数值、文本或者日期)

* 4、Alias(别名)
    * SELECT 列名(s) FROM 表名 AS alias_name
    * SELECT 列名 AS alias_name FROM 表名
    
* 5、Inner Join/ Left Join/ Right Join/ Full Join (内联/左联/右联/全联-用于根据两个或多个表中的列之间的关系，从这些表中查询数据)
    * Inner Join 在表中存在至少一个匹配时，INNER JOIN 关键字返回行
    * LEFT JOIN 关键字会从左表 (table_name1) 那里返回所有的行，即使在右表 (table_name2) 中没有匹配的行
    * RIGHT JOIN 关键字会右表 (table_name2) 那里返回所有的行，即使在左表 (table_name1) 中没有匹配的行
    * FULL JOIN 只要其中某个表存在匹配，FULL JOIN 关键字就会返回行
    
      SELECT column_name(s) FROM table_name1 INNER(LEFT/RIGHT/FULL) JOIN table_name2  ON table_name1.column_name=table_name2.column_name (ORDER BY 表名.列名)
        
* 6、UNION 操作符用于合并两个或多个 SELECT 语句的结果集
    * UNION 内部的 SELECT 语句必须拥有相同数量的列。列也必须拥有相似的数据类型。同时，每条 SELECT 语句中的列的顺序必须相同        
        
        SELECT column_name(s) FROM table_name1 UNION (ALL) SELECT column_name(s) FROM table_name2 
        
* 7、SELECT INTO (从一个表中选取数据，然后把数据插入另一个表中)

    * SELECT INTO 语句常用于创建表的备份复件或者用于对记录进行存档
    
        SELECT */column_name(s) INTO new_table_name [IN externaldatabase] FROM old_tablename
        
        
**DDL**

* 1、创建数据库
    *  CREATE DATABASE database_name
    
* 2、创建数据表

```
        CREATE TABLE 表名称
        (
        列名称1 数据类型,
        列名称2 数据类型,
        列名称3 数据类型,
        ...
        )
        
        常见数据类型的定义：
        整数：
            integer(size)
            int(size)
            smallint(size)
            tinyint(size)
            
        带小数数字：("d" 规定小数点右侧的最大位数)
            decimal(size,d)
            numeric(size,d)
        
        固定长度的字符串：(可容纳字母、数字以及特殊字符)
            char(size)	 
            
        可变长度的字符串：(可容纳字母、数字以及特殊的字符)
            varchar(size)
        
        日期：
            date(yyyymmdd)
            
         (PS:size表示最大位数或者最大字符长度)
```

* 3、SQL约束

    * 约束是用于限制加入表的数据的类型。可以在创建表时规定约束（通过 CREATE TABLE 语句），或者在表创建之后也可以（通过 ALTER TABLE 语句）
    * 常见约束有：
        * NOT NULL          # 不允许为Null
        * UNIQUE            # 设置唯一标识数据库表中的每条记录
        * PRIMARY KEY       # 主键
        * FOREIGN KEY       # 外键
        * CHECK             # 限定值
        * DEFAULT           # 默认值
        
* 4、SQL索引
    * 创建索引，以便更加快速高效地查询数据(PS: 由于索引本身也需要更新,所以只在常常被搜索的列（以及表）上面创建索引)
        
        CREATE (UNIQUE) INDEX index_name ON table_name (column_name)
        
    * 删除索引：
        
        DROP INDEX index_name (DB2 和 Oracle 语法)
        ALTER TABLE table_name DROP INDEX index_name (MySQL 的语法)
        
* 5、Drop -删除数据库/表/表数据
    * DROP DATABASE 数据库名称
    * DROP TABLE 表名称
    * TRUNCATE TABLE 表名称(仅仅删除表格中的数据)
    
* 6、ALTER TABLE -用于在已有的表中添加、修改或删除列
    * ALTER TABLE table_name ADD column_name datatype               # 添加列   
    * ALTER TABLE table_name DROP COLUMN column_name                # 删除列 
    * ALTER TABLE table_name ALTER COLUMN column_name datatype      # 更改列的数据类型
    
* 7、AUTO INCREMENT -在每次插入新记录时，自动地创建主键字段的值 

    * Id int NOT NULL AUTO_INCREMENT     # MySQL语法：默认地，AUTO_INCREMENT 的开始值是 1，每条新记录递增 1
    
* 8、SQL 日期
    * 在数据库中存储日期或日期/时间值(MySQL)
        * DATE - 格式 YYYY-MM-DD
        * DATETIME - 格式: YYYY-MM-DD HH:MM:SS
        * TIMESTAMP - 格式: YYYY-MM-DD HH:MM:SS
        * YEAR - 格式 YYYY 或 YY   
        
* 9、SQL NULL -默认地，表的列可以存放 NULL值(表示是遗漏的未知数据)
    * 无法比较 NULL 和 0；它们是不等价的
    * 无法使用比较运算符来测试 NULL 值，比如 =, <, 或者 <>
    * 使用 IS NULL 和 IS NOT NULL 操作符 
    * 相关函数有：ISNULL()、NVL()、IFNULL() 和 COALESCE()
    
    
       
#### SQL常用函数

* 1、COUNT(column_name) 函数返回指定列的值的数目（NULL 不计入）
    * SELECT COUNT(column_name) FROM table_name
    * COUNT(*) 函数返回表中的记录数
    * COUNT(DISTINCT column_name) 函数返回指定列的不同值的数目
    
* 2、avg()
    * SELECT AVG(column_name) FROM table_name
    
* 3、Group By -用于结合合计函数，根据一个或多个列对结果集进行分组

        SELECT column_name, aggregate_function(column_name)
        FROM table_name
        WHERE column_name operator value
        GROUP BY column_name
    
* 4、Having

        SELECT column_name, aggregate_function(column_name)
        FROM table_name
        WHERE column_name operator value
        GROUP BY column_name
        HAVING aggregate_function(column_name) operator value
        


[SQL快速参考](https://www.w3school.com.cn/sql/sql_quickref.asp)