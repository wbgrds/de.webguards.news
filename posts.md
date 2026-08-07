---
layout: default
title: Artikel
permalink: /posts/
---

# WEBGUARDS News

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})** – {{ post.date | date: "%d. %B %Y" }}
{% endfor %}

{% if site.posts.size == 0 %}
Noch keine Artikel veröffentlicht.
{% endif %}
