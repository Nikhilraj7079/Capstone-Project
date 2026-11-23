# M5 — References

## Primary project evidence
- D5-v1 Executive Decision Memorandum, dated 15-Nov-2026, received as `ANCP_T___D5_v1 (1).pdf`.
- D4 expanded model-training report and `ML_Model_Training(5).ipynb`, which provide the training workflow and feature definitions.
- [M4 modelling milestone](../../M4_D4_Modelling/README.md).
- [Project data governance](../../../data/README.md).

## Methodology references captured by the D5 submission
- Chronological time-series validation; no random row shuffling.
- Causal lag and target alignment for one-quarter-ahead prediction.
- Pipeline-isolated preprocessing and training-only MASE scaling.
- Holdout test separation from model selection.
- MAE, RMSE and MASE for forecast error reporting.
- Error-cost asymmetry and regime-specific error analysis.

External sources should be added only when the exact method, definition or data claim is used in the evaluation. Do not cite the crude benchmark as IndiGo ATF cost.
