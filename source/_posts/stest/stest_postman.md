---
title: postman工具使用指南
date: 2017-03-15 09:09:04
tags: 
- 软件工具
 
categories:
- 软件测试

---

####  Postman安装与界面：
    1、安装：chrome插件版已被舍弃，使用app版
    2、界面的介绍、登录云端保存共享、创建测试用例集合，
    3、请求4要素：请求url，请求方法，请求头域headers，请求参数params（post请求时有请求body）
       响应4要素：响应码 、响应头域、响应body
       
    4、post方法请求时，请求体body里携带的参数格式有：form-data(文件上传 )/x-www-form-urlencoded/binary/
       raw(text/plain、application/json、application/javascript、application(text)/xml、text/html)   
       相对应于请求头Request Headers中Content-Type：
       
    5、请求有时需要Refer、Content-type、Cookies、token等参数才能成功访问
    
    6、环境变量与请求参数的参数化，既使用{{xxx}}获取对应环境中的xxx参数的值
    
    7、测试沙箱：
        postman测试沙箱是结合js脚本完成测试中的功能，在请求发起前后实现部分测试操作。
        常用功能：
        请求前脚本设置请求前置操作如设置变量等。
        请求后对状态码、响应头、响应正文等信息进行断言操作。
        使用console控制台进行调试。
        通过console查看接口请求返回信息，一级对脚本中使用的变量进行输出调试等操作。
        (Pre-request Script-设置请求前脚本，Tests-断言判断 )
        
    8、数据集与数据驱动：
        点击运行数据集执行Run
        文件数据格式支持json/cvs
        在Pre-request Script、Tests引用数据格式为data.xxx
        
    9、Newman命令与Jenkins持续集成
    
    10、monitor的使用[https://www.cnblogs.com/zouzou-busy/p/11134683.html]