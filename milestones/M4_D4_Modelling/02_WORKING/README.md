# M4 — Working Files

## Latest submitted D4 assignment notebook
- **Received file:** `ML_Model_Training(5).ipynb` — received 23-Nov-2026; binary upload to this GitHub folder is pending.
- The notebook defines next-quarter EBITDA Margin as the target, uses ten engineered features, and applies a chronological 60/20/20 split (20/7/7 rows).
- It compares baseline, linear, tree-based and ETS approaches and selects the lowest validation-MAE model.
- It saves a deployment artifact named `best_ebitda_model.pkl` when run successfully.

## D4 report
The expanded five-page D4 report is indexed in [03_DELIVERABLES](../03_DELIVERABLES/README.md). The D5 memo provides a subsequent forecast-alignment correction; retain the submitted D4 report as historical evidence.

## Reproducibility status
The notebook expects `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, with the monthly oil benchmark quarterly-mean column. The exact workbook hash/version and original execution environment are not recorded. Saved outputs can be reviewed, but a clean rerun is pending the exact workbook and environment capture.

## Existing structured pipeline
- `src/d4_train.py`
- `notebooks/D4_modeling_experiment.ipynb`
- `tests/test_d4_train.py`
- `requirements-d4.txt`

The structured pipeline's legacy PAT-margin experiment is separate from the current EBITDA-margin assignment and must not be mixed with D4-v1 results.
