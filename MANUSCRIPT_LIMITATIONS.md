# Manuscript Limitations and Open Issues

## 2026-06-21 — Manuscript integration preflight

Implementation of the LaTeX manuscript layer, results manifest, asset export, Makefile targets,
and Overleaf submission packaging. See also `paper/OVERLEAF_ASSESSMENT.md`.

### LIM-001 — Target journal is still a shortlist, not a single frozen journal

- **Severity:** Medium
- **Area:** journal-template
- **Observed issue:** CoPPer currently has multiple plausible targets: Journal of Agricultural Economics, Agricultural Economics, Agricultural Systems, and aspirational AJAE. These have different publishers and LaTeX workflows.
- **Why it matters:** A Wiley manuscript package and an Elsevier manuscript package are not interchangeable. Citation style, class files, submission assets, and supplementary material expectations may differ.
- **Immediate mitigation:** Use a common-section LaTeX architecture with journal-specific wrappers: Wiley, Elsevier, and generic preprint.
- **Owner action required:** yes
- **Status:** open

### LIM-002 — No journal-specific Wiley template confirmed for Journal of Agricultural Economics

- **Severity:** Medium
- **Area:** journal-template
- **Observed issue:** No local Wiley LaTeX template package found under `paper/journal_templates/wiley/`. Using `article.cls` fallback until the official Wiley template is downloaded.
- **Why it matters:** A generic Wiley template may be acceptable for drafting, but final submission should follow the journal’s current author guidelines.
- **Immediate mitigation:** Download the official Wiley template package directly from Wiley and check the journal’s current Author Guidelines before submission.
- **Owner action required:** yes
- **Status:** open

### LIM-003 — Agricultural Economics uses Wiley-style workflow but journal-specific template requirements remain to be verified

- **Severity:** Medium
- **Area:** journal-template
- **Observed issue:** Agricultural Economics is handled through Wiley/IAAE author guidance, but a dedicated LaTeX template requirement was not confirmed.
- **Why it matters:** The manuscript should not assume final formatting requirements from a generic publisher template alone.
- **Immediate mitigation:** Use the same Wiley-wrapper strategy as for Journal of Agricultural Economics until a target is frozen.
- **Owner action required:** yes
- **Status:** open

### LIM-004 — Agricultural Systems requires Elsevier workflow rather than Wiley workflow

- **Severity:** Medium
- **Area:** journal-template
- **Observed issue:** Agricultural Systems is an Elsevier journal and should use Elsevier’s LaTeX workflow, typically `elsarticle`, if selected.
- **Why it matters:** If the paper is redirected to Agricultural Systems, the manuscript wrapper, citation style, and submission package need to switch from Wiley to Elsevier.
- **Immediate mitigation:** Build an Elsevier wrapper using `elsarticle` and shared section files.
- **Owner action required:** yes
- **Status:** open

### LIM-005 — AJAE has moved from Oxford Academic to Wiley

- **Severity:** Medium
- **Area:** journal-template
- **Observed issue:** AJAE has historical Oxford Academic pages, but the journal is now published by Wiley.
- **Why it matters:** Old OUP templates should not be used for AJAE unless explicitly required by the current publisher workflow.
- **Immediate mitigation:** Treat AJAE as a Wiley target for manuscript-template purposes.
- **Owner action required:** yes
- **Status:** open

### LIM-006 — Official template files should be downloaded locally, not vendored blindly

- **Severity:** Medium
- **Area:** journal-template
- **Observed issue:** Publisher template packages may include class files, style files, or fonts subject to license restrictions.
- **Why it matters:** The repository should not redistribute publisher assets or font files unless the license clearly permits it.
- **Immediate mitigation:** Store download instructions in `paper/journal_templates/README.md`; do not commit proprietary fonts.
- **Owner action required:** yes
- **Status:** open

### LIM-007 — Overleaf GitHub synchronization is not ideal for the full research repository

- **Severity:** High
- **Area:** Overleaf
- **Observed issue:** The full CoPPer repository may contain raw data, processed data, logs, experiments, code, and large generated artifacts that should not be synced to Overleaf.
- **Why it matters:** Overleaf projects should remain lightweight manuscript workspaces, not full computational research repositories.
- **Immediate mitigation:** Use a separate manuscript-only repository or submodule containing only `.tex`, `.bib`, figures, tables, and supplementary files. See `paper/OVERLEAF_SYNC.md`.
- **Owner action required:** yes
- **Status:** open

### LIM-008 — Overleaf GitHub Sync is premium and has setup constraints

- **Severity:** Medium
- **Area:** Overleaf
- **Observed issue:** Overleaf documents GitHub Synchronization as a premium Cloud feature. It cannot link an existing Overleaf project to an existing GitHub repository directly.
- **Why it matters:** Repository architecture must be designed before starting Overleaf collaboration.
- **Immediate mitigation:** Create the GitHub manuscript repository first, then create the Overleaf project from it.
- **Owner action required:** yes
- **Status:** open

### LIM-010 — Result-to-claim traceability must be enforced

- **Severity:** High
- **Area:** reproducibility
- **Observed issue:** Manuscripts often drift from code outputs when authors manually copy numbers into text.
- **Why it matters:** This undermines reproducibility and creates submission risk.
- **Immediate mitigation:** Populate tables/figures from generated outputs only; use `\coppertodo{}` placeholders for missing results; run `make paper-check`.
- **Owner action required:** no
- **Status:** mitigated

### LIM-011 — Journal-specific supplementary-material expectations remain to be checked

- **Severity:** Medium
- **Area:** LaTeX
- **Observed issue:** Data/code/supplementary appendix expectations differ across Wiley, Elsevier, and AJAE.
- **Why it matters:** The reproducibility appendix and data availability statement may require journal-specific wording.
- **Immediate mitigation:** Create a generic reproducibility statement now and finalize after target-journal selection.
- **Owner action required:** yes
- **Status:** open

### LIM-012 — No claim of submission readiness yet

- **Severity:** Blocking
- **Area:** LaTeX
- **Observed issue:** Until LaTeX compiles locally, all required results are synced, and the target journal is frozen, the manuscript cannot be submission-ready.
- **Why it matters:** Avoids premature claims and prevents accidental overstatement.
- **Immediate mitigation:** Label the current manuscript layer as “draft automation scaffold.”
- **Owner action required:** no
- **Status:** open

### LIM-013 — Local TeX distribution not available in CI/dev sandbox

- **Severity:** High
- **Area:** LaTeX
- **Observed issue:** `pdflatex` and `latexmk` were not found on the build host used for manuscript integration.
- **Why it matters:** `make paper-pdf` cannot be verified until a TeX Live or MacTeX installation is available.
- **Immediate mitigation:** Install TeX Live locally and run `make paper-pdf`; log compile errors to this file.
- **Owner action required:** yes
- **Status:** closed

### LIM-014 — Incomplete bibliography metadata

- **Severity:** Medium
- **Area:** LaTeX
- **Observed issue:** `paper/bibliography/references.bib` contains TODO placeholder entries and manually curated stubs without verified DOIs.
- **Why it matters:** Undefined or incorrect citations block submission.
- **Immediate mitigation:** Replace placeholders via Zotero/Crossref export before submission; run `make paper-check`.
- **Owner action required:** yes
- **Status:** open

### LIM-015 — Missing pipeline export: price summary by crop

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: `outputs/tables/price_summary_by_crop.tex`
- **Why it matters:** Required for manuscript data/descriptive sections.
- **Immediate mitigation:** Add table export to the data pipeline; `\coppertodo{}` placeholder inserted in Section~\ref{sec:data}.
- **Owner action required:** no
- **Status:** closed

### LIM-016 — Missing pipeline export: cost summary by crop

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: `outputs/tables/cost_summary_by_crop.tex`
- **Why it matters:** Required for manuscript data/descriptive sections.
- **Immediate mitigation:** Add table export to the data pipeline; `\coppertodo{}` placeholder inserted in Section~\ref{sec:data}.
- **Owner action required:** no
- **Status:** closed

### LIM-017 — Missing pipeline export: profit correlation matrix

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected sources not found: `outputs/tables/correlation_matrix_profits.tex` and `outputs/figures/publication/correlation_matrix_profits.pdf`
- **Why it matters:** Required for methods/optimization discussion.
- **Immediate mitigation:** Export correlation matrix from optimization module; `\coppertodo{}` in Section~\ref{sec:methods}.
- **Owner action required:** no
- **Status:** closed

### LIM-018 — Missing pipeline export: dedicated Gini summary table

- **Severity:** Medium
- **Area:** results
- **Observed issue:** Expected source not found: `outputs/tables/gini_coefficient_summary.tex`. Gini metrics appear in `welfare_sharing_comparison` but not as a standalone table.
- **Why it matters:** Charter lists a dedicated Gini table; partial coverage may suffice for drafting.
- **Immediate mitigation:** Use `welfare_sharing_comparison` for now or add dedicated export.
- **Owner action required:** no
- **Status:** closed

### LIM-019 — Missing pipeline export: member-level welfare change table

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: `outputs/tables/member_welfare_change.tex`
- **Why it matters:** Required for welfare results (H3).
- **Immediate mitigation:** Extend welfare module export; `\coppertodo{}` in Section~\ref{sec:results}.
- **Owner action required:** no
- **Status:** closed

### LIM-020 — Missing pipeline export: CVaR / downside-risk summary table

- **Severity:** Medium
- **Area:** results
- **Observed issue:** Expected source not found: `outputs/tables/cvar_downside_risk.tex`. Partial CVaR metrics exist in `backtest_summary`.
- **Why it matters:** Charter lists a dedicated downside-risk table.
- **Immediate mitigation:** Add dedicated export or cite `backtest_summary` only with traceable numbers.
- **Owner action required:** no
- **Status:** closed

### LIM-021 — Missing pipeline export: crop area trends figure

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: `outputs/figures/publication/crop_area_trends.pdf`
- **Why it matters:** Required for crop-universe data section.
- **Immediate mitigation:** Add figure to `scripts/make_figures.py`; `\coppertodo{}` in Section~\ref{sec:data}.
- **Owner action required:** no
- **Status:** closed

### LIM-022 — No local Wiley LaTeX template package

- **Severity:** Medium
- **Area:** journal-template
- **Observed issue:** No local Wiley LaTeX template package found under paper/journal_templates/wiley/.
- **Why it matters:** Draft manuscript uses article.cls fallback until official template is downloaded.
- **Immediate mitigation:** Download Wiley template locally; see paper/journal_templates/README.md.
- **Owner action required:** yes
- **Status:** open

### LIM-023 — Missing manuscript table: price_summary_by_crop

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/tables/price_summary_by_crop.tex
- **Why it matters:** Required for manuscript sections: data, descriptive
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open

### LIM-024 — Missing manuscript table: cost_summary_by_crop

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/tables/cost_summary_by_crop.tex
- **Why it matters:** Required for manuscript sections: data, descriptive
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open

### LIM-025 — Missing manuscript table: correlation_matrix_profits

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/tables/correlation_matrix_profits.tex
- **Why it matters:** Required for manuscript sections: methods, optimization
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open

### LIM-026 — Missing manuscript table: gini_coefficient_summary

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/tables/gini_coefficient_summary.tex
- **Why it matters:** Required for manuscript sections: results, welfare
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open

### LIM-027 — Missing manuscript table: member_welfare_change

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/tables/member_welfare_change.tex
- **Why it matters:** Required for manuscript sections: results, welfare
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open

### LIM-028 — Missing manuscript table: cvar_downside_risk

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/tables/cvar_downside_risk.tex
- **Why it matters:** Required for manuscript sections: results, risk
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open

### LIM-029 — Missing manuscript figure: crop_area_trends

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/figures/publication/crop_area_trends.pdf
- **Why it matters:** Required for manuscript sections: data, crop_universe
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open

### LIM-030 — Missing manuscript figure: correlation_matrix_profits

- **Severity:** High
- **Area:** results
- **Observed issue:** Expected source not found: outputs/figures/publication/correlation_matrix_profits.pdf
- **Why it matters:** Required for manuscript sections: methods, optimization
- **Immediate mitigation:** Run the relevant pipeline step or add a LaTeX TODO placeholder.
- **Owner action required:** no
- **Status:** open
