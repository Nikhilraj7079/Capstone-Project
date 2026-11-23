# M5 / D5 — Model Evaluation & Validation

**Status: COMPLETED WITH DOCUMENTED LIMITATIONS.** The D5 executive decision memorandum has been received and its results, leakage audit, error-cost assessment and limitations are indexed below. Binary upload to GitHub is still pending verification.

## D5 submitted deliverable
- **Received filename:** `ANCP_T___D5_v1 (1).pdf`
- **Canonical repository filename intended:** `ANCP_T##_D5_v1.pdf`
- **Length:** 4 pages.
- **Memo date:** 15 November 2026.
- **Title:** Executive Decision Memorandum — D5 Model Evaluation & Validation, Next-Quarter EBITDA Margin Forecast.
- **Repository binary status:** received in this conversation; not yet committed to GitHub.

## Executive decision
Adopt **Seasonal Naive** (same quarter one year earlier) as the primary one-quarter-ahead EBITDA-margin benchmark. Use ETS and Gradient Boosting as secondary cross-checks.

## Evaluation design
- Target: next-quarter EBITDA Margin; target is shifted forward one quarter.
- Raw history: 38 quarterly observations, 2017 Q1–2026 Q2.
- Usable supervised observations: 34.
- Split: 20 train / 7 validation / 7 test, chronological and unshuffled.
- Locked holdout: 2024 Q3–2026 Q1 (7 target quarters).
- Leakage controls documented: chronological split, causal lag/target alignment, scaler fitted within training pipeline, training-only MASE scale and validation-only model selection.
- Forecast-origin control is conditional: current-quarter EBITDA and macro means must be final and available at forecast time.

## Reported results

| Model | Validation MAE (pp) | Test MAE (pp) | Test RMSE (pp) | Test MASE |
|---|---:|---:|---:|---:|
| Seasonal Naive (selected) | 7.47 | 3.95 | 4.71 | 0.24 |
| Historical Mean | 13.79 | 12.95 | 14.35 | 0.78 |
| ETS | 19.37 | 6.61 | 6.97 | 0.40 |
| Gradient Boosting | 15.97 | 7.25 | 7.87 | 0.44 |
| XGBoost | 16.29 | 7.87 | 8.63 | 0.47 |
| Random Forest | 20.11 | 7.87 | 8.73 | 0.47 |
| Elastic Net | 38.33 | 20.58 | 22.39 | 1.23 |
| Ridge | 39.40 | 23.30 | 25.24 | 1.40 |
| Lasso | 48.86 | 25.88 | 27.92 | 1.55 |

The first two test rows reproduce saved notebook metrics; other candidate test metrics are reconstructed from the notebook's chart-generation code and are labelled as reconstructed in the submitted report.

## Forecast correction and risk communication
The memo corrects the earlier D4 draft's 2026 Q3 point forecast:
- **D5 corrected point forecast:** 26.11% EBITDA Margin, repeating the 2025 Q3 value under the documented `shift(3)` Seasonal Naive alignment.
- **Earlier D4 draft value:** 29.93%; the D5 memo identifies this as a prior-draft alignment error (it corresponds to 2025 Q1).
- **D5 empirical band:** ±9.24 percentage points, or approximately 16.9%–35.4%. This is an empirical risk buffer, not a model-native prediction interval or guarantee.

Use 26.11% when communicating the D5 memo's corrected 2026 Q3 forecast. Preserve the earlier D4 report as historical submission evidence.

## Business interpretation
The memo estimates quarterly revenue of about ₹18,000–20,000 crore, implying roughly ₹180–200 crore for each EBITDA-margin percentage point. It discusses asymmetric forecast errors: overprediction can lead to delayed fuel/FX hedging, excess capacity commitments and liquidity stress; underprediction can lead to over-hedging or premature discounting.

## Limitations and follow-up
- Seven test quarters are too few for strong generalisation claims; rankings are provisional.
- Seasonal Naive is insensitive to crude, USD/INR and inflation shocks and cannot answer macro what-if questions.
- Oil is a global crude benchmark proxy, not IndiGo's actual ATF landed cost.
- Forecast timing is conditional on current-quarter financial and macro inputs being available.
- Exact source workbook hash and original execution environment are not captured in submitted evidence.
- Rolling-origin backtesting is recommended before production use.
- Interpret MAE/RMSE in margin percentage points alongside MASE.

## Folder map
- `01_INPUTS/` — D4 model/data vintage and evaluation protocol.
- `02_WORKING/` — submitted notebook reference and evaluation working notes.
- `03_DELIVERABLES/` — formal D5 memorandum index.
- `04_EVIDENCE/` — metrics, leakage audit, forecast correction and limitations.
- `05_REFERENCES/` — methodology and source references.

## Exit status
D5 is marked **Completed with documented limitations** as the evaluation memorandum has been submitted and reviewed. This does not certify production readiness. The recommended rolling-origin extension, exact source-workbook pinning and clean-run reproduction remain follow-up requirements before M6 production deployment.
