# Zachary Witte's Blog

A personal blog built with Hugo, showcasing projects, thoughts on software development, and explorations in AI integrations.

## About

This is the personal website of Zachary Witte, a software developer focused on building tools and exploring AI integrations. The site includes:

- **About**: Personal background and current focus areas
- **Projects**: Showcase of MCP servers and AI-powered applications
- **Blog**: Technical writing and project documentation

## Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) v0.146.0 or later
- Git (for theme management)

## Local Development

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd zacharywitte-blog
   ```

2. **Initialize git submodules** (for themes):
   ```bash
   git submodule update --init --recursive
   ```

3. **Start the development server**:
   ```bash
   hugo serve
   ```

   The site will be available at `http://localhost:1313`

4. **Include draft content** (optional):
   ```bash
   hugo serve -D
   ```

## Creating Content

### New Blog Post
```bash
hugo new posts/your-post-name.md
```

### New Project Page
```bash
hugo new projects/project-name.md
```

## Building for Production

```bash
hugo --gc --minify
```

The built site will be in the `public/` directory.

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the main branch via GitHub Actions.

## Theme

This site uses the Hugo Blox - Tailwind theme for a modern, responsive design with Tailwind CSS styling.