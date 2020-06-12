---
title: Markdown常用语法
date: 2017-06-23 09:29:22
tags: 
- markdown

categories:
- others

---

## Markdown常用语法总结

**=====================效果=======================**

**================================================**
#### -标题

###标题3号
#####标题5号
######标题6号


#### -列表
    
有序列表

1.列表

2.列表

无序列表（可以是"-或*"加空格）
* 列表
    * 二级列表（一个tab）
    * 二级列表
        * 三级列表（两个tab）
        * 三级列表
- 列表
    - 二级列表


#### -引用块

>数据结构  
>>树  
>>>二叉树  
>>>>平衡二叉树  
>>>>>满二叉树


#### -强调/加粗，斜体

**粗体**

*斜体*  


#### -超链接

行内式：

[baidu](https://www.cnblogs.com/zhuminghui/p/10472193.html '标题/可选')

引用式： [GitHub][2]

自动连接：https://www.google.com // <example@gmail.com>

[2]: https://github.com/kolenj "我的 GitHub 主页"


#### -图片引用

![markDown使用截图](https://gitee.com/kolenj/BlogImages/raw/master/20200529211458.png)

* 设定图片显示的大小
<div align="center">
    <img width="600" height="300" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529211458.png"/>
</div>


#### 水平分割线（在一单独空白行使用三个或以上 */- 即来实现一条水平分割线）

---
***


#### 代码块

//1.行内代码
 
`var a= 1;`

//2.代码块

    ``` -begin-
         void daima(){
            printf("hello world!");
         }
    ``` -end-


#### LaTex公式

$ y = x+1 $; // 行内公式

$$ a^2 + b^2 = c^ $$; // 整行公式


#### 表格
    
|Item    |        Value|    Qty|
|:--------|---------:|:---:|
|Computer |     1600 USD|      5|
|Computer |     1. one<br />2. two<br />|      5|


#### 任务列表

- [x] 洗碗
- [ ] 拖地
- [x] 打酱油

#### 删除线

后面三个字打上~~删除线~~
    

#### emoji(没起作用)

:camel: 

:blush: 

:smile:

我和我的小伙伴们惊呆了 :smile:


#### 行首缩进
    
    &ensp;/&emsp;分别代表半角空格和全角空格(PS: 要带上";"号)

---
---
**====================原始文本=====================**
#### -标题

    ###标题3号
    #####标题5号
    ######标题6号


#### -列表
    
    有序列表
    
    1.列表
    
    2.列表
    
    无序列表（可以是"-或*"加空格）
    * 列表
        * 二级列表（一个tab）
        * 二级列表
            * 三级列表（两个tab）
            * 三级列表
    - 列表
        - 二级列表


#### -引用块

    >数据结构  
    >>树  
    >>>二叉树  
    >>>>平衡二叉树  
    >>>>>满二叉树
    > #### 引用块内的标题
    

#### -强调/加粗，斜体

    **粗体**
    
    *斜体*  


#### -超链接

    行内式：
    
    [baidu](http://www.baidu.com '标题/可选')   # 是单引号'!!
    
    引用式： [GitHub][2]
    
    自动连接：https://www.google.com // <example@gmail.com>
    
    [2]: https://github.com/kolenj "我的 GitHub 主页"


#### -图片引用

    ![markDown使用截图](https://gitee.com/kolenj/BlogImages/raw/master/20200529211458.png)
    
    * 设定图片显示的大小
    <div align="left">
        <img width="800" height="500" src="https://gitee.com/kolenj/BlogImages/raw/master/20200529211458.png"/>
    </div>


#### 水平分割线（在一单独空白行使用三个或以上 */- 即来实现一条水平分割线）

    ---
    ***


#### 代码块

    //1.行内代码
     
    `var a= 1;`
    
    //2.代码块
    
        ``` -begin-
            void daima(){
                printf("hello world!");
            }
        ``` -end-
    

#### LaTex公式

    $ y = x+1 $; // 行内公式
    
    $$ a^2 + b^2 = c^ $$; // 整行公式
    

#### 表格
    
    |Item    |        Value|    Qty|
    |:--------|---------:|:---:|
    |Computer |     1600 USD|      5|
    |Computer |     1. one<br />2. two<br />|      5|
    

#### 任务列表

    - [x] 洗碗
    - [ ] 拖地
    - [x] 打酱油

#### 删除线

    后面三个字打上~~删除线~~
    

#### emoji

    :camel: 
    
    :blush: 
    
    :smile:
    
    我和我的小伙伴们惊呆了 :smile:


#### 行首缩进
    
    &ensp; / &emsp; -分别代表半角空格和全角空格(PS: 要带上";"号)
        

[参考](https://mazhuang.org/2018/09/06/markdown-intro)