# anasdox.github.io

Personal website of Anas Ameziane, served at <https://anasdox.github.io/>.

AI-Native Product Engineering: essays, experiments and method, in
French first (English originals kept in `_en/`). Minimal Jekyll site
with a hand-written CSS theme. No JavaScript except Mermaid on pages
that contain a diagram, no build step on your machine: GitHub Pages
picks up the source on every push and builds it.

## Structure

```
_config.yml          site metadata, SEO, nav, newsletter hook
_data/               editorial topics, French month names
_layouts/            default, page, post
_includes/           header, footer, cta, date, topic
_posts/              French essays (YYYY-MM-DD-slug.md)
_en/                 English originals, served at their original URLs
assets/css/style.css single hand-written stylesheet (light + dark)
index.html           home
articles.html        /articles/
labo.md              /labo/ (experiments)
playbook.md          /playbook/ (in preparation)
methode.md           /methode/
a-propos.md          /a-propos/
parcours.md          /parcours/ (career)
contact.md           /contact/
```

## Edit content

Every page is plain Markdown with YAML frontmatter. To add a new blog
post, drop a file in `_posts/` named `YYYY-MM-DD-slug.md`:

```markdown
---
title: "Your title"
date: 2026-05-28
description: "150-160 characters, used as meta description and lede."
topic: validation        # a slug from _data/topics.yml
tags: [agentic]
---

Your post here.
```

## Preview locally (optional)

You only need this if you want to see changes before pushing.
Requires Ruby 3.x.

```bash
bundle install
bundle exec jekyll serve
# open http://localhost:4000
```

## Deploy

Push to the `main` branch of `anasdox/anasdox.github.io`. GitHub Pages
detects a user site repository and serves it at the user URL within
about a minute. No GitHub Actions config required.
