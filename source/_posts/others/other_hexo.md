---
title: hexo博客的搭建
date: 2018-09-18 09:09:04
tags: 
- hexo

categories:
- others

---
### 环境的搭建

#####  1、登陆GitHub，创建博客仓库，仓库名格式固定为：yourname.github.io

#####  2、git的安装(详情请看git篇博文)

#####  3、node.js的安装

        下载地址：https://nodejs.org/en/download/
        (PS:Node.js的安装会包含环境变量设置及npm的安装)
        安装完命令行窗口执行: 
        node -v     验证是否安装成功
        npm  -v     验证npm是否安装成功

### 创建第一个hexo博客 

        mkdir myblog                (创建一个文件夹如：myblog
        cd myblog                   (进入该文件夹
        npm install -g hexo-cli     (执行安装hexo,电脑已安装则跳过
        hexo init                   (初始化hexo
        hexo n myfirstblog          (hexo new "我的博客" #新建文章
        hexo g                      (hexo generate #生成
        hexo s                      (hexo server #启动服务预览
        
        其它Hexo 命令：
        hexo server #Hexo会监视文件变动并自动更新，无须重启服务器
        hexo server -s #静态模式
        hexo server -p 5000 #更改端口
        hexo server -i 192.168.1.1 #自定义 IP
        hexo clean #清除缓存，若是网页正常情况下可以忽略这条命令
        

###  推送部署到远程GitHub
        
        1、配置本地blog项目与GitHub的仓库的关联：
            打开根目录里的_config.yml站点设置文件进行如下修改
            
            deploy:
                type: git
                repo: https://github.com/kolenj/kolenj.github.io.git
                branch: master
                
        (PS：根目录里的themes文件夹里也有个同名的“主题”配置文件_config.yml)
        
        2、安装Git部署插件
            npm install hexo-deployer-git --save
            
        3、进行部署：
            hexo clean 
            hexo g 
            hexo d              (hexo deploy #部署到GitHub
            

###  端更新维护
        
         说明：
         hexo g -d 部署的是项目根目录下.deploy_git目录(“静态文件”)，存放在master分支(PS:该分支并不是git仓库)
         现在我们创建hexo分支，将本地的hexo博客项目与hexo分支关联起来 从而进行多端维护更新“环境文件”(博客)
         
         终端A:(源端）
             1、登录到GitHub在当前博客仓库下创建hexo分支，并将其设置为默认
             2、git clone 仓库.git  如：git clone https://github.com/kolenj/kolenj.github.io.git
             3、本地将多出一个xxx.github.io文件夹，cd 进入该目录，将该文件夹下除了“.git”文件夹的其它文件(夹)全部删除
             4、-----！！！ 将themes文件夹下“主题”文件夹里的.git文件夹删除(如果安装了主题的话）！！！-----
             5、执行：git add -A                        (把工作区的变化（包括已删除的文件）提交到暂存区
             6、执行：git commint -m "提交描述..."       (提交更改
             7、执行：git push origin hexo              (推送到远程hexo分支
             
             8、复制本地xxx.github.io文件夹中的.git文件夹到hexo项目根目录(此时既是将hexo博客项目(环境文件)与GitHub仓库的hexo分支关联起来)
             9、切换回到hexo博客项目根目录，并将文件夹xxx.github.io删除
             
             10、推送部署则执行：
                hexo clean
                hexo g -d
                
             11、经过步骤10部署后经过浏览检查则可把环境文件推送到hexo分支：
                git add . 
                git commit -m "some commit description" 
                git push origin hexo (如果推送失败，则先用git pull抓取远程的新提交，解决冲突再推送)
             
                
            
         终端B:(非源端-新电脑）
              1、安装node.js、Git
              2、安装hexo：npm install -g hexo-cli
              3、clone远程仓库到本地：git clone https://github.com/yourname/yourname.github.io.git
              4、进入clone的仓库目录根据packge.json安装依赖：npm install
              5、测试部署，并浏览检查(操作步骤同上10)
              6、提交博客的更改(操作步骤同上11)
              
            
###  域名绑定
        
        Todo：

###  个性化设置

        Todo：


    
*参考*：

https://zhuanlan.zhihu.com/p/35668237
https://zhuanlan.zhihu.com/p/26625249
https://blog.plcent.com/2019/11/05/hexo-theme-pure/
https://www.jianshu.com/p/fceaf373d797
