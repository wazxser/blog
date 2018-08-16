---
title: Hexo博客添加搜索功能
date: 2018-08-16 20:13:10
tags:
  - hexo
categories:
  - 博客
---
为自己的博客添加搜索功能。

# local_search
* 安装hexo-generator-searchdb模块，在博客的根目录下执行以下命令：
``` python
npm install hexo-generator-searchdb --save
```
* 在站点配置文件中加入如下内容：
``` python
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```
* 在主题配置文件中开启local_search功能：
``` python
local_search:
  enable: true
```
# algolia_search
[官方教程](http://theme-next.iissnan.com/third-party-services.html#algolia-search)
