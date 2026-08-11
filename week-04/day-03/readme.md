# Day 3 

## Summary

In Day 3, we studied the Bias-Variance Trade-off and learned how to
diagnose model fit using training and validation performance.

We investigated three important cases:

### 1. Underfitting

Underfitting occurs when the model is too simple to capture the patterns
in the data.

Its typical symptoms are low training and validation performance.

### 2. Overfitting

Overfitting occurs when the model is too complex and learns the training
data too closely.

Its typical symptom is high training performance combined with
significantly lower validation performance.

### 3. Good Fit

A good fit provides strong training and validation performance with a
relatively small gap between them.

## Bias-Variance Trade-off

We learned that increasing model complexity generally decreases bias but
increases variance.

The goal is to find a suitable balance between the two so that the model
can learn meaningful patterns while still generalizing to unseen data.

## Model Diagnosis

The training-validation score gap was used as the main diagnostic tool:

- Low training + low validation → Underfitting
- High training + much lower validation → Overfitting
- High training + high validation with a small gap → Good fit

## Regularization

We also introduced regularization as a method for reducing overfitting.

The two main techniques studied were:

- Ridge (L2)
- Lasso (L1)

The `alpha` parameter controls the regularization strength.

## Final Conclusion

The main lesson from Day 3 is that a high training score alone does not
mean that a model is good.

A trustworthy model should generalize well to unseen data.

Therefore, model complexity must be carefully controlled and model
performance should always be evaluated using both training and validation
results.