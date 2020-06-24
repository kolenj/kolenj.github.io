---
title: selenium
date: 2018-05-22 09:09:04
tags: 
- selenium

categories:
- 软件测试

---

##### 一、python+selenium自动化测试环境的搭建

* python的下载与安装

    * 1、根据自身需求下载相应的 [python](https://www.python.org/downloads/) 版本
    
    * 2、默认安装就行(勾选将python添加到系统环境中)，然后打开cmd，执行：python -V 显示python版本即表示安装成功
    
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200612002801.png)

---

* pycharm的下载与安装

    * 1、官方下载 [PyCharm](https://www.jetbrains.com/pycharm/download/#section=windows) 的社区版

    * 2、双击默认安装即可
    
    * 3、在设置中配置python的安装目录(Project Interpreter)
    
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200612003415.png)

---

* selenium两种常见安装方式

    * 1、在终端(cmd中)使用pip命令直接安装 (PS: pip是python包安装及管理工具)
        * pip install selenium
    
    * 2、在pycharm->file->Settings->Project（Interpreter） 下面点击"+" 搜索selenium 包进行安装
    
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200611235446.png)
      
    * 3、在项目中，如果能正确导入: from selenium import webdriver ，则表示selenium已安装好 

---

* 浏览器驱动的下载与安装
 
    * 1、下载浏览器驱动(PS:驱动的版本要与浏览器当前版本对应!!!)，比如 [chromedriver.exe](https://sites.google.com/a/chromium.org/chromedriver/downloads)
        
         ![](https://gitee.com/kolenj/BlogImages/raw/master/20200612000850.png)
        
    * 2、然后将其放到python安装目录的”Scripts“目录下
    
         ![](https://gitee.com/kolenj/BlogImages/raw/master/20200612001946.png)

---
        
* 测试环境是否搭建成功

    * 1、打开PyCharm，创建一个新项目
    * 2、新建一个helloworld.py文件，具体代码如下
    
        ![](https://gitee.com/kolenj/BlogImages/raw/master/20200612004445.png)
    
    * 3、如果能正常打开chrome浏览器并成功访问网站，则表示环境已全部搭建成功
       


##### 二、selenium常见需求

* 请求常见需求设置(加header)

```python
    
    # 获取浏览器设置(chrome) -from selenium.webdriver.chrome.options import Options
    chrome_options = Options()
    
    chrome_options.add_argument('--headless')  # 浏览器不提供可视化页面(即无头模式)
    chrome_options.add_argument('--user-agent=""')  # 设置请求头的User-Agent
    chrome_options.add_argument('--window-size=1280x1024')  # 设置浏览器窗口大小，（--start-maximized  # 全屏窗口）
    chrome_options.add_argument('--disable-infobars')  # 禁用浏览器正在被自动化程序控制的提示
    chrome_options.add_argument('--incognito')  # 隐身模式（无痕模式）
    chrome_options.add_argument('--hide-scrollbars')  # 隐藏滚动条
    chrome_options.add_argument('--disable-javascript')  # 禁用javascript
    chrome_options.add_argument('--blink-settings=imagesEnabled=false')  # 不加载图片, 提升速度


    # 添加cookie访问
    # chrome_options.add_argument('cookie=session-id=143-0027246-5158912')
    
    # 设置代理
    proxyIP = 'ip:port'
    chrome_options.add_argument('--proxy-server'+proxyIP)   #无用户名密码认证的代理

    driver = webdriver.Chrome(options=chrome_options)
```

* 元素等待(Implicit Waits)   
   
         driver.implicitly_wait(10) # seconds
 
         
* 元素等待(Explicit Waits)


```python
        from selenium import webdriver
        from selenium.webdriver.common.by import By
        from selenium.webdriver.support.ui import WebDriverWait
        from selenium.webdriver.support import expected_conditions as EC
        
        driver = webdriver.Firefox()
        driver.get("http://somedomain/url_that_delays_loading")
        try:
            element = WebDriverWait(driver, 10).until(
                EC.presence_of_element_located((By.ID, "myDynamicElement"))
            )
        finally:
            driver.quit()
```
       
* 元素等待(Custom Wait Conditions) 

```python
        class element_has_css_class(object):
          """An expectation for checking that an element has a particular css class.
        
          locator - used to find the element
          returns the WebElement once it has the particular css class
          """
          def __init__(self, locator, css_class):
            self.locator = locator
            self.css_class = css_class
        
          def __call__(self, driver):
            element = driver.find_element(*self.locator)   # Finding the referenced element
            if self.css_class in element.get_attribute("class"):
                return element
            else:
                return False
        
        # Wait until an element with id='myNewInput' has class 'myCSSClass'
        wait = WebDriverWait(driver, 10)
        element = wait.until(element_has_css_class((By.ID, 'myNewInput'), "myCSSClass"))
```

[官方文档](https://selenium-python.readthedocs.io/waits.html)


##### 三、selenium加载元素(Locating Elements)

* selenium 的8种加载元素方法(PS：多个元素则将element替换为elements)

    * find_element_by_id
    * find_element_by_nam
    * find_element_by_link_text
    * find_element_by_partial_link_text
    * find_element_by_tag_name
    * find_element_by_class_name
    
    * find_element_by_xpath
    * find_element_by_css_selector
    
* selenium 以私有方法方式加载元素
    
        from selenium.webdriver.common.by import By
    
        driver.find_element(By.XPATH, '//button[text()="Some text"]')
        driver.find_elements(By.XPATH, '//button')  # 多个元素

* 以"xpath" 方式加载元素的例子

     ![](https://gitee.com/kolenj/BlogImages/raw/master/20200612084558.png)

[官方参考文档](https://selenium-python.readthedocs.io/locating-elements.html#locating-elements)
[参考1](https://saucelabs.com/resources/articles/selenium-tips-css-selectors)
[参考2](https://www.cnblogs.com/zidonghua/p/7430083.html#_label3)


   
