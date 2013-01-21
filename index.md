---
layout: page
title: Home
tagline: 
---
{% include JB/setup %}

## (Seth + Nix) Blog == 6blog

[Seth Holloway](http://www.sethholloway.com/)

[Nick Dollarhide](http://www.6blog.us/)

## Posts
Jump in and start reading!

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
