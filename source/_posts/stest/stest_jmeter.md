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

  

####  七、jmeter连接数据库

**jmeter连接数据库(MySQL)**   

* 准备"mysql-connector-java-xxx.jar"驱动jar包：[官方jar包下载](https://dev.mysql.com/downloads/connector/j/) ，然后将其放在jmeter的bin目录下

* 在“测试计划”面板下将mysql的驱动jar包添加到ClassPath

* 添加 "JDBC Connection Configuration"：线程组-> 配置单元-> JDBC Connection Configuration，常需的配置如下

    * 设置数据库连接池的变量名称(Variable Name for created Pool)，供下一步的"JDBC Request"配置中使用(引用)
    * 配置数据库的连接设置：
        * Database URL: (mysql格式：jdbc:mysql://数据库ip:端口/数据库名称)
        * JDBC Driver class: 选择连接数据库的驱动(com.mysql.jdbc.Driver)
        * Username: 连接数据库的用户名
        * Password: 连接数据库的密码
        
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619104647.png)
        
* 添加 "JDBC Request" ：线程组-> 取样器-> JDBC Request ，相关配置如下
    * 设置需使用的数据库线程池(Variable Name of Pool declared in JDBC Connection Configuration)
    * 在SQL Query中编写执行sql语句
    
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619104743.png)    
  
  
####  八、jmeter其他常用功能

**参数化**

* 参数化即是根据需求动态获取数据并进行赋值的过程

* 参数化中的变量引用方式为：${变量名}/"${变量名}"

* jmeter中参数化常见方式：
    * 方式1、用户定义的变量(User Defind Variables): 一般在"测试计划"下直接添加，作为全局变量使用
    * 方式2、用户参数(User Variables): 一般在Http请求(取样器)/线程组的”前置处理器“中添加，作为局部变量使用
    * 方式3、CSV数据文件(CSV Data Set Config): 一般在”线程组“下添加，实现大批量的数据赋值引用
        * 步骤1：创建csv数据文件
        * 步骤2：添加”csv数据文件设置”(线程组->配置单元->csv数据文件设置)
        * 步骤3：设置文件编码，建议使用"utf-8"
        * 步骤4：填写变量名称,多个之间使用英文逗号 "," 进行隔开，其他设置一般默认
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619093046.png)
        
(PS:在参数化的参数配置中，参数的"组数"一般与"线程数"[即模拟的用户数/请求数]有对应关系)   
   
        
**jmeter中的数据关联** 
  
* 定义：从前面的请求中获取的数据提取出来给后面的请求使用()

* xpath关联
    * 使用场景：响应数据为HTML/xml时使用
    * 添加xpath提取器：http请求-> 后置处理器-> xpath提取器
    * 配置xpath提取器：
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619115259.png)
        
* json关联：
    * 使用场景：响应数据为json时使用
    * 添加json提取器：http请求-> 后置处理器-> json提取器
    * 配置json提取器：
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619120103.png)
        
* 正则表达式
    * 使用场景：所有场景
    * 添加正则表达式提取器：http请求-> 后置处理器-> 正则表达式提取器
    * 配置正则表达式提取器：
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619120355.png)


**jmeter中常用断言** 
* 响应断言(Response Assertion) 
    * 根据需求在对应的请求接口下面添加“响应断言”：HTTP请求(取样器)-> 断言-> 响应断言
    * 断言配置：
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619122504.png)

* json断言    
    * 根据需求在对应的请求接口下面添加“json断言”：HTTP请求(取样器)-> 断言-> json断言
    * 断言配置：
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619223842.png)

* 大小断言
    * 根据需求在对应的请求接口下面添加“大小断言”：HTTP请求(取样器)-> 断言-> 大小断言
    * 断言配置：
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619223056.png)
  
* 断言持续时间
    * 根据需求在对应的请求接口下面添加“断言持续时间”：HTTP请求(取样器)-> 断言-> 断言持续时间
    * 断言配置：
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200619223229.png)
  
* 自由断言(BeanShell 断言)
    * 根据需求在对应的请求接口下面添加“断言持续时间”：HTTP请求(取样器)-> 断言-> BeanShell断言
    * 断言配置：根据需求编写响应的断言脚本
 
 
**jmeter跨线程组关联(函数)**
* jmeter跨线程组关联即跨线程组之间的数据(参数)传递，类似java编程中的setXXX(),getXXX()方法，具体操作步骤如下
    * 1、工具栏选择”函数助手“-> 选择"setProperty" -> 设置属性的名称，属性值(引用)-> 点击生成-> 复制生成的函数字符串
    * 2、在对应的线程组下面添加 "BeanShell取样器",在其脚本框中粘贴上一步所生成的函数字符串
    * 3、工具栏选择”函数助手“-> 选择"property" -> 填写属性的名称(步骤1设定的属性名称)-> 点击生成-> 复制生成的函数字符串
    * 4、在其他线程组需要使用的地方粘贴步骤3所生成的”函数字符串"即可
    (PS: 注意线程组的执行顺序，set值在前，get值在后，可以通过"调度器"的启动延迟功能实现)
    
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200620002557.png)
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200620003715.png)
    ()
    
**jmeter分布式**

* 执行机：
    * 将执行机的IP写入到自己的配置文件jmeter.properties中，格式为：remote_hosts=ip:端口(1099)
    * 关闭必要的防火墙之类软件/网卡程序
    * 执行其jmeter-server.bat程序
    
* 控制机：
    * 将执行机的IP写入到配置文件jmeter.properties中，格式为：remote_hosts=ip:端口(1099)，多个执行机ip则用","分隔开
    * 如果控制机也需要执行脚本，则同样要执行其jmeter-server.bat程序
    
(PS:执行机同样需要放置jmeter脚本，路径与控制机保持一致；控制机和执行机应在同一网段)

**jmeter命令行模式下的常用命令举例**

* 执行测试，输出测试计划和结果：
    * jmeter -n -t 脚本路径(.jmx文件) -l 生成的执行结果(.jtl/.csv文件)
    
* 执行测试，输出测试计划和结果，并输出日志报告：
    * jmeter -n -t 脚本路径(.jmx文件) -l 生成的执行结果(.jtl/.csv文件) -j 生成的日志文件(.log)
    
* 默认分布式执行：
    * jmeter -n -t 脚本路径(.jmx文件) -r -l 生成的执行结果(.jtl/.csv文件) -j 生成的日志文件(.log)
    
* 指定ip分布式执行：
    * jmeter -n -t 脚本路径(.jmx文件) -R IP:端口 -l 生成的执行结果(.jtl/.csv文件) -j 生成的日志文件(.log)
    
* 生成测试报表：
    * jmeter -n -t 脚本路径(.jmx文件) -l 生成的执行结果(.jtl/.csv文件) -e -o tableresult(报告目录)
    
    
**jmeter常用逻辑控制器**  

* 如果(If)控制器
    * 添加：线程组-> 逻辑控制单元-> 如果(If)控制器
    * 字符串比较："${username}"=="xxx"
    * 数字比较：${counter}==100
    * 布尔值比较：${isLogin}
    * 勾选选项的说明如下图所示：
    ![](https://gitee.com/kolenj/BlogImages/raw/master/20200620025013.png)
    
* ForEach控制器
    * 添加：线程组-> 逻辑控制单元-> ForEach控制器
    * 使用方式：(一般于”用户定义的变量“一起使用)
        * 1、设置用户定义的变量：
            * 变量名：前缀_数字(user_1)
            (PS:数字须是连续的)
            ![](https://gitee.com/kolenj/BlogImages/raw/master/20200620031237.png)
             
        * 2、配置foreach控制器
            * 输入变量名前缀(user)
            * 开始循环字段(不包含)
            * 结束循环字段(包含)
            * 输出的变量名称
            ![](https://gitee.com/kolenj/BlogImages/raw/master/20200620031619.png)
            
        * 3、使用foreach控制器输出的变量${名称}
 
 * 循环控制器
    * 添加：线程组-> 逻辑控制单元-> 循环控制器
            ![](https://gitee.com/kolenj/BlogImages/raw/master/20200620031953.png)
        
**jmeter元件与组件**  

* 组件(jmeter元件中最小的单元统称为一个个组件)
      
* 元件(一系列类似功能组件的集合)：取样器/ 逻辑控制器/ 前置处理器/ 后置处理器/ 断言/ 定时器/ 配置单元/ 监听器
    * jmeter元件的作用域:
        * 配置元件( config elements )会影响其作用范围内的所有元件。
        * 前置处理程序( Per processors )在其作用范围内的每个sampler元件之 前执行。
        * 定时器( timers ) 对其作用范围内的每一个 sampler有效
        * 后置处理程序( Post processors )在其作用范围内的每个sampler元件之 后执行。
        * 断言( Assertions )对其作用范围内的每一个sampler 元件执行后的结果执行校验。
        * 监听器( Listeners )收集其作用范围的每个sampler元件的信息并呈现。
s       * 取样器( Sampler )元件不和其它元件相互作用,因此不存在作用域的问题

    * 元件的执行顺序：
        * 配置单元-> 前置处理器-> 定时器-> 取样器-> 后置处理器-> 断言-> 监听器
        (PS: 如果在同一作用域范围内有多个同一类型的元件， 则这些元件按照它们在测试计划中的上下顺序次执行)
    
       
####  九、jmeter性能测试


**添加集合点**

* 右击需要集合并发的请求，添加“定时器" -> "同步定时器(Synchronizing Timer)”，模拟的用户组数量不能大于“线程组”里的线程数，
超时时间应大于Ramp-up时间，具体如下图

![](https://gitee.com/kolenj/BlogImages/raw/master/20200615014124.png)


