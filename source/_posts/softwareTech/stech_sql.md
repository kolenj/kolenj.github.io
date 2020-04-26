---
title: SQL常见操作
date: 2018-05-15 19:13:32
tags: 
- sql
 
categories:
- 软件技术

---

**SQL基本查询**
 
    1、基本查询：select * from <表名>
    
    2、条件查询：SELECT * FROM <表名> WHERE <条件表达式> 
               (常用的条件表达式：and/or/not/，like 'xx%xx'(%表示任意字符))
       
    3、投影查询：SELECT 列1, 列2, 列3 FROM <表名> WHERE <条件表达式>    
               (让结果集只包含指定列这种查询操作称为投影查询)
               SELECT 列1 别名1, 列2 别名2, 列3 别名3 FROM ...
               (给列起别名)
       
    4、排序查询：使用ORDER BY对结果集进行排序，默认是升序、倒序排序使用DESC,可以对多个列进行排序
                如果有WHERE子句，那么ORDER BY子句要放到WHERE子句后面
                例：
                    SELECT id, name, gender, score
                    FROM students
                    WHERE class_id = 1
                    ORDER BY score DESC,gender;
    
    5、分页查询：使用“LIMIT <pageSize> OFFSET <pageIndex>”实现，
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