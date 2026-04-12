# Deployment

This is a **Quarto website** served via GitHub Pages from `master /docs`.

## How to update

```bash
# Edit content
vim index.qmd    # main project index
vim projects.qmd # detailed project page

# Build
quarto render    # outputs to docs/

# Deploy
git add docs/ index.qmd projects.qmd
git commit -m "update site"
git push         # GitHub Pages auto-deploys from master /docs
```

## CRITICAL: Do NOT use `quarto publish gh-pages`

This is a `username.github.io` repo (user site). User sites **must** serve
from the default branch (`master`). The `gh-pages` branch approach silently
404s — the GitHub API accepts it and reports `status: built` but the content
is never served.

Only project repos (e.g. `JohnGavin/micromort`) can use `gh-pages`.

## History

- **Pre 2026-04-12:** Hugo site with `hugo-universal-theme` (24MB, 1,335 files, CVE-prone npm deps)
- **2026-04-12:** Migrated to Quarto (3 source files, zero npm deps, cosmo theme)
- **Lesson learned:** `quarto publish gh-pages` produced a 404 for 15 minutes before we realised the user-site constraint
