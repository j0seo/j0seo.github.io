# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static academic profile website (forked from [Jon Barron's template](https://github.com/jonbarron/jonbarron_website)), hosted via GitHub Pages. There is no build system, bundler, or framework — it is plain HTML/CSS/JS served directly.

## Architecture

- **`index.html`** (~4500 lines): The entire site in a single HTML file. Contains the profile header, research publications list, service/teaching sections, and inline JavaScript for image hover effects.
- **`stylesheet.css`**: Global styles using the Lato font family. Defines paper entry layout (`.one`/`.two` for hover image swap, `.papertitle`, `.highlight` for featured papers).
- **`images/`**: Publication thumbnails and hover images (typically `*_before.jpg` / `*_after.jpg` pairs, or still/video pairs).
- **`data/`**: BibTeX files for citations, CV PDF, and bio text.
- **`mipnerf/`, `mipnerf360/`, `zipnerf/`**: Standalone project pages, each with their own `index.html`, `css/`, `js/`, and `img/` directories.
- **`CNAME`**: Custom domain configuration for GitHub Pages.

## Development

No build or install step. Open `index.html` in a browser or use any local HTTP server:

```
python3 -m http.server 8000
```

## Publication Entry Pattern

Each paper in `index.html` follows this structure:
1. A `<tr>` with `onmouseout`/`onmouseover` handlers (add `bgcolor="#ffffd0"` for highlighted papers)
2. Left cell: image container using `.one`/`.two` divs for hover effect
3. Inline `<script>` defining `{name}_start()` and `{name}_stop()` functions that toggle opacity
4. Right cell: paper title (`.papertitle`), author list (self-citations in `<strong>`), venue/year in `<em>`, links, and description

When adding a new publication, copy an existing `<tr>` block and update the ID, function names, images, and metadata. Place new entries at the top of the publications table.
