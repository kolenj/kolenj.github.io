---
title: selenium + python 自动化测试
date: 2017-03-25 09:09:04
tags: 
- selenium

categories:
- 软件测试

---

##### 一、python+selenium环境的搭建

      
      前提条件：手机(移动端设备)和PC处于同一局域网 
      
      如果手机端有”网络ADB调试“功能：
          1、在手机端打开“Android调试”、“网络ADB调试"即可通过adb命令远程连接
          2、adb connect 192.168.3.11(我手机端的ip)
          
      如果手机端没有”网络ADB调试“功能：
          1、通过usb将手机连接电脑，并开启Android调试和网络ADB调试（Android 9.0）
          2、测试是否连接成功：adb connect 设备ip地址（或者：ping 设备ip地址）
             （如果connect拒绝，用adb tcpip模式重启adb）
          3、adb devices 显示成功连接则表示调试环境已创建成功

##### 二、常用adb命令

      查看手机信息：
          adb shell ifconfig          //查看手机ip
          adb shell getprop ro.build.version.release        //查看系统版本
          (更多参考： https://www.cnblogs.com/zhuminghui/p/10472193.html )
      
      adb服务的开启与关闭：
          adb kill-server             //关闭adb服务
          adb start-server            //开启adb服务
        
      查看/无线调试-设备：
          adb devices              //显示连接设备
          adb -s 设备号 指令         //多个设备时指定操作某个设备
          
          adb tcpip 5555           //以tcpip模式开启adb，端口为5555
          adb connect IP地址/IP地址:端口      //连接设备
          adb disconnect ip/ip:端口          //断开连接
      
      查看当前应用/Activity：
          dumpsys window windows | grep mFocusedApp       //查看当前的app包名和activity -/执行adb shell命令后再执行）
         （Linux/Mac系统下：adb shell dumpsys activity | grep "mFocusedActivity"
      
      列出包名：
      adb shell pm list package [-s/f]
      -s：列出系统应用
      -f：列出应用包名及对应的apk名及存放位置
      
      上传与下载：
      adb push <本地文件> <远程路径>        //上传
      adb pull <远程路径> <本地路径>        //下载
      
      安装与卸载：
      adb install [-r] xxx.apk           //-r：强制安装，最后一个参数时apk的全路径（文件位于当前主机端）
      adb shell pm install [-r] /data/local/tmp/xxx.apk    //安装的apk来源于设备中，例：data/local/tmp 目录
      adb uninstall [k] <PACKAGE>        //卸载  <PACHAGE>应用包名
      adb shell pm uninstall [-k] <PACKAGE>        //-k：卸载应用且保留数据与缓存，不加的话，则全部删除
      
      截图和录制视频
      adb shell screencap -p /sdcard/test_screencap01.png
      adb shell screenrecord /sdcard/test_record01.mp4
 
      adb logcat/
      adb logcat -s tag         // 查看指定标签日志
      adb logcat -v time >D:\android_log.txt
       

##### 三、appium的安装 

      1、官网下载对应系统版本的appium：
         地址1：https://github.com/appium/appium-desktop/releases/
         地址2：http://appium.io/downloads.html
      2、双击执行.exe进行安装，设置都默认就好
      3、安装成功之后打开，设置默认就好，地址：127.0.0.1/0.0.0.0，端口：443
      
![](https://gitee.com/kolenj/BlogImages/raw/master/20200522125803.png)
      

##### 四、demo代码及常用API

###### demo
```python

    from appium import webdriver
    import time
    
    # 初始化信息,方式二：
    desired_caps = {
    
        # 基本信息：
        "platformName": "Android",  # 对应平台 Android/IOS
        "deviceName": "SAMSUNG",    # 设备名称
        "platformVersion": "6.0",   # 手机/模拟器的系统版本号(设置里可查看)
        
        # 避免输入的中文乱码：
        "unicodeKeyboard": True,
        "resetKeyboard": True,

        # 打开应用的信息：
        # (windows系统获取app相关信息：cmd下执行 1、 adb shell 2、dumpsys window windows | grep mFocusedApp  即可查看到当前打开的app包名和activity)
    
        # 不同版本包名和active可能不一样

        # 打开设置：
        # "appPackage": "com.android.setting",   # 应用的包名
        # "appActivity": ".Settings",  # 打开应用的页面Activity
    
        # 打开自带浏览器：
        # "appPackage": "com.android.browser",   # 应用的包名
        # "appActivity": ".BrowserActivity",  # 打开应用的页面Activity
    
        # 打开qq
        "appPackage": "com.tencent.mobileqq",   # 应用的包名
        "appActivity": ".activity.SplashActivity",  # 打开应用的页面Activity
        "noReset": True  # 不要重置应用数据！！！
    }
    
    driver = webdriver.Remote("http://127.0.0.1:4723/wd/hub", desired_caps)
    time.sleep(10)
    driver.quit()

```
###### 常用API
```python

    # 根据应用包名和activity打开应用：
    # driver.start_activity("com.android.messaging", ".ui.conversationlist.ConversationListActivity")
    # time.sleep(5)
    
    # 代码获取当前包名和界面activity：
    # print("当前应用包名："+driver.current_package)
    # print("当前应用界面的activity："+driver.current_activity)
    
    # app应用的安装与卸载
    # if driver.is_app_installed("com.android.music"):    # 判断应用是否已安装，这里以“com.android.music”为例
    #     print("com.android.music has installed")
    #     # 卸载应用(根据包名)
    #     driver.remove_app("com.android.music")
    # else:
    #     # 安装应用(apk的路径)
    #     driver.install_app("")
    #     print("已执行安装")
    
    # 将应用置于后台运行，单位时间为秒
    # driver.background_app(2)
    
    # 元素等待方式1：
    driver.implicitly_wait(10)  # 全局元素都设置为等待10s之内
    
    # 元素等待方式2：(对不同元素分别设置)
    element = WebDriverWait(driver, 10, poll_frequency=1).until(
            EC.presence_of_element_located((By.ID, 'prodDetails'))
        )
    
    # 元素的常用操作方法：click()/点击,  send_keys("xxx")/输入发送内容,  clear()/清空内容，  get_attribute("xxx")/获取元素对应属性
    # location()/获取元素起始xy坐标,  size()/获取元素的高和宽
    
    # 获取手机分辨率
    print(driver.get_window_size())
    
    # 保存截图
    driver.get_screenshot_as_file("example.png")
    
    # 获取当前手机网络信息
    print(driver.network_connection)
    
    # 设置手机网络
    driver.set_network_connection(1)    # 数字代表详情进入方法里进行查看
    
    # 打开通知栏
    driver.open_notifications()
    
    time.sleep(5)
    
    # 发送按键
    driver.press_keycode(4)  # 4对应返回
    
    # driver的close_app()与quit()方法的区别
    # driver.close_app()  # 只是关闭当前操作的app
    # driver.quit()   # 直接关闭驱动对象，同时也关闭了所有关联的app    
```



##### 四、UIAutomatorViewer.bat 的使用

    1、在Android\sdk\tools\bin下打开uiautomatorviewer.bat运行，期间不要关闭其关联的cmd窗口
    2、进入到你想定位的页面，点击第二个图标按钮进行截图，进而定位分析元素等操作，如下图
![](https://gitee.com/kolenj/BlogImages/raw/master/20200522132955.png)
      

          
   