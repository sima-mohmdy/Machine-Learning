
# Logistic Regression

## Overview
This project focuses on implementing Logistic Regression from scratch and comparing its performance with the Scikit-learn implementation using the Heart Disease dataset.

The main objective is to understand the internal mechanism of Logistic Regression and evaluate its performance on a binary classification task.

## Dataset
- **Dataset:** Heart Disease
- **Samples:** 303
- **Features:** 13
- **Target:** Binary classification
  - `0`: No heart disease
  - `1`: Presence of heart disease

## Project Workflow
1. Data loading and preprocessing
2. Exploratory data inspection
3. Handling categorical features using One-Hot Encoding
4. Splitting data into training and testing sets
5. Feature scaling using StandardScaler
6. Implementing Logistic Regression from scratch using gradient descent
7. Evaluating the model using classification metrics and ROC-AUC
8. Analyzing the classification threshold
9. Comparing the scratch implementation with Scikit-learn

## Models
- **Logistic Regression from Scratch:** Implemented using NumPy, the sigmoid function, binary cross-entropy loss, and gradient descent.
- **Scikit-learn Logistic Regression:** Implemented using `sklearn.linear_model.LogisticRegression`.

## Results

| Metric | From Scratch | Scikit-learn |
|---|---:|---:|
| Accuracy | 0.84 | 0.84 |
| Precision (Class 1) | 0.83 | 0.83 |
| Recall (Class 1) | 0.88 | 0.88 |
| F1-score (Class 1) | 0.85 | 0.85 |
| ROC-AUC | 0.8918 | 0.8950 |

Both implementations achieved comparable performance on the test set, with Scikit-learn obtaining a slightly higher ROC-AUC score.

## Tools & Libraries
- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

## Conclusion
This project demonstrates the implementation and evaluation of Logistic Regression from scratch and provides a comparison with the Scikit-learn implementation. It also helps develop a better understanding of gradient descent, probability estimation, and threshold-based classification.
