---
title: 常用快捷键
date: 2017-05-16 09:09:04
tags: 
- 快捷键

categories:
- others

---

####  Windows常用快捷键/命令

* Win + E                   （打开 文件资源
* Win + R                   （打开 运行
* Win+  1\2\3...            （打开 任务栏软件
* Alt/Win  +Tab             （切换工作窗口
* Ctrl + Shift + N          （创建文件夹
* Win  + S/Q                （打开快速搜索S/
* Win  + I                  （打开设置
* Win  + D                  （回到桌面
* Win+W /Win + Shift + S    （打开自带截图
* Win  + L                 （快速锁屏
* Win  + G                 （打开录制屏幕功能
* Win + X                  （打开快捷菜单G
* Win + ;                  （呼出Windows自带的 Emoji、颜文字和符号
* Ctrl+A/C/X/V              （全选/复制/剪贴/粘贴
* Ctrl+Shift+W             （自我设置的打开截图工具快捷键


####  chrome常用快捷键

* Ctrl+T                    （打开新标签页
  在地址栏输入网站名称并按“Ctrl+Enter”键 为网站名称添加 www. 和 .com，并在当前标签页中打
* Ctrl+F4                   （关闭当前标签页/弹出窗口
* Ctrl+Shift+T              （重新打开最后关闭的标签页
* Ctrl+1-8/Tab/(Shift+Tab)  （切换标签页PS：Ctrl + 9 跳转到最后一个标签页
* Ctrl+D                    （将当前标签页加入书签
* Ctrl+Shift+O              （打开书签管理器
* Ctrl+H                     (查看打开历史
* Ctrl+J                     (查看"下载"页
* Ctrl+R/=F5                 (重新加载当前页
* Ctrl+F5                   (重新加载当前页，但忽略缓存的内存
* Ctrl+U                   （查看源代码
* Ctrl+Shift+I/=F12        （打开开发者工具
* Ctrl+F/=F3                (搜索
  Ctrl+K/E                  (从页面中的任意位置搜索
  Ctrl+G                    (跳转到与关键字搜索框中的文本相匹配的下一条内容
* Ctrl+Shift+N             （在隐身模式下打开新窗口
* Ctrl+Shift+Delete        （去除缓存
    
* F11                      （开启或关闭全屏模式
* Ctrl+Shift+B             （显示或隐藏书签栏
* Shift+Esc                （打开 Chrome 任务管理器
* Ctrl+Shift+S             （打开chrome网页截图工具
    

####  Pycharm常用快捷键

* Ctrl + F 查找
* Ctrl + R 替换
* Ctrl + Shift + F 全局查找
* Ctrl + Shift + R 全局替换
* Ctrl + N 查找所有的类的名称
* Ctrl + Shift + N 查找项目中的任何文件
    
    
####  photoshop常用快捷键

* 图片的放大缩小，移动：		ctrl+space+鼠标左键拖动 /Alt+鼠标滑轮 / 空格+鼠标左键拖动
* 任意变形，(裁剪时变形）		ctrl+T
* 抠图生成新图层(复制)：		ctrl+J
  直接复制			        alt+移动工具+鼠标左键拖拽
* 橡皮擦大小的调整：		    alt+鼠标右击滑动 / 或 []  
* 全选/反选/取消选择		    ctrl+A / ctrl+shift+I / ctrl+D
* 选择全页			        ctrl+0
  
     
####  SharX截图工具常用快捷键

* Ctrl + PrtSc              （窗口截图
* PrtSc                     （全屏截图
* A                         （箭头指向
* L                         （画直线

          
####  Tmux常用指令

    1、Tmux安装：    
        $ sudo apt-get install tmux                 （# Ubuntu 或 Debian
        
        $ sudo yum install tmux                      （# CentOS 或 Fedora

        $ brew install tmux                          （# Mac
        
    2、会话操作：
        $ tmux
        
        $ tmux new -s <session-name>                 （启动一个自定义名称的会话
        
        $ tmux detach（=Ctrl+b d                      （将当前会话与窗口分离
        
        $ tmux ls                                     （查看所有会话
        
        $ tmux attach -t 会话编号/会话名称               （接入会话
        
        $ tmux kill-session -t 会话编号/会话名称         （杀死会话
        
        $ tmux switch -t 会话编号/会话名称                （切换会话
        
        $ tmux rename-session -t 会话编号 会话名称(新名称)  （重命名会话
    
    3、窗格操作：
        $ tmux split-window (-h)                （ 划分为上下两个窗格/-h划分为左右两个窗格
        
        $ tmux select-pane -U(D/L/R)            （移动光标到上/下/左/右
        
        $ tmux swap-pane -U/D                     （# 当前窗格上移/下移
        
        
    
    4、其它命令： 
        $ tmux list-keys                        （# 列出所有快捷键，及其对应的 Tmux 命令

        $ tmux list-commands                    （# 列出所有 Tmux 命令及其参数

        $ tmux info                             （# 列出当前所有 Tmux 会话的信息
  
        $ tmux source-file ~/.tmux.conf          （# 重新加载当前的 Tmux 配置
        
    5、Tmux常用快捷键：
        Ctrl+b                    (前缀键   
        Ctrl+d                    (退出当前会话=exit
        
        Ctrl+b d                  (分离当前会话
        Ctrl+b s                  (列出所有会话
        Ctrl+b $                  (重命名当前会话
        
        Ctrl+b %                  (划分左右两个窗格。
        Ctrl+b "                  (划分上下两个窗格。
        Ctrl+b <arrow key>        (光标切换到其他窗格。<arrow key>是指向要切换到的窗格的方向键，比如切换到下方窗格，就按方向键↓。
        Ctrl+b ;                  (光标切换到上一个窗格。
        Ctrl+b o                  (光标切换到下一个窗格。
        Ctrl+b {                  (当前窗格左移。
        Ctrl+b }                  (当前窗格右移。
        Ctrl+b Ctrl+o             (当前窗格上移。
        Ctrl+b Alt+o              (当前窗格下移。
        Ctrl+b x                  (关闭当前窗格。
        Ctrl+b !                  (将当前窗格拆分为一个独立窗口。
        Ctrl+b z                  (当前窗格全屏显示，再使用一次会变回原来大小。
        Ctrl+b Ctrl+<arrow key>   (按箭头方向调整窗格大小。
        Ctrl+b q                  (显示窗格编号。

