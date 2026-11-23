# IndiGo Profitability Intelligence System

**Capstone:** PGDM Business Analytics · **Modules:** M1–M7 · **Deliverables:** D1–D7  
**Primary forecast target:** Next-quarter EBITDA Margin (%) = EBITDA / Revenue from Operations × 100  
**Repository owner:** Nikhilraj7079

> This project forecasts IndiGo's operating profitability, not its share price. The primary modelling target is EBITDA Margin, not PAT Margin or EBITDAR.

## Project status

| Module | Deliverable | Status | Evidence / next step |
|---|---|---|---|
| M1 | D1 — Project Charter | **Completed** | Revised EBITDA-focused project scope and charter records |
| M2 | D2 — Data Audit | **Completed** | Source register, data dictionary, audit and data-governance records |
| M3 | D3 — Exploratory Data Analysis | **Completed with reproducibility caveat** | Executed EBITDA-margin EDA notebook and 38-quarter analysis; exact source workbook reconciliation is still required for a clean rerun |
| M4 | D4 — Model Training | **In Progress** | D4 expanded training report and updated model-training notebook received; reproducibility/data-vintage and model handoff controls remain open |
| M5 | D5 — Model Evaluation & Validation | **Completed with documented limitations** | D5 executive decision memorandum submitted; locked chronological holdout, leakage audit, error-cost assessment and forecast-risk discussion documented |
| M6 | D6 — Deployment & Monitoring | **Todo** | Build and validate the application using the approved D5 model and feature contract |
| M7 | D7 — Final Communication | **Todo** | Final report, model card, presentation, speaker notes and demo |

For the complete milestone sequence, see [Milestone Register](milestones/MILESTONE_REGISTER.csv), [Milestone Archive](milestones/README.md), and [Project Status and Work Log](docs/PROJECT_STATUS_AND_WORKLOG.md).

## Latest project update — D4 and D5

### M4 / D4 — Model Training
- Report: `ANCP_T##_D4_Expanded_Model_Training_Report.pdf` — received; GitHub binary placement is pending.
- Notebook: `ML_Model_Training(5).ipynb` — latest notebook received; GitHub binary placement is pending.
- D4 modelling record: 38 raw quarterly observations, 34 usable supervised rows, 10 engineered features and a chronological 20 / 7 / 7 train-validation-test split.
- Nine candidate approaches were compared. Seasonal Naive had the lowest validation MAE of 7.470.
- D4 remains **In Progress** until the exact source workbook/version is pinned, the notebook is clean-run with environment metadata, and forecast-time feature availability is verified.

See [M4 / D4 README](milestones/M4_D4_Modelling/README.md).

### M5 / D5 — Model Evaluation & Validation
- Evaluation memorandum: `ANCP_T___D5_v1.pdf` — received; GitHub binary placement is pending.
- D5 records a locked seven-quarter holdout from 2024 Q3 to 2026 Q1 and a leakage-control checklist.
- Selected benchmark: Seasonal Naive.
- Validation MAE: **7.47 percentage points**.
- Holdout test MAE / RMSE / MASE: **3.95 / 4.71 / 0.24**.
- D5 corrects the earlier D4 draft's next-quarter point forecast: under the documented `shift(3)` seasonal-naive alignment, the 2026 Q3 point forecast is **26.11%**, not 29.93%. The memorandum reports an empirical ±9.24 percentage-point band (16.9%–35.4%); this is a risk buffer, not a model-native prediction interval.
- The D5 memo documents small-sample, forecast-timing, oil-proxy and regime-change limitations. Rolling-origin backtesting remains a recommended extension before production use.

See [M5 / D5 README](milestones/M5_D5_Model_Evaluation/README.md).

## Module and deliverable navigation

| Module | Main workspace |
|---|---|
| M1 / D1 — Project Charter | [M1](milestones/M1_D1_Project_Charter/) |
| M2 / D2 — Data Audit | [M2](milestones/M2_D2_Data_Audit/) |
| M3 / D3 — Exploratory Data Analysis | [M3](milestones/M3_D3_Exploratory_Data_Analysis/) |
| M4 / D4 — Model Training | [M4](milestones/M4_D4_Modelling/) |
| M5 / D5 — Model Evaluation | [M5](milestones/M5_D5_Model_Evaluation/) |
| M6 / D6 — Deployment & Monitoring | [M6](milestones/M6_D6_Deployment_Monitoring/) |
| M7 / D7 — Final Communication | [M7](milestones/M7_D7_Final_Communication/) |

## Data governance and source package

The project data hub is [data/README.md](data/README.md). Data ownership is milestone-specific:
- M2 owns audited source provenance, definitions and data quality.
- M3 owns the EDA analysis panel and exploratory outputs.
- M4 owns the versioned modelling input, features, splits and experiments.
- M5 freezes and evaluates the M4 model/data vintage and owns evaluation predictions, errors and validation evidence.
- M6 consumes the D5-approved model and feature contract.
- M7 reports only traceable, approved evidence.

The model dataset used by the D4/D5 assignment report contains 38 quarterly observations (2017 Q1–2026 Q2), with 34 usable supervised rows. The notebook expects the monthly oil benchmark quarterly-mean field. Do not substitute another workbook version without reconciling columns, financial alignment and quarter values. Licensed Bloomberg exports and data-derived workbooks must not be published unless the applicable licence permits redistribution.

## Project objective and methodology

**Business question:** Can historical IndiGo financial performance and available macroeconomic indicators help forecast next-quarter EBITDA Margin, and does the selected model outperform a simple baseline on unseen quarters?

The D4/D5 assignment uses:
- EBITDA Margin and lag/rolling features;
- USD/INR, a monthly crude-oil benchmark proxy, CPI and WPI;
- chronological 60% / 20% / 20% splitting without random shuffling;
- MAE, RMSE and MASE for model evaluation;
- validation MAE for model selection, with the holdout test kept separate.

Seasonal Naive is a benchmark, not a macro-sensitive model. It cannot answer crude-oil or FX what-if questions. D5 reports that the ranking is provisional because the test set contains only seven quarters. The oil input is a global crude benchmark proxy, not IndiGo's actual ATF landed cost.

## Product development status

The planned product includes a Python data/ML backend, API, interactive web interface, data refresh, scenario analysis and monitoring. The D5 evaluation memo is not proof that deployment is complete. M6 remains Todo until the D5-approved model and feature contract are integrated and the API/UI, refresh, data health and monitoring workflow are tested.

## Important project links

- [Master Project Plan](docs/Master_Project_Plan.md)
- [Project Status and Work Log](docs/PROJECT_STATUS_AND_WORKLOG.md)
- [Workflow and Data Governance](docs/WORKFLOW_AND_DATA_GOVERNANCE.md)
- [Project Data Hub](data/README.md)
- [Milestone Register](milestones/MILESTONE_REGISTER.csv)
- [GitHub Project Board and Delivery Workflow](docs/GITHUB_PROJECT_BOARD.md)

## Academic and usage note

This is an academic capstone prototype. Forecasts are estimates, not guarantees or financial advice. Results must be presented with their evaluation period, data vintage, assumptions and limitations.