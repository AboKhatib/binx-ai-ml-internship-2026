# Week 4 - Day 5: Scikit-learn Pipeline

## Overview

This project demonstrated how to build a professional, end-to-end machine learning workflow using **Scikit-learn** and the **Iris dataset**.

The final workflow combines:

* Data preparation
* Feature engineering
* `ColumnTransformer`
* `StandardScaler`
* Logistic Regression
* Stratified 5-Fold Cross-Validation
* `GridSearchCV`
* Leakage prevention
* Final evaluation on held-out test data
* Baseline comparison

The main lesson from Day 5 is that **preprocessing, feature engineering, hyperparameter tuning, and modeling should be organized into one reproducible Pipeline**.

The final test set was kept isolated until all model selection and tuning decisions were completed.

## Dataset

The project uses `Iris.csv`.

### Target

* `Species`

### Input Features

* `SepalLengthCm`
* `SepalWidthCm`
* `PetalLengthCm`
* `PetalWidthCm`

The `Id` column was removed because it is only an identifier and does not provide useful information for prediction.

## Feature Engineering

Four additional features were created to provide the model with more informative representations of the original measurements:

* `SepalArea`
* `PetalArea`
* `PetalRatio`
* `SepalRatio`

## What I Learned

Through this project, I learned how to:

* Build Scikit-learn Pipelines.
* Use `ColumnTransformer` for preprocessing.
* Create engineered features inside a Pipeline.
* Apply `StandardScaler`.
* Use Stratified 5-Fold Cross-Validation.
* Tune Pipeline hyperparameters with `GridSearchCV`.
* Prevent data leakage during preprocessing and cross-validation.
* Evaluate the final model on a held-out test set.
* Compare a tuned model against a baseline model.

## Main Takeaway

A well-designed machine learning workflow should keep **data preparation, feature engineering, preprocessing, model training, and hyperparameter tuning together inside a reproducible Pipeline**. This approach helps prevent data leakage, makes cross-validation more reliable, and ensures that the final evaluation on unseen test data provides a realistic estimate of model performance.
