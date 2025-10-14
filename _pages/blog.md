---
layout: blog       # 或者你自定义的布局
title: Blog
permalink: /blog/
---
# 博客列表

<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%Y-%m-%d" }}
  </li>
{% endfor %}
</ul>
