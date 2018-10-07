---
layout:     post
title:     BootStrap 笔记
subtitle:   按钮 导航
date:       2018-10-5
author:     IAKGnaHz
header-img: img/post-a.jpg
catalog: true
tags:****
    - bootstrap
    - css
    
---
# 按钮
按钮组和下拉菜单组件一样，需要依赖于button.js插件才能正常运行。不过我们同样可以直接只调用bootstrap.js文件。因为这个文件已集成了button.js插件功能。

<em>使用一个名为“btn-group”的容器，把多个按钮放到这个容器中。</em>

```
<div class="btn-group">
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-step-backward"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-fast-backward"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-backward"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-play"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-pause"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-stop"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-forward "></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-fast-forward"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-step-forward"></span></button>
</div>
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvx4qtxn5rj30dh03e0sq.jpg)

除了可以使用`<button>`元素之外，还可以使用其他标签元素，比如`<a>`标签。**唯一要保证的是：不管使用什么标签，“.btn-group”容器里的标签元素需要带有类名“.btn”。**

##### 按钮工具栏

+ 在富文本编辑器中，将按钮组分组排列在一起，比如说复制、剪切和粘贴一组；左对齐、中间对齐、右对齐和两端对齐一组
    + 那么Bootstrap框架按钮工具栏也提供了这样的制作方法，你只需要将按钮组“btn-group”按组放在一个大的容器“btn-toolbar”中。
    + 实现原理主要是让容器的多个分组“btn-group”元素进行浮动，并且组与组之前保持5px的左外距。
        + 注意在”btn-toolbar”上清除浮动。
    
```
<div class="btn-toolbar">
  <div class="btn-group">
    …
  </div>
  <div class="btn-group">
    …
  </div>
  <div class="btn-group">
    …
  </div>
  <div class="btn-group">
    …
  </div>
</div>
```

<em>清除浮动</em>

```
.btn-toolbar:before,
.btn-toolbar:after｛
　display: table;
content: " ";
｝
.btn-toolbar:after{
  clear: both;
}
```

##### 按钮大小设置
+ .btn-group-lg:大按钮组
+ .btn-group-sm:小按钮组
+ .btn-group-xs:超小按钮组
+ 只需要在“.btn-group”类名上追加对应的类名，就可以得到不同大小的按钮组。

```
<div class="btn-toolbar">
  <div class="btn-group btn-group-lg">
    …
  </div>
  <div class="btn-group">
    …
  </div>
  <div class="btn-group btn-group-sm">
    …
  </div>
  <div class="btn-group btn-group-xs">
   …
  </div>
</div>
```

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvx52s5a0zj30hi062aag.jpg)

##### 嵌套分组
使用的时候，只需要把当初制作下拉菜单的“dropdown”的容器换成“btn-group”，并且和普通的按钮放在同一级。

```
<div class="btn-group">
<button class="btnbtn-default" type="button">首页</button>
<button class="btnbtn-default" type="button">产品展示</button>
<button class="btnbtn-default" type="button">案例分析</button>
<button class="btnbtn-default" type="button">联系我们</button>
<div class="btn-group">
   <button class="btnbtn-default dropdown-toggle" data-toggle="dropdown" type="button">关于我们<span class="caret"></span></button>
   <ul class="dropdown-menu">
         <li><a href="##">公司简介</a></li>
         <li><a href="##">企业文化</a></li>
         <li><a href="##">组织结构</a></li>
         <li><a href="##">客服服务</a></li>
    </ul>
</div>
</div>
```

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvx5ae3nhxj30gp06rjrx.jpg)

##### 按钮 垂直分布
**我们只需要把水平分组的“btn-group”类名换成“btn-group-vertical”即可。**

```
<div class="btn-group-vertical">
<button class="btnbtn-default" type="button">首页</button>
<button class="btnbtn-default" type="button">产品展示</button>
<button class="btnbtn-default" type="button">案例分析</button>
<button class="btnbtn-default" type="button">联系我们</button>
<div class="btn-group">
   <button class="btnbtn-default dropdown-toggle" data-toggle="dropdown" type="button">关于我们<span class="caret"></span></button>
   <ul class="dropdown-menu">
      <li><a href="##">公司简介</a></li>
      <li><a href="##">企业文化</a></li>
      <li><a href="##">组织结构</a></li>
      <li><a href="##">客服服务</a></li>
</ul>
</div>
</div>
```
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvx5h4sx0yj30fo09zmxr.jpg)

+ 和水平分组按钮不一样的是：
    + 平分组按钮第一个按钮左上角和左下角具有圆角以及最后一个按钮右上角和右下角具有圆角
    + 垂直分组按钮第一个按钮左上角和右上角具有圆角以及最后一个按钮左下角和右下角具有圆角
    
##### 按钮（等分按钮）

+ 等分按钮的效果在移动端上特别的实用。整个按钮组宽度是容器的100%，而按钮组里面的每个按钮平分整个容器宽度。
    + 如果你按钮组里面有五个按钮，那么每个按钮是20%的宽度，
    + 如果有四个按钮，那么每个按钮是25%宽度，以此类推。
+ 等分按钮也常被称为是自适应分组按钮，其实现方法也非常的简单，只需要在按钮组“btn-group”上追加一个“btn-group-justified”类名


```
<div class="btn-wrap">
<div class="btn-group btn-group-justified">
  <a class="btnbtn-default" href="#">首页</a>
  <a class="btnbtn-default" href="#">产品展示</a>
  <a class="btnbtn-default" href="#">案例分析</a>
  <a class="btnbtn-default" href="#">联系我们</a>
</div>
</div>
```

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvx5laho2yj30pw02sjrk.jpg)

<em>特别声明：在制作等分按钮组时，请尽量使用`<a>`标签元素来制作按钮，因为使用`<button>`标签元素时，使用display:table在部分浏览器下支持并不友好。</em>

##### 菜单下拉按钮
按钮下拉菜单仅从外观上看和上一节介绍的下拉菜单效果基本上是一样的。不同的是在普通的下拉菜单的基础上`封装了按钮`（.btn）样式效果。简单点说就是**点击一个按钮，会显示隐藏的下拉菜单**

按钮下拉菜单就是普通的下拉菜单，只不过把`<a>`标签元素换成了`<button>`标签元素。唯一不同的是外部器容“div.dropdown”换成了“div.btn-group”

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvx5rdll1fj30b506674h.jpg)

##### 按钮的向下向上三角形
按钮的向下三角形，我们是通过在`<button>`标签中添加一个`<span>`标签元素，并且命名为“caret”:


```
<button class="btn btn-default dropdown-toggle" data-toggle="dropdown" type="button">按钮下拉菜单<span class="caret"></span></button>
```

**这个三角形完全是通过CSS代码实现的**

```
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px solid;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
```

+ 三角形向上弹起
    + 需要在“.btn-group”类上追加“dropup”类名
    
  <em>css源码<br>
  向上三角与向下三角的区别：其实就是改变了一个border-bottom的值</em>
    
```
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  content: "";
  border-top: 0;
  border-bottom: 4px solid;
}
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvx5vib7hyj30dk066dge.jpg)

# 导航
+ 在Bootstrap框架将导航独立出来成为一个导航组件，根据不同的版本，可以找到对应的源码
    + LESS版本：对应的源文件是navs.less
    + Sass版本：对应的源文件是_navs.scss
    + 编译后版本：对应源码是bootstrap.css文件第3450行～第3641行

##### 导航基础样式
+ Bootstrap框架中制作导航条主要通过“.nav”样式。
    + 默认的“.nav”样式不提供默认的导航样式
    + 必须附加另外一个样式才会有效，比如“nav-tabs”、“nav-pills”之类
    
```
<ul class="nav nav-tabs">
    <li><a href="##">Home</a></li>
    <li><a href="##">CSS3</a></li>
 	<li><a href="##">Sass</a></li>
 	<li><a href="##">jQuery</a></li>
 	<li><a href="##">Responsive</a></li>
</ul>
```

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvx63pncrqj30ly036t8u.jpg)

#####  导航（标签形tab导航）
+ 标签形导航，也称为选项卡导航。特别是在很多内容分块显示的时，使用这种选项卡来分组十分适合。
+ 标签形导航是通过“nav-tabs”样式来实现。在制作标签形导航时需要在原导航“nav”上追加此类名
    +  假设我们想让“Home”项为当前选中项，只需要在其标签上添加类名“class="active"”
    +  除了当前项之外，有的选项卡还带有禁用状态，实现这样的效果，只需要在标签项上添加“class="disabled"”

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvx67laazxj30mm06kjs5.jpg)

##### 导航（胶囊形(pills)导航）
+ 其实现方法和“nav-tabs”类似，同样的结构，只需要把类名“nav-tabs”换成“nav-pills

```
<ul class="nav nav-pills">
      <li class="active"><a href="##">Home</a></li>
      <li><a href="##">CSS3</a></li>
      <li><a href="##">Sass</a></li>
      <li><a href="##">jQuery</a></li>
      <li class="disabled"><a href="##">Responsive</a></li>
</ul>
```

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvx6j5vv4oj30dv06bt98.jpg)

##### 导航（垂直堆叠的导航）
+ 制作垂直堆叠导航只需要在“nav-pills”的基础上添加一个“nav-stacked”
+ 分隔线效果
    + 在垂直堆叠导航也具有这样的效果，只需要添加在导航项之间添加“<li class=”nav-divider”></li>”

```
<ul class="nav nav-pills nav-stacked">
     <li class="active"><a href="##">Home</a></li>
     <li><a href="##">CSS3</a></li>
     <li><a href="##">Sass</a></li>
     <li><a href="##">jQuery</a></li>
     <li class="disabled"><a href="##">Responsive</a></li>
</ul>
```

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvx6lublx4j30pl07zmxf.jpg)

##### 自适应导航（使用）
+ 自适应导航指的是导航占据容器全部宽度，而且菜单项可以像表格的单元格一样自适应宽度。
    + 自适应导航和前面使用“btn-group-justified”制作的自适应按钮组是一样的。
    + 只不过在制作自适应导航时更换了另一个类名“nav-justified”。
    + 当然他需要和“nav-tabs”或者“nav-pills”配合在一起使用
    
    
```
<ul class="nav nav-tabs nav-justified">
     <li class="active"><a href="##">Home</a></li>
     <li><a href="##">CSS3</a></li>
     <li><a href="##">Sass</a></li>
     <li><a href="##">jQuery</a></li>
     <li><a href="##">Responsive</a></li>
</ul>
```

<em>小屏效果</em>
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvx6oizor6j30bz07xaa9.jpg)
<em>宽屏效果</em>
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvx6pdwqp9j30rz0330sw.jpg)

##### 自适应导航（实现原理）
+ 列表（<ul>）上设置宽度为“100%”，然后每个菜单项(<li>)设置了“display:table-cell”，让列表项以模拟表格单元格的形式显示：
    + 这里有一个媒体查询条件：`@media (min-width:768px){…}`表示自适应导航仅在浏览器视窗宽度大于768px才能按宽屏风格显示。当你的浏览器视窗宽度小于768px的时候，按照小屏风格显示
    + “nav-tabs”和“nav-justified”配合在一起使用，也就是自适应选项卡导航，浏览器视窗宽度小于768px时，在样式上做了另外的处理。
    
##### 导航加下拉菜单（二级导航）
+ 只需要将li当作父容器，使用类名“dropdown”，同时在li中嵌套另一个列表ul

```
<ul class="nav nav-pills">
     <li class="active"><a href="##">首页</a></li>
     <li class="dropdown">
        <a href="##" class="dropdown-toggle" data-toggle="dropdown">教程<span class="caret"></span></a>
        <ul class="dropdown-menu">
            <li><a href="##">CSS3</a></li>
            …
       </ul>
     </li>
     <li><a href="##">关于我们</a></li>
</ul>
```

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvx70ie076j30cf06e74l.jpg)

##### 面包屑式导航
+ 面包屑(Breadcrumb)一般用于导航，主要是起的作用是告诉用户现在所处页面的位置（当前位置）。在Bootstrap框架中面包屑也是一个独立模块组件
    + LESS版本：对应源文件breadcrumbs.less
    + Sass版本：对应源文件_breadcrumbs.scss
    + 编译出来的版本：源码对应bootstrap.css文件第4112行～第4129行
    
    <em>使用方式就很简单，为ol加入breadcrumb类</em>
    
```
<ol class="breadcrumb">
  <li><a href="#">首页</a></li>
  <li><a href="#">我的书</a></li>
  <li class="active">《图解CSS3》</li>
</ol>
```

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvx72mqsqaj30ed02wdfy.jpg)

<br>
<br>
   
<em>The End</em>
<br>
<em>From IAKGnaHz</em>

<hr>