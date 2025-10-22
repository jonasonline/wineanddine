# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo-based static site blog called "Wine and Dine" focused on food, wine, and life content. The site uses the Hugo Theme Stack theme and is deployed to GitHub Pages.

## Common Commands

### Development
- `hugo server` - Start the Hugo development server with live reload
- `hugo server -D` - Start server including draft posts
- `hugo server --disableFastRender` - Start server with full rebuilds (useful when theme changes aren't reflected)

### Building
- `hugo` - Build the site for production (outputs to `public/`)
- `hugo --gc --minify` - Build with garbage collection and minification (production-ready)
- `hugo --buildDrafts` - Build including draft posts

### Content Creation
- `hugo new posts/<post-name>/index.md` - Create a new blog post
- `hugo new page/<page-name>/index.md` - Create a new page

### Deployment
The site automatically deploys to GitHub Pages via GitHub Actions on push to `main` branch. The workflow uses Hugo v0.135.0 extended edition.

## Architecture

### Site Configuration
- `hugo.toml` - Main configuration file containing:
  - Site metadata (title, baseURL)
  - Theme configuration (hugo-theme-stack)
  - Menu structure (Home, Recipes, Wine, Life, About, Search)
  - Site parameters (sidebar, footer, article settings)
  - Social media links

### Content Structure
- `content/posts/` - Blog posts organized by subdirectories (each post in its own folder with `index.md`)
- `content/page/` - Static pages (About, Search)
- Posts use front matter in TOML format (`+++`)
- Main content sections: "posts" (configured in `params.mainSections`)

### Theme
- Uses `hugo-theme-stack` as a Git submodule
- Theme files in `themes/hugo-theme-stack/`
- Custom layouts can be added to `layouts/` to override theme defaults
- Theme documentation: https://stack.jimmycai.com

### Assets & Static Files
- `static/img/` - Static images (avatar, favicons)
- `assets/` - Processed assets (contains jsconfig.json for IDE support)
- `resources/` - Hugo's resource cache (gitignored)

### Navigation Structure
The site follows the Stack theme demo with these main menu items:
- Home - Main landing page
- Archives - Chronological post listing
- Search - Content search functionality
- Links - Curated resource links

Main content category: Wine (`/categories/wine/`)
Primary content series: "Grape Escapes" - wine grape variety explorations

### Deployment Pipeline
- GitHub Actions workflow: `.github/workflows/hugo.yml`
- Triggers on push to `main` or manual dispatch
- Uses Hugo Extended v0.135.0
- Builds with `--gc --minify` flags
- Deploys to GitHub Pages automatically

## Important Configuration Details

### Front Matter Format
Posts use TOML format (`+++`) not YAML (`---`). The archetype in `archetypes/default.md` provides the template.

### Image Processing
Image processing is enabled for both cover images and content images (configured in `hugo.toml`).

### Markup Settings
- Goldmark renderer with `unsafe = true` (allows raw HTML)
- Table of contents: levels 2-4, ordered
- Syntax highlighting enabled with line numbers

### Theme Requirements
- Theme is a Git submodule - when cloning, use `git clone --recurse-submodules` or run `git submodule update --init --recursive`
- Theme is licensed under GPL v3.0
