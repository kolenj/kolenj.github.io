---
title: Git常用操作命令
date: 2017-06-25 09:09:04
tags: 
- git

categories:
- others

---

**Git的简介**

    流行版本控制系统有：SVN、CVS、Git，其中SVN、CVS是集中式的版本控制，而Git是分布式
    
   
**Git的安装****Git的安装**
**Git的安装****Git的安装**

    -Linux-
    Debian或Ubuntu系统：sudo apt-get install git
    
    Linux其他系统版本的源码安装方式：从Git官网下载源码，解压，依次输入：./config，make，sudo make install
    
    -Windows-
    Windows下安装：从Git官网下载安装程序，安装完成后从“开始菜单”里找到“Git”->“Git Bash”，能正常打开
    则表示已安装成功。
    进行全局配置：
    $ git config --global user.name "Your Name"
    $ git config --global user.email "email@example.com"
    
**Git的版本创建**(windows)
    
    1、打开“Git Bash”，通过命令创建一个新目录并进入该目录：
        mkdir studygit
        cd studygit
        (pwd命令 显示当前目录/c/Users/xxx/studygit)
        
    2、通过git init命令把这个目录变成Git可以管理的一个空仓库
        git init
        Initialized empty Git repository in /xxx/../.git/
        (Tips:之后将创建一个.git的目录，这个目录是Git来跟踪管理版本库)
        
    3、创建文件如：readme.txt,并添加一些描述说明
        touch readme.txt
        vi readme.txt   #添加'Git is a free control system.'
    4、把文件添加到本地仓库：
        git add readme.txt
    5、把文件提交到本地仓库    
        git commit -m "wrote a readme file"
        (Tips：其中 -m 'xxx...' 是提交说明注解）
    
        

**通过ssh加密方式进行本地Git仓库与GitHub仓库之间传输**

    1、打开Git Bash
    2、$ ssh-keygen -t rsa -C "youremail@example.com"    (创建SSH Key，默认一路回车
    3、执行步骤1命令将在用户主目录里生成.ssh目录，里面有id_rsa(私玥)和id_rsa.pub(公玥)两个文件
    4、登陆GitHub账号，打开“Account settings”，“SSH Keys”页面，
       点“Add SSH Key”，Title任意取，在Key文本框里粘贴id_rsa.pub文件的全部内容
    5、$ ssh -T git@github.com      （测试是否连接成功，PS:成功提示会有successfuly authenticated字段



**远程库(github)操作**

    1、登录GitHub，创建一个新的仓库，如testblog
    2、$ git remote add origin git@github.com:path/testblog.git    (可以从testblog克隆新仓库或将一个本地仓库与之关联
       (克隆命令：git clone git@github.com:kolenj/testblog.git ,然后cd testblog)
    3、$ git push -u origin master       (将本地库的所有内容推送到远程库上，第一次推送使用参数u表示将本地的master与远程master关联起来


    
**Git的工作区和暂存区**

    git add 将文件从“工作区”添加到->“版本区”的stage，
    git commit 将“版本区”stage里的文件提交到HEAD的指向区，如主分区master

![myImg](public/images/avatar.jpg)

解决markdown显示不了图片：
https://blog.csdn.net/weixin_30444105/article/details/98096284?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-4&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-4

https://blog.csdn.net/qq_41223155/article/details/89672742?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2

**Git的常用命令及说**
    
    1、git add <file>                    #添加文件到仓库,可以多个一个添加
    2、git commit -m "xxx..."            #一次提交所有add的文件到仓库
    3、git status                        #查看工作区的状态
    4、git diff <file>                   #查看文件的具体修改内容
    5、git log                           #查看历史提交记录(详情模式
    6、git log --pretty=oneline          #查看历史提交记录(简洁模式
       git reset --hard HEAD^            #回退到上一个版本（HEAD表示当前版本，^表示上一个版本
       git reset --hard 1094a            #回退到1094a...版本
    7、git reflog                        #查看历史命令
    
    8、git checkout -- file              #丢弃工作区的修改/误删恢复
    9、git reset HEAD <file>             #把暂存区的修改撤销掉（unstage），重新放回工作区
    10、git rm <file>                    #从版本库中删除文件,之后也要执行git commit 命令才起效

    11、git checkout -b dev              #创建并切换到dev分支(新：git switch -c dev)
       (相当于创建: git branch dev, 切换：git checkout dev(新：git switch dev))
    12、git branch                       #查看所有分支，带*表示当然default分支
    13、git merge dev                    #合并指定分支(dev)到当前分支
    14、git branch -d dev                #删除分区dev

    15、git log --graph                  #查看分支合并图
    