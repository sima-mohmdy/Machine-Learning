# Home Credit Default Risk Prediction

## Overview
This project focuses on predicting clients who may have difficulty repaying their loans using machine learning techniques. A Random Forest classifier is used to predict the probability of payment difficulties based on applicants' financial, demographic, and credit-related information.

## Dataset
The dataset used in this project is the **Home Credit Default Risk** dataset.

- **Dataset file:** `application_data.csv`
- **Number of records:** 307,511
- **Number of original features:** 122
- **Target variable:** `TARGET`
  - `0`: No payment difficulties
  - `1`: Payment difficulties

The dataset is not included in this repository due to its large size.

Download the dataset from Kaggle:

[Home Credit Default Risk Dataset](https://www.kaggle.com/competitions/home-credit-default-risk/data)

## Project Workflow

### 1. Exploratory Data Analysis (EDA)
- Examining dataset structure and statistical information
- Analyzing missing values
- Investigating target class distribution
- Visualizing feature distributions and relationships
- Exploring correlations between features

### 2. Data Preprocessing
- Stratified train-test split
- Handling missing values using median imputation for numerical features and most-frequent imputation for categorical features
- Encoding categorical variables using One-Hot Encoding

### 3. Feature Engineering
Creating additional features based on existing variables, including:

- `CREDIT_INCOME_PERCENT`
- `ANNUITY_INCOME_PERCENT`
- `CREDIT_TERM`
- `DAYS_EMPLOYED_PERCENT`

Polynomial features were also explored during the analysis.

### 4. Model Training
- Random Forest Classifier
- Handling class imbalance using class weights
- Model evaluation using classification metrics and ROC-AUC

### 5. Hyperparameter Tuning
- RandomizedSearchCV
- Cross-validation
- F1-score-based parameter selection

### 6. Feature Selection
- Ranking features based on Random Forest feature importance
- Selecting the top 10 features
- Training a reduced model and comparing its performance with the original model

### 7. Threshold Optimization
- Finding an optimal classification threshold using G-Mean
- Comparing default and optimized thresholds
- Analyzing the trade-off between precision and recall

### 8. Model Comparison

Comparing models using Accuracy, Precision, Recall, F1-score, and ROC-AUC.

| Model | Features | Accuracy | Precision (Class 1) | Recall (Class 1) | F1 (Class 1) | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Original RF (0.5) | 248 | 0.72 | 0.17 | 0.62 | 0.7365 |
| Original RF (Optimal) | 248 | 0.67 | 0.15 | 0.25 | — |
| Tuned RF (0.5) | 248 | 0.80 | 0.19 | 0.47 | 0.7284 |
| Top 10 RF (0.5) | 10 | 0.71 | 0.17 | 0.63 | 0.7383 |
| Top 10 RF (Optimal) | 10 | 0.69 | 0.16 | 0.66 | — |

## Key Findings

- The tuned Random Forest achieved the highest accuracy and F1-score for class 1, but with lower recall.
- Threshold optimization improved recall for clients with payment difficulties.
- The Top 10 feature model achieved comparable performance to the original model using significantly fewer features.
- External credit scores (`EXT_SOURCE_1`, `EXT_SOURCE_2`, and `EXT_SOURCE_3`) were among the most important features.

## Business Insights

- The model can support credit risk assessment and help prioritize applicants for further review.
- Threshold selection can be adjusted based on business requirements and the cost of false positives and false negatives.
- Predictions should be used as decision-support tools rather than as the sole basis for loan approval or rejection.

## Limitations

- The dataset is imbalanced, with relatively few applicants experiencing payment difficulties.
- The model has low precision for class 1, meaning many predicted high-risk applicants are not actual high-risk cases.
- Further improvements in model performance, validation, and fairness analysis are needed before real-world deployment.

## Conclusion

The Random Forest model was able to identify patterns associated with loan repayment difficulties. Feature selection reduced the number of features from 248 to 10 while maintaining comparable predictive performance.

The results highlight the importance of class imbalance handling, feature selection, and threshold optimization in credit risk prediction.


