---
title: appium的环境搭建与常用adb命令
date: 2018-04-20 09:09:04
tags: 
- appium

categories:
- 软件测试

---

#### 一、wifi无线调试环境的搭建

1.手机(移动端设备)和PC处于同一局域网

2.在手机的开发者选项里选择开启“Android 调试”功能

3.先用usb数据线将手机连接上电脑，然后cmd命令行执行 ：adb tcpip 5555，
  显示成功开放5555端口后拔掉数据线

4.cmd执行: adb connect [手机的ip地址]:5555 (PS: 5555为默认端口)

5.如果成功连接，执行adb devices 命令即可显示已连接的设备(手机)

Tips：如果手机端有”网络ADB调试“功能，在手机端开启“网络ADB调试"，
即可通过cmd执行: adb connect [手机的ip地址] 进行远程连接 -(端口默认5555) 
 
   

#### 二、常用adb命令

查看手机信息：
- adb shell ifconfig          //查看手机ip
* adb shell getprop ro.build.version.release        //查看系统版本

[更多参考](https://www.cnblogs.com/zhuminghui/p/10472193.html)
  
adb服务的开启与关闭：
* adb kill-server             //关闭adb服务
* adb start-server            //开启adb服务
        
查看/无线调试-设备：
* adb devices              //显示连接设备
* adb -s 设备号 指令         //多个设备时指定操作某个设备  
* adb tcpip 5555           //以tcpip模式开启adb，端口为5555
* adb connect IP地址/IP地址:端口      //连接设备
* adb disconnect ip/ip:端口          //断开连接

查看当前应用包名/Activity：
* dumpsys window windows | grep mFocusedApp       //查看当前的app包名和activity -PS：在执行adb shell命令后再执行）
 （Linux/Mac系统下：adb shell dumpsys activity | grep "mFocusedActivity"）

* 另一种方式：
    获取appActivity：aapt dump badging xxxx.apk | find "launchable-activity"
    获取appPackage：aapt dump badging xxxx.apk | find "package: name="


列出包名：
* adb shell pm list package [-s/f]

    -s：列出系统应用
    
    -f：列出应用包名及对应的apk名及存放位置

上传与下载：
* adb push <本地文件> <远程路径>        //上传
* adb pull <远程路径> <本地路径>        //下载

安装与卸载：
* adb install [-r] xxx.apk           //-r：强制安装，最后一个参数时apk的全路径（文件位于当前主机端）
* adb shell pm install [-r] /data/local/tmp/xxx.apk    //安装的apk来源于设备中，例：data/local/tmp 目录
* adb uninstall [k] <PACKAGE>        //卸载  <PACHAGE>应用包名
* adb shell pm uninstall [-k] <PACKAGE>        //-k：卸载应用且保留数据与缓存，不加的话，则全部删除

截图和录制视频
* adb shell screencap -p /sdcard/test_screencap01.png
* adb shell screenrecord /sdcard/test_record01.mp4

日志log
* adb logcat/
* adb logcat -s tag         // 查看指定标签日志
* adb logcat -v time >D:\android_log.txt
       

#### 三、appium的安装 

    1.官网下载对应系统版本的appium：
     地址1：https://github.com/appium/appium-desktop/releases/
     地址2：http://appium.io/downloads.html
    2.双击执行.exe进行安装，设置都默认就好
    3.安装成功之后打开，设置默认就好，地址：127.0.0.1/0.0.0.0，端口：443
      
![](https://gitee.com/kolenj/BlogImages/raw/master/20200522125803.png)
      
#### 四、配置Capability，启动APP(也可以直接在代码中实现，二选一)

* 配置Capability

    操作路径：
     Start Server --> Start Inspector Session --> Automatic Server：Desired Capabilities
    
    一个打开qq的配置模板：
        {
          "platformName": "Android",    # 对应平台   
          "platformVersion": "9.0",     # 系统版本(查看手机)
          "deviceName": "see_adb_devices",   # 通过adb devices 命令查看设备名称
          "appPackage": "com.tencent.mobileqq",
          "appActivity": "com.tencent.mobileqq.activity.SplashActivity",
          "noReset": true   # 不要重置数据！！！
        }

<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200602000524.png"/>
</div>

---

* 代码demo：
       
        
    import time
    from appium import webdriver
    
    desired_caps = {
    
        # 基本信息：
        "platformName": "Android",  # 对应平台 Android/IOS
        "deviceName": "PhoneName",    # 设备名称
        "platformVersion": "9.0",   # 手机/模拟器的系统版本号(设置里可查看)
    
        # # 打开qq:
        "appPackage": "com.tencent.mobileqq",   # 应用的包名
        "appActivity": ".activity.SplashActivity",  # 打开应用的页面Activity
        "noReset": True  # 不要重置应用数据！！！
    }
    driver = webdriver.Remote("http://127.0.0.1:4723/wd/hub", desired_caps) 
    time.sleep(10)
    driver.quit()


<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200602001738.png"/>
</div>


#### 五、UIAutomatorViewer.bat 的使用

    1、在Android\sdk\tools\bin下打开uiautomatorviewer.bat运行，期间不要关闭其关联的cmd窗口
    2、进入到你想定位的页面，点击第二个图标按钮进行截图，进而定位分析元素等操作，如下图    
    
<div align="left">
        <img width="900" height="600" src="https://gitee.com/kolenj/BlogImages/raw/master/20200522132955.png"/>
</div>

