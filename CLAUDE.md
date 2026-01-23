# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website built with Hugo static site generator.

## Repository

- Branch: `main`
- Remote: `https://github.com/mjkaul/website.git`

## Development Commands

```bash
hugo server        # Local dev server with live reload (http://localhost:1313)
hugo               # Build static site to public/
```

## Adding Essays

Create a markdown file in `content/essays/` with frontmatter:

```yaml
---
title: "Essay Title"
date: 2024-01-23
description: "Brief description shown on homepage"
---
```

Essays automatically appear on the homepage, sorted by date (newest first).

## Structure

- `layouts/_default/baseof.html` - Base template with site CSS
- `layouts/index.html` - Homepage template (lists essays dynamically)
- `layouts/essays/single.html` - Individual essay page template
- `content/essays/` - Markdown essay files
- `public/` - Generated output (gitignored)

## Styling

- Font: Iowan Old Style/Palatino serif
- Link color: `#F71735` (red), bold, no underline
- Max content width: 720px
- Design based on Rob Beschizza's homepage

## Notes

- `kaulhome.html` is the original static file (archived, no longer used)
- Projects section still has placeholder links
