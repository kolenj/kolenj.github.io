---
title: 使用Sakura Frp进行内网穿透实现远程桌面
date: 2019-11-17 09:29:22
tags: 
- 远程桌面/frp

categories:
- others

---

**注册并下载安装Sakura Frp**

1、到 [Sakura官网](https://www.natfrp.com/) 进行注册

2、登录获取"访问密钥"

![](https://gitee.com/kolenj/BlogImages/raw/master/20200611200524.png)

3、下载安装客户端(需被远程访问的主机上安装)

![](https://gitee.com/kolenj/BlogImages/raw/master/20200611215519.png)

4、点击添加隧道，按下图所示配置,然后启动该隧道

![](https://gitee.com/kolenj/BlogImages/raw/master/20200611215213.png)
 
5、获取第四步开启隧道后的提示的-服务器/ip地址

![](https://gitee.com/kolenj/BlogImages/raw/master/20200611215846.png)

6、在其他电脑上运行“远程桌面”通过上一步的服务器/ip地址进行连接访问

![](https://gitee.com/kolenj/BlogImages/raw/master/20200611223443.png)

(PS：确保需被远程访问的pc开启了’允许被远程连接‘，进行远程桌面连接时使用用户名和mima)

[参考](https://www.iappi.cn/2020_04/20191370.html)