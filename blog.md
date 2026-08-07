---
layout: page
title: Blog
permalink: /blog/
---

{% for post in site.posts %}
### [{{ post.title }}]({{ post.url }})
{{ post.date | date: "%d. %B %Y" }}{% if post.author %} – {{ post.author }}{% endif %}

{% endfor %}
