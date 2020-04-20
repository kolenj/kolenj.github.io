---
title: Linux常用命令
date: 2019-03-25 09:09:04
tags: 
- Linux

categories:
- others

---

+ **查询IP**
          
          1、ipconfig（查看ip地址-Windows） - 2019/04/11

          2、ifconfig （查看ip地址-Linux） - 2019/04/11

---

+ **基本操作**

      1、shutdown -h  now/1  （立即关机/1分钟后关机
         shutdown -r now  （立即重启

      2、reboot   （重启

      3、clear  （清屏


+ **文件/目录的操作**

      1、cd 目录/~/../-   （转移到某目录/回到用户家目录，等同cd 回到上级目录/上次目录

      2、mkdir -p /usr/local/python3   （创建目录(多级递归创建) 、可一次创建多个，使用空格分开

      3、touch hello.py /or 直接 vi/vim 文件名   （创建文件

      4、chmod u/g/o/a +/-/= rwx 文件  （ chmod 777 test.py 其 r：4   w：2   x：1
         [-R : 对目前目录下的所有档案与子目录进行相同的权限变更(即以递回的方式逐个变更)]

      5、ls -a/l/d   （-a 显示所有文件/-l	long 长格式显示/-d 查看目录属性
         ls > test.txt ( test.txt 如果不存在，则创建，存在则覆盖其内容 )

      6、pwd   （查看当前工作目录

      7、cp -rp [源文件] [目标文件]  （-r 复制目录/-p 保留文件属性（时间属性等）

      8、mv [旧文件名] [新文件名]   （重命名/转移-tips：同目录则是重命名/否则是转移

      9、rmdir [目标]  （只能删除空白目录

      10、rm [-rf ] 文件/目录   (-r: 删除目录-f: 强制执行

      11、cat是一次性显示整个文件的内容，适用于文件内容少的情况；
          more和less一般用于显示文件内容超过一屏的内容，并且提供翻页的功能。
          tail 和 head分别显示文件的后几行和前几行内容。常用于大文件的截取。
          [参考：https://blog.csdn.net/lijing742180/article/details/83409704]

+ **其他常用命令**

      1、ps -l   （查看程序进程
         ps -ef | grep redis  （查看特定进程-redis
         kill -9 xxx(进程pid)  （杀死特定进程

      2、grep 'hello' test.txt  （文本搜索

      3、ssh root@xxx.xxx.xxx.xxx(ip地址) -p xxx(端口)   （ssh连接Linux服务器

      4、find ./ -name '*.sh'  （查找文件/文件夹

      5、sudo passwd root  （刚刚装好的系统切换到root用户

      6、systemctl enable/restart tinyproxy.service  （重启某个服务

      7、iptables -I INPUT -p tcp --dport 8888 -j ACCEPT  （防火墙开发某个端口

      8、systemctl stop firewalld.service  （关闭防火墙

      9、tar -czvf test.tar.gz a.c  （ 压缩 a.c文件为test.tar.gz
         tar -xzvf test.tar.gz   （ 解压test.tar.gz文件

         压缩用法：tar -jcvf 压缩包包名 文件...(tar jcvf bk.tar.bz2 *.c)
         解压用法：tar -jxvf 压缩包包名 (tar jxvf bk.tar.bz2)

      10、ln 源文件 链接文件
         ln -s 源文件 链接文件
         [如果没有-s选项代表建立一个硬链接文件，两个文件占用相同大小的硬盘空                  
         间，即使删除了源文件，链接文件还是存在，所以-s选项是更常见的形式。]



+ **vi常用命令**

      1、H-(左) J-(下) K-(上) L-(右)
      
      2、ctrl+f/b，向前/后翻页
      
      3、命令行模式下查找：/xxx

   