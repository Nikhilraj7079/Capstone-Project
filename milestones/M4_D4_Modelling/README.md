# M4 / D4 — Model Training and Forecasting

**Status: COMPLETED.** The D4 expanded training report and updated model-training notebook have been submitted and documented. Source-workbook/version and clean-run reproducibility caveats remain recorded as handoff controls for M6 / D6.

## Scope
Train and compare forecasting baselines and candidate models for IndiGo's next-quarter **EBITDA Margin**. PAT-margin experiment records in the legacy structured pipeline are separate and must not be reported as current EBITDA results.

## D4 assignment artifacts received
- **Expanded report:** `ANCP_T##_D4_Expanded_Model_Training_Report.pdf` — received 23-Nov-2026; binary repository upload is pending.
- **Updated notebook:** `ML_Model_Training(5).ipynb` — received 23-Nov-2026; binary repository upload is pending.
- Earlier report version: `ANCP_T##_D4_Expanded_Model_Training_Report(1).pdf` was received in the same update and is treated as the supplied report copy, not as a separate experiment.
- Existing experiment log and run instructions remain under [04_EVIDENCE](04_EVIDENCE/README.md).

## Methodology and results recorded in the D4 report
- 38 raw quarterly observations (2017 Q1–2026 Q2); 34 usable supervised rows.
- Ten features: current EBITDA Margin, EBITDA lag 1, two-quarter EBITDA rolling mean, current/lagged USD-INR, current/lagged monthly oil benchmark quarterly mean, two-quarter oil rolling mean, CPI and WPI.
- Chronological split: 20 train / 7 validation / 7 test; no random shuffle.
- Nine candidate approaches: Seasonal Naive, Historical Mean, Ridge, Lasso, Elastic Net, Random Forest, Gradient Boosting, XGBoost and ETS.
- Seasonal Naive selected on validation MAE 7.470; saved test MAE/RMSE/MASE 3.948 / 4.714 / 0.237.

## Reproducibility and scope controls
- Notebook expects `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, and the monthly oil benchmark quarterly-mean field.
- Exact source workbook hash/version and original execution environment are not recorded in the report.
- The submitted notebook contains saved outputs but clean execution must be verified from the exact source workbook and a documented environment.
- Current-quarter EBITDA and macro means must be final and available at the forecast cutoff; otherwise lag or forecast inputs separately.
- The D5 evaluation memorandum supersedes the earlier D4 draft forecast of 29.93% with a corrected 2026 Q3 Seasonal Naive forecast of 26.11% under the `shift(3)` alignment. Keep this correction traceable; do not silently rewrite the historical D4 submission.

## Folder map
- `01_INPUTS/` — input data contracts and source lineage.
- `02_WORKING/` — submitted notebook and working code.
- `03_DELIVERABLES/` — formal D4 report index.
- `04_EVIDENCE/` — experiment log, environment and run instructions.
- `experiments/`, `src/`, `tests/` — structured M4 pipeline; keep legacy PAT experiment records separate.

## Exit criteria
D4 is recorded as completed for the capstone submission. The exact input workbook/hash, clean-run environment, quarterly-value reconciliation and feature-timing controls remain visible follow-up items for the D6 deployment handoff.
