# Burnout Forecast (Local-First)

Burnout Forecast is a **local-first** tool that estimates when I’m trending toward burnout using personal behavior signals (sleep, coding workload, focus patterns, and context switching). It generates a **daily risk score (0–100)** with **human-readable explanations** (“what drove the score”), not just a number.

**Privacy by default:** data stays on-device. A realistic **demo dataset** is included for interview viewing (no personal logs committed).

---

## Why this exists
Most productivity tools reward grinding. This does the opposite: it looks for early signs of overextension and recommends recovery before things crash.

---

## What it does
- Ingests behavior signals (manual logs or import)
- Builds interpretable features like:
  - late-night work streaks
  - workload ramp rate (sudden increases)
  - session volatility (erratic schedule)
  - context-switch frequency
  - sleep deficit streaks
- Outputs:
  - daily burnout risk score (0–100)
  - top contributing factors (“receipts”)
  - suggested intervention (e.g., lighter workload, earlier stop time)
- Tracks trends over time so patterns are visible

---

## Tech overview
- **Data layer:** CSV / JSON (upgrade path to SQLite)
- **Feature engineering:** rolling averages, streaks, deltas, variance
- **Modeling:** baseline rules → interpretable model (logistic regression / small tree)
- **Explanations:** top contributing features per prediction
- **Interface:** CLI and/or local dashboard

> This repo intentionally prioritizes **interpretability** over fancy ML.

---

## Privacy stance
- Default: local-only, no cloud sync
- No third-party analytics
- Demo dataset included (not real personal data)

---

## Pipeline (high level)
1. Collect daily logs (sleep, sessions, breaks, etc.)
2. Transform into features (rolling averages, streaks, changes)
3. Train on self-labeled burnout/low-energy days
4. Predict risk (today + optional tomorrow)
5. Explain drivers of the prediction
6. Visualize trends + interventions

---

## Demo mode
A demo dataset is included so the full pipeline works without exposing personal logs.

- Real logs: `data/private/` (gitignored)
- Demo logs: `data/demo/` (committed)

---

## Roadmap
- [ ] Data schema + import pipeline
- [ ] Baseline rule-based score + explanations
- [ ] Feature engineering v1
- [ ] Model v1 (interpretable) + comparison vs baseline
- [ ] CLI report output + saved JSON
- [ ] Minimal dashboard (local)
- [ ] Demo mode + screenshots
- [ ] Packaging: one-command run

---

## Success criteria
- Scores are stable (not noisy day-to-day)
- Explanations feel true (“yeah… that checks out”)
- Outputs suggest an actionable next step

---

## Non-goals
- Medical diagnosis or treatment
- “Optimization” that encourages overwork

---

## License
MIT (or keep Proprietary until you’re ready)


### Demo Mode

This repository includes a realistic demo dataset (`data/demo/`) so the
pipeline can be run without exposing personal data.

Real personal logs are stored locally and intentionally excluded from version control.
