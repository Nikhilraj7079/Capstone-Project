# D4 — Experiment Evidence and Reproducibility

This folder records the D4-v1 assignment experiment and its reproducibility status for the adopted **next-quarter EBITDA Margin** target.

## Assignment artifacts
- Five-page report: [ANCP_T##_D4_Expanded_Model_Training_Report.pdf](../03_DELIVERABLES/README.md).
- Notebook: `ML_Model_Training(1).ipynb` in `02_WORKING`.
- [Experiment log CSV](experiment_log_d4-v1.csv) — candidate validation results, available test metrics, features, parameters, seeds and metric provenance.
- [Run instructions](RUN_D4_v1.md).
- [Requirements](requirements-d4-v1.txt).

## Declared setup and results
- 38 raw quarterly observations; 34 usable supervised rows; 10 features.
- Chronological split: 20 train / 7 validation / 7 test (60% / 20% / 20%).
- Nine candidate approaches: Seasonal Naive, Historical Mean, Ridge, Lasso, Elastic Net, Random Forest, Gradient Boosting, XGBoost and ETS.
- Validation winner: Seasonal Naive, MAE 7.470.
- Saved holdout metrics: Seasonal Naive MAE 3.948, RMSE 4.714, MASE 0.237; Historical Mean MAE 12.948, RMSE 14.347, MASE 0.777.
- Test scores for the other candidate models are reconstructed from the chart-generation code in the report; their metric source is explicitly flagged in the CSV.

## Recording limitations
The notebook/report do not capture the original model execution timestamp, the exact input workbook hash/version or a package lockfile. The CSV preserves these as not recorded; 8 November 2026 is the date attached to the earlier evidence-preparation record, not a verified model-run timestamp. The PDF metadata creation date is 10 November 2026 and is also not treated as the experiment run date.

The notebook expects `EDA ANALYSIS.xlsx` / `Sheet1` and the monthly oil benchmark quarterly-mean column. That exact workbook is not supplied with this upload. The original notebook also lacks an imports/setup cell and execution counts. Saved outputs are reviewable; a clean run remains pending the exact workbook and a complete environment record.

## Keep the two M4 experiment tracks separate
The `experiments/D4_*.csv/json` records are from the earlier structured PAT-margin experiment. The assignment log in this folder is EBITDA-margin modelling. Do not combine their metrics, data versions or target definitions.
