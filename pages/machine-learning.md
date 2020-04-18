# Machine Learning

## Table of Contents
1. [Courses](#courses)
1. [Neural Networks](#neural-networks)
1. [Pandas](#pandas)
1. [scikit-learn](#scikit-learn)
1. [keras](#keras)
1. [TensorFlow](#tensorflow)
1. [Predicting House Prices](#predicting-house-prices)

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

## Neural Networks
### Rectifier (neural networks)
The rectifier is the most commonly used activation function for deep neural networks. A unit employing the rectifier is also called a **Rectified Linear Unit** (`ReLU`).

## Pandas
[pandas](https://pandas.pydata.org) is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool, built on top of the Python programming language.
```python
import pandas as pd
```

### `DataFrame.iloc`
> Purely integer-location based indexing for selection by position.
`.iloc[]` is primarily integer position based (from 0 to length-1 of the axis), but may also be used with a boolean array.
```python
>>> type(df.iloc[0])
```

### Importing CSVs
```python
dataset = pd.read_csv('data.csv', names=column_names)
dataset.head()
```

## scikit-learn
[`train_test_split`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)  
> Split arrays or matrices into random train and test subsets.
```python
sklearn.model_selection.train_test_split(*arrays, **options)
```

## keras
### Models
* [`Sequential`](https://keras.io/getting-started/sequential-model-guide/)  
The `Sequential` model is a linear stack of layers. You can create a Sequential model by passing a list of layer instances to the constructor:
  ```python
  from keras.models import Sequential
  from keras.layers import Dense, Activation

  model = Sequential([
      Dense(32, input_shape=(784,)),
      Activation('relu'),
      Dense(10),
      Activation('softmax'),
  ])
  ```
  You can also simply add layers via the .add() method:
  ```python
  model = Sequential()
  model.add(Dense(32, input_dim=784))
  model.add(Activation('relu'))
  ```

## TensorFlow
[TensorFlow](https://www.tensorflow.org) is an end-to-end open source platform for Machine Learning. It has a comprehensive, flexible ecosystem of tools, libraries and community resources that lets researchers push the state-of-the-art in ML and developers easily build and deploy ML powered applications.  
```python
import tensorflow as tf
```

## Predicting House Prices
### Features
1. Year of sale
1. Age at time of sale
1. Distance from city center
1. Latitude
1. Longitude

### Check Missing Data  
> It's a good practice to check if the data has any missing values. In real world data, this is quite common and must be taken care of before any data pre-processing or model training.
```python
dataset.isna().sum()
```

### Data Normalization  
> We can make it easier for optimization algorithms to find minimas by normalizing the data before training the model.
```python
df = df.iloc[:, 1:]
# [all rows, columns 1 onwards]
df_norm = (df - df.mean())/df.std()
df_norm.head()
```

### Convert Label Value
> Because we are using normalized values for the labels, we will get the predictions back from a trained model in the same distribution. So, we need to convert the predicted values back to the original distribution if we want predicted prices.
```python
y_mean = df['price'].mean()
y_std = df['price'].std()

def convert_label_value(prediction):
    return int(prediction * y_std + y_mean)

print(convert_label_value(n))
```

### Training and Test Sets
#### Select Features  
> Make sure to remove the column `price` from the list of features as it is the label and should be used as a feature.
```python
x = df_norm.iloc[:, :6] # [all rows, first six columns]
x.head()
```
#### Select Labels  
```python
y = df_norm.iloc[:, -1]
y.head()
```
#### Feature and Label Values  
> We will need to extract just the numberic values for the features and labels as the TensorFlow model will expect just numeric values as input.
```python
x_arr = x.values
y_arr = y.values

print('Features array shape:', x_arr.shape)
print('Labels array shape:', y_arr.shape)
```
#### Train and Test Split
> We will keep some part of the data aside as a test set. The model will not use this set during training and it will be used only for checking the performance of the model in trained and un-trained states. This way, we can make sure that we are going in the right direction with our model training.
```python
x_train, x_test, y_train, y_test = train_test_split(x_arr, y_arr, test_size=0.05, random_state=0)

print('Training set:', x_train.shape, y_train.shape)
print('Test set:', x_test.shape, y_test.shape)
```

### Create the Model
Write a function that returns an untrained model of a certain architecture.
```python
def get_model():
    model = Sequential([
        Dense(10, input_shape=(6,), activation='relu'),
        Dense(20, activation='relu'),
    ])
```
