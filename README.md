# anasdox.github.io

Personal website of Anas Ameziane, served at <https://anasdox.github.io/>.

Built as a minimal Jekyll site with a hand-written CSS theme. No
JavaScript, no build step on your machine: GitHub Pages picks up the
source on every push and builds it.

## Structure

```
_config.yml          site metadata + nav
_layouts/            default, page, post
_includes/           header, footer
_posts/              blog posts (YYYY-MM-DD-slug.md)
assets/css/style.css single hand-written stylesheet
index.html           home (hero)
about.md             about page
experience.md        career timeline
projects.md          project cards
blog.html            blog index
contact.md           contact info
```

## Edit content

Every page is plain Markdown with YAML frontmatter. To add a new blog
post, drop a file in `_posts/` named `YYYY-MM-DD-slug.md`:

```markdown
---
layout: post
title: "Your title"
date: 2026-05-28
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
