---
layout: page
title: 6blog - Home of Nick and Seth's Learning Club
tagline:
---
{% include JB/setup %}

We are passionate about learning, and we want to share our lessons learned. We hope you will find it valuable.

## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
