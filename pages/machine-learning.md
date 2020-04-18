# Machine Learning

## Table of Contents
1. [Courses](#courses)
1. [Predicting House Prices](#predicting-house-prices)
1. [Pandas](#pandas)
1. [TensorFlow](#tensorflow)

## Courses
### Coursera
* [Predicting House Prices](https://www.coursera.org/learn/tensorflow-beginner-predicting-house-prices-regression)
  * Understand the problem statement
  * Understand the dataset
  * Data normalization
  * Train and Test split
  * Create a neural network model
  * Train the model to fit the dataset
  * Evaluate the model
  * Visualize the predictions

## Predicting House Prices
### Features
1. Year of sale
1. Age at time of sale
1. Distance from city center
1. Latitude
1. Longitude

## Pandas
[pandas](https://pandas.pydata.org) is a fast, powerful, flexible and easy to use open source data analysis and manipulationtool, built on top of the Python programming language.
```python
import pandas as pd
```

### `DataFrame.iloc`
Purely integer-location based indexing for selection by position.
`.iloc[]` is primarily integer position based (from 0 to length-1 of the axis), but may also be used with a boolean array.
```python
>>> type(df.iloc[0])
```

### Importing CSVs
```python
dataset = pd.read_csv('data.csv', names = column_names)
dataset.head()
```

### Check Missing Data  
> It's a good practice to check if the data has any missing values. In real world data, this is quite common and must be taken care of before any data pre-processing or model training.
```python
dataset.isna().sum()
```

### Data Normalization  
We can make it easier for optimization algorithms to find minimas by normalizing the data before training the model.
```python
dataframe = dataframe.iloc[:, 1:]
# [all rows, columns 1 onwards]
dataframe_norm = (dataframe - dataframe.mean())/dataframe.std()
dataframe_norm.head()
```

### Convert Label Value
Because we are using normalized values for the labels, we will get the predictions back from a trained model in the same distribution. So, we need to convert the predicted values back to the original distribution if we want predicted prices.
```python
y_mean = df['price'].mean()
y_std = df['price'].std()

def convert_label_value(prediction):
    return int(prediction * y_std + y_mean)

print(convert_label_value(n))
```

### Training and Test Sets
Select Features  
> Make sure to remove the column `price` from the list of features as it is the label and should be used as a feature.
```python
x = df_norm.iloc[:, :6] # [all rows, first six columns]
x.head()
```
Select Labels  
```python
y = df_norm.iloc[:, -1]
y.head()
```

## Tensorflow
[TensorFlow](https://www.tensorflow.org) is an end-to-end open source platform for Machine Learning. It has a comprehensive, flexible ecosystem of tools, libraries and community resources that lets researchers push the state-of-the-art in ML and developers easily build and deploy ML powered applications.  
```python
import tensorflow as tf
```
