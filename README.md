# DSA 210 — Personalized Well-being Prediction from Sleep & Lifestyle Data

**Author:** Deniz Elbek
**Term:** Spring 2026
**Course:** DSA 210 Introduction to Data Science

---

## Project Overview

This project investigates how sleep metrics, lifestyle habits, and environmental conditions predict two personal outcomes: morning feel rating (how rested one feels upon waking) and daily productivity rating. Data was collected over 34 nights (April 1 – May 4, 2026) using an Apple Watch, a daily self-log, and external API enrichment. A dual-target model jointly predicts both outcomes and identifies the full set of personal conditions that simultaneously maximize them.

---

## Repository Structure

```
├── notebooks/
│   ├── eda.ipynb               # Milestone 1: EDA & hypothesis tests
│   ├── eda_run.ipynb           # Milestone 1: executed with outputs
│   ├── ml_models.ipynb         # Milestone 2: ML models & SHAP analysis
│   └── ml_models_run.ipynb     # Milestone 2: executed with outputs
├── requirements.txt            # Python dependencies
├── .gitignore                  # Excludes data folder (private health data)
└── README.md
```

> **Note on raw data:** The entire `data/` folder is excluded via `.gitignore` as it contains private health information (Apple Health export, self-log spreadsheet, and featurized dataset). The original files can be shown upon request during final evaluation.

---

## Data Sources

| Source | Features | Collection Method |
|---|---|---|
| Apple Watch (Apple Health XML) | Sleep stages, HRV, SpO₂, HR, steps, calories, exercise, Apple sleep score | Exported via Health app |
| Apple Screen Time | Pre-sleep screen usage | Apple Screen Time export |
| Daily Self-Log | Morning feel (1–10), productivity (1–10), caffeine, alcohol, meal timing | Manual log filled each morning/evening |
| OpenWeatherMap API | Temperature, humidity, barometric pressure | Automatic API retrieval |
| Sunrise/Sunset API | Sunset time, bedtime-to-sunset offset | Automatic API retrieval |

---

## Milestones

| Date | Deliverable | Status |
|---|---|---|
| 17 Mar 2026 | GitHub repo created | ✅ Done |
| 31 Mar 2026 | Project proposal submitted | ✅ Done |
| 14 Apr 2026 | EDA & hypothesis tests (preliminary, ~13 nights) | ✅ Done |
| 5 May 2026 | ML models applied (full dataset, 28 complete nights) | ✅ Done |
| 18 May 2026 | Final report & code | 🔲 Pending |

---

## How to Reproduce

```bash
# Clone the repository
git clone git@github.com:delbek/dsa_210.git
cd dsa_210

# Install dependencies
pip install -r requirements.txt

# Run notebooks
jupyter notebook notebooks/eda.ipynb
jupyter notebook notebooks/ml_models.ipynb
```

---

## Known Limitations

- **Sample size (n=28 complete nights):** 6 nights excluded due to Apple Watch not being worn. Full generalizability is limited.
- **Missing physiological metrics:** HRV, SpO₂, and resting HR unavailable for first 5 nights (Apple Watch calibration period); handled via median imputation.
- **Self-log reliability:** Self-reported ratings may carry minor inaccuracies; documented as a limitation.
- **Environmental confound:** Elevated awake-time on several nights attributable to roommate snoring rather than controllable lifestyle factors.
- **No screen time data:** Apple Screen Time extraction planned for final report.
