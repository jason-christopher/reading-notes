# Module 1 - Create machine learning models

## Train and evaluate regression models

### What is regression?

**Regression** works by establishing a relationship between variables in the data that represent characteristics (known as the **features**) of the thing being observed, and the variable we're trying to predict (known as the **label**).

To train the model, we start with a data sample containing the **features**, as well as known values for the **label**. We'll then split this data sample into two subsets:

* A **training** dataset to which we'll apply an algorithm that determines a function encapsulating the relationship between the feature values and the known label values.
* A **validation** or **test** dataset that we can use to evaluate the model by using it to generate predictions for the label and comparing them to the actual known label values.

The use of historic data with known label values to train a model makes regression an example of **supervised machine learning**. There are lots of machine learning algorithms for supervised learning, and they can be broadly divided into two types:

* **Regression algorithms** - Algorithms that predict a `y` value that is a numeric value, such as the price of a house or the number of sales transactions.
* **Classification algorithms** - Algorithms that predict to which category, or class, an observation belongs. The `y` value in a classification model is a vector of probability values between 0 and 1, one for each class, indicating the probability of the observation belonging to each class.

We're comparing a predicted value (`ŷ`) with an observed value (`y`) we refer to the difference between them as the **residuals**. We can summarize the residuals for all of the validation data predictions to calculate the overall loss in the model as a measure of its **predictive performance**. There are multiple ways to calculate the predictive performance:

* **Mean Squared Error (MSE)** - Squaring the residuals has the effect of basing the calculation on absolute values (ignoring whether the difference is negative or positive) and giving more weight to larger differences.
  * MSE = Mean of ∑ (y - ŷ)^2
* **Root Mean Squared Error (RMSE)** - Calculating the square root of the MSE.
  * Square root of MSE
* **Coefficient of Determination (R^2 or R-Squared)** - Correlation between x and y squared. This produces a value between 0 and 1 that measures the amount of variance that can be explained by the model. Generally, the closer this value is to 1, the better the model predicts.

### Regression Model Training Example

Load the dataset and, clean up the data, identify the features and labels, and plot different graphs to identify relationships:

  ```python
  import pandas as pd
  import matplotlib.pyplot as plt
  import numpy as np

  # load the training dataset
  !wget https://raw.githubusercontent.com/MicrosoftDocs/mslearn-introduction-to-machine-learning/main/Data/ml-basics/daily-bike-share.csv
  bike_data = pd.read_csv('daily-bike-share.csv')

  # add a new column named day to the dataframe
  bike_data['day'] = pd.DatetimeIndex(bike_data['dteday']).day

  numeric_features = ['temp', 'atemp', 'hum', 'windspeed']
  bike_data[numeric_features + ['rentals']].describe()

  # Plot a histogram for each numeric feature
  for col in numeric_features:
      fig = plt.figure(figsize=(9, 6))
      ax = fig.gca()
      feature = bike_data[col]
      feature.hist(bins=100, ax = ax)
      ax.axvline(feature.mean(), color='magenta', linestyle='dashed', linewidth=2)
      ax.axvline(feature.median(), color='cyan', linestyle='dashed', linewidth=2)
      ax.set_title(col)
  plt.show()

  # plot a bar plot for each categorical feature count
  categorical_features = ['season','mnth','holiday','weekday','workingday','weathersit', 'day']

  for col in categorical_features:
      counts = bike_data[col].value_counts().sort_index()
      fig = plt.figure(figsize=(9, 6))
      ax = fig.gca()
      counts.plot.bar(ax = ax, color='steelblue')
      ax.set_title(col + ' counts')
      ax.set_xlabel(col) 
      ax.set_ylabel("Frequency")
  plt.show()

  # create scatter plots that show the intersection of feature and label values.
  for col in numeric_features:
    fig = plt.figure(figsize=(9, 6))
    ax = fig.gca()
    feature = bike_data[col]
    label = bike_data['rentals']
    correlation = feature.corr(label)
    plt.scatter(x=feature, y=label)
    plt.xlabel(col)
    plt.ylabel('Bike Rentals')
    ax.set_title('rentals vs ' + col + '- correlation: ' + str(correlation))
  plt.show()

  # plot a boxplot for the label by each categorical feature
  for col in categorical_features:
      fig = plt.figure(figsize=(9, 6))
      ax = fig.gca()
      bike_data.boxplot(column = 'rentals', by = col, ax = ax)
      ax.set_title('Label by ' + col)
      ax.set_ylabel("Bike Rentals")
  plt.show()
  ```

Now that we've explored the data, it's time to use it to train a regression model that uses the features we've identified as potentially predictive to predict the rentals label. The first thing we need to do is to separate the features we want to use to train the model from the label we want it to predict. To randomly split the data, we'll use the `train_test_split` function in the **scikit-learn** library. This library is one of the most widely used machine learning packages for Python.

  ```python
  from sklearn.model_selection import train_test_split

  # Separate features and labels
  X, y = bike_data[['season','mnth', 'holiday','weekday','workingday','weathersit','temp', 'atemp', 'hum', 'windspeed']].values, bike_data['rentals'].values
  print('Features:',X[:10], '\nLabels:', y[:10], sep='\n')
  ```

Now we have the following four datasets:

* **X_train**: The feature values we'll use to train the model
* **y_train**: The corresponding labels we'll use to train the model
* **X_test**: The feature values we'll use to validate the model
* **y_test**: The corresponding labels we'll use to validate the model

In **Scikit-Learn**, training algorithms are encapsulated in *estimators*, and in this case we'll use the **LinearRegression** estimator to train a linear regression model.

  ```python
  # Train the model
  from sklearn.linear_model import LinearRegression

  # Fit a linear regression model on the training set
  model = LinearRegression().fit(X_train, y_train)
  print (model)
  ```

We can quantify the residuals by calculating a number of commonly used evaluation metrics.

  ```python
  from sklearn.metrics import mean_squared_error, r2_score

  mse = mean_squared_error(y_test, predictions)
  print("MSE:", mse)

  rmse = np.sqrt(mse)
  print("RMSE:", rmse)

  r2 = r2_score(y_test, predictions)
  print("R2:", r2)
  ```

***

### Different Regression Models

* **Linear regression** - Simplest form of regression, with no limit to the number of features used. Linear regression comes in many forms - often named by the number of features used and the shape of the curve that fits. Not just the Linear Regression algorithm we used above (which is technically an **Ordinary Least Squares** algorithm), but other variants such as **Lasso** and **Ridge**.
* **Decision trees** - Algorithms that build a decision tree to reach a prediction. Uses a tree-based approach in which the features in the dataset are examined in a series of evaluations, each of which results in a branch in a decision tree based on the feature value. At the end of each series of branches are leaf-nodes with the predicted label value based on the feature values.
* **Ensemble algorithms** - Work by combining multiple base estimators to produce an optimal model, either by applying an aggregate function to a collection of base models (sometimes referred to a **bagging**) or by building a sequence of models that build on one another to improve predictive performance (referred to as **boosting**). Ensemble algorithms, such as **Random Forest**, are widely used in machine learning and science due to their strong prediction abilities.

Let's try training our regression model by using a **Lasso** algorithm. We can do this by just changing the estimator in the training code.

  ```python
  from sklearn.linear_model import Lasso

  # Fit a lasso model on the training set
  model = Lasso().fit(X_train, y_train)
  print (model, "\n")
  ```

Let's train a Decision Tree regression model using the bike rental data.

  ```python
  from sklearn.tree import DecisionTreeRegressor
  from sklearn.tree import export_text

  # Train the model
  model = DecisionTreeRegressor().fit(X_train, y_train)
  print (model, "\n")

  # Visualize the model tree
  tree = export_text(model)
  print(tree)
  ```

Let's try a **Random Forest** model, which applies an averaging function to multiple Decision Tree models for a better overall model.

  ```python
  from sklearn.ensemble import RandomForestRegressor

  # Train the model
  model = RandomForestRegressor().fit(X_train, y_train)
  print (model, "\n")
  ```

For good measure, let's also try a **boosting** ensemble algorithm. We'll use a **Gradient Boosting** estimator, which like a **Random Forest** algorithm builds multiple trees, but instead of building them all independently and taking the average result, each tree is built on the outputs of the previous one in an attempt to incrementally reduce the *loss* (error) in the model.

  ```python
  # Train the model
  from sklearn.ensemble import GradientBoostingRegressor

  # Fit a lasso model on the training set
  model = GradientBoostingRegressor().fit(X_train, y_train)
  print (model, "\n")
  ```

For any of the previous examples we can evaluate the model using the test data and plot the predicted vs actual visually.

  ```python
  # Evaluate the model using the test data
  predictions = model.predict(X_test)
  mse = mean_squared_error(y_test, predictions)
  print("MSE:", mse)
  rmse = np.sqrt(mse)
  print("RMSE:", rmse)
  r2 = r2_score(y_test, predictions)
  print("R2:", r2)

  # Plot predicted vs actual
  plt.scatter(y_test, predictions)
  plt.xlabel('Actual Labels')
  plt.ylabel('Predicted Labels')
  plt.title('Daily Bike Share Predictions')
  # overlay the regression line
  z = np.polyfit(y_test, predictions, 1)
  p = np.poly1d(z)
  plt.plot(y_test,p(y_test), color='magenta')
  plt.show()
  ```

***

### Improve models with hyperparameters & preprocessing data

**Hyperparameters** are values that change the way that the model is fit during these loops. Learning rate, for example, is a hyperparameter that sets how much a model is adjusted during each training cycle. A high learning rate means a model can be trained faster, but if it’s too high the adjustments can be so large that the model is never ‘finely tuned’ and not optimal. In machine learning, the term **parameters** refers to values that can be determined from data; values that you specify to affect the behavior of a training algorithm are more correctly referred to as **hyperparameters**.

**Preprocessing** refers to changes you make to your data before it is passed to the model (cleaning your dataset). It can also include changing the format of your data, so it's easier for the model to use.

* **Scaling features** - preprocessing step to scale features so they fall between zero and one.
* **Using categories as features** - representing categorical features such as 'bicycle', 'skateboard’ or 'car' as 0 or 1 values in one-hot vectors - vectors that have a 0 or 1 for each possible value. For example, bicycle, skateboard, and car might respectively be (1,0,0), (0,1,0), and (0,0,1).

SciKit-Learn provides a way to *tune* hyperparameters by trying multiple combinations and finding the best result for a given performance metric. Let's try using a grid search approach to try combinations from a grid of possible values for the **learning_rate** and **n_estimators** hyperparameters of the **GradientBoostingRegressor** estimator.

  ```python
  from sklearn.ensemble import GradientBoostingRegressor, RandomForestRegressor
  from sklearn.model_selection import GridSearchCV
  from sklearn.metrics import make_scorer, r2_score

  # Use a Gradient Boosting algorithm
  alg = GradientBoostingRegressor()

  # Try these hyperparameter values
  params = {
  'learning_rate': [0.1, 0.5, 1.0],
  'n_estimators' : [50, 100, 150]
  }

  # Find the best hyperparameter combination to optimize the R2 metric
  score = make_scorer(r2_score)
  gridsearch = GridSearchCV(alg, params, scoring=score, cv=3, return_train_score=True)
  gridsearch.fit(X_train, y_train)
  print("Best parameter combination:", gridsearch.best_params_, "\n")

  # Get the best model
  model=gridsearch.best_estimator_
  print(model, "\n")
  ```

We trained a model with data that was loaded straight from a source file, with only moderately successful results. In practice, it's common to perform some preprocessing of the data to make it easier for the algorithm to fit a model to it.

To apply these preprocessing transformations to the bike rental, we'll make use of a **Scikit-Learn** feature named **pipelines**. These enable us to define a set of preprocessing steps that end with an algorithm. You can then fit the entire pipeline to the data, so that the model encapsulates all of the preprocessing steps as well as the regression algorithm. This is useful, because when we want to use the model to predict values from new data, we need to apply the same transformations (based on the same statistical distributions and category encodings used with the training data).

  ```python
  # Train the model
  from sklearn.compose import ColumnTransformer
  from sklearn.pipeline import Pipeline
  from sklearn.impute import SimpleImputer
  from sklearn.preprocessing import StandardScaler, OneHotEncoder
  from sklearn.linear_model import LinearRegression
  import numpy as np

  # Define preprocessing for numeric columns (scale them)
  numeric_features = [6,7,8,9]
  numeric_transformer = Pipeline(steps=[
      ('scaler', StandardScaler())])

  # Define preprocessing for categorical features (encode them)
  categorical_features = [0,1,2,3,4,5]
  categorical_transformer = Pipeline(steps=[
      ('onehot', OneHotEncoder(handle_unknown='ignore'))])

  # Combine preprocessing steps
  preprocessor = ColumnTransformer(
      transformers=[
          ('num', numeric_transformer, numeric_features),
          ('cat', categorical_transformer, categorical_features)])

  # Create preprocessing and training pipeline
  pipeline = Pipeline(steps=[('preprocessor', preprocessor),
                            ('regressor', GradientBoostingRegressor())])

  # Or use a different estimator in the pipeline
  pipeline = Pipeline(steps=[('preprocessor', preprocessor),
                            ('regressor', RandomForestRegressor())])

  # fit the pipeline to train a linear regression model on the training set
  model = pipeline.fit(X_train, (y_train))
  print (model)

  # Display metrics
  mse = mean_squared_error(y_test, predictions)
  print("MSE:", mse)
  rmse = np.sqrt(mse)
  print("RMSE:", rmse)
  r2 = r2_score(y_test, predictions)
  print("R2:", r2)

  # Plot predicted vs actual
  plt.scatter(y_test, predictions)
  plt.xlabel('Actual Labels')
  plt.ylabel('Predicted Labels')
  plt.title('Daily Bike Share Predictions - Preprocessed')
  z = np.polyfit(y_test, predictions, 1)
  p = np.poly1d(z)
  plt.plot(y_test,p(y_test), color='magenta')
  plt.show()
  ```

We can save the model and load it whenever we need it, and use it to predict labels for new data. This is often called **scoring** or **inferencing**. The model's `predict` method accepts an array of observations, so you can use it to generate multiple predictions as a batch.

  ```python
  import joblib

  # Save the model as a pickle file
  filename = './bike-share.pkl'
  joblib.dump(model, filename)

  # Load the model from the file
  loaded_model = joblib.load(filename)

  # Create a numpy array containing a new observation (for example tomorrow's seasonal and weather forecast information)
  X_new = np.array([[1,1,0,3,1,1,0.226957,0.22927,0.436957,0.1869]]).astype('float64')
  print ('New sample: {}'.format(list(X_new[0])))

  # Use the model to predict tomorrow's rentals
  result = loaded_model.predict(X_new)
  print('Prediction: {:.0f} rentals'.format(np.round(result[0])))

  # An array of features based on five-day weather forecast
  X_new = np.array([[0,1,1,0,0,1,0.344167,0.363625,0.805833,0.160446],
                    [0,1,0,1,0,1,0.363478,0.353739,0.696087,0.248539],
                    [0,1,0,2,0,1,0.196364,0.189405,0.437273,0.248309],
                    [0,1,0,3,0,1,0.2,0.212122,0.590435,0.160296],
                    [0,1,0,4,0,1,0.226957,0.22927,0.436957,0.1869]])

  # Use the model to predict rentals
  results = loaded_model.predict(X_new)
  print('5-day rental predictions:')
  for prediction in results:
      print(np.round(prediction))
  ```

***

### Summary

You learned how regression can be used to create a machine learning model that predicts numeric values. You then used the scikit-learn framework in Python to train and evaluate a regression model.

While scikit-learn is a popular framework for writing code to train regression models, you can also create machine learning solutions for regression using the graphical tools in Microsoft Azure Machine Learning. You can learn more about no-code development of regression models using Azure Machine Learning in the Create a Regression Model with Azure Machine Learning designer module.

Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/train-evaluate-regression-models/)
