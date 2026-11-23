# Project Status and Work Log — IndiGo Profitability Intelligence

**Status date:** 23 November 2026  
**Repository:** Nikhilraj7079/Capstone-Project  
**Branch:** main  
**Current active development milestone:** M6 / D6 — Deployment and Monitoring  
**Latest submitted evaluation milestone:** M5 / D5 — Model Evaluation

## 1. Project purpose

Develop an end-to-end analytics system to forecast IndiGo's next-quarter **EBITDA Margin** using historical company financial data and selected macroeconomic/market indicators. This is profitability forecasting, not stock-price prediction.

**Primary target:** EBITDA Margin (%) = EBITDA / Revenue from Operations × 100. PAT Margin and EBITDAR are not substitutes for this target.

## 2. Executive module status

| Module | Deliverable | Status | Evidence / next gate |
|---|---|---|---|
| M1 | D1 Project Charter | Completed | Revised EBITDA-focused scope and charter records |
| M2 | D2 Data Audit | Completed | Source register, collection tracker, data dictionary, audit and governance records |
| M3 | D3 EDA | Completed | Executed EDA notebook and 38-quarter analysis; exact workbook is needed for a clean rerun and one quarterly discrepancy requires reconciliation |
| M4 | D4 Model Training | **Completed** | Expanded report and updated training notebook received; pin exact input workbook, clean-run and verify forecast timing |
| M5 | D5 Model Evaluation | **Completed** | Four-page evaluation memo received; chronological holdout, leakage checklist, error-cost assessment, robustness discussion and empirical risk band |
| M6 | D6 Deployment & Monitoring | **In Progress** | Integrate D5-approved model and feature contract; test API/UI, refresh, data health and monitoring |
| M7 | D7 Final Communication | Todo | Final report, model card, slides, speaker notes and reproducible demo |

## 3. Latest D4 / D5 update

### D4 — Model Training (M4)
The expanded five-page D4 report and updated `ML_Model_Training(5).ipynb` were received. The assignment describes 38 raw quarters (2017 Q1–2026 Q2), 34 usable supervised rows, ten features and a chronological split of 20 training / 7 validation / 7 test rows. Nine candidates are compared. Seasonal Naive wins validation with MAE 7.470.

D4 is recorded as Completed. The exact source workbook version/hash and original execution environment are not captured in the submitted evidence; retain these as reproducibility follow-ups during D6 integration. The notebook expects `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, with the monthly oil benchmark quarterly-mean field.

### D5 — Model Evaluation & Validation (M5)
The four-page `ANCP_T___D5_v1.pdf` executive decision memorandum was received. It evaluates the selected Seasonal Naive benchmark on a locked seven-quarter holdout from 2024 Q3 through 2026 Q1 and documents a leakage checklist.

Reported results:
- Validation MAE: 7.47 EBITDA-margin percentage points.
- Test MAE: 3.95 pp.
- Test RMSE: 4.71 pp.
- Test MASE: 0.24.
- D5 recommends Seasonal Naive as the primary one-quarter-ahead benchmark, with ETS / Gradient Boosting as secondary cross-checks.

**Forecast correction:** D5 states that the 2026 Q3 Seasonal Naive forecast is 26.11%, because `shift(3)` repeats the 2025 Q3 actual. The earlier D4 draft's 29.93% value is explicitly identified as a prior draft error (it corresponds to 2025 Q1). Use 26.11% when referencing the D5 memo, and retain the correction history.

D5 also reports an empirical ±9.24 pp risk band (16.9%–35.4%). This is an empirical error buffer, not a model-native prediction interval or guarantee.

### D5 limitations retained
- Only seven test quarters; model ranking is provisional and confidence comparisons are limited.
- Seasonal Naive is not sensitive to crude, FX or inflation shocks; it cannot answer macroeconomic what-if questions.
- Dated/global oil benchmark is a proxy, not IndiGo's actual ATF landed cost.
- Forecast validity depends on current-quarter financial and macro data being final and available at forecast time.
- Rolling-origin backtesting and more quarters are recommended before production use.
- The notebook's source workbook hash and clean-run environment are not yet recorded.

## 4. Current active milestone — D6 Deployment and Monitoring

D1–D5 are complete. D6 is now the active development phase. The deployment work consumes the evaluated D5 model and its feature contract; it does not silently retrain or change the model. Active tasks are model loading, preprocessing parity, API request/response validation, frontend integration, controlled data refresh, secure secrets handling, logging, monitoring and end-to-end testing.

The D4/D5 data-vintage and forecast-origin limitations remain visible as deployment controls. Do not claim production readiness until the end-to-end application, tests and monitoring evidence pass.

## 5. Data ownership by milestone

| Module | Data responsibility |
|---|---|
| M1 | Define target, scope and required inputs |
| M2 | Own source provenance, definitions, quality and data audit |
| M3 | Own exact EDA panel, notebook and exploratory outputs |
| M4 | Own model-ready dataset, features, splits, experiments and model training evidence |
| M5 | Freeze/evaluate M4 model and data vintage; own predictions, errors and evaluation evidence |
| M6 | Consume D5-approved model and feature contract; own runtime refresh and monitoring |
| M7 | Reference approved, traceable versions for final report and presentation |

## 6. Data governance

- Keep source observation dates separate from publication/availability dates.
- Exclude financial rows marked estimates from realised historical target labels.
- Do not bridge missing target quarters when building next-quarter labels.
- Do not substitute a different oil field or quarterly workbook without schema and value reconciliation.
- The D5 report's oil benchmark is a proxy, not IndiGo's realised ATF price.
- Preserve source workbook hashes, transformation version, units and row counts for every modelling data vintage.
- Keep licensed Bloomberg exports and data-derived workbooks private unless redistribution is permitted.
- Never commit API keys, credentials or secrets.

## 7. End-to-end delivery sequence

M1 charter → M2 data audit → M3 EDA → M4 model training → M5 model evaluation → M6 deployment and monitoring → M7 final communication.

## 8. Next actions

1. Integrate the D5-evaluated model and preprocessing into the API.
2. Enforce the D4/D5 feature schema, data-vintage and forecast-origin availability rules.
3. Connect the frontend to the prediction and data-health endpoints.
4. Validate model loading, request/response schemas, errors and fallback behaviour.
5. Complete secure API-key configuration and controlled market-data refresh.
6. Add prediction logging, source freshness checks, drift/error monitoring and a deployment runbook.
7. Run end-to-end tests and capture D6 demonstration evidence.
