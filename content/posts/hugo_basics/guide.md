---
title: "Guide"
date: 2020-10-27T15:46:23+08:00
draft: false
author: "Losa"
description: "Hugo基础操作 主题配置"
featuredImage: "/hugo_basics/featured-image.png"
tags: ["Markdown", "Hugo"]
categories: ["Cookbook"]
lightgallery: true
---

<!--more-->

### Create site

* hugo new site xxx

### Wrtite article

* hugo new XXX/xxx.md

### Preview

* hugo server  [本地预览](localhost:1313)

### Deploy

* hugo 更新public
* git push 文件夹public下内容

### Theme

#### LoveIt

* [LoveIt Demo Site](https://hugoloveit.com)

* folder
  * 保持博客文章存放在 `content/posts` 目录，例如： `content/posts/我的第一篇文章.md`
  * 保持简单的静态页面存放在 `content` 目录，例如： `content/about.md`
  * 保持图片之类的媒体资源存放在 `static` 目录，例如： `static/images/2019/9/screenshot.png`

* summary
  * 如果文章中有 `<!--more-->` 摘要分隔符, 但分隔符之前没有内容, 则使用描述作为摘要.
  * 如果文章中有 `<!--more-->` 摘要分隔符, 则将按照手动摘要拆分的方法获得摘要.
  * 如果文章前置参数中有摘要变量, 那么将以该值作为摘要.
  * 按照自动摘要拆分方法.

### Template



