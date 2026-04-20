---
layout: default
title: Home
---

Welcome. This is a small technical blog: tools, APIs, and things that broke in interesting ways.

## Posts

<ul class="post-list">
{% for post in site.posts %}
  <li><span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span> — <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
