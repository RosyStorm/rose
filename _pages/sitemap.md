---
layout: archive
title: "站点地图"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

本站所有页面与文章的索引。机器人可以读取 [XML 版本]({{ base_path }}/sitemap.xml)。

## 页面

{% for post in site.pages %}
  {% unless post.sitemap == false %}
    - [{{ post.title }}]({{ post.url | relative_url }})
  {% endunless %}
{% endfor %}

## 文章

{% for post in site.posts %}
  - [{{ post.title }}]({{ post.url | relative_url }}) — {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}
