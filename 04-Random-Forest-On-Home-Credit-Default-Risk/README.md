# Home Credit Default Risk Prediction

## Overview
This project focuses on predicting loan repayment difficulties using applicant data from the Home Credit dataset. The goal is to identify clients who are likely to have difficulties repaying their loans, helping financial institutions improve credit risk assessment and lending decisions.

A **Random Forest Classifier** is used to predict whether a client is likely to experience payment difficulties.

## Dataset
- **Dataset:** Home Credit Application Data (`application_data.csv`)
- **Rows:** 307,511
- **Original Features:** 122
- **Target Variable:** `TARGET`
  - `0`: No payment difficulties
  - `1`: Payment difficulties

The dataset contains demographic, financial, employment, housing, and credit-related information.

## Project Workflow

### 1. Exploratory Data Analysis (EDA)
- Dataset structure and statistical analysis
- Missing value analysis
- Target distribution and class imbalance
- Exploring relationships between loan repayment status and applicant characteristics
- Correlation analysis

### 2. Data Preprocessing
- Train-test split using stratified sampling
- Median imputation for numerical features
- Most frequent imputation for categorical features
- One-hot encoding of categorical variables

### 3. Feature Engineering
- Polynomial features using external credit scores
- Domain-based feature creation:
  - `CREDIT_INCOME_PERCENT`
  - `ANNUITY_INCOME_PERCENT`
  - `CREDIT_TERM`
  - `DAYS_EMPLOYED_PERCENT`

### 4. Model Training
- Random Forest Classifier
- Class weighting to address class imbalance
- Evaluation using ROC curve and ROC-AUC

### 5. Hyperparameter Tuning
- RandomizedSearchCV
- Cross-validation
- F1-score optimization

### 6. Feature Selection
- Random Forest feature importance
- Selecting the top 10 features
- Training and evaluating a reduced-feature model

### 7. Threshold Optimization
- Classification threshold optimization using G-Mean
- Comparing default and optimized thresholds
- Evaluating the trade-off between Recall and Precision

### 8. Model Comparison
Comparing different Random Forest configurations based on:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- G-Mean

## Results

| Model | Features | Accuracy | Precision (Class 1) | Recall (Class 1) | F1 (Class 1) | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Original RF (0.5) | 248 | 0.72 | 0.17 | 0.62 | 0.7365 |
| Original RF (Optimal) | 248 | 0.67 | 0.15 | 0.25 | — |
| Tuned RF (0.5) | 248 | 0.80 | 0.19 | 0.47 | 0.7284 |
| Top 10 RF (0.5) | 10 | 0.71 | 0.17 | 0.63 | 0.7383 |
| Top 10 RF (Optimal) | 10 | 0.69 | 0.16 | 0.66 | — |

## Key Findings
- The tuned Random Forest achieved the highest accuracy and F1-score for class 1, although its recall was lower.
- Threshold optimization increased Recall for the default class, helping identify more applicants at risk of payment difficulties.
- The top 10 features model achieved comparable performance to the full-feature model while using significantly fewer features.
- External credit scores (`EXT_SOURCE_1`, `EXT_SOURCE_2`, and `EXT_SOURCE_3`) were among the most important predictors.

## Business Recommendations
- Use model predictions to support credit risk assessment and prioritize high-risk applicants for further review.
- Pay particular attention to external credit scores and other influential features.
- Adjust the classification threshold according to business priorities and the trade-off between missed defaults and false alarms.
- Predictions should support human decision-making rather than automatically determine loan approval or rejection.

## Conclusion
Random Forest was able to identify patterns associated with loan repayment difficulties. Feature selection reduced the number of features from 248 to 10 while maintaining comparable performance.

However, class 1 precision remains low, and further improvements in model performance, validation, and fairness assessment are needed before real-world deployment.

