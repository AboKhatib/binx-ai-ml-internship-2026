# Day 4 — Feature Engineering & Hyperparameter Tuning

## Overview

This notebook implements **Day 4 of Week 4** of the AI & Machine Learning internship.

The main goals were:

- Create engineered demographic features.
- Train a Random Forest baseline model.
- Tune hyperparameters using `GridSearchCV` with 5-fold stratified cross-validation.
- Compare the tuned model with the baseline.
- Analyze feature importance and tuning results.

The experiment uses the **2017 Census Ages dataset** to predict the `Governorate` of each locality based on demographic information.

---

## Dataset

- **586 localities**
- Original features: age and gender population groups
- Final feature matrix: **34 features**
- Target: `Governorate`

### Excluded Columns

- `Governorate_a` — excluded to avoid target leakage.
- `Locality` — identifier/name.
- `Year` — constant 2017 value.

---

## Feature Engineering

Four demographic features were created:

| Feature | Description |
|---|---|
| `total_population` | Total population of the locality |
| `youth_ratio` | Proportion of population aged 0–19 |
| `senior_ratio` | Proportion of population aged 60+ |
| `female_share` | Proportion of females |

### Feature Importance

The most important engineered feature was **`youth_ratio`** with an importance of **0.076567**.

| Feature | Importance |
|---|---:|
| `youth_ratio` | 0.076567 |
| `senior_ratio` | 0.057137 |
| `female_share` | 0.044162 |
| `total_population` | 0.025371 |

After validation:

- Rows: **586**
- Features: **34**
- Missing values: **0**

---

## Baseline Model

A **Random Forest Classifier** was trained as the baseline.

### Test Performance

- Accuracy: **0.322034**
- Weighted F1: **0.278793**

---

## Hyperparameter Tuning

`GridSearchCV` with **Stratified 5-Fold Cross-Validation** was used.

### Search Space

```text
n_estimators: [100, 200]
max_depth: [None, 10, 20]
min_samples_split: [2, 5]
min_samples_leaf: [1, 2]