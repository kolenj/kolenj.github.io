---
title: 正则表达式
date: 2017-05-23 09:29:22
tags: 
- 正则表达式

categories:
- others

---

####  常用元字符(规则)释义

    常用限定符：
    
    *  匹配“0/多次”
    +  匹配“1/多次”
    ?  匹配“0/1次”
    {n} 匹配“n次”
    {n,m} 匹配“n-m次”
    
    [xyz...] 匹配方括号中的任意“1个”字符
    [^x]     匹配除了x以外的任意字符
    [^xyz]   匹配除了xyz以外的任意字符
    
    .  匹配任意字符
    \w 匹配字母、数字、下划线或汉字【\W 大写反义
    \d 匹配数字【\D 大写反义
    \s 匹配任意的空白字符（空格/制表符/换行符等）【\S 大写反义
    \b 单词的开头或结尾，单词的分界处【\B 大写反义
    ^  匹配字符串的开始
    $  匹配字符串的结束
    
    ():  小括号()用于分组匹配
    | :  分支条件，如：\d{5}-\d{4}|\d{5}这个表达式用于匹配美国的邮政编码 
        （Tips：匹配分枝条件时，将会从左到右地测试每个条件，如果满足了某个分枝的话，就不会去再管其它的条件）
    \1:  反向引用，如（\b(\w+)\b\s+\1\b可以用来匹配重复的单词，像go go, kitty kitty）
        （Tips：从左向右，以分组的左括号为标志，第一个出现的分组的组号为1，第二个为2，以此类推）
    
    a.*b： 匹配最长的，以a开始，以b结束的字符串（贪婪）
    a.*?b：匹配最短的，以a开始，以b结束的字符串（懒惰）
    
    \r	回车
    \f	换页符
    \n	换行符
    \t	制表符Tab
    \v	竖向制表符
    
####  常用匹配
    
    1.匹配单词：\b\w+\b
    2.匹配IP地址：((2[0-4]\d|25[0-5]|[01]?\d\d?)\.){3}(2[0-4]\d|25[0-5]|[01]?\d\d?)
    3.匹配手机号：
   

**参考：** https://deerchao.cn/tutorials/regex/regex.htm