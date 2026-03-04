# NoSignal

*[English](README.md) | [中文](README.zh.md)*

A personal blog built with [Astro](https://astro.build), featuring [Keystatic](https://keystatic.com) as the content management system.

## Features

- **Astro** - Static site generator with excellent performance
- **Keystatic** - Git-based CMS for content management
- **Markdoc** - Content format with custom components
- **Tailwind CSS** - Utility-first CSS framework
- **Vercel** - Deployment platform
- **Pagefind** - Static search functionality

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/OtavioLeonardo/NoSignal-Blog.git
cd NoSignal-Blog

# Install dependencies
npm install

# Start development server
npm run dev
```

### Build for Production

```bash
npm run build
```

### Deployment

This project is configured for deployment on [Vercel](https://vercel.com). Simply push your changes to GitHub and Vercel will automatically deploy.

## Site Configuration

### Basic Settings

Edit `src/utils/AppConfig.ts`:

```typescript
export const AppConfig = {
    site_name: 'NoSignal',
    title: 'NoSignal | Just Write',
    description: 'Your site description here',
    author: 'Your Name',
    locale_region: 'zh-CN',
    locale: 'zh'
};
```

### SEO & Social

- Site URL: Edit `astro.config.mjs` → `site` field
- Favicon: Replace `public/favicon.svg`
- Social images: Edit `public/showcase.jpg` and `public/showcase.png`

### Navigation

Edit `src/components/Navbar.astro` to modify navigation links.

## Content Management

### Using Keystatic Admin Panel

Run the development server, then visit:
```
http://localhost:4321/keystatic
```

#### Posts Collection

Create new blog posts at `src/content/posts/*.mdoc`

**Frontmatter Fields:**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `title` | string | Yes | Post title |
| `series` | string | No | Series name (groups related posts) |
| `layout` | string | Yes | Fixed: `../../layouts/post.astro` |
| `pubDate` | date | Yes | Publication date (YYYY-MM-DD) |
| `description` | string | No | SEO description |
| `excerpt` | string | No | Post summary for listings |
| `author` | string | Yes | Author name |
| `isPinned` | boolean | No | Pin post to top |
| `image` | object | No | Cover image |
| `tags` | array | No | Tags for categorization |
| `updates` | array | No | Update history |

**Example:**

```yaml
---
title: My First Post
series: Tutorial
layout: ../../layouts/post.astro
pubDate: 2026-03-04
description: A brief description
excerpt: >-
  This is a longer summary that appears in post listings.
author: Your Name
isPinned: false
image: {}
tags:
  - Tutorial
  - Example
updates:
  - date: 2026-03-04
    title: Initial version
    content: First draft published
---
```

#### Diary Collection

Quick thoughts and daily notes at `src/content/diary/*.mdoc`

**Frontmatter Fields:**

| Field | Type | Required |
|-------|------|----------|
| `title` | string | Yes |
| `pubDate` | date | Yes |
| `description` | string | No |

#### Now Page

The "Now" page shows what you're currently working on. Edit at `src/content/pages/now.mdoc`

**Fields:**

- `title`: Always "Now"
- `updatedDate`: Last update date
- `content`: Markdown content

### Writing Content Manually

You can also create content files directly in your editor:

```
src/content/posts/my-post.mdoc
src/content/diary/2026-03-04.mdoc
```

### Custom Components

This blog supports custom Markdoc components:

#### Aside (Tip Box)

```markdoc
{% aside type="tip" title="Helpful Tip" %}
Your content here
{% /aside %}
```

Types: `tip`, `note`, `danger`, `caution`

## Development

### Project Structure

```
no-signal/
├── src/
│   ├── content/
│   │   ├── posts/      # Blog posts
│   │   ├── diary/      # Daily notes
│   │   └── pages/      # Static pages (now)
│   ├── components/     # Astro components
│   ├── layouts/       # Page layouts
│   ├── pages/          # Route pages
│   ├── styles/         # Global styles
│   └── utils/          # Utilities & config
├── public/             # Static assets
├── keystatic.config.tsx # CMS configuration
└── astro.config.mjs     # Astro config
```

### Adding New Tags

1. Create a new tag using the post editor
2. Tags will automatically appear on the tags index page

### Search

The site uses Pagefind for static search. Search index is built during the build process.

## Troubleshooting

### Keystatic not loading

Make sure you're running the development server:
```bash
npm run dev
```

### Build errors

Clear the cache:
```bash
rm -rf node_modules/.astro
```

### Content not appearing

- Check the frontmatter format
- Ensure the file is in the correct directory
- Verify the `layout` path is correct

## License

MIT

## Credits

Built with [Astro](https://astro.build), [Keystatic](https://keystatic.com), and [Tailwind CSS](https://tailwindcss.com).

