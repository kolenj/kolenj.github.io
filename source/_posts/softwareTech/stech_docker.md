---
title: Docker的安装
date: 2018-09-12 19:13:32
tags: 
- docker
 
categories:
- 软件技术

---
####一、docker简介

    Docker 是一个开源的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的容器中,
    然后发布到任何流行的Linux机器或Windows 机器上,也可以实现虚拟化,容器是完全使用沙箱机制,相互之间不会有任何接口。
   

####二、docker安装

**Windows安装：(https://docs.docker.com/docker-for-windows/install/)**

1、系统硬件要求：

    64位系统
    最小4GB内存
    BIOS支持虚拟化技术
![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200426211735.png)

2、开启Hvper-V：
    
    在电脑上进入——》“控制面板\程序\程序和功能”，点击启动或关闭Windows功能
    
    Microsoft Hyper-V is required to run Docker Desktop. The Docker Desktop Windows installer enables Hyper-V if required, and restarts your machine.
    When Hyper-V is enabled, VirtualBox no longer works. However, any existing VirtualBox VM images are retained.
![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200426212658.png)

3、下载并安装Docker Desktop Installer.exe

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200426212108.png) 

4、运行docker：

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200426212250.png)

5、使用docker国内镜像

    右击点击docker图标，点击Settigs,进入设置页面按照如下图添加docker国内镜像
    如我用的是阿里云的镜像：https://rsdddmei.mirror.aliyuncs.com
![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200427231456.png)



**Linux安装(ubuntu): (https://docs.docker.com/engine/install/ubuntu/)**

1、OS requirements

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200426222602.png)

2、Uninstall old versions
``` 
    $ sudo apt-get remove docker docker-engine docker.io containerd runc
```

3、Install using the repository
```
    1.Update the apt package index and install packages to allow apt to use a repository over HTTPS:
    
        $ sudo apt-get update
        
        $ sudo apt-get install \
            apt-transport-https \
            ca-certificates \
            curl \
            gnupg-agent \
            software-properties-common
    
    2.Add Docker’s official GPG key:
    
        $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

        $ sudo apt-key fingerprint 0EBFCD88

    3.to set up the stable repository

        $ sudo add-apt-repository \
           "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
           $(lsb_release -cs) \
           stable"

```

4、INSTALL DOCKER ENGINE
``` 
    1.安装最新版本：Update the apt package index, and install the latest version of Docker Engine and containerd
        $ sudo apt-get update
        $ sudo apt-get install docker-ce docker-ce-cli containerd.io

      安装指定版本：
        $ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io

    2.开启docker服务
        $ sudo systemctl start docker

    3.运行hello world
        $ sudo docker run hello-world
```


**其它版本安装请自己参考官方文档：https://docs.docker.com/**







        