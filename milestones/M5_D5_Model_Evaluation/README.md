# M5 / D5 — Model Evaluation & Validation

**Status: COMPLETED WITH DOCUMENTED LIMITATIONS.** The D5 executive decision memorandum, updated model-training notebook and Python training script have been received and are indexed below. The latest uploaded notebook (`ML_Model_Training(7).ipynb`) has replaced the earlier notebook at the stable M5 path `02_WORKING/ML_Model_Training.ipynb`. The separate Python script remains available. **Current model designation:** the latest notebook designates SARIMAX as the final project model. Its validation MAE is the lowest among the compared models. The holdout table is reported transparently: Seasonal Naive has lower holdout errors than SARIMAX. The earlier D5 memorandum's Seasonal Naive selection and 26.11% forecast are retained as historical memorandum results and are not the current notebook's model decision/output.

## 1. Submitted D5 files and data record

| Artifact | Received filename | Purpose | SHA-256 | GitHub binary status |
|---|---|---|---|---|
| Evaluation memorandum | `ANCP_Team-K_D5_v1.pdf` (4 pages) | D5 decision, validation, leakage audit, error-cost and robustness assessment | `9055c5e0e35a3dd7e7ea88e36e03929f8d00a131af0d7808ad36fa787cd74c82` | Pending upload/verification |
| Jupyter notebook | `ML_Model_Training.ipynb` | Latest uploaded notebook replacing the earlier M5 notebook; compares SARIMAX and other candidate models | Committed: [Open notebook](02_WORKING/ML_Model_Training.ipynb) |
| Python training script | `ml_model_training(2).py` | Original received Python source | Committed: [Open Python file](02_WORKING/ml_model_training%282%29.py) |
| Original D5 notebook upload | `ML_Model_Training(6).ipynb` | Original submitted notebook version | Not available in this update; not claimed as uploaded |


**Data vintage described by D5:** 38 raw quarterly observations from 2017 Q1 through 2026 Q2; 34 usable supervised rows after target/lag/rolling-feature construction; 10 engineered features. The split is chronological and unshuffled: 20 train / 7 validation / 7 test. The locked test targets cover 2024 Q3–2026 Q1.

**Feature set:** current EBITDA Margin; EBITDA lag 1; two-quarter EBITDA rolling mean; current and lagged USD/INR; current and lagged monthly oil-benchmark quarterly mean; two-quarter oil rolling mean; CPI quarterly mean; WPI quarterly mean.

**Source input dependency:** the notebook and script expect `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, including the monthly oil benchmark quarterly-mean field. The exact source workbook is not included with these three uploads and its SHA-256/source version is not pinned in the D5 memorandum. A clean rerun therefore remains conditional on obtaining and reconciling that exact workbook.

## 2. Executive decision — latest notebook designation

The latest uploaded M5 notebook explicitly designates **SARIMAX as the final project model**. SARIMAX achieves the lowest validation MAE (4.953 percentage points) among the models compared, ahead of Seasonal Naive (7.470 pp). It is therefore the selected model for the project workflow and forecast artifact.

**Important holdout qualification:** SARIMAX does not achieve the lowest error on the locked test set. Seasonal Naive performs better on holdout MAE, RMSE and MASE. The README reports this result rather than describing SARIMAX as the holdout-performance winner. SARIMAX is the designated final model based on the notebook's model decision and validation comparison; Seasonal Naive remains the strongest holdout comparator in this run.

## 3. Model comparison from the latest M5 notebook

All MAE and RMSE values are EBITDA Margin percentage points (pp). Values below are transcribed from the saved validation and holdout comparison tables in `02_WORKING/ML_Model_Training.ipynb`. XGBoost was not installed in the saved execution, so it does not appear in the displayed tables.

### Validation comparison

| Role | Model | MAE (pp) | RMSE (pp) | MASE |
|---|---|---:|---:|---:|
| **Final model** | **SARIMAX** | **4.953** | **6.307** | **0.297** |
| Comparator | Seasonal Naive | 7.470 | 8.187 | 0.448 |
| Comparator | Lasso | 10.074 | 10.978 | 0.604 |
| Comparator | Elastic Net | 13.264 | 14.069 | 0.796 |
| Comparator | Ridge | 13.278 | 14.064 | 0.796 |
| Comparator | Gradient Boosting | 14.795 | 15.988 | 0.887 |
| Comparator | Random Forest | 16.635 | 17.735 | 0.998 |
| Comparator | Historical Mean | 16.876 | 17.931 | 1.012 |
| Comparator | ETS | 19.370 | 20.358 | 1.162 |

### Locked holdout comparison

| Role | Model | MAE (pp) | RMSE (pp) | MASE |
|---|---|---:|---:|---:|
| **Designated final model** | **SARIMAX** | **14.197** | **15.193** | **0.851** |
| Best holdout comparator | Seasonal Naive | 3.948 | 4.714 | 0.237 |
| Comparator | ETS | 6.612 | 6.973 | 0.397 |
| Comparator | Random Forest | 7.188 | 7.896 | 0.431 |
| Comparator | Gradient Boosting | 8.207 | 8.841 | 0.492 |
| Comparator | Elastic Net | 11.562 | 12.334 | 0.693 |
| Comparator | Ridge | 12.612 | 13.527 | 0.756 |
| Comparator | Lasso | 13.752 | 14.881 | 0.825 |
| Comparator | Historical Mean | 14.853 | 16.083 | 0.891 |

**Interpretation:** SARIMAX is the validation leader and the notebook-designated final model. Seasonal Naive is materially more accurate on this seven-observation holdout. The test sample is small, so this contrast should be treated as a model-risk finding, not hidden or dismissed. Before production reliance, investigate why validation and holdout rankings differ and perform rolling-origin evaluation.

**Saved notebook forecast:** the latest notebook's saved output reports a next-quarter EBITDA Margin forecast of **21.75%** from the final SARIMAX fit. This is the notebook output, not the D5 memorandum's earlier corrected 2026 Q3 Seasonal Naive forecast of 26.11%. These values arise from different model versions/decision contexts and must not be blended.

## 4. Evaluation design and leakage controls

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

## 5. Forecast output and version reconciliation

- **Latest notebook SARIMAX forecast:** 21.75% next-quarter EBITDA Margin, as displayed in the saved notebook output after refitting SARIMAX on the available observations.
- **Earlier D5 memorandum forecast:** 26.11% for 2026 Q3 using Seasonal Naive. This remains a historical submitted-memorandum result, not the current SARIMAX notebook forecast.
- **Earlier D4 draft:** 29.93%, identified by the D5 memorandum as a prior-draft alignment error.

The three figures refer to different model/version contexts. Use 21.75% when describing the latest notebook's SARIMAX output; use 26.11% only when describing the earlier D5 memorandum. Do not present either as a live/current forecast without rerunning the notebook against the reconciled source workbook and confirming the forecast origin.

## 6. Business interpretation and error analysis

The earlier D5 memorandum estimates quarterly revenue of about ₹18,000–20,000 crore, implying roughly ₹180–200 crore per EBITDA-margin percentage point. Its ₹710–790 crore average quarterly variance estimate is based on the memorandum's Seasonal Naive 3.95 pp test MAE, not the latest notebook's SARIMAX holdout MAE of 14.197 pp. Do not attribute the memorandum's error-cost estimate to SARIMAX.

Errors are asymmetric:
- Overprediction example: 2024 Q4 predicted 18.83% vs actual 10.95% (+7.88 pp), with potential delayed fuel/FX hedging, over-commitment, liquidity strain and covenant stress.
- Underprediction example: 2025 Q4 predicted 10.95% vs actual 18.59% (-7.64 pp), with potential over-hedging, idle cash and premature discounting.

The earlier D5 memorandum notes Seasonal Naive is weaker around Q4 inflections: MAE 2.42 pp on five stable high-margin quarters versus 7.76 pp on two Q4 quarters. This is memorandum analysis of the Seasonal Naive model, not SARIMAX. It also identifies a 2020 Q4 outlier (-201% margin) in the 27-row refit window as a major issue for linear-model intercepts and extrapolation.

## 7. Limitations and follow-up

- Seven test quarters are too few for strong generalisation claims; rankings are provisional.
- The Seasonal Naive comparator is insensitive to crude, USD/INR and inflation shocks and cannot answer macro what-if questions. SARIMAX includes macroeconomic exogenous inputs, but its weaker holdout result must be considered.
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
