---
layout: default
title: Artikel
permalink: /posts/
---

# Alle Artikel

{% if site.posts.size > 0 %}
<div class="posts-list">
{% for post in site.posts %}
<div class="post-card">
  <div class="article-meta">
    {{ post.date | date: "%d. %B %Y" }}
    {% if post.author %} • {{ post.author }}{% endif %}
  </div>
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p style="margin: 0; color: #cbd5e1; font-size: 0.95rem;">{{ post.excerpt | strip_html }}</p>
</div>
{% endfor %}
</div>
{% else %}
<p style="text-align: center; margin: 3rem 0; color: #cbd5e1;">
  Noch keine Artikel. Schaue bald wieder vorbei! 🚀
</p>
{% endif %}
