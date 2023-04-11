# Reading Notes: Locally Weighted Regression, Probabilistic Interpretation, Logistic Regression, and Newton's Method

## Locally Weighted Regression (Loess/LOWESS)

**Concepts:**

* Non-parametric regression method that fits a smooth curve to data points.
* Does not assume a global function for the entire dataset but instead fits local functions to subsets of data points.
* Reduces the influence of outliers and captures local patterns.

**Basic Algorithm:**

1. For each data point, fit a weighted least-squares regression model to its neighbors.
2. Assign weights to the neighbors based on their distance from the target point, with higher weights for closer points.
3. Compute the estimated value at the target point using the fitted local model.
4. Repeat steps 1-3 for all data points to obtain a smooth curve.

**Use Cases:**

* Exploratory data analysis to identify trends and patterns.
* Smoothing noisy data in time series analysis and signal processing.
* Non-linear regression when the global function is unknown or complex.

***

## Parametric and Non-parametric Learning Algorithms

**Parametric Algorithms:**

* Assume a specific form or function for the underlying relationship between variables.
* Require estimating a fixed number of parameters from the data.
* Examples: Linear regression, logistic regression.

**Non-parametric Algorithms:**

* Do not assume a specific form or function for the underlying relationship.
* Estimate an arbitrary function based on the data without a fixed number of parameters.
* Examples: Locally weighted regression, k-Nearest Neighbors, decision trees.

***

## Probabilistic Interpretation

**Concepts:**

* Provides a probability-based framework for understanding and optimizing learning algorithms.
* Involves modeling the distribution of the target variable conditioned on the input features.
* Enables quantifying uncertainty and making decisions under uncertainty.

**Use Cases:**

* Bayesian inference for updating beliefs in light of new data.
* Model evaluation and comparison using likelihood or Bayesian Information Criterion (BIC).
* Probabilistic classification and regression, such as logistic regression or Gaussian processes.

***

## Logistic Regression

**Concepts:**

* Logistic regression is a parametric classification algorithm used to model the probability of a binary outcome.
* Uses the logistic function (sigmoid function) to transform a linear combination of input features into a probability.
* Suitable for binary classification tasks and can be extended to multi-class classification using techniques like one-vs-rest.

**Basic Algorithm:**

* Model the probability of the positive class as `P(y=1|x) = 1 / (1 + exp(-(b0 + b1*x1 + ... + bn*xn)))`.
* Estimate the coefficients `b0`, `b1`, ..., `bn` by maximizing the log-likelihood of the observed data.
* Classify a new instance by calculating the estimated probability and comparing it to a threshold (e.g., 0.5).

**Use Cases:**

* Predicting customer churn based on usage patterns and demographics.
* Diagnosing diseases based on medical test results and patient history.
* Detecting spam emails based on textual features and sender information.

***

## Newton's Method

**Concepts:**

* Newton's method is an optimization algorithm for finding the roots (zeros) of a real-valued function.
* Iteratively refines an initial guess using the function's derivatives.
* Converges quadratically when close to the root, making it faster than gradient descent in some cases.

**Basic Algorithm:**

1. Initialize a guess for the root of the function.
2. Calculate the first and second derivatives of the function with respect to the variable.
3. Update the guess by subtracting the ratio of the function value to its first derivative: `x_new = x_old - f(x_old) / f'(x_old)`.
4. Repeat steps 2 and 3 until convergence or a maximum number of iterations.
