# My Academic Website — Quarto

Personal academic website built with [Quarto](https://quarto.org) and hosted on GitHub Pages.

## Structure

```
.
├── _quarto.yml              # Site configuration (navbar, theme, options)
├── styles.css               # Custom CSS
├── index.qmd                # Home page (bio, news, recent publications)
├── research.qmd             # Publications, thesis, talks
├── code.qmd                 # Code projects and computational notebooks
├── teaching.qmd             # Teaching experience and materials
├── cv.qmd                   # Curriculum Vitae
├── code/                    # Computational notebooks
│   ├── lid-driven-cavity.qmd    # Julia example (live kernel)
│   └── spectral-analysis.qmd   # MATLAB example (static code + figures)
├── images/                  # Profile photo, figures
├── _freeze/                 # Frozen computational outputs (committed to git)
└── .github/workflows/
    └── publish.yml          # GitHub Actions for auto-deploy
```

## Quick start

### Prerequisites

- [Quarto](https://quarto.org/docs/get-started/) (≥ 1.4)
- [Julia](https://julialang.org/) + IJulia kernel (for Julia notebooks)
- MATLAB (for running MATLAB scripts locally — not needed for the site build)

### Local development

```bash
# Clone this repo
git clone https://github.com/your-username/your-username.github.io.git
cd your-username.github.io

# Preview the site (auto-reloads on changes)
quarto preview

# Render everything (executes Julia code, freezes output)
quarto render
```

### Deploying

The site uses the **local execution + CI rendering** strategy:

1. Run `quarto render` locally (this executes Julia code and saves results in `_freeze/`)
2. Commit everything, including `_freeze/`
3. Push to `main` — GitHub Actions will render the markdown and deploy to GitHub Pages

### Adding a new computational notebook

**Julia (live execution):**
```yaml
---
title: "My Analysis"
jupyter: julia-1.10
---
```
Write Julia code in ```` ```{julia} ```` blocks — it will be executed by Quarto.

**MATLAB (static code display):**
```yaml
---
title: "My MATLAB Analysis"
---
```
Use ```` ```matlab ```` blocks (no curly braces = no execution).
Run your MATLAB scripts separately, save figures as images, and include them with `![](images/figure.png)`.

### Custom domain

1. Buy a domain (e.g., `yourname.com`)
2. Add a `CNAME` file to the repo root containing just your domain name
3. Configure DNS (A records or CNAME) pointing to GitHub Pages
4. Uncomment `site-url` in `_quarto.yml`

## License

Content: CC-BY 4.0 | Code: MIT
