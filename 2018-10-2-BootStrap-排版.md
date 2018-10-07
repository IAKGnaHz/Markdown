---
layout:     post
title:      BootStrap 笔记
subtitle:   排版
date:       2018-10-2
author:     IAKGnaHz
header-img: img/post-a.jpg
catalog: true
tags:
    - bootstrap
    - css
    
---

# BootStrap
## 排版
### 基本的HTML模版

```javascript
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Bootstrap的HTML标准模板</title>   
        <!-- Bootstrap -->
        <link href="css/bootstrap.min.css" rel="stylesheet">
        <!--你自己的样式文件 -->
        <link href="css/your-style.css" rel="stylesheet">        
        <!-- 以下两个插件用于在IE8以及以下版本浏览器支持HTML5元素和媒体查询，如果不需要用可以移除 -->
        <!--[if lt IE 9]>
        <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
        <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
        <![endif]-->
    </head>
    <body>
        <h1>Hello, world!</h1>
        
        <!-- 如果要使用Bootstrap的js插件，必须先调入jQuery -->
        <script src="https://www.imooc.com/static/lib/jquery/1.9.1/jquery.js"></script>
        <!-- 包括所有bootstrap的js插件或者可以根据需要使用的js插件调用　-->
        <script src="http://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script> 
    </body>
</html>
```

+ bootstrap模板为使IE6、7、8版本（IE9以下版本）浏览器兼容html5新增的标签，引入下面代码文件即可。

```javascript
<script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
```

+ 同理为使IE6、7、8版本浏览器兼容css3样式，引入下面代码：

```javascript
<script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
```

### 全局样式
> 在制作Web页面时，前端人员都习惯为网站设置一个全局样式（reset.css）。那么在Bootstrap框架中也不例外。Bootstrap框架的核心是轻量的CSS基础代码库，他并没有一味的重置样式，而是注重各浏览器基础表现，降低开发难度。大部分前端人员都具有归零的思想，但实际你会发现，归零之后的样式在开发过程中会存在着潜在的问题，例如，在全局样式表中将em变成一个普通标记，明明应该是斜体，怎么就没效果了呢？
Bootstrap框架在这一部分做了一定的变更，不再一味追求归零，而是更注重重置可能产生问题的样式（如，body,form的margin等），保留和坚持部分浏览器的基础样式，解决部分潜在的问题，提升一些细节的体验，具体说明如下：

+ 移除body的margin声明
+ 设置body的背景色为白色
+ 为排版设置了基本的字体、字号和行高
+ 设置全局链接颜色，且当链接处于悬浮“:hover”状态时才会显示下划线样式

下面的部分css样式展现了该特性


```javascript

html {
  font-family: sans-serif;
  -webkit-text-size-adjust: 100%;
      -ms-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  margin: .67em 0;
  font-size: 2em;
}
mark {
  color: #000;
  background: #ff0;
}
small {
  font-size: 80%;
}
sub,
sup {
  position: relative;
  font-size: 75%;
  line-height: 0;
  vertical-align: baseline;
}
sup {
  top: -.5em;
}
sub {
  bottom: -.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  height: 0;
  -moz-box-sizing: content-box;
       box-sizing: content-box;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  margin: 0;
  font: inherit;
  color: inherit;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  padding: 0;
  border: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-box-sizing: content-box;
     -moz-box-sizing: content-box;
          box-sizing: content-box;
  -webkit-appearance: textfield;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  padding: .35em .625em .75em;
  margin: 0 2px;
  border: 1px solid #c0c0c0;
}
legend {
  padding: 0;
  border: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-spacing: 0;
  border-collapse: collapse;
}
td,
th {
  padding: 0;
}
@media print {
  * {
    color: #000 !important;
    text-shadow: none !important;
    background: transparent !important;
    box-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="javascript:"]:after,
  a[href^="#"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;

    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  select {
    background: #fff !important;
  }
  .navbar {
    display: none;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}

```


### 标题
> Bootstrap和普通的HTML页面一样，定义标题都是使用标签`<h1>到<h6>`,只不过Bootstrap覆盖了其默认的样式，使用其在所有浏览器下显示的效果一样，具体定义的规则可以如下表所示：

![](https://ws3.sinaimg.cn/large/006tNc79gy1fvtmlk6ahgj30nx0bcdhd.jpg)

BootStrap 对标题样式进行了一下显著的优化重置

+ 重新设置了margin-top和margin-bottom的值，  h1~h3重置后的值都是20px；h4~h6重置后的值都是10px。
+ 所有标题的行高都是1.1（也就是font-size的1.1倍）,而且文本颜色和字体都继承父元素的颜色和字体。
+ 固定不同级别标题字体大小，h1=36px，h2=30px，h3=24px，h4=18px，h5=14px和h6=12px。

> 使用`<small>`标签来制作副标题，这些副标题也有其独特的样式

+ 行高都是1，而且font-weight设置了normal变成了常规效果（不加粗），同时颜色被设置为灰色（#999）。
+ 由于<small>内的文本字体在h1~h3内，其大小都设置为当前字号的65%；而在h4~h6内的字号都设置为当前字号的75%；
+ 详细代码请参阅bootstrap.css文件中第407行~第443行。


```javascript
<!DOCTYPE HTML>
<html>
<head>
<meta charset="utf-8">
<title>标题（二）</title>
<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/4.0.0-beta.2/css/bootstrap.min.css">
</head>

<body>

<!--Bootstrap中使用了<small>标签来制作副标题-->
<h1>Bootstrap标题一<small>我是副标题</small></h1>
<h2>Bootstrap标题二<small>我是副标题</small></h2>
<h3>Bootstrap标题三<small>我是副标题</small></h3>
<h4>Bootstrap标题四<small>我是副标题</small></h4>
<h5>Bootstrap标题五<small>我是副标题</small></h5>
<h6>Bootstrap标题六<small>我是副标题</small></h6>

<h1>孤儿院无私奉献30年<small>一曲人性的赞歌</small></h1>
</body>
</html>
```

### 段落
> 在Bootstrap中为文本设置了一个全局的文本样式（这里所说的文本是指正文文本）：

+ 全局文本字号为14px(font-size)。
+ 行高为1.42857143（line-height），大约是20px(大家看到一串的小数或许会有疑惑，其实他是通过LESS编译器计算出来的，当然Sass也有这样的功能)。
+ 颜色为深灰色（#333）；
+ 字体为"Helvetica Neue", Helvetica, Arial, sans-serif;（font-family），或许这样的字体对我们中文并不太合适，但在实际项目中，大家可以根据自己的需求进行重置，在此我们不做过多阐述，我们回到这里。该设置都定义在<body>元素上，由于这几个属性都是继承属性，所以Web页面中文本（包括段落p元素）如无重置都会具有这些样式效果。
+ `/*源码请查看bootstrap.css文件中第274行~280行*/`

```javascript
body {
font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
font-size: 14px;
line-height: 1.42857143;
color: #333;
background-color: #fff;
}
```

> 另外在Bootstrap中，为了让段落p元素之间具有一定的间距，便于用户阅读文本，特意设置了p元素的margin值（默认情况之下，p元素具有一个上下外边距，并且保持一个行高的高度）：


```javascript
p {
 margin: 0 0 10px;
}
```

> 如果你对CSS预处理器有所了解，那么你完全可以根据Bootstrap提供的预编译版本LESS(或者Sass)进行自定义排版设置。在Bootstrap中，排版设置的默认值都存在variables.less文件中(Sass版本存在_variables.scss中)的两个变量：

+ LESS版本

```javascript
@font-size-base: 14px; @line-height-base: 1.428571429; // 20/14
```
+ Sass版本

```javascript
$font-size-base: 14px !default; $line-height-base: 1.428571429 !default; // 20/14
```

第一条语句用于设置字体大小，第二条语句用于设置行高。系统默认使用这两个值产生整个页面相应的margin、padding和line-height的值。换句话说，你只需要修改这两个变量的值，然后重新编译，就可以自定义自己的Bootstrap排版样式。

### 强调内容
> 在实际项目中，对于一些重要的文本，希望突出强调的部分都会做另外的样式处理。Bootstrap同样对这部分做了一些轻量级的处理。如果想让一个段落p突出显示，可以通过添加类名“.lead”实现，其作用就是增大文本字号，加粗文本，而且对行高和margin也做相应的处理。用法如下：


```javascript
<p>我是普通文本，我的样子长成这样我是普通文本，我的样子长成这样我是普通文本，</p>
<p class="lead">我是特意要突出的文本，我的样子成这样。我是特意要突出的文本，我的样子长成这样。</p>
```
+ “.lead”对应的样式如下：
+ 源码查看bootstrap.css文件第470行~480行

```javascript
.lead {
margin-bottom: 20px;
font-size: 16px;
font-weight: 200;
line-height: 1.4;
}
@media (min-width: 768px) {/*大中型浏览器字体稍大*/
.lead {
font-size: 21px;
  }
}
```

### 粗体
> 粗体就是给文本加粗，在普通的元素中我们一般通过font-weight设置为bold关键词给文本加粗。在Bootstrap中，可以使用<b>和<strong>标签让文本直接加粗。

```javascript
b,strong {
  font-weight: bold; /*文本加粗*/
}
```
### 斜体
> 在排版中，除了用加粗来强调突出的文本之外，还可以使用斜体。斜体类似于加粗一样，除了可以给元素设置样式font-style值为italic实现之外，在Bootstrap中还可以通过使用标签<em>或<i>来实现。

### 强调相关的类
> 在Bootstrap中除了使用标签<strong>、<em>等说明正文某些字词、句子的重要性，Bootstrap还定义了一套类名，这里称其为强调类名（类似前面说的“.lead”）,这些强调类都是通过颜色来表示强调，具本说明如下：

+ .text-muted：提示，使用浅灰色（#999）
+ .text-primary：主要，使用蓝色（#428bca）
+ .text-success：成功，使用浅绿色(#3c763d)
+ .text-info：通知信息，使用浅蓝色（#31708f）
+ .text-warning：警告，使用黄色（#8a6d3b）
+ .text-danger：危险，使用褐色（#a94442）


```javascript
.text-muted {
color: #999;
}
.text-primary {
color: #428bca;
}
a.text-primary:hover {
color: #3071a9;
}
.text-success {
color: #3c763d;
}
a.text-success:hover {
color: #2b542c;
}
.text-info {
color: #31708f;
}
a.text-info:hover {
color: #245269;
}
.text-warning {
color: #8a6d3b;
}
a.text-warning:hover {
color: #66512c;
}
.text-danger {
color: #a94442;
}
a.text-danger:hover {
color: #843534;
}
```
### 文本对齐风格
> Bootstrap通过定义四个类名来控制文本的对齐风格：

+ .text-left: 左对齐
+ .text-center：居中对齐
+ .text-right：右对齐
+ .text-justify：两端对齐

```javascript
.text-left {
text-align: left;
}
.text-right {
text-align: right;
}
.text-center {
text-align: center;
}
.text-justify {
text-align: justify;
}
```

### 列表
#### 无序列表 有序列表
> 无序列表和有序列表使用方式和我们平时使用的一样（无序列表使用ul，有序列表使用ol标签），在样式方面，Bootstrap只是在此基础上做了一些细微的优化，源码请查看bootstrap.css文件的第569行~第579行：

```javascript
ul,
ol {
  margin-top: 0;
  margin-bottom: 10px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
```

**从源码上我们可以得知，Bootstrap对于列表，只是在margin上做了一些调整**


####  去点列表
> 通过给无序列表添加一个类名“.list-unstyled”,这样就可以去除默认的列表样式的风格。

```javascript
.list-unstyled {
padding-left: 0;
list-style: none;
}
//将列表的默认的左边内距也清0了
```

#### 内联列表
> Bootstrap像去点列表一样，通过添加类名“.list-inline”来实现内联列表，简单点说就是把垂直列表换成水平列表，而且去掉项目符号（编号），保持水平显示。也可以说内联列表就是为制作水平导航而生。

```javascript
.list-inline {
padding-left: 0;
margin-left: -5px;
list-style: none;
}
.list-inline > li {
display: inline-block;
padding-right: 5px;
padding-left: 5px;
}
```

#### 水平定义列表
> 水平定义列表就像内联列表一样，Bootstrap可以给<dl>添加类名“.dl-horizontal”给定义列表实现水平显示效果。

```javascript
@media (min-width: 768px) {
.dl-horizontal dt {
float: left;
width: 160px;
overflow: hidden;
clear: left;
text-align: right;
text-overflow: ellipsis;
white-space: nowrap;
  }
.dl-horizontal dd {
margin-left: 180px;
  }
}
```

此处添加了一个媒体查询。也就是说，只有屏幕大于768px的时候，添加类名“.dl-horizontal”才具有水平定义列表效果。其实现主要方式：

+ 将dt设置了一个左浮动，并且设置了一个宽度为160px
+ 将dd设置一个margin-left的值为180px，达到水平的效果
+ 当标题宽度超过160px时，将会显示三个省略号

宽屏显示效果 水平显示
> ![](https://ws1.sinaimg.cn/large/006tNc79gy1fvton0706vj30oa039aag.jpg)

缩小屏幕时
> ![](https://ws1.sinaimg.cn/large/006tNc79gy1fvtong23pcj30h804swez.jpg)

### 代码
+ 使用`<code></code>`来显示单行内联代码 一般是针对于单个单词或单个句子的代码
+ 使用`<pre></pre>`来显示多行块代码  一般是针对于多行代码（也就是成块的代码）
+ 使用`<kbd></kbd>`来显示用户输入代码 一般是表示用户要通过键盘输入的内容

> 正如前面所示，`<pre>`元素一般用于显示大块的代码，并保证原有格式不变。但有时候代码太多，而且不想让其占有太大的页面篇幅，就想控制代码块的大小。Bootstrap也考虑到这一点，你只需要在pre标签上添加类名“.pre-scrollable”，就可以控制代码块区域最大高度为340px，一旦超出这个高度，就会在Y轴出现滚动条。

```javascript
.pre-scrollable {
max-height: 340px;
overflow-y: scroll;
}
```

### 表格
> 表格是Bootstrap的一个基础组件之一，Bootstrap为表格提供了1种基础样式和4种附加样式以及1个支持响应式的表格。

+  .table：基础表格
+  .table-striped：斑马线表格
+  .table-bordered：带边框的表格
+  .table-hover：鼠标悬停高亮的表格
+  .table-condensed：紧凑型表格
+  .table-responsive：响应式表格 
+  所以大家在使用Bootstrap表格时，千万注意，你的`<table>`元素中一定不能缺少类名**table**。

#### 表格行的类
![](https://ws4.sinaimg.cn/large/006tNc79gy1fvtp6lnzjaj30ke0e4gmv.jpg)

> **特别提示**：除了”.active”之外，其他四个类名和”.table-hover”配合使用时，Bootstrap针对这几种样式也做了相应的悬浮状态的样式设置，所以如果需要给tr元素添加其他颜色样式时，在”.table-hover”表格中也要做相应的调整。

**注意要实现悬浮状态，需要在<table>标签上加入table-hover类。**

`<table class="table-hover">`

![](https://ws1.sinaimg.cn/large/006tNc79gy1fvtp9auco7j30c107kq3w.jpg)

