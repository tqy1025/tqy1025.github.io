---
layout: page
title: 文章归档
permalink: /archive/
---

{% assign postsByYear = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year in postsByYear %}
## {{ year.name }}

<ul>
  {% for post in year.items %}
    <li>
      {{ post.date | date: "%Y-%m-%d" }}
      <a href="{{ post.url | relative_url }}">
        {{ post.title }}
      </a>
    </li>
  {% endfor %}
</ul>
{% endfor %}
