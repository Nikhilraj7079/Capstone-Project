# Capstone Milestone Archive — IndiGo Profitability Intelligence

**Primary target:** Next-quarter EBITDA Margin (%) = EBITDA / Revenue from Operations × 100.

## Executive milestone overview

| Module | Deliverable | Focus | Status | Workspace |
|---|---|---|---|---|
| M1 | D1 — Project Charter | Business problem, target, scope, stakeholders and delivery plan | **Completed** | [M1](M1_D1_Project_Charter/) |
| M2 | D2 — Data Audit | Source register, definitions, quality, lineage and governance | **Completed** | [M2](M2_D2_Data_Audit/) |
| M3 | D3 — Exploratory Data Analysis | EBITDA-margin EDA, distributions, hypotheses and insights | **Completed with reproducibility caveat** | [M3](M3_D3_Exploratory_Data_Analysis/) |
| M4 | D4 — Model Training | Target/features, baselines, candidate models and training evidence | **In Progress** | [M4](M4_D4_Modelling/) |
| M5 | D5 — Model Evaluation & Validation | Holdout evaluation, leakage audit, error costs, robustness and uncertainty | **Completed with documented limitations** | [M5](M5_D5_Model_Evaluation/) |
| M6 | D6 — Deployment & Monitoring | Approved model integration, API/UI, refresh, testing and monitoring | **Todo** | [M6](M6_D6_Deployment_Monitoring/) |
| M7 | D7 — Final Communication | Final report, model card, presentation and reproducible demo | **Todo** | [M7](M7_D7_Final_Communication/) |

## Delivery sequence

`M1/D1 → M2/D2 → M3/D3 → M4/D4 → M5/D5 → M6/D6 → M7/D7`

M1–M3 have been completed with the stated M3 clean-rerun caveat. M4 remains active. D5's evaluation memorandum has now been received and documented. M6 and M7 remain Todo.

## Latest D4 / D5 evidence

### M4 / D4 — Model Training
The five-page expanded report and updated `ML_Model_Training(5).ipynb` have been received. The assignment uses 38 raw quarterly observations, 34 usable supervised rows, ten features and a chronological 20/7/7 split. Seasonal Naive is the validation winner (MAE 7.470). D4 remains In Progress because the exact source workbook hash/version and clean-run environment are not yet verified.

### M5 / D5 — Model Evaluation
The four-page executive decision memorandum `ANCP_T___D5_v1.pdf` has been received. It documents a seven-quarter holdout (2024 Q3–2026 Q1), leakage checks, candidate comparisons, forecast-error costs and limitations. Seasonal Naive records validation MAE 7.47 pp and test MAE/RMSE/MASE 3.95/4.71/0.24. The D5 point forecast for 2026 Q3 is 26.11%, correcting the earlier D4 draft's 29.93% value under the stated seasonal shift alignment.

D5 is marked completed as a submitted evaluation deliverable, with the limitations preserved: small holdout, provisional ranking, no macro sensitivity in Seasonal Naive, forecast-origin data-availability dependency and a recommended rolling-origin extension. This does not mean deployment is complete.

## Standard artifact rule

A README or folder is not proof that a binary deliverable is in GitHub. File manifests must distinguish received files from committed files. Do not claim a PDF or notebook has been uploaded until its exact repository path is verified.

## Data ownership

| Module | Data responsibility |
|---|---|
| M1 | Define target and required data; no analytical data ownership |
| M2 | Own source provenance, definitions, audit and quality controls |
| M3 | Own exact EDA panel and exploratory outputs |
| M4 | Own versioned modelling dataset, feature engineering, splits and experiments |
| M5 | Freeze/evaluate M4 model and data vintage; own holdout predictions and error evidence |
| M6 | Consume D5-approved model and feature contract; own runtime/monitoring data |
| M7 | Reference approved versions for final communication |

## Governance links

- [Milestone Register](MILESTONE_REGISTER.csv)
- [Project Status and Work Log](../docs/PROJECT_STATUS_AND_WORKLOG.md)
- [Project Data Hub](../data/README.md)
- [Workflow and Data Governance](../docs/WORKFLOW_AND_DATA_GOVERNANCE.md)
