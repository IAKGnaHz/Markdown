---
layout:     post
title:      JavaScript面试题整理
subtitle:   数组
date:       2018-9-27
author:     IAKGnaHz
header-img: img/post-a.jpg
catalog: true
tags:
    - js面试题
    
---

# 数组篇
## 1.查找数组元素位置
> 找出元素 item 在给定数组 arr 中的位置
> 如果数组中存在 item ，则返回元素在数组中的位置，否则返回-1


```javascript
function indexOf(arr,item) {
			for (var i = 0; i < arr.length; i++) {
						if (arr[i]==item) {
							return i;
						} else {
						  return -1;
						}
					}		
				}
```

## 2.数组求和
> 计算给定数组 arr 中所有元素的总和
> 数组中的元素均为 Number 类型


```javascript
//计算数组内元素的和
		//
		//1.不考虑算法复杂度，用递归实现
		function sum(arr) {
			var len = arr.length;
			if (len == 0) {
				return 0;
			} else if (len == 1) {
				return arr[0];
			} else {
				return arr[0] + sum(arr.slice(1));
				//从已有的数组中返回选定的元素
			}
		}

		//2.常规循环
		function sum1(arr) {
			var s = 0;
			for (var i = 0; i < arr.length; i++) {
				s += arr[i];
			}
			return s;
		}

		//3.函数式编程 map-reduce
		//reduce()方法接收一个函数作为累加器，数组中的每个值（从左到右)开始缩减，最终计算为一个值
		function sum3(arr) {
			return arr.reduce(function (prev, curr, idx, arr) {
				return prev + curr;
			});
		}


		//4.eval
		//eval 方法用于计算某个字符串，并执行其中的javaScript代码
		//join 
		//把数组中的所有元素放入一个字符串中，通过指定分隔符进行分隔
		function sum4(arr) {
			return eval(arr.join("+"));
		}

```

+ `reduce()`方法解析 
    + [reduce()方法详解及高级技巧](https://segmentfault.com/a/1190000010731933)
+ `eval()` 方法
    + [W3school](http://www.w3school.com.cn/jsref/jsref_eval.asp)
+ `join()` 方法
    + [W3school](http://www.w3school.com.cn/jsref/jsref_join.asp)

## 3.移除数组中的元素
> 移除数组arr 中的所有值与item 相等的元素。不要直接修改 arr ，结果返回新的数组


```javascript
//移除数组中的元素
		//移除数组中与给定元素item 相等的元素,结果返回新的数组
		//1.push()方法
		function remove(arr, item) {
			var arr1 = [];
			arr.forEach(function (e) {
				if (e!=item) {
					arr1.push(e)
				};
			})
			return arr1;
		}
		

		//2.Array.prototype.filter()
		//filter()方法创建一个新的数组，新数组中的的元素师通过检查指定数组中符合条件的所有条件。不会改变原数组，不会对空数组进行检测
		function remove1(arr,item){
			return arr.filter(function (e) {
				return e != item;
			})
		}

```

+ `forEach()` 方法
    + [forEach()解析](http://www.runoob.com/jsref/jsref-foreach.html)
    + [原生JS forEach()和map()遍历的区别以及兼容写法](https://www.cnblogs.com/liuruyi/p/6483526.html)

## 4.移除数组中的元素
> 移除数组 arr 中的所有值与 item 相等的元素，直接在给定的 arr 数组上进行操作，并将结果返回


```javascript
function removeWithoutCopy(arr, item) {
			for (var i = 0; i < arr.length; i++) {
				if (item == arr[i]) {
					arr.splice(i,1);
					i--;
				}
			}
			return arr;
		}

// 		splice(index,len,[item])    注释：该方法会改变原始数组。
// splice有3个参数，它也可以用来替换/删除/添加数组内某一个或者几个值
// index:数组开始下标        len: 替换/删除的长度       item:替换的值，删除操作的话 item为空
// 如：arr = ['a','b','c','d']

// 删除 ----  item不设置
// arr.splice(1,1)   //['a','c','d']         删除起始下标为1，长度为1的一个值，len设置的1，如果为0，则数组不变
// arr.splice(1,2)  //['a','d']          删除起始下标为1，长度为2的一个值，len设置的2

// 替换 ---- item为替换的值
// arr.splice(1,1,'ttt')        //['a','ttt','c','d']         替换起始下标为1，长度为1的一个值为‘ttt’，len设置的1
// arr.splice(1,2,'ttt')        //['a','ttt','d']         替换起始下标为1，长度为2的两个值为‘ttt’，len设置的1

// 添加 ----  len设置为0，item为添加的值
// arr.splice(1,0,'ttt')        //['a','ttt','b','c','d']         表示在下标为1处添加一项‘ttt’

// 看来还是splice最方便啦

```

## 5.添加元素
> 在数组 arr 末尾添加元素 item。不要直接修改数组 arr，结果返回新的数组


```javascript
//1.普通的代码拷贝
	function append(arr, item) {
		var len = arr.length;
		var arr1 = arr;
		arr1[len] = item;
		return arr1;
	}

	//2.使用slice()浅拷贝+ push 组合
	function append2(arr, item) {
		var newArr = arr.slice(0); //slice(start, end)浅拷贝数组
		newArr.push(item);
		return newArr;
	}


	//3.使用concat将传入的数组与或非数组值与原数组合并，组成新的数组返回
	function append3(arr, item) {
		return arr.concat(item);
	}

```

+ `slice()` 方法
    + [W3school](http://www.w3school.com.cn/jsref/jsref_slice_array.asp)