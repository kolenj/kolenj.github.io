---
title: appium自动化测试
date: 2018-03-15 09:09:04
tags: 
- 软件工具
- 环境搭建

categories:
- 软件测试

---

##### 一、创建wifi无线调试环境

      1、让手机和PC处于同一个WIFI网络环境
      2、通过usb将手机连接电脑，并开启Android调试和网络ADB调试（Android 9.0）
      3、测试是否连接成功：adb connect 设备ip地址（或者：ping 设备ip地址）
         （如果connect拒绝，用adb tcpip模式重启adb）
      4、adb devices 显示成功连接则表示环境已创建成功

##### 二、常用命令及注意点

      1、adb devices  （显示连接设备
      2、adb connect IP地址/IP地址:端口（ping IP地址  （测试是否连接成功
      3、adb tcpip 5555 （以tcpip模式重启adb，端口为5555
      4、dumpsys window windows | grep mFocusedApp （显示当前的app包名和activity -/在shell下执行）
      5、
      
      tips：
      1、如果提示：grep 提示“不是内部或外部命令”，则先进入adb shell ，再执行命令

##### 三、代码demo

      from appium import webdriver
      import time

      #初始化信息
      desired_caps=dict()
      desired_caps["platformName"]="Android"
      desired_caps["platformVersion"]="9.0"  
      desired_caps["deviceName"]="HuaWeiP30"
      
      # 打开设置
      desired_caps["appPackage"]="com.android.setting"
      desired_caps["appActivity"]=".Settings"

      driver = webdirver.Remote("http://127.0.0.1:4723/wd/hub",desired_caps)
      time.sleep(5)
      driver.quit()


##### 四、结合UI Automator Viewer.bat 进行自动化测试
    1、在Android\sdk\tools\bin下打开uiautomatorviewer.bat运行
      

          
   