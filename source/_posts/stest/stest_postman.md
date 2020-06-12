---
title: postman使用指南及实战
date: 2017-03-15 09:09:04
tags: 
- 软件工具
 
categories:
- 软件测试

---


####  一、Postman的安装及基本使用
1.官网下载安装 [Postman](https://www.postman.com/downloads/)


<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528134158.png"/>
</div>


（PS：Postman 的 Chrome浏览器插件版已不再维护，不推荐使用了）

2.安装好之后可以注册个账户进行登录


<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528134645.png"/>
</div>


3.界面操作的说明


<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529012446.png"/>
</div>



####  二、接口测试

**接口测试说明**


<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528183501.png"/>
</div>


**接口测试的流程**

1.获取接口信息
一般是通过接口文档获取接口的基本调用方式和返回的数据说明，如果没接口文档，可通过抓包方式获取。[抓包教程](http://localhost:4000/2017/05/15/stest/stest_fiddler%E7%9A%84%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B/)

2.设计接口测试用例
根据接口信息，按照接口测试用例的设计方法，进行设计参数和预期返回结果。

3.发起接口请求
使用工具或编程方式发起接口请求。

4.验证返回信息
获取接口返回的结果，进行解析和验证。


<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528181633.png"/>
</div>


**Postman接口请求过程**

    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528175913.png"/>
</div>


**通过chrome浏览器打开开发者工具(快捷键F12)查看请求和响应的一个实例**
* 请求

    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528181724.png"/>
</div>


* 响应 

    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528181444.png"/>
</div>



####  三、请求头域的一些相关说明

* 请求有时需要携带Refer、Content-type、Cookies、token等参数才能成功访问

* Post方法请求时请求体Body的参数携带方式与请求头域Content-Type的类型相对应：

    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528190524.png"/>
</div>


(PS：请求体body里携带的参数格式有：
form-data(键-值/文件)/ x-www-form-urlencoded(键值对)/ binary(文件)/
raw(text/plain、application/json、application/javascript、application(text)/xml、text/html) )


####  四、环境变量与全局变量

* 创建环境变量/全局变量

    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528211818.png"/>
</div>


* 通过"{{变量名}}"方式进行变量的引用(使用)

    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200528212421.png"/>
</div>



####  五、测试沙箱和测试断言
* 作用:

    请求前脚本设置请求前置操作如设置变量等；
    
    请求后对状态码、响应头、响应正文等信息进行断言操作；
    
    使用console控制台进行调试；
    
    通过console查看接口请求返回信息，以及对脚本中使用的变量进行输出调试等操作。
    
    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529010451.png"/>
</div>


    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529010827.png"/>
</div>



####  六、多接口测试管理-测试集与测试驱动

* 运行步骤：

    1.点击运行要测试的数据集(执行Runner)
    
    2.设置要使用的环境，循环次数，延迟设定，导入数据集(数据格式支持json/cvs,另外要注意编码问题，建议使用"utf-8"格式)
    
    (PS:在测试沙箱的Pre-request Script、Tests中引用数据格式为：data.xxx，请求头中为：{{xxx}})
    
    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529022314.png"/>
</div>

    
* 执行结果：

    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529022705.png"/>
</div>

    
####  七、cookies的获取方式及后续操作

1.先网页登录后使用浏览器的开发者工具在Network选项栏查找到cookie值，后续使用Postman的请求中在Headers项通过“Cookie"携带上该cookie


<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529025810.png"/>
</div>


2.先网页登录后使用浏览器的开发者工具在Application选项栏点击"Cookies"选项，其中会含有用户成功登录后维持该请求会话的信息数据，
  一般会是含有“sess”字段的 键值对，找到之后在postman的cookies面板添加该请求域名(网址)，然后添加cookie，将模板的cookie键值对
  替换即可
  
 
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529030311.png"/>
</div>

  
3.直接在Postman中通过账户密码进行成功登录，Postman的Cookies管理器自动将请求后的cookies保存下来，后续的请求(同一个网站)则会
  自动引用这些cookies
    

#### 八、Newman命令与Jenkins持续集成

* Newman命令与Jenkins持续集成

#### 九、monitor的使用

* monitor的使用[https://www.cnblogs.com/zouzou-busy/p/11134683.html]