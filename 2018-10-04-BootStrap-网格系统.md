---
layout:     post
title:     BootStrap 笔记
subtitle:   网格系统 下拉菜单
date:       2018-10-5
author:     IAKGnaHz
header-img: img/post-a.jpg
catalog: true
tags:
    - bootstrap
    - css
    
---

#  网格系统
### 实现原理
网格系统的实现原理非常简单，仅仅是通过定义容器大小，平分12份(也有平分成24份或32份，但12份是最常见的)，再调整内外边距，最后结合媒体查询，就制作出了强大的响应式网格系统。Bootstrap框架中的网格系统就是将容器平分成12份。
### 工作原理
+ 数据行(.row)必须包含在容器（.container）中，以便为其赋予合适的对齐方式和内距(padding)。

```
<div class="container">
<div class="row"></div>
</div>
```
+ 在行(.row)中可以添加列(.column)，但列数之和不能超过平分的总列数，比如12。

```
<div class="container">
<div class="row">
  <div class="col-md-4"></div>
  <div class="col-md-8"></div>
```
+ 具体内容应当放置在列容器（column）之内，而且只有列（column）才可以作为行容器(.row)的直接子元素
+ 通过设置内距（padding）从而创建列与列之间的间距。然后通过为第一列和最后一列设置负值的外距（margin）来抵消内距(padding)的影响

<hr>


![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvwh17n1wpj30fe07u0tg.jpg)

简单对图解释一下：

+ 最外边框，带有一大片白色区域，就是相当于浏览器的可视区域。在Bootstrap框架的网格系统中带有响应式效果，其带有四种类型的浏览器（超小屏，小屏，中屏和大屏），其断点（像素的分界点）是768px、992px和1220px。
+ 第二个边框(1)相当于容器(.container)。针对不同的浏览器分辨率，其宽度也不一样：自动、750px、970px和1170px。在bootstrap.css的第736行～第756行进行设置：

```
.container {
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
  @media (min-width: 768px) {
  .container {
    width: 750px;
  }
  @media (min-width: 992px) {
  .container {
    width: 970px;
  }
  @media (min-width: 1200px) {
  .container {
    width: 1170px;
  }
```
+ ２号横条阐述的是，将容器的行（.row）平分了12等份，也就是列。每个列都有一个“padding-left:15px”(图中粉红色部分)和一个“padding-right:15px”(图中紫色部分)。这样也导致了第一个列的padding-left和最后一列的padding-right占据了总宽度的30px，从而致使页面不美观，当然，如果你需要留有一定的间距，这个做法是不错的。如bootstrap.css中第767行~第772行所示：

```
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-right: 15px;
  padding-left: 15px;
```
+ ３号横条就是行容器(.row),其定义了“margin-left”和”margin-right”值为”-15px”，用来抵消第一个列的左内距和最后一列的右内距。在bootstrap.css的第763行~第767行可以看到

```
.row {
  margin-right: -15px;
  margin-left: -15px;
```

+ 将行与列给合在一起就能看到横条4的效果。也就是我们期望看到的效果，第一列和最后一列与容器（.container）之间没有间距。

### 基本用法
+ 网格系统用来布局，其实就是列的组合。Bootstrap框架的网格系统中有四种基本的用法。
    + `列组合`简单理解就是更改数字来合并列（原则：列总和数不能超12），有点类似于表格的colspan属性，
        + 实现列组合方式非常简单，只涉及两个CSS两个特性：浮动与宽度百分比。
            + 确保所有列左浮动
            + 定义每个列组合的宽度（使用的百分比）
    + `列偏移`不希望相邻的两个列紧靠在一起，但又不想使用margin或者其他的技术手段来。这个时候就可以使用列偏移（offset）功能来实现
        + 使用列偏移也非常简单，只需要在列元素上添加类名“col-md-offset-*”(其中星号代表要偏移的列组合数)，那么具有这个类名的列就会向右偏移。
            + 你在列元素上添加“col-md-offset-4”，表示该列向右移动4个列的宽度。
        + 使用”col-md-offset-*”对列进行向右偏移时，要保证列与偏移列的总数不超过12，不然会致列断行显示
        
```
<div class="row">
  <div class="col-md-3">.col-md-3</div>
  <div class="col-md-3 col-md-offset-3">col-md-offset-3</div>
  <div class="col-md-4">col-md-4</div>
</div>
```
<em>上面代码中列和偏移列总数为3+3+3+4 = 13>12，所以发生了列断行。</em>

+ `列排序`其实就是改变列的方向，就是改变左右浮动，并且设置浮动的距离。
    + 在Bootstrap框架的网格系统中是通过添加类名“col-md-push-*”和“col-md-pull-*” (其中星号代表移动的列组合数)。
    
```
<div class="container">
  <div class="row">
    <div class="col-md-4">.col-md-4</div>
    <div class="col-md-8">.col-md-8</div>
  </div>
</div>
```
<em>默认情况之下，上面的代码效果,col-md-4”居左，“col-md-8”居右，如果要互换位置，需要将“col-md-4”向右移动８个列的距离，也就是8个offset ,也就是在“`<div class=“col-md-4”>`”添加类名“col-md-push-8”，调用其样式。也要将“col-md-8”向左移动４个列的距离，也就是4个offset，在“`<div class=”col-md-8”>`”上添加类名“col-md-pull-4”：</em>

#### 列的嵌套
你可以在一个列中添加一个或者多个行（row）容器，然后在这个行容器中插入列（像前面介绍的一样使用列）。但在列容器中的行容器（row），宽度为100%时，就是当前外部列的宽度

<em>嵌套的列总数也需要遵循不超过12列。不然会造成末位列换行显示。</em>

# 下拉菜单
+ 在Bootstrap框架中的下拉菜单组件是一个独立的组件，根据不同的版本，它对应的文件：
    + LESS版本：对应的源码文件为 dropdowns.less
    + Sass版本：对应的源码文件为 _dropdowns.scss
    + 编译后的Bootstrap版本：查看bootstrap.css文件第3004行～第3130行
    + 在使用Bootstrap框架的下拉菜单时，必须调用Bootstrap框架提供的bootstrap.js文件。
    
```
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script>
```

<em>因为Bootstrap的组件交互效果都是依赖于jQuery库写的插件，所以在使用bootstrap.min.js之前一定要先加载jquery.min.js才会生效果。</em>

<hr>

<em>示例</em>

```
<div class="dropdown">
<button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
下拉菜单
<span class="caret"></span>
</button>
<ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
   <li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
   …
   <li role="presentation" class="divider"></li>
   <li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
</ul>
</div>
```
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvwhskbnlbj30cn06874n.jpg)

<em>注意事项</em>
+ 使用一个名为“dropdown”的容器包裹了整个下拉菜单元素，示例中为:
    + `<div class="dropdown"></div>`
+ 使用了一个`<button>`按钮做为父菜单，并且定义类名“dropdown-toggle”和自定义“data-toggle”属性，且值必须和最外容器类名一致。
    + `data-toggle="dropdown"`
+ 下拉菜单项使用一个ul列表，并且定义一个类名为“dropdown-menu”
    + `<ul class="dropdown-menu">`

    
**原理分析**
+ Bootstrap框架中的下拉菜单组件，其下拉菜单项默认是隐藏的
    + 因为“dropdown-menu”默认样式设置了“display:none”
    + 当用户点击父菜单项时，下拉菜单将会被显示出来
    + 当用户再次点击时，下拉菜单将继续隐藏

+ 通过js技术手段，给父容器“div.dropdown”添加或移除类名“open”来控制下拉菜单显示或隐藏。
    + 默认情况，“div.dropdown”没有类名“open”
    + 当用户第一次点击时，“div.dropdown”会添加类名“open”；
    + 当用户再次点击时，“div.dropdown”容器中的类名“open”又会被移除。

    <hr>
    
    <em>未下拉时</em>
    ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvwi74npntj30kj03vt9p.jpg)
    <em>下拉菜单后，类名发生变化</em>
    ![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvwi95rybgj30lb03j0tr.jpg)
    
```
.open > .dropdown-menu {
  display: block;
}
```
    <hr>
    
**下拉分隔线**
在Bootstrap框架中的下拉菜单还提供了下拉分隔线，假设下拉菜单有两个组，那么组与组之间可以通过添加一个空的<li>，并且给这个<li>添加类名“divider”来实现添加下拉分隔线的功能。

<em>对于样式</em>

```
.dropdown-menu .divider {
  height: 1px;
  margin: 9px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
```
<hr>

 **菜单标题**   
 
为了让这个分组更明显，还可以给每个组添加一个头部（标题）。

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvwid7k4s0j30js09hgmd.jpg)


```
<div class="dropdown">
<button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
下拉菜单
<span class="caret"></span>
</button>
<ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
<li role="presentation" class="dropdown-header">第一部分菜单头部</li>
<li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
…
<li role="presentation" class="divider"></li>
<li role="presentation" class="dropdown-header">第二部分菜单头部</li>
…
<li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
</ul>
</div>
```

<em>样式</em>

```
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #999;
}
```

**对齐方式**

Bootstrap框架中下拉菜单默认是左对齐，如果你想让下拉菜单相对于父容器右对齐时，可以在“dropdown-menu”上添加一个“pull-right”或者“dropdown-menu-right”类名，


```
<div class="dropdown">
  <button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
  下拉菜单
  <span class="caret"></span>
  </button>
  <ul class="dropdown-menu pull-right" role="menu" aria-labelledby="dropdownMenu1">
   …
  </ul>
</div>
```
![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvwih4c4ulj30ie0a0ta3.jpg)

**同时一定要为.dropdown添加`float:leftcss`样式**

**菜单项状态**

+ 悬浮状态(:hover)
+ 焦点状态(:focus)
+ 当前状态(.active)
+ 禁用状态(.disabled)


```
<div class="dropdown">
  <button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
  下拉菜单
  <span class="caret"></span>
  </button>
  <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
    <li role="presentation" class="active"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
    ….
    <li role="presentation" class="disabled"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
  </ul>
</div>
```
![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvwinl4x6nj30fd06f0t6.jpg)

<br>
<br>
   
<em>The End</em>
<br>
<em>From IAKGnaHz</em>

<hr>