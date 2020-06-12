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


#### SQL基本查询

* 1、基本查询：
    * select * from <表名>                         # 查询所有列(整个表)                           
    * elect 列名称(,列名称...) FROM <表名>           # 查询指定列
    * select distinct 列名 from <表名>              # 关键词 DISTINCT 用于返回唯一不同的值
    
* 2、条件查询：
    * SELECT * FROM <表名> WHERE <条件表达式> 
           (常用的条件表达式逻辑算法：and/or/not/，like 'xx%xx'(%表示任意字符))
   
* 3、投影查询：
SELECT 列1, 列2, 列3 FROM <表名> WHERE <条件表达式>    
           (让结果集只包含指定列这种查询操作称为投影查询)
           SELECT 列1 别名1, 列2 别名2, 列3 别名3 FROM ...
           (给列起别名)
   
* 4、排序查询：
使用ORDER BY对结果集进行排序，默认是升序、倒序排序使用DESC,可以对多个列进行排序
            如果有WHERE子句，那么ORDER BY子句要放到WHERE子句后面
            例：
                SELECT id, name, gender, score
                FROM students
                WHERE class_id = 1
                ORDER BY score DESC,gender;

* 5、分页查询：
使用“LIMIT <pageSize> OFFSET <pageIndex>”实现，
            要查询出第N页的记录集：(PS:SQL记录集的索引从0开始)
            假设LIMIT设定为pageSize，则pageIndex计算公式为pageSize * (N - 1)
            例：
                SELECT id, name, gender, score
                FROM students
                ORDER BY score DESC
                LIMIT 3 OFFSET 3;

 

**SQL进阶查询**
   
    6、聚合查询：
    
    7、多表查询：
    
    8、连接查询：    