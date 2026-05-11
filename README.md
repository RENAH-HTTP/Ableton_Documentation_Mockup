# Live Documentation (Mockup)

**Live site: [https://renah-http.github.io/Documentation_Example/](https://renah-http.github.io/Documentation_Example/)**

> If you don't see the latest content, refresh the page (Ctrl+Shift+R / Cmd+Shift+R).

---

A documentation mockup for Ableton Live, built with [MkDocs](https://www.mkdocs.org/) and the [Material theme](https://squidfunk.github.io/mkdocs-material/). Created for interview purposes to demonstrate structure, tone, and how I would approach writing documentation for software workflows, audio effects, and release notes.

## Contents

- **Manual** — Audio effects reference and workflow documentation
- **Release Notes** — Live 12 release notes

## Local Development

**Prerequisites:** Python 3.x

1. Create and activate a virtual environment:

   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # macOS/Linux
   source venv/bin/activate
   ```

2. Install dependencies:

   ```bash
   pip install mkdocs mkdocs-material
   ```

3. Serve locally:

   ```bash
   mkdocs serve
   ```

   The site will be available at `http://127.0.0.1:9001`.

## Deployment

Pushes to `main` automatically build and deploy to GitHub Pages via the workflow in [.github/workflows/ci.yml](.github/workflows/ci.yml).
