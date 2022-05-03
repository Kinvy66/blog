---
title: "第13章 拷贝控制 (C++ Primer 5th)"
slug: "Cpp Primer 5th Ch13"
description: 
date: 2022-05-02T18:42:06+08:00
image: 
math: 
hidden: true
comments: true
draft: true
categories: ["C++"]
tags: ["C++","笔记","C++ Primer 5th"]
lastmod:

---





## 1. 拷贝、赋值与销毁

拷贝、赋值和销毁对应的是类的拷贝构造函数、拷贝赋值运算符和析构函数，这三个是类的最基本操作。在任何情况下（没有使用 `delete`）这三个函数都是存在，没有自定义，编译器就会提供。



### 1.1 拷贝构造函数

如果一个构造函数的第一个参数是自身类类型的引用，且其他额外的参数都有默认值，则此构造函数是**拷贝构造函数**。

```cpp
class Foo {
public:
    Foo();		// 默认构造函数
    Foo(const Foo& );  // 拷贝构造函数
    // ...
};
```

拷贝函数的注意：

- 拷贝函数的第一个参数必须是引用类型
- 第一参数一般情况下都是定义为 `const`
- 拷贝函数会被隐式使用，所以拷贝函数通常不应该是 `explicit`



#### 合成拷贝构造函数

如果没有为一个类定义拷贝构造函数，编译器会生成一个默认的拷贝构造函数，叫做**合成拷贝构造函数**。 默认构造函数在我们定义了其他任意的构造函数编译器就不会在自动生成，但是合成拷贝构造函数不同，即使我们定义了构造函数（没有定义拷贝构造函数），编译器也会生成默认的拷贝构造函数。

以 `Sales_data` 为例，合成拷贝构造函数的操作就是进行简单的 <span style="color:red">值拷贝</span>，等价代码：

```cpp
class Sales_data {
public:
    // ...
    Sales_data(const Sales_data&);
private:
    std::string bookNo;
    int units_sold = 0;
    double revenue = 0.0;
};
Sales_data::Sales_data(const Sales_data &orig):
	bookNo(orig.bookNo),
	units_sold(orig.units_sold),
	revenue(orig.revenue)
    {  }
```

合成拷贝构造函数在大多数的情况下是可以满足需求的，比如 `Sales_data` 这样的类。但是在类的成员变量中有引用类型的变量（指针），那么合成拷贝构造函数会出现浅拷贝（后面会详细讲解）。



#### 拷贝初始化





