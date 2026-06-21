# CoPPer bibliography

BibTeX entries for Paper 1 live in `references.bib`.

## Source of entries

| Entry | Source | Status |
|-------|--------|--------|
| `hardaker2015` | Manually curated from known agricultural risk text | Verify edition/publisher |
| `Bradford1997` | Manually curated placeholder | Verify DOI and pages |
| `TODO_forecasting_placeholder` | Placeholder | **Incomplete — replace** |
| `copper2026software` | Project metadata | Add Zenodo/repo DOI at release |

Entries were **not** bulk-exported from Zotero in this scaffold. Before submission:

1. Export verified entries from Zotero/Crossref/DOI lookup.
2. Remove or complete all `TODO` entries.
3. Confirm journal citation style (`author_year` in `configs/manuscript.yaml`).
4. Run `make paper-pdf` and fix undefined citations reported by `make paper-check`.

## Final verification checklist

- [ ] Every `\cite{}` key in `paper/manuscript/` appears in `references.bib`
- [ ] No placeholder `TODO_*` keys remain
- [ ] Publisher template bibliography style matches target journal
- [ ] Software and data citations match journal data-availability requirements
