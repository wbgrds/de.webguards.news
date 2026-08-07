---
layout: default
title: Suche
permalink: /suche/
---

# Suche

<input type="text" id="search-input" placeholder="Artikel durchsuchen..." style="
  width: 100%;
  padding: 0.75rem;
  background: #1a2f4d;
  color: #f8fafc;
  border: 1px solid #334155;
  border-radius: 6px;
  font-size: 1rem;
  margin-bottom: 2rem;
">

<div id="search-results" style="margin-top: 2rem;"></div>

<script>
const posts = [
{% for post in site.posts %}
  {
    title: "{{ post.title | escape }}",
    url: "{{ post.url }}",
    date: "{{ post.date | date: '%d. %B %Y' }}",
    excerpt: "{{ post.excerpt | strip_html | truncatewords: 30 | escape }}",
    author: "{{ post.author | escape }}",
    tags: [{% for tag in post.tags %}"{{ tag }}"{% unless forloop.last %},{% endunless %}{% endfor %}]
  }{{ unless forloop.last }},{{ endunless }}
{% endfor %}
];

const searchInput = document.getElementById('search-input');
const searchResults = document.getElementById('search-results');

function search(query) {
  if (!query.trim()) {
    searchResults.innerHTML = '';
    return;
  }

  const q = query.toLowerCase();
  const results = posts.filter(post => 
    post.title.toLowerCase().includes(q) ||
    post.excerpt.toLowerCase().includes(q) ||
    post.tags.some(tag => tag.toLowerCase().includes(q))
  );

  if (results.length === 0) {
    searchResults.innerHTML = '<p style="color: #94a3b8;">Keine Artikel gefunden.</p>';
    return;
  }

  searchResults.innerHTML = results.map(post => `
    <div class="post-card">
      <div class="article-meta">${post.date}${post.author ? ` • ${post.author}` : ''}</div>
      <h3><a href="${post.url}">${post.title}</a></h3>
      <p style="margin: 0; color: #cbd5e1; font-size: 0.95rem;">${post.excerpt}</p>
      ${post.tags.length > 0 ? `<div style="margin-top: 0.75rem; font-size: 0.85rem;">
        ${post.tags.map(tag => `<span style="color: #22d3ee;">#${tag}</span>`).join(' ')}
      </div>` : ''}
    </div>
  `).join('');
}

searchInput.addEventListener('keyup', (e) => search(e.target.value));
searchInput.addEventListener('input', (e) => search(e.target.value));
</script>
