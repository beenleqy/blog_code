---
next/title: Hexo+Next博客搭建
categories: 
           - Hexo
tags:
           - 工具
---
#### 环境准备

node：  [node官网](https://nodejs.org/en/)

github账号：  [github](https://github.com/)

```
Hexo v4.2.1    Next v7.5.0
```
 <!-- more -->

#### 安装Hexo

``` bash
$ npm install -g hexo-cli

// 创建blog文件

$ hexo init
$ npm install

$ hexo server //启动
```

```yml
#blog/_config.yml文件
# Site
title: ''       # 博客标题
subtitle: ''    # 博客副标题
description: '' # 博客描述
keywords:       # 关键字
author: qy      # 作者
language: zh-CN # 语言
```



#### Next主题

 [next官网下载](https://github.com/theme-next/hexo-theme-next/releases)

```bash
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

```yml
#blog/_config.yml文件

# Schemes
#scheme: Muse
scheme: Pisces

menu:
  home: / || home   #主页
  tags: /tags/ || tags   #标签
  categories: /categories/ || th  #分类
  archives: /archives/ || archive  #归档
```

```bash
// 新建tags文件
$ hexo new page "tags"
// tags/index.md
 + type: tags
// 新写的blog
  next/title: Hexo+Next博客搭建
 +tags:
           - 博客

// 新建categories文件
$ hexo new page "categories"
// categories/index.md
 + type: categories
// 新写的blog
  next/title: Hexo+Next博客搭建
 +categories:
           - Hexo
```

```yml
#themes/next/_config.yml文件

# Extensions
theme: next
```

```bash
//切换后，用命令清除下缓存
$ hexo clean

//执行hexo s本地产看NexT主题效果
$ hexo server
```



##### 其他优化

**点击头像进入首页**

```swig
// blog\themes\next\layout\_partials\sidebar\site-overview.swig
+ <a href="/">
    <img class="site-author-image" itemprop="image"
       src="{{ url_for( theme.avatar.url | default(theme.images + '/avatar.gif') ) }}"
       alt="{{ author }}" />
+ </a>
```



**blog右上角显示github图标**

在[这里](http://tholman.com/github-corners/)(图片版)或[这里](https://github.com/blog/273-github-ribbons)(文字版)选择一款自己喜欢的图标，拷贝代码

```swig
// blog\themes\next\layout\_layout.swig
<div class="headband"></div>
// 选中图标置于此处。。。
```



#### 部署

``` yml
#_config.yml文件下，deploy配置
deploy:
  type: git
  repo: https://github.com/username/username.github.io.git
  branch: master
```

安装部署工具

```bash
$ npm install hexo-deployer-git --save

// 新建blog
$ hexo new 文件名

$ hexo g //生成网页文件
$ hexo s //localhost:4000本地预览效果
$ hexo d //部署

//访问：https://username.github.io/
```