# Cardiac Patient Monitoring System

## Overview

This project presents an individual machine learning analysis of a
cardiac-related dataset using classical machine learning techniques.

The project follows the AI & Machine Learning curriculum covered during
the BinX Tech internship.

## Objective

The objective is to analyze the dataset, build classification models,
evaluate them using cross-validation, tune a final model, and explore
the data using unsupervised learning.

## Workflow

Dataset
→ Data Cleaning
→ EDA
→ Classification
→ Model Comparison
→ Cross-Validation
→ Feature Engineering
→ Pipeline
→ GridSearchCV
→ Final Evaluation
→ Clustering
→ PCA

## Dataset

The project uses `heart.csv`.

The target variable is:

`target`

The dataset contains cardiac-related features such as age, sex,
chest-pain type, resting blood pressure, cholesterol, maximum heart
rate, exercise-induced angina, and other measurements.

## Data Cleaning

The dataset was inspected for:

- Missing values
- Duplicate rows
- Invalid values
- Data types
- Feature distributions

Duplicate observations were removed before modeling.

## Exploratory Data Analysis

EDA includes:

- Target distribution
- Numerical distributions
- Categorical feature analysis
- Correlation analysis
- Outlier detection

## Supervised Learning

The project evaluates several classification models:

- Logistic Regression
- Random Forest
- SVM
- k-NN

## Evaluation

Models are evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix
- Stratified 5-fold Cross-Validation

## Feature Engineering

Two engineered features are introduced:

- `age_group`
- `stress_index`

## Machine Learning Pipeline

A Scikit-learn Pipeline combines:

1. Feature preprocessing
2. Numerical scaling
3. Categorical encoding
4. Classification model

This structure helps prevent preprocessing leakage.

## Hyperparameter Tuning

Random Forest hyperparameters are optimized using
`GridSearchCV` with 5-fold cross-validation.

## Unsupervised Learning

K-Means clustering is used to explore possible groups in the dataset.

PCA is used to visualize the processed feature space in two dimensions.

## Limitations

This project is educational and is not intended for clinical diagnosis,
treatment recommendations, or medical decision-making.