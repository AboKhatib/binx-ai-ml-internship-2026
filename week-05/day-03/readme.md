# Day 3 — Dimensionality Reduction with PCA

**BinX Tech AI & ML Internship Program — Week 5, Phase 2 → Phase 3**
**Focus:** Principal Component Analysis, explained variance, and dimensionality reduction

## Overview

Day 3 shifts from grouping data (Days 1–2) to compressing it. Real datasets often carry far more features than a person can reason about at once, and high dimensionality brings real costs: sparse data, distances that lose meaning, and a search space where models overfit more easily. Principal Component Analysis (PCA) addresses this by re-expressing the data along a new set of axes — the principal components — ordered so that the first few capture as much of the original variance as possible. The result is a smaller feature set that keeps most of the original story.

This notebook works through PCA end-to-end on the **Breast Cancer Wisconsin (Diagnostic)** dataset (30 numeric features, 569 samples, built into scikit-learn), following the lab exactly as scoped for Day 3.

## Learning Objectives

- Explain the curse of dimensionality and why reduction helps.
- Apply PCA to reduce a dataset's dimensions.
- Interpret explained variance and choose how many components to keep.

## Contents

| File | Description |
|---|---|
| `Day3_PCA_Dimensionality_Reduction.ipynb` | Fully executed notebook covering the complete Day 3 lab, from raw scaled data to a justified, visualized reduction |

## Notebook Structure

1. **Load and Scale the Dataset** — loads the Breast Cancer dataset and applies `StandardScaler`, since PCA is variance-based and requires all features on a common scale before fitting.
2. **Fit PCA and Plot Cumulative Explained Variance** — fits PCA across all 30 components and plots the cumulative variance curve to visualize the diminishing-returns shape.
3. **Choose the Number of Components (~95% Variance)** — identifies the smallest component count that retains at least 95% of total variance, with the trade-off justified in writing.
4. **Reduce to 2 Components and Visualize** — refits PCA at 2 components and produces a 2D scatter plot colored by the true diagnosis label (used only for visualization, never during fitting).
5. **What the Reduction Preserved, and What It Cost** — a written reflection on the trade-off between compression, retained variance, and lost interpretability.

## Key Results

- **Original dimensionality:** 30 features
- **Components needed for ~95% variance:** 10 (95.16% retained), a 66.7% reduction in dimensionality
- **Variance retained at 2 components:** 63.2% — enough to visually separate malignant and benign samples despite the label never being used to fit PCA

## Key Takeaways

- PCA requires scaled input; an unscaled large-range feature would dominate the variance calculation purely due to units, not information content.
- The cumulative explained variance plot is the standard way to judge the compression trade-off before committing to a component count.
- Principal components are linear combinations of the original features — compression is gained at the cost of direct, feature-level interpretability.
- A 10-component representation is well suited for downstream modeling; a 2-component representation is best reserved for exploration and communication.

## Tools Used

Scikit-learn (`PCA`, `StandardScaler`) • Matplotlib • Pandas • NumPy • Jupyter Notebook

## How to Run

```bash
pip install scikit-learn pandas numpy matplotlib jupyter
jupyter notebook Day3_PCA_Dimensionality_Reduction.ipynb
```

Run all cells top to bottom; the notebook has no external data dependencies beyond scikit-learn's built-in dataset loader.

## Status

Notebook fully executed with all outputs (printed metrics and plots) committed. Ready for mentor review as part of the Week 5 deliverables.