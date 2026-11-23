# M5 — Evaluation Evidence

## Evidence from submitted D5 memorandum
- Locked chronological holdout: 2024 Q3–2026 Q1, seven quarters.
- Validation winner: Seasonal Naive, validation MAE 7.47 pp.
- Test metrics: MAE 3.95 pp, RMSE 4.71 pp, MASE 0.24.
- Leakage checklist: chronological split; causal target/lag alignment; training-only scaler; training-only MASE scale; validation-only selection; forecast-origin availability conditional.
- Error analysis includes over/under-forecast examples and quarter/regime comparisons.
- Empirical forecast-risk buffer: ±9.24 pp, approximately 16.9%–35.4%.
- Business cost framing: approximately ₹180–200 crore per EBITDA-margin percentage point at quarterly revenue of ₹18,000–20,000 crore, as stated in the memo.

## Metric provenance
The D5 report states that the saved notebook test-results table includes Seasonal Naive and Historical Mean. Test scores for ETS, Gradient Boosting, XGBoost, Random Forest and regularised linear models are reconstructed from the chart-generation code. Preserve this distinction whenever reproducing the table.

## Leakage audit summary
| Check | D5 result |
|---|---|
| Chronological split, no shuffling | PASS |
| Causal feature/target alignment | PASS |
| Scaler/preprocessing isolation | PASS |
| MASE denominator uses training targets | PASS |
| Test set not used for model selection | PASS |
| Foundation-model/LLM memorisation | N/A |
| Forecast-origin publication cutoff | PASS, conditional on current-quarter data being final and available |

## Known limitations
- Seven-quarter test sample; rankings remain provisional.
- Seasonal Naive is insensitive to macroeconomic shocks.
- Oil is a global crude benchmark proxy, not IndiGo's actual ATF landed cost.
- Empirical band is a risk buffer, not a model-native interval.
- Exact workbook hash and original execution environment were not captured.
- Rolling-origin backtesting remains recommended before production deployment.

The D5 memorandum file was received but its binary GitHub upload is pending. This evidence index is not a substitute for the PDF.
