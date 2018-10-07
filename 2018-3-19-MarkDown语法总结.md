---
layout:     post
title:      MarkDown
subtitle:   MarkDown-语法总结
date:       20018-3-19
author:     IAKGnaHz
header-img: img/post-bg-debug.png
catalog: true
tags:
    - MarkDown语法
    
---

<head> 
    <script defer src="https://use.fontawesome.com/releases/v5.0.13/js/all.js"></script> 
    <script defer src="https://use.fontawesome.com/releases/v5.0.13/js/v4-shims.js"></script> 
</head> 
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.0.13/css/all.css">



#  写在前面 
> <i class="fas fa-quote-left fa-3x fa-pull-left"></i>  Markdown 语法的目标是：成为一种适用于网络的书写语言。

>Markdown 不是想要取代 HTML，甚至也没有要和它相近，它的语法种类很少，只对应 HTML 标记的一小部分。Markdown 的构想不是要使得 HTML 文档更容易书写。在我看来， HTML 已经很容易写了。Markdown 的理念是，能让文档更容易读、写和随意改。HTML 是一种发布的格式，Markdown 是一种书写的格式。就这样，Markdown 的格式语法只涵盖纯文本可以涵盖的范围。

>不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。不需要额外标注这是 HTML 或是 Markdown；只要直接加标签就可以了.

我也是去年才开始接触和使用**markdown**这种书写语言的。之前开通了公众号，在**pages**上写东西怎么都感觉不太舒服，可能是因为功能太多了。后来搭建了博客网站，接触到了**markdown**书写语言，觉得终于遇到了知己的感觉。最近想在博客上多写一点东西，使用**markdown**就更加频繁了。最近学习了**html:**前端web开发中最基础的标记语言后，发现之间还是有很多的联系的。今天就来总结一下**markdown**的语法（平时写文章的时候经常忘记！）

## MarkDown语法总结
### 标题
markdown的标题可以采取两种写法

#### Setext类写法：利用`=`和`-`表示

```
	这是一级标题
	==========
	这是二级标题
	----------
```
#### atx类写法：在行首插入1~6个`#`表示从一级到六级标题

```
	# 这是一级标题
	## 这是二级标题
	### 这是三级标题
	####	....
```
 
### 区块引用
引用一段文字可以使用`>`符号

```
	> 这是一段引用。具体效果如下:
```
> 伟大的成绩和辛勤劳动是成正比例的，有一分劳动就有一分收获，日积月累，从少到多，奇迹就可以创造出来。 —— 鲁迅

***引用允许在一段文字中只需在第一行加上`>`标志即可。***

#### 引用可以嵌套使用

```
	> 这是一级引用
	> >这是二级引用
	> > >这是三级引用
	> 效果如下	
```

> 这是一级引用
> >这是二级引用
> > >这是三级引用


### 列表
MarkDown支持有序列表和无序列表

#### 无序列表
***无序列表使用星号、加号或是减号作为列表标记：***

```
	* 列表一
	+ 列表二
	- 列表三
```
* 列表一
+ 列表二
- 列表三

#### 有序列表
***有序列表则使用数字接着一个英文句点：***

```
	1.列表一
	2.列表二
	3.列表三
```
#### 列表的嵌套

``` 
* grFather
* grMother
	* Father
	* Mother
		* You
		* You Wife
```
* grFather
* grMother
	* Father
	* Mother
		* You
		* You Wife


### 链接

#### 链接样式

`[链接文字](网页链接)`

```
	[张凯的博客网站](http://www.iakgnahz.top)
	[苹果的官方网站] (https://www.apple.com/cn/)
	[张凯的github主页](https://github.com/IAKGnaHz)
```


[张凯的博客网站](http://www.iakgnahz.top)
[苹果的官方网站] (https://www.apple.com/cn/)
[张凯的github主页](https://github.com/IAKGnaHz)
**注意⚠️**`()`**括号一定使用英文输入法下的括号**



### 强调
#### 强调样式
`**在两个星号之间加上强调的内容**`

**强调内容会使用加粗的字体**

### 斜体
#### 斜体样式
`***在三个星号之间加上斜体的内容***`

***这是斜体的字样，也会使用加粗的字体***
### 代码
#### 标记代码行
使用``` ` ```使用反引号标记代码区域如下演示

```
	` javaScript`
```

`javaScript`

#### 标记代码段
```
	```javascript
<html>
<body>

<input type="text" id="clock" size="35" />
<script language=javascript>
var int=self.setInterval("clock()",50)
function clock()
  {
  var t=new Date()
  document.getElementById("clock").value=t
  }
</script>
</form>
<button onclick="int=window.clearInterval(int)">
Stop interval</button>

</body>
</html>
	```
```
***在三个反引号之间插入代码段***

```javascript
<html>
<body>

<input type="text" id="clock" size="35" />
<script language=javascript>
var int=self.setInterval("clock()",50)
function clock()
  {
  var t=new Date()
  document.getElementById("clock").value=t
  }
</script>
</form>
<button onclick="int=window.clearInterval(int)">
Stop interval</button>

</body>
</html>
```


### 图片
#### 图片标记样式

```
	![图片名称]（图片链接）
	例如:
	![斯嘉丽约翰逊](https://ws3.sinaimg.cnlarge006tKfTcgy1fl1tufiaw5j313g0powwi.jpg)
```
![斯嘉丽约翰逊](https://ws3.sinaimg.cn/large/006tKfTcgy1fl1tufiaw5j313g0powwi.jpg)

### 自动链接
#### 自动链接样式
```
	<在方括号之间插入链接即可>
	例如：张凯的博客<http://iakgnahz.top>
	张凯的邮箱<iakgnahz1@gmail.com>
```
张凯的博客<http://iakgnahz.top>
张凯的邮箱<iakgnahz1@gmail.com>
# 总结

希望这篇文章能够对大家有所帮助，其实网上也有很多相似的总结，但是自己总结一遍的话会对markdown更加熟悉的。更加详细的介绍可以看这里[MarkDown-语法说明](http://www.markdown.cn).感谢。