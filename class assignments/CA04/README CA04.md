# CA04 – Ensemble Models Analysis

## Project Overview
This project evaluates the performance of multiple **ensemble learning algorithms** on the Census Income dataset to predict whether an individual earns more than \$50K annually. The primary objective is to understand how ensemble methods improve predictive performance and how model behavior changes as the number of estimators increases.

The analysis compares **bagging** and **boosting** approaches through systematic hyperparameter tuning and performance evaluation using classification metrics and visualization.

---

## Problem Statement
Given demographic and employment-related features, build classification models capable of predicting income category:

- **1** → Income > \$50K  
- **0** → Income ≤ \$50K

The assignment specifically investigates:

- How model performance changes with increasing ensemble size
- Whether an optimal number of estimators exists
- Which ensemble method performs best overall

---

## Dataset
The project uses the **Census Income dataset**, loaded directly from the required GitHub raw data source.

A provided column, `flag`, was used to programmatically split the dataset into:

- Training dataset
- Testing dataset

This ensures reproducibility and consistency with assignment requirements.

---

## Data Preparation
Data preprocessing followed best practices for machine learning workflows:

- Removed duplicate observations
- Dropped missing values
- Standardized categorical variables by trimming whitespace
- Encoded categorical predictors using Label Encoding
- Managed unseen categories in test data by assigning a fallback value (`-1`)

These steps ensured compatibility with tree-based ensemble algorithms while preventing data leakage.

---

## Ensemble Models Implemented
Four ensemble learning techniques were implemented and compared:

1. **Random Forest (Bagging Method)**
2. **AdaBoost (Adaptive Boosting)**
3. **Gradient Boosting**
4. **XGBoost (Extreme Gradient Boosting)**

Each model represents a different strategy for improving predictive accuracy through model aggregation.

---

## Hyperparameter Tuning
Model performance was evaluated across the required estimator range:

```
n_estimators = [50,100,150,200,250,300,350,400,450,500]
```

For each value:

1. Model trained on training data
2. Predictions generated on test data
3. Accuracy computed
4. ROC-AUC calculated using predicted probabilities

This systematic approach allows performance trends to be analyzed rather than relying on a single configuration.

---

## Evaluation Metrics

### Accuracy
Measures overall classification correctness.

### ROC-AUC (Receiver Operating Characteristic – Area Under Curve)
Evaluates the model’s ability to distinguish between income classes across classification thresholds.  
ROC-AUC is emphasized because it provides a more robust comparison for classification models.

---

## Visual Analysis
For every model, two diagnostic plots were generated:

- **Accuracy vs Number of Estimators**
- **ROC-AUC vs Number of Estimators**

These plots help identify:
- performance stability
- diminishing returns
- optimal estimator regions

---

## Results Summary
A final comparison table reports:

- Best Accuracy achieved
- Best ROC-AUC achieved
- Corresponding optimal number of estimators

This enables direct benchmarking across ensemble approaches.

---

## Key Findings

- Increasing the number of estimators improves performance initially for all models.
- Performance gains diminish after a certain threshold, indicating convergence.
- Random Forest stabilizes earlier due to variance reduction through averaging.
- Boosting models improve more gradually by sequentially correcting prediction errors.
- XGBoost demonstrates strong and stable predictive performance due to optimized gradient boosting implementation.

Overall, ensemble methods significantly enhance predictive capability compared to single-model approaches.

---

## Technologies Used
- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib

---

## Reproducibility Instructions
1. Open the notebook in Jupyter Notebook or Google Colab.
2. Run all cells sequentially.
3. The workflow will:
   - Load and preprocess the dataset
   - Train ensemble models
   - Perform hyperparameter tuning
   - Generate evaluation plots
   - Output comparison results

No manual parameter adjustment is required.

---

## Conclusion
This project demonstrates how ensemble learning improves classification performance through aggregation and iterative error correction. Hyperparameter tuning reveals that increasing ensemble size enhances model stability up to an optimal range, after which improvements become marginal.

The comparison highlights practical differences between bagging and boosting strategies and reinforces the effectiveness of ensemble techniques in real-world predictive modeling tasks.

---
