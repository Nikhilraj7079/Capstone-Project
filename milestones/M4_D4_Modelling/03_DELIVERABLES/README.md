# M4 — Deliverables

## D4 — Expanded Model Training Report

- **Received file:** `ANCP_T##_D4_Expanded_Model_Training_Report(1).pdf` — received 23-Nov-2026.
- **Report length:** 5 pages.
- **Repository binary status:** pending upload; this README records receipt and intended placement only.
- **Target:** next-quarter EBITDA Margin.

The report documents:
1. Business question, target and supervised one-quarter-ahead regression.
2. 38 raw quarterly observations, 34 usable supervised rows and ten engineered features.
3. Chronological 60/20/20 split (20 train, 7 validation, 7 test).
4. Nine model families and their rationale.
5. Validation ranking, holdout metrics, actual-versus-predicted test values and limitations.

Seasonal Naive wins validation with MAE 7.470. Its saved test MAE/RMSE/MASE are 3.948 / 4.714 / 0.237.

## Related evidence
- Latest submitted notebook: [02_WORKING](../02_WORKING/README.md).
- Experiment log, run instructions and requirements: [04_EVIDENCE](../04_EVIDENCE/README.md).
- Subsequent D5 evaluation memorandum: [M5 / D5](../../M5_D5_Model_Evaluation/README.md).

**Status remains IN PROGRESS.** Receipt of the report does not close D4's source-workbook, clean-run and data-lineage gates.
