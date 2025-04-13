---
layout: home
title: README
permalink: /
---

这是博客，本地只编写，github自动部署发布

- posts文件命名 必须以日期开头

1. 一个大项目，分为很多章节，但是一个md又很长， 可用使用collections 或者tags， categories
_posts 是默认的特殊合集：以时间组织
例如：_pages, _others
```yml
collections:
  pages:
    output: true
    permalink: /:collection/:path/
```

collections 适合管理严格结构和顺序的。
tags,categories 用来标记 不需要结构或顺序的

collections 要指定layout， 默认使用default