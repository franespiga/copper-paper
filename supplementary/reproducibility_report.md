# CoPPer Reproducibility Report

**Generated (UTC):** 2026-06-21T13:11:08.672773+00:00
**Git commit:** `d289d8ef96ec000329823d96ad4e234d3d25d31d`
**Python:** 3.13.5
**Platform:** macOS-15.3.1-arm64-arm-64bit-Mach-O

## Summary

- Configured experiments: 8
- Experiments with all outputs present: 8
- Recorded pipeline runs: 4
- Provenance records: 18

## Package versions

| Package | Version |
|---------|---------|
| copper | 0.1.0 |
| cvxpy | 1.9.1 |
| matplotlib | 3.10.0 |
| numpy | 2.1.3 |
| pandas | 2.2.3 |
| pydantic | 2.10.3 |
| pytest | 8.3.4 |
| pyyaml | 6.0.2 |
| scikit-learn | 1.6.1 |
| scipy | 1.15.3 |

## Experiment output audit

| Experiment | Output | Exists | SHA-256 (first 12) |
|------------|--------|--------|--------------------|
| crop_universe_pareto | `outputs/tables/crop_universe_pareto.csv` | yes | 3da22323d848 |
| crop_universe_pareto | `outputs/figures/publication/crop_universe_pareto.pdf` | yes | a1dcf7fef9c8 |
| crop_universe_pareto | `outputs/reports/crop_universe_selection.md` | yes | 0a82c648df09 |
| profit_panel_m2 | `data/processed/profit_county_crop_season.parquet` | yes | c76ac9a34d49 |
| profit_panel_m2 | `outputs/tables/profit_summary_by_crop.csv` | yes | 7bc013879748 |
| profit_panel_m2 | `outputs/reports/profit_dataset.md` | yes | ca95fc2715d4 |
| historical_backtest_m3 | `outputs/tables/backtest_summary.csv` | yes | 8fe91daeb986 |
| historical_backtest_m3 | `outputs/reports/historical_backtest.md` | yes | afdd88c03016 |
| historical_backtest_m3 | `experiments/runs/historical_backtest/season_profits.parquet` | yes | f21d8efafd1c |
| bootstrap_m3 | `outputs/tables/bootstrap_simulation_summary.csv` | yes | 5f11b92d4d9e |
| bootstrap_m3 | `outputs/reports/bootstrap_scenarios.md` | yes | c44dabd134ee |
| optimization_m4 | `outputs/tables/efficient_frontier.csv` | yes | cae8e8eb325d |
| optimization_m4 | `outputs/tables/hypothesis_test_summary.csv` | yes | 09d85a235ef1 |
| optimization_m4 | `outputs/tables/welfare_sharing_comparison.csv` | yes | cb79ccd24225 |
| optimization_m4 | `outputs/reports/optimization_inference.md` | yes | 289b98ec2c64 |
| robustness_m5 | `outputs/tables/price_forecast_metrics.csv` | yes | 63ddce0c9e37 |
| robustness_m5 | `outputs/tables/robustness_summary.csv` | yes | cc899ec3341c |
| robustness_m5 | `outputs/reports/robustness_forecasting.md` | yes | 226e40fe6d19 |
| robustness_m5 | `outputs/figures/publication/robustness_heatmap.pdf` | yes | 1e3c1bb0735c |
| publication_m5 | `paper/figures/backtest_comparison.pdf` | yes | ea1413303c26 |
| publication_m5 | `paper/tables/backtest_summary.csv` | yes | 8fe91daeb986 |
| reproducibility_m6 | `outputs/reports/reproducibility_report.md` | yes | 18e9c4671652 |
| reproducibility_m6 | `outputs/reports/experiment_output_audit.csv` | yes | 05639762026a |
| reproducibility_m6 | `experiments/experiment_registry.yaml` | yes | 2c2602790094 |

## Pipeline run metadata

### bootstrap_scenarios
- Timestamp: 2026-06-21T11:33:18.646466+00:00
- Git commit: `d289d8ef96ec000329823d96ad4e234d3d25d31d`
- Metadata file: `/Users/franes/git/research/CoPPer/experiments/runs/bootstrap/run_metadata.json`

### historical_backtest
- Timestamp: 2026-06-21T11:33:17.991610+00:00
- Git commit: `d289d8ef96ec000329823d96ad4e234d3d25d31d`
- Metadata file: `/Users/franes/git/research/CoPPer/experiments/runs/historical_backtest/run_metadata.json`

### optimization_m4
- Timestamp: 2026-06-21T11:48:05.475406+00:00
- Git commit: `d289d8ef96ec000329823d96ad4e234d3d25d31d`
- Metadata file: `/Users/franes/git/research/CoPPer/experiments/runs/optimization/run_metadata.json`

### robustness_m5
- Timestamp: 2026-06-21T12:29:07.757659+00:00
- Git commit: `d289d8ef96ec000329823d96ad4e234d3d25d31d`
- Metadata file: `/Users/franes/git/research/CoPPer/experiments/runs/robustness/run_metadata.json`

## Threats to validity (charter §22)

This pipeline partially addresses:

- **Yield / price / cost measurement error** — documented reference data and provenance logs
- **Correlation estimation error** — multiple covariance estimators and bootstrap methods
- **Model overfitting** — forecasting is auxiliary and benchmarked against naive baselines

Remaining limitations:

- UK-specific external validity
- Cooperative adoption and agronomic feasibility not modelled structurally
- Welfare metrics rely on profit proxies, not full household accounts
- National cooperative benchmark is an upper bound, not policy advice

## Reproduction instructions

```bash
make setup
make reproduce
make test
make docs
```

Or run `python scripts/reproduce_all.py` followed by `python scripts/generate_reproducibility_report.py`.
