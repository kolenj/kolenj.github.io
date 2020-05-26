---
title: other_trojan_vpn
date: 2020-05-20 03:57:38
tags: 
- trojan
- vpn

categories:
- others

---

### 注册Google/Azure/Amazon AWS/阿里云/其他等云服务器
    
#### -Azure：

1、进入控制面板主页，点击创建虚拟机，建议设置如下图

![](https://gitee.com/kolenj/BlogImages/raw/master/20200521055520.png)

2、创建存储账户，名字随便起

![](https://gitee.com/kolenj/BlogImages/raw/master/20200521055938.png)

3、点击公网ip，将其改为静态ip

![](https://gitee.com/kolenj/BlogImages/raw/master/20200521061923.png)

4、到你已申请好的域名下绑定该公网ip，我这里是阿里云平台下的域名面板

    tips：添加两条记录，其中一条在主机记录填写 www，另外一条填写 @
    绑定好之后在cmd下执行ping命令测试是否绑定生效：
    ping 刚才绑定的域名
    
![](https://gitee.com/kolenj/BlogImages/raw/master/20200521060251.png)



5、通过公网静态ip，进行ssh连接登录（我这里是win10 cmd 下执行）
    
    ssh 用户名@xxx.xxx.xxx.xxx(公网ip)
    输入第一步配置时的密码进行登录
    登录成功后给root设置密码，切换到root执行之后命令 
    相关命令：sudo passwd(给root设置密码), su root(切换到root)
    
![](https://gitee.com/kolenj/BlogImages/raw/master/20200521061100.png)

6、执行trojan安装脚本

    执行更新：                  yum update
    安装wget：                  yum install wget -y
    安装trojan，开启 TLS1.3：    curl -O https://raw.githubusercontent.com/atrandys/trojan/master/trojan_mult.sh && chmod +x trojan_mult.sh && ./trojan_mult.sh
    选择安装Trojan(数字1)
    输入上面绑定的域名
    通过下载连接（下图)下载trojan-cli客户端！！！
    （tips：如果真忘记下载了，进入/usr/share/nginx/html/目录下查找一个类似“5052ee55af3e6b04”这样名称的文件夹，里边有）

![](https://gitee.com/kolenj/BlogImages/raw/master/trojan下载.jpg)

##### (PC端的VPN配置)

7、下载trojan-cli后解压，通过执行文件夹下的 start.bat/stop.bat 文件进行trojan服务的开启与关闭

8、到 https://github.com/2dust/v2rayN/releases 下载最新稳定版 v2rayN-Core.zip，解压执行v2rayN.exe，
第一次要进配置：点击服务器，选择添加[Sockes]服务器,进行如下图配置

![](https://gitee.com/kolenj/BlogImages/raw/master/20200521061231.png)

9、运行后右击v2rayN.exe 图标，进行选择需要的代理上网模式，一般选择PAC模式（本地网址智能的选择无需通过代理进行访问）

![](https://gitee.com/kolenj/BlogImages/raw/master/20200521061429.png)

10、浏览器访问 www.google.com  成功访问，Trojan翻墙VPN搭建成功！

![](https://gitee.com/kolenj/BlogImages/raw/master/20200521061506.png)


#### 移动端vpn软件的安装(android)：

1、下载安装lgniter

https://github.com/trojan-gfw/igniter/releases

2、进行lgniter如下图配置，其中ip填写上面公网的ip地址，端口默认443，密码在上面解压的 trojan-cli 客户端文件夹里找到config.json,
记事本打开查看“password”字段即可获取

![](https://gitee.com/kolenj/BlogImages/raw/master/20200521064224.png)


