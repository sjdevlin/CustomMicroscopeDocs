# CustomMicroscopeDocs

Documentation site for a custom-built microscope using MkDocs + Material.

## What this repo is for

This repository is a code-as-docs system for microscope build records, operating SOPs, calibration protocols, and maintenance history.

## Suggested first workflow

1. Complete `docs/data-capture-pack.md` during a focused lab session.
2. Fill `docs/overview.md` and `docs/bom.md` with measured values and real part numbers.
3. Validate one end-to-end run using `docs/operation-sops.md`.
4. Record outcomes in `docs/maintenance-change-log.md`.

## Local preview

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

Open <http://127.0.0.1:8000>.

## Build

```bash
source .venv/bin/activate
mkdocs build
```

## Publish

Publishing is automated via GitHub Actions in `.github/workflows/pages.yml`.
In repository settings, enable GitHub Pages and choose **GitHub Actions** as the source.
