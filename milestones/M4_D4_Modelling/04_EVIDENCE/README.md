# D4 — Experiment Evidence and Reproducibility

This folder records the D4 assignment experiment for the adopted **next-quarter EBITDA Margin** target.

## Received assignment artifacts
- Five-page expanded report: `ANCP_T##_D4_Expanded_Model_Training_Report(1).pdf` — received 23-Nov-2026; binary upload pending.
- Updated notebook: `ML_Model_Training(5).ipynb` — received 23-Nov-2026; binary upload pending.
- [Experiment log CSV](experiment_log_d4-v1.csv).
- [Run instructions](RUN_D4_v1.md).
- [Requirements](requirements-d4-v1.txt).

## Declared setup and results
- 38 raw quarterly observations; 34 usable supervised rows; ten features.
- Chronological split: 20 train / 7 validation / 7 test.
- Nine candidates: Seasonal Naive, Historical Mean, Ridge, Lasso, Elastic Net, Random Forest, Gradient Boosting, XGBoost and ETS.
- Validation winner: Seasonal Naive, MAE 7.470.
- Saved holdout metrics: MAE 3.948, RMSE 4.714, MASE 0.237.
- D4's earlier report draft displayed a 29.93 point forecast. The later D5 memorandum corrects the 2026 Q3 Seasonal Naive value to 26.11 under the documented shift(3) alignment. Keep the original D4 submission intact and cite D5 for the corrected forecast.

## Reproducibility limitations
The exact input workbook hash/version, original model execution timestamp and package lockfile were not captured. The notebook expects `EDA ANALYSIS.xlsx` / `Sheet1` and the monthly oil benchmark quarterly-mean field. The original notebook has saved outputs, but a clean rerun remains pending the exact workbook and complete environment record.

## Keep experiment tracks separate
Existing `experiments/D4_*.csv/json` records from the earlier structured PAT-margin experiment are legacy evidence. The submitted D4 assignment report/notebook is EBITDA-margin modelling. Do not combine their metrics, target definitions or dataset versions.
