# CoPPer submission / Overleaf package

Generated from the main CoPPer repository. This package contains manuscript
sources, exported figures/tables, bibliography, and supplementary notes only.

## Compile

```bash
cd manuscript
latexmk -pdf -interaction=nonstopmode main_wiley.tex
```

## Contents

- `manuscript/` — shared section files and journal wrapper (`main_wiley.tex`)
- `bibliography/` — BibTeX database
- `figures/`, `tables/` — code-generated assets synced from pipeline outputs
- `supplementary/` — markdown reports and experiment registry snapshot
- `MANUSCRIPT_LIMITATIONS.md` — open integration and scientific limitations

## Excluded by design

Raw data, processed datasets, experiment run artifacts, Python environments,
and large computational outputs are **not** included.

Regenerate assets in the main repository with `make paper-assets` before syncing.
