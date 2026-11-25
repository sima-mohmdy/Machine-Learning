
# KNN, SVM, and Naive Bayes on Adult Dataset

## Overview

This project compares three classical machine learning classification algorithms: **K-Nearest Neighbors (KNN)**, **Support Vector Machine (SVM)**, and **Gaussian Naive Bayes**.

The Adult Income dataset is used to predict whether an individual's annual income exceeds $50K based on demographic and employment-related features.

## Objectives

- Implement and evaluate KNN, SVM, and Naive Bayes classifiers.
- Preprocess numerical and categorical features.
- Evaluate model performance using classification metrics.
- Apply hyperparameter tuning to improve model performance.
- Visualize model predictions and decision boundaries using PCA.
- Explore ensemble learning through Hard Voting, Soft Voting, and Averaging.

## Methods and Workflow

### 1. Data Preprocessing
- Handling missing values.
- Encoding categorical features.
- Scaling numerical features.
- Splitting the data into training and testing sets.

### 2. Classification Models
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM) with RBF kernel
- Gaussian Naive Bayes

### 3. Hyperparameter Tuning
- KNN: Cross-validation to find the optimal number of neighbors.
- SVM: RandomizedSearchCV to select the best values of `C` and `gamma`.
- Naive Bayes: GridSearchCV to optimize `var_smoothing`.

### 4. Ensemble Learning
- Hard Voting
- Soft Voting
- Averaging

## Results

### Tuned Model Comparison

| Model | Train Accuracy | Test Accuracy | Precision (Class 1) | Recall (Class 1) | F1-score (Class 1) |
|---|---:|---:|---:|---:|---:|
| KNN (K=23) | 85.57% | 84.56% | 70% | 61% | 65% |
| SVM (RBF) | 86.97% | 85.77% | 75% | 59% | 66% |
| Gaussian Naive Bayes | 83.15% | 82.83% | 66% | 56% | 61% |

### Ensemble Model Comparison

| Method | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-score (Class 1) |
|---|---:|---:|---:|---:|
| Hard Voting | 85% | 73% | 59% | 65% |
| Soft Voting | 85% | 73% | 58% | 64% |
| Averaging | 85% | 73% | 59% | 65% |

## Conclusion

SVM achieved the best overall performance, with a test accuracy of **85.77%** and an F1-score of **66%** for the positive class (income above $50K).

KNN achieved a test accuracy of 84.56%, while Gaussian Naive Bayes reached 82.83% after hyperparameter tuning.

Hyperparameter tuning significantly improved Naive Bayes performance, whereas the improvements for KNN and SVM were relatively small.

The ensemble methods produced comparable results but did not outperform the best individual model. Averaging binary predictions from three classifiers produced the same classification results as majority voting.

Overall, SVM provided the best performance among the evaluated models. However, identifying individuals with income above $50K remained more challenging than identifying the other class.

## Libraries

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Plotly

## How to Run

The notebook was developed using Google Colab.

1. Open the notebook in Google Colab.
2. Mount Google Drive if required.
3. Update the dataset paths according to your environment.
4. Run the notebook cells in order.
