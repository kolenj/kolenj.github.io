---
title: 数据库常见操作
date: 2018-05-16 15:13:32
tags: 
- sql
 
categories:
- 软件技术

---

**1、SQL简介：**

    SQL(Structured Query Language)，结构化查询语言，用于访问和处理数据库的标准的计算机语言。

**2、SQL语言定义了以下几种操作数据库的能力：**

    DDL：Data Definition Language
    DDL允许用户定义数据，也就是创建表、删除表、修改表结构这些操作。通常，DDL由数据库管理员执行。
    
    DML：Data Manipulation Language
    DML为用户提供添加、删除、更新数据的能力，这些是应用程序对数据库的日常操作。
    
    DQL：Data Query Language
    DQL允许用户查询数据，这也是通常最频繁的数据库日常操作
    
    Tips：
    SQL语言关键字不区分大小写！！！但是，针对不同的数据库，对于表名和列名，有的数据库区分大小写，有的数据库不区分大小写。同一个数据库，
    有的在Linux上区分大小写，有的在Windows上不区分大小写。

**3、常见数据库类型：**
     
    常见关系型数据库有：
        Oracle，SQLServer，DB2，MySQL，Access，Sqlite
    
    常见非关系型数据库有：          
        MongoDB，Redis，HBase，NoSql

**4、数据库/表的常见操作(MySql为例)：**
        
        1.创建数据库：
            create databases 数据库名称;
            (创建一个以utf-8为默认编码的数据库：CREATE DATABASE IF NOT EXISTS aimin DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
            
        2.创建表：
            create table 表名称
            (
            列名称1 数据类型,
            列名称2 数据类型,
            .......
            );
            
        3.show databases/tables;                                    (查看数据库/表
        4.use 数据库名xxx                                           （切换到xxx数据库
        5.show columns from xxx/desc xxx                            (查看表结构,xxx为表名
        6.drop database if exists xxx;                               (删除数据库xxx
        7.drop table xxx（表名）                                           （删除表xxx
          delete from xxx（表名）                                    （清空表
        8.alter table xxx(表名) change 原列名  想改成的列名 列类型;     (更改表的列名
        9.alter table tablename rename newtablename;                （对表名进行重命名
          rename table tablename to newtablename;
        10. alter table tablename modify 列名 想改的类型;              (更改列的类型
        11.alter table tablename add 列名 类型;                       (增加列
        12.alter table tablename drop 列名;                           (删除某列
        
        
**5、MySql常见操作：**

    1、登录到MySQL：
        mysql - h 主机地址 -u 用户名 -p 用户密码;         （本地可省略 -h 主机地址
     
    2、更改登录密码：
        update user set password=PASSWORD('新密码') where user=‘用户名';
        flush privileges;(刷新权限设置)
       
    3、增加新用户：
        grant select(insert,update,delete)/=(all privileges) on 数据库.* to 用户名@登录主机 identified by '密码'; 
        flush privileges;(刷新权限设置) 
        
    4、让root用户免密码操作数据库：
        grant select,insert,update,delete on 数据库.* to root@localhost identified by '';
        flush privileges;(刷新权限设置)
        
    5、删除用户：
        delete from user where user='用户名' and host='localhost';
        flush privileges;(刷新权限设置)
        