# M5 — Inputs and Data Contract

## Required upstream inputs
1. D4 next-quarter EBITDA-margin target definition and feature schema.
2. D4 training notebook, Python script and model settings.
3. Exact quarterly input workbook used for D4/D5 evaluation.
4. M2 source register and point-in-time availability rules.
5. M3 EDA handoff and known data-quality caveats.

## D5 data vintage record
The D5 memorandum records 38 raw quarterly observations from 2017 Q1 to 2026 Q2 and 34 usable supervised rows. Ten engineered features are used. The chronological split is 20 train / 7 validation / 7 test, with a locked test period of 2024 Q3–2026 Q1.

### Feature contract
- EBITDA Margin (current quarter)
- EBITDA lag 1
- EBITDA two-quarter rolling mean
- USD/INR quarterly mean and one-quarter lag
- Monthly oil benchmark quarterly mean and one-quarter lag
- Oil benchmark two-quarter rolling mean
- CPI quarterly mean
- WPI quarterly mean

### Received D5 files
| File | SHA-256 | Role |
|---|---|---|
| `ANCP_Team-K_D5_v1.pdf` | `9055c5e0e35a3dd7e7ea88e36e03929f8d00a131af0d7808ad36fa787cd74c82` | Evaluation decision memorandum |
| `ML_Model_Training(6).ipynb` | `3e8a2b8a255450cddee32fe5d3bd26e1ac14dd6e4ed7b33f81e3406de7948310` | Training/evaluation notebook |
| `ml_model_training(2).py` | `31abe74c8db7d247780a35b83b95bf1bb546120e3b8a4b31b86766670b9bea4f` | Python source script |

**Repository note:** These files have been received in the project conversation. Their binary upload to GitHub must be verified by exact repository paths before they are described as committed.

## Source workbook dependency and reproducibility
The notebook/script expect `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, with these exact required columns:
- `EBITDA Margin`
- `USD INR (Quarterly Mean)`
- `Oil benchmark(MONTHLY) (Quarterly Mean)`
- `CPI inflation (Quarterly Mean)`
- `WPI inflation (Quarterly Mean)`

The code sorts by `Year` and `Quarter (Calendar)` when both are available. The exact source workbook is not among the three newly received files, and its SHA-256/source version is not pinned in the D5 memo. Do not claim full clean-run reproducibility until the exact workbook is obtained, reconciled and hashed.

## Evaluation contract
- Target: next-quarter EBITDA Margin (%), created by shifting EBITDA Margin forward one quarter.
- Forecast horizon: one quarter.
- Preserve chronology; do not shuffle.
- Seasonal Naive alignment: `shift(3)`, corresponding to the same seasonal quarter one year earlier for a one-quarter-ahead target.
- Model selection uses validation MAE only.
- Holdout test is not used for model selection.
- StandardScaler is inside a Pipeline fitted on training data only.
- MASE scale is calculated using training targets only.
- Inputs must be available at forecast origin. If current-quarter values are not final, shift or forecast them separately.
- Dated Brent/oil benchmark is a proxy, not IndiGo's actual ATF cost.

## Ownership
M2 owns original source lineage; M3 owns the EDA panel and exploratory outputs; M4 owns modelling data/features and training workflow; M5 owns evaluation predictions, errors, metrics and evaluation evidence. M6 consumes the approved D5 model and feature contract without silently substituting another data vintage.
