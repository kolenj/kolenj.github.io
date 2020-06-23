---
title: 搭建Git服务器
date: 2017-06-11 19:33:12
tags: 
- git

categories:
- others

---

**搭建Git服务器流程**

    说明：
    GitHub就是一个免费托管开源代码的远程仓库。如果我们不想公开源代码，又舍不得给GitHub使用商业收费版，
    那我们可以自己搭建一台Git服务器作为私有仓库使用。
    搭建Git服务器需准备一台运行Linux的机器，这里强烈推荐用Ubuntu或Debian。
    
    步骤：
    1、安装git：
        $ sudo apt-get install git              #在sudo权限下
        
    2、创建一个git用户，用来运行git服务：
        $ sudo adduser git           
                   
    3、创建登录证书:
        收集所有需要登录的用户的公钥，就是他们自己的id_rsa.pub文件，把所有公钥
        导入到/home/git/.ssh/authorized_keys文件里，一行一个
        
    4、初始化Git仓库：
        先选定一个目录作为Git仓库，假定是/srv/learn.git，在/srv目录下输入命令：
        $ sudo git init --bare learn.git
        配置不让用户直接登录到服务器上去改工作区
        $ sudo chown -R git:git learn.git
        
    5、禁用shell登录：
        编辑/etc/passwd
        将：git:x:1001:1001:,,,:/home/git:/bin/bash
        改为：git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell
        
    6、克隆远程仓库：
        $ git clone git@server:/srv/learn.git
        Cloning into 'sample'...
        warning: You appear to have cloned an empty repository.
        
    7、推送更改
        git add xxx
        git commit -m "some description..."
        git push 
 
**要方便管理公钥，使用Gitosis**  

**要像SVN那样进行权限控制，用Gitolite**   