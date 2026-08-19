# Day 4 — t-SNE & Anomaly Detection

**Focus:** Visualization with t-SNE, PCA vs. t-SNE, and unsupervised anomaly detection with Isolation Forest

## Overview

Day 3 used PCA to compress the dataset while preserving global variance. Day 4 introduces a second, purpose-built visualization technique — **t-SNE** — which preserves local neighborhoods instead, making it more effective at revealing cluster shapes that PCA can blur. The session then shifts to a related but distinct problem: **anomaly detection**, using **Isolation Forest** to flag data points that differ meaningfully from the rest without any labeled examples of what an anomaly looks like.

This notebook continues on the same **Breast Cancer Wisconsin (Diagnostic)** dataset used on Day 3 (30 scaled features, 569 samples), so the t-SNE projection can be compared directly against the PCA projection on identical data. K-Means (k=2) is refit in a short setup step to reproduce the Day 1–2 cluster labels used for coloring the t-SNE plot.

## Learning Objectives

- Use t-SNE to visualize high-dimensional data and distinguish it from PCA.
- Explain what anomaly detection is and why it is often unsupervised.
- Detect anomalies with Isolation Forest and interpret the flagged points.

## Contents

| File | Description |
|---|---|
| `Day4_tSNE_Anomaly_Detection.ipynb` | Fully executed notebook covering the complete Day 4 lab, from t-SNE visualization through Isolation Forest anomaly inspection |

## Notebook Structure

0. **Setup — Recreate Cluster Labels** — reloads the scaled dataset and refits K-Means (k=2) so the t-SNE plot can be colored by cluster, matching the Day 1–2 workflow.
1. **Apply t-SNE and Plot, Colored by Cluster** — reduces the 30-dimensional dataset to 2D with t-SNE, colored by the K-Means cluster assignment.
2. **Compare the t-SNE Plot to the Day 3 PCA Plot** — places both projections side by side and explains what each technique reveals and gives up.
3. **Run Isolation Forest and Report Flagged Anomalies** — fits Isolation Forest with `contamination=0.05` and reports the anomaly count and rate.
4. **Inspect Two Flagged Points and Hypothesize Why** — pulls two flagged samples, compares their feature values against dataset averages via z-scores, and hypothesizes the cause of each flag.

## Key Results

- **t-SNE vs. PCA:** t-SNE produced tighter, more clearly separated cluster regions than PCA, at the cost of interpretable axes and reusability for modeling.
- **Anomalies flagged:** 29 of 569 samples (5.1%), consistent with the `contamination=0.05` setting.
- **Inspected anomalies:** both sampled points were malignant cases with several features (compactness, symmetry, fractal dimension) deviating 3–6 standard deviations from the dataset average — extreme values in shape-irregularity measurements are the likely driver of their isolation.

## Key Takeaways

- PCA preserves global variance and produces interpretable, reusable axes; t-SNE preserves local neighborhoods and produces a visualization-only layout with no meaningful axis interpretation.
- t-SNE's output should never be fed into a downstream model — it is a tool for looking, not for computing with.
- Anomaly detection is naturally unsupervised: anomalies are rare and rarely pre-labeled, so the model learns what "normal" looks like and flags whatever deviates from it.
- Isolation Forest's `contamination` parameter is a direct estimate of the expected anomaly fraction, not something the algorithm discovers on its own.
- DBSCAN's noise points (Day 2) and Isolation Forest's flagged anomalies are two different mechanisms — density-based vs. isolation-based — converging on the same underlying idea: identifying what doesn't fit.

## Tools Used

Scikit-learn (`TSNE`, `IsolationForest`, `PCA`, `KMeans`) • Matplotlib • Pandas • NumPy • Jupyter Notebook

## How to Run

```bash
pip install scikit-learn pandas numpy matplotlib jupyter
jupyter notebook Day4_tSNE_Anomaly_Detection.ipynb
```

Run all cells top to bottom; the notebook has no external data dependencies beyond scikit-learn's built-in dataset loader. Note that t-SNE fitting is the slowest step in the notebook and may take a short while longer than the other cells.

## Status

Notebook fully executed with all outputs (printed metrics and plots) committed. Ready for mentor review as part of the Week 5 deliverables.
