# Week 5 - Day 1: Unsupervised Learning & K-Means Clustering

## Overview

This notebook provides a comprehensive introduction to unsupervised learning, focusing on the K-Means clustering algorithm. We apply these concepts to the BreastCancer dataset to discover natural groupings in the data without using the target labels.

## Objectives

By the end of this session, you will be able to:

- Understand the fundamental differences between supervised and unsupervised learning
- Prepare a dataset for clustering by removing identifiers and target labels
- Apply feature scaling using StandardScaler for distance-based algorithms
- Implement K-Means clustering using scikit-learn
- Determine the optimal number of clusters using the Elbow Method
- Evaluate cluster quality using Silhouette Score
- Train and interpret a final K-Means model
- Visualize clustering results
- Interpret the discovered clusters in the context of the original data

## Dataset

**BreastCancer.csv** contains medical features related to breast cancer cases:

- **Features:** 9 numerical medical measurements (e.g., Cl.thickness, Cell.size, Cell.shape, Bare.nuclei, etc.)
- **Target:** `Class` column (0 = Benign, 1 = Malignant) - used only for post-analysis interpretation
- **Samples:** 699 observations
- **Missing Values:** Present in the `Bare.nuclei` column (handled via median imputation)

## Methodology

### 1. Data Preparation
- Removed identifier (`Id`) and target (`Class`) columns from clustering features
- Converted all features to numeric type
- Handled missing values using median imputation
- Applied StandardScaler for feature standardization

### 2. Clustering with K-Means
- Implemented K-Means clustering from scikit-learn
- Tested cluster numbers from k=1 to k=10

### 3. Optimal K Selection
- **Elbow Method:** Visualized inertia (within-cluster sum of squares) to identify potential k values
- **Silhouette Score:** Quantitatively evaluated candidate clusters (k=2 and k=3)
- **Selected k = 2** based on higher Silhouette Score

### 4. Final Model Training
- Trained final K-Means model with k=2
- Assigned cluster labels to each observation
- Analyzed cluster centroids

### 5. Visualization & Interpretation
- Visualized clusters using 2D scatter plot (Cl.thickness vs. Cell.size)
- Compared cluster assignments with original Class labels
- Interpreted cluster characteristics using feature centroids

## Key Results

### Optimal Number of Clusters
- **Elbow Method:** Suggested k=2 or k=3
- **Silhouette Scores:**
  - k=2: 0.5740
  - k=3: 0.5567
- **Selected:** k=2 (higher Silhouette Score)

### Cluster Characteristics (Original Feature Scale)

| Feature | Cluster 0 | Cluster 1 |
| :--- | :--- | :--- |
| Cl.thickness | **6.6** | 2.9 |
| Cell.size | **6.5** | 2.1 |
| Cell.shape | **6.2** | 2.1 |
| Marg.adhesion | **5.6** | 2.0 |
| Epith.c.size | **5.2** | 2.4 |
| Bare.nuclei | **8.0** | 2.3 |
| Bl.cromatin | **6.4** | 2.8 |
| Normal.nucleoli | **5.8** | 2.4 |
| Mitoses | **1.9** | 1.2 |

### Cluster Interpretation

**Cluster 0 (Likely Malignant):**
- High values across all medical features
- Particularly elevated in Bare.nuclei, Cl.thickness, and Bl.cromatin
- Strongly associated with cancerous cells

**Cluster 1 (Likely Benign):**
- Low values across all medical features
- Normal cell characteristics
- Associated with healthy/benign cells

### Comparison with Original Class Labels

| Cluster | Class 0 (Benign) | Class 1 (Malignant) |
| :--- | :--- | :--- |
| Cluster 0 | 12 | 221 |
| Cluster 1 | 446 | 20 |

> **Note:** Clusters largely align with original classes but are not identical, demonstrating that unsupervised learning discovers natural patterns without using labels.

## Tools & Libraries

- **Python 3.13**
- **Pandas:** Data manipulation and analysis
- **NumPy:** Numerical operations
- **Matplotlib:** Data visualization
- **Scikit-learn:**
  - `StandardScaler`: Feature standardization
  - `KMeans`: Clustering algorithm
  - `silhouette_score`: Cluster quality evaluation


