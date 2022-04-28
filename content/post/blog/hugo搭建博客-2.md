---
title: "Hugo搭建博客(二)--Stack主题配置"
description: "Hugo Stack 主题的详细配置"
date: 2022-04-27T19:42:09+08:00
image: https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/68747470733a2f2f692e696d6775722e636f6d2f634369484f47532e6a7067.jpg
math: 
hidden: false
comments: true
draft: true
categories: ["博客搭建"]
tags: ["Hugo"]
lastmod: 2022-04-28
---



以下配置都是以 Stack 主题为例，其他主题可能不适用。



## 一、调整目录结构

在[hugo博客搭建(一)](http://kinvy.cn/p/hugo博客搭建一/) 已经把  `content` 文件夹和 `config.yaml` 文件复制到博客网站的根文件夹下了。

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

5. 如果目录下有 `index.zh-cn.md` 和 `index.md` ，将 `index.md` 删除， `index.zh-cn.md` 重命名为 `index.md`

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



## 二、配置文件

`\blog` 文件夹下的 `config.yaml` 文件是需要修改的配置文件

所有的配置说明，以及改动



###  1. 网站主要信息

```yaml
baseurl: https://example.com   # 网站的 url 
languageCode: zh-cn   # 网站的语言，改为中文  
theme: hugo-theme-stack
paginate: 5
title: Example Site   # 浏览器标签，头像下面，页脚显示的名称
```



### 2. 网站语言设定

```yaml
# 只用中文，可以把下面全部注释
# languages:
#     en:
#         languageName: English
#         title: Example Site
#         weight: 1
#     zh-cn:
#         languageName: 中文
#         title: 演示站点
#         weight: 2
#     ar:
#         languageName: عربي
#         languagedirection: rtl
#         title: موقع تجريبي
#         weight: 3

# Change it to your Disqus shortname before using
disqusShortname: hugo-theme-stack   # 评论系统名称，下面有主题支持的评论系统

# GA Tracking ID
googleAnalytics:

# Theme i18n support
# Available values: ar, ca, de, el, en, es, fr, id, it, ja, ko, nl, pt-br, th, uk, zh-cn, zh-hk, zh-tw
DefaultContentLanguage: zh-cn  # 默认语言改为中文

# Set hasCJKLanguage to true if DefaultContentLanguage is in [zh-cn ja ko]
# This will make .Summary and .WordCount behave correctly for CJK languages.
hasCJKLanguage: true   # 改为 true

permalinks:
    post: /p/:slug/
    page: /:slug/
```



### 3. 各个页面参数设定

```yaml
params:
    mainSections:
        - post  # 主页面存放的路径
    featuredImageField: image
    rssFullContent: true
    favicon:    # 网站标签的图标，

    footer:
        since: 2022   # 页脚信息
        customText:	

    dateFormat:
        published: 2006-01-02  # 文章发布日期的格式
        lastUpdated: 2006-01-02T  # 文章更新日期的格式

	# 侧边栏设置
    sidebar:	
        emoji: 🍥  # 头像的emoji， 不显示留空即可
        subtitle: Lorem ipsum dolor sit amet, consectetur adipiscing elit. # 头像下的简介
        avatar:
            enabled: true   # 是否使用头像
            local: true		# 是否使用本地的图片作为头像
            src: img/avatar.png	# 头像文件路径 
	
	# 文章页面设置
    article:
        math: false  # 是否支持 KaTex 数学公式
        toc: true	 # 是否显示目录
        readingTime: true	# 是否显示阅读时间
        # 文章许可
        license:		
            enabled: true
            default: Licensed under CC BY-NC-SA 4.0

```



### 4. 评论系统

```yaml
	# 评论系统配置
    comments:
        enabled: true # 是否启用评论系统
        provider: disqus # 使用的评论系统名称
        
		# 支持的评论系统
        disqusjs:
            shortname:
            apiUrl:
            apiKey:
            admin:
            adminLabel:

        utterances:
            repo:
            issueTerm: pathname
            label:

        remark42:
            host:
            site:
            locale:

        vssue:
            platform:
            owner:
            repo:
            clientId:
            clientSecret:
            autoCreateIssue: false

        # Waline client configuration see: https://waline.js.org/en/reference/client.html
        waline:
            serverURL:
            lang:
            visitor:
            avatar:
            emoji:
                - https://cdn.jsdelivr.net/gh/walinejs/emojis/weibo
            requiredMeta:
                - name
                - email
                - url
            placeholder:
            locale:
                admin: Admin

        twikoo:
            envId:
            region:
            path:
            lang:

        # See https://cactus.chat/docs/reference/web-client/#configuration for description of the various options
        cactus:
            defaultHomeserverUrl: "https://matrix.cactus.chat:8448"
            serverName: "cactus.chat"
            siteName: "" # You must insert a unique identifier here matching the one you registered (See https://cactus.chat/docs/getting-started/quick-start/#register-your-site)

        giscus:
            repo:
            repoID:
            category:
            categoryID:
            mapping:
            lightTheme:
            darkTheme:
            reactionsEnabled: 1
            emitMetadata: 0

        gitalk:
            owner:
            admin:
            repo:
            clientID:
            clientSecret:

        cusdis:
            host:
            id:

```



### 5. 右侧导航栏内容

```yaml
    widgets:
    	# 主页面导航栏显示的内
        homepage:
            - type: search	 # 搜索
            - type: archives # 归档	
              params:
                  limit: 5  # 显示的数量
            - type: categories # 分类
              params:
                  limit: 10
            - type: tag-cloud  # 标签云
              params:
                  limit: 10
        # 子页面导航栏显示的内容
        page:
            - type: toc   # 在文章页面显示目录

    opengraph:
        twitter:
            # Your Twitter username
            site:

            # Available values: summary, summary_large_image
            card: summary_large_image

    defaultImage:
        opengraph:
            enabled: false
            local: false
            src:

    colorScheme:
        # Display toggle
        toggle: true

        # Available values: auto, light, dark
        default: auto

    imageProcessing:
        cover:
            enabled: true
        content:
            enabled: true




```



### 6. 自定义左侧导航栏

```yaml
### Custom menu
### See https://docs.stack.jimmycai.com/configuration/custom-menu.html
### To remove about, archive and search page menu item, remove `menu` field from their FrontMatter
# 自定义左侧导航栏， 已在相关页面的 FrontMatter 设置了
menu:
    main: []
   
    # 显示的社交
    social:
        - identifier: github
          name: GitHub
          url: https://github.com/CaiJimmy/hugo-theme-stack
          params:
              icon: brand-github

        - identifier: twitter
          name: Twitter
          url: https://twitter.com
          params:
              icon: brand-twitter
```





### 7. 其他

```yaml

related:
    includeNewer: true
    threshold: 60
    toLower: false
    indices:
        - name: tags
          weight: 100

        - name: categories
          weight: 200

markup:
    goldmark:
        renderer:
            ## Set to true if you have HTML content inside Markdown
            unsafe: false
    tableOfContents:
        endLevel: 4    # 目录显示的最小标题
        ordered: false	# 目录的标题是否加上对应的序号
        startLevel: 2  # 目录显示的开始标题
    highlight:
        noClasses: false
        codeFences: true
        guessSyntax: true
        lineNoStart: 1
        lineNos: true
        lineNumbersInTable: true
        tabWidth: 4
```



>以上这些只是基本的配置

我的博客工程git仓库（仅供参考）： [Kinvy66/blog (github.com)](https://github.com/Kinvy66/blog)

## 参考

[1] [介绍 | Hugo 主题 Stack (jimmycai.com)](https://docs.stack.jimmycai.com/zh/)

[2] [Hugo Stack 主题配置与使用 | Bore's Notes](https://bore.vip/archives/3bf3725e/#删除相关文章图片)