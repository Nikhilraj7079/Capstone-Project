# M5 — Working Files

## Current model-training notebook

| File | Description | Link |
|---|---|---|
| `ML_Model_Training.ipynb` | Latest uploaded notebook, replacing the earlier notebook in this folder. Compares SARIMAX with feature-based ML models and statistical benchmarks, reports validation and holdout metrics, plots comparisons, refits SARIMAX and saves the model artifact. | [Open current notebook](ML_Model_Training.ipynb) |
| `ml_model_training(2).py` | Previously received Python training/evaluation script, retained as a separate source file. | [Open Python file](ml_model_training%282%29.py) |

The current notebook contains the uploaded `ML_Model_Training(7).ipynb` content, stored under the stable repository name `ML_Model_Training.ipynb`. The earlier notebook content has been replaced at that path.

## Current model decision and comparison

The latest notebook explicitly designates **SARIMAX as the final project model**. It has the lowest validation MAE in the saved comparison (4.953 pp). On the seven-quarter holdout, however, Seasonal Naive has lower error. Both results are shown below exactly as saved in the notebook.

### Validation results

| Role | Model | MAE (pp) | RMSE (pp) | MASE |
|---|---|---:|---:|---:|
| **Final model** | **SARIMAX** | **4.953** | **6.307** | **0.297** |
| Comparator | Seasonal Naive | 7.470 | 8.187 | 0.448 |
| Comparator | Lasso | 10.074 | 10.978 | 0.604 |
| Comparator | Elastic Net | 13.264 | 14.069 | 0.796 |
| Comparator | Ridge | 13.278 | 14.064 | 0.796 |
| Comparator | Gradient Boosting | 14.795 | 15.988 | 0.887 |
| Comparator | Random Forest | 16.635 | 17.735 | 0.998 |
| Comparator | Historical Mean | 16.876 | 17.931 | 1.012 |
| Comparator | ETS | 19.370 | 20.358 | 1.162 |

### Holdout results

| Role | Model | MAE (pp) | RMSE (pp) | MASE |
|---|---|---:|---:|---:|
| **Designated final model** | **SARIMAX** | **14.197** | **15.193** | **0.851** |
| Best holdout comparator | Seasonal Naive | 3.948 | 4.714 | 0.237 |
| Comparator | ETS | 6.612 | 6.973 | 0.397 |
| Comparator | Random Forest | 7.188 | 7.896 | 0.431 |
| Comparator | Gradient Boosting | 8.207 | 8.841 | 0.492 |
| Comparator | Elastic Net | 11.562 | 12.334 | 0.693 |
| Comparator | Ridge | 12.612 | 13.527 | 0.756 |
| Comparator | Lasso | 13.752 | 14.881 | 0.825 |
| Comparator | Historical Mean | 14.853 | 16.083 | 0.891 |

**Interpretation:** SARIMAX is the validation leader and designated final model in the latest notebook. Seasonal Naive is the best model on the saved holdout results. The holdout contains only seven observations; the difference is an important model-risk signal and should be investigated with rolling-origin evaluation before production reliance.

## Forecast output and historical D5 memorandum

- Latest notebook SARIMAX forecast output: **21.75%** next-quarter EBITDA Margin.
- Earlier D5 memorandum: **26.11%** 2026 Q3 forecast from Seasonal Naive. Retained as historical submitted-memorandum result, not the current notebook forecast.
- Earlier D4 draft: 29.93%, recorded by D5 as a prior alignment error.

Do not combine these values. Use 21.75% only when describing the saved latest-notebook output. Re-run against the reconciled source workbook before presenting a current operational forecast.

## D5 evaluation scope
The notebook uses a chronological 60/20/20 split and displays validation and holdout comparisons. The D5 memorandum describes a locked seven-quarter holdout (2024 Q3–2026 Q1). Neither artifact claims a rolling-origin backtest.

## Reproduction requirements
1. Place the exact `EDA ANALYSIS.xlsx` source workbook in the notebook working directory (or Colab `/content/`).
2. Use worksheet `Sheet1` with the required columns: EBITDA Margin, USD/INR quarterly mean, monthly oil-benchmark quarterly mean, CPI quarterly mean and WPI quarterly mean.
3. Record the workbook SHA-256 and Python/package versions.
4. Run from a clean clone and compare the new run with the saved notebook outputs.
5. Verify that the latest-quarter macroeconomic inputs are available at the forecast origin.

**Reproducibility caution:** The exact source workbook vintage is not pinned in this repository. The notebook should not be treated as a clean reproduction until the source workbook is reconciled.
