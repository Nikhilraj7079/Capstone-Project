# D4 — Experiment Evidence and Reproducibility

This folder records the modelling evidence and reproducibility instructions for the M4 / D4 checkpoint. The active project target is **next-quarter EBITDA Margin**.

## Assignment notebook and report
- ML Model Training notebook — user-supplied notebook identified for this checkpoint; its binary commit to this repository is still pending.
- Expanded D4 report (DOCX) — prepared for this checkpoint; its binary commit to this repository is still pending. The report covers the dataset, feature engineering, model families, validation and holdout results, actual-versus-predicted test values, interpretation and limitations.

## Experiment and environment evidence
- [Experiment log CSV](experiment_log_d4-v1.csv) — candidate-level validation metrics, test metrics where saved, model parameters, feature set, seed and data-version caveats.
- [Requirements](requirements-d4-v1.txt) — Python package dependencies; XGBoost is optional.
- [Run instructions](RUN_D4_v1.md) — setup and execution steps.
- [Repository experiment outputs](../experiments/) — candidate comparison, data manifest, environment, experiment log, metrics and test predictions from the structured M4 pipeline.

## Recorded assignment outcome
- Target: next-quarter EBITDA Margin.
- Assignment notebook split: chronological 60% / 20% / 20% (20 train, 7 validation, 7 test rows, from 34 usable supervised rows).
- Validation winner: Seasonal Naive (MAE 7.470).
- Saved holdout metrics: Seasonal Naive MAE 3.948, RMSE 4.714, MASE 0.237; Historical Mean MAE 12.948, RMSE 14.347, MASE 0.777.
- The expanded report labels the individual candidate-model test predictions as reconstructed from the notebook's charting/model code where the notebook did not save a standalone numerical test-prediction table for every candidate.

## Data and execution caveats
The notebook expects an input workbook named `EDA ANALYSIS.xlsx` and a monthly oil benchmark quarterly-mean column. Keep that workbook version aligned with the notebook. The report explains the difference between the source workbook versions available during preparation. The original notebook does not preserve the exact source workbook hash/version, original run timestamp or a package lockfile. The experiment CSV records these omissions; its report-preparation date is not the original model execution timestamp.

This assignment notebook/report is a separately documented D4 exercise. Do not silently merge its metrics with the structured pipeline outputs under `milestones/M4_D4_Modelling/experiments/`; compare them only after confirming target construction, data version, feature timing and split windows are identical.
