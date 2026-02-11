# CA01 — Spam Email Classification using Naive Bayes

## Project Description

This project develops a machine learning classifier that identifies whether an email is **spam** or **ham (not spam)**.
The model is built using a **Gaussian Naive Bayes algorithm** and relies on word frequency patterns extracted from email text files.

The goal of the assignment is to demonstrate a complete text analytics pipeline:

1. Read raw text emails
2. Clean and preprocess text
3. Convert text into numerical features
4. Train a classifier
5. Evaluate model performance

---

## Dataset

The dataset is organized into two directories:

* `train-mails/` — used to train the model
* `test-mails/` — used to evaluate the model

Each file represents one email message.

---

## Methodology

### Step 1 — Build Dictionary

All words from the training emails are collected and counted.
Only valid words are kept:

* Alphabetic characters only
* Remove numbers and punctuation
* Remove single-letter words

The top **3000 most frequent words** form the dictionary used for modeling.

---

### Step 2 — Feature Extraction

Each email is transformed into a numeric vector based on word frequency.

For every dictionary word:

* Count how many times it appears in an email

This creates a matrix where:

* Rows = emails
* Columns = word counts

---

### Step 3 — Train Model

A **Gaussian Naive Bayes classifier** is trained on the training dataset.

The model learns probability patterns of words appearing in spam vs non-spam emails.

---

### Step 4 — Prediction & Evaluation

The trained model predicts labels for the test dataset.

Performance metrics calculated:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

---

## Example Output

```
Training Model using Gaussian Naive Bayes algorithm .....
Training completed
testing trained model to predict Test Data labels
Completed classification of the Test Data .... now printing Accuracy Score:

Accuracy: 0.9653846153846154
```

---

## File Structure

```
CA01/
│
├── train-mails/
├── test-mails/
├── CA01.ipynb
└── README.md
```

---

## Key Concepts

* Natural Language Processing (NLP)
* Bag-of-Words Feature Engineering
* Supervised Classification
* Naive Bayes Algorithm
* Model Evaluation Metrics

---

## How to Run

1. Place dataset folders in the same directory as the notebook:

```
./train-mails
./test-mails
```

2. Open the notebook:

```
CA01.ipynb
```

3. Run all cells sequentially.

---

## Conclusion

The model successfully classifies emails using word frequency patterns.
Naive Bayes performs well on text data because high-dimensional sparse features (words) follow distinct probability distributions between spam and non-spam emails.

---

**Author:** Josh Tsutaoka
M.S. Business Analytics — Loyola Marymount University
