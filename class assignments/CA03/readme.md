# CA03 — Decision Tree Classifier (Census Income)

Build and evaluate a **Decision Tree** model to predict whether an individual earns **> $50K** based on **discretized (binned) census features**. This project focuses on interpretable modeling, basic preprocessing for categorical bins, and hyperparameter experiments to improve performance.

---

## Project Goals
- Train a baseline Decision Tree classifier on a discretized census dataset
- Compare key hyperparameters (split criterion, max depth, min samples leaf, max features)
- Report classification performance (Accuracy / Precision / Recall / F1)
- Demonstrate a safe encoding workflow for categorical features (including unseen labels)

---

## Dataset
Loaded directly from:
- `census_data.csv` (hosted on GitHub):  
  `https://github.com/ArinB/MSBA-CA-03-Decision-Trees/blob/master/census_data.csv?raw=true`

**Target**
- `y`  
  - `0` = `<=50K`
  - `1` = `>50K`

**Split indicator**
- `flag` {`train`, `test`}

**Feature columns (already discretized / binned)**
- `hours_per_week_bin`
- `occupation_bin`
- `msr_bin`
- `capital_gl_bin`
- `race_sex_bin`
- `education_num_bin`
- `education_bin`
- `workclass_bin`
- `age_bin`

---

## Method Overview
1. **Load data**
2. **Split** into train/test using `flag`
3. **Encode categorical bins**
   - `LabelEncoder` per column
   - Includes a safeguard for **previously unseen labels** in the test/new rows (mapped to `-1`)
4. **Train baseline Decision Tree**
5. **Run hyperparameter comparisons**
   - Split criterion: `gini` vs `entropy`
   - `max_depth`
   - `min_samples_leaf`
   - `max_features`
6. **Evaluate**
   - Accuracy, Precision, Recall, F1
   - Classification report for final model

---

## Results (from notebook output)

### Baseline Model
- **Accuracy:** 0.7508  
- **Precision:** 0.6455  
- **Recall:** 0.4328  
- **F1:** 0.5182  

### Hyperparameter Notes (best observed)
- Best split criterion: **entropy**
- Best max depth: **10**
- Best min samples leaf (tested): **25**
- Best max features: **None**

### Best Model Performance
- **Accuracy:** 0.7581  
- **Precision:** 0.6740  
- **Recall:** 0.4232  
- **F1:** 0.5200  

Classification Report (Best Model):
- `<=50K`: strong recall
- `>50K`: higher precision than baseline, but recall remains the main challenge (class imbalance / overlap)

---

## How to Run

### Option A: Jupyter / VS Code
1. Clone the repo
2. Open the notebook
3. Run cells top-to-bottom

### Option B: Google Colab
1. Upload the notebook to Colab
2. Run all cells

---

## Requirements
Suggested environment:
- Python 3.9+
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
