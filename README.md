# AI-SDLC-SDD

Source for <https://joeshc.github.io/AI-SDLC-SDD/> — a Jekyll site published with GitHub Pages.
No CI workflow is needed; Pages builds it. Mermaid diagrams render client-side.

## Publishing

The site is configured as a **project site**: `url` is `https://joeshc.github.io` and
`baseurl` is `/AI-SDLC-SDD` in `_config.yml`.

To turn it on, in this repo go to **Settings → Pages → Source: Deploy from a branch →
`main` → `/ (root)`**. The first build takes a couple of minutes.

Posts are then live at:

```
https://joeshc.github.io/AI-SDLC-SDD/blog/<slug>/
```

The current post resolves to
`https://joeshc.github.io/AI-SDLC-SDD/blog/spec-driven-development-hospital-erp/` — use that
as `canonical_url` when cross-posting to DEV or Hashnode.

If the site later moves to a user site (a repo named `joeshc.github.io`), set `baseurl: ""`
and the URLs shorten to `https://joeshc.github.io/blog/<slug>/`.

## Run it locally

```bash
bundle install
bundle exec jekyll serve
```

Open <http://localhost:4000/AI-SDLC-SDD/>.

## Structure

```
.
├── _config.yml                 site settings, permalink shape, plugins
├── _layouts/
│   ├── default.html            shell, meta tags, Mermaid loader
│   ├── home.html               post archive
│   └── post.html               article page
├── _posts/
│   └── 2026-09-13-spec-driven-development-hospital-erp.md
├── assets/css/main.css
└── index.md
```

## Adding a post

Create `_posts/YYYY-MM-DD-slug.md` with:

```yaml
---
layout: post
title: "Your title"
subtitle: "Optional one-liner"
description: "Shown in the archive and in meta tags."
date: 2026-09-20
slug: short-url-slug
reading_time: "8 min read"
tags: [ai, architecture]
---
```

`slug` overrides the URL, which keeps long titles from producing unwieldy links.

## How Mermaid works here

`_config.yml` disables Rouge highlighting so fenced ` ```mermaid ` blocks reach the browser
as plain text. The module script in `_layouts/default.html` swaps each one for a `div.mermaid`
and runs Mermaid 11 from jsDelivr, themed to match the site palette. To add a diagram in a
future post, just write a ` ```mermaid ` fence — nothing else is needed.
