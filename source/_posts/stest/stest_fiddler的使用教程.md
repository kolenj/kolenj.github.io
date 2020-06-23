---
title: Fiddler的使用教程
date: 2018-08-15 19:13:32
tags: 
- fildder
 
categories:
- 软件测试

---

####  一、Fiddler的下载安装

1.官网下载安装:[Fiddler](https://www.telerik.com/download/fiddler)

![](https://gitee.com/kolenj/BlogImages/raw/master/20200527234712.png)

2、Fiddler界面的简单说明：

![](https://gitee.com/kolenj/BlogImages/raw/master/20200527235440.png)

3、配置Fiddler：

* 点击Tools菜单栏选择Options，在HTTPS选项卡选择 勾选抓取https请求，同时勾选忽略服务证书错误(可选)：

![](https://gitee.com/kolenj/BlogImages/raw/master/20200527235951.png)

* 接着在Connections选项卡选择勾选允许远程主机连接：

![](https://gitee.com/kolenj/BlogImages/raw/master/20200528000458.png)

4、拦截过滤的简单设置：

* 在右边面板点击“Filters”，
* 在弹出的面板中勾选“Use Filters"，其中"-No Zone Filter-"可选内网(intranet)和外网(internet),
* "-No Host Filter-"可选隐藏下面的主机请求(Hide)/显示下面的主机请求(Show)/标记下面的主机请求(Flag)
* 然后在右边”Actions“选择立即执行过滤条件(Run)/保存该过滤条件(Save)/载入其他过滤条件(Load),具体操作如下图：

![](https://gitee.com/kolenj/BlogImages/raw/master/20200528004236.png)


####  二、Android移动端的拦截设置

1.手机和PC(Fiddler)处于同一个网络

2.确保Fiddler允许远程连接(上面步骤3)

3.打开手机连接的网络，找到”高级选项“进行手动代理设置
* 代理服务器主机名填写PC端的ip地址，如：192.168.3.11
* 代理服务器端口填写：8888(与Fiddler设置的一致)

4.在手机的浏览器中打开上一步的地址与端口（192.168.3.11:8888）
* 在打开的界面中下载 ”FiddlerRoot certificate“证书
* 下载好之后安装该证书(并让该证书生效，凭证用途选择VPN&应用)

![](https://gitee.com/kolenj/BlogImages/raw/master/20200528010305.png)

5.设置过滤条件即可进行抓包工作

![](https://gitee.com/kolenj/BlogImages/raw/master/20200528014203.png)
          
（PS：抓包之后记得关闭手机代理，以免手机上不了网）


####  三、iOS移动端的拦截设置
**基本与Android端配置一致，要注意的不同的一点就是ios系统安装证书后要开启，具体操作如下：** 

* 进入“设置-通用-关于本机”，点击“证书信任设置”，将fiddler的证书开启即可  

（PS：抓包之后记得关闭手机代理，以免手机上不了网）


####  四、Fiddler额外一些常用操作

0.一些常用名词说明：
* Statistics -请求的性能数据分析
* Inspectors -查看数据内容
* AutoResponder -允许拦截指定规则的请求
* Composer -自定义请求发送服务器
* Filters -请求过滤规则
* Timeline -请求响应时间

1.拦截更改请求/响应的一些数据参数：
* 右击需修改的请求链接url，选中”Unlock For Editing",进入编辑状态
* 修改你需要修改的数据，取消选中”Unlock For Editing",退出编辑状态
* 点击右边的“AutoResponder”，将刚才修改的url拖进面板的空白处，然后勾选"Enable rules"和"Unmatched requests passthrough"
* 再一次执行该请求(刷新对应界面)，即可看到我们期待的结果


####  五、Fiddler的一些高级用法
[官方文档/支持](https://www.telerik.com/support/fiddler)

[参考1](https://my.oschina.net/leejun2005/blog/399108)
[参考2](https://yq.aliyun.com/articles/594456?utm_content=m_1000000403)