---
title: "第1章 开始(C++ Primer 5th)"
date: 2022-04-27
lastmod: 2022-06-04
author: ["Kinvy"]
keywords: 
- 
categories: ["C++"]
tags: ["C++","C++ Primer 5th"]
description: "第一章是C++的概览"
hideSummary: false
weight:
slug: "CPP Primer 5th Ch1"
draft: false 
comments: true
reward: false 
mermaid: true 
showToc: true 
TocOpen: true 
hidemeta: false 
disableShare: true 
showbreadcrumbs: true 
hidden: true
cover:
    image: https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/2021-12-25.jpg 
    caption: "" 
    alt: ""
---






本章以一个实际问题，书店问题，来简单的介绍C++的基本特性。这个问题的代码将贯彻整本书，后面的章节会逐一讲解代码中涉及到的 C++ 语言特性。

这个问题具体，就是要保存书店的所有销售记录的档案，每条记录保存了某本书的一次销售信息，包含三个数据：

```
0-201-70353-X	4	24.99
```

它们分别是书的 ISBN，售出的册数，书的单价。有时，书店老板需要查询此档案，计算每本书的销售量、销售额及平均售价。

这个问题会涉及到的有：

- 定义变量
- 进行输入和输出
- 使用数据结构保存数据
- 检测两条数据是否有相同的 ISBN
- 包含一个循环来处理销售档案中的每条记录

我们首先介绍如何使用 C++ 来解决这些子问题，然后编写书店程序。

## 1. 一个简单的C++程序

从一个简单的C++程序开始

```c++
int main()
{
    return 0;
}
```

由这个程序简单的介绍了函数的定义。函数定义包含四部分：**返回类型** 、**函数名** 、一个阔话包围的**形参列表** （允许为空） 以及 **函数体** 。`main` 是一个比较特殊的函数，但其定义与其他函数是一样的。

简单的介绍了c++程序在不同的平台编译运行的方式。



### 1.1 编译、运行程序





## 2. 初始输入和输出

c++的输入和输出 `cin` `cout` 以及对应的运算符 `<<` `>>`

```c++
std::cout << "hello" << std::endl;
std::cin >> val;
```



## 3. 注释

c++的注释两种：

```c++
//注释1
std::cout << "hello" << std::endl;
/*
注释2
*/
std::cin >> val;
```



## 4. 控制流

循环和判断语句

### 4.1 while



### 4.2  for



### 4.3 if



### 一个示例

读取一串数据并统计每个数字出现的次数 ，windows下的终止键 `ctrl` + `z` 

```c++
#include <iostream>
using namespace std;
int main()
{
	int currVal = 0, val = 0;
	if (cin >> currVal) {
		int cnt = 1;
		while (cin >> val) {
			if (val == currVal) {
				++cnt;
			}
			else {
				cout << currVal << " occurs "
					<< cnt << " times" << endl;
				currVal = val;
				cnt = 1;
			}
		}
		cout << currVal << " occurs "
			<< cnt << " times" << endl;
	}
	system("pause");
	return 0;
}
```



## 5. 类的简介

用书店的示例简单的介绍了类，这里使用的类 `Sales——item` 是已经写好的，所以应该说这小节是使用类。

类就是一种数据类型，叫做 `类类型` ，它和我们使用的普通数据类型一样，同样有 `+`, `-`, `*` , `/` 等基本运算，甚至还有 `>>` 和　`<<` ，这些运算符都是通过 `重载运算符` 操作实现的。不过在这里好像并没有提及运算符的重载。







