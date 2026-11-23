# M5 — Working Files

## Shared D4 training notebook
The submitted `ML_Model_Training(5).ipynb` is the current training/evaluation workflow and is owned by M4 / D4. Its canonical intended location is [M4 / 02_WORKING](../../M4_D4_Modelling/02_WORKING/README.md). The binary notebook upload to GitHub is pending; do not create duplicate copies in M4 and M5.

## D5 evaluation work
The submitted D5 memorandum evaluates a locked chronological holdout of seven target quarters (2024 Q3–2026 Q1). It does not claim a rolling-origin backtest. Rolling-origin evaluation remains a recommended extension.

## Reproduction requirement
Pin the exact `EDA ANALYSIS.xlsx` source workbook, record SHA-256 and environment/package versions, then rerun the notebook from a clean clone. Record the output and compare the corrected Seasonal Naive 2026 Q3 forecast of 26.11% against the `shift(3)` rule.
