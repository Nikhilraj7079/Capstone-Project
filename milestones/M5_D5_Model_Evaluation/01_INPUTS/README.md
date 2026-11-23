# M5 — Inputs and Data Contract

## Required upstream inputs
1. D4 next-quarter EBITDA-margin modelling definition and feature schema.
2. D4 assignment notebook and model settings.
3. Exact quarterly input workbook used for D4/D5 evaluation (the memo says 38 raw quarters, 34 supervised rows).
4. M2 source register and point-in-time availability rules.
5. M3 EDA handoff and known data-quality caveats.

## Submitted D5 data vintage description
The D5 memorandum records 38 raw quarterly observations from 2017 Q1 to 2026 Q2 and 34 usable supervised rows. It uses ten engineered features and a chronological split of 20 train / 7 validation / 7 test. The locked test targets run from 2024 Q3 to 2026 Q1.

**Important:** the exact source workbook hash/version and original model execution environment were not captured in the submitted D5 memo. The D4 notebook expects `EDA ANALYSIS.xlsx`, worksheet `Sheet1`, with the monthly oil benchmark quarterly-mean field. Do not label the D5 vintage fully reproducible until that exact workbook is pinned and hashed.

## Evaluation contract
- Target: next-quarter EBITDA Margin (%).
- Forecast horizon: one quarter.
- Preserve chronology; do not shuffle.
- Model selection uses validation MAE only.
- The final test block is used for holdout evaluation, not model selection.
- Inputs must be available at the forecast origin. If current-quarter values are not yet final, shift or forecast them separately.
- Global Brent/oil proxy is not IndiGo's actual ATF cost.

## Source ownership
M2 owns original source lineage; M3 owns EDA panel and exploratory outputs; M4 owns the modelling data/features; M5 owns evaluation predictions/errors and evaluation evidence. Do not duplicate or silently replace upstream workbooks.
