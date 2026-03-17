# TemikaMicroscopeDocs

Documentation site for the Temika microscope using MkDocs + Material.

## What this repo is for

This repository is a code-as-docs system for the Temika microscope user guide, control reference, automation examples, troubleshooting notes, and maintenance documentation.

## Site structure

- `docs/overview.md`
- `docs/operating-via-user-interface/basic-operation.md`
- `docs/operating-via-user-interface/advanced-controls.md`
- `docs/programmatic-control/xml-script.md`
- `docs/programmatic-control/software.md`
- `docs/programmatic-control/templates.md`
- `docs/troubleshooting.md`
- `docs/maintenance.md`
- `docs/documentation-maintenance.md`

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
