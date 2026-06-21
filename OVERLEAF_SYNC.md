# Overleaf synchronization for CoPPer

Do **not** sync the full CoPPer computational repository to Overleaf. Use a lightweight
manuscript-only package.

## Preferred workflow: separate manuscript repository

Target layout (example repository name: `copper-paper`):

```text
copper-paper/
├── manuscript/
├── bibliography/
├── figures/
├── tables/
├── supplementary/
├── latexmkrc
├── README.md
├── MANUSCRIPT_LIMITATIONS.md
├── OVERLEAF_SYNC.md
└── results_manifest.yaml
```

### Steps

1. Generate results in the main CoPPer repository (`make reproduce` or relevant targets).
2. Export manuscript assets: `make paper-assets`
3. Build submission package: `make paper-package`
4. Copy or push `paper/submission_package/` contents to a dedicated GitHub repository (`copper-paper`).
5. Create a **new** Overleaf project from that GitHub repository, **or** create a new GitHub
   repository from Overleaf (one side must be created from the other).
6. Use Overleaf GitHub Sync manually to pull/push text edits.
7. Pull Overleaf edits back into `copper-paper`, then merge reviewed prose changes into the
   main CoPPer repository under `paper/manuscript/sections/`.
8. Regenerate figures/tables from code in CoPPer; never treat Overleaf as the source of truth
   for numerical results.

## Alternative: Overleaf Git remote

If you have Overleaf Git integration and credentials locally, you may add Overleaf as a Git
remote for the manuscript-only repository. CoPPer does not configure remotes automatically.

Example (replace with your Overleaf Git URL):

```bash
git remote add overleaf https://git.overleaf.com/<project-id>
git push overleaf main
```

## Important constraints

- **Overleaf GitHub Sync is a premium Overleaf Cloud feature.**
- Overleaf **cannot** link an existing Overleaf project to an existing GitHub repository
  directly; one must be created from the other.
- Sync is **not** a substitute for reproducible result generation in CoPPer.
- Generated tables and figures must flow from pipeline outputs → `make paper-assets` → manuscript.
- Exclude from Overleaf: `data/raw/`, `data/interim/`, `data/processed/`, `experiments/runs/`,
  Python environments, caches, and large logs.

## Journal target switching

Edit `configs/manuscript.yaml` (`target_journal`) in the main repository, then rerun
`make paper-assets` and `make paper-package`. Wrapper selection:

| `target_journal` | LaTeX wrapper |
|------------------|---------------|
| `journal_of_agricultural_economics` | `main_wiley.tex` |
| `agricultural_economics` | `main_wiley.tex` |
| `american_journal_of_agricultural_economics` | `main_wiley.tex` |
| `agricultural_systems` | `main_elsevier.tex` |
| `generic_preprint` | `main_preprint.tex` |

See also `paper/journal_templates/README.md` and `paper/OVERLEAF_ASSESSMENT.md`.
