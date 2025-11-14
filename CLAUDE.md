# CLAUDE.md - AI Assistant Guide

This document provides comprehensive information about the blazickjp.github.io repository structure, development workflows, and conventions for AI assistants to follow when working with this codebase.

## Repository Overview

This is a personal blog and portfolio website for Joseph Blazick, built using:
- **Hugo** (v0.82.0) - Static site generator
- **R blogdown** - R package for creating blogs with R Markdown
- **Anatole theme** - Hugo theme for styling
- **GitHub Pages** - Hosting platform

The blog focuses on data science, statistics, and optimization topics, with posts featuring mathematical content, code examples, and visualizations.

## Repository Structure

```
blazickjp.github.io/
├── config.yaml           # Hugo configuration file
├── content/              # Source content files
│   ├── _index.md        # Homepage content
│   ├── about.md         # About page
│   ├── contact.md       # Contact page
│   ├── archives.md      # Archives page
│   └── post/            # Blog posts directory
│       ├── _index.md    # Posts index
│       ├── bib.bib      # Bibliography file
│       └── YYYY-MM-DD-post-name/  # Individual post folders
│           ├── index.en.Rmd       # R Markdown source
│           └── index.en.html      # Generated HTML
├── docs/                 # Published site (Hugo output)
├── layouts/              # Custom Hugo layouts
│   └── shortcodes/      # Custom shortcodes
│       └── blogdown/    # Blogdown-specific shortcodes
├── themes/               # Hugo themes
│   └── anatole/         # Anatole theme files
├── static/               # Static assets (images, CSS, JS)
├── resources/            # Hugo resources cache
├── R/                    # R scripts
│   ├── build.R          # Pre-build script
│   └── build2.R         # Post-build script
├── .Rprofile            # R project configuration
├── .Rhistory            # R command history
├── .RData               # R workspace data
└── blazickjp.github.io.Rproj  # RStudio project file
```

## Key Configuration Files

### config.yaml
Located at `/home/user/blazickjp.github.io/config.yaml`

Important settings:
- **baseURL**: `http://blazickjp.github.io`
- **publishDir**: `docs` (GitHub Pages publishes from this directory)
- **theme**: `anatole`
- **Hugo version**: 0.82.0 (specified in .Rprofile)
- **Math support**: Enabled via params.math.enable
- **Main sections**: `post` (for homepage post listings)

Author information:
- Name: Joseph Blazick
- Description: Data Science and Optimization Manager at Lucas Systems Inc.
- Social links: LinkedIn, GitHub, Email

### .Rprofile
Located at `/home/user/blazickjp.github.io/.Rprofile`

Key settings:
- Python environment: `/usr/local/bin/python3`
- blogdown.serve_site.startup: FALSE
- blogdown.knit.on_save: TRUE
- blogdown.method: 'html' (builds .Rmd to .html via Pandoc)
- blogdown.hugo.version: "0.82.0"

### .Rproj File
Located at `/home/user/blazickjp.github.io/blazickjp.github.io.Rproj`

Project settings:
- BuildType: Website
- UseSpacesForTab: Yes
- NumSpacesForTab: 2
- Encoding: UTF-8

## Content Structure

### Blog Posts

Posts are organized in dated directories under `content/post/`:
```
content/post/YYYY-MM-DD-post-title/
├── index.en.Rmd      # R Markdown source
├── index.en.html     # Generated HTML output
└── [figures/]        # Generated figures (if any)
```

### Post Front Matter Format

R Markdown posts use YAML front matter:
```yaml
---
title: Post Title Here
author: Joseph Blazick
date: 'YYYY-MM-DD'
slug: []
categories: []
tags: []
Description: ''
Tags: []
Categories: []
DisableComments: no
link-citations: true
bibliography: [../bib.bib]
---
```

### Content Types

1. **R Markdown Posts** (.Rmd):
   - Technical posts with R code, statistics, and mathematical notation
   - Support for LaTeX math via KaTeX
   - Support for pseudocode rendering
   - Bibliography support with citations
   - Code chunks with syntax highlighting

2. **Static Pages** (.md):
   - About, Contact, Archives pages
   - Simple markdown without R code execution

## Development Workflow

### Creating New Content

1. **New Blog Post**:
   ```r
   # In R/RStudio
   blogdown::new_post(
     title = "Post Title",
     ext = ".Rmd",  # or ".md" for simple markdown
     author = "Joseph Blazick"
   )
   ```
   - Posts are automatically created in dated directories
   - Use .Rmd for posts with R code or complex math
   - Use .md for simple text posts

2. **Writing Content**:
   - Write R Markdown content with code chunks
   - Include LaTeX math using `$...$` or `$$...$$`
   - Reference bibliography using `@citationkey`
   - Add figures with R code chunks or markdown syntax

3. **Building the Site**:
   ```r
   # In R/RStudio
   blogdown::serve_site()  # Local preview with live reload
   blogdown::build_site()  # Build for production
   ```
   - Or use Hugo directly: `hugo` (builds to docs/ directory)

### Publishing Workflow

1. **Build the site**:
   - Run `blogdown::build_site()` in R, or
   - Run `hugo` command to generate static files in `docs/`

2. **Commit changes**:
   ```bash
   git add .
   git commit -m "descriptive message"
   ```

3. **Push to GitHub**:
   ```bash
   git push -u origin <branch-name>
   ```
   - Note: Branch names should start with 'claude/' for AI assistant work
   - GitHub Pages automatically serves from the `docs/` directory

## Conventions and Best Practices

### Coding Conventions

1. **R Code Style**:
   - Use 2 spaces for indentation (as per .Rproj settings)
   - Use snake_case for variable names
   - Include comments for complex algorithms

2. **Markdown Style**:
   - Use ATX-style headers (# ## ###)
   - Include blank lines around code blocks
   - Use fenced code blocks with language specification

3. **File Naming**:
   - Posts: `YYYY-MM-DD-descriptive-title/`
   - Use lowercase with hyphens for slugs
   - R Markdown files: `index.en.Rmd`

### Mathematical Content

Posts frequently include:
- LaTeX equations via KaTeX
- Pseudocode algorithms
- Statistical formulas
- Machine learning concepts

Example includes:
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.11.1/katex.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/pseudocode@latest/build/pseudocode.min.js"></script>
```

### Bibliography Management

- Central bibliography file: `content/post/bib.bib`
- Reference in front matter: `bibliography: [../bib.bib]`
- Cite using: `@citationkey`
- Enable citations: `link-citations: true`

## Git Workflow

### Branch Naming
- Main branch: Default branch (typically `main` or `master`)
- Feature/AI branches: Should start with `claude/` prefix
- Example: `claude/claude-md-mhy8hbxdidg5d517-01C1hbz47rrobeC3fwSiAcrq`

### Commit Message Style
Based on recent commits, the repository uses simple, concise commit messages:
- Typically one word: "update"
- For AI assistants, use more descriptive messages like:
  - "Add new post about [topic]"
  - "Update about page"
  - "Fix styling in [component]"
  - "Refactor [functionality]"

### Git Push Requirements
- Always use: `git push -u origin <branch-name>`
- Branch must start with 'claude/' for AI assistant work
- Retry with exponential backoff on network failures (2s, 4s, 8s, 16s)

## Common Tasks for AI Assistants

### 1. Creating a New Blog Post

```bash
# Create new post directory
mkdir -p "content/post/$(date +%Y-%m-%d)-post-title"

# Create index.en.Rmd with proper front matter
# Include YAML front matter as shown in "Post Front Matter Format"
```

### 2. Modifying Existing Posts

- Read the post: `content/post/YYYY-MM-DD-title/index.en.Rmd`
- Make changes to the .Rmd file (not the .html)
- Rebuild if needed: The .html will be regenerated

### 3. Updating Site Configuration

- Edit `config.yaml` for site-wide settings
- Common changes: menu items, social links, theme parameters

### 4. Adding Static Assets

- Images: Place in `static/images/`
- Reference in posts: `/images/filename.png`
- CSS/JS: Place in `static/css/` or `static/js/`

### 5. Customizing Layouts

- Override theme layouts in `layouts/` directory
- Create shortcodes in `layouts/shortcodes/`
- Blogdown-specific shortcodes: `layouts/shortcodes/blogdown/`

## Important Notes

### DO:
- ✅ Always build the site before committing (generates docs/)
- ✅ Maintain proper front matter in all content files
- ✅ Use descriptive commit messages
- ✅ Test locally with `blogdown::serve_site()` when possible
- ✅ Keep the docs/ directory in version control (GitHub Pages serves from it)
- ✅ Use the specified Hugo version (0.82.0)
- ✅ Reference the central bibliography file for citations

### DON'T:
- ❌ Don't edit .html files directly (they're generated from .Rmd)
- ❌ Don't commit .Rproj.user/ directory (in .gitignore)
- ❌ Don't change Hugo version without testing
- ❌ Don't delete the docs/ directory
- ❌ Don't modify theme files directly (use layouts/ for overrides)
- ❌ Don't push to wrong branch (must start with 'claude/')

## Dependencies and Tools

### Required Software
- **R**: For blogdown and R Markdown processing
- **Hugo**: v0.82.0 (static site generator)
- **Python**: v3.x (path: /usr/local/bin/python3)
- **Git**: For version control

### R Packages
- **blogdown**: Core package for site generation
- **knitr**: R Markdown processing
- **reticulate**: Python integration (if needed)

### External Libraries (CDN)
- KaTeX: Math rendering
- Pseudocode.js: Algorithm rendering
- Font Awesome: Social icons

## Troubleshooting

### Common Issues

1. **Hugo version mismatch**:
   - Ensure Hugo 0.82.0 is used
   - Set in .Rprofile: `options(blogdown.hugo.version = "0.82.0")`

2. **R Markdown not rendering**:
   - Check that blogdown.method is set to 'html'
   - Verify Python path is correct if using reticulate

3. **Math not displaying**:
   - Ensure KaTeX scripts are included in post
   - Check params.math.enable in config.yaml

4. **Bibliography not working**:
   - Verify bibliography path in front matter
   - Check bib.bib file exists at content/post/bib.bib
   - Ensure link-citations: true in front matter

## References and Resources

- Hugo Documentation: https://gohugo.io/documentation/
- Blogdown Book: https://bookdown.org/yihui/blogdown/
- Anatole Theme: https://github.com/lxndrblz/anatole
- GitHub Pages: https://docs.github.com/en/pages

## Contact Information

- Author: Joseph Blazick
- Email: joe.blazick@yahoo.com
- LinkedIn: https://www.linkedin.com/in/joe-blazick-119307a2/
- GitHub: https://github.com/blazickjp

---

**Last Updated**: 2025-11-14

This document should be updated whenever significant changes are made to the repository structure, build process, or development workflow.
