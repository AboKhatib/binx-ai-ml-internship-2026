# Cardiac Patient Monitoring - Phase 3 Project Plan

## 1. Project Overview & Problem Statement

Cardiovascular disease remains one of the leading causes of death worldwide, and early risk identification is critical for timely clinical intervention. This project uses the `heart.csv` dataset (302 unique patient records after de-duplication) to build a machine learning system that predicts the presence of heart disease from routine clinical measurements (age, sex, chest pain type, resting blood pressure, cholesterol, max heart rate, ST depression, etc.).

**Problem statement:** Manual risk assessment is time-consuming and inconsistent across practitioners. This project delivers a data-driven decision-support tool that flags at-risk patients early, helping clinicians prioritize follow-up care. *Note: this is an educational ML project — outputs are not a substitute for clinical diagnosis.*

Background work already completed:
- Data cleaning (duplicate removal, no missing values) and EDA
- Feature engineering (`age_group`, `stress_index`)
- Supervised modeling: Logistic Regression baseline and a GridSearchCV-tuned Random Forest pipeline (Accuracy 0.770, Precision/Recall/F1 ≈ 0.788, ROC-AUC 0.876)
- Unsupervised analysis (Week 5): K-Means clustering and PCA (detailed below)

Phase 3 shifts focus from model development to **productionizing and communicating** these results.

## 2. Week 5 Unsupervised Learning Integration

To validate whether the dataset contains natural patient sub-groups independent of the labeled target, K-Means clustering and PCA were applied to the preprocessed feature set (target excluded).

- **Optimal K selection:** K-Means was run for K = 2–7, and the Silhouette Score was used to evaluate cluster cohesion/separation. The best score (0.194) was achieved at **K = 2**, indicating the data splits most naturally into two broad patient groups rather than several fine-grained ones. This resulted in clusters of 187 and 115 patients respectively.
- **PCA visualization:** The processed feature space was reduced to 2 principal components (explaining ~41.3% of total variance: PC1 = 27.7%, PC2 = 13.6%) to visualize cluster structure in 2D.
- **Key finding — cluster/target correlation:** Although the target label was never used to build the clusters, a post-hoc comparison showed a meaningful correlation: Cluster 0 is 76.5% target-positive, while Cluster 1 is 81.7% target-negative. This confirms that the natural, unsupervised grouping of patients aligns reasonably well with actual disease status, reinforcing that the selected features carry real diagnostic signal — and gives confidence in the supervised models built on the same feature set.

## 3. Phase 3 Roadmap (Weeks 6-9)

| Sprint | Week | Focus | Key Deliverables |
|---|---|---|---|
| Sprint 1 | Week 6 | **Deploy MVP** | Streamlit app, model persistence (pickle/joblib), public URL |
| Sprint 2 | Week 7 | **Explainability & UX** | SHAP/LIME explanations, improved UI/UX |
| Sprint 3 | Week 8 | **Feature Expansion & Performance** | CSV upload, batch prediction, performance optimization |
| Sprint 4 | Week 9 | **Wrap-up** | Final documentation, code review, technical report |

## 4. Sprint 1 Details (Week 6)

**Sprint Goal:** Ship a publicly accessible, working MVP that lets a user input patient data and receive a heart disease risk prediction from the tuned Random Forest pipeline.

| # | Task | Effort (hrs) | Acceptance Criteria |
|---|---|---|---|
| 1 | Serialize final pipeline (preprocessing + model) with `joblib` | 3h | Model loads in <2s; predictions on saved test set match notebook output exactly |
| 2 | Build Streamlit input form (age, sex, cp, trestbps, chol, thalach, oldpeak, etc.) | 6h | All 13 features covered; invalid/missing inputs show inline validation errors; form submits without page crash |
| 3 | Wire prediction pipeline into app (load model → transform input → predict → display result) | 5h | Output shows predicted class + probability score; response time < 1s per prediction |
| 4 | Deploy to Streamlit Community Cloud (or equivalent) and verify public URL | 4h | App accessible via public URL on a fresh browser/session; README updated with the live link |

**Total estimated effort:** ~18 hours

## 5. Risks & Mitigation

| Risk | Impact | Mitigation |
|---|---|---|
| Model generalization on new/unseen patient data (dataset is small, 302 records) | Predictions may be unreliable for patient profiles outside the training distribution | Add input-range validation/warnings for out-of-distribution values; document known dataset limitations in the app and report |
| Deployment latency / cold-start delays on free hosting tiers | Poor user experience, timeouts | Cache the loaded model in memory; keep pipeline lightweight; monitor load times post-deploy |
| Data/label leakage when adding new engineered features in Sprint 3 | Inflated offline metrics that don't hold in production | Reuse the existing scikit-learn `Pipeline` for all new features; re-validate with cross-validation before merging |
| SHAP/LIME explanations slow down or confuse non-technical users | Reduced usability, misinterpretation of results | Precompute/cache explanations where possible; pair visual explanations with plain-language summaries |
| Scope creep in Sprint 3 (CSV upload + batch prediction + performance work in one sprint) | Sprint overrun, rushed testing | Timebox each sub-feature; if needed, defer batch prediction polish to Sprint 4 buffer time |