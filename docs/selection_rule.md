# AquaPulse — Pre-Dated State & Demo District Selection Rule

- **Date Locked:** November 21, 2026 (Committed prior to any data joining, model training, or result inspection)
- **Project:** AquaPulse (GenHacks 2026 — Healthcare & Environmental Track)
- **Purpose:** Prevent cherry-picking of states, districts, or evaluation windows.

---

## 1. State Selection Rule (Strictly ONE Indian State)
Candidate states to evaluate first: **Maharashtra, Karnataka, Tamil Nadu, and Kerala**.

The single target state will be selected **solely** based on public data completeness before any modeling occurs:
1. **Water Quality Coverage:** Highest number of active CPCB / India WRIS monitoring stations with valid latitude/longitude coordinates and multi-year monthly readings (turbidity, coliform, pH, dissolved oxygen).
2. **Health Surveillance Coverage:** Most complete multi-year IDSP / data.gov.in district-level outbreak logs for waterborne diseases (typhoid, acute diarrhoeal disease, cholera, hepatitis A).

*The single winning state will be locked by November 23, 2026, and documented in `docs/data_provenance.md`.*

---

## 2. Demo District Selection Rule
The primary district featured in the live demo will **not** be chosen based on model accuracy. It will be selected strictly by:
1. **Highest CPCB station density** (most valid monthly water quality readings per monsoon season).
2. **Documented historical outbreak activity** (clear presence of waterborne outbreak months in public IDSP records so the system can be tested on real events).

---

## 3. Non-Negotiable Scope & Anti-Leakage Rules
- **Granularity:** Strictly **district-month** level (never weekly, never interpolated).
- **Spatial Join:** Stations are mapped to districts using latitude/longitude and an official Indian district boundary file (`GeoPandas` spatial join)—never fragile string matching.
- **Data Integrity:** Real public data only. Synthetic data will never enter model training or headline evaluation scores.
- **Evaluation Split:** Strict chronological holdout on the **most recent monsoon season**, locked before hyperparameter tuning.
- **Uncertainty Honesty:** Districts below the minimum sample threshold are rendered in grey (`Insufficient Data`) rather than guessed.
