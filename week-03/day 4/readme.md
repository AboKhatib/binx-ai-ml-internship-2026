## Day 4 — Classification Model Comparison

On Day 4, I trained and compared four supervised classification algorithms:

- Decision Tree
- Random Forest
- Support Vector Machine
- k-Nearest Neighbors

All models were evaluated using the same reproducible train/test split.
SVM and k-NN were trained through Scikit-learn pipelines containing
`StandardScaler` to prevent inconsistent feature scales and data leakage.

The models were evaluated using accuracy, precision, recall, and F1-score,
with F1-score used as the primary comparison metric.

I also:

- produced a unified model-comparison table;
- examined confusion matrices and classification reports;
- compared training and test performance;
- extracted Random Forest feature importances;
- identified and justified the best-performing classifier.