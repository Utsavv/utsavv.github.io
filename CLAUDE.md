# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website for Utsav Verma (utsavverma.com), built on the **al-folio** Jekyll theme. Deployed via GitHub Pages using the `deploy.yml` workflow on push to `main`.

## Build & Dev Commands

```bash
bundle install                  # install Ruby dependencies
bundle exec jekyll serve        # local dev server at http://localhost:4000
bundle exec jekyll build        # production build (output in _site/)
JEKYLL_ENV=production bundle exec jekyll build  # production build with analytics enabled
```

Ruby version: 3.2.9 (see `.ruby-version`).

There are no test suites or linters configured for the Jekyll content itself. CI runs **Prettier** on push/PR (`npx prettier . --check`) and a **link checker** (lychee) on push to main.

## Architecture

**Theme:** al-folio (academic Jekyll theme). The site uses Liquid templates, Kramdown markdown, and SCSS.

**Key directories:**
- `_pages/` — top-level pages: `about.md` (serves as homepage at `/`), `blog.md`, `cv.md`
- `blog/_posts/` — blog posts in markdown, named `YYYY-MM-DD-slug.md`
- `_layouts/` — Liquid layout templates (inherits from `default.liquid`)
- `_includes/` — reusable partials (header, footer, latest_posts, social, etc.)
- `_data/articles.yml` — structured list of external publications rendered on the CV page
- `_sass/` — SCSS partials; `_variables.scss` and `_themes.scss` control colors/theming
- `assets/` — static files (CSS, JS, images, fonts, CV PDF)
- `_plugins/taint_compat.rb` — monkey-patches Ruby 3.2+ taint API removal for Liquid compatibility

**Homepage flow:** `_pages/about.md` (layout: `about`) → `_layouts/about.liquid` → renders bio content, then conditionally includes `latest_posts.liquid` which shows the most recent 3 posts (controlled by `latest_posts.limit` in `_config.yml`).

**Blog pagination:** Handled by `jekyll-paginate-v2`; configured in `_config.yml` under `pagination:`. The blog page uses `paginator.posts` not `site.posts`.

**Configuration:** `_config.yml` is the single source for site settings, social links, analytics, blog config, plugin list, and third-party library versions/SRI hashes.

## Blog Post Conventions

Front matter pattern:
```yaml
---
layout: post
title: "Post Title"
date: YYYY-MM-DD
excerpt: "One-line summary."
---
```

Posts go in `blog/_posts/` (not the root `_posts/`). Display order is reverse chronological — newest first — everywhere on the site (homepage latest_posts, blog listing, archives).

## Agent Instructions

From `AGENT.md`:
1. Always ensure the newest blog post is visible on the home page before the rest of the list.
2. Display blog posts in reverse chronological order (newest first) wherever they appear on the site.

## Deployment

Push to `main` triggers `.github/workflows/deploy.yml` which builds with Jekyll and deploys to GitHub Pages. The site is served from a custom domain (`utsavverma.com` via `CNAME`).
