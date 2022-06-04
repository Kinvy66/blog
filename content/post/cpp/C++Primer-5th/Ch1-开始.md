---
title: "第1章 开始(C++ Primer 5th)"
description: "第一章是C++的概览"
slug: "CPP Primer 5th Ch1"
date: 2022-04-27
image: https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/2021-12-25.jpg
math: 
license: 
hidden: false
comments: true
draft: true	
categories: ["CPP"]
tags: ["CPP","笔记","C++ Primer 5th"]
lastmod: 2022-06-04
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

![image-20220604174737974](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220604174737974.png)

上图是一个 C 程序（C++ 程序类似）的编译过程，可供参考。

更详细参考：[【6】【Cherno C++】【中字】C++编译器是如何工作的](https://www.bilibili.com/video/BV1er4y1c7nj/?spm_id_from=333.788)



## 2. 初始输入和输出

在C++语言中并未定义任何输入输出（IO）语句，取而代之，包含了一个一个全面的标准库来提供 IO 机制。当然，我们也可可以使用 C 语言中的 `printf` ，C++ 是兼容 C 的，但是并不建议，所以本书中的示例都是使用标准库中提供的 `iostream` 库。`iostream` 库包含两个基础类型 `istream` 和 `ostream` ，分别表示输入流和输出流。

#### 标准输入输出对象

标准库定义类4个 IO 对象。输入， 使用一个名为 `cin` 的 `istream`  类型的对象。 输出，使用一个名为 `cout` 的 `ostream` 类型的对象。标准库还定义了其他两个 `ostream` 对象，名为 `cerr` 和 `clog` 。 

#### 一个使用 IO 库的程序

```cpp
#include <iostream>
int main()
{
    std::cout << "Enter two numbers:" << std::endl;
    int v1 = 0, v2 = 0;
    std::cin >> v1 >> v2;
    std::cout << "The sum of " << v1 << " and " << v2
              << " is " << v1 + v2 << std::endl;
    return 0;
}
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

示例： 求 1 到 10 的和

```cpp
#include <iostream>
int main()
{
    int sum = 0, val = 0;
    while (val <= 10)
    {
        sum += val;
        ++val;
    }
    std::cout << "Sum of 1 to 10 inclusive is "
              << sum << std::endl;
    return 0;
}
```



### 4.2  for

`for` 循环， 将上面 `while` 循环改成  `for`

```cpp
#include <iostream>
int main()
{
    int sum = 0; 
	for (int val = 1; val <= 10; ++val)
        sum += val;
    std::cout << "Sum of 1 to 10 inclusive is "
              << sum << std::endl;
    
    return 0;
    
}
```



### 4.3 读取数量不定的输入数据

```cpp
#include <iostream>
int main()
{
    int sum = 0, val = 0;
    while (std::cin >> val)
        sum += val;
    std::cout << "Sum  is " << sum << std::endl;
    return 0;
}
```

上面程序在输入结束后除了按回车键，还需要按**结束符** 

>在Windows 系统中输入结束符是按 `Ctrl + Z`
>
>在 UNIX系统中，包括 Mac OS X 系统中，文件结束符输入用 `Ctrl + D`



###   4.3 if

示例

```cpp
#include <iostream>
int main() 
{
    // currVal是我们正在统计的数，我们将读入的新值存入val
    int currVal = 0, val = 0;
    // 读取第一个数，并确保确实有数据可以处理
    if(std::cin >> currVal) {
        int cnt = 1;
        while(std::cin >> val) {
            if(val == currVal) {
                ++cnt;
            }
            else {
                std::cout << currVal << " occurs " 
                          << cnt << " times " << std::endl;
                currVal = val;
                cnt = 1;
            }
        }
        std::cout << currVal << " occurs " 
                  << cnt << " times " << std::endl;
    }

    return 0;
}
```



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







