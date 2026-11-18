# M4 / D4 — Modelling and Forecasting

**Status:** IN PROGRESS — D4 assignment report and notebook received; repository binary upload verification pending.

## Brief
Develop and document reproducible forecasting baselines and candidate models for IndiGo's next-quarter **EBITDA Margin**. This milestone includes target construction, feature engineering, a predeclared chronological split, model comparison, experiment tracking and a modelling report. The D4 assignment checkpoint is documented separately from the structured legacy PAT-margin experiment also retained in this folder.

## Current D4-v1 assignment artifacts
- **Five-page report:** [ANCP_T##_D4_Expanded_Model_Training_Report.pdf](03_DELIVERABLES/README.md). It documents the business question, target, problem type, features, train/validation/test split, model-family rationale, validation ranking, holdout performance and limitations.
- **Submitted notebook:** [ML_Model_Training(1).ipynb](02_WORKING/README.md). This is the notebook referenced by the report and contains the saved validation/test outputs.
- **Experiment log:** [experiment_log_d4-v1.csv](04_EVIDENCE/experiment_log_d4-v1.csv) records the nine validation candidates, model parameters, seeds and available test metrics. Candidate test scores reconstructed from chart code are explicitly distinguished from saved notebook tables.
- **Run and environment instructions:** [RUN_D4_v1.md](04_EVIDENCE/RUN_D4_v1.md) and [requirements-d4-v1.txt](04_EVIDENCE/requirements-d4-v1.txt).
- **Existing structured M4 pipeline:** [source code](src/d4_train.py), [tests](tests/test_d4_train.py) and [machine-readable experiment outputs](experiments/).

## D4-v1 assignment result
The notebook treats the task as supervised one-quarter-ahead time-series regression. It retains 38 raw quarterly observations and 34 usable supervised rows with 10 features. The split is chronological and fixed at 20 train / 7 validation / 7 test rows (60% / 20% / 20%); there is no random shuffle.

Nine approaches are compared: Seasonal Naive, Historical Mean, Ridge, Lasso, Elastic Net, Random Forest, Gradient Boosting, XGBoost and ETS. Seasonal Naive records the lowest validation MAE (7.470) and is selected. Its saved test metrics are MAE 3.948, RMSE 4.714 and MASE 0.237 on the seven-row holdout. The report's additional all-model test metrics are reconstructed from the notebook's chart code and are labelled as reconstructed in the report and experiment log.

## Important reproducibility caveats
- The submitted notebook expects an input workbook named `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, with the monthly oil benchmark quarterly-mean field. That exact workbook version/hash is not embedded in the notebook or supplied with this upload.
- The original notebook has saved outputs but does not include an imports/setup cell or execution counts. The saved outputs can be reviewed; a clean run requires the source workbook and the imports listed in the run instructions.
- Original model execution timestamp, input workbook hash and original package lockfile were not captured. The experiment log does not misstate the report-preparation date as the actual run date.
- The notebook assumes current-quarter financial and macro inputs are available at the forecast cutoff. If they were not public by that date, predictors must be lagged or forecast separately.
- The report prints a next-quarter point forecast of 29.93. This is an estimate only; its current-quarter information-availability assumption and seasonal-lag alignment must be rechecked against the exact input workbook before operational use.

## Data used
The D4-v1 assignment notebook's input is distinct from the structured M4 pipeline snapshot. Do not substitute `data/Final_Quarterly_Data(1).xlsx` or the M3 CSV into the assignment notebook without mapping the exact expected headers and reconciling source values. See [D4 inputs](01_INPUTS/README.md) and [D4 evidence](04_EVIDENCE/README.md).

## Folder map
- `01_INPUTS/` — approved datasets and input documentation.
- `02_WORKING/` — assignment notebook, pipeline notebooks and working code.
- `03_DELIVERABLES/` — submission-ready report.
- `04_EVIDENCE/` — experiment log, environment and run instructions.
- `05_REFERENCES/` — source/method reference index.
- `data/`, `experiments/`, `src/`, `tests/` — structured M4 data, metrics, scripts and tests.

## Legacy experiment separation
The older top-level [README_D4.md](../../README_D4.md) and existing structured records in `experiments/` describe a separate PAT-margin experiment. Those metrics are legacy evidence and are not results from this EBITDA Margin assignment notebook. Keep the target, dataset and split labels separate in all future reporting.

## Exit criteria
The submitted five-page report, assignment notebook and experiment log are the D4 assignment evidence. M4 remains in progress until the exact source workbook is pinned, the notebook can be clean-run with recorded environment metadata, the feature-availability assumptions are validated, and the broader active pipeline passes its data, tests and handoff gates.
