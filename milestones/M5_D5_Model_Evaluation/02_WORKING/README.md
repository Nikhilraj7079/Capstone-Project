# M5 — Working Files

## D5 model training code

The Python source and Jupyter notebook are now committed in this folder.

| File | Description | Link |
|---|---|---|
| `ML_Model_Training.ipynb` | Runnable Jupyter notebook version of the received Python workflow, with dependency/import setup and input instructions | [Open notebook](ML_Model_Training.ipynb) |
| `ml_model_training(2).py` | Original received Python training/evaluation script | [Open Python file](ml_model_training%282%29.py) |

**Notebook provenance:** The committed notebook is assembled from the received `ml_model_training(2).py` source and includes a setup cell for required imports. It is not represented as the exact original `ML_Model_Training(6).ipynb` upload. The original notebook binary was not available in the files attached to this update.

## D5 evaluation scope
The D5 memorandum evaluates a locked chronological holdout of seven target quarters (2024 Q3–2026 Q1). It does not claim a rolling-origin backtest. Rolling-origin evaluation remains a recommended extension.

## Reproduction requirements
1. Place the exact `EDA ANALYSIS.xlsx` source workbook in the notebook working directory (or Colab `/content/`).
2. Use worksheet `Sheet1` with the required columns documented in [M5 inputs](../01_INPUTS/README.md).
3. Record the workbook SHA-256 and Python/package versions.
4. Run from a clean clone and confirm 38 raw observations, 34 supervised rows, 10 features and the expected chronological split.
5. Verify Seasonal Naive `shift(3)` alignment and compare the results with the D5 memorandum.
6. Preserve the distinction between saved test metrics and candidate metrics reconstructed from chart-generation code.

**Reproducibility caution:** The exact source workbook vintage is not yet pinned. The notebook should not be treated as a clean reproduction of D5 report results until the source workbook is reconciled.
