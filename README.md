# DSA 210 — Personalized Sleep Quality Prediction

**Author:** Deniz Elbek
**Term:** Spring 2026  
**Course:** DSA 210 Introduction to Data Science

---

## Project Overview

This project investigates how sleep metrics, lifestyle habits, and environmental conditions predict two personal outcomes: morning feel rating (how rested one feels upon waking) and daily productivity rating using 45 consecutive nights of self-collected data. The goal is to build a dual-target model that jointly predicts a nightly sleep score (morning feel rating) and the following day's productivity rating, and to identify the full set of personal conditions — including sleep duration, timing, caffeine intake, alcohol consumption, meal timing, screen time, and physical activity — that simultaneously maximize both outcomes.

---

## Repository Structure

```
├── notebooks/
│   └── eda.ipynb               # Milestone 1: EDA & hypothesis tests
├── requirements.txt            # Python dependencies
├── .gitignore                  # Excludes data folder (private health data)
└── README.md
```

> **Note on raw data:** The entire `data/` folder is excluded via `.gitignore` as it contains private health information (Apple Health export, self-log spreadsheet, and featurized dataset). The original files can be shown upon request during final evaluation.

---

## Data Sources

| Source | Features | Collection Method |
|---|---|---|
| Apple Watch (Apple Health XML) | Sleep stages, HRV, SpO₂, HR, steps, calories, exercise | Exported via Health app |
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
| 14 Apr 2026 | EDA & hypothesis tests (preliminary, ~14 days data) | ✅ Done |
| 5 May 2026 | ML models applied | 🔲 Pending |
| 18 May 2026 | Final report & code | 🔲 Pending |

---

## How to Reproduce

```bash
# Clone the repository
git clone git@github.com:delbek/dsa_210.git
cd dsa_210

# Install dependencies
pip install -r requirements.txt

# Launch notebooks
jupyter notebook notebooks/eda.ipynb
```

---

## Known Limitations (Milestone 1)

- **Sample size:** Only ~13 nights of data available at this milestone (April 1–14, excluding April 10 where the Watch was not worn). Full 45-night dataset will be available by the ML submission.
- **Missing physiological metrics:** HRV, SpO₂, and resting heart rate are unavailable for April 1–5 as the Apple Watch requires a calibration period before logging these metrics.
- **Self-log reliability:** Some entries may contain minor logging inaccuracies due to the self-reported nature of the data. This is documented as a limitation.
- **External noise confound:** Elevated awake-time readings on several nights are attributable to environmental disturbance (roommate snoring) rather than controllable lifestyle factors. This is visible as a confound in the awake_min feature.
- **No screen time data yet:** Apple Screen Time export integration is planned for the final submission.
