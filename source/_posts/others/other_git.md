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
    
   
**Git的安装**

    -Linux-
    Debian或Ubuntu系统：sudo apt-get install git
    
    Linux其他系统版本的源码安装方式：从Git官网下载源码，解压，依次输入：./config，make，sudo make install
    
    -Windows-
    Windows下安装：从Git官网下载安装程序，安装完成后从“开始菜单”里找到“Git”->“Git Bash”，能正常打开
    则表示已安装成功。
    进行全局配置：
    $ git config --global user.name "your name"
    $ git config --global user.email "youremail@example.com"
    
    
**通过ssh加密方式进行本地Git仓库与GitHub仓库之间传输**

    1、打开Git Bash
    2、$ ssh-keygen -t rsa -C "youremail@example.com"    (创建SSH Key，默认一路回车
    3、执行步骤1命令将在用户主目录里生成.ssh目录，里面有id_rsa(私玥)和id_rsa.pub(公玥)两个文件
    4、登陆GitHub账号，打开“Account settings”，“SSH Keys”页面，
       点“Add SSH Key”，Title任意取，在Key文本框里粘贴id_rsa.pub文件的全部内容
    5、$ ssh -T git@github.com      （测试是否连接成功，PS:成功提示会有successfuly authenticated字段


    
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
    
 
**远程库(github)操作**

    1、登录GitHub，创建一个新的仓库，如testblog
    2、$ git remote add origin git@github.com:yourname/testblog.git    (可以从testblog克隆新仓库或将一个本地仓库与之关联
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
    16、git remote                       #查看远程库的信息,远程仓库的默认名称是origin
    17、git remote -v                    #显示更详细的信息
    18、git push origin dev              #推送分支dev(一般分支有master、dev、bug、feature)
    19、git checkout -b branch-name origin/branch-name               #在本地创建和远程分支对应的分支(名称最好一致)
    20、git branch --set-upstream branch-name origin/branch-name     #建立本地分支和远程分支的关联
    21、git pull                         #从远程抓取分支，如果有冲突，要先处理冲突
    
    标签：
    1、git tag <tagname>                             #用于新建一个标签，默认为HEAD，也可以指定一个commit id
    2、git tag -a <tagname> -m "blablabla..."        #指定标签信息blabla...
    3、git tag                                       #查看所有标签
    
    4、git push origin <tagname>                     #推送一个本地标签
    5、git push origin --tags                        #推送全部未推送过的本地标签
    6、git tag -d <tagname>                          #删除一个本地标签
    7、git push origin :refs/tags/<tagname>          #删除一个远程标签
    
    
**使用Gitee**

    1、注册账号并登录Gitee
    2、上传自己的SSH公钥 (用户主目录下的.ssh/id_rsa.pub文件的内容,没有则执行：
    
        $ git config --global user.name "your name"
        $ git config --global user.email "youremail@example.com"
        $ ssh-keygen -t rsa -C "youremail@example.com"    #创建SSH Key
        (PS: 如果登录邮箱不一致该公玥是否有效？)
    3、在Gitee中创建项目，名称保持和本地项目一致
    4、git remote add origin git@gitee.com:kolenj/testgit.git（将本地的项目和Gitee的远程库关联）
       (如果出现：fatal: remote origin already exists.说明本地库已经关联了一个名叫origin的远程库）
    5、git remote -v             #查看远程库信息,如果该项目之前关联了GitHub的远程库，则可能提示：
       （origin	git@github.com:kolenj/testgit.git (fetch)
         origin	git@github.com:kolenj/testit.git (push)
         
    6、git remote rm origin      #删除之前关联的GitHub远程库
    7、执行步骤4
       

**同时关联GitHub与Gitee**

    1、git remote rm origin          #首先删除已关联的名为origin的远程库
    2、git remote add github git@github.com:kolenj/testgit.git     #接着先关联GitHub的远程库
       (此时远程库的名称叫github，不叫origin了）
    3、git remote add gitee git@gitee.com:kolenj/testgit.git       #再关联Gitee的远程库
       (此时远程库的名称叫gitee，不叫origin了）
    4、git remote -v                 #查看关联库的信息
    5、git push github master        #推送送GitHub
    6、git push gitee master         #推送到Gitee
    
    
    
**Git其它有用命令**
    
    1、$ git config --global color.ui true       #让Git显示颜色
    2、$ git add -f App.class                    #强制提交提交(该类文件已被在.gitignore配置中忽略)
    3、git check-ignore -v db.json               #检查对应文件(这里是db.json)的gitignore配置信息
    4、$ git config --global alias.st status     #配置别名：将status简写成st
    

Tips：Git常见命令

https://gitee.com/liaoxuefeng/learn-java/raw/master/teach/git-cheatsheet.pdf

    