---
title: appium的常用api与测试用例Demo
date: 2018-03-25 09:09:04
tags: 
- appium

categories:
- 软件测试

---

#### 一、元素常用api/属性
    
* appium查找元素的几种方式：

      driver.find_element(s)_by_id("xxx)
      driver.find_element(s)_by_xpath("xxx")
      driver.find_element(s)_by_class_name("xxx")
      ...
      
[Selenium查找元素方法总结](http://...)
      
![](https://gitee.com/kolenj/BlogImages/raw/master/20200601160040.png)  

* 元素常用方法：
    
    element.click()                 #点击
    element.clear()                 #清除文本
    element.send_keys("xxx")        #发送文本
    element.submit()                #提交
    
    element.get_attribute('xxx)     #获取属性对应值
    element.get_property()          #获取全部属性 
    
    element.is_displayed()          #是否显示
    element.is_enabled()            #是否可用
    element.is_selected()           #是否选中
    
    
* 元素常用属性：
    
    element.location                # 元素起始xy坐标
    element.size                    # 元素的高和宽
    element.id                      # 元素id
    element.text                    # 元素文本
    element.rect     #A dictionary with the size and location of the element.
    element.parent                  # 元素父类
    element.tag_name                # 元素的标签名
 

* 等待元素：
    
    # 元素等待方式1：(强制等待)
    time.sleep(5)
    # 元素等待方式2：
    driver.implicitly_wait(10)  # 全局元素都设置为等待10s之内
    # 元素等待方式3：(对不同元素分别设置)
    element = WebDriverWait(driver, 10, poll_frequency=1).until(
            EC.presence_of_element_located((By.ID, 'prodDetails'))
        )
    (PS:By的引用 - from selenium.webdriver.common.by import By)


* driver常用方法

    # 获取手机分辨率
    driver.get_window_size()
    
    # 保存截图
    driver.get_screenshot_as_file("example.png")
    
    # 获取当前手机网络信息
    driver.network_connection
    
    # 设置手机网络
    driver.set_network_connection(1)    # 数字所代表的详情信息进入方法里自行查看
    
    # 打开通知栏
    driver.open_notifications()
    
    # 将应用置于后台运行，单位时间为秒
    driver.background_app(2)
    
    # 发送按键
    driver.press_keycode(4)  # 常用按键：3-Home,4-返回，84-search，66-回车
 
 
* 滑动&拖拽事件：
     
    * swipe(操作坐标)
    
        driver.swipe(起始x坐标，起始y坐标，结束x坐标，结束y坐标, 持续时间/ms)      #持续时间越短，惯性越大
      
    * scroll & drag_and_drop(操作元素)
    
       element1 = driver.find_element_by_id("xxx")
       element2 = driver.find_element_by_id("xxx")
       
       driver.scroll(element1, element2)            # 有惯性
       driver.drag_and_drop(element1, element2)     # 无惯性


* TouchAction:
    
    * tap(轻敲，相当于click)
        touchAction = TouchAction(driver)     # from appium.webdriver.common.touch_action import TouchAction
        touchAction = touchAction.tap(element)
        touchAction.perform()
        (简写：TouchAction(driver).tap(element).perform() )
        
        PS: def tap(self, element=None, x=None, y=None, count=1)
    
    * press&release(按下&抬起)
        TouchAction(driver).press(x=xxx, y=yyy).perform()                          # 按下(自动弹起)
        TouchAction(driver).press(x=xxx, y=yyy).release().perform()                # release() 抬起
        TouchAction(driver).press(x=xxx, y=yyy).wait(2000).release().perform()     # wait() 相当于长按
        
    * long_press(长按)
        TouchAction(driver).long_press(x=xxx, y=yyy, duration=2000).perform()      # 参数可以是坐标/element，自动松手，没有release()
        
    * move_to(移动/手势拖拽)       
        TouchAction(driver).press(x=xxx, y=yyy).move_to(x=xxx, y=yyy).move_to...release().perform()     # 移动，见图案解锁屏幕功能
        

* 截屏： 
    
    ts = time.strftime("%Y_%m_%d_%H_%M_%S)
    activityName = driver.current_activity
    fileName = activityName + ts
    driver.save_screenshot("source/_posts/stest/"+fileName+".png")
          

* 录屏：
    driver.start_recording_screen()     # 开始录屏
    ...
    ...
    videoRawData = driver.stop_recording_screen()       # 开始录屏
    videoName = driver.current_activity + time.strftime("%Y_%m_%d_%H_%M_%S)
    filePath = os.path.join("source/_posts/stest/", videoName+".mp4")
    with open(filePath, "wd") as wd:
        wd.write(base64.b64decode(videoRawData))
       
* 执行脚本：

      driver.execute_scripts('mobile:performEditorAction', {'action':'search'})
      常用action：go, search, send, next, done, previous
      
      (Tips:操作弹出窗口可以使用driver.set_value(element, "操作按钮的文本/如：'CONFIRM' "))

       
#### 二、demo

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

        # 1、打开设置：
        # "appPackage": "com.android.setting",   # 应用的包名
        # "appActivity": ".Settings",  # 打开应用的页面Activity
    
        # 2、打开自带浏览器：
        # "appPackage": "com.android.browser",   # 应用的包名
        # "appActivity": ".BrowserActivity",  # 打开应用的页面Activity
    
        # 3、打开qq(最新版)
        "appPackage": "com.tencent.mobileqq",   # 应用的包名
        "appActivity": ".activity.SplashActivity",  # 打开应用的页面Activity
        "noReset": True  # 不要重置应用数据！！！
    }
    
    driver = webdriver.Remote("http://127.0.0.1:4723/wd/hub", desired_caps)
    driver.implicitly_wait(30)
    
    # 4、代码获取当前包名和界面activity：
    # print("当前应用包名："+driver.current_package)
    # print("当前应用界面的activity："+driver.current_activity)
    
    # 5、根据应用包名和activity打开应用：
    # driver.start_activity("com.android.messaging", ".ui.conversationlist.ConversationListActivity")
    # time.sleep(5)
    
    # 6、app应用的安装与卸载
    # if driver.is_app_installed("com.android.music"):    # 判断应用是否已安装，这里以“com.android.music”为例
    #     print("com.android.music has installed")
    #     # 卸载应用(根据包名)
    #     driver.remove_app("com.android.music")
    # else:
    #     # 安装应用(apk的路径)
    #     driver.install_app("")
    #     print("已执行安装")
    
    # 7、断言
    name = driver.find_element_by_id("xxx").get_attribute('text')
    assert name = “xxx", '断言结果描述说明(name=xxx)..."
    
    # driver.close_app()  # 只是关闭当前操作的app
    driver.quit()   # 直接关闭驱动对象，同时也关闭了所有关联的app
    


          
   