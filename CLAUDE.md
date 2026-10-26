# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo static site blog built with the Hugo Blox - Tailwind theme. The site is for Zachary Witte, a software developer focused on building tools and exploring AI integrations. The site includes pages for About, Projects, and Blog posts, and is automatically deployed to GitHub Pages.

## Architecture

- **Static Site Generator**: Hugo v0.146.0 (extended version)
- **Theme**: Hugo Blox - Tailwind (installed as Hugo module)
- **Module System**: Uses Hugo modules instead of git submodules
- **Content Structure**:
  - `content/_index.md` - Landing page with hero sections
  - `content/about.md` - About page
  - `content/projects.md` - Projects page
  - `content/posts/` - Blog posts directory (currently empty)
- **Configuration**: `hugo.toml` - Main Hugo configuration file
- **Deployment**: Automatic GitHub Actions workflow to GitHub Pages

## Development Commands

Hugo must be installed locally for development. Common Hugo commands:

- `hugo serve` - Start development server with live reload
- `hugo serve -D` - Include draft content in development server
- `hugo mod get` - Download Hugo modules
- `hugo mod tidy` - Update and clean Hugo modules
- `hugo` - Build static site to `public/` directory
- `hugo --gc --minify` - Build with garbage collection and minification
- `hugo new posts/post-name.md` - Create new blog post

## Content Creation

- Blog posts go in `content/posts/` directory
- Use front matter with `title`, `date`, `draft` fields
- Set `draft: false` when ready to publish
- The home page uses Hugo Blox sections/blocks system for layout
- Hugo Blox supports various block types: hero, markdown, portfolio, etc.

### Rules for every new blog post

Internal links and search/AI discoverability are not automatic on this site (the theme only adds previous/next links at the bottom of a post), so do these by hand for every new post in `content/posts/`:

- **Link to related posts in the body.** Add at least 2 inline links from the new post to existing posts it relates to, written naturally in the text (e.g. "I wrote about this in [Post Title](/posts/post-slug/)"). Use site-relative paths ending in a slash, matching the post's filename without `.md`.
- **Link back from the older posts.** Add a link from at least one relevant existing post to the new post, so the new post is not an orphan and older posts point forward to it.
- **Check that every link resolves.** The slug must match an existing file in `content/posts/`, and the build must still succeed.
- **Add a `description` to the front matter**: one plain sentence summarizing the post. Search engines and AI tools use it as the snippet.
- **Keep the email address and employer name out of metadata.** Never put an email address anywhere on the site. Do not name DCS Corporation in page `description`s or structured data (`layouts/partials/extend_head.html`); on the About page it appears only in the "By day" paragraph.

## Deployment

The site automatically deploys to GitHub Pages via `.github/workflows/hugo.yml` when changes are pushed to the main branch. The workflow:
1. Installs Hugo v0.146.0 extended
2. Checks out code (no submodules needed)
3. Runs `hugo mod get` to download modules
4. Builds site with production settings
5. Deploys to GitHub Pages

## Theme Configuration

The Hugo Blox theme is configured in `hugo.toml` with:
- Minimal theme variant
- Ocean color theme
- Module imports for Hugo Blox components
- Three main menu items: About, Projects, Blog

## Site Structure

- Base URL: https://zacharywitte.com/
- Main navigation: About (/about/), Projects (/projects/), Blog (/posts/)
- Landing page with hero section and blocks
- The site focuses on software development, AI tools, and MCP servers