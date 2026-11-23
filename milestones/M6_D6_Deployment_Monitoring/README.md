# M6 / D6 — Deployment and Monitoring

**Status:** IN PROGRESS — ACTIVE DEVELOPMENT

## Brief
Integrate the D5-evaluated forecasting model into a tested API and user interface, with controlled market-data refresh and ongoing data/model monitoring. Existing backend/frontend/connectors provide the starting scaffold; D6 is active and is not complete until end-to-end integration is tested.

## Inputs and data
- D5-approved model artefact and model card.
- Frozen preprocessing and feature schema from M4/M5.
- M2 source register and connector contracts for USD/INR, CPI, WPI and Brent proxies.
- No duplicate training dataset is created in this milestone.

## Workflow
1. Receive the D5 approval and model contract.
2. Integrate model and preprocessing into API routes.
3. Align live feature transformation and update cadence with training.
4. Validate request/response schemas and error cases.
5. Connect the HTML frontend to the API.
6. Protect secrets and document deployment configuration.
7. Log timestamp, input vintage, model version and predictions.
8. Monitor freshness, missingness, source errors, drift and prediction errors once actuals arrive.
9. Run a reproducible end-to-end demo and capture evidence.

## Planned deliverables
Architecture and API contract; integrated prediction service; API/UI tests; refresh/store configuration; monitoring plan and thresholds; deployment runbook; demo evidence.

## Folder map
01_INPUTS approved model/features; 02_WORKING implementation/tests; 03_DELIVERABLES deployable app/runbook; 04_EVIDENCE test reports/logs/screens; 05_REFERENCES deployment/security references.

## Current phase status

D1–D5 are complete. D6 is the active implementation phase. Work must preserve the D5 model choice, evaluation metrics, feature definitions and forecast-origin limitations. Any model change or retraining must be separately documented and evaluated rather than silently substituted during deployment.

## Exit gate
End-to-end application works with D5-approved model, secure configuration, tests and monitoring plan.
