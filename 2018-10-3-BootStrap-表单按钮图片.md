---
layout:     post
title:      BootStrap 笔记
subtitle:   表单 按钮 图片
date:       2018-10-3
author:     IAKGnaHz
header-img: img/post-a.jpg
catalog: true
tags:
    - bootstrap
    - css
    
---

# BootStrap
## 表单
### 基础表单
> 表单主要功能是用来与用户做交流的一个网页控件，良好的表单设计能够让网页与用户更好的沟通。表单中常见的元素主要包括：文本输入框、下拉选择框、单选按钮、复选按钮、文本域和按钮等。其中每个控件所起的作用都各不相同，而且不同的浏览器对表单控件渲染的风格都各有不同。

Bootstrap框架的表单，其源码占据了大量的代码，同样的，根据不同的Bootstrap版本，你可以轻松获取相应的源码：

+ LESS版本：对应源文件 forms.less
+ Sass版本：对应源文件 _forms.scss

对于基础表单，Bootstrap并未对其做太多的定制性效果设计，仅仅对表单内的fieldset、legend、label标签进行了定制

```javascript
fieldset {
min-width: 0;
padding: 0;
margin: 0;
border: 0;
}
legend {
display: block;
width: 100%;
padding: 0;
margin-bottom: 20px;
font-size: 21px;
line-height: inherit;
color: #333;
border: 0;
border-bottom: 1px solid #e5e5e5;
}

label {
display: inline-block;
margin-bottom: 5px;
font-weight: bold;
}
```

当然表单除了这几个元素之外，还有input、select、textarea等元素，在Bootstrap框架中，通过定制了一个类名`form-control`，也就是说，如果这几个元素使用了类名“form-control”，将会实现一些设计上的定制效果。

+ 宽度变成了100%
+ 设置了一个浅灰色（#ccc）的边框
+ 具有4px的圆角
+ 设置阴影效果，并且元素得到焦点之时，阴影和边框效果会有所变化
+ 设置了placeholder的颜色为#999

### 水平表单
> Bootstrap框架默认的表单是垂直显示风格，但很多时候我们需要的水平表单风格（标签居左，表单控件居右）
> 在Bootstrap框架中要实现水平表单效果，必须满足以下两个条件：

+ 在<form>元素是使用类名“form-horizontal”。
+ 配合Bootstrap框架的网格系统。（网格布局会在以后的章节中详细讲解）

在<form>元素上使用类名“form-horizontal”主要有以下几个作用：
+ 设置表单控件padding和margin值。
+ 改变“form-group”的表现形式，类似于网格系统的“row”。


```javascript
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
	<title>水平表单</title>
	<link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.1.1/css/bootstrap.min.css">
</head>
<body>
<form class="form-horizontal" role="form">
  <div class="form-group">
    <label for="inputEmail3" class="col-sm-2 control-label">邮箱</label>
    <div class="col-sm-10">
      <input type="email" class="form-control" id="inputEmail3" placeholder="请输入您的邮箱地址">
    </div>
  </div>
  <div class="form-group">
    <label for="inputPassword3" class="col-sm-2 control-label">密码</label>
    <div class="col-sm-10">
      <input type="password" class="form-control" id="inputPassword3" placeholder="请输入您的邮箱密码">
    </div>
  </div>
  <div class="form-group">
    <div class="col-sm-offset-2 col-sm-10">
      <div class="checkbox">
        <label>
          <input type="checkbox"> 记住密码
        </label>
      </div>
    </div>
  </div>
  <div class="form-group">
    <div class="col-sm-offset-2 col-sm-10">
      <button type="submit" class="btn btn-default">进入邮箱</button>
    </div>
  </div>
</form>
</body>
</html>
```

![](https://ws4.sinaimg.cn/large/006tNc79gy1fvurt2fi62j309u02jq2t.jpg)

### 内联表单
> 有时候我们需要将表单的控件都在一行内显示.在Bootstrap框架中实现这样的表单效果是轻而易举的，你只需要在<form>元素中添加类名“form-inline”即可。内联表单实现原理非常简单，欲将表单控件在一行显示，就需要将表单控件设置成内联块元素（display:inline-block）。

如果你要在input前面添加一个label标签时，会导致input换行显示。如果你必须添加这样的一个label标签，并且不想让input换行，你需要将label标签也放在容器“form-group”中，如：

```javascript
<div class="form-group">
    <label class="sr-only" for="exampleInputEmail2">Email address</label>
</div>
<div class="form-group">
    <inputtype="email" class="form-control" id="exampleInputEmail2" placeholder="Enter email">
</div>
```

实例

```javascript
<form class="form-inline" role="form">
<div class="form-group">
  <label class="sr-only" for="exampleInputEmail2">邮箱</label>
  <input type="email" class="form-control" id="exampleInputEmail2" placeholder="请输入你的邮箱地址">
</div>
<div class="form-group">
  <label class="sr-only" for="exampleInputPassword2">密码</label>
  <input type="password" class="form-control" id="exampleInputPassword2" placeholder="请输入你的邮箱密码">
</div>
<div class="checkbox">
<label>
   <input type="checkbox">记住密码
</label>
</div>
<button type="submit" class="btnbtn-default">进入邮箱</button>
</form>
```

![](https://ws3.sinaimg.cn/large/006tNc79gy1fvurylmkbqj308t01h745.jpg)

回过头来看示例，你或许会问，为什么添加了label标签，而且没有放置在”form-group”这样的容器中，input也不会换行；还有label标签怎么没显示出来。如果你仔细看，在label标签运用了一个类名“sr-only”，标签没显示就是这个样式将标签隐藏了。

```javascript
.sr-only {
position: absolute;
width: 1px;
height: 1px;
padding: 0;
margin: -1px;
overflow: hidden;
clip: rect(0, 0, 0, 0);
border: 0;
}
```

### 表单控件
#### 输入框input  单行输入框
> 常见的文本输入框，也就是input的type属性值为text。在Bootstrap中使用input时也必须添加type类型，如果没有指定type类型，将无法得到正确的样式，因为Bootstrap框架都是通过input[type=“?”](其中?号代表type类型，比如说text类型，对应的是input[type=“text”])的形式来定义样式的。为了让控件在各种表单风格中样式不出错，需要添加类名“form-control”

```javascript
<form role="form">
<div class="form-group">
<input type="email" class="form-control" placeholder="Enter email">
</div>
</form>
```

![](https://ws1.sinaimg.cn/large/006tNc79gy1fvus3jah0yj308j017742.jpg)

#### 下拉选择框
> Bootstrap框架中的下拉选择框使用和原始的一致，多行选择设置multiple属性的值为multiple。Bootstrap框架会为这些元素提供统一的样式风格。如：

```javascript
<form role="form">
<div class="form-group">
  <select class="form-control">
    <option>1</option>
    <option>2</option>
    <option>3</option>
    <option>4</option>
    <option>5</option>
  </select>
  </div>
  <div class="form-group">
  <select multiple class="form-control">
    <option>1</option>
    <option>2</option>
    <option>3</option>
    <option>4</option>
    <option>5</option>
  </select>
</div>
</form>
```

![](https://ws2.sinaimg.cn/large/006tNc79gy1fvut97ysttj3075020wea.jpg)

#### 文本域
> 文本域和原始使用方法一样，设置rows可定义其高度，设置cols可以设置其宽度。但如果textarea元素中添加了类名“form-control”类名，则无需设置cols属性。因为Bootstrap框架中的“form-control”样式的表单控件宽度为100%或auto。

```javascript
<form role="form">
  <div class="form-group">
    <textarea class="form-control" rows="3"></textarea>
  </div>
</form>
```

#### 复选框checkbox和单选择按钮radio
> Bootstrap框架中checkbox和radio有点特殊，Bootstrap针对他们做了一些特殊化处理，主要是checkbox和radio与label标签配合使用会出现一些小问题（最头痛的是对齐问题）。使用Bootstrap框架，开发人员无需考虑太多，只需要按照下面的方法使用即可

```javascript
<form role="form">
<div class="checkbox">
<label>
<input type="checkbox" value="">
记住密码
</label>
</div>
<div class="radio">
<label>
<input type="radio" name="optionsRadios" id="optionsRadios1" value="love" checked>
喜欢
</label>
</div>
<div class="radio">
<label>
<input type="radio" name="optionsRadios" id="optionsRadios2" value="hate">
不喜欢
</label>
</div>
</form>
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvutdvfuufj30br05174h.jpg)

从上面的实例，我们可以得知

+ 不管是checkbox还是radio都使用label包起来了
+ checkbox连同label标签放置在一个名为“.checkbox”的容器内
+ radio连同label标签放置在一个名为“.radio”的容器内
+ Bootstrap框架中，主要借助“.checkbox”和“.radio”样式，来处理复选框、单选按钮与标签的对齐方式。

#### 复选框和单选按钮水平排列
+ 如果checkbox需要水平排列，只需要在label标签上添加类名“checkbox-inline”
+ 如果radio需要水平排列，只需要在label标签上添加类名“radio-inline”



```javascript
.radio-inline,
.checkbox-inline {
display: inline-block;
padding-left: 20px;
margin-bottom: 0;
font-weight: normal;
vertical-align: middle;
cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
margin-top: 0;
margin-left: 10px;
}
```

#### 按钮

```javascript
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单控件状态——焦点状态</title>
	<link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.1.1/css/bootstrap.min.css">
</head>
<body>
<table class="table table-bordered table-striped">  
    <thead>  
      <tr>  
        <th>Button</th>  
        <th>class=""</th>  
        <th>Description</th>  
      </tr>  
    </thead>  
    <tbody>  
      <tr>  
        <td><button class="btn" href="#">Default</button></td>  
        <td><code>btn</code></td>  
        <td>Standard gray button with gradient</td>  
      </tr>  
      <tr>  
        <td><button class="btn btn-primary" href="#">Primary</button></td>  
        <td><code>btn btn-primary</code></td>  
        <td>Provides extra visual weight and identifies the primary action in a set of buttons</td>  
      </tr>  
      <tr>  
        <td><button class="btn btn-info" href="#">Info</button></td>  
        <td><code>btn btn-info</code></td>  
        <td>Used as an alternative to the default styles</td>  
      </tr>  
      <tr>  
        <td><button class="btn btn-success" href="#">Success</button></td>  
        <td><code>btn btn-success</code></td>  
        <td>Indicates a successful or positive action</td>  
      </tr>  
      <tr>  
        <td><button class="btn btn-warning" href="#">Warning</button></td>  
        <td><code>btn btn-warning</code></td>  
        <td>Indicates caution should be taken with this action</td>  
      </tr>  
      <tr>  
        <td><button class="btn btn-danger" href="#">Danger</button></td>  
        <td><code>btn btn-danger</code></td>  
        <td>Indicates a dangerous or potentially negative action</td>  
      </tr>  
      <tr>  
        <td><button class="btn btn-inverse" href="#">Inverse</button></td>  
        <td><code>btn btn-inverse</code></td>  
        <td>Alternate dark gray button, not tied to a semantic action or use</td>  
      </tr>  
    </tbody>  
  </table>    
</body>
</html>
```

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvutn7ikv0j30bz0f2di4.jpg)

#### 表单控件大小
> 可以通过设置控件的height，line-height，padding和font-size等属性来实现控件的高度设置。不过Bootstrap框架还提供了两个不同的类名，用来控制表单控件的高度。这两个类名是：
 
+ input-sm:让控件比正常大小更小
+ input-lg:让控件比正常大小更大


```javascript
<input class="form-control input-lg" type="text" placeholder="添加.input-lg，控件变大">
<input class="form-control" type="text" placeholder="正常大小">
<input class="form-control input-sm" type="text" placeholder="添加.input-sm，控件变小">
```
`sm lg 示例`
![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvutqlgmoij30c109fmxs.jpg)

> 从上面的源码中不难发现，不管是“input-sm”还是“input-lg”仅对控件高度做了处理。但往往很多时候，我们需要控件宽度也要做一定的变化处理。这个时候就要借住Bootstrap框架的网格系统。所以你要控制表单宽度，可以像下面这样使用：


```javascript
<form role="form" class="form-horizontal">
  <div class="form-group">
  <div class="col-xs-4">
    <input class="form-control input-lg" type="text" placeholder=".col-xs-4">
  </div>
  <div class="col-xs-4">
    <input class="form-control input-lg" type="text" placeholder=".col-xs-4">
  </div>
  <div class="col-xs-4">
    <input class="form-control input-lg" type="text" placeholder=".col-xs-4">
  </div>
  </div>
    …
</form>
```
`col-xs-X`示例
![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvutrebqvpj30c007bweu.jpg)

#### 表单控件状态
> 焦点状态是通过伪类“:focus”来实现。Bootstrap框架中表单控件的焦点状态删除了outline的默认样式，重新添加阴影效果。


```javascript
.form-control:focus {
border-color: #66afe9;
outline: 0;
  -webkit-box-shadow: inset 0 1px 1pxrgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, .6);
box-shadow: inset 0 1px 1pxrgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, .6);
}
```

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvutvlj1e5j30g403jt90.jpg)

#### 禁用状态
> Bootstrap框架的表单控件的禁用状态和普通的表单禁用状态实现方法是一样的，在相应的表单控件上添加属性“disabled”。和其他表单的禁用状态不同的是，Bootstrap框架做了一些样式风格的处理：

**/*源码请查看bootstrap.css文件第1723行～第1729行*/**


```javascript
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
cursor: not-allowed;
background-color: #eee;
opacity: 1;
}
```


```javascript
<input class="form-control" type="text" placeholder="表单已禁用，不能输入" disabled>
```

> 在使用了“form-control”的表单控件中，样式设置了禁用表单背景色为灰色，而且手型变成了不准输入的形状。如果控件中不使用类名“form-control”，禁用的控件只会有一个不准输入的手型出来。

#### 表单控件状态(验证状态)
+ .has-warning:警告状态（黄色）
+ .has-error：错误状态（红色）
+ .has-success：成功状态（绿色）


```javascript
<form role="form">
<div class="form-group has-success">
  <label class="control-label" for="inputSuccess1">成功状态</label>
  <input type="text" class="form-control" id="inputSuccess1" placeholder="成功状态" >
</div>
<div class="form-group has-warning">
  <label class="control-label" for="inputWarning1">警告状态</label>
  <input type="text" class="form-control" id="inputWarning1" placeholder="警告状态">
</div>
<div class="form-group has-error">
  <label class="control-label" for="inputError1">错误状态</label>
  <input type="text" class="form-control" id="inputError1" placeholder="错误状态">
</div>
</form>
```
![](https://ws2.sinaimg.cn/large/006tNbRwgy1fvuu7fbv4nj30a109o0t7.jpg)

> 很多时候，在表单验证的时候，不同的状态会提供不同的 icon，比如成功是一个对号（√），错误是一个叉号（×）等。在Bootstrap框中也提供了这样的效果。如果你想让表单在对应的状态下显示 icon 出来，只需要在对应的状态下添加类名“has-feedback”。请注意，此类名要与“has-error”、“has-warning”和“has-success”在一起


```javascript
<h3>示例2</h3>   
<form role="form">
  <div class="form-group has-success has-feedback">
    <label class="control-label" for="inputSuccess1">成功状态</label>
    <input type="text" class="form-control" id="inputSuccess1" placeholder="成功状态" >
    <span class="glyphicon glyphicon-ok form-control-feedback"></span>
  </div>
  <div class="form-group has-warning has-feedback">
    <label class="control-label" for="inputWarning1">警告状态</label>
    <input type="text" class="form-control" id="inputWarning1" placeholder="警告状态">
    <span class="glyphicon glyphicon-warning-sign form-control-feedback"></span>
  </div>
  <div class="form-group has-error has-feedback">
    <label class="control-label" for="inputError1">错误状态</label>
    <input type="text" class="form-control" id="inputError1" placeholder="错误状态">
    <span class="glyphicon glyphicon-remove form-control-feedback"></span>  
  </div>
</form>
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvuu8rp63uj308x08zt97.jpg)

#### 表单提示信息
> 平常在制作表单验证时，要提供不同的提示信息。在Bootstrap框架中也提供了这样的效果。使用了一个"help-block"样式，将提示信息以块状显示，并且显示在控件底部。


```javascript
<form role="form">
<div class="form-group has-success has-feedback">
  <label class="control-label" for="inputSuccess1">成功状态</label>
  <input type="text" class="form-control" id="inputSuccess1" placeholder="成功状态" >
  <span class="help-block">你输入的信息是正确的</span>
  <span class="glyphiconglyphicon-ok form-control-feedback"></span>
</div>
  …
</form>
```
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvuughy8eyj30c009oaar.jpg)

> 在Bootstrap V2.x版本中还提供了一个行内提示信息，其使用了类名“help-inline”。一般让提示信息显示在控件的后面，也就是同一水平显示。如果你想在BootstrapV3.x版本也有这样的效果，你可以添加这段代码：


```javascript
.help-inline{
  display:inline-block;
  padding-left:5px;
  color: #737373;
}
```

## 按钮
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvuujjgqcsj30bv058mxy.jpg)

> Bootstrap框架的按钮也是一个独立部分，我们同样在不同的版本之中能找到对应的代码：

+ LESS版本：查看源文件buttons.less
+ Sass版本：查看源文件_buttons.scss
+ 已编译版本：查看源文件bootstrap.css文件第1992行～第2353行

### 基本按钮
> Bootstrap框架V3.x版本的基本按钮和V2.x版本的基本按钮一样，都是通过类名“btn”来实现。不同的是在V3.x版本要简约很多，去除了V2.x版本中的大量的CSS3中的部分特效，比如说文本阴影（text-shadow）、渐变背景（background-image）、边框阴影（box-shadow）等。
难能可贵的是，Bootstrap框架中的考虑了不同浏览器的解析差异，进行了比较安全的兼容性处理，使按钮效果在不同的浏览器中所呈现的效果基本相同。


```javascript
<button class="btn" type="button">我是一个基本按钮</button>
```
### 默认按钮
> Bootstrap框架首先通过基础类名“.btn”定义了一个基础的按钮风格，然后通过“.btn-default”定义了一个默认的按钮风格。默认按钮的风格就是在基础按钮的风格的基础上修改了按钮的背景颜色、边框颜色和文本颜色。


```javascript
<button class="btn btn-default" type="button">默认按钮</button>
```

### 多标签支持
> 一般制作按钮除了使用<button>标签元素之外，还可以使用<input type="submit">和<a>标签等。同样，在Bootstrap框架中制作按钮时，除了刚才所说的这些标签元素之外，还可以使用在其他的标签元素上，唯一需要注意的是，要在制作按钮的标签元素上添加类名“btn”。如果不添加是不会有任何按钮效果。


```javascript
<button class="btn btn-default" type="button">button标签按钮</button>
<input type="submit" class="btn btn-default" value="input标签按钮"/>
<a href="##" class="btn btn-default">a标签按钮</a>
<span class="btn btn-default">span标签按钮</span>
<div class="btn btn-default">div标签按钮</div>
```

### 定制风格
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvuutok8qoj30kx08ot9m.jpg)
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fvuutveo1mj30ma0migp1.jpg)

### 按钮大小
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvuuukkciij30j70gtq4s.jpg)

那么在实际使用中，这几个类名可以配合按钮中其他颜色类名一起使用，但唯一一点不能缺少“.btn”类名：


```javascript
<button class="btn btn-primary btn-lg" type="button">大型按钮.btn-lg</button>
<button class="btn btn-primary" type="button">正常按钮</button>
<button class="btn btn-primary btn-sm" type="button">小型按钮.btn-sm</button>
<button class="btn btn-primary btn-xs" type="button">超小型按钮.btn-xs</button>
```

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvuuxf6ycaj30bi02taa9.jpg)

### 块状按钮
> 但有时候在制作按钮的时候需要按钮宽度充满整个父容器（width:100%），特别是在移动端的制作中。那么前面的方法我们都无法很好的实现，除非重新定义按钮的宽度。其实在Bootstrap中并不需要这样做，Bootstrap框架中提供了一个类名“btn-block”。按钮使用这个类名就可以让按钮充满整个容器，并且这个按钮不会有任何的padding和margin值。在实际当中，常把这种按钮称为块状按钮。

**css样式**

```javascript
.btn-block {
display: block;
width: 100%;
padding-right: 0;
padding-left: 0;
}
.btn-block + .btn-block {
margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
width: 100%;
}
```

**示例**

```javascript
<button class="btnbtn-primary btn-lg btn-block" type="button">大型按钮.btn-lg</button>
<button class="btnbtn-primary btn-block" type="button">正常按钮</button>
<button class="btnbtn-primary btn-sm btn-block" type="button">小型按钮.btn-sm</button>
<button class="btnbtn-primary btn-xs btn-block" type="button">超小型按钮.btn-xs</button>
```
![](https://ws3.sinaimg.cn/large/006tNbRwgy1fvuv09i3tjj30bj05mmxh.jpg)

### 按钮状态
#### 活动状态
> Bootstrap按钮的活动状态主要包括按钮的悬浮状态(:hover)，点击状态(:active)和焦点状态（:focus）几种。

**css样式**
```javascript
.btn:focus,
.btn:active:focus,
.btn.active:focus {
outline: thin dotted;
outline: 5px auto -webkit-focus-ring-color;
outline-offset: -2px;
}
.btn:hover,
.btn:focus {
color: #333;
text-decoration: none;
}
.btn:active,
.btn.active {
background-image: none;
outline: 0;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, .125);
box-shadow: inset 0 3px 5px rgba(0, 0, 0, .125);
}
```

+ 而且不同风格下的按钮都具有这几种状态效果，只是颜色做了一定的调整，我们以默认风格（btn-default）为例：

**css样式**

```javascript
.btn-default:hover,
.btn-default:focus,
.btn-default:active,
.btn-default.active,
.open .dropdown-toggle.btn-default {
color: #333;
background-color: #ebebeb;
border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open .dropdown-toggle.btn-default {
background-image: none;
}
```

#### 禁用状态
> 和input等表单控件一样，在Bootstrap框架的按钮中也具有禁用状态的设置。禁用状态与其他状态按钮相比，就是背景颜色的透明度做了一定的处理，opcity的值从100%调整为65%。

+ 在Bootstrap框架中，要禁用按钮有两种实现方式：
    + 方法1：在标签中添加disabled属性
    + 方法2：在元素标签中添加类名“disabled”

**两者之间的区别是**
> “.disabled”样式不会禁止按钮的默认行为，比如说提交和重置行为等。如果想要让这样的禁用按钮也能禁止按钮的默认行为，则需要通过JavaScript这样的语言来处理。对于<a>标签也存在类似问题，如果通过类名“.disable”来禁用按钮，其链接行为是无法禁止。而在元素标签中添加“disabled”属性的方法是可以禁止元素的默认行为的。

**示例**
```javascript
<button class="btnbtn-primary btn-lgbtn-block" type="button" disabled="disabled">通过disabled属性禁用按钮</button>
<button class="btnbtn-primary btn-block disabled" type="button">通过添加类名disabled禁用按钮</button>
<button class="btnbtn-primary btn-smbtn-block" type="button">未禁用的按钮</button>
```

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fvuvedgm1dj30bk04qq3d.jpg)

其他类型的按钮也有，只是相关颜色做了调整

## 图像
+ img-responsive：响应式图片，主要针对于响应式设计
+ img-rounded：圆角图片
+ img-circle：圆形图片
+ img-thumbnail：缩略图片

使用方法

```javascript
<img  alt="140x140" src="http://placehold.it/140x140">
<img  class="img-rounded" alt="140x140" src="http://placehold.it/140x140">
<img  class="img-circle" alt="140x140" src="http://placehold.it/140x140">
<img  class="img-thumbnail" alt="140x140" src="http://placehold.it/140x140">
<img  class="img-responsive" alt="140x140" src="http://placehold.it/140x140">
```

**css样式**

```javascript
img {
vertical-align: middle;
}
.img-responsive,
.thumbnail>img,
.thumbnail a >img,
.carousel-inner > .item >img,
.carousel-inner > .item > a >img {
display: block;
max-width: 100%;
height: auto;
}
.img-rounded {
border-radius: 6px;
}
.img-thumbnail {
display: inline-block;
max-width: 100%;
height: auto;
padding: 4px;
line-height: 1.42857143;
background-color: #fff;
border: 1px solid #ddd;
border-radius: 4px;
  -webkit-transition: all .2s ease-in-out;
transition: all .2s ease-in-out;
}
.img-circle {
border-radius: 50%;
}
```

设置图片大小
> 由于样式没有对图片做大小上的样式限制，所以在实际使用的时候，需要通过其他的方式来处理图片大小。比如说控制图片容器大小。（注意不可以通过css样式直接修改img图片的大小，这样操作就不响应了）

## 图标
> Bootstrap框架中的图标都是字体图标，其实现原理就是通过@font-face属性加载了字体。

```javascript
@font-face {
font-family: 'Glyphicons Halflings';
src: url('../fonts/glyphicons-halflings-regular.eot');
src: url('../fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../fonts/glyphicons-halflings-regular.woff') format('woff'), url('../fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
```
> 自定义完字体之后，需要对icon设置一个默认样式，在Bootstrap框架中是通过给元素添加“glyphicon”类名来实现，然后通过伪元素“:before”的“content”属性调取对应的icon编码：

在网页中使用图标也非常的简单，在任何内联元素上应用所对应的样式即可：


```javascript
<span class="glyphicon glyphicon-search"></span>
<span class="glyphicon glyphicon-asterisk"></span>
<span class="glyphicon glyphicon-plus"></span>
<span class="glyphicon glyphicon-cloud"></span>
```

所有名称查看
请点击 [http://getbootstrap.com/components/#glyphicons](http://getbootstrap.com/components/#glyphicons)链接查询

