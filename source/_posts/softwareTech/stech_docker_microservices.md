---
title: 使用Docker搭建微服务
date: 2019-07-12 19:13:32
tags: 
- docker
 
categories:
- 软件技术

---
#### 一、使用Docker搭建Tomcat

* 1、搜索Tomcat镜像
    * docker search tomcat

* 2、拉取Tomcat镜像
    * docker pull tomcat (tomcat:8.0 -拉取指定的版本,默认是最新版本latest)
    
* 3、启动Tomcat容器
    * docker run -d -p 8080:8080 tomcat
    
        (-d 允许后台运行，-p 端口映射[宿主机端口:容器端口])
        
* 4、成功启动后在浏览器输入:IP:宿主机端口(localhost:8080) 能正确访问Tomcat主页,则表示容器的Tomcat已配置成功

     ![](https://gitee.com/kolenj/BlogImages/raw/master/20200613110934.png)

    (PS:[问题(HTTP Status 404 – Not Found)解决参考](https://blog.csdn.net/laiyuan999/article/details/105802110))


#### 二、使用Docker搭建java环境

#### 二、使用Docker搭建Jenkins

* 搜索Jenkins镜像
    * docker search jenkins

#### 二、使用Docker搭建nginx

#### 二、使用Docker搭建MySQL

#### 二、使用Docker搭建Redis

#### 二、使用Docker搭建MongoDB

        