# D4-v1 — Run Instructions

## 1. Environment
Use Python 3.10 or newer. Create and activate a virtual environment:

- Windows: `py -3.10 -m venv .venv`, then `.venv\\Scripts\\activate`
- macOS/Linux: `python3 -m venv .venv`, then `source .venv/bin/activate`

Install dependencies:

```bash
pip install -r requirements-d4-v1.txt
```

XGBoost is optional; the notebook includes it only if the package is available.

## 2. Input workbook
Place the exact approved workbook named `EDA ANALYSIS.xlsx` beside the notebook (or under `/mnt/data` / Colab `/content`) and ensure it contains `Sheet1` with at least:
- `EBITDA Margin`
- `USD INR (Quarterly Mean)`
- `Oil benchmark(MONTHLY) (Quarterly Mean)`
- `CPI inflation (Quarterly Mean)`
- `WPI inflation (Quarterly Mean)`

The original source workbook version and SHA-256 were not embedded in the submitted notebook. Do not substitute a different quarterly file without checking its headers, values and monthly-oil field.

## 3. Notebook execution
Open `ML_Model_Training(1).ipynb` in Jupyter or Colab and run cells in order. The submitted copy has saved outputs but does not contain a standalone imports/setup cell or execution counts. Before a clean run, add/run the imports below in the first code cell:

```python
import os, sys, pickle, warnings, hashlib, platform
from datetime import datetime, timezone
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from IPython.display import display
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import Ridge, Lasso, ElasticNet
from sklearn.ensemble import RandomForestRegressor, GradientBoostingRegressor
from sklearn.metrics import mean_absolute_error, mean_squared_error
from statsmodels.tsa.holtwinters import ExponentialSmoothing
try:
    from xgboost import XGBRegressor
    XGBOOST_AVAILABLE = True
except Exception:
    XGBOOST_AVAILABLE = False
    XGBRegressor = None
np.random.seed(42)
warnings.filterwarnings("ignore")
```

After loading the workbook, record the run timestamp (UTC), workbook SHA-256, Python version and `pip freeze`. The original notebook uses `random_state=42` for Random Forest, Gradient Boosting and XGBoost; it does not set a global seed.

## 4. Expected outputs
The saved assignment result uses 20 train / 7 validation / 7 test rows. Seasonal Naive wins on validation MAE 7.470. Saved holdout MAE/RMSE/MASE are 3.948 / 4.714 / 0.237. The notebook saves `best_ebitda_model.pkl` and prints a point forecast. Check forecast cutoff availability before treating it as usable.

## 5. Reproducibility checklist
For future runs, record the UTC execution date, input filename and SHA-256, quarter coverage, exact features, parameters, random seeds, package versions, split row boundaries and all metrics in `experiment_log_d4-v1.csv`. Do not call the PDF-preparation date the model-run date.
