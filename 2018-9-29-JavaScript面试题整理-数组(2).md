---
layout:     post
title:      JavaScript面试题整理
subtitle:   数组(二)
date:       2018-9-29
author:     IAKGnaHz
header-img: img/post-a.jpg
catalog: true
tags:
    - js面试题
    
---


# 数组
## 删除数组最后一个元素
> 删除数组`arr` 最后一个元素。不要直接修改数组arr，结果返回新的数组

```javascript
	// 1.splice方法删除数组中最后一个元素
	function truncate(arr) {
		var newArr = [];
		index = arr.length;
		arr.splice(index-1,1);
		var a = arr.slice(0); //slice拷贝
		return newArr;
	}

	//2.pop 弹出数组中最后一个元素
	function truncate_demo2(arr) {
		var newArr = [];
		var a = arr.slice(0); //slice拷贝
		newArr.pop();       //pop弹出
		return newArr;
	}

	//3.利用slice
	function truncate_demo3(ar) {
		return arr.slice(0,-1);
	}


	//4.利用filter
	function truncate_demo4(arr) {
		// body...
		return arr.filter(function (v,i,ar) {
			return i != ar.length-1;
		});
	}

  //5.利用concat+pop
	function truncate_demo5(arr) {
		// body...
		var newArr = arr.concat();
		newArr.pop();
		return newArr;
	}
```

## 添加元素
> 在数组 arr 开头添加元素 item。不要直接修改数组 arr，结果返回新的数组

```javascript
//1.unshift 在数组的开头添加元素
	function prepend_demo1(arr, item) {
		// body...
		var newArr = arr.slice(0);
		newArr.unshift(item);
		return newArr;
	}


	//2.concat将两个数组连接起来
	function prepend_demo2(arr, item) {
		// body...
		var newArr =[];
		newArr[0] = item;
		return newArr.concat(arr);
	}


	//3.concat()连接item
	function prepend_demo3(arr, item) {
		// body...
		return [item].concat(arr);
	}
```

## 删除数组第一个元素
> 删除数组 arr 第一个元素。不要直接修改数组 arr，结果返回新的数组


```javascript
//1.shift 弹出第一个元素
	function curtail_demo1(arr) {
		// body...
		var newArr = [];
		newArr = arr.slice(0);
		newArr.shift();
		return newArr;
	}

	//2.常规遍历
	function curtail_demo2(arr) {
		// body...
		var newArr = [];
		for (var i = 1; i < arr.length; i++) {
			newArr.push(arr[i]);
		}
		return newArr;
	}

	//3.slice复制 从第二个元素开始复制
	function curtail_demo3(arr) {
		// body...
		return arr.slice(1);
	}

	//4.filter
	function curtail_demo4(arr) {
		// body...
		return arr.filter(function (v, i) {
			return i != 0;
		});
	}

```

## 数组合并
> 合并数组 arr1 和数组 arr2。不要直接修改数组 arr，结果返回新的数组


```javascript
//1.push推入数组返回
	function concat_demo1(arr1, arr2) {
		// body...
		for (var i = 0; i < arr2.length; i++) {
			arr1.push(arr2[i]);
		}
		return arr1;
	}

	//2.利用concat
	function concat_demo2(arr1, arr2) {
		return arr1.concat(arr2);
	}

	//3.利用slice 和push.apply
	function concat_demo3(arr1, arr2) {
		// body...
		var newArr = arr1.slice(0);
		[].push.apply(newArr, arr2);
		return newArr;
	}

```

## 添加元素
> 在数组的arr的index处添加元素item 返回新的数组

```javascript
	//1.slice分别复制数组的两个部分
	function insert_demo1(arr, item, index) {
		// body...
		var newArr = arr.slice(0,index);
		newArr.push(item);
		var anothArr = arr.slice(index);
		return newArr.concat(anothArr);
	}


	// 2.splice方法，方法可接收多个参数。
	//第一个参数表示数组起始位置，
	//第二个参数表示需要删除元素的个数，如果后面还有参数，
	//则将随后的全部参数插入到第一个参数表示的起始位置。
	
	function insert_demo2(arr, item, index) {
		// body...
		var newArr = arr.slice(0);
		newArr.splice(index, 0, item);
		return newArr;
	}
```