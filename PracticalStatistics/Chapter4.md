# Chapter 4: Regression and Prediction

## Simple Linear Regression

**Simple linear regression** is a statistical method that models the relationship between a single predictor variable and a continuous response variable. The model is defined by the equation:

`y = β₀ + β₁x + ε`

where `y` is the response variable, `x` is the predictor variable, `β₀` is the intercept, `β₁` is the slope, and `ε` is the error term.

In Python, we can use the `statsmodels` or `scikit-learn` libraries to perform simple linear regression:

```python
import numpy as np
import statsmodels.api as sm

# Example data
x = np.array([1, 2, 3, 4, 5])
y = np.array([2, 4, 5, 4, 5])

# Perform simple linear regression using statsmodels
x = sm.add_constant(x)
model = sm.OLS(y, x).fit()
```

### Use Case

A real estate analyst wants to model the relationship between the square footage of a house and its selling price. They can use simple linear regression to estimate the effect of square footage on the selling price and make predictions for new houses.

## Multiple Linear Regression

**Multiple linear regression** extends simple linear regression to model the relationship between multiple predictor variables and a continuous response variable. The model is defined by the equation:

`y = β₀ + β₁x₁ + β₂x₂ + ... + βₚxₚ + ε`

where `y` is the response variable, `x₁, x₂, ..., xₚ` are the predictor variables, `β₀` is the intercept, `β₁, β₂, ..., βₚ` are the coefficients, and `ε` is the error term.

In Python, we can use the `statsmodels` or `scikit-learn` libraries to perform multiple linear regression:

```python
import pandas as pd
from sklearn.linear_model import LinearRegression

# Example data
data = pd.DataFrame({"x1": [1, 2, 3, 4, 5], "x2": [2, 3, 1, 5, 4], "y": [2, 4, 5, 4, 5]})

# Perform multiple linear regression using scikit-learn
X = data[["x1", "x2"]]
y = data["y"]
model = LinearRegression().fit(X, y)
```

### Use Case

The real estate analyst now wants to consider additional factors, such as the number of bedrooms and bathrooms, to improve their house price predictions. They can use multiple linear regression to model the relationship between these predictor variables and the selling price.

## Polynomial Regression

**Polynomial regression** is a form of linear regression in which the relationship between the predictor variable and the response variable is modeled as an _n_-th degree polynomial. Polynomial regression can be used to model nonlinear relationships between variables.

In Python, we can use the `numpy` and `scikit-learn` libraries to perform polynomial regression:

```python
from sklearn.preprocessing import PolynomialFeatures

# Example data
x = np.array([1, 2, 3, 4, 5]).reshape(-1, 1)
y = np.array([2, 4, 5, 4, 5])

# Perform polynomial regression using scikit-learn
poly_features = PolynomialFeatures(degree=2, include_bias=False)
x_poly = poly_features.fit_transform(x)

model = LinearRegression().fit(x_poly, y)
```

### Use Case

An environmental scientist is analyzing the relationship between the concentration of a pollutant and the mortality rate of a species. Since the relationship is not linear, they can use polynomial regression to model the nonlinear association between the variables and make predictions for different pollution levels.

## Stepwise Regression

**Stepwise regression** is a method for selecting the most relevant predictor variables in a multiple linear regression model. There are three main types of stepwise regression:

- **Forward selection**: Starts with an empty model and adds predictors one at a time, selecting the predictor that leads to the greatest improvement in model fit.
- **Backward elimination**: Starts with a full model and removes predictors one at a time, removing the predictor that leads to the smallest deterioration in model fit.
- **Bidirectional elimination**: Combines forward selection and backward elimination, iteratively adding and removing predictors based on their contribution to the model fit.

In Python, we can use the `statsmodels` library to perform stepwise regression:

```python
import statsmodels.formula.api as smf

# Example data
data = pd.DataFrame({"x1": [1, 2, 3, 4, 5], "x2": [2, 3, 1, 5, 4], "x3": [3, 1, 4, 2, 5], "y": [2, 4, 5, 4, 5]})

# Perform stepwise regression using statsmodels
def stepwise_selection(data, response, initial_list, sl_in=0.05, sl_out=0.05):
    # ... stepwise regression implementation ...

best_features = stepwise_selection(data, "y", ["x1", "x2", "x3"])
```

### Use Case

A marketing analyst wants to identify the most important factors affecting the success of an advertising campaign. They can use stepwise regression to iteratively select the most relevant predictor variables and build a parsimonious model for predicting campaign success.

## Ridge Regression

**Ridge regression** is a regularization technique that addresses the problem of multicollinearity in multiple linear regression by adding a penalty term to the loss function. The penalty term is proportional to the sum of the squared coefficients and shrinks the coefficients towards zero. Ridge regression can help prevent overfitting and improve model generalization.

In Python, we can use the `scikit-learn` library to perform ridge regression:

```python
from sklearn.linear_model import Ridge

# Example data
X = data[["x1", "x2", "x3"]]
y = data["y"]

# Perform ridge regression using scikit-learn
model = Ridge(alpha=1).fit(X, y)
```

### Use Case

A financial analyst is building a model to predict stock returns based on multiple economic indicators. Since some of the indicators are highly correlated, they can use ridge regression to address multicollinearity and improve the model's generalization to new data.

## Lasso Regression

**Lasso regression** (Least Absolute Shrinkage and Selection Operator) is another regularization technique that adds a penalty term to the loss function, similar to ridge regression. The penalty term is proportional to the sum of the absolute values of the coefficients. Lasso regression encourages sparsity in the model by shrinking some coefficients to exactly zero, effectively performing variable selection.

In Python, we can use the `scikit-learn` library to perform lasso regression:

```python
from sklearn.linear_model import Lasso

# Example data
X = data[["x1", "x2", "x3"]]
y = data["y"]

# Perform lasso regression using scikit-learn
model = Lasso(alpha=1).fit(X, y)
```

### Use Case

A genomics researcher is building a model to predict the expression of a target gene based on the expression of thousands of other genes. They can use lasso regression to select a small number of most relevant genes and build a sparse model for gene expression prediction.

## Generalized Linear Models

**Generalized linear models** (GLMs) extend linear regression to model the relationship between multiple predictor variables and a non-continuous response variable. GLMs use a link function to connect the linear predictor to the response variable's distribution, which can be any distribution in the exponential family (e.g., Gaussian, Poisson, or binomial).

In Python, we can use the `statsmodels` library to fit a generalized linear model:

```python
import statsmodels.api as sm

# Example data
data = pd.DataFrame({"x1": [1, 2, 3, 4, 5], "x2": [2, 3, 1, 5, 4], "y": [0, 1, 1, 1, 0]})

# Perform logistic regression (a type of GLM) using statsmodels
X = sm.add_constant(data[["x1", "x2"]])
y = data["y"]
model = sm.GLM(y, X, family=sm.families.Binomial()).fit()
```

### Use Case

A medical researcher is building a model to predict the probability of a patient developing a specific disease based on their age, lifestyle, and genetic factors. They can use a generalized linear model with a logistic link function to model the binary response variable (disease presence) and make predictions for individual patients.

## Regression Trees

**Regression trees** are a type of decision tree that can be used for regression problems. They recursively partition the data into subsets based on the values of the predictor variables and fit a constant model (e.g., the mean of the response variable) in each leaf node.

In Python, we can use the `scikit-learn` library to fit a regression tree:

```python
from sklearn.tree import DecisionTreeRegressor

# Example data
X = data[["x1", "x2"]]
y = data["y"]

# Fit a regression tree using scikit-learn
model = DecisionTreeRegressor(max_depth=2).fit(X, y)
```

### Use Case

An energy analyst wants to model the relationship between weather conditions and electricity demand in a region. They can use a regression tree to capture complex, nonlinear relationships between temperature, humidity, wind speed, and electricity demand, and make predictions for different weather conditions.

## Model Evaluation

**Model evaluation** is the process of assessing the performance of a regression model using various metrics, such as the **coefficient of determination** (R²), **mean squared error** (MSE), **mean absolute error** (MAE), or **root mean squared error** (RMSE).

In Python, we can use the `scikit-learn` library to calculate these metrics:

```python
from sklearn.metrics import r2_score, mean_squared_error, mean_absolute_error

# Example data and model
X = data[["x1", "x2"]]
y = data["y"]
model = LinearRegression().fit(X, y)

# Predictions
y_pred = model.predict(X)

# Model evaluation
r2 = r2_score(y, y_pred)
mse = mean_squared_error(y, y_pred)
mae = mean_absolute_error(y, y_pred)
rmse = np.sqrt(mse)
```

### Use Case

A data scientist has built several models to predict customer churn for a subscription-based service. They can use model evaluation metrics like R², MSE, MAE, and RMSE to compare the performance of the models and choose the best one for their specific problem.

## Residual Analysis

**Residual analysis** is a diagnostic tool for assessing the quality of a regression model by examining the residuals (i.e., the differences between the observed and predicted values). Residual analysis can help identify issues such as nonlinearity, heteroscedasticity, and outliers.

In Python, we can use the `matplotlib` library to create residual plots:

```python
import matplotlib.pyplot as plt

# Example data and model
X = data[["x1", "x2"]]
y = data["y"]
model = LinearRegression().fit(X, y)

# Predictions and residuals
y_pred = model.predict(X)
residuals = y - y_pred

# Residual plot
plt.scatter(y_pred, residuals)
plt.xlabel("Predicted Values")
plt.ylabel("Residuals")
plt.axhline(y=0, color="r", linestyle="--")
plt.show()
```

### Use Case

A transportation analyst has built a model to predict the travel time between two locations based on the time of day, distance, and traffic conditions. They can use residual analysis to check the assumptions of their model and identify any systematic patterns that might suggest the need for a more complex model or additional predictor variables.

## Summary

In summary, Chapter 4 of Practical Statistics for Data Scientists - Second Edition provides a comprehensive overview of regression and prediction techniques, including simple and multiple linear regression, polynomial regression, stepwise regression, ridge and lasso regression, generalized linear models, regression trees, model evaluation, and residual analysis. Understanding these concepts and techniques is essential for data scientists to build accurate and interpretable models for a wide range of prediction tasks.
