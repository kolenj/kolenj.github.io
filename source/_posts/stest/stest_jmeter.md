---
title: jmeter的安装与介绍
date: 2017-03-25 09:09:04
tags: 
- jmeter

categories:
- 软件测试

---

####  一、jmeter简介

&emsp; &emsp; Apache JMeter是Apache组织开发的基于Java的压力测试工具。其可在不同平台比如Windows、Linux或macOS系统上进行软件测试。
主要用于应用程序的功能负载测试以度量软件的性能，也可以用于其他类型的测试比如接口测试，API测试等。


####  二、jmeter常用测试

1、接口测试

2、性能测试

3、压力测试

4、数据库测试   


####  三、jmeter下载安装及启动         
  
1、默认已准备好了java的运行环境

2、jmeter其官方下载地址为：[jmeter](https://jmeter.apache.org/download_jmeter.cgi)  

3、下载完成后解压，进入其bin目录双击 “ApacheJMeter.jar/jmeter.bat” 即可启动jmeter   -(PS：Linux系统下为jmeter.sh)

4、jmeter语言更改及界面如下：

<div align="left">
        <img width="800" height="500" src="https://gitee.com/kolenj/BlogImages/raw/master/20200610013024.png"/>
    </div>

&emsp; &emsp;  
5、jmeter插件管理器的下载: [plugins-manager.jar](https://jmeter-plugins.org/install/Install/)

6、jmeter插件管理器下载之后放到jmeter的“extras” 目录下，然后重启jmeter，之后在“选项”菜单栏最下边如果看到Plugins Manager，则表示jmeter插件管理器也安装成功了


####  四、jmeter常用操作界面介绍

* "测试计划" 下可添加：
    * 线程
    * 配置单元
    * 监听器
    * 定时器
    * 前置处理器
    * 后置处理器
    * 断言
    * 测试片段
    * 非测试元件  
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200610024927.png)


* "线程组" 下可添加：
    * 取样器
    * 逻辑控制单元
    * 前置处理器
    * 后置处理器
    * 断言
    * 定时器
    * 配置元件
    * 监听器
    * 测试片段  
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200610024413.png)

* "http请求(取样器)" 下可添加：
    * 断言
    * 定时器
    * 前置处理器
    * 后置处理器
    * 配置元件
    * 监听器  
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200610030251.png)
    
    
####  四、jmeter测试计划基本流程(要素)

1、创建测试计划

2、添加最少一个线程组

3、在线程组中添加最少一个取样器(比如常用的http请求)

4、给测试计划(线程组)最少添加一个监听器(如"查看结果树")


**具体测试操作界面说明如下：**

![](https://gitee.com/kolenj/BlogImages/raw/master/20200610141010.png)

![](https://gitee.com/kolenj/BlogImages/raw/master/20200610142542.png)

![](https://gitee.com/kolenj/BlogImages/raw/master/20200610141931.png)


####  五、使用badboy录制脚本

* 使用badboy录制

    * 下载 [badboy](https://badboy1.software.informer.com/download/#downloading)
    
     安装后运行badboy，其打开时默认为录制recording状态，直接输入网址回车操作即可
    
    * 操作完成，点击停止记录
    
    * 导出脚本
        * 点击”file“ 选择”export to jmeter“ 导出.jmx文件  
        
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200610174841.png)       
* 在jmeter中打开已有的文件

    * jmeter脚本文件后缀为".jmx"
    
    * 选择打开文件，找到badboy录制导出的jmx文件打开即可
    
    * 然后添加监听器(例如：查看结果树)，点击运行  
    
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200610175017.png)


####  六、jmeter代理录制移动端请求

* 配置jmeter
    * 1.打开jmeter创建新测试计划
    * 2.在测试计划下添加一个线程组
    * 3.右击测试计划，在”非测试单元“中添加一个HTTP代理服务器
    * 4.配置代理服务器
        * 设定端口，其默认端口为8888
        * HTTPS Domains 中填写 本机ip地址或localhost
        * 在目标控制器中选择：[测试计划名称]>线程组
        * 点击启动按钮，在弹出的窗口点击ok/确定 执行  
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200610181627.png)
        
* 配置手机(类同fiddler中的配置)

  

####  四、jmeter常用操作界面介绍


####  四、jmeter常用操作界面介绍


####  四、jmeter常用操作界面介绍