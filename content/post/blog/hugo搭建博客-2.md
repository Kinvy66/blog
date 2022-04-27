---
title: "Hugo搭建博客(二)--Stack主题配置"
description: "Hugo Stack 主题的详细配置"
date: 2022-04-27T19:42:09+08:00
image: https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/68747470733a2f2f692e696d6775722e636f6d2f634369484f47532e6a7067.jpg
math: 
hidden: false
comments: true
draft: true
categories: ["搭建博客"]
tags: ["Hugo"]
lastmod:
---



以下配置都是以 Stack 主题为例，其他主题可能不适用。



## 一、调整目录结构

在[hugo博客搭建(一)]() 已经把  `content` 文件夹和 `config.yaml` 文件复制到博客网站的根文件夹下了。

接下来需要对 `content` 的文件做些调整

1. 删除 `\post` 文件夹下的所有文件和文件夹

2. 删除 `\categories` 文件夹的所有文件和文件夹，并在 `\categories`  文件夹下创建一个 `index.md` 文件

   `index.md` 内容

   ```markdown
   ---
   title: "分类"
   date: 2022-04-27
   layout: "categories"
   slug: "categories"
   menu:
       main:
           weight: -90
           params: 
               icon: categories
   ---
   ```

3. 将 `\categories` 文件夹移动到 `\page` 文件夹下

4. 删除 `\links` 文件夹

最后`\content` 下的文件结构

```
.
├── _index.md     
├── page
│   ├── about   
│   │   └── index.md
│   ├── archives
│   │   └── index.md      
│   ├── categories        
│   │   └── index.md      
│   └── search
│       └── index.md      
└── post
```



在 `about` ，`archives` ，`search`，`categories`   文件夹下都有一个 `index.md` 文件，以 `categories`   下的为例

```markdown
---
title: "分类"
date: 2022-04-27
layout: "categories"
slug: "categories"
menu:
    main:
        weight: -90
        params: 
            icon: categories
---
```

部分属性说明

- `title` 左侧导航栏显示的文字，以及选中对应条目时网页标签的文字
- `date`  时间
- `weight` 权重， 左侧条目显示的顺序就是按权重的大小排列的
- `icon` 是图标，可用的图标在主题文件夹 `\assets\icons` 下

如果