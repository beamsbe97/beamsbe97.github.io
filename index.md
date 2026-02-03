---
layout: default
title: Home
---

<div class="cards">
  {% for post in site.posts %}
    <article class="card">
      <img src="{{ post.thumbnail }}" alt="{{ post.title }}">

      <div class="card-content">
        <h2 class="card-title">
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h2>

        <p class="card-date">
          {{ post.date | date: "%B %d, %Y" }}
        </p>

        <p class="card-excerpt">
          {{ post.excerpt | strip_html | truncate: 140 }}
        </p>

        <a class="card-link" href="{{ post.url }}">
          Continue reading →
        </a>
      </div>
    </article>
  {% endfor %}
</div>
