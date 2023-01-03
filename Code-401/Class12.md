# Pandas

## Getting Started with Pandas

### What kind of data does pandas handle?

* To load the pandas package and start working with it, import the package. The community agreed alias for pandas is pd, so loading pandas as pd is assumed standard practice for all of the pandas documentation: `import pandas as pd`.
* To manually store data in a table, create a `DataFrame`. When using a Python dictionary of lists, the dictionary keys will be used as column headers and the values in each list as columns of the `DataFrame`.
* A `DataFrame` is a 2-dimensional data structure that can store data of different types (including characters, integers, floating point values, categorical data and more) in columns. It is similar to a spreadsheet, a SQL table or the `data.frame` in R: `df = pd.DataFrame({<data>})`.
* When selecting a single column of a pandas `DataFrame`, the result is a pandas `Series`. To select the column, use the column label in between square brackets `[]`. You can create a `Series` from scratch as well: `ages = pd.Series([22, 35, 58], name="Age")`.

Remember

* Import the package, aka `import pandas as pd`
* A table of data is stored as a pandas `DataFrame`
* Each column in a `DataFrame` is a `Series`
* You can do things by applying a method to a `DataFrame` or `Series`

### How do I read and write tabular data?

* pandas provides the `read_csv()` function to read data stored as a csv file into a pandas `DataFrame`. pandas supports many different file formats or data sources out of the box (csv, excel, sql, json, parquet, …), each of them with the prefix `read_*`: `titanic = pd.read_csv("data/titanic.csv")`.
* Make sure to always have a check on the data after reading in the data. When displaying a `DataFrame`, the first and last 5 rows will be shown by default.
* To see the first N rows of a `DataFrame`, use the `head()` method with the required number of rows as argument: `titanic.head(8)`.
* Interested in the last N rows instead? pandas also provides a `tail()` method. For example, `titanic.tail(10)` will return the last 10 rows of the DataFrame.
* A check on how pandas interpreted each of the column data types can be done by requesting the pandas `dtypes` attribute: `titanic.dtypes`.
* Whereas `read_*` functions are used to read data to pandas, the `to_*` methods are used to store data. The `to_excel()` method stores the data as an excel file. In the example here, the `sheet_name` is named passengers instead of the default Sheet1. By setting `index=False` the row index labels are not saved in the spreadsheet: `titanic.to_excel("titanic.xlsx", sheet_name="passengers", index=False)`.
* The equivalent `read function` read_excel() will reload the data to a `DataFrame`: `titanic = pd.read_excel("titanic.xlsx", sheet_name="passengers")`.

Remember

* Getting data in to pandas from many different file formats or data sources is supported by `read_*` functions.
* Exporting data out of pandas is provided by different `to_*` methods.
* The `head`/`tail`/`info` methods and the `dtypes` attribute are convenient for a first check.

### How do I select a subset of a DataFrame?

* To select a single column, use square brackets `[]` with the column name of the column of interest: `ages = titanic["Age"]`.
  * The inner square brackets define a Python list with column names, whereas the outer brackets are used to select the data from a pandas `DataFrame`: `age_sex = titanic[["Age", "Sex"]]`.
* `DataFrame.shape` is an attribute (remember tutorial on reading and writing, do not use parentheses for attributes) of a pandas `Series` and `DataFrame` containing the number of rows and columns: (nrows, ncolumns). A pandas Series is 1-dimensional and only the number of rows is returned: `titanic["Age"].shape`.
* To select rows based on a conditional expression, use a condition inside the selection brackets `[]`: `above_35 = titanic[titanic["Age"] > 35]`.
  * The condition inside the selection brackets `titanic["Age"] > 35` checks for which rows the `Age` column has a value larger than 35.
* Similar to the conditional expression, the `isin()` conditional function returns a `True` for each row the values are in the provided list. To filter the rows based on such a function, use the conditional function inside the selection brackets `[]`. In this case, the condition inside the selection brackets `titanic["Pclass"].isin([2, 3])` checks for which rows the `Pclass` column is either 2 or 3: `class_23 = titanic[titanic["Pclass"].isin([2, 3])]`.
  * The above is equivalent to filtering by rows for which the class is either 2 or 3 and combining the two statements with an `|` (or) operator: `class_23 = titanic[(titanic["Pclass"] == 2) | (titanic["Pclass"] == 3)]`.
* The `notna()` conditional function returns a `True` for each row the values are not a `Null` value. As such, this can be combined with the selection brackets `[]` to filter the data table: `age_no_na = titanic[titanic["Age"].notna()]`.
* A subset of both rows and columns is made in one go and just using selection brackets `[]` is not sufficient anymore. The `loc`/`iloc` operators are required in front of the selection brackets `[]`. When using `loc`/`iloc`, the part before the comma is the rows you want, and the part after the comma is the columns you want to select: `adult_names = titanic.loc[titanic["Age"] > 35, "Name"]`.
* When specifically interested in certain rows and/or columns based on their position in the table, use the `iloc` operator in front of the selection brackets `[]`: ``titanic.iloc[9:25, 2:5]`.

Remember

* When selecting subsets of data, square brackets `[]` are used.
* Inside these brackets, you can use a single column/row label, a list of column/row labels, a slice of labels, a conditional expression or a colon.
* Select specific rows and/or columns using `loc` when using the row and column names.
* Select specific rows and/or columns using `iloc` when using the positions in the table.
* You can assign new values to a selection based on `loc`/`iloc`.

### How do I create plots in pandas?

* Import matplotlib: `import matplotlib.pyplot as plt`.
* The usage of the `index_col` and `parse_dates` parameters of the `read_csv` function to define the first (0th) column as index of the resulting `DataFrame` and convert the dates in the column to `Timestamp` objects, respectively: `air_quality = pd.read_csv("data/air_quality_no2.csv", index_col=0, parse_dates=True)`.
* With a `DataFrame`, pandas creates by default one line plot for each of the columns with numeric data:

```
air_quality.plot()
plt.show()
```

* To plot a specific column, use the selection method of the subset data tutorial in combination with the `plot()` method. Hence, the `plot()` method works on both `Series` and `DataFrame`:

```
air_quality["station_paris"].plot()
plt.show()
```

* Apart from the default `line` plot when using the `plot` function, a number of alternatives are available to plot data. Let’s use some standard Python to get an overview of the available plot methods:

```
air_quality.plot.scatter(x="station_london", y="station_paris", alpha=0.5)
plt.show()
```

* One of the options is `DataFrame.plot.box()`, which refers to a `boxplot`. The `box` method is applicable on the air quality example data:

```
air_quality.plot.box()
plt.show()
```

* Separate subplots for each of the data columns are supported by the `subplots` argument of the `plot` functions:

```
axs = air_quality.plot.area(figsize=(12, 4), subplots=True)
plt.show()
```

Remember

* The `.plot.*` methods are applicable on both Series and DataFrames.
* By default, each of the columns is plotted as a different element (line, boxplot,…).
* Any plot created by pandas is a Matplotlib object.

Source: <https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html>
