# M5 — Working Files

## Current model-training notebook


| File | Description | Link |
|---|---|---|
| `ML_Model_Training.ipynb` | Latest uploaded notebook, replacing the previous notebook in this folder. It compares SARIMAX with feature-based ML models and statistical benchmarks, reports validation and holdout metrics, plots model comparisons, refits SARIMAX and saves the model artifact. | [Open current notebook](ML_Model_Training.ipynb) |
| `ml_model_training(2).py` | Previously received Python training/evaluation script, retained as a separate source file. | [Open Python file](ml_model_training%282%29.py) |

The current notebook is the uploaded `ML_Model_Training(7).ipynb` content, stored under the stable repository name `ML_Model_Training.ipynb`. The earlier notebook content has been replaced at that path; there is no second “(7)” copy in this module.

## Important model-decision reconciliation

The new notebook explicitly designates **SARIMAX** as the final project model and its saved outputs show SARIMAX holdout MAE 14.197, RMSE 15.193 and MASE 0.851, while Seasonal Naive has lower holdout errors (MAE 3.948, RMSE 4.714 and MASE 0.237).

The submitted D5 evaluation memorandum, however, selects **Seasonal Naive** as the primary one-quarter-ahead benchmark and reports a corrected 2026 Q3 forecast of 26.11%. These are different model decisions. The notebook has been replaced as requested, but the D5 memorandum and its decision have not been silently rewritten. Confirm the project team's final model-selection decision before treating the notebook's SARIMAX designation as the approved D5 decision or using its forecast in the application.

## D5 evaluation scope
The D5 memorandum evaluates a locked chronological holdout of seven target quarters (2024 Q3–2026 Q1). The notebook uses a chronological 60/20/20 split and displays validation and holdout comparisons. It does not claim a rolling-origin backtest.

## Reproduction requirements
1. Place the exact `EDA ANALYSIS.xlsx` source workbook in the notebook working directory (or Colab `/content/`).
2. Use worksheet `Sheet1` with the required columns: EBITDA Margin, USD/INR quarterly mean, monthly oil-benchmark quarterly mean, CPI quarterly mean and WPI quarterly mean.
3. Record the workbook SHA-256 and Python/package versions.
4. Run from a clean clone and compare the new run with the saved notebook outputs and D5 memorandum.
5. Verify that the latest-quarter macroeconomic inputs are available at the forecast origin.
6. Preserve the distinction between the notebook's designated SARIMAX model and the D5 memorandum's Seasonal Naive decision until formally reconciled.

**Reproducibility caution:** The exact source workbook vintage is not pinned in this repository. The notebook should not be treated as a clean reproduction until the source workbook is reconciled.
