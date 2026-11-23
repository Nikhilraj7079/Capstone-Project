# GitHub Project Board and Delivery Workflow

**Project:** IndiGo Profitability Intelligence  
**Active development milestone:** M4 / D4 — Model Training  
**Latest submitted evaluation:** M5 / D5 — Model Evaluation  
**Board columns:** Todo · In Progress · Done

## Done

| Work item | Record | Evidence |
|---|---|---|
| M1 / D1 — Project Charter | [Issue #1](../issues/1) | `milestones/M1_D1_Project_Charter/` |
| M2 / D2 — Data Audit | [Issue #2](../issues/2) | `milestones/M2_D2_Data_Audit/` |
| M3 / D3 — EBITDA-only EDA | [Issue #3](../issues/3) | `milestones/M3_D3_Exploratory_Data_Analysis/` |
| M5 / D5 — Model Evaluation | [Issue #6](../issues/6) | [M5 evaluation memo index](../milestones/M5_D5_Model_Evaluation/03_DELIVERABLES/README.md) |

M3 is completed with a clean-rerun/source-workbook reconciliation caveat. M5 is completed as a submitted evaluation memorandum with documented limitations; it is not production approval.

## In Progress

| Work item | Record | Current focus |
|---|---|---|
| M4 / D4 — EBITDA-margin Model Training | [Issue #4](../issues/4) | Pin exact source workbook, clean-run notebook, verify data vintage and feature availability, and close reproducibility gates |

## Todo

| Work item | Record | Planned output |
|---|---|---|
| M6 / D6 — Deployment and Monitoring | [Issue #5](../issues/5) | Integrate D5-evaluated model/feature contract; API/UI tests, refresh, data health, logs and monitoring |
| M7 / D7 — Final Communication | [Issue #7](../issues/7) | Final report, model card, presentation, speaker notes and demo |

## Workflow

M1 Charter → M2 Data Audit → M3 EBITDA EDA → M4 Model Training → M5 Evaluation → M6 Deployment/Monitoring → M7 Final Communication.

## Board rules

1. The GitHub Project Status field controls the visible columns; issue open/closed state is separate.
2. M1, M2, M3 and the D5 evaluation submission are Done, with the caveats stated above. M4 is the active development milestone. M6 and M7 remain Todo.
3. D5's submitted memo records a seven-quarter holdout (2024 Q3–2026 Q1), Seasonal Naive validation MAE 7.47 pp and test MAE/RMSE/MASE 3.95/4.71/0.24.
4. D5 corrects the D4 draft's 2026 Q3 Seasonal Naive forecast to 26.11%; the earlier 29.93% value is retained only as historical draft evidence.
5. D4-v1 assignment evidence is EBITDA-margin modelling; legacy structured PAT-margin experiment metrics must remain separate.
6. A deliverable status does not imply binary repository upload. Verify the exact file path before claiming an artifact is committed.
7. Keep README, this workflow, milestone register and issue bodies synchronized.
