# Day 2 — Cross-Validation

## Overview

On Day 2 of the project, the focus was on evaluating the machine learning model using **Cross-Validation**.

The main goal was to determine whether the performance obtained from a single train/test split was reliable, or whether it was influenced by the specific way the dataset was divided.

---

## 1. Single Train/Test Split

Initially, the model was evaluated using a single split of the dataset into:

* Training Set
* Test Set

The resulting F1 Score was:

```text
Single-split F1 : 0.8094
```

While this provides an initial estimate of the model's performance, it depends entirely on one particular data split.

Therefore, it may not fully represent the model's generalization performance.

---

## 2. Why Cross-Validation?

**Cross-Validation** was introduced to obtain a more reliable estimate of model performance.

Instead of training and evaluating the model only once, the dataset is divided into multiple **folds**.

For each fold:

1. One portion of the data is used as the validation set.
2. The remaining portions are used for training.
3. The model is trained on the training data.
4. The F1 Score is calculated on the validation data.
5. The process is repeated until every fold has been used for validation.

The final Cross-Validation score is calculated as the average performance across all folds.

---

## 3. Cross-Validation Results

After applying Cross-Validation, the model achieved:

```text
Cross-validation F1 : 0.8004
```

The standard deviation across the folds was:

```text
Cross-validation std : 0.0150
```

The relatively small standard deviation indicates that the model's performance remained reasonably consistent across the different folds.

---

## 4. Comparison

The results from the single split and Cross-Validation were compared:

```text
Single-split F1       : 0.8094
Cross-validation F1   : 0.8004
Difference             : +0.0089
Cross-validation std  : 0.0150
```

The difference was:

```text
0.8094 - 0.8004 = 0.0089
```

Therefore, the Single-Split evaluation produced an F1 Score approximately **0.009 higher** than the average Cross-Validation score.

---

## 5. Interpretation

The Single-Split F1 Score was slightly higher than the Cross-Validation average.

However, the difference is relatively small.

This suggests that the model's performance is not heavily dependent on one specific train/test split.

The Cross-Validation standard deviation of:

```text
0.0150
```

also indicates relatively limited variation between the different folds.

Overall, Cross-Validation provides a more robust estimate of the model's expected performance than relying on a single split.

---

## 6. Why F1 Score?

The **F1 Score** was used as the main evaluation metric because it combines:

* **Precision**
* **Recall**

The F1 Score is calculated as:

```text
F1 = 2 × (Precision × Recall) / (Precision + Recall)
```

It provides a balance between precision and recall and is useful when both types of errors are important.

---

## 7. Results Summary

| Metric               |     Result |
| -------------------- | ---------: |
| Single-Split F1      | **0.8094** |
| Cross-Validation F1  | **0.8004** |
| Difference           | **0.0089** |
| Cross-Validation Std | **0.0150** |

### Key Finding

The model achieved an F1 Score of approximately **0.80** under Cross-Validation.

The Cross-Validation result was close to the Single-Split result, indicating that the model's performance is relatively stable across different data splits.

---

## 8. What Was Accomplished on Day 2?

During Day 2, the following tasks were completed:

* Implemented **Cross-Validation**.
* Evaluated the model across multiple folds.
* Calculated the mean Cross-Validation F1 Score.
* Calculated the standard deviation across folds.
* Compared Cross-Validation with the Single Train/Test Split.
* Analyzed the stability of the model's performance.
* Checked whether the Single-Split result was representative of the model's overall performance.

---

## Conclusion

Cross-Validation provided a more reliable evaluation of the model compared with using a single train/test split.

The final results were:

```text
Single-split F1       : 0.8094
Cross-validation F1   : 0.8004
Difference             : 0.0089
Cross-validation std  : 0.0150
```

The small difference between the two evaluation methods, together with the relatively low standard deviation, suggests that the model performs consistently across different subsets of the dataset.

Therefore, the Cross-Validation results provide stronger evidence for the model's generalization performance and establish a more reliable baseline for the next stages of the project.
