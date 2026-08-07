# WEBGUARDS News

Blog-Plattform für WEBGUARDS – gebaut mit [11ty](https://www.11ty.dev/).

## Setup

```bash
npm install
npm run serve    # Lokal entwickeln
npm run build    # Produktions-Build
npm run watch    # Mit Watch-Modus
```

## Neue Posts schreiben

Erstelle eine neue Datei in `src/blog/posts/`:

```markdown
---
layout: post
title: Dein Titel
date: 2026-08-07
author: Dein Name
excerpt: Kurze Zusammenfassung für die Übersicht
---

# Inhalt

Schreib hier dinen Artikel...
```

## Struktur

```
src/
  /blog/posts/         ← Blog-Artikel (Markdown)
  /css/               ← Stylesheets
  /js/                ← JavaScript
  /_layouts/          ← Seitenlayouts
  /_includes/         ← Wiederverwendbare Komponenten
  index.md            ← Homepage
.eleventy.js          ← 11ty Konfiguration
```

## Deployment

- Commits zu `main` triggern automatisch GitHub Actions
- Build und Deploy zu GitHub Pages
- Live unter: `news.webguards.de`

## Live-Domain

```
Repository: wbgrds/de.webguards.news
GitHub Pages Domain: news.webguards.de (mit Custom Domain)
```
