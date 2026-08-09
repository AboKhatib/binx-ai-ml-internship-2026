# Week 4 — Day 1: Train, Validation & Test Splits

## What We Learned

* Why a simple train/test split is not enough for model development.
* The difference between **Training, Validation, and Test Sets**.
* How to create a **60/20/20** train/validation/test split.
* How to use `random_state=42` for reproducibility.
* Why **stratification** is important for classification problems.
* How to use the validation set for **hyperparameter tuning**.
* Why the test set must remain untouched until final evaluation.
* How tuning against the test set can cause **data leakage**.
* Why a single validation split can be unreliable.
* Why **Cross-Validation** is introduced as the next step.

## Practical Work

Using the **Breast Cancer Classification Dataset**, we:

* Prepared the features and target.
* Removed the `Id` column.
* Handled missing values.
* Created a 60/20/20 split.
* Trained a Random Forest classifier.
* Tuned `n_estimators` using the validation set.
* Selected the best configuration.
* Evaluated the final model on the test set once.

