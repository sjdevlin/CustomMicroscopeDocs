# Documentation Maintenance

This site is a MkDocs documentation repository hosted from GitHub and published with GitHub Pages.

## Where the docs live

- Repository: [sjdevlin/CustomMicroscopeDocs](https://github.com/sjdevlin/CustomMicroscopeDocs)
- Published site: [https://sjdevlin.github.io/CustomMicroscopeDocs/](https://sjdevlin.github.io/CustomMicroscopeDocs/)
- Main content directory: `docs/`
- Site navigation: `mkdocs.yml`
- Deployment workflow: `.github/workflows/pages.yml`

## How to edit

1. Edit Markdown files in `docs/`.
2. Add screenshots or photos under `docs/assets/images/`.
3. Update navigation in `mkdocs.yml` if a page is added, renamed, or reordered.
4. Preview locally with `mkdocs serve`.
5. Commit and push to `main` to trigger GitHub Pages deployment.

## Local preview

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

## What "code as docs" means here

This project does not treat documentation as a separate artifact. The docs sit alongside the source materials that define how the microscope is actually used:

- GUI screenshots from the ODT manuals
- XML scripts such as `temika.xml` and `scriptfile.xml`
- Python control code such as `temika_comms.py` and the controller modules

When control logic changes, update the matching documentation page in the same revision. The goal is to keep operational guidance, example code, and actual automation syntax aligned.

## Practical rules for future editors

- Prefer short, explicit operating instructions over generic prose.
- Keep file and command names literal: `temika`, XML tags, camera feature names, and axis names should match the real system.
- If a screenshot cannot be extracted cleanly, leave a visible placeholder with the intended filename and caption.
- Record unknown optical specifications as `TODO` tables rather than guessing.
