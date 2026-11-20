
# Classification Models on Glass Dataset

## Overview

This project focuses on multi-class classification using the **Glass Identification Dataset**. Three machine learning algorithms are implemented and evaluated:

- Logistic Regression
- Decision Tree
- Random Forest

The main objective is to compare their classification performance, investigate the effect of hyperparameter tuning, and evaluate model stability using Stratified K-Fold Cross-Validation.

## Dataset

The Glass Identification dataset contains 214 samples and 10 columns:

- **9 numerical features:** RI, Na, Mg, Al, Si, K, Ca, Ba, and Fe.
- **1 target variable:** Target, representing the glass class.

The dataset contains six classes: 1, 2, 3, 5, 6, and 7.

There are no missing values in the dataset.

## Project Workflow

### 1. Data Loading and Exploration

- Loaded the dataset using Pandas.
- Inspected dataset dimensions, data types, and missing values.
- Examined target class distribution.
- Analyzed feature correlations using a correlation heatmap.

### 2. Data Preprocessing

- Separated the independent features (X) from the target variable (y).
- Split the dataset into training and testing sets using an 80/20 ratio.
- Used stratified sampling to preserve class proportions.
- Applied StandardScaler to standardize the features.

| Dataset | Number of Samples |
|---|---:|
| Training Set | 171 |
| Test Set | 43 |

### 3. Model Development and Evaluation

Three classification algorithms were trained and evaluated.

#### 3.1 Logistic Regression

- Implemented Logistic Regression with L2 regularization.
- Evaluated the model using Accuracy, Precision, Recall, F1-score, and Confusion Matrix.
- Applied Stratified 5-Fold Cross-Validation using Accuracy and Macro F1-score.

#### 3.2 Decision Tree

- Trained a Decision Tree classifier with a maximum depth of 5.
- Compared training and testing accuracy to investigate potential overfitting.
- Extracted and visualized decision rules.
- Analyzed feature importance.
- Examined the relationship between tree depth and model accuracy.
- Used GridSearchCV to tune hyperparameters and control model complexity.
- Evaluated the model using Stratified 5-Fold Cross-Validation.

#### 3.3 Random Forest

- Implemented a Random Forest classifier with 100 estimators.
- Evaluated its classification performance.
- Applied GridSearchCV for hyperparameter optimization.
- Compared the tuned and untuned models.
- Used Stratified 5-Fold Cross-Validation to assess model performance and stability.

## Model Evaluation and Results

### 1. Test Set Performance

The following table compares the performance of the models before and after hyperparameter tuning.

| Model | Approach | Accuracy | Macro Precision | Macro Recall | Macro F1-score |
|---|---|---:|---:|---:|---:|
| Logistic Regression | Default Configuration | 74.42% | 66% | 70% | 66% |
| Decision Tree | Before Tuning | 74.42% | 70% | 79% | 73% |
| Decision Tree | After Tuning | 69.77% | 46% | 53% | 49% |
| Random Forest | Before Tuning | 83.72% | 88% | 83% | 84% |
| Random Forest | After Tuning | **86.05%** | 84.13% | **93.17%** | **88%** |

*Note: Hyperparameter tuning results for Logistic Regression are not included because no GridSearchCV experiment was reported for this model.*

### 2. Hyperparameter Tuning

GridSearchCV with 5-fold cross-validation was used to optimize the Decision Tree and Random Forest models.

**Decision Tree – Best Parameters**

| Parameter | Best Value |
|---|---|
| Criterion | gini |
| Max Depth | 3 |
| Min Samples Split | 2 |
| Min Samples Leaf | 4 |
| Best CV Accuracy | 68.45% |

**Random Forest – Best Parameters**

| Parameter | Best Value |
|---|---|
| Number of Estimators | 50 |
| Max Depth | 10 |
| Min Samples Split | 2 |
| Min Samples Leaf | 1 |

The tuned Random Forest achieved a test accuracy of 86.05%, improving upon its initial accuracy of 83.72%.

In contrast, hyperparameter tuning reduced the Decision Tree test accuracy from 74.42% to 69.77%.

### 3. Stratified 5-Fold Cross-Validation

Stratified 5-Fold Cross-Validation was performed on the training set to evaluate model performance across different data partitions.

| Model | Mean Accuracy | Accuracy Std | Mean Macro F1 | Macro F1 Std |
|---|---:|---:|---:|---:|
| Logistic Regression | 61.36% | 8.55% | 45.31% | 12.72% |
| Decision Tree | 60.81% | 4.85% | - | - |
| Random Forest | **74.77%** | 8.67% | - | - |

Random Forest achieved the highest mean cross-validation accuracy among the three models.

However, the variation across folds indicates that model performance is somewhat sensitive to the training and validation samples.

### 4. Overall Model Comparison

Based on the experimental results:

- **Logistic Regression** achieved 74.42% test accuracy but showed lower performance in cross-validation.
- **Decision Tree** achieved the same initial test accuracy as Logistic Regression. Its decision rules and feature importance provided additional interpretability, but hyperparameter tuning did not improve its test performance.
- **Random Forest** outperformed the other models in both test accuracy and mean cross-validation accuracy. Hyperparameter tuning further improved its test accuracy to 86.05%.

The tuned Random Forest also achieved the highest Macro F1-score (88%) and Macro Recall (93.17%) among the reported test results.

## Limitations

Despite the promising results, several limitations should be considered:

- The dataset is relatively small, containing only 214 samples.
- Some target classes have very few observations, which makes their evaluation metrics less reliable.
- Cross-validation results show variation across folds, indicating sensitivity to data partitioning.
- Hyperparameter tuning did not improve every model.
- The difference between test accuracy and cross-validation accuracy suggests that model performance should be interpreted with caution.

## Conclusion

Among the evaluated classification algorithms, **Random Forest achieved the best overall performance** on the Glass Identification dataset.

After hyperparameter tuning, it reached 86.05% test accuracy and an 88% Macro F1-score. It also achieved the highest mean accuracy (74.77%) in Stratified 5-Fold Cross-Validation.

These results suggest that Random Forest was more effective than Logistic Regression and Decision Tree for this classification task.

However, due to the small dataset size and uneven class distribution, further evaluation on a larger and more representative dataset would be necessary to assess the models' generalization performance more reliably.
