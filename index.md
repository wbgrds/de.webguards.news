---
layout: home
---

# WEBGUARDS News

Blog für Gründer – Tipps zu Prozessen, Automation und rechtlicher Sicherheit.

## Neueste Posts

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) – {{ post.date | date: "%d. %B %Y" }}
{% endfor %}

[Alle Posts anschauen](/blog)
