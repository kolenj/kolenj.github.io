---
title: docker常用命令
date: 2016-06-23 09:29:22
tags: 
- docker

categories:
- 软件技术

---


#### 一、docker镜像常用命令

    常用参数说明：
        -a/-filter/-f                                   （所有/过滤条件/强制执行---常用参数说明
        
    搜索镜像：
        docker search 镜像名                             （搜索镜像
        docker search --filter=is-offical=true ngix
        docker search --filter=stars=10 tensorflow
    
    拉取镜像：
        docker pull [服务器]/镜像名:版本号                 （不指定版本号则默认拉取最新版本=镜像名:latest
        docker images                                     (列出本机已拉取的镜像
        docker tag 镜像名 标签名                           (给镜像添加标签
    
    查看镜像：
        docker inspect 镜像名                               (查看镜像信息
        docker inspect -f {{".Architecture"}} mysql         (根据过滤条件查看镜像信息
    
    删除镜像：
        docker rmi 镜像的id/标签                             （删除镜像
        docker image prune                                  （清理镜像，-a，-f
        
    
    创建镜像的3种方式：
        1、基于已有容器创建
              docker commit -m "added a new file " -a "kolenj" 容器id test:0.1
        2、基于本地模板导入
              cat ubuntu-18.04-x86_64-minimal.tar.gz | docker import - ubuntu:l8.04
        3、基于Dockerfile创建
              docker build -t 镜像名 Dockerfile路径          （比如：docker build -t tomcat7 . 
            
        
    存出与载入镜像：
        docker load -i ubuntu_18.04.tar                      (载入镜像
        docker save -o ubuntu 18.04.tar ubuntu:18.04         （存出镜像
    
    上传镜像：
        docker tag test:latest user/test:latest 
        docker push user/test:latest
  
#### 二、docker容器常用命令
    
    参数说明：
        -t 选项让Docker分配一个伪终端（pseudo－tty）并绑定到容器的标准输入上，-i 则让容器的标准输入保持打开
        -p 端口映射[宿主机端口:容器的端口];   -v 路径(数据卷)映射 
    
    查看容器：
        docker ps	                                        （查看运行的容器	
        docker ps -a	                                    （查看所有的容器
        docker container inspect 容器id                      （查看容器详情
        docker top 容器id                                    （查看容器内进程信息
     
    查看容器使用的资源：
        docker stats                                        （查看容器使用的资源信息，持续输出
        docker stats --no-stream                            （查看容器使用的资源信息,只输出当前使用的资源
        docker stats --no-stream 容器id                      （查看指定容器使用的资源信息
        docker stats --no-stream                            （查看容器使用的资源信息,只输出当前使用的资源
        
        docker stats --format "table {{.Name}}\t{{.CPUPerc}}\t{{.MemUsage}}"    (格式化输出结果信息
        
    创建/启动容器：
        docker create -it 镜像id                             （创建
        docker start [create命令产生的容器id]                  （启动
    
        docker run ubuntu /bin/echo 'hello world'             (创建并启动容器
        docker run -it ubuntu:18.04 /bin/bash                 (启动一个 bash终端，允许用户进行交互：
        
        docker run -d ubuntu /bin/sh -c "while true; do echo hello world; sleep 1; done"       (以守护状态运行
    
    停止容器：
        docker pause/unpause 容器                              (暂停容器/继续运行容器
        docker stop 容器                                      （该命令会首先向容器发送SIGTERM信号，等待一段超时时间后（默认为10秒），
                                                               再发SIGKILL信号来终止容器
        docker kill 容器                                      （直接发送SIGKILL信号强行终止容器
   
     
     进入容器：
        docker attach 容器name/id                             （进入容器方式一
        docker exec -it 容器name/id  /bin/bash(=bash)         （进入容器方式二 ---推荐方式   
     
     删除容器：
         docker rm 容器                                       （删除处于终止/退出状态的容器，                                                  
         docker rm -f 容器                                    （强制删除运行中的容器
         docker container prune                               (清除掉所有处于停止状态的容器


     导出容器：
         docker export -o xxx.tar 容器id                      (方式一
         docker export 容器id > xxx.tar                       (方式二
         
      导入容器：
          docker import xxx.tar 镜像名:标签
          
#### 三、docker其它命令

       docker cp data 容器名/id:/tmp/                             (将本地路径data 复制到test容器的/tmp路径下
       docker container diff 容器名/id                           （查看容器内文件系统的变更
       docker container port 容器名/id                           （查看容器的端口映射
       docker logs [OPTIONS] CONTAINER                           (查看日志


#### 四、docker数据管理

    1、容器中的管理数据主要有两种方式：
    
            数据卷(Data Volumes)：容器内数据直接映射到本地主机环境
            数据卷容器(Data Volume Containers)：使用特定容器维护数据卷


#### 五、Dockerfile

    Dockerfile：
        Dockerfile是一个文本格式的配置文件，用户可以使用Dockerfile来快速创建自定义的镜像
    它是由一行行命令语句组成，并且支持以＃开头的注释行。
    
    主要格式形式可以分为四部分： 基础镜像信息、维护者信息、镜像操作指令和容器启动时执行指令。
    
    FROM XXX                                表示以xxx镜像为基础来创建当前镜像，类似面向对象编程中的继承概念
    
    WORKDIR /webapps                        指明接下来的shell语句是运行在那个路径下
    
    COPY src/ /webapps                      表示将当前宿主机src/下所有文件拷贝到镜像的/webapps中
    -ADD COPY与ADD的区别是 ADD命令时 "src/"    可以是uri（网络资源）
    
    RUN echo helloworld >> hw.txt           执行shell语句（在镜像构建时就执行
    
    CMD cat hw.txt                          执行shell语句（容器启动后执行
    CMD ["cat", "hw.txt"]                   json格式，等同上面语句
    -ENTRYPOINT  CMD与ENTRYPOINT区别，两者都存在，ENTRYPOINT命令后面是以非json格式时，执行ENTRYPOINT，CMD无效，
     如果都是json格式则两者都执行
    
    EXPOSE                                  镜像暴露端口
    
    VOLUME /test/a 宿主机xxx路径               将容器的/test/a 映射到宿主机xxx路径下
    
    ENV A 10                                 创建环境变量A，从镜像构建到容器运行都有效
    ARG B 20                                 创建环境变量B，只在镜像构建时有效，相当默认值，在构建时可重新赋值
    -例子：docker build -t test --build-arg B=100 .
    
    LABEL key="value"                        就起到一个标识标签的作用
    ONBUILD 其他Dockerfile命令                 在它的"子镜像"-继承当前镜像构建镜像时才起作用
    
   