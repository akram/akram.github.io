# akram.github.io

Personal site and blog, built with [al-folio](https://github.com/alshedivat/al-folio) and deployed to GitHub Pages from the `gh-pages` branch via Actions.

## Deploy notes

1. Repo **Settings → Actions → General → Workflow permissions**: enable **Read and write**.
2. Repo **Settings → Pages**: source **Deploy from a branch**, branch **`gh-pages`** (not `main`).

After pushing to `main`, wait for the **Deploy site** workflow, then a short **pages-build-deployment** run.

## Local preview

See [INSTALL.md](INSTALL.md) (Docker Compose is the smoothest path).
