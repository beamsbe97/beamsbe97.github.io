---
layout: default
title: Home
---

<div class="home-layout">

  <!-- MAIN: posts -->
  <main class="home-main">
    <div class="cards single-column">
      {% for post in site.posts %}
        <article class="card">
          <img src="{{ post.thumbnail }}" alt="{{ post.title }}">
          <div class="card-content">
            <h2 class="card-title">
              <a href="{{ post.url }}">{{ post.title }}</a>
            </h2>
            <p class="card-date">{{ post.date | date: "%B %d, %Y" }}</p>
            <p class="card-excerpt">
              {{ post.excerpt | strip_html | truncate: 140 }}
            </p>
            <a class="card-link" href="{{ post.url }}">Continue reading →</a>
          </div>
        </article>
      {% endfor %}
    </div>
  </main>

  <!-- SIDEBAR: profile -->
  <aside class="home-sidebar">
    <div class="profile-card">
      <img src="/assets/images/profile.jpg" alt="Profile photo">
      <h3>Your Name</h3>
      <p>
        MSc AI / CS<br>
        Research interests: LLM safety, RL, generative models
      </p>
      <div class="profile-links">
        <a href="https://github.com/yourname">GitHub</a> ·
        <a href="https://scholar.google.com">Scholar</a>
      </div>
    </div>
  </aside>

</div>
