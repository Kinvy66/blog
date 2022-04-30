---
title: "Hugo博客搭建(一)"
description: "使用Hugo搭建博客"
slug: "Hugo 1"
date: 2022-04-27T16:41:03+08:00
image: https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/hugo-logo-wide.svg
math: 
hidden: false
comments: true
draft: true
categories: ["博客搭建"]
tags: ["Hugo"]
lastmod:
---



[Hugo](https://gohugo.io/)是基于[Go](https://go.dev/)语言的静态博客框架



## 一、 软件安装

### 安装Go

Hugo 框架是基于Go，所以使用必须先安装Go的编译器

#### 下载安装Go

下载地址： https://go.dev/dl/

![image-20220427172133292](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427172133292.png)

官方提供了不同平台的不同版本，这里为了方便以后卸载，我们下载压缩包版本（免安装版）。下载后解压，将解压的整个文件夹放一个指定的路径下（最好不要有中文），我放的路径是 `C:\Env` 

**配置环境变量**

在`Path`环境添加go编译器的路径 `C:\Env\go\bin`



### 安装git

下载地址 https://git-scm.com/

安装配置参考 



### 安装Hugo

下载地址： https://github.com/gohugoio/hugo/releases

同样是下载对应平台的压缩包版本，下载 ==hugo_extended== 版， 因为有些主题的功能需要扩展版才支持。

下载后的压缩包解压指定的目录，我存放的目录同样是`C:\Env` 

**配置环境变量**

在`Path`环境添加Hugo的路径:  `C:\Env\hugo`

测试Hugo安装是否成功，打开 gitBash, 输入 `hugo version`, 出现版本信息

![image-20220427175141215](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427175141215.png)



## 二、新建Hugo网站

Hugo的使用在[官网](https://gohugo.io/) 和 [Hugo中文](https://www.gohugo.org/) 有详细的说明， 下面的建命令参考这两个网站的文档

在存放站点的文件夹下打开GitBash，不需要新建文件夹，执行下面的命令会新建一个 `blog` 的文件夹

```shell
$ hugo new site blog
```

`blog`是网站文件夹名，可以是任意其他的名称（不建议使用中文）

![image-20220427185109213](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427185109213.png)

进入`blog` 文件夹，下面这些文件是自动生成的

![image-20220427185217051](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427185217051.png)

## 三、配置主题

1. 打开 hugo theme 的网站，选择合适的主题，以Stack举例。 

   Hugo Themes: https://themes.gohugo.io

2. 下载主题

   ```shell
   # 进入网站目录 blog 
   $ cd blog 
   # 下载主题到 themes 文件夹下
   $ git clone https://github.com/CaiJimmy/hugo-theme-stack/ themes/hugo-theme-stack
   ```



3. 配置主题

   不同的主题的配置是不同，Hugo的主题官网不同主题对应的详情页面有相关的配置说明，这里以 Stack 为例

   主题文件夹中一般会有一个demo，直接用给的demo 站点的配置，之后再做一些修改。

   打开 `blog\themes\hugo-theme-stack\exampleSite` 复制 `content` 文件夹和 `config.yaml` 文件

   ![image-20220427190903140](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427190903140.png)

   先把 `\blog` 下的 `config.toml` 文件删除，再将复制的文件粘贴到 `\blog` 文件下， 如果有相同的文件，选择覆盖可以了。

   删除`\blog\content\post` 下的 `rich-content` 文件夹。这个只是针对 Stack 主题

   ![image-20220427191702714](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427191702714.png)

4. 启动网站

   执行下面命令，在浏览器打开  `http://localhost:1313/`

   ```shell
   $ hugo server -D
   ```

   ![image-20220427191954221](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427191954221.png)

   demo 效果

   ![image-20220427192215331](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20220427192215331.png)



## 四、新建文章

1. 进入网站文件夹 `\blog` ，打开GitBash

2. 新建文章, test.md

   ```shell
   $ hugo new post/test.md
   ```

   新建的文件在 `\blog\content\post`  下，直接用markdown的编辑器打开编写内容。



## 五、总结

使用Hugo搭建博客的整个流程还是比较简单，主要的还是后面的主题配置，不同的主题的配置修改都不同。

后面会另写一篇关于我现在使用的主题 Stack 的基本配置。



## 参考

- [Hugo中文文档 (gohugo.org)](https://www.gohugo.org/)
- [Quick Start | Hugo (gohugo.io)](https://gohugo.io/getting-started/quick-start/)

- [Hugo Stack 主题配置与使用 | Bore's Notes](https://bore.vip/archives/3bf3725e/#下载主题-amp-更新主题)
- [Github Pages + Hugo 搭建个人博客 - 渣渣的夏天 (zz2summer.github.io)](https://zz2summer.github.io/github-pages-hugo-搭建个人博客/#零效果)
