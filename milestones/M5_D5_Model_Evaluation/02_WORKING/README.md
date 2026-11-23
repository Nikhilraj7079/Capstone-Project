# M5 — Working Files

## Submitted notebook reference
- **Received file:** `ML_Model_Training(5).ipynb` — received 23-Nov-2026; binary upload to this folder is pending.
- The notebook retains the D4 next-quarter EBITDA Margin target, engineered feature sequence, chronological 60/20/20 split, candidate model comparison and deployment-artifact save step.
- The D5 memorandum references this training workflow for the leakage checklist and test-period evidence.

## Evaluation work
The submitted D5 memorandum evaluates a locked chronological holdout of seven target quarters (2024 Q3–2026 Q1). It does not claim a rolling-origin backtest. Rolling-origin evaluation remains a recommended extension.

## Reproduction requirement
Pin the exact `EDA ANALYSIS.xlsx` source workbook, record SHA-256 and environment/package versions, then rerun the notebook from a clean clone. Record the output and compare the corrected Seasonal Naive 2026 Q3 forecast of 26.11% against the `shift(3)` rule.
