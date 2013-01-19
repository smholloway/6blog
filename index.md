---
layout: page
title: Home
tagline: 
---
{% include JB/setup %}

Seth + Nick's Blog -- 6blog

Jump in and start reading!

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
