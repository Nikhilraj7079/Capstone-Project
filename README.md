# IndiGo Profitability Intelligence System

**Academic capstone | PGDM Business Analytics | Modules M1–M7 | Deliverables D1–D7**

**Primary target:** Next-quarter EBITDA Margin (%) = EBITDA / Revenue from Operations × 100.

> This project analyses and forecasts IndiGo's operating profitability. The target is EBITDA Margin—not share price, PAT Margin or EBITDAR.

## Table of contents
- [1. Introduction](#1-introduction)
- [2. Project objectives](#2-project-objectives)
- [3. Business problem and scope](#3-business-problem-and-scope)
- [4. End-to-end methodology](#4-end-to-end-methodology)
- [5. Module-wise project journey](#5-module-wise-project-journey)
  - [M1 / D1 — Project Charter](#m1--d1--project-charter)
  - [M2 / D2 — Data Audit](#m2--d2--data-audit)
  - [M3 / D3 — Exploratory Data Analysis](#m3--d3--exploratory-data-analysis)
  - [M4 / D4 — Model Training](#m4--d4--model-training)
  - [M5 / D5 — Model Evaluation](#m5--d5--model-evaluation-and-validation)
  - [M6 / D6 — Deployment and Monitoring](#m6--d6--deployment-and-monitoring)
  - [M7 / D7 — Final Communication](#m7--d7--final-communication)
- [6. Dataset and data sources](#6-dataset-and-data-sources)
- [7. Model results](#7-model-results-and-interpretation)
- [8. Application architecture](#8-application-architecture-and-d6-progress)
- [9. Repository structure](#9-repository-structure)
- [10. Project status](#10-project-status)
- [11. Key documents](#11-key-project-documents)
- [12. Limitations](#12-limitations-and-responsible-use)

---

## 1. Introduction

Airline profitability can change due to fuel prices, foreign exchange movements, inflation and wider operating conditions. This capstone develops an analytics workflow to understand IndiGo's historical operating profitability and estimate its next-quarter EBITDA Margin using quarterly financial information and selected macroeconomic/market indicators.

The work follows a full analytics lifecycle: project definition, data audit, exploratory analysis, model training, model evaluation, application development, monitoring and final communication.

## 2. Project objectives

- Understand IndiGo's historical operating profitability.
- Define and consistently calculate EBITDA Margin as the target.
- Collect, document and audit relevant financial and macroeconomic data.
- Explore historical patterns and associations between EBITDA Margin and USD/INR, CPI, WPI and an oil-market proxy.
- Engineer time-aware features and compare forecasting approaches.
- Evaluate models using chronological validation and holdout testing.
- Carry the evaluated model and feature contract into a web application.
- Establish API, data-refresh, testing and monitoring workflows.
- Communicate results with their assumptions and limitations.

## 3. Business problem and scope

**Business question:** Can IndiGo's historical financial performance and available macroeconomic/market indicators help estimate next-quarter EBITDA Margin, and does the selected approach perform better than a simple baseline on unseen quarters?

**Target formula:** EBITDA Margin (%) = EBITDA / Revenue from Operations × 100.

**In scope:** Quarterly revenue and EBITDA; USD/INR; CPI; WPI; Dated Brent crude benchmark; exploratory analysis; feature engineering; forecasting; evaluation; API and web application development.

**Out of scope / distinctions:** This is not a share-price prediction project. PAT Margin and EBITDAR are not substitutes for the approved target. Dated Brent is a global crude benchmark proxy, not IndiGo's actual aviation turbine fuel landed cost. Same-period correlations are exploratory and do not establish causation or predictive power.

## 4. End-to-end methodology

| Stage | Module | Main work |
|---|---|---|
| Define | [M1 / D1](milestones/M1_D1_Project_Charter/) | Business problem, target, scope and project plan |
| Audit | [M2 / D2](milestones/M2_D2_Data_Audit/) | Data collection, definitions, quality and governance |
| Explore | [M3 / D3](milestones/M3_D3_Exploratory_Data_Analysis/) | EDA, distributions, hypotheses and insights |
| Train | [M4 / D4](milestones/M4_D4_Modelling/) | Features, baselines and candidate models |
| Evaluate | [M5 / D5](milestones/M5_D5_Model_Evaluation/) | Chronological validation, holdout testing and model decision |
| Deploy | [M6 / D6](milestones/M6_D6_Deployment_Monitoring/) | API, web interface, refresh, tests and monitoring |
| Communicate | [M7 / D7](milestones/M7_D7_Final_Communication/) | Final report, model card, presentation and demo |

The modelling workflow uses chronological splits without random shuffling. Validation is used for model selection; the holdout test is kept separate for evaluation.

## 5. Module-wise project journey

### M1 / D1 — Project Charter

**Purpose:** Define the business problem, objectives, target, scope, stakeholders, responsibilities, assumptions, risks and delivery plan.

**Work completed:** Established the IndiGo profitability forecasting problem; selected EBITDA Margin as the primary target; documented project scope, intended outputs, governance and milestone plan.

**Status: Completed.**  
**Module workspace:** [M1 — Project Charter](milestones/M1_D1_Project_Charter/)

### M2 / D2 — Data Audit

**Purpose:** Confirm that financial and macroeconomic data are traceable, consistently defined and suitable for analysis.

**Work completed:** Registered source workbooks and instruments; documented fields, units and frequencies; reviewed coverage, missingness, duplicates, estimates, alignment and data-quality issues; prepared source register, dictionary and collection tracker.

**Data categories:** IndiGo financial statements, USD/INR, CPI, WPI and Dated Brent.

**Status: Completed.**  
**Module workspace:** [M2 — Data Audit](milestones/M2_D2_Data_Audit/)

### M3 / D3 — Exploratory Data Analysis

**Purpose:** Understand the distribution and historical movement of EBITDA Margin and explore its same-period associations with selected indicators.

**Work completed:** Analysed 38 quarterly observations from 2017 Q1 to 2026 Q2; examined EBITDA Margin with USD/INR, CPI, WPI and oil benchmark measures; reviewed descriptive statistics and exploratory hypotheses; retained the executed notebook and saved outputs.

**Descriptive results:** Mean EBITDA Margin 12.306%; median 15.000%; standard deviation 14.255 percentage points; minimum -36.667%; maximum 29.933%.

These are exploratory sample results, not causal conclusions or next-quarter predictive validation. The exact source workbook needed for a clean notebook rerun remains a reproducibility caveat.

**Status: Completed.**  
**Module workspace:** [M3 — Exploratory Data Analysis](milestones/M3_D3_Exploratory_Data_Analysis/)

### M4 / D4 — Model Training

**Purpose:** Train and compare candidate approaches for next-quarter EBITDA Margin forecasting.

**Work completed:** Prepared a supervised dataset; engineered lagged and rolling features; used a chronological split of 20 training, 7 validation and 7 test observations; compared Seasonal Naive, Historical Mean, Ridge, Lasso, Elastic Net, Random Forest, Gradient Boosting, XGBoost and ETS.

**Modelling profile:** 38 raw quarterly observations, 34 usable supervised rows and 10 engineered features. Seasonal Naive recorded the lowest validation MAE of 7.470 percentage points.

**Status: Completed as a submitted modelling deliverable.** Exact source workbook/version and clean-run environment remain documented reproducibility controls for the D6 handoff.

**Module workspace:** [M4 — Model Training](milestones/M4_D4_Modelling/)

### M5 / D5 — Model Evaluation and Validation

**Purpose:** Evaluate candidate models on chronological validation and holdout data, assess forecast risk and select the approach to carry into deployment.

**Work completed:** Evaluated a locked seven-quarter holdout from 2024 Q3 to 2026 Q1; documented chronological split and leakage controls; compared model errors; discussed business implications of over- and under-prediction; recorded limitations and robustness recommendations.

**Decision:** Seasonal Naive is the primary one-quarter-ahead benchmark; ETS and Gradient Boosting are secondary cross-checks.

| Selected-model metric | Result |
|---|---:|
| Validation MAE | 7.47 percentage points |
| Holdout test MAE | 3.95 percentage points |
| Holdout test RMSE | 4.71 percentage points |
| Holdout test MASE | 0.24 |

The D5 memorandum records a corrected 2026 Q3 point forecast of 26.11%, replacing the earlier D4 draft value of 29.93%. Its empirical range of approximately 16.9%–35.4% is a risk buffer, not a model-native confidence interval.

**Limitations:** Only seven test quarters are available, so rankings are provisional. Seasonal Naive does not directly respond to macroeconomic shocks. Rolling-origin backtesting is recommended before production use.

**Status: Completed as a submitted evaluation deliverable, with limitations documented.**  
**Module workspace:** [M5 — Model Evaluation](milestones/M5_D5_Model_Evaluation/)

### M6 / D6 — Deployment and Monitoring

**Purpose:** Convert the evaluated forecasting workflow into a usable application while preserving the D4/D5 model definition, preprocessing and forecast-time data controls.

**Work in progress:**
- Integrate the D5-evaluated model and feature contract into the prediction service.
- Connect the Python backend/API to the web interface.
- Align live transformations and refresh frequency with the training schema.
- Validate API request/response formats and missing-data handling.
- Protect API credentials and configuration.
- Record model version, forecast time, input vintage and predictions.
- Monitor source freshness, data quality, drift and prediction errors when actuals become available.
- Run end-to-end tests and prepare deployment evidence.

**Status: In Progress.** Existing code is a starting scaffold; D6 is not complete until end-to-end integration and testing are demonstrated.

**Module workspace:** [M6 — Deployment and Monitoring](milestones/M6_D6_Deployment_Monitoring/)

### M7 / D7 — Final Communication

**Purpose:** Communicate the completed project, findings, model performance, application workflow and limitations.

**Planned work:** Final capstone report; model card; presentation and speaker notes; reproducible application demonstration and runbook; verification that all claims trace to approved evidence.

**Status: Todo — planned after D6 completion.**  
**Module workspace:** [M7 — Final Communication](milestones/M7_D7_Final_Communication/)

## 6. Dataset and data sources

The [Project Data Hub](data/README.md) contains the source catalogue, data dictionary references, collection tracker, source register, raw workbooks, processed workbook and templates.

### Main dataset links

| Dataset / resource | Direct repository link | Purpose |
|---|---|---|
| Project Data Hub | [data/README.md](data/README.md) | Main data catalogue and ownership |
| Data Collection Register | [DATA_COLLECTION_REGISTER.md](data/DATA_COLLECTION_REGISTER.md) | Workbook inventory, tabs and lineage |
| Source Register | [source_register.csv](data/source_register.csv) | Source identifiers and provenance |
| Collection Tracker | [collection_tracker.csv](data/collection_tracker.csv) | Data collection tracking |
| IndiGo Data Dictionary | [IndiGo_Data_Dictionary.csv](IndiGo_Data_Dictionary.csv) | Field definitions |
| Raw source folder | [data/raw/](data/raw/) | Original source workbooks |
| CP(4).xlsx | [Open workbook](data/raw/CP%284%29.xlsx) | Financial and macro/market source workbook |
| CP Master Data(3).xlsx | [Open workbook](data/raw/CP%20Master%20Data%283%29.xlsx) | Consolidated historical workbook |
| Processed data folder | [data/processed/](data/processed/) | Processed datasets |
| Final Quarterly Data workbook | [Open workbook](data/processed/Final_Quarterly_Data%281%29.xlsx) | Processed quarterly dataset |
| Data templates | [data/templates/](data/templates/) | Standardized source templates |

### Data categories and intended use

| Category | Frequency | Intended role |
|---|---|---|
| IndiGo revenue and EBITDA | Quarterly | Construct EBITDA Margin target |
| USD/INR | Monthly | Currency indicator |
| CPI | Monthly | Inflation indicator |
| WPI | Monthly | Inflation indicator |
| Dated Brent | Daily / monthly | Global oil-market proxy |

### Data ownership and governance

- M2 owns source provenance and data-quality records.
- M3 owns the EDA panel and exploratory outputs.
- M4 owns the versioned modelling input, features, splits and experiment lineage.
- M5 freezes and evaluates the M4 model/data vintage.
- M6 consumes the evaluated model and feature contract; it must not silently substitute a different dataset or retrain a different model.
- M7 uses only traceable and approved data/model versions.

**Reproducibility note:** The D4 notebook expects a workbook named EDA ANALYSIS.xlsx, worksheet Sheet1, with a monthly oil benchmark quarterly-mean field. Its exact version/hash is not pinned in the submitted evidence. Do not substitute a different workbook without reconciling schema, financial alignment and quarter values.

**Data rights:** Some source values originate from Bloomberg exports. Proprietary exports and derived data should not be redistributed publicly unless the applicable licence permits it. Never commit API keys or credentials.

## 7. Model results and interpretation

The D4/D5 work compares simple benchmarks, linear models, tree-based models and ETS. Seasonal Naive repeats the corresponding quarter from the prior year. It is transparent and useful as a reference, but does not directly respond to changes in fuel prices, foreign exchange or inflation.

The reported D5 holdout MAE is 3.95 percentage points and MASE is 0.24. Since the test set contains only seven quarters, these results are provisional and should not be treated as proof of stable future performance.

The corrected D5 point forecast for 2026 Q3 is 26.11%. The empirical risk band is not a statistical guarantee. Present forecasts with their target quarter, data vintage, feature-availability cutoff and evaluation limitations.

## 8. Application architecture and D6 progress

The intended application flow is:

1. Data sources and the approved data store provide historical financial and macroeconomic inputs.
2. The data pipeline validates, transforms and aligns inputs with the training feature contract.
3. The prediction service loads the evaluated model and returns a next-quarter EBITDA Margin estimate.
4. The backend API exposes forecast and data-health information.
5. The frontend displays the forecast, supporting indicators and caveats.
6. Monitoring records source freshness, model version, input snapshot, predictions and subsequent errors when actual results become available.

**Repository components:**
- [Backend](backend/) — Python API and request/response routes.
- [Frontend](frontend/) — HTML, CSS and JavaScript interface.
- [Source connectors](src/connectors/) — market and macro data connectors.
- [Data pipeline and feature code](src/) — dataset and feature processing.
- [Automated tests](tests/) — test files.
- [Environment example](.env.example) — configuration template; populate secrets locally, never commit them.

**D6 status: In Progress.** The presence of code files does not by itself mean the application is fully integrated, deployed or production-ready. End-to-end tests, secure configuration, refresh validation and monitoring evidence remain part of the D6 completion gate.

## 9. Repository structure

```text
Capstone-Project/
├── README.md
├── data/                  # Raw, processed, templates and registers
├── docs/                  # Charter, plans, governance and work log
├── milestones/
│   ├── M1_D1_Project_Charter/
│   ├── M2_D2_Data_Audit/
│   ├── M3_D3_Exploratory_Data_Analysis/
│   ├── M4_D4_Modelling/
│   ├── M5_D5_Model_Evaluation/
│   ├── M6_D6_Deployment_Monitoring/
│   └── M7_D7_Final_Communication/
├── backend/               # API service
├── frontend/              # Web interface
├── src/                   # Data pipeline, features and connectors
├── notebooks/             # Analysis and modelling notebooks
├── experiments/           # Experiment evidence
├── models/                # Model artefact location
└── tests/                 # Automated tests
```

Each milestone folder contains its own README, milestone controls, checklist, evaluation record and manifest, with working files and evidence where available.

## 10. Project status

| Module | Deliverable | Status |
|---|---|---|
| M1 | D1 — Project Charter | **Completed** |
| M2 | D2 — Data Audit | **Completed** |
| M3 | D3 — Exploratory Data Analysis | **Completed** |
| M4 | D4 — Model Training | **Completed** |
| M5 | D5 — Model Evaluation and Validation | **Completed** |
| M6 | D6 — Deployment and Monitoring | **In Progress** |
| M7 | D7 — Final Communication | **Todo** |

For detailed records, see the [Milestone Register](milestones/MILESTONE_REGISTER.csv), [Milestone Archive](milestones/README.md) and [Project Status and Work Log](docs/PROJECT_STATUS_AND_WORKLOG.md).

## 11. Key project documents

- [Master Project Plan](docs/Master_Project_Plan.md)
- [Project Charter](docs/Project_Charter.md)
- [Project Data Hub](data/README.md)
- [Data Collection Register](data/DATA_COLLECTION_REGISTER.md)
- [Data Feasibility Audit](docs/Data_Feasibility_Audit.md)
- [Master Dataset Schema](docs/Master_Dataset_Schema.md)
- [Workflow and Data Governance](docs/WORKFLOW_AND_DATA_GOVERNANCE.md)
- [Milestone Register](milestones/MILESTONE_REGISTER.csv)
- [Milestone Archive](milestones/README.md)
- [Project Status and Work Log](docs/PROJECT_STATUS_AND_WORKLOG.md)
- [GitHub Project Board and Delivery Workflow](docs/GITHUB_PROJECT_BOARD.md)

## 12. Limitations and responsible use

- The historical quarterly sample is small, and the holdout period contains only seven quarters.
- EDA correlations are same-period associations and must not be described as causal effects.
- Dated Brent is a proxy, not IndiGo's actual ATF landed cost.
- Historical publication/availability timestamps are incomplete; a feature must be available at the forecast origin to be used legitimately.
- Seasonal Naive does not directly incorporate macroeconomic shocks or scenario changes.
- The exact D4 source workbook/version and clean-run environment require reconciliation for full reproducibility.
- Forecasts are estimates, not guarantees. This academic prototype is not investment advice or a production-ready operational decision system without further validation.

---

**Project repository:** [Nikhilraj7079 / Capstone-Project](https://github.com/Nikhilraj7079/Capstone-Project)  
**Current active module:** [M6 / D6 — Deployment and Monitoring](milestones/M6_D6_Deployment_Monitoring/)
