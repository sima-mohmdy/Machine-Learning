
# META-DES for Breast Cancer Classification

## Overview

This project implements **META-DES (Meta-Learning for Dynamic Ensemble Selection)** to classify breast cancer tumors as benign or malignant using the Breast Cancer Wisconsin Diagnostic dataset.

The main goal is to build a pool of classifiers, apply dynamic ensemble selection, evaluate the model, and investigate the effect of hyperparameter optimization on classification performance.

## Dataset

The project uses the Breast Cancer Wisconsin Diagnostic dataset.

- **Number of samples:** 569
- **Number of original features:** 30 numerical features
- **Target variable:** `diagnosis`
  - `0`: Benign
  - `1`: Malignant

The `id` and `Unnamed: 32` columns were removed during preprocessing. The target variable was encoded using `LabelEncoder`.

## Methodology

The project follows these steps:

1. **Exploratory Data Analysis (EDA)**
   - Dataset inspection and statistical analysis
   - Target distribution visualization
   - Missing values and duplicate checks
   - Feature relationship analysis using pair plots and correlation heatmaps

2. **Data Preprocessing**
   - Removing unnecessary columns
   - Encoding the target variable
   - Feature scaling

3. **META-DES Implementation**
   - Splitting the dataset into training, DSEL, and test subsets
   - Building a pool of 10 classifiers using `BaggingClassifier`
   - Using calibrated Perceptron models as base classifiers
   - Training and evaluating the META-DES model

4. **Model Evaluation**
   - Holdout evaluation
   - Stratified 5-fold cross-validation
   - Confusion matrix and classification report

5. **Hyperparameter Optimization**
   - Evaluating 24 parameter combinations
   - Using stratified 5-fold cross-validation
   - Selecting the best configuration based on mean accuracy

## Results

| Evaluation Method | Accuracy |
|---|---:|
| Initial META-DES (Holdout) | 93.62% |
| META-DES (5-Fold CV) | 96.49% ± 2.05% |
| Optimized META-DES (5-Fold CV) | 96.14% |
| Optimized META-DES (Holdout) | 94.15% |

### Best Hyperparameters

| Parameter | Value |
|---|---:|
| `k` | 7 |
| `Kp` | 3 |
| `Hc` | 1.0 |
| `selection_threshold` | 0.8 |
| `mode` | `hybrid` |

### Conclusion

META-DES achieved promising classification results on the Breast Cancer Wisconsin Diagnostic dataset. The initial model obtained 93.62% holdout accuracy, while the initial 5-fold cross-validation achieved 96.49% mean accuracy.

Hyperparameter optimization resulted in a best cross-validation accuracy of 96.14%. The optimized model achieved 94.15% accuracy in the holdout evaluation.

Detecting malignant cases remains particularly important, as false negative predictions may have serious consequences.

**Evaluation Note:** The hyperparameter search was performed on the complete dataset, including samples used in the holdout evaluation. Therefore, the optimized holdout result should not be interpreted as a fully independent estimate of generalization performance.

## Libraries and Tools

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- DESlib
- Google Colab

## Notebook

The complete implementation, visualizations, model evaluation, and hyperparameter optimization are available in:

`META-DES-on-Breast-Cancer-Dataset.ipynb`
