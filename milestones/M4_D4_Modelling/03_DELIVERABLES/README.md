# M4 — Deliverables

## D4-v1 — Expanded Model Training Report

**Submitted file:** `ANCP_T##_D4_Expanded_Model_Training_Report.pdf`  
**Page limit:** 5 pages (verified: 5 pages).  
**Project target:** next-quarter EBITDA Margin.

The report covers:
1. Business problem, target and supervised one-quarter-ahead regression type.
2. 38 raw quarterly observations, 34 usable supervised rows and the ten engineered features.
3. A declared chronological 60/20/20 split (20 train, 7 validation, 7 test).
4. Rationale for baseline, regularised-linear, tree-ensemble and ETS model families.
5. Validation ranking, final holdout results, actual-versus-predicted test values, interpretation and limitations.

Seasonal Naive is selected on validation MAE 7.470. Its saved test MAE/RMSE/MASE are 3.948 / 4.714 / 0.237. The report explicitly distinguishes reconstructed all-model test metrics from values saved directly by the notebook.

## Other modelling evidence
- Assignment notebook: [02_WORKING](../02_WORKING/README.md).
- Experiment log, run instructions and requirements: [04_EVIDENCE](../04_EVIDENCE/README.md).
- Structured M4 pipeline outputs: [experiments](../experiments/).

**Milestone status remains IN PROGRESS.** The five-page assignment report does not by itself close M4 or the later M5 evaluation work.
