---
title: "git实例"
date: 2020-10-29T14:47:59+08:00
draft: false
tags: ["git"]
categories: ["CookBook"]
author: Losa
---

git 命令使用实例

<!--more-->

[官方网站](https://git-scm.com/book/zh/v2/)

##### 取消跟踪文件或目录

```shell
# 清理cache
git rm -r --cached fileName/folderName
# 取消index
git update-index --assume-unchanged fileName/folderName
# .gitignore 忽略指定文件
```

