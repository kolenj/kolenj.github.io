---
title: 使用七牛和picGO设置免费图床
date: 2018-03-25 19:09:04
tags: 
- 图床

categories:
- 建站

---

### 如何用七牛和picGO设置免费图床 


#### 一、七牛注册设置

**1、注册认证：(个人/企业)，下面是否个人版，一般博客之类是够用了**

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200421113913.png)


**2、新建图床：进入产品主页，点击添加“对象存储”**

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200421114735.png)


**3、图床设置：命名存储空间名称，就近选择存储服务器，访问控制设置为公开**

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200421115311.png)


**4、上传图片：选择存储空间，进入“文件管理”，进行图片文件上传**

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200421115849.png)


**5、复制外链：上传完成后，复制外链，就可以在markdown的网站文本中使用了**

![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200421120245.png)




#### 二、pigGO配置

1、下载安装之后进行配置：其中accesskey、secretkey到七牛个人面板“密钥管理”里找，存储空间名称，访问地址(空间域名)一一对应,

确认存储区域的对应编码为：华东 z0, 华北 z1，华南 z2，北美 na0，东南亚 as0

最后的存储路径是方便归类
![](http://q92hyc32h.bkt.clouddn.com/blog_picgo/20200421120621.png)

2、picGO剪贴板图片快捷键设置，方便上传图片，提高工作效率，我自己这里设置为Ctrl+Shift+U


#### 三、压缩图片

1、在图片上传之前，可以先把图片压缩，不仅可以节省存储空间，还可以加快图片的加载速度