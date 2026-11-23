# Project Data Hub — IndiGo Profitability Intelligence

**Current target:** Next-quarter EBITDA Margin (%) = EBITDA / Revenue from Operations × 100.  
**Data governance owner:** M2 / D2 — Data Audit.

This folder is the project-wide source catalogue. Milestone-specific data records identify the exact version, source hash, transformation and purpose used by each module.

## 1. Data ownership by module

| Module | Data responsibility | Canonical location |
|---|---|---|
| M1 / D1 | Define target, scope and required inputs; no analytical dataset | [M1 workspace](../milestones/M1_D1_Project_Charter/) |
| M2 / D2 | Own original source files, definitions, source register, data dictionary and quality controls | [M2 data](../milestones/M2_D2_Data_Audit/data/) |
| M3 / D3 | Own the EDA analysis panel, notebook, outputs and hypotheses | [M3 data](../milestones/M3_D3_Exploratory_Data_Analysis/data/) |
| M4 / D4 | Own versioned modelling input, target/features, splits and experiment lineage | [M4 data](../milestones/M4_D4_Modelling/data/) |
| M5 / D5 | Freeze and evaluate the M4 model/data vintage; own holdout predictions, errors, metrics and evaluation records | [M5 inputs](../milestones/M5_D5_Model_Evaluation/01_INPUTS/) and [M5 evidence](../milestones/M5_D5_Model_Evaluation/04_EVIDENCE/) |
| M6 / D6 | Consume D5-approved model and feature contract; own runtime schemas, refresh logs and monitoring | [M6 inputs](../milestones/M6_D6_Deployment_Monitoring/01_INPUTS/) |
| M7 / D7 | Reference approved data/model versions for final communication | [M7 inputs](../milestones/M7_D7_Final_Communication/01_INPUTS/) |

## 2. Source inventory and controls

| Category | Source / fields | Frequency | Intended use | Control |
|---|---|---|---|---|
| IndiGo financials | INDIGO IN; SALES_REV_TURN and EBITDA | Quarterly | EBITDA Margin target | Reconcile source line items; exclude estimated future periods from actual labels |
| USD/INR | USDINR REGN Curncy; PX_LAST | Monthly | Currency indicator | Apply historical availability cutoff |
| CPI | INFUTOTY Index; PX_LAST | Monthly | Inflation indicator | Verify instrument definition and base |
| WPI | INBGWPIY Index; PX_LAST | Monthly | Inflation indicator | Verify series definition and base continuity |
| Dated Brent | EUCRBRDT Index; PX_LAST | Daily/monthly | Global crude benchmark proxy | Not Indian ATF or IndiGo's realised fuel cost |

The Bloomberg Terminal exports are the actual source for the collected workbook values. Public RBI, MoSPI, OEA and IndiGo links elsewhere in project documentation are independent cross-check references, not the source of those exported values.

## 3. Dataset allocation and version rules

- M2 owns raw source provenance and audit evidence.
- M3 owns the 38-quarter EBITDA-only EDA panel and exploratory outputs.
- M4 owns the modelling dataset and engineered features. The D4 assignment workbook is expected to contain the monthly oil benchmark quarterly mean.
- M5 consumes the exact M4 model/data vintage and owns evaluation predictions, errors and metrics. The D5 memorandum reports 38 raw quarters (2017 Q1–2026 Q2), 34 usable supervised rows and a 20/7/7 chronological split. The exact source workbook hash/version was not captured in the submitted memo and must be pinned before claiming a fully reproducible frozen vintage.
- M6 consumes the D5-approved model and feature contract; it must not silently retrain on a different data vintage.
- M7 uses only approved and traceable results.

Every new dataset version must record source file names, SHA-256, observation coverage, units, transformation version, row counts, data-quality checks and publication/availability dates where known.

## 4. D5 evaluation data record — 15 November 2026 memorandum

The submitted D5 evaluation memorandum records:
- 38 raw quarterly observations from 2017 Q1 to 2026 Q2;
- 34 usable supervised observations after target/lag/rolling feature construction;
- ten engineered features;
- chronological split: 20 train, 7 validation, 7 test;
- locked test period: 2024 Q3–2026 Q1;
- selected Seasonal Naive validation MAE 7.47 pp and test MAE/RMSE/MASE 3.95/4.71/0.24.

**Data limitation:** the exact source workbook hash and original model execution environment are not captured in the submitted artifacts. The D4 notebook expects `EDA ANALYSIS.xlsx` / `Sheet1` and the monthly oil benchmark quarterly-mean column. Do not substitute a newer workbook without reconciling column schema, quarterly values and financial alignment. The D5 report's point-in-time condition requires current-quarter EBITDA and macro means to be final and available at the forecast date; otherwise features must be lagged or separately forecast.

## 5. Important modelling and governance rules

1. Target is EBITDA Margin (%) = EBITDA / Revenue from Operations × 100. PAT Margin and EBITDAR are not substitutes.
2. Rebuild financial outcomes from audited raw statement rows; do not use a known misaligned legacy financial sheet.
3. Exclude estimated financial periods from realised target labels.
4. Use consistent Indian fiscal-quarter labels where the approved pipeline requires them.
5. Separate observation dates from publication/availability dates.
6. Do not bridge missing target quarters when creating next-quarter labels.
7. Dated Brent is a crude benchmark proxy, not IndiGo's realised ATF cost.
8. Keep proprietary Bloomberg exports and derived data private unless redistribution is permitted.
9. Do not publish credentials or API keys.

## 6. File navigation

- [Raw source index](raw/README.md)
- [Processed data index](processed/README.md)
- [Source register](source_register.csv)
- [Collection tracker](collection_tracker.csv)
- [Milestone archive](../milestones/README.md)
- [M5 evaluation inputs](../milestones/M5_D5_Model_Evaluation/01_INPUTS/README.md)
