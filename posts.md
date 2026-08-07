---
layout: default
title: Artikel
permalink: /posts/
---

# Alle Artikel

<div style="display: flex; gap: 1rem; margin-bottom: 2rem; flex-wrap: wrap;">
  <a href="/posts/" style="padding: 0.5rem 1rem; background: #22d3ee; color: #0f172a; border-radius: 4px; font-weight: 500;">Neueste</a>
  <a href="/suche/" style="padding: 0.5rem 1rem; background: #1a2f4d; color: #f8fafc; border: 1px solid #334155; border-radius: 4px;">Suche</a>
  <a href="/tags/" style="padding: 0.5rem 1rem; background: #1a2f4d; color: #f8fafc; border: 1px solid #334155; border-radius: 4px;">Nach Tags</a>
</div>

{% if site.posts.size > 0 %}
<div class="posts-list">
{% for post in site.posts %}
<div class="post-card">
  <div class="article-meta">
    {{ post.date | date: "%d. %B %Y" }}
    {% if post.author %} • {{ post.author }}{% endif %}
  </div>
  {% if post.last_modified_date %}
  <div style="color: #94a3b8; font-size: 0.85rem; margin-bottom: 0.5rem;">
    Aktualisiert: {{ post.last_modified_date | date: "%d. %B %Y" }}
  </div>
  {% endif %}
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p style="margin: 0; color: #cbd5e1; font-size: 0.95rem;">{{ post.excerpt | strip_html }}</p>
  {% if post.tags %}
  <div style="margin-top: 0.75rem; font-size: 0.85rem;">
    {% for tag in post.tags %}
      <a href="/tags/#{{ tag | slugify }}" style="color: #22d3ee; margin-right: 0.75rem;">#{{ tag }}</a>
    {% endfor %}
  </div>
  {% endif %}
</div>
{% endfor %}
</div>
{% else %}
<p style="text-align: center; margin: 3rem 0; color: #cbd5e1;">
  Noch keine Artikel. Schaue bald wieder vorbei! 🚀
</p>
{% endif %}
