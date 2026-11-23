# M5 — Working Files

## Received training/evaluation code

| File received | Purpose | SHA-256 | GitHub binary status |
|---|---|---|---|
| `ML_Model_Training(6).ipynb` | Notebook for target/feature construction, chronological split, model comparison, holdout evaluation, deployment artefact and next-quarter forecast | `3e8a2b8a255450cddee32fe5d3bd26e1ac14dd6e4ed7b33f81e3406de7948310` | Pending upload/verification |
| `ml_model_training(2).py` | Python script version of the training workflow | `31abe74c8db7d247780a35b83b95bf1bb546120e3b8a4b31b86766670b9bea4f` | Pending upload/verification |

The notebook and script are training workflow artefacts shared with M4 / D4. M5 references them as the evaluation implementation evidence; avoid creating inconsistent duplicate copies across modules. If stored centrally under M4, link to that canonical location from this folder.

## D5 evaluation scope
The D5 memorandum evaluates a locked chronological holdout of seven target quarters (2024 Q3–2026 Q1). It does not claim a rolling-origin backtest. Rolling-origin evaluation remains a recommended extension.

## Reproduction requirements
1. Pin the exact `EDA ANALYSIS.xlsx` source workbook and record SHA-256.
2. Record Python and package versions.
3. Run from a clean clone with the workbook in the expected location.
4. Confirm the 38 raw observations, 34 supervised rows, 10 features and 20/7/7 split.
5. Verify the Seasonal Naive `shift(3)` alignment and corrected 2026 Q3 forecast of 26.11%.
6. Preserve the distinction between saved test metrics and candidate metrics reconstructed from chart-generation code.
