# akram.github.io

Personal site and blog, built with [Hugo](https://gohugo.io/) and the [Blowfish](https://blowfish.page/) theme.

## Deploy (GitHub Pages)

1. **Settings → Actions → General → Workflow permissions:** enable **Read and write** (needed to push `gh-pages`).
2. **Settings → Pages:** **Deploy from a branch** → branch **`gh-pages`** (the workflow publishes there).

Source lives on **`main`**; each push runs `.github/workflows/gh-pages.yml`.

## Hugo compatibility

This repo includes small **layout overrides** under `layouts/` (patched from Blowfish) so the site builds on current Hugo Extended (for example `LanguageCode` instead of removed `Locale`, and `site.Data` where the upstream theme still references `hugo.Data` in a few partials). When you update the `themes/blowfish` submodule, re-run a local `hugo` build and merge any upstream fixes into those overrides if templates drift.

## Local

Install [Hugo Extended](https://gohugo.io/installation/) (Blowfish needs extended for SCSS), **0.141+** (tested with **0.154.x**), then:

```bash
git submodule update --init --recursive
hugo server
```

Theme path: `themes/blowfish` (git submodule). Update the theme with:

```bash
git submodule update --remote --merge themes/blowfish
```
