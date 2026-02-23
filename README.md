# Credit Card Fraud Detection using Machine Learning and SMOTE

## Project Overview

This project focuses on detecting fraudulent credit card transactions
using machine learning techniques. Due to the highly imbalanced nature
of the dataset, SMOTE (Synthetic Minority Over-sampling Technique) is
used to improve the detection of fraudulent transactions.

---

## Dataset

- Source: Kaggle Credit Card Fraud Dataset
- Total transactions: 284,807
- Fraudulent transactions: 492
- Legitimate transactions: 284,315
- Features:
  - Time
  - Amount
  - 28 anonymized numerical features (V1–V28)
- Target variable:
  - Class (0 = Legitimate, 1 = Fraud)
-https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
---

## Problem Statement

The objective of this project is to accurately classify credit card
transactions as fraudulent or legitimate while addressing severe class
imbalance and minimizing false negatives, as missed frauds have a high
financial impact.

---

## Project Workflow

1. Loaded and explored the dataset.
2. Analyzed class imbalance in the target variable.
3. Performed feature scaling on Time and Amount.
4. Split the dataset into training and testing sets using stratification.
5. Applied SMOTE only on the training data to handle class imbalance.
6. Trained machine learning models on SMOTE-balanced data.
7. Evaluated model performance using appropriate metrics.
8. Simulated real-time fraud detection.
9. Saved the final trained model for reuse.

---

## Class Imbalance Handling (SMOTE)

The dataset is extremely imbalanced, with fraudulent transactions
representing less than 0.2% of the total data.

To address this issue, SMOTE (Synthetic Minority Over-sampling Technique)
was applied **only to the training dataset** after the train-test split.
This approach balances the classes while preventing data leakage into
the test set.

---

## Models Used

- Logistic Regression
- Random Forest Classifier

---

## Evaluation Metrics

Due to class imbalance, accuracy alone is not sufficient. The following
metrics were used:

- Confusion Matrix
- Precision
- Recall
- ROC-AUC Score

---

## Results

Baseline (Default Threshold = 0.5):

- Fraud Recall: 84%
- Fraud Precision: 85%
- ROC-AUC Score: 0.973
- 82 out of 98 fraudulent transactions were correctly detected.

Threshold Optimization:

Lowering the decision threshold improved fraud detection performance.

- At threshold = 0.4:
  - Fraud Recall: 86%
  - Fraud Precision: 79%

- At threshold = 0.3:
  - Fraud Recall: 90%
  - Fraud Precision: 73%

- At threshold = 0.2:
  - Fraud Recall: 90%
  - Fraud Precision: 59%

Lower thresholds increase fraud detection (recall) but also increase false positives. 
This trade-off is critical in real-world fraud detection systems where missing fraud 
is often more costly than investigating false alarms.


---

## Real-Time Fraud Detection Simulation

A real-time fraud detection simulation was implemented by passing
individual transactions from the test dataset into the trained model.
Each transaction was classified one-by-one to mimic live transaction
processing in a real-world fraud detection system.

---

## How to Run the Project

1. Clone the repository.
2. Install dependencies listed in `requirements.txt`.
3. Open the Jupyter Notebook from the `notebooks` folder.
4. Run all cells sequentially from top to bottom.

---

## Conclusion

This project demonstrates a complete end-to-end machine learning
pipeline for credit card fraud detection, including data preprocessing,
class imbalance handling with SMOTE, model training, evaluation, and
