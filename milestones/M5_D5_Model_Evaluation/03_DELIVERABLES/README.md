# M5 — Deliverables

## D5-v1 — Executive Decision Memorandum

- **Received filename:** `ANCP_T___D5_v1 (1).pdf`
- **Canonical intended repository filename:** `ANCP_T##_D5_v1.pdf`
- **Pages:** 4
- **Memo date:** 15 November 2026
- **Repository binary status:** received; binary commit is pending.

The memorandum covers:
1. Executive model decision and forecast summary.
2. Chronological validation design and leakage audit.
3. Validation and holdout model comparison.
4. Business cost of over- and under-prediction.
5. Error analysis, regime sensitivity and limitations.
6. Corrected 2026 Q3 Seasonal Naive point forecast and empirical risk band.

**Decision:** Seasonal Naive is the primary one-quarter-ahead benchmark; ETS and Gradient Boosting are secondary cross-checks.

**Key metrics:** validation MAE 7.47 pp; test MAE 3.95 pp; test RMSE 4.71 pp; test MASE 0.24.

**Corrected forecast:** 26.11% for 2026 Q3, with an empirical ±9.24 pp band (16.9%–35.4%). The band is not a model-native confidence interval.

The report is a completed D5 submission. Its limitations and follow-up recommendations are recorded in the [M5 overview](../README.md).
