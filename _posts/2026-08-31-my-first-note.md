---
layout: post
title: "我的第一篇学习笔记"
date: 2026-08-31
categories: [Web-security]
tags: [Web攻击, Git]
---

## 今天学习了什么

今天搭建了自己的 GitHub Blog。

## 知识点

- GitHub Pages 可以托管静态网站
- Jekyll 可以把 Markdown 转换成博客文章
- `_posts` 文件夹用于存放文章

## 总结

以后可以继续在这里记录学习过程。

{% if page.tags %}
<p>
  标签：
  {% for tag in page.tags %}
    <a href="{{ '/tags/' | relative_url }}#{{ tag | uri_escape }}">
      #{{ tag }}
    </a>
  {% endfor %}
</p>
{% endif %}
