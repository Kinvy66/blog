---
title: "第5章  语句"
description: ""
date: 2021-12-02T13:42:48+08:00
image: https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/th_id=OHR.XmasBeachHuts_ZH-CN6195800613_1920x1080.jpg
math: 
license: 
hidden: false
comments: false
draft: true	
categories: ["cpp"]
tags: ["C++","Note"]
---


## 1. 简单语句

#### 表达式语句

表达式加上分号就是一条语句

```cpp
ival + 5;		//一条没有实际作用的表达式语句
cout << ival;	//一条有用的表达式语句
```



#### 空语句

一个分号 `;` 就是空语句

```cpp
;	//空语句
ival = v1 + v2;;	//第二分号是空语句，没有影响
while (iter != svec.end()) ;	//分号是空语句，导致下面的语句不会出现在循环中执行
	++iter;						//不属于循环体的一部分
```



> 空语句单独不会有什么作用，但是和其他语句组合会有不同的作用
>
> 注意：别漏写分号，也别多写分号





#### 复合语句