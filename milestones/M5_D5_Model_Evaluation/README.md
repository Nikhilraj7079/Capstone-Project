# M5 / D5 — Model Evaluation & Validation

**Status: COMPLETED WITH DOCUMENTED LIMITATIONS.** The D5 executive decision memorandum, updated model-training notebook and Python training script have been received and are indexed below. Their binary presence on GitHub must be verified separately; documentation does not imply binary upload.

## 1. Submitted D5 files and data record

| Artifact | Received filename | Purpose | SHA-256 | GitHub binary status |
|---|---|---|---|---|
| Evaluation memorandum | `ANCP_Team-K_D5_v1.pdf` (4 pages) | D5 decision, validation, leakage audit, error-cost and robustness assessment | `9055c5e0e35a3dd7e7ea88e36e03929f8d00a131af0d7808ad36fa787cd74c82` | Pending upload/verification |
| Updated training notebook | `ML_Model_Training(6).ipynb` | Reproducible model-training/evaluation workflow and saved outputs | `3e8a2b8a255450cddee32fe5d3bd26e1ac14dd6e4ed7b33f81e3406de7948310` | Pending upload/verification |
| Python training script | `ml_model_training(2).py` | Python source version of the training/evaluation workflow | `31abe74c8db7d247780a35b83b95bf1bb546120e3b8a4b31b86766670b9bea4f` | Pending upload/verification |

**Data vintage described by D5:** 38 raw quarterly observations from 2017 Q1 through 2026 Q2; 34 usable supervised rows after target/lag/rolling-feature construction; 10 engineered features. The split is chronological and unshuffled: 20 train / 7 validation / 7 test. The locked test targets cover 2024 Q3–2026 Q1.

**Feature set:** current EBITDA Margin; EBITDA lag 1; two-quarter EBITDA rolling mean; current and lagged USD/INR; current and lagged monthly oil-benchmark quarterly mean; two-quarter oil rolling mean; CPI quarterly mean; WPI quarterly mean.

**Source input dependency:** the notebook and script expect `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, including the monthly oil benchmark quarterly-mean field. The exact source workbook is not included with these three uploads and its SHA-256/source version is not pinned in the D5 memorandum. A clean rerun therefore remains conditional on obtaining and reconciling that exact workbook.

## 2. Executive decision

Adopt **Seasonal Naive** (same quarter one year earlier) as the primary one-quarter-ahead EBITDA-margin benchmark. Use ETS and Gradient Boosting as secondary cross-checks.

## 3. Evaluation design and leakage controls

- Target: next-quarter EBITDA Margin; target shifted forward one quarter.
- Raw history: 38 quarterly observations, 2017 Q1–2026 Q2.
- Usable supervised observations: 34.
- Split: 20 train / 7 validation / 7 test, chronological and unshuffled.
- Locked holdout: 2024 Q3–2026 Q1 (7 target quarters).
- Feature/target alignment: predictors use current and past observations; Seasonal Naive uses `shift(3)` for the same quarter in the previous year when predicting one quarter ahead.
- StandardScaler is inside a scikit-learn Pipeline and fitted on training data only.
- MASE denominator is calculated from training targets only (approximately 16.67 pp).
- Model selection uses validation MAE only; the holdout is evaluated after selection.
- Forecast-origin condition: current-quarter EBITDA and macro means must be final and available at forecast time; otherwise inputs must be shifted to t-1 or forecast separately.

The memo marks the chronological split, causal alignment, scaler isolation, training-only MASE scale and test-set selection discipline as PASS. Foundation-model/LLM memorisation is N/A. Forecast-origin availability is PASS only conditionally on the reporting calendar.

## 4. Reported results

All MAE/RMSE values are EBITDA-margin percentage points (pp).

| Model | Validation MAE | Test MAE | Test RMSE | Test MASE |
|---|---:|---:|---:|---:|
| Seasonal Naive (selected) | 7.47 | 3.95 | 4.71 | 0.24 |
| Historical Mean | 13.79 | 12.95 | 14.35 | 0.78 |
| ETS (additive trend) | 19.37 | 6.61 | 6.97 | 0.40 |
| Gradient Boosting | 15.97 | 7.25 | 7.87 | 0.44 |
| XGBoost | 16.29 | 7.87 | 8.63 | 0.47 |
| Random Forest | 20.11 | 7.87 | 8.73 | 0.47 |
| Elastic Net | 38.33 | 20.58 | 22.39 | 1.23 |
| Ridge | 39.40 | 23.30 | 25.24 | 1.40 |
| Lasso | 48.86 | 25.88 | 27.92 | 1.55 |

**Metric provenance:** the D5 memo states that Seasonal Naive and Historical Mean test results reproduce the saved notebook test-results table. The other candidate test metrics are reconstructed from the notebook's chart-generation code (Cell 10 reconstruction), not all verbatim from the saved test-results table. Preserve this distinction when quoting the results.

For Seasonal Naive, the memo reports a 95% t-based interval for the mean absolute error of 1.38–6.52 pp, based on seven test errors. It also reports that the confidence interval overlaps those of ETS and Gradient Boosting, so the apparent margin over those models is not statistically conclusive.

## 5. Forecast correction and risk communication

- **D5 corrected 2026 Q3 point forecast:** 26.11% EBITDA Margin, repeating the 2025 Q3 actual under the documented `shift(3)` alignment.
- **Earlier D4 draft:** 29.93%, identified in D5 as a prior-draft alignment error corresponding to 2025 Q1.
- **D5 empirical risk band:** ±9.24 percentage points, approximately 16.9%–35.4%. This is an empirical risk buffer, not a model-native prediction interval or guarantee.

Use 26.11% when communicating the D5 memo's corrected 2026 Q3 forecast. Preserve the earlier D4 report as historical submission evidence.

## 6. Business interpretation and error analysis

The memo estimates quarterly revenue of about ₹18,000–20,000 crore, implying roughly ₹180–200 crore per EBITDA-margin percentage point. It frames the selected model's 3.95 pp MAE as roughly ₹710–790 crore of average quarterly cash-flow variance, and a 7.9 pp miss as about ₹1,400–1,580 crore.

Errors are asymmetric:
- Overprediction example: 2024 Q4 predicted 18.83% vs actual 10.95% (+7.88 pp), with potential delayed fuel/FX hedging, over-commitment, liquidity strain and covenant stress.
- Underprediction example: 2025 Q4 predicted 10.95% vs actual 18.59% (-7.64 pp), with potential over-hedging, idle cash and premature discounting.

The memo notes Seasonal Naive is weaker around Q4 inflections: MAE 2.42 pp on five stable high-margin quarters versus 7.76 pp on two Q4 quarters. It also identifies a 2020 Q4 outlier (-201% margin) in the 27-row refit window as a major issue for linear-model intercepts and extrapolation.

## 7. Limitations and follow-up

- Seven test quarters are too few for strong generalisation claims; rankings are provisional.
- Seasonal Naive is insensitive to crude, USD/INR and inflation shocks and cannot answer macro what-if questions.
- Oil is a global crude benchmark proxy, not IndiGo's actual ATF landed cost.
- The empirical band is a risk buffer, not a model-native interval.
- Forecast timing depends on current-quarter financial and macro inputs being final and available.
- The MASE denominator may be influenced by COVID-era swings; interpret MAE and RMSE in percentage points alongside MASE.
- The notebook/script use a static Excel extract; automated ingestion, schema validation and rolling-origin retraining are needed before production.
- Exact source workbook hash/version and original execution environment remain unpinned.
- Rolling-origin backtesting is recommended before production use.

## 8. Folder map

- [01_INPUTS](01_INPUTS/README.md) — upstream data vintage, feature contract and source dependency.
- [02_WORKING](02_WORKING/README.md) — received notebook and Python script index.
- [03_DELIVERABLES](03_DELIVERABLES/README.md) — D5 executive decision memorandum.
- [04_EVIDENCE](04_EVIDENCE/README.md) — metrics, leakage audit, error analysis and forecast correction.
- [05_REFERENCES](05_REFERENCES/README.md) — methods and source references.

## 9. Exit status

D5 is **Completed with documented limitations** as the evaluation memorandum has been submitted and reviewed. This does not certify production readiness. The exact source-workbook pinning, clean-run reproduction and rolling-origin extension remain follow-up requirements before M6 production deployment.
