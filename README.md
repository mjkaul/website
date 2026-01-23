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

**GitHub Pages (recommended):**
1. Go to your repo on GitHub → Settings → Pages
2. Under "Build and deployment", set Source to **GitHub Actions**
3. Create `.github/workflows/hugo.yml` (see below)
4. Push to main - the site will build and deploy automatically

The workflow file is already included in this repo at `.github/workflows/hugo.yml`.

**Cloudflare Pages (alternative):**
1. Go to Cloudflare Dashboard → Workers & Pages → Create application → Pages
2. Select "Import an existing Git repository" and connect `mjkaul/website`
3. Configure build settings:
   - Production branch: `main`
   - Build command: `hugo`
   - Build directory: `public`
   - Deploy command: `npx wrangler pages deploy public`
4. (Optional) Add environment variable `HUGO_VERSION` = `0.148.2`
5. Save and Deploy

### 2. Set Up Custom Domain (mjkaul.com)

**DNS Configuration (at your domain registrar):**
- Add a CNAME record: `@` → `mjkaul.github.io`
- Or for apex domain, add A records pointing to GitHub's IPs:
  ```
  185.199.108.153
  185.199.109.153
  185.199.110.153
  185.199.111.153
  ```

**GitHub Pages Configuration:**
1. Go to repo Settings → Pages
2. Under "Custom domain", enter `mjkaul.com`
3. Check "Enforce HTTPS" (after DNS propagates)

**Hugo Configuration:**
The `hugo.toml` baseURL is already set to `https://mjkaul.com/`.

### 3. Set Up Micro.blog Subdomain (micro.mjkaul.com)

**DNS Configuration:**
- Add a CNAME record: `micro` → `micro.blog`

**Micro.blog Configuration:**
1. Log in to micro.blog → Account → Edit Domains & Design
2. Add `micro.mjkaul.com` as your custom domain

### 4. Install the Micro.blog Theme

1. Log in to micro.blog
2. Go to **Posts → Design → Edit Custom Themes**
3. Click **New Theme**
4. Enter a name (e.g., "Kaul Theme")
5. Set **Clone URL** to: `https://github.com/mjkaul/website.git`
   - Or create a separate repo with just the `microblog-theme/` contents
6. Save and select the theme as your active design

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
