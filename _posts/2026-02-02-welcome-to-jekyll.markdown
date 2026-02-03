---
layout: default
title: "Hello World"
---

This is my Machine Learning blog.

<h1>Posts</h1>

<div class="posts">
  {% for post in site.posts %}
    <div class="post-card">
      <img src="{{ post.thumbnail }}" alt="{{ post.title }}">
      <h2>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </h2>
      <p>{{ post.date | date: "%b %d, %Y" }}</p>
    </div>
  {% endfor %}
</div>