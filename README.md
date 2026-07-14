# Siklab Core — Public Documentation

The public documentation site for **Siklab Core**, built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

> This repository contains **only public documentation**. It is intentionally separate from the Siklab Core source (which is private). Nothing here includes agent prompts, secrets, or implementation internals.

## Contents

- `docs/index.md` — landing page
- `docs/getting-started.md` — install, connect an AI engine, and create your first app
- `mkdocs.yml` — site config

## Preview locally

```bash
pip install -r requirements.txt
mkdocs serve
# open http://localhost:8000
```

## Publish (GitHub Pages)

This repo ships a workflow at `.github/workflows/deploy.yml` that builds and deploys on every push to `main`.

**One-time setup after you create the public repo:**

1. Push this folder's contents to the new **public** repository.
2. In the repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. (Optional) set `site_url` in `mkdocs.yml` to your published URL, e.g. `https://<org>.github.io/<repo>/`, and add your custom domain under Settings → Pages if you have one.

Every push to `main` then rebuilds and republishes the site automatically.

## Adding pages

1. Add a Markdown file under `docs/`.
2. Add it to the `nav:` list in `mkdocs.yml`.
