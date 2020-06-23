---
title: Fake RestApi For Testing Or Mocking
date: 2018-06-15 09:09:04
tags: 
- Mock/Fake Api

categories:
- 软件测试

---


####  一. 安装 node.js,因为等下要用到npm命令来安装json-server

    1.官网下载对应平台的node.js进行安装
    (https://nodejs.org/dist/v12.17.0/node-v12.17.0-x64.msi)
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527102308.png)

    2. 成功之后在命令行执行node -v, npm -v 如显示安装的版本则表示安装成功
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527102434.png)

####  二、安装json-server，并启动服务

    1.在命令行执行： npm install -g json-server
    
    2. 启动json-server: json-server --watch db.json
       其将在当前用户目录下生成一个默认数据 “db.json”
       在浏览器打开localhost:3000/+数据路径，即可访问数据
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527103012.png)

![](https://gitee.com/kolenj/BlogImages/raw/master/20200527103540.png)
    
####  三、通过postman使用常见方法操作这些Rest Api来模拟我们的测试工作

    1、Get方法：
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527112314.png)
    
    2、Post方法：（其中Headers里边采用的key-value为：Content-Type：application/json）
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527112909.png)  
  
    3、Patch方法：
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527112909.png)  
 
    4、Put方法：
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527113836.png)

    5、Delete方法：
![](https://gitee.com/kolenj/BlogImages/raw/master/20200527133016.png)
    

####  四、官方文档参考文档链接: [json-server](https://github.com/typicode/json-serve)

          
   