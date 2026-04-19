# Anthony Baptista – Academic Website

Personal academic website built with [Hugo Academic (HugoBlox)](https://hugoblox.com/).

## Quick Start

### Prerequisites
- [Hugo Extended](https://gohugo.io/installation/) (v0.128+)
- [Go](https://go.dev/dl/) (v1.21+)
- [Node.js](https://nodejs.org/) (v18+)
- Git

### Local Development

```bash
# Extract the archive
tar xzf academic-site.tar.gz
cd academic-site

# Install dependencies
npm install

# Start local dev server
hugo server -D
```

Then open http://localhost:1313 in your browser.

### Deploy to GitHub Pages

1. Create a GitHub repo named `YOUR_USERNAME.github.io`
2. Update `baseURL` in `config/_default/hugo.yaml` to `https://YOUR_USERNAME.github.io/`
3. Push the code:

```bash
cd academic-site
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_USERNAME.github.io.git
git push -u origin main
```

4. In GitHub repo → Settings → Pages → Source: select **GitHub Actions**
5. Create `.github/workflows/hugo.yml`:

```yaml
name: Deploy Hugo site

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: '0.139.5'
          extended: true
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      - name: Install dependencies
        run: npm install
      - name: Build
        run: hugo --minify
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## What to Customise

### Your Profile
- **`data/authors/me.yaml`** — Name, bio, links (GitHub, ORCID, Scholar), education, experience, skills
- **`assets/media/`** — Add your avatar as `avatar.jpg` or `avatar.png`
- **`static/uploads/resume.pdf`** — Your CV (linked from the Download CV button)

### Social Links (in `data/authors/me.yaml`)
Replace the placeholder URLs:
- `YOUR_GITHUB_USERNAME` → your GitHub username
- `YOUR_LINKEDIN` → your LinkedIn slug
- `YOUR_SCHOLAR_ID` → your Google Scholar user ID
- `YOUR_ORCID` → your ORCID number

### Theme & Appearance
- **`config/_default/params.yaml`** — Theme mode (dark/light), colours, typography, layout

### Content

| Section       | Location                          | How to add                          |
|---------------|-----------------------------------|-------------------------------------|
| Publications  | `content/publications/<slug>/`    | Create `index.md` per paper         |
| Blog posts    | `content/blog/<slug>/`            | Create `index.md` per post          |
| Projects      | `content/projects/<slug>/`        | Create `index.md` per project       |
| Teaching      | `content/courses/<slug>/`         | Create `index.md` per course        |
| Experience    | `content/experience.md`           | Edit directly                       |

### Adding a New Publication

```bash
mkdir content/publications/my-new-paper
```

Then create `content/publications/my-new-paper/index.md`:

```markdown
---
title: "Paper Title"
authors:
  - Anthony Baptista
  - Co-Author Name
date: "2025-06-01"
publication_types: ["article-journal"]
publication: "*Journal Name*"
abstract: "Your abstract here."
featured: true
tags:
  - Spatial Omics
url_pdf: ""
doi: "10.xxxx/xxxxx"
---
```

### Adding a Blog Post

```bash
mkdir content/blog/my-post-slug
```

Then create `content/blog/my-post-slug/index.md`:

```markdown
---
title: "My Blog Post Title"
date: 2025-04-01
tags:
  - Tutorial
summary: "A short description."
authors:
  - me
---

Your content in Markdown, with support for LaTeX ($E = mc^2$),
code blocks, images, and more.
```

### BibTeX Import
You can bulk-import publications from BibTeX using the `academic` CLI:

```bash
pip install academic
academic import --bibtex my_papers.bib
```

## File Structure

```
academic-site/
├── config/_default/
│   ├── hugo.yaml          # Base URL, language, build settings
│   ├── params.yaml        # Theme, identity, features
│   ├── menus.yaml         # Navigation bar links
│   └── ...
├── content/
│   ├── _index.md          # Homepage layout (sections/blocks)
│   ├── authors/           # Author listing page
│   ├── blog/              # Blog posts
│   ├── courses/           # Teaching content
│   ├── experience.md      # Work experience page
│   ├── projects/          # Project pages
│   └── publications/      # Papers
├── data/authors/
│   └── me.yaml            # Your profile data
├── assets/media/          # Images, avatar
├── static/uploads/        # CV, downloadable files
└── hugoblox.yaml          # HugoBlox version pinning
```

## Useful Commands

```bash
hugo server -D        # Dev server (includes drafts)
hugo server           # Dev server (production content only)
hugo --minify         # Build for production
hugo new blog/my-post # Scaffold a new blog post
```

## Documentation
- [HugoBlox Docs](https://docs.hugoblox.com/)
- [Hugo Docs](https://gohugo.io/documentation/)
