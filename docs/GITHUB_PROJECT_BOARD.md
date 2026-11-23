# GitHub Project Board and Delivery Workflow

**Project:** IndiGo Profitability Intelligence  
**Active development milestone:** M6 / D6 — Deployment and Monitoring  
**Latest submitted evaluation:** M5 / D5 — Model Evaluation  
**Board columns:** Todo · In Progress · Done

## Done

| Work item | Record | Evidence |
|---|---|---|
| M1 / D1 — Project Charter | [Issue #1](../issues/1) | `milestones/M1_D1_Project_Charter/` |
| M2 / D2 — Data Audit | [Issue #2](../issues/2) | `milestones/M2_D2_Data_Audit/` |
| M3 / D3 — EBITDA-only EDA | [Issue #3](../issues/3) | `milestones/M3_D3_Exploratory_Data_Analysis/` |
| M4 / D4 — Model Training | [Issue #4](../issues/4) | [M4 modelling report and notebook index](../milestones/M4_D4_Modelling/README.md) |
| M5 / D5 — Model Evaluation | [Issue #6](../issues/6) | [M5 evaluation memo index](../milestones/M5_D5_Model_Evaluation/03_DELIVERABLES/README.md) |

D1–D5 are completed. Documented data-vintage, reproducibility and evaluation limitations remain visible as controls for D6; completion of D5 is not production approval.

## In Progress

| Work item | Record | Current focus |
|---|---|---|
| M6 / D6 — Deployment and Monitoring | [Issue #5](../issues/5) | Integrate D5-evaluated model, API/UI, refresh, testing, data health, logging and monitoring |

## Todo

| Work item | Record | Planned output |
|---|---|---|
| M7 / D7 — Final Communication | [Issue #7](../issues/7) | Final report, model card, presentation, speaker notes and demo |

## Workflow

M1 Charter → M2 Data Audit → M3 EBITDA EDA → M4 Model Training → M5 Evaluation → M6 Deployment/Monitoring → M7 Final Communication.

## Board rules

1. The GitHub Project Status field controls the visible columns; issue open/closed state is separate.
2. D1–D5 are Done. M6 / D6 is the active development milestone. M7 / D7 remains Todo.
3. D5's submitted memo records a seven-quarter holdout (2024 Q3–2026 Q1), Seasonal Naive validation MAE 7.47 pp and test MAE/RMSE/MASE 3.95/4.71/0.24.
4. D5 corrects the D4 draft's 2026 Q3 Seasonal Naive forecast to 26.11%; the earlier 29.93% value is retained only as historical draft evidence.
5. D4-v1 assignment evidence is EBITDA-margin modelling; legacy structured PAT-margin experiment metrics must remain separate.
6. A deliverable status does not imply binary repository upload. Verify the exact file path before claiming an artifact is committed.
7. Keep README, this workflow, milestone register and issue bodies synchronized.
