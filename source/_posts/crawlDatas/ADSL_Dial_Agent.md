---
title: ADSL拨号代理总结
date: 2019-07-18 09:09:04
tags: 
- 爬虫

categories:
- 爬虫

---

### 阶段一：购买ADSL拨号主机并测试验证代理ip是否能正常使用
#### 1.购买ADSL动态拨号主机(如：云立方动态拨号云主机）
    1.1  购买动态拨号vps，安装CentOS7.1版本
    1.2  成功之后通过cmd命令行执行：ssh root@14.21.37.12 -p 20325 ，输入密码，连接远程拨号主机
    1.3  adsl-start (拨号命令）
    1.4  ifconfig  (Linux下查看IP命令）
    1.5  ping www.baidu.com (测试是否连网成功)
    1.6  adsl-stop (停止拨号命令）
    1.7  adsl-start；ifconfig（测试查看ip是否已不相同）

#### 2.将主机设置为代理服务器
    2.1 安装 TinyProxy
      (在CentOS下使用yum命令来安装)
      yum install -y epel-release
      yum update -y
     （在安装时若出现：Cannot retrieve metalink for repository: epel/x86_64. Please verify its path and try again）
      解决方法见：https://blog.csdn.net/StriverChuiYing/article/details/82318798
      yum install -y tinyproxy
#### 3.配置 TinyProxy
    3.1 对tinyproxy.conf文件进行编辑（查找：find / -name tinyproxy.conf)
          port 8888 - (tinyproxy默认端口，不做更改）
          Allow 127.0.0.1 （默认本地才可进行代理，这里直接注释掉，如下：
          # Allow 127.0.0.1
    3.2 重启TinyProxy
          systemctl enable tinyproxy.service
          systemctl restart tinyproxy.service
    3.3 防火墙开放该端口
          iptables -I INPUT -p tcp --dport 8888 -j ACCEPT
#### 4.验证 TinyProxy 是否配置成功
    4.1 使用命令查看现在的ip地址：ifconfig
          比如我现在的代理ip是：183.52.131.17:8888
    4.2 进行验证：
          可以在这个网站直接验证该代理ip是否可用  [http://web.chacuo.net/netproxycheck]
          或者其他Linux主机进行验证：curl -x 183.52.131.17:8888 httpbin.org/get
          如果有正常的结果输出，并且origin的值为代理IP的地址，则证明TinyProxy配置成功

### 阶段二：编写将动态拨号主机的代理ip发送到固定ip(另外服务器)的redis数据库进行保存更新；以该redis数据的ip构建代理ip池，爬虫程序通过接口随机获取代理ip，具体如下：
#### 1.在一台固定ip的服务器上安装用来保存拨号代理ip的redis数据库
        1.1 下载redis最新稳定版(通用)：wget http://download.redis.io/redis-stable.tar.gz
        1.2 查找redis压缩包位置：find / -name 'redis-stable*'
        1.3 找到执行解压：tar xzf /root/redis-stable.tar.gz
        1.4 编辑redis.conf文件配置redis连接参数:
            daemonize yes  （允许远程连接访问，默认no）
            requirepass redis123456 （设置访问密码，默认无）
            #bind 127.0.0.1
            bind 0.0.0.0  （允许所有ip连接）
      1.5 启动redis：src/redis-server（redis-stable目录下执行）
      1.6 测试redis数据库是否启动成功
            使用Redis Desktop Manager进行远程连接测试
            启动redis-cli客户端进行测试
tips:
官方教程：[https://redis.io/download](https://redis.io/download)
redis设置为随系统启动：[https://blog.csdn.net/qq_42403743/article/details/81358676](https://blog.csdn.net/qq_42403743/article/details/81358676)


#### 2.在ADSL代理主机上安装python3，执行定时更新并向远程redis发送代理ip的脚本
        2.1 安装python3：https://blog.csdn.net/metoo9527/article/details/80330877
        2.2 从GitHub clone编写好的脚本项目：git clone https://github.com/Germey/ADSLProxy.git (崔大项目)
        2.3 编辑项目中的config.py文件， 配置连接远程redis的数据
              *redis主机的ip地址 (默认本地 localhost）
              *连接redis的密码（默认 foobared)
              *连接redis的端口（默认 6379） 
        2.4 安装项目相关依赖库
              pip3 install redis
              pip3 install requests
              pip3 install tornado
        2.5 进入到项目ADSLProxy目录下，执行：
              python3 run.py
              执行结果如下则成功：
![image.png](https://upload-images.jianshu.io/upload_images/2932323-6a1c5f7f6960c5fa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

       
        



          
   