# Matthew Kaul's Website

Personal website built with Hugo, featuring essays and micro.blog integration.

## What's Included

- **Hugo-powered homepage** with dynamic essay listing
- **Short posts section** that pulls recent posts from micro.blog
- **Micro.blog theme** with matching design for visual consistency across both sites

## Local Development

```bash
hugo server    # Start dev server at http://localhost:1313
hugo           # Build static site to public/
```

## Project Structure

```
website/
├── content/essays/       # Markdown essay files go here
├── layouts/              # Hugo templates for main site
├── microblog-theme/      # Theme for micro.blog
├── hugo.toml             # Hugo configuration
└── public/               # Generated output (gitignored)
```

---

## Action Steps

### 1. Deploy the Main Site

Choose a static hosting provider and deploy the `public/` folder:

**Cloudflare Pages:**
1. Go to Cloudflare Dashboard → Workers & Pages → Create application → Pages
2. Select "Import an existing Git repository" and connect `mjkaul/website`
3. Configure build settings:
   - Production branch: `main`
   - Build command: `hugo`
   - Build directory: `public`
4. (Optional) Add environment variable `HUGO_VERSION` = `0.148.2`
5. Save and Deploy

**Other options:** Netlify, Vercel, GitHub Pages

### 2. Update Your Domain

In `hugo.toml`, change the baseURL to your actual domain:

```toml
baseURL = 'https://matthewkaul.com/'
```

### 3. Install the Micro.blog Theme

1. Log in to micro.blog
2. Go to **Posts → Design → Edit Custom Themes**
3. Click **New Theme**
4. Enter a name (e.g., "Kaul Theme")
5. Set **Clone URL** to: `https://github.com/mjkaul/website.git`
   - Or create a separate repo with just the `microblog-theme/` contents
6. Save and select the theme as your active design

### 4. Update the Micro.blog URL (if needed)

If you change your micro.blog subdomain, update `hugo.toml`:

```toml
[params]
  microblog_url = "https://your-new-subdomain.micro.blog"
```

Then rebuild and redeploy.

### 5. Write Your First Essay

Create a file in `content/essays/`, e.g., `content/essays/my-first-essay.md`:

```yaml
---
title: "My First Essay"
date: 2024-01-23
description: "A brief description for the homepage"
---

Your essay content here. Write in Markdown.
```

Delete `content/essays/example-essay.md` when ready.

### 6. Update Placeholder Content

Edit `layouts/index.html` to replace:
- Project placeholders in "Other projects" section
- Any other placeholder text

---

## Design

Both the main site and micro.blog theme share:

- **Font:** Iowan Old Style, Palatino, serif
- **Link color:** #F71735 (red), bold
- **Max width:** 720px centered
- **Inspired by:** [Rob Beschizza's homepage](https://beschizza.com/)
