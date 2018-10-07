---
layout:     post
title:      JavaScript中setTimeout()用法总结
subtitle:   JavaScript学习笔记
date:       20018-3-8
author:     IAKGnaHz
header-img: img/post-bg-js-version.jpg
catalog: true
tags:
    - JavaScript
    
---

# 写在前面
最近才开始学习JavaScript和前端知识，这段时间就会将学习过程中遇到的一些问题和难以理解的地方记录在我的[博客网站](http://www.iakgnahz.top)上。作为最近这段时间学习的总结。
## setTimeout与setInterval的区别
>setTimeOut() 方法用于在指定的毫秒数后调用函数或计算表达式。
>
>setInterval() 方法可按照指定的周期（以毫秒计）来调用函数或计算表达式。
setInterval() 方法会不停地调用函数，直到 clearInterval() 被调用或窗口被关闭。由 setInterval() 返回的 ID 值可用作 clearInterval() 方法的参数。

从两个方法的定义中也可以看出，他们的功能是相类似的`在指定的毫米数后调用函数或者计算表达式`，但是也有很大的区别
#### setTimeout() 方法

##### 语法
>setTimeout(code,millisec)

|**参数**|**用法**|
|:--:|:--:|
|`code`|***必需。要调用的函数后要执行的 JavaScript 代码串。***|
|`millisec`|***必需。在执行代码前需等待的毫秒数。***|

##### 特点
>setTimeout() 只执行 code 一次。如果要多次调用，请使用 setInterval() 或者让 code 自身再次调用 setTimeout()。

##### 实例1.1

```javaScript  
<html>
<head>
<script type="text/javascript">
function timedMsg()
{
var t=setTimeout("alert('5 seconds!')",5000)
}
</script>
</head>

<body>
<form>
<input type="button" value="Display timed alertbox!"
onClick="timedMsg()">
</form>
<p>Click on the button above. An alert box will be
displayed after 5 seconds.</p>
</body>

</html>

```
👆上面的代码在运行之后会在网页5秒钟后弹出`5 seconds!`的字眼。

**👇接下来的代码像你演示使用setTimeout()通过自身调用setTimeout()来实现在网页上事实显示时间的功能**

##### 实例1.2
```javaScript
<html>
<head>
<script type="text/javascript">
function startTime()
{
var today=new Date()
var h=today.getHours()
var m=today.getMinutes()
var s=today.getSeconds()
// add a zero in front of numbers<10
m=checkTime(m)
s=checkTime(s)
document.getElementById('txt').innerHTML=h+":"+m+":"+s
t=setTimeout('startTime()',500)
}

function checkTime(i)
{
if (i<10) 
  {i="0" + i}
  return i
}
</script>
</head>

<body onload="startTime()">
<div id="txt"></div>
</body>
</html>
```

**通过以上的两个例子，应该对setTimeout()方法有了更好的理解了吧**，还可以参考以下资料[setTimeout()用法介绍](http://www.w3school.com.cn/jsref/met_win_settimeout.asp)

#### setInterval()方法

##### 语法
>setInterval(code,millisec[,"lang"])

|参数|描述|
|:----:|:----:|
|`code`|***必需。要调用的函数或要执行的代码串。***|
|`millisec`|***必须。周期性执行或调用 code 之间的时间间隔，以毫秒计。***|

##### 返回值
***一个可以传递给 Window.clearInterval() 从而取消对 code 的周期性执行的值。***

##### 实例2.1
```javaScript
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
👆运行上面的例子会在网页上生成一个实时显示时间的按钮，按钮的右边有一个可以暂停的按钮

![](https://ws4.sinaimg.cn/large/006tKfTcgy1fpgy0psiipj309j00z74b.jpg)
**实例2.1图**

#### clearTimeout()方法
##### 定义和用法
> clearTimeout() 方法可取消由 setTimeout() 方法设置的 timeout。

##### 语法
>clearTimeout(id_of_settimeout)

|参数|描述|
|:----:|:----:|
|`id_of_settimeout`|***由 setTimeout() 返回的 ID 值。该值标识要取消的延迟执行代码块***|

##### 实例3.1
***带有停止按钮的计时程序***👇
<html>
<head>
<script type="text/javascript">
var c=0
var t
function timedCount()
{
document.getElementById('txt').value=c
c=c+1
t=setTimeout("timedCount()",1000)
}

function stopCount()
{
clearTimeout(t)
}
</script>
</head>

<body>
<form>
<input type="button" value="开始计时！" onClick="timedCount()">
<input type="text" id="txt">
<input type="button" value="停止计时！" onClick="stopCount()">
</form>

<p>
请点击上面的“开始计时”按钮。输入框会从 0 开始一直进行计时。点击“停止计时”可停止计时。
</p>

</body>

</html>

```javascript

<html>
<head>
<script type="text/javascript">
var c=0
var t
function timedCount()
{
document.getElementById('txt').value=c
c=c+1
t=setTimeout("timedCount()",1000)
}

function stopCount()
{
clearTimeout(t)
}
</script>
</head>

<body>
<form>
<input type="button" value="开始计时！" onClick="timedCount()">
<input type="text" id="txt">
<input type="button" value="停止计时！" onClick="stopCount()">
</form>

<p>
请点击上面的“开始计时”按钮。输入框会从 0 开始一直进行计时。点击“停止计时”可停止计时。
</p>

</body>

</html>
```

# 总结
在运行和总结了以上实例后，明白了两种方法之间的区别和具体的使用。我发现通过博客记录学习生活中的问题是一种很好的锻炼与思考的过程，同时也锻炼了我的写作能力。希望自己能够继续加油，早日实现自己的理想。
这篇博文也是参照了网站[w3school.com](http://www.w3school.com.cn/index.html)的具体介绍。感谢。























