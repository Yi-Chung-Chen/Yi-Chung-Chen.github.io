# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is an **al-folio** Jekyll academic website repository. Al-folio is a clean, responsive Jekyll theme designed for academics to showcase their research, publications, CV, and blog posts. The site is deployed to GitHub Pages.

## Development Commands

### Local Development (Docker - Recommended)
```bash
# Pull and run the site locally
docker compose pull
docker compose up

# Build with slim image (faster)
docker compose -f docker-compose-slim.yml up

# Build custom image
docker compose up --build
```

The site will be available at `http://localhost:8080` with live reload enabled.

### Local Development (Legacy)
```bash
# Install dependencies
bundle install
pip install jupyter

# Serve locally
bundle exec jekyll serve
# Available at http://localhost:4000
```

### Build and Deployment
```bash
# Build static site
bundle exec jekyll build

# Purge unused CSS (optional)
purgecss -c purgecss.config.js

# Format code
npm run prettier
```

### Code Quality
```bash
# Prettier formatting (JavaScript/Liquid)
npm run prettier

# Jekyll build (includes minification)
bundle exec jekyll build
```

## Repository Structure

### Core Jekyll Structure
- `_config.yml` - Main Jekyll configuration
- `_pages/` - Site pages (about, CV, publications, etc.)
- `_posts/` - Blog posts
- `_projects/` - Project showcases
- `_news/` - News/announcements
- `_books/` - Book reviews
- `_layouts/` - Page layouts
- `_includes/` - Reusable template components
- `_sass/` - SCSS stylesheets
- `_data/` - Data files (CV, repositories, etc.)
- `_bibliography/papers.bib` - BibTeX publications

### Assets and Content
- `assets/` - Images, CSS, JS, PDFs, JSON data
- `_site/` - Generated static site (excluded from git)

### Configuration Files
- `Gemfile` - Ruby dependencies
- `package.json` - Node.js dependencies (Prettier)
- `docker-compose.yml` / `docker-compose-slim.yml` - Docker setup
- `purgecss.config.js` - CSS purging configuration

### Scripts
- `bin/entry_point.sh` - Docker entrypoint with auto-restart
- `.github/workflows/` - GitHub Actions for deployment and CI

## Key Architecture Concepts

### Jekyll Scholar Integration
- Publications are managed via BibTeX in `_bibliography/papers.bib`
- Automatic publication page generation with customizable badges
- Support for PDF links, abstracts, and additional metadata

### Multi-Collection System
- **News**: Announcements displayed on homepage
- **Projects**: Portfolio items with grid layout
- **Books**: Book reviews with rating system
- **Posts**: Blog posts with pagination and tagging

### Responsive Design
- Mobile-first Bootstrap-based layout
- Dark/light mode toggle
- Optimized images with WebP support via Jekyll ImageMagick

### Content Management
- YAML front matter for page configuration
- Liquid templating for dynamic content
- Support for math (MathJax), code highlighting, and interactive elements

## Customization Points

### Personal Information
- Update `_config.yml` with your details (name, URL, social links)
- Replace `assets/img/prof_pic.jpg` with your photo
- Edit `_pages/about.md` for homepage content
- Modify `_data/cv.yml` or `assets/json/resume.json` for CV data

### Content Areas
- **Publications**: Add entries to `_bibliography/papers.bib`
- **Projects**: Create markdown files in `_projects/`
- **Blog Posts**: Add to `_posts/` with date prefix
- **News**: Add announcements to `_news/`

### Styling
- Theme colors in `_sass/_themes.scss`
- Custom CSS in `_sass/_base.scss`
- Layout modifications in `_layouts/` and `_includes/`

## Deployment

The site uses GitHub Actions for automatic deployment:
1. Push to main branch triggers `.github/workflows/deploy.yml`
2. Site builds and deploys to `gh-pages` branch
3. GitHub Pages serves from `gh-pages` branch

Manual deployment: Use Actions tab → "Deploy" → "Run workflow"

## Important Notes

- This is a personal website fork, currently configured for "Yi-Chung (Andrew) Chen"
- The repository name suggests it's hosted at `Yi-Chung-Chen.github.io`
- Most sample content (Einstein references) should be replaced with actual personal content
- The site includes extensive documentation in README.md, INSTALL.md, and CUSTOMIZE.md for detailed setup instructions