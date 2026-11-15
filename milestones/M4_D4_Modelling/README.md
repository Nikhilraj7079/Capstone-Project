# M4 / D4 — Modelling and Forecasting

**Status:** IN PROGRESS — current active milestone.

## Brief
Develop and document reproducible forecasting baselines and candidate models for IndiGo's next-quarter **EBITDA Margin**. This milestone includes target construction, feature engineering, chronological validation, model comparison, experiment tracking and a modelling report. M4 remains in progress; the expanded assignment report and notebook are evidence additions, not a declaration that all M4 exit criteria are complete.

## Current D4 assignment artifacts
- [Expanded D4 Model Training Report (DOCX)](03_DELIVERABLES/ANCP_T%23%23_D4_Expanded_Model_Training_Report.docx) — detailed explanation of the data, ten engineered features, nine model approaches, validation/test metrics, actual-versus-predicted values for the seven-row test period, interpretation and limitations.
- [ML Model Training notebook](02_WORKING/ML_Model_Training.ipynb) — user-supplied notebook used as the modelling source. It forecasts next-quarter EBITDA Margin.
- [D4 evidence and reproducibility](04_EVIDENCE/README.md) — experiment log, requirements and run guidance.
- [D4 modelling outputs](experiments/) — repository-tracked candidate results, metrics, test predictions, experiment log, data manifest and environment record from the active M4 pipeline.
- [D4 source code](src/d4_train.py) and [tests](tests/test_d4_train.py).

## Data used
- [M4 quarterly snapshot](data/Final_Quarterly_Data%281%29.xlsx) — preserved modelling input snapshot and audit tabs.
- [M3 EBITDA-only analysis panel](../M3_D3_Exploratory_Data_Analysis/data/EDA_ANALYSIS_EBITDA_ONLY_38Q.csv) — 38-quarter exploratory handoff.
- [M2 source data index](../M2_D2_Data_Audit/data/README.md) — raw data lineage and dictionary.

The user-supplied assignment notebook expects an input workbook named `EDA ANALYSIS.xlsx` and the monthly oil benchmark quarterly-mean field. Its report explains the workbook/version caveat. Keep the exact workbook version aligned with the notebook when reproducing those results. Do not assume this assignment workbook is interchangeable with the canonical M4 quarterly snapshot above.

## Workflow
1. Lock the M2/M3 dataset versions and checksums.
2. Verify EBITDA definition and revenue denominator; reconcile unavailable/estimated periods.
3. Build a chronological one-quarter-ahead supervised dataset without bridging missing periods.
4. Create persistence and seasonal-naive baselines.
5. Build candidate models with preprocessing fitted on training data only.
6. Tune on chronological validation; preserve a final untouched test segment.
7. Compare MAE/RMSE, inspect residuals and report limits.
8. Save model artefacts, run logs, predictions, tests, environment and report.
9. Hand the selected model/baseline and exact data version to M5.

## Folder map
- `01_INPUTS/` — approved datasets and input documentation.
- `02_WORKING/` — working notebooks, scripts and tests.
- `03_DELIVERABLES/` — reports and submission-ready documents.
- `04_EVIDENCE/` — experiment logs, environment and run instructions.
- `05_REFERENCES/` — methodology/source references.
- `data/` — milestone modelling dataset snapshots.
- `experiments/` — machine-readable candidate results, metrics, predictions and manifests.
- `src/`, `tests/`, `notebooks/` — reproducible code, checks and notebooks.

## Important historical record
Older D4-v1 files and the top-level [README_D4.md](../../README_D4.md) describe a separate legacy PAT-margin experiment. That legacy work must not be mixed with the current project's adopted EBITDA Margin target. The current project target is EBITDA Margin only. Where historical PAT-margin material is retained for audit/history, it is labelled as legacy and is not evidence for the current EBITDA model.

## Exit criteria
M4 is complete only after the active EBITDA modelling pipeline has a pinned and reconciled input dataset, leakage-safe chronological validation, baseline comparison, candidate results, tests, reproducibility artifacts and a documented selection decision handed to M5. The expanded assignment report and notebook are additional M4 documentation; they do not by themselves close the milestone.
