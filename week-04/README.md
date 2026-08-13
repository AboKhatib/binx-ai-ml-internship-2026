# Week 4 — Model Evaluation, Tuning & Pipelines

## Overview

Week 4 focused on improving the reliability and performance of machine
learning models through proper evaluation, cross-validation, feature
engineering, hyperparameter tuning, and Scikit-learn Pipelines.

## Day 1 — Train / Validation / Test Split

### What I Learned

- The purpose of Training, Validation, and Test sets.
- Why the test set should remain untouched during model selection.
- How to create separate datasets using `train_test_split`.
- The importance of evaluating the final model on unseen data.

## Day 2 — Cross-Validation

### What I Learned

- Why a single validation split may not provide a reliable estimate.
- How K-Fold Cross-Validation works.
- How to use `cross_val_score`.
- How to calculate mean and standard deviation of CV scores.
- How Stratified K-Fold is used for classification problems.

## Day 3 — Bias, Variance & Model Fit

### What I Learned

- The difference between underfitting and overfitting.
- The relationship between bias and variance.
- How to compare training and validation performance.
- How model complexity affects generalization.
- How regularization can help reduce overfitting.
- The basic concepts of Ridge (L2) and Lasso (L1) regularization.

## Day 4 — Feature Engineering & Hyperparameter Tuning

### What I Learned

- How feature engineering can improve model performance.
- How to create useful features from existing data.
- The difference between parameters and hyperparameters.
- How to use `GridSearchCV`.
- How cross-validation is used during hyperparameter tuning.
- The purpose of `RandomizedSearchCV`.
- How to select suitable hyperparameters based on validation performance.

## Day 5 — Scikit-learn Pipelines

### Dataset

The Day 5 mini-project used `Iris.csv`.

The target variable was:

- `Species`

The `Id` column was removed because it is an identifier rather than a useful
predictive feature.

### What I Learned

- How to build Scikit-learn Pipelines.
- How to use `ColumnTransformer`.
- How to include Feature Engineering inside a Pipeline.
- How to use `StandardScaler`.
- How to tune a complete Pipeline using `GridSearchCV`.
- How to use Stratified 5-Fold Cross-Validation.
- How Pipelines help prevent Data Leakage.
- How to evaluate the final model using a held-out test set.
- How to compare a tuned model with a baseline model.

### Feature Engineering

Four additional features were created:

- `SepalArea`
- `PetalArea`
- `PetalRatio`
- `SepalRatio`

### Model Tuning

Logistic Regression was used as the final model.

`GridSearchCV` was used to tune its hyperparameters using Stratified 5-Fold
Cross-Validation.

The optimization metric was Macro F1 because the Iris dataset contains three
target classes.

### Evaluation

The final model was evaluated using:

- Accuracy
- Macro F1-score
- Classification Report
- Confusion Matrix

The tuned model was also compared with the baseline model.

## Data Leakage

A major focus of Week 4 was preventing Data Leakage.

Preprocessing and Feature Engineering were included inside the Pipeline so that
they are handled correctly during Cross-Validation.

The test set remained separate from the hyperparameter tuning process and was
used only for the final evaluation.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Jupyter Notebook
- Git
- GitHub

## Main Takeaway

Week 4 focused on building machine learning models that are properly evaluated,
tuned, reproducible, and protected against Data Leakage.

The week provided practical experience with model evaluation, Cross-Validation,
Bias-Variance, Feature Engineering, Hyperparameter Tuning, and Scikit-learn
Pipelines.