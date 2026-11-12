
# Multivariate Linear Regression

## Overview
This project focuses on implementing Multivariate Linear Regression from scratch using Python and comparing its performance with the built-in Linear Regression model from Scikit-learn.

The main objective is to understand the fundamentals of Linear Regression, implement Gradient Descent, evaluate model performance, and investigate the effect of hyperparameters on prediction accuracy.

## Dataset
The dataset contains two input features and one target variable representing house prices.

- `multivariateData.dat`: Training dataset.
- `holdout.npz`: Holdout dataset used for model evaluation.

## Implementation

### 1. Linear Regression from Scratch
A custom Linear Regression class was implemented with the following methods:

- `fit()`: Trains the model using Gradient Descent.
- `predict()`: Generates predictions.
- `computeCost()`: Calculates the Cost Function.
- `gradientDescent()`: Updates model parameters iteratively.

Two implementations of Gradient Descent were developed:

- **Low-Speed Implementation:** Uses loops to calculate predictions, errors, and gradients.
- **High-Speed Implementation:** Uses vectorized NumPy operations for more efficient computation.

### 2. Model Evaluation
The custom model was evaluated using:

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)

### 3. Hyperparameter Tuning
The effects of the following hyperparameters were investigated:

- **Number of Iterations (`n_iter`)**
- **Learning Rate (`alpha`)**
- **Combined Tuning of `alpha` and `n_iter`**

The best hyperparameter combination within the tested ranges was:

| Hyperparameter | Best Value |
|---|---:|
| Learning Rate (`alpha`) | 0.01 |
| Number of Iterations (`n_iter`) | 210 |

### 4. Scikit-learn Implementation
The built-in `LinearRegression` class from `sklearn.linear_model` was used to train another model and compare its performance with the custom implementation.

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

- Understanding the mathematical foundations of Multivariate Linear Regression.
- Implementing Gradient Descent from scratch.
- Comparing loop-based and vectorized implementations.
- Understanding the role of learning rate and number of iterations.
- Evaluating regression models using MSE, RMSE, and MAE.
- Comparing a custom implementation with Scikit-learn.

