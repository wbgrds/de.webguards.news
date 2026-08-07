---
layout: default
title: Tags
permalink: /tags/
---

# Nach Tags filtern

{% assign sorted_tags = site.posts | map: 'tags' | join: ',' | split: ',' | uniq | sort %}

{% for tag in sorted_tags %}
{% assign posts_with_tag = site.posts | where_exp: "post", "post.tags contains tag" %}
<h2 id="{{ tag | slugify }}" style="margin-top: 2.5rem; padding-top: 1rem; border-top: 1px solid #334155;">{{ tag }}</h2>

<div class="posts-list">
{% for post in posts_with_tag %}
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
{% endfor %}
