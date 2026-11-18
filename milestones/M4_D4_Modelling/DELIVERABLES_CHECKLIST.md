# M4 / D4 — EBITDA Margin Modelling Checklist

**Status:** D4-v1 assignment report/notebook received; clean-run reproducibility and broader M4 exit gate remain open.

## D4-v1 assignment submission
- [x] Five-page report received and checked: problem type, target, model choice, validation design, results and limitations.
- [x] Submitted notebook received with saved validation/test outputs.
- [x] Nine model approaches compared; Seasonal Naive selected on validation MAE.
- [x] Experiment log records validation runs, parameters, features, seeds and available test metrics.
- [x] Report clearly labels the reconstructed all-model test metrics.

## Reproducibility
- [ ] Commit and pin the exact `EDA ANALYSIS.xlsx` input workbook plus SHA-256.
- [ ] Clean-run notebook with imports/setup cell and record UTC run date.
- [ ] Save exact Python/package environment (`pip freeze`) and input fingerprint.
- [x] Requirements and run instructions are present.
- [ ] Verify current-quarter input availability at the forecast cutoff and recheck the printed 29.93 point forecast.
- [ ] Add new clean-run metrics and data hash to the experiment log.

## Broader M4 exit
- [ ] Reconcile the D4-v1 assignment dataset with the M2/M3 approved EBITDA source lineage.
- [ ] Preserve target quarter, split boundaries and feature timing in the model manifest.
- [ ] Pass data/target-construction tests and hand off the selected baseline/candidate to M5 rolling-origin evaluation.

## Legacy evidence separation
- [x] The older structured PAT-margin experiment remains labelled as legacy and is not mixed with this EBITDA assignment.
