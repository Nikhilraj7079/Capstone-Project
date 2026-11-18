# M4 / D4 — Modelling: Milestone Control

**Status:** IN PROGRESS — D4-v1 EBITDA assignment report/notebook received; reproducibility verification remains open.

## Purpose
Build and compare forecasting baselines and candidate models for IndiGo's next-quarter EBITDA Margin using a fixed chronological validation design, a final holdout and a recorded experiment history.

## Adopted target
EBITDA Margin (%) = EBITDA / Revenue from Operations × 100. The D4-v1 assignment uses `Target_Next_Q_EBITDA`, created by shifting EBITDA Margin forward by one quarter.

## D4-v1 assignment artifacts
- Five-page report: `03_DELIVERABLES/ANCP_T##_D4_Expanded_Model_Training_Report.pdf`.
- Submitted training notebook: `02_WORKING/ML_Model_Training(1).ipynb`.
- Experiment log: `04_EVIDENCE/experiment_log_d4-v1.csv`.
- Setup and run guide: `04_EVIDENCE/RUN_D4_v1.md`; requirements: `04_EVIDENCE/requirements-d4-v1.txt`.

## Declared validation design
The assignment notebook uses 38 raw quarters and 34 usable supervised observations. It preserves chronology and assigns 20 training rows, 7 validation rows and 7 test rows (60% / 20% / 20%). Model selection uses validation MAE; the test block is held back for final reporting. Standard scaling for Ridge/Lasso/Elastic Net is fitted inside pipelines using training data only.

## Candidate model families and rationale
- Seasonal Naive and Historical Mean: transparent reference baselines.
- Ridge, Lasso and Elastic Net: regularised linear regressions suitable for small samples and correlated predictors.
- Random Forest and Gradient Boosting: shallow tree ensembles to test limited non-linear relationships.
- XGBoost: optional shallow gradient-boosted trees.
- ETS: univariate trend-based statistical benchmark.

## Recorded assignment outcome
Seasonal Naive has the lowest validation MAE (7.470) and is selected. Its saved holdout metrics are MAE 3.948, RMSE 4.714 and MASE 0.237. Additional all-model test scores in the report are reconstructed from the comparison chart code, not a verbatim saved table. See the experiment log for metric provenance.

## Reproducibility risks
1. The expected source workbook `EDA ANALYSIS.xlsx` / `Sheet1` and its SHA-256 are not captured in the submitted notebook.
2. The original notebook has no imports/setup cell and no execution counts; saved outputs exist but clean execution is not yet demonstrated.
3. The original run timestamp and exact package versions are not embedded.
4. The current-quarter feature availability assumption must be checked against actual publication cut-offs.
5. The report's printed point forecast (29.93) must be rechecked against the source workbook and seasonal alignment before use.

## Separation from legacy structured run
The prior structured M4 experiment in `experiments/D4_*.csv/json` used PAT Margin and is legacy evidence. It is not to be merged with this D4-v1 EBITDA assignment experiment. Both remain separately versioned until the current active pipeline is finalised.

## Exit gate
Pin the exact assignment input workbook and hash; add/verify imports and environment; clean-run the notebook; preserve run date, package versions, seed and data fingerprint; then reconcile its target and split against the broader M4 modelling handoff. M4 is not closed by the report alone.
