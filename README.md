# Hugo + Micro.blog Personal Website Template

A minimal, elegant personal website setup that combines:
- **Hugo** for your main homepage and long-form essays
- **Micro.blog** for short posts and microblogging
- **Unified design** across both platforms

Your main site displays essays you write in Markdown, plus a feed of your latest micro.blog posts. Both sites share the same visual design.

## Features

- Static site with no JavaScript frameworks or build complexity
- Essays written in Markdown with automatic homepage listing
- Short posts pulled from micro.blog in real-time
- Matching Hugo theme for micro.blog
- Archive page with year/month filtering
- Mobile-responsive design

## Quick Start

### 1. Fork or Clone This Repo

```bash
git clone https://github.com/YOUR_USERNAME/website.git
cd website
```

### 2. Install Hugo

On macOS:
```bash
brew install hugo
```

See [Hugo installation docs](https://gohugo.io/installation/) for other platforms.

### 3. Preview Locally

```bash
hugo server
```

Visit http://localhost:1313 to see your site.

---

## Configuration

### Site Settings

Edit `hugo.toml`:

```toml
baseURL = 'https://yourdomain.com/'
languageCode = 'en-us'
title = 'Your Name'

[permalinks]
  essays = '/essays/:slug/'

[params]
  microblog_url = "https://micro.yourdomain.com"
```

### Customizing the Design

The site's styling is in `layouts/_default/baseof.html`. Key values to customize:

```css
/* Font family - change to your preferred fonts */
font-family: "Iowan Old Style", Palatino, "Palatino Linotype", serif;

/* Base font size */
font-size: 120%;

/* Link color - change to match your brand */
a { color: #F71735; }

/* Content width */
max-width: 720px;
```

**Color ideas:**
- Classic blue: `#2563eb`
- Forest green: `#166534`
- Purple: `#7c3aed`
- Orange: `#ea580c`
- Keep it black: `#000000`

**Font ideas:**
- System fonts: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`
- Serif: `Georgia, "Times New Roman", serif`
- Monospace: `"SF Mono", Monaco, "Courier New", monospace`

### Customizing the Homepage

Edit `layouts/index.html` to change:
- Your bio/introduction
- Section headings
- Blogroll links
- Any other static content

The Essays section and Short Posts section are dynamic - they update automatically.

---

## Writing Essays

Create a Markdown file in `content/essays/`:

```bash
touch content/essays/my-first-essay.md
```

Add frontmatter and content:

```yaml
---
title: "My First Essay"
date: 2024-01-23
description: "A brief description shown on the homepage"
---

Your essay content here. Write in Markdown.

## Subheadings work

You can use all standard Markdown:
- Lists
- **Bold** and *italic*
- [Links](https://example.com)
- Images, code blocks, etc.
```

Essays automatically appear on your homepage, sorted by date (newest first).

---

## Deployment

### GitHub Pages (Recommended)

1. Push your repo to GitHub
2. Go to repo **Settings → Pages**
3. Set Source to **GitHub Actions**
4. The included workflow (`.github/workflows/hugo.yml`) builds and deploys automatically

Your site will be at `https://USERNAME.github.io/REPO_NAME/`

### Custom Domain

1. **Add DNS records** at your registrar:
   - A records pointing to GitHub's IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```

2. **Configure GitHub Pages:**
   - Go to repo Settings → Pages
   - Enter your custom domain
   - Check "Enforce HTTPS" (after DNS propagates)

3. **Update hugo.toml:**
   ```toml
   baseURL = 'https://yourdomain.com/'
   ```

---

## Micro.blog Integration

### Setting Up Short Posts

The homepage includes a "Short Posts" section that fetches your latest micro.blog posts. Update the URL in `hugo.toml`:

```toml
[params]
  microblog_url = "https://yourusername.micro.blog"
```

Or use a custom subdomain:
```toml
  microblog_url = "https://micro.yourdomain.com"
```

### Installing the Micro.blog Theme

The `microblog-theme/` directory contains a matching Hugo theme for micro.blog.

1. Create a separate repo with the theme contents, or use this repo directly
2. In micro.blog: **Posts → Design → Edit Custom Themes → New Theme**
3. Set **Clone URL** to your theme repo
4. Save and select as your active theme

### Custom Domain for Micro.blog

1. **Add DNS:** CNAME record `micro` → `yourusername.micro.blog`
2. **In micro.blog:** Account → Edit Domains → Add `micro.yourdomain.com`

---

## Customizing the Micro.blog Theme

The theme files are in `microblog-theme/`. Key files:

| File | Purpose |
|------|---------|
| `static/css/style.css` | All styling (colors, fonts, spacing) |
| `layouts/partials/header.html` | Site header and navigation |
| `layouts/partials/footer.html` | Footer content |
| `layouts/_default/list.html` | Homepage post listing |
| `layouts/_default/single.html` | Individual post pages |
| `layouts/_default/list.archivehtml.html` | Archive page with filters |

Edit `static/css/style.css` to match any design changes you made to your main site.

---

## Project Structure

```
website/
├── content/
│   └── essays/              # Your essay Markdown files
├── layouts/
│   ├── _default/
│   │   └── baseof.html      # Base template with CSS
│   ├── essays/
│   │   └── single.html      # Essay page template
│   └── index.html           # Homepage template
├── microblog-theme/         # Micro.blog theme (separate repo recommended)
├── .github/
│   └── workflows/
│       └── hugo.yml         # GitHub Pages deployment
├── hugo.toml                # Site configuration
└── README.md
```

---

## Local Development

```bash
hugo server              # Dev server with live reload
hugo                     # Build to public/
hugo server -D           # Include draft posts
```

---

## License

MIT - Use this template however you like.
