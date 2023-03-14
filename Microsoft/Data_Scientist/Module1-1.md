# Module 1 - Create machine learning models

## Explore and analyze data with Python

### Explore data with NumPy and Pandas

* **NumPy** - Python library that provides functionality comparable to mathematical tools such as MATLAB and R. Significantly simplifies the user experience and offers comprehensive mathematical functions.  

  ```python
  import numpy as np
  ```

* **Pandas** - popular Python library for data analysis and manipulation. Like a spreadsheet application for Python that provides easy-to-use functionality for data tables.  
  
  ```python
  import pandas as pd`
  ```

* **Jupyter notebooks** - popular way of running basic scripts using your web browser.

Data exploration and analysis is typically an iterative process, in which the data scientist takes a sample of data and performs the following kinds of tasks to analyze it and test hypotheses:

1. **Clean data** to handle errors, missing values, and other issues.
2. **Apply statistical techniques to better understand the data** and how the sample might be expected to represent the real-world population of data, allowing for random variation.
3. **Visualize data** to determine relationships between variables, and in the case of a machine learning project, identify features that are potentially predictive of the label.
4. Revise the hypothesis and repeat the process.

NumPy provides a lot of the functionality and tools you need to work with numbers, such as arrays of numeric values. However, when you start to deal with two-dimensional tables of data, the **Pandas** package offers a more convenient structure to work with: the **DataFrame**.

```python
df_students = pd.DataFrame({'Name': ['Dan', 'Joann', 'Pedro', 'Rosie', 'Ethan', 'Vicky', 'Frederic', 'Jimmie', 
                                     'Rhonda', 'Giovanni', 'Francesca', 'Rajab', 'Naiyana', 'Kian', 'Jenny',
                                     'Jakeem','Helena','Ismat','Anila','Skye','Daniel','Aisha'],
                            'StudyHours':student_data[0],
                            'Grade':student_data[1]})
```

* You can use the DataFrame's `loc` method to retrieve data for a specific index value. In addition to being able to use the `loc` method to find rows based on the index, you can use the `iloc` method to find rows based on their ordinal position in the DataFrame (regardless of the index). `iloc` identifies data values in a DataFrame by position, which extends beyond rows to columns. The `loc` method will return rows with index label in the list of values from 0 to 5, which includes 0, 1, 2, 3, 4, and 5 (six rows). However, the `iloc` method returns the rows in the positions included in the range 0 to 5. Since integer ranges don't include the upper-bound value, this includes positions 0, 1, 2, 3, and 4 (five rows). There are also many different ways in Pandas to achieve the same result (such as looking up a value).

  ```python
  # Get the data for index value 5
  df_students.loc[5]
  # Get the rows with index values from 0 to 5
  df_students.loc[0:5]
  # Get data in the first five rows
  df_students.iloc[0:5]

  # 4 different ways to look up data
  df_students.loc[df_students['Name']=='Aisha']
  df_students[df_students['Name']=='Aisha']
  df_students.query('Name=="Aisha"')
  df_students[df_students.Name == 'Aisha']
  ```

In many real-world scenarios, data is loaded from sources such as files. The DataFrame's `read_csv` method is used to load data from text files. 

  ```python
  !wget https://raw.githubusercontent.com/MicrosoftDocs/mslearn-introduction-to-machine-learning/main/Data/ml-basics/grades.csv
  df_students = pd.read_csv('grades.csv',delimiter=',',header='infer')
  df_students.head()
  ```

One of the most common issues data scientists need to deal with is incomplete or missing data. You can use the `isnull` method to identify which individual values are null. When the DataFrame is retrieved, the missing numeric values show up as **NaN** (not a number).

* One common approach is to impute replacement values. We can use the `fillna` method:

  ```python
  df_students.StudyHours = df_students.StudyHours.fillna(df_students.StudyHours.mean())
  ```

* Alternatively, it might be important to ensure that you only use data you know to be absolutely correct. You can drop rows or columns that contain null values by using the `dropna` method:

  ```python
  df_students = df_students.dropna(axis=0, how='any')
  ```

We can create a new column by creating a Pandas **Series** containing the pass/fail indicator (True or False), and then we'll concatenate that series as a new column (axis 1) in the DataFrame:

  ```python
  passes  = pd.Series(df_students['Grade'] >= 60)
  df_students = pd.concat([df_students, passes.rename("Pass")], axis=1)
  ```

***

### Visualize data

DataFrames provide a great way to explore and analyze tabular data, but sometimes a picture is worth a thousand rows and columns. The **Matplotlib** library provides the foundation for plotting data visualizations that can greatly enhance your ability to analyze the data.

  ```python
  # Ensure plots are displayed inline in the notebook
  %matplotlib inline

  from matplotlib import pyplot as plt

  # Create a bar plot of name vs grade
  plt.bar(x=df_students.Name, height=df_students.Grade)

  # Display the plot
  plt.show()
  ```

Note that we used the `pyplot` class from Matplotlib to plot the chart. This class provides many ways to improve the visual elements of the plot. A plot is technically contained within a **Figure**. In the previous examples, the figure was created implicitly for you, but you can create it explicitly with a specific size.

  ```python
  # Create a figure for 2 subplots (1 row, 2 columns)
  fig, ax = plt.subplots(1, 2, figsize = (10,4))

  # Create a bar plot of name vs grade on the first axis
  ax[0].bar(x=df_students.Name, height=df_students.Grade, color='orange')
  ax[0].set_title('Grades')
  ax[0].set_xticklabels(df_students.Name, rotation=90)

  # Create a pie chart of pass counts on the second axis
  pass_counts = df_students['Pass'].value_counts()
  ax[1].pie(pass_counts, labels=pass_counts)
  ax[1].set_title('Passing Grades')
  ax[1].legend(pass_counts.keys().tolist())

  # Add a title to the Figure
  fig.suptitle('Student Data')

  # Show the figure
  fig.show()
  ```

When examining a variable (for example, a sample of student grades), data scientists are particularly interested in its distribution (in other words, how are all the different grade values spread across the sample). The starting point for this exploration is often to visualize the data as a **histogram** and see how frequently each value for the variable occurs.

  ```python
  # Get the variable to examine
  var_data = df_students['Grade']

  # Create a Figure
  fig = plt.figure(figsize=(10,4))

  # Plot a histogram
  plt.hist(var_data)

  # Add titles and labels
  plt.title('Data Distribution')
  plt.xlabel('Value')
  plt.ylabel('Frequency')

  # Show the figure
  fig.show()
  ```

To understand the distribution better, we can examine **measures of central tendency**, which is a way of describing statistics that represent the "middle" of the data. The goal of this analysis is to try to find a "typical" value. Common ways to define the middle of the data include:

* The mean: A simple average based on adding together all of the values in the sample set and then dividing the total by the number of samples.
* The median: The value in the middle of the range of all of the sample values.
* The mode: The most commonly occurring value in the sample set (in some sample sets, there may be a tie for the most common value. In those cases, the dataset is described as bimodal or even multimodal).

  ```python
  # Get the variable to examine
  var = df_students['Grade']

  # Get statistics
  min_val = var.min()
  max_val = var.max()
  mean_val = var.mean()
  med_val = var.median()
  mod_val = var.mode()[0]

  print('Minimum:{:.2f}\nMean:{:.2f}\nMedian:{:.2f}\nMode:{:.2f}\nMaximum:{:.2f}\n'.format(min_val,
                                                                                          mean_val,
                                                                                          med_val,
                                                                                          mod_val,
                                                                                          max_val))

  # Create a Figure
  fig = plt.figure(figsize=(10,4))

  # Plot a histogram
  plt.hist(var)

  # Add lines for the statistics
  plt.axvline(x=min_val, color = 'gray', linestyle='dashed', linewidth = 2)
  plt.axvline(x=mean_val, color = 'cyan', linestyle='dashed', linewidth = 2)
  plt.axvline(x=med_val, color = 'red', linestyle='dashed', linewidth = 2)
  plt.axvline(x=mod_val, color = 'yellow', linestyle='dashed', linewidth = 2)
  plt.axvline(x=max_val, color = 'gray', linestyle='dashed', linewidth = 2)

  # Add titles and labels
  plt.title('Data Distribution')
  plt.xlabel('Value')
  plt.ylabel('Frequency')

  # Show the figure
  fig.show()
  ```

Another way to visualize the distribution of a variable is to use a **box plot** (sometimes called a box-and-whiskers plot). The box part of the plot shows where the inner two quartiles of the data reside. The whiskers extending from the box show the outer two quartiles. The line in the box indicates the median value.

  ```python
  # Get the variable to examine
  var = df_students['Grade']

  # Create a Figure
  fig = plt.figure(figsize=(10,4))

  # Plot a histogram
  plt.boxplot(var)

  # Add titles and labels
  plt.title('Data Distribution')

  # Show the figure
  fig.show()
  ```

If we have enough samples, we can calculate something called a **probability density function**, which estimates the distribution of grades for the full population. The `pyplot` class from Matplotlib provides a helpful plot function to show this density. As expected from the histogram of the sample, the density shows the characteristic "bell curve" of what statisticians call a **normal distribution** with the mean and mode at the center and symmetric tails.

  ```python
  def show_density(var_data):
    from matplotlib import pyplot as plt

    fig = plt.figure(figsize=(10,4))

    # Plot density
    var_data.plot.density()

    # Add titles and labels
    plt.title('Data Density')

    # Show the mean, median, and mode
    plt.axvline(x=var_data.mean(), color = 'cyan', linestyle='dashed', linewidth = 2)
    plt.axvline(x=var_data.median(), color = 'red', linestyle='dashed', linewidth = 2)
    plt.axvline(x=var_data.mode()[0], color = 'yellow', linestyle='dashed', linewidth = 2)

    # Show the figure
    plt.show()

  # Get the density of Grade
  col = df_students['Grade']
  show_density(col)
  ```

***

### Examine real world data

Data presented in educational material is often remarkably perfect, designed to show students how to find clear relationships between variables. "Real world" data is a bit less simple. Real world data can contain many different issues that can affect the utility of the data and our interpretation of the results.

* Most real-world data are influenced by factors that weren't recorded at the time. If problematic, the influence of these factors can often be reduced by increasing the size of the dataset.
* Data points that are clearly outside of what is expected—also known as "outliers"—can sometimes be safely removed from analyses, although care must be taken to not remove data points that provide real insights.
* Bias refers to a tendency to select certain types of values more frequently than others in a way that misrepresents the underlying population, or "real world". Bias can sometimes be identified by exploring data while keeping in mind basic knowledge about where the data came from.

Real-world data will always have issues, but data scientists can often overcome these issues by:

* Checking for missing values and badly recorded data
* Considering removing obvious outliers
* Examining what real-world factors might affect their analysis and determining if their dataset size is large enough to reduce the impact of these factors
* Checking for biased raw data and considering their options to fix the bias, if found

When we have more data available, our sample becomes more reliable. This makes it easier to consider outliers as being values that fall below or above percentiles within which most of the data lie. For example, the following code uses the Pandas quantile function to exclude observations below the 0.01th percentile (the value above which 99% of the data reside).

  ```python
  # calculate the 0.01th percentile
  q01 = df_students.StudyHours.quantile(0.01)
  # Get the variable to examine
  col = df_students[df_students.StudyHours>q01]['StudyHours']
  # Call the function
  show_distribution(col)
  ```

Typical statistics that measure variability in the data include:

* **Range**: The difference between the maximum and minimum. There's no built-in function for this, but it's easy to calculate using the `min` and `max` functions.
* **Variance**: The average of the squared difference from the mean. You can use the built-in `var` function to find this.
* **Standard Deviation**: The square root of the variance. You can use the built-in `std` function to find this.

Of these statistics, the standard deviation is generally the most useful. It provides a measure of variance in the data on the same scale as the data itself (so grade points for the Grade distribution and hours for the StudyHours distribution). The higher the standard deviation, the more variance there is when comparing values in the distribution to the distribution mean—in other words, the data is more spread out.

Because descriptive statistics are such an important part of exploring data, there's a built-in `describe` method of the DataFrame object that returns the main descriptive statistics for all numeric columns.

  ```python
  df_students.describe()
  ```

To see if there's a correlation between study time and grade, we can use a **statistical correlation measurement** to quantify the relationship between two columns. The correlation statistic is a value between -1 and 1 that indicates the strength of a relationship. Values above 0 indicate a positive correlation (high values of one variable tend to coincide with high values of the other), while values below 0 indicate a negative correlation (high values of one variable tend to coincide with low values of the other).

  ```python
  df_normalized.Grade.corr(df_normalized.StudyHours)
  ```

Another way to visualize the apparent correlation between two numeric columns is to use a scatter plot. 

  ```python
  # Create a scatter plot
  df_sample.plot.scatter(title='Study Time vs Grade', x='StudyHours', y='Grade')
  ```

***

### Summary

* In this module, you learned how to use Python to explore, visualize, and manipulate data. Data exploration is at the core of data science and is a key element in data analysis and machine learning.
* Machine learning is a subset of data science that deals with predictive modeling. In other words, machine learning uses data to create predictive models in order to predict unknown values. You might use machine learning to predict how much food a supermarket needs to order or to identify plants in photographs.
* Machine learning works by identifying relationships between data values that describe the characteristics of something (its features—such as the height and color of a plant) and the value we want to predict (the label—such as the species of plant). These relationships are built into a model through a training process.

Source: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/explore-analyze-data-with-python)
