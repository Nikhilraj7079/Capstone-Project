# M5 — Evaluation Evidence

## Evidence from D5-v1 memorandum

- Locked chronological holdout: 2024 Q3–2026 Q1, seven quarters.
- Validation winner: Seasonal Naive, validation MAE 7.47 pp.
- Test metrics: MAE 3.95 pp, RMSE 4.71 pp, MASE 0.24.
- Leakage checklist: chronological split; causal target/lag alignment; training-only scaler; training-only MASE scale; validation-only model selection; forecast-origin availability conditional.
- Error analysis includes over/under-forecast examples, regime comparisons and quarter-level residuals.
- Empirical forecast-risk buffer: ±9.24 pp, approximately 16.9%–35.4%; not a model-native prediction interval.
- Business-cost framing: approximately ₹180–200 crore per EBITDA-margin percentage point at quarterly revenue of ₹18,000–20,000 crore, as stated in the memo.

## Leakage audit
| Check | D5 result |
|---|---|
| Chronological split, no shuffling | PASS |
| Causal feature/target alignment | PASS |
| Scaler/preprocessing isolation | PASS |
| MASE denominator uses training targets | PASS |
| Test set not used for model selection | PASS |
| Foundation-model/LLM memorisation | N/A |
| Forecast-origin publication cutoff | PASS, conditional on current-quarter data being final and available |

## Metric provenance
The memo states that Seasonal Naive and Historical Mean test results reproduce the saved notebook test-results table. Test scores for ETS, Gradient Boosting, XGBoost, Random Forest and regularised linear models are reconstructed from chart-generation code (Cell 10 reconstruction). Preserve this distinction in any downstream report or dashboard.

For the selected Seasonal Naive model, the memo reports a 95% t-based interval for mean absolute error of 1.38–6.52 pp based on seven test errors. The memo also cautions that its interval overlaps ETS and Gradient Boosting intervals, so the performance margin over those models is not statistically conclusive.

## Error and robustness findings
- Seasonal Naive MAE is reported as 2.42 pp on five stable high-margin quarters and 7.76 pp on two Q4 quarters.
- 2024 Q4 overprediction: 18.83% predicted versus 10.95% actual (+7.88 pp).
- 2025 Q4 underprediction: 10.95% predicted versus 18.59% actual (-7.64 pp).
- The 2020 Q4 -201% margin outlier in the 27-row refit window is identified as a source of distortion for linear-model intercepts.
- ±10% USD/INR or crude shocks do not change Seasonal Naive or ETS forecasts; these methods are not macro-sensitive scenario models.

## Received source artefacts
| File | SHA-256 | GitHub binary status |
|---|---|---|
| `ANCP_Team-K_D5_v1.pdf` | `9055c5e0e35a3dd7e7ea88e36e03929f8d00a131af0d7808ad36fa787cd74c82` | Pending upload/verification |
| `ML_Model_Training(6).ipynb` | `3e8a2b8a255450cddee32fe5d3bd26e1ac14dd6e4ed7b33f81e3406de7948310` | Pending upload/verification |
| `ml_model_training(2).py` | `31abe74c8db7d247780a35b83b95bf1bb546120e3b8a4b31b86766670b9bea4f` | Pending upload/verification |

## Limitations and next steps
- Seven-quarter test sample; rankings are provisional.
- Seasonal Naive is insensitive to macroeconomic shocks.
- Oil is a global crude benchmark proxy, not IndiGo's actual ATF landed cost.
- Exact source workbook hash and original execution environment are not captured.
- The notebook uses a static Excel extract; automated ingestion, schema validation and rolling-origin retraining are needed before production.
- Rolling-origin backtesting remains recommended before production deployment.

This evidence index documents the submitted evidence; it is not a substitute for the original PDF, notebook or script binaries.
