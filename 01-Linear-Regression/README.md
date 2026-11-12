# Linear Regression From Scratch

## Overview

This project focuses on understanding and implementing Linear Regression from scratch using Python and NumPy. Both **Univariate** and **Multivariate Linear Regression** are implemented using Gradient Descent.

The custom implementation is also compared with the built-in Linear Regression model from Scikit-learn.

The main objectives are to understand the mathematical foundations of Linear Regression, implement the optimization algorithm, evaluate model performance, and investigate the effects of hyperparameters.

## Datasets

Three datasets are provided for this exercise:

- `univariateData.dat`: Contains one input feature and one target variable, used for Univariate Linear Regression.
- `multivariateData.dat`: Contains multiple input features (two features in this exercise) and one target variable, used for Multivariate Linear Regression.
- `holdout.npz`: Contains holdout data used to evaluate the Multivariate Linear Regression models.

The target variable represents house prices.

## Implementation

### 1. Univariate Linear Regression

Univariate Linear Regression was implemented from scratch using Gradient Descent.

The model learns two parameters:

- `theta0`: Intercept (bias).
- `theta1`: Coefficient of the input feature.

The implementation includes:

- Prediction using the linear hypothesis.
- Cost Function calculation.
- Gradient Descent optimization.
- Visualization of the data and fitted regression line.
- Visualization of the Cost Function and optimization process.

### 2. Multivariate Linear Regression

Multivariate Linear Regression was implemented from scratch using two input features.

The model learns three parameters: one intercept and two feature coefficients.

Two implementations of Gradient Descent were developed:

- **Low-Speed Implementation:** Uses loops to calculate predictions, errors, and gradients.
- **High-Speed Implementation:** Uses vectorized NumPy operations for more efficient computation.

### 3. Model Evaluation

The custom Multivariate Linear Regression model was evaluated using the holdout dataset.

The following evaluation metrics were calculated:

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)

### 4. Hyperparameter Tuning

The effects of the following hyperparameters on model performance were investigated:

- **Number of Iterations (`n_iter`)**
- **Learning Rate (`alpha`)**
- **Combined Tuning of `alpha` and `n_iter`**

The best hyperparameter combination within the tested ranges was:

| Hyperparameter | Best Value |
|---|---:|
| Learning Rate (`alpha`) | 0.01 |
| Number of Iterations (`n_iter`) | 210 |

### 5. Scikit-learn Implementation

The built-in `LinearRegression` model from `sklearn.linear_model` was used to train and evaluate a Multivariate Linear Regression model.

Its performance was compared with the custom implementation.

## Results

| Evaluation Metric | Custom Model | Scikit-learn |
|---|---:|---:|
| MSE | 2,598,961,047.73 | 2,306,007,735.74 |
| RMSE | 50,980.01 | 48,020.91 |
| MAE | — | 38,658.82 |

Scikit-learn achieved lower MSE and RMSE values in the obtained results.

**Note:** The comparison is not entirely consistent because different standardization procedures were used for the holdout data. A fair comparison requires applying the same training-set scaling parameters to both models.

## Technologies and Libraries

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

## Key Takeaways

- Understanding Univariate and Multivariate Linear Regression.
- Implementing Gradient Descent from scratch.
- Comparing loop-based and vectorized implementations.
- Understanding the role of learning rate and number of iterations.
- Visualizing the regression line and Cost Function.
- Evaluating regression models using MSE, RMSE, and MAE.
- Comparing a custom implementation with Scikit-learn.
