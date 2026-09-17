# Agentic Systems — reference guide

A self-contained, single-page reference covering how agentic systems are built:
models, context, MCP, agents and sub-agents, memory, knowledge, token economics,
storage and orchestration, plus the platform configuration surfaces for Claude
Code and OpenAI Codex. No build step, no framework, no external JavaScript.

Ten views: Architecture, Concepts, Topologies, Workflows, Playbooks, Runbooks,
Checklist, Glossary, Metrics, Platforms. Eight interactive diagrams, 21 concept
cards, 10 playbooks, 10 runbooks, 51 readiness checks, 76 glossary terms.

## Contents

| File | Purpose |
| --- | --- |
| `index.htm` | The guide. Everything inline: markup, styles, scripts, diagrams. |
| `index.html` | Redirect to `index.htm` — see the note below. |
| `404.html` | Styled not-found page. |
| `favicon.ico` | Multi-size ICO (16/32/48). |
| `favicon.svg` | Vector favicon for modern browsers. |
| `favicon-16x16.png`, `favicon-32x32.png` | PNG fallbacks. |
| `apple-touch-icon.png` | 180×180 home-screen icon for iOS. |
| `icon-192x192.png`, `icon-512x512.png` | PWA / Android icons; the 512 doubles as maskable. |
| `og-image.png` | 1200×630 social share card. |
| `site.webmanifest` | Web app manifest, `start_url` set to `index.htm`. |
| `robots.txt` | Crawl directives, points at the sitemap. |
| `sitemap.xml` | Single-URL sitemap. |
| `.nojekyll` | Stops GitHub Pages running the files through Jekyll. |

## Why there is both an index.htm and an index.html

The guide itself is `index.htm`, as requested. GitHub Pages resolves a bare
directory URL to `index.html`, so a visitor to
`https://USERNAME.github.io/agentic-systems/` would otherwise get a 404. The
`index.html` here is a 1KB redirect that sends them straight to `index.htm`. It
carries `noindex` and a canonical pointing at `index.htm`, so search engines
index the guide rather than the redirect.

If you would rather have a single file, rename `index.htm` to `index.html`,
delete the redirect, and change `start_url` in `site.webmanifest`, the `<loc>`
in `sitemap.xml`, the canonical and `og:url` in the page head, and the link in
`404.html`.

## Publishing to GitHub Pages

1. Create a repository — `agentic-systems` is assumed below.
2. Unzip this package into the repository root and push to `main`.
3. In **Settings → Pages**, set the source to **Deploy from a branch**, branch
   `main`, folder `/ (root)`.
4. The guide will be live at `https://USERNAME.github.io/agentic-systems/`.

## Set your URL before publishing

Absolute URLs are required for the canonical tag, the Open Graph image and the
sitemap, so five files carry a `USERNAME` placeholder: `index.htm`,
`index.html`, `robots.txt`, `sitemap.xml` and this README. Replace it in one
pass from the repository root:

```bash
# macOS
sed -i '' 's|USERNAME.github.io/agentic-systems|YOURNAME.github.io/YOURREPO|g' index.htm index.html robots.txt sitemap.xml

# Linux
sed -i 's|USERNAME.github.io/agentic-systems|YOURNAME.github.io/YOURREPO|g' index.htm index.html robots.txt sitemap.xml
```

Publishing to a user site (`USERNAME.github.io` with no subpath)? Drop the
repository segment from the replacement string.

Every icon and the manifest use relative paths, so those work unchanged at any
subpath.

## Notes

- Fonts (IBM Plex Sans and Mono) load from Google Fonts. The guide degrades to
  system sans and monospace if that request is blocked.
- Dark and light themes are both supported, toggled from the header. The 404
  page follows the operating-system preference instead.
- Opening `index.htm` directly from the filesystem works; no server needed.
- The Platforms view documents fast-moving product surfaces. It was verified
  against `code.claude.com/docs` and `developers.openai.com` in September 2026;
  check those before relying on a specific key.
