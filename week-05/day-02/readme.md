# Day 2 — DBSCAN and Hierarchical Clustering

**BinX Tech • AI & Machine Learning Training Program — Week 5**

This notebook is the Day 2 lab of the clustering module. It picks up from Day 1's K-Means baseline and extends the analysis with two additional clustering approaches — **DBSCAN** (density-based) and **Hierarchical Clustering** (Ward linkage) — applied to the same scaled Iris dataset, so all three methods can be compared fairly.

## Learning Objectives

- Explain the limitations of K-Means and when to prefer another algorithm.
- Apply DBSCAN and interpret its output (clusters vs. noise/outlier points).
- Build and read a dendrogram, and choose an appropriate cut height.
- Compare K-Means, DBSCAN, and Hierarchical Clustering on the same data and justify which method fits best.

## Contents

1. Setup — imports and reproducibility (`random_state=42`)
2. Recap of Day 1 — load Iris, select numeric features, scale with `StandardScaler`, K-Means baseline (k=3)
3. Why K-Means isn't always enough
4. DBSCAN
   - Choosing `eps` via a k-distance plot
   - Trying multiple `eps` candidates
   - Final DBSCAN run (`eps=0.6`, `min_samples=5`) and cluster/noise visualization
5. Hierarchical Clustering
   - Building the linkage matrix (Ward method) and dendrogram
   - Choosing a cut height and extracting cluster labels with `fcluster`
6. Choosing the right method — comparison table of strengths/weaknesses
7. Hands-on lab: side-by-side comparison of all three methods
   - Quantitative summary table (clusters, noise, silhouette score)
   - Visual comparison (subplots)
   - Agreement analysis via Adjusted Rand Index (ARI), including comparison to true `Species` labels (post-hoc evaluation only)
8. Written conclusion on which method best fits the Iris dataset

## Dataset

- **File:** `Iris.csv`
- **Features used:** `SepalLengthCm`, `SepalWidthCm`, `PetalLengthCm`, `PetalWidthCm`
- `Id` and `Species` are excluded from clustering (unsupervised learning doesn't use labels); `Species` is only used afterward to evaluate results.

## Requirements

```
python >= 3.9
pandas
numpy
matplotlib
scikit-learn
scipy
```

Install with:

```bash
pip install pandas numpy matplotlib scikit-learn scipy
```

## How to Run

1. Place `Iris.csv` in the same directory as the notebook.
2. Open the notebook in Jupyter:
   ```bash
   jupyter notebook Day2_dbscan_hierarchical_clustering_EN.ipynb
   ```
3. Run all cells in order (Kernel → Restart & Run All) for reproducible results.

## Key Results

| Method | Clusters | Noise Points | Notes |
|---|---|---|---|
| K-Means (k=3) | 3 | — | Best match to true Iris species; assumes spherical clusters |
| DBSCAN (eps=0.6, min_samples=5) | see notebook output | see notebook output | Clearly isolates *setosa*; struggles to separate *versicolor*/*virginica* due to overlapping density |
| Hierarchical (Ward, cut=7) | see notebook output | — | Very close to K-Means; adds full nested structure via dendrogram |

**Conclusion:** Iris forms roughly spherical, low-noise clusters, so K-Means (or Ward-linkage hierarchical clustering) fits best. DBSCAN's strengths — automatic cluster count and explicit noise detection — matter more on data with irregular shapes or genuine outliers.

## Deliverables

- ✅ Clustering comparison notebook (K-Means vs. DBSCAN vs. Hierarchical) with a method recommendation
- ✅ DBSCAN run with reported cluster/noise counts
- ✅ Dendrogram with a chosen cut height and resulting cluster count
- ✅ Quantitative and visual comparison across all three methods
- ✅ Written conclusion on the best-fitting method for the Iris dataset

## Next Steps

Push this notebook to the project's GitHub repository with a clear commit message, per mentor sign-off, before starting Day 3 (PCA and Dimensionality Reduction).

## Tools

`scikit-learn` (KMeans, DBSCAN) • `SciPy` (linkage, dendrogram, fcluster) • `Matplotlib` • `Pandas` • `Jupyter Notebook`