# CLAUDE.md — AI Assistant Guide for mikelindell.info

## Project Overview

This is the source repository for **mikelindell.info**, a professional landing page for **Lindell & Associates**, an IT consulting business offering remote IT support, network infrastructure, cybersecurity, and AI strategy services.

- **Live domain:** mikelindell.info
- **GitHub Pages repo:** hisworkmanship/hisworkmanship.github.io
- **Stack:** Pure static HTML/CSS — no build tools, no frameworks, no JavaScript

---

## Repository Structure

```
/
├── Index.html      # The entire website — all HTML, CSS, and content in one file
├── README.md       # Brief repo description
└── CLAUDE.md       # This file
```

The site is intentionally minimal: one self-contained HTML file with embedded CSS. There is no separate stylesheet, no JS, no package.json, and no build step.

---

## Architecture & Conventions

### Single-File Design
All code lives in `Index.html`. CSS is embedded in a `<style>` block in the `<head>`. Do not create separate `.css` or `.js` files unless the user explicitly requests a structural change.

### CSS Variables
The design system is defined via CSS custom properties on `:root`:

```css
--bg-color: #ffffff
--text-main: #1a1a1a
--text-muted: #666666
--accent: #000000
--spacing: 40px
```

Always use these variables when adding new styles. Do not hardcode raw color values or spacing that duplicates these.

### Typography
- **Font:** Inter (loaded from Google Fonts), weights 300 / 400 / 600
- Headings use letter-spacing and weight variations for hierarchy
- Body text uses `--text-muted` for secondary copy

### Layout
- Max content width: `1200px`, centered with `margin: 0 auto`
- Horizontal padding: `5%` on `.container`
- Services grid: CSS Grid with `auto-fit` + `minmax(280px, 1fr)` for responsive columns
- Mobile breakpoint: `max-width: 768px`

### Design Aesthetic
Minimalist, high-end, corporate. Favor whitespace, clean lines, and restrained color use. Avoid gradients, drop shadows, or decorative effects unless explicitly requested.

---

## Page Content Sections

| Section | Element | Notes |
|---------|---------|-------|
| Header | `.header` | Displays "Lindell & Associates" brand name |
| Hero | `.hero` | Headline, tagline, CTA button |
| Services | `.services` grid | Three cards: Technical Infrastructure, Security & Strategy, Remote Support |
| Footer | `footer` | Copyright line |

---

## Known Placeholders (Must Update)

- **CTA email:** `mailto:your-email@yourdomain.com` in the "Request a Consultation" button — replace with real contact address
- **README typo:** "Gihub" should be "Github"

---

## Development Workflow

### Branching
- **Production branch:** `main` — deploys to GitHub Pages / mikelindell.info
- **Feature branches:** `claude/<description>` pattern (e.g., `claude/add-claude-documentation-OKWMQ`)
- Always develop on a feature branch; open a PR to merge into `main`

### No Build Step
There is no `npm install`, no compilation, no bundling. Edit `Index.html` directly and open it in a browser to preview.

### Deployment
GitHub Pages serves `main` automatically. Merging to `main` deploys the site.

---

## AI Assistant Guidelines

1. **Read before editing.** Always read `Index.html` before making changes.
2. **Preserve design language.** Keep the minimalist, monochrome aesthetic unless the user asks for a style change.
3. **Stay in-file.** Add new styles to the existing `<style>` block; do not create new files without a clear reason.
4. **Use CSS variables.** Reference `--bg-color`, `--text-main`, `--text-muted`, `--accent`, `--spacing` consistently.
5. **No JS by default.** This is a static page. Do not add JavaScript unless explicitly requested.
6. **Mobile-first considerations.** Any new layout additions should be responsive; use the existing 768px breakpoint.
7. **Do not over-engineer.** This is a simple landing page. Avoid introducing frameworks, npm packages, or complex architecture.
8. **Branch correctly.** All changes should be committed to a feature branch, not directly to `main`.
