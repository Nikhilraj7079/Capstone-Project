# M5 — Deliverables

## D5-v1 — Executive Decision Memorandum

- **Received filename:** `ANCP_Team-K_D5_v1.pdf`
- **Pages:** 4
- **Memo date:** 15 November 2026
- **Title:** Executive Decision Memorandum — D5 Model Evaluation & Validation, Next-Quarter EBITDA Margin Forecast.
- **SHA-256:** `9055c5e0e35a3dd7e7ea88e36e03929f8d00a131af0d7808ad36fa787cd74c82`
- **GitHub binary status:** pending upload/verification; this README is an index, not the PDF itself.

The memorandum covers:
1. Executive model decision and forecast summary.
2. Chronological validation design and leakage audit.
3. Validation and holdout model comparison.
4. Business cost of over- and under-prediction.
5. Error analysis, regime sensitivity and limitations.
6. Corrected 2026 Q3 Seasonal Naive point forecast and empirical risk band.

**Decision:** Seasonal Naive is the primary one-quarter-ahead benchmark; ETS and Gradient Boosting are secondary cross-checks.

**Selected-model metrics:** validation MAE 7.47 pp; test MAE 3.95 pp; test RMSE 4.71 pp; test MASE 0.24.

**Corrected forecast:** 26.11% for 2026 Q3. The memo gives an empirical ±9.24 pp band (16.9%–35.4%); this is a risk buffer, not a model-native confidence interval.

See the [M5 overview](../README.md) for the full data record, results and limitations.
