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

# 导航条
+ 在导航条(navbar)中有一个背景色、而且导航条可以是纯链接（类似导航），也可以是表单，还有就是表单和导航一起结合等多种形式。
+ LESS版本：对应的源文件navbar.less
+ Sass版本：对应的源文件_navbar.scss

### 基础导航条
+ 第一步：首先在制作导航的列表(<ul class=”nav”>)基础上添加类名“navbar-nav”
+ 第二步：在列表外部添加一个容器（div），并且使用类名“navbar”和“navbar-default”
    + .navbar”样式的主要功能就是设置左右padding和圆角等效果，但他和颜色相关的样式没有进行任何的设置。
    + 而导航条的颜色都是通过“.navbar-default”来进行控制
    
```
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
```

```
<div class="navbar navbar-default" role="navigation">
     <ul class="nav navbar-nav">
	 	<li class="active"><a href="##">网站首页</a></li>
        <li><a href="##">系列教程</a></li>
        <li><a href="##">名师介绍</a></li>
        <li><a href="##">成功案例</a></li>
        <li><a href="##">关于我们</a></li>
	 </ul>
</div>
```

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvyq7hm24tj30ew038mxe.jpg)

### 为导航条添加标题、二级菜单及状态
##### 加入导航条标题
+ 通过“navbar-header”和“navbar-brand”来实现
+ 此功能主要起一个提醒功能，当然改良一下可以当作是logo(此处不做过多阐述)。其样式主要是加大了字体设置，并且设置了最大宽度：

```
.navbar-brand {
float: left;
height: 50px;
padding: 15px 15px;
font-size: 18px;
line-height: 20px;
}
.navbar-brand:hover,
.navbar-brand:focus {
text-decoration: none;
}
@media (min-width: 768px) {
.navbar> .container .navbar-brand,
.navbar> .container-fluid .navbar-brand {
margin-left: -15px;
}
}
```
##### 导航条状态、二级菜单
+ 同样的，在基础导航条中对菜单提供了当前状态，禁用状态，悬浮状态等效果，而且也可以带有二级菜单的导航条

*二级菜单代码*
```
<div class="navbar navbar-default" role="navigation">
  　<div class="navbar-header">
  　    <a href="##" class="navbar-brand">慕课网</a>
  　</div>
	<ul class="nav navbar-nav">
	 	<li class="active"><a href="##">网站首页</a></li>
        <li class="dropdown">
          <a href="##" data-toggle="dropdown" class="dropdown-toggle">系列教程<span class="caret"></span></a>
          <ul class="dropdown-menu">
        	<li><a href="##">CSS3</a></li>
        	<li><a href="##">JavaScript</a></li>
        	<li class="disabled"><a href="##">PHP</a></li>
          </ul>
       </li>
       <li><a href="##">名师介绍</a></li>
       <li><a href="##">成功案例</a></li>
       <li><a href="##">关于我们</a></li>
	</ul>
</div>
```

*二级菜单效果*

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvyqbg3700j30iw065jrw.jpg)

### 带表单的导航条
在Bootstrap框架中提供了一个“navbar-form”，使用方法很简单，在navbar容器中放置一个带有navbar-form类名的表单


```
<form action="##" class="navbar-form navbar-left" rol="search">
   	    <div class="form-group">
   		   <input type="text" class="form-control" placeholder="请输入关键词" />
   	    </div>
        <button type="submit" class="btn btn-default">搜索</button>
     </form>
```

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvyqcz0xejj30pd03mmxm.jpg)

### 导航条中的按钮、文本和链接
+ 导航条中的按钮navbar-btn
+ 导航条中的文本navbar-text
+ 导航条中的普通链接navbar-link

**但这三种样式在框架中使用时受到一定的限制，需要和navbar-brand、navbar-nav配合起来使用。而且对数量也有一定的限制，一般情况在使用一到两个不会有问题，超过两个就会有问题**

### 固定导航条
+ 很多情况之一，设计师希望导航条固定在浏览器顶部或底部，这种固定式导航条的应用在移动端开发中更为常见。Bootstrap框架提供了两种固定导航条的方式：
    +  .navbar-fixed-top：导航条固定在浏览器窗口顶部
    +  .navbar-fixed-bottom：导航条固定在浏览器窗口底部
+ 实现原理很简单，就是在navbar-fixed-top和navbar-fixed-bottom使用了position：fixed属性，并且设置navbar-fixed-top的top值为0,而navbar-fixed-bottom的bottom值为0。

### 响应式导航条

```
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>响应式导航条</title>
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
<style type="text/css">
    body{padding:50px 0 0 0;}
</style>
</head>

<body>
<!--代码-->
<div class="navbar navbar-default" role="navigation">
  <div class="navbar-header">
     　<!-- .navbar-toggle样式用于toggle收缩的内容，即nav-collapse collapse样式所在元素 -->
       <button class="navbar-toggle" type="button" data-toggle="collapse" data-target=".navbar-responsive-collapse">
         <span class="sr-only">Toggle Navigation</span>
         <span class="icon-bar"></span>
         <span class="icon-bar"></span>
         <span class="icon-bar"></span>
       </button>
       <!-- 确保无论是宽屏还是窄屏，navbar-brand都显示 -->
       <a href="##" class="navbar-brand">慕课网</a>
  </div>
  <!-- 屏幕宽度小于768px时，div.navbar-responsive-collapse容器里的内容都会隐藏，显示icon-bar图标，当点击icon-bar图标时，再展开。屏幕大于768px时，默认显示。 -->
  <div class="collapse navbar-collapse navbar-responsive-collapse">
    	<ul class="nav navbar-nav">
      		<li class="active"><a href="##">网站首页</a></li>
      		<li><a href="##">系列教程</a></li>
      		<li><a href="##">名师介绍</a></li>
      		<li><a href="##">成功案例</a></li>
      		<li><a href="##">关于我们</a></li>
	 	</ul>
  </div>
</div>

<script src="https://www.imooc.com/static/lib/jquery/1.9.1/jquery.js"></script>
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script> 

</body>
</html>
```

+ 保证在窄屏时需要折叠的内容必须包裹在带一个div内，并且为这个div加入collapse、navbar-collapse两个类名。最后为这个div添加一个class类名或者id名。
+ 保证在窄屏时要显示的图标样式（固定写法）

```
<button class="navbar-toggle" type="button" data-toggle="collapse">
  <span class="sr-only">Toggle Navigation</span>
  <span class="icon-bar"></span>
  <span class="icon-bar"></span>
  <span class="icon-bar"></span>
</button>
```
+ 并为button添加data-target=".类名/#id名"，究竞是类名还是id名呢？由需要折叠的div来决定。

```
<div class="collapse navbar-collapse" id="example">
      <ul class="nav navbar-nav">
      …
      </ul>
</div>
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvyqr22nnej30by09h3yw.jpg)

### 反色导航条
+ 反色导航条其实是Bootstrap框架为大家提供的第二种风格的导航条
+ 与默认的导航条相比，使用方法并无区别，只是将navbar-deafult类名换成navbar-inverse。
+ 其变化只是导航条的背景色和文本做了修改。

```
<div class="navbar  navbar-inverse" role="navigation">
<div class="nav bar-header">
      <a href="##" class="navbar-brand">慕课网</a>
</div>
<ul class="nav navbar-nav">
      <li class="active"><a href="">首页</a></li>
      <li><a href="">教程</a></li>
      <li><a href="">关于我们</a></li>
</ul>
</div>
```

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvyqwpujpoj30lr037q33.jpg)

### 分页导航（带页码的分页导航）
+ 在Bootstrap框架中提供了两种分页导航：
    + 带页码的分页导航
    + 带翻页的分页导航
    + LESS版本：对应的源文件pagination.less
    + Sass版本：对应的源文件_pagination.scss
    + 在Bootstrap框架中使用的是ul>li>a这样的结构，在ul标签上加入`pagination`方法
    
```
<ul class="pagination">
   <li><a href="#">&laquo;</a></li>
   <li><a href="#">1</a></li>
   <li><a href="#">2</a></li>
   <li><a href="#">3</a></li>
   <li><a href="#">4</a></li>
   <li><a href="#">5</a></li>
   <li><a href="#">&raquo;</a></li>
</ul>
```

**大小设置**

+ 通过“pagination-lg”让分页导航变大；
+ 通过“pagination-sm”让分页导航变小：

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvyr4u0h3yj30r305ewey.jpg)

### 分页导航（翻页分页导航）
+ 这种分页导航是看不到具体的页码，只会提供一个“上一页”和“下一页”的按钮。
    + Bootstrap框架将其独立成一个单独的部分：
    + LESS版本：对应源文件为pager.less
    + Sass版本：对应源文件为_pager.scss
+ 在实际使用中，翻页分页导航和带页码的分页导航类似，为ul标签加入`pager`类

```
<ul class="pager">
   <li><a href="#">&laquo;上一页</a></li>
   <li><a href="#">下一页&raquo;</a></li>
</ul>
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvyr700w8nj30a302v0sq.jpg)

+ 和带页码分页导航一样，如果在li标签上添加了disabled类名的时候，分页按钮处于禁用状态，但同样不能禁止其点击功能。你可以通过js来处理，或将a标签换成span标签。

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvyr86hh7hj30da02vq31.jpg)

### 标签
+ 那么在Bootstrap框架中特意将这样的效果提取出来成为一个标签组件，并且以`.label`样式来实现高亮显示。
    +  LESS版本：对应的源文件label.less
    +  Sass版本：对应的源文件_label.scss
    +  编译后版本：bootstrap.css文件第4261行～第4327行

```
<h3>Example heading <span class="label label-default">New</span></h3>
```

**颜色设置**
+ label-deafult:默认标签，深灰色
+ label-primary：主要标签，深蓝色
+ label-success：成功标签，绿色
+ label-info：信息标签，浅蓝色
+ label-warning：警告标签，橙色
+ label-danger：错误标签，红色


```
<span class="label label-default">默认标签</span>
<span class="label label-primary">主要标签</span>
<span class="label label-success">成功标签</span>
<span class="label label-info">信息标签</span>
<span class="label label-warning">警告标签</span>
<span class="label label-danger">错误标签</span>
```

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvyrbafsfrj30en03vmxk.jpg)

### 徽章
+ 从某种意义上来说，徽章效果和前面介绍的标签效果是极其的相似。也是用来做一些提示信息使用。
+ 常出现的是一些系统发出的信息，比如你登录你的twitter后，如果你信息没有看，系统会告诉你有多少信息未读
+ 使用span标签来制作，然后为他加入badge类

```
<a href="#">Inbox <span class="badge">42</span></a>
```

```
<ul class="nav nav-pills">
  <li class="active"><a href="#">Home <span class="badge">42</span></a></li>
  <li><a href="#">Profile</a></li>
  <li><a href="#">Messages <span class="badge">3</span></a></li>
</ul>
<br /> 
<ul class="nav nav-pills nav-stacked" style="max-width: 260px;">
      <li class="active">
        <a href="#">
          <span class="badge pull-right">42</span>
          Home
        </a>
      </li>
      <li><a href="#">Profile</a></li>
      <li>
        <a href="#">
          <span class="badge pull-right">3</span>
          Messages
        </a>
      </li>
</ul>
<br />
<!--按钮勋章-->
<button class="btn btn-primary" type="button">
      Messages <span class="badge">4</span>
</button> 
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvyrjf9ifnj30de08fjrr.jpg)

<br>
<br>
   
<em>The End</em>
<br>
<em>From IAKGnaHz</em>
<br>
<em>2018-10-6</em>

<hr>