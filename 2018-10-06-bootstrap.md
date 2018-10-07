---
layout:     post
title:     BootStrap 笔记
subtitle:   导航条
date:       2018-10-6
author:     IAKGnaHz
header-img: img/post-a.jpg
catalog: true
tags:
    - bootstrap
    - css
    
---

# 其他内置组件
### 缩略图
+ 。Bootstrap框架将这一部独立成一个模块组件。并通过“thumbnail”样式配合bootstrap的网格系统来实现。可以将产品列表页变得更好看。


```
//缩略图结构
<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="http://img.mukewang.com/5434eba100014fe906000338.png" style="height: 180px; width: 100%; display: block;" alt="">
            </a>
        </div>
    …
    </div>
</div>
```
 + 还可以让缩略图配合标题、描述内容，按钮
     + 在仅有缩略图的基础上，添加了一个div名为“caption“的容器，在这个容器中放置其他内容，比如说标题，文本描述，按钮等：
     
```
<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="http://a.hiphotos.baidu.com/image/w%3D400/sign=c56d7638b0b7d0a27bc9059dfbee760d/3b292df5e0fe9925d46873da36a85edf8cb171d7.jpg" style="height: 180px; width: 100%; display: block;" alt="">
            </a>
            <div class="caption">
                <h3>Bootstrap框架系列教程</h3>
                <p>Bootstrap框架是一个优秀的前端框，就算您是一位后端程序员或者你是一位不懂设计的前端人员，你也能依赖于Bootstrap制作做优美的网站...</p>
                <p>
                    <a href="##" class="btn btn-primary">开始学习</a>
                    <a href="##" class="btn btn-info">正在学习</a>
                </p>
            </div>
        </div>
    …
    </div>
</div>
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvzcs3cm63j308m0ewwht.jpg)

### 警示框