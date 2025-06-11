---
layout: default
title: 97-vinash Homepage
---

<h1>Blog Posts</h1>
<ul class="posts-list">
  {% for post in site.posts %}
  <li class="post-item">
    <div class="post-date">{{ post.date | date: "%B %-d, %Y" }}</div>
    <h2 class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    {% if post.tags %}
    <div class="post-tags">
      {% for tag in post.tags %}
        <span class="tag">{{ tag }}</span>{% unless forloop.last %}, {% endunless %}
      {% endfor %}
    </div>
    {% endif %}
    <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
  </li>
  {% endfor %}
</ul>

