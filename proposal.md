# Project Proposal — Personalized Sleep Quality Prediction

## DSA 210 Introduction to Data Science | Spring 2026

### Overview

This project investigates the relationship between lifestyle habits, environmental
conditions, and personal sleep quality using 45 consecutive nights of self-collected
data. The goal is twofold: to build a dual-target model that jointly predicts a
nightly sleep score and the following day's productivity, and to identify the full
set of personal conditions — including sleep duration, timing, caffeine intake, alcohol
consumption, meal timing, screen time, and physical activity — that simultaneously
maximize both outcomes.

### Data Sources

**Apple Watch & Apple Ecosystem** — exported via Apple Health XML and Screen Time:
sleep stages (Light/Deep/REM/Awake), sleep duration, bedtime/wake time, Apple's
proprietary nightly sleep score (objective sensor-derived quality index), resting
heart rate, HRV, SpO₂, respiratory rate, daily steps, active calories, exercise
minutes, and total/pre-sleep screen time across all Apple devices.

**Daily Self-Log** — filled each morning and evening throughout the 45-day period:
morning feel rating (1–10, first target), daily productivity rating (1–10, second
target), caffeine count and time of last intake, alcohol consumption, nap duration,
and last meal time before bed.

**External API Enrichment** — retrieved automatically via OpenWeatherMap and a
sunrise/sunset API matched by date and location: nighttime temperature, humidity,
barometric pressure, and sunset time (to derive natural light exposure and
bedtime-to-sunset offset).

### Analysis Plan

EDA and correlation analysis will be followed by hypothesis testing using
non-parametric methods (Spearman correlation, Mann–Whitney U) suited to small samples.
A dual-target predictive model (morning feel + daily productivity) will be built
ranging from linear regression to Random Forest/XGBoost with SHAP interpretation,
evaluated via Leave-One-Out Cross-Validation (LOOCV) given n = 45. Including Apple's
algorithmic sleep score as a feature allows the model to quantify the gap between
objective sensor-based quality and subjective personal outcomes — itself a meaningful
finding. SHAP feature importance outputs will then be used to derive a fully
personalized daily routine recommendation — covering not only the optimal sleep
duration and timing window but also the lifestyle conditions (caffeine cutoff time,
alcohol, last meal timing, screen time, physical activity, and nap habits) that
jointly maximize both target variables.

### Dataset Characteristics

- **Samples:** 45 nights (April 1 – May 15, 2026)
- **Features:** ~23 (sensor + Apple sleep score + self-log + environmental)
- **Targets:** Morning feel rating (1–10) and daily productivity rating (1–10);
  both also used to derive a composite joint score for optimization