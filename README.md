# Laboratory 2

## Introduction

Machine learning is an area that requires the use of appropriate data for practical application. These classes will help you gain skills in how to get and correctly prepare data for further work. The final result of this laboratory will be a tool that will be useful on next laboratories.

Please put solutions in the [`solution.py`](solution.py) file.

## Data generation

Data for work can be obtained in two ways. Using generators or loading data from repositories / files. The first option is fairly easy to use and allows you to get data practically ready for use.

- https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_classification.html
- https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html
- https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_gaussian_quantiles.html

> ### Exercise 1 (1 pts)
>
> Generate and display three different data sets using generators from the `sklearn` library with 1000 objects.

## Data loading

Another way is loading data from the file. This is the most-used option, because we can use real data. These files can be found in repositories, for example:

- http://archive.ics.uci.edu/ml/index.php
- https://sci2s.ugr.es/keel/datasets.php

The data downloaded from the repository can be in a variety of formats. Most often, despite different formats, these data after deleting the unnecessary part of the header are similar to `csv` files. Each row represents one object. Each column is an attribute except the column with the class name. Most often it is the first or last column. The columns are separated by a separator character, for example "." 

Sometimes we are forced to earlier "reformat" data into a `csv` file. A convenient way to load data from `csv` files is to use the `read_csv` function from the `pandas` library. Data loaded in this way end up in a structure called dataframe.

- https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html
- https://pandas.pydata.org/pandas-docs/version/0.23/generated/pandas.DataFrame.html

> ### Exercise 2 (1 pts)
>
> Download any dataset from https://sci2s.ugr.es/keel/datasets.php. Prepare it for loading as a "csv" file. The correct data format in the `csv` file can be found here: [`iris.csv`](data/iris.csv). Then load this downloaded data and display.

## Filling the gaps

Sometimes the loaded data may have some missing gaps. After loading and displaying such a set, one can notice that NaN appears in some places. Such gaps should be filled in because no further actions can be taken on the set. The simplest method is to fill the gap with the average value from a given column.

- https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.fillna.html
- https://pandas.pydata.org/pandas-docs/version/0.23.4/generated/pandas.DataFrame.mean.html

> ### Exercise 3 (1 pts)
>
> Load data from the [`iris.csv`](data/iris.csv) file. Check if the data is consistent. Fill in the blank fields (NaN) with the median value from the given column/atribute.

## Categorical data

Niektóre dane w zbiorach składają się z łańcuchów znaków. Najczęściej takie dane posiadają kilka powtarzających się wartości. Są to wtedy dane kategorialne. Należy wtedy takie zdane zbinaryzować. Przydatny do tego jest mechanizm `LabelEncoder` z biblioteki `sklearn`.

- https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html

> ### Exercise 4 (2 pts)
>
> Load data from the [`saheart.csv`](data/saheart.csv) file. Change columns / attributes with text to numerical values using the `LabelEncoder` mechanism. Then, replace the text data with numerical data.

## Preparation for classification

The `dataframe` structure from the `pandas` library is convenient for pre-processing. At a later stage, it is better to use the `ndarray` structure from the `numpy` library because it is much more efficient. It is possible to directly load data from a file into the `ndarray`. However, loading data into such a structure requires the homogenization of all attributes. This means that all data must be of the same type.

The data thus prepared is usually divided into two tables, which are designated `X` and `y`. These tables divide the entire data set into a subset of the attributes themselves and a subset of the labels themselves. Individual lines from one and the other table correspond to the same objects.

- https://pandas.pydata.org/pandas-docs/version/0.23/generated/pandas.DataFrame.html
- https://docs.scipy.org/doc/numpy-1.15.0/reference/generated/numpy.ndarray.html

> ### Exercise 5 (2 pts)
>
> Change the data from the previous task to one type. Then create two `ndarray` tables from them. In one named `X`, put only the attributes. The second named `y` put only the labels. Arrays should be created so that the order of the labels corresponds to the order of the attributes in the same object.

## Creating a tool

All of the above steps make up the whole process (skipping the first task) which, from loading the data, creates data that is properly processed and ready for use. It is worth remembering these activities, because they will be used quite often. It's a pity to waste time writing such a program every time.

> ### Exercise 6 (3 pts)
>
> The last task is to create a tool that gathers all these stages into one function. Skipping the first task - generating data. The solution to this task will greatly facilitate work in future laboratories. The main difficulty is the automation of the mechanism from task 4.
