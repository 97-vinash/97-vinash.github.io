---
layout: default
title: Home
---

<header class="topbar">
  <div class="container">
    <a href="{{ '/' | relative_url }}" class="site-name">97-vinash</a>
    <nav class="nav-links">
      <a href="{{ '/about' | relative_url }}">About Me</a>
      <a href="https://github.com/yourgithubusername" target="_blank" rel="noopener">GitHub</a>
      <a href="https://youtube.com/yourchannel" target="_blank" rel="noopener">YouTube</a>
    </nav>
  </div>
</header>

<main class="content">
  <div class="container">
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
  </div>
</main>

