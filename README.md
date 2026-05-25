# byungkookim.github.io

Source code for my personal website, built with [Quarto](https://quarto.org).

## Repository layout

```
.
├── _quarto.yml            # site config + navbar
├── index.qmd              # Home
├── research.qmd           # Auto-renders publications/ and working-papers/
├── teaching.qmd
├── cv.qmd                 # Links to files/cv.pdf
├── publications/          # ONE FILE PER PUBLISHED PAPER
├── working-papers/        # ONE FILE PER WORKING PAPER
├── files/cv.pdf
├── images/profile.jpg     # Photo for Home page (add manually)
├── _pub-listing.ejs       # Custom listing template (academic style)
├── styles.css
└── .github/workflows/publish.yml   # Builds + deploys on push
```

## Common tasks

### Add a new publication
Copy any file in `publications/`, rename to `YYYY-slug.qmd`, edit the
five fields in the front matter. Commit and push — the Research page
re-renders automatically, sorted by year (newest first).

```yaml
---
title: "Paper title"
author: "Author A and Author B"
date: "2026-01-01"      # year used for sorting
year: 2026              # displayed on the page
venue: "Journal Name, vol(issue), pp"
url: "https://doi.org/..."
---
```

### Add a working paper
Same idea — copy a file in `working-papers/`, edit the front matter.
Working papers are sorted by the `order:` field, so move it to whatever
position you want.

### Update the CV
Replace `files/cv.pdf` with the new PDF (keep the filename), commit, push.

### Edit the photo
Drop a square JPG/PNG into `images/profile.jpg`.

## Local preview

```bash
brew install --cask quarto    # one-time install
quarto preview                # auto-reloads in browser
```

## Deployment

Pushes to `main` trigger the GitHub Action in `.github/workflows/publish.yml`,
which renders the site and publishes it to the `gh-pages` branch. GitHub
Pages then serves it at <https://byungkookim.github.io>.

First-time setup on the GitHub side:

1. Create the repo `byungkookim/byungkookim.github.io` (must be named
   exactly that for the user-site URL to work).
2. Push this directory to `main`.
3. Once the first Action run finishes, go to **Settings → Pages** and
   set "Source" to "Deploy from a branch", branch `gh-pages`, folder `/`.
4. After the second Action run, the site is live.
