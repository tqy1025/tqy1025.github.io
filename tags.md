---
layout: page
title: 标签
permalink: /tags/
---

## 全部标签

<div class="tag-list">
{% assign sorted_tags = site.tags | sort %}
{% for tag in sorted_tags %}
  <a href="#{{ tag[0] | uri_escape }}">
    {{ tag[0] }}（{{ tag[1].size }}）
  </a>
{% endfor %}
</div>

<hr>

{% for tag in sorted_tags %}
<section id="{{ tag[0] }}">
  <h2>{{ tag[0] }}</h2>

  <ul>
  {% for post in tag[1] %}
    <li>
      {{ post.date | date: "%Y-%m-%d" }}
      <a href="{{ post.url | relative_url }}">
        {{ post.title }}
      </a>
    </li>
  {% endfor %}
  </ul>
</section>
{% endfor %}
