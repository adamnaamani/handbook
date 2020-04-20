# Machine Learning

> "Gives computers the ability to learn without being explicitly programmed."

> "The most advanced AVMs use regression models to predict how small differences between properties influence a property’s value."

With machine learning, what we are trying to do, essentially, is find out that if we are given a large amount of data (pairs of X and corresponding y), can we write an algorithm to figure out the optimal values of W and b? 

## Table of Contents
1. [Courses](#courses)
1. [Neural Networks](#neural-networks)
1. [Data Products](#data-products)
1. [Preprocessing](#preprocessing)
1. [Recommender Systems](#recommender-systems)
1. [NumPy](#numpy)
1. [Pandas](#pandas)
1. [scikit-learn](#scikit-learn)
1. [keras](#keras)
1. [TensorFlow](#tensorflow)
1. [Predicting House Prices](#predicting-house-prices)
   1. [Features](#features)
   1. [Check Missing Data](#1-check-missing-data)
   1. [Data Normalization](#2-data-normalization)
   1. [Convert Label Value](#3-convert-label-value)
   1. [Training and Test Sets](#4-training-and-test-sets)
   1. [Create the Model](#create-the-model)
   1. [Model Training](#model-training)
   1. [Predictions](#predictions)

## Courses
### Coursera
* [Predicting House Prices with Regression](https://www.coursera.org/learn/tensorflow-beginner-predicting-house-prices-regression)

## Neural Networks
Artificial neural networks (ANN) or connectionist systems are computing systems vaguely inspired by the biological neural networks that constitute animal brains. Such systems "learn" to perform tasks by considering examples, generally without being programmed with task-specific rules.
### Activation Functions
There are various types of activation functions used in Neural Networks:
* `ReLU`  
The rectifier is the most commonly used activation function for deep neural networks. A unit employing the rectifier is also called a **Rectified Linear Unit** (ReLU).
* `softmax`  
This function gives us probability scores for various nodes, in this case 10 nodes of the output layer, which sum up to 1. This activation gives us the probabilities for various classes given the input. The class with the highest probability gives us our prediction.
### Learn-able parameters
For any densely connected layer, the number of learn-able parameters are:
```python
num_parameters = (nodes in current layer * nodes in previous layer) + nodes in current layer
```

## Data Products
Arises when we want to build systems that depend on predictive models.
* Predict users' future actions based on their past activities.
* Recommend content to users that they are likely to consume.
* Estimate demand for a product.
### Data Strategy
1. Aim
1. Policy
1. Plan
1. Action
### Business Objectives
* Start with business objectives
* Educate yourself
* Identify the opportunity
* Analyze gaps
* Prioritize actions
### Data-oriented Culture
* Remove barriers to data access
* No data silos
* Data sharing mindset
* Foster collaborations

## Preprocessing
Although the datasets we're working with have already been "cleaned" to some extent, in general there may be many reasons we'd want to further clean or pre-process datasets, e.g.:  
* Certain fields may be missing from some entries.
* Certain entries may be garbled / poorly formatted.
* Parts of a dataset may be "stale" or otherwise unusable.
* Parts of the dataset may contain statistical outliers (which we may or may not want to keep).
* We may want to remove data pertaining to rare or inactive users.
* May want to restrict our dataset to a certain demographic or region.

## Recommender Systems
Recommender Systems work by trying to model the relationships between people and the items they’re evaluating.
### Regression and classification tasks
* Time series modeling
* Text analysis
* Visualization

## NumPy
[`NumPy`](https://numpy.org) is the fundamental package for scientific computing with Python. It contains among other things:
* A powerful N-dimensional array object.
* Sophisticated (broadcasting) functions.
* Tools for integrating C/C++ and Fortran code.
* Useful linear algebra, Fourier transform, and random number capabilities.

```python
import numpy
```
* **Arrays**  
  Can be treated much like regular Python arrays, though they support a variety of additional operations, such as statistical operations:  
  ```python
  numpy.array()
  ```
* `numpy.mean()`
* `numpy.var()`
* `numpy.stack()`
* `numpy.matrix()`

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

## Scikit-learn
[scikit-learn](https://scikit-learn.org) provides simple and efficient tools for predictive data analysis. Built on NumPy, SciPy, and matplotlib.  
* [`train_test_split`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)  
  > Split arrays or matrices into random train and test subsets.
  ```python
  sklearn.model_selection.train_test_split(*arrays, **options)
  ```

## Keras
[Keras](https://keras.io) is a high-level neural networks API, written in Python and capable of running on top of TensorFlow, CNTK, or Theano. It was developed with a focus on enabling fast experimentation.

Keras (κέρας) means horn in Greek. It is a reference to a literary image from ancient Greek and Latin literature, first found in the Odyssey, where dream spirits (Oneiroi, singular Oneiros) are divided between those who deceive men with false visions, who arrive to Earth through a gate of ivory, and those who announce a future that will come to pass, who arrive through a gate of horn. It's a play on the words κέρας (horn) / κραίνω (fulfill), and ἐλέφας (ivory) / ἐλεφαίρομαι (deceive).

> "_Being able to go from idea to result with the least possible delay is key to doing good research._"

### Models
There are two main types of models available in Keras: the Sequential model, and the Model class used with the functional API.

These models have a number of methods and attributes in common:
* `model.layers`: flattened list of layers comprising the model.
* `model.inputs`: list of input tensors of the model.
* `model.outpus`: list of output tensors of the model.
* `model.summary()`: prints a summary representation of a model.
* `model.get_config()`: returns a dictionary containing the configuration of the model. 
#### Sequential  
The [`Sequential`](https://keras.io/getting-started/sequential-model-guide/) model is a linear stack of layers. You can create a Sequential model by passing a list of layer instances to the constructor:
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
### Optimizers
An optimizer is one of the two arguments required for compiling a Keras model:
```python
from keras import optimizers

model = Sequential()
model.add(Dense(64, kernel_initializer='uniform', input_shape=(10,)))
model.add(Activation('softmax'))

sgd = optimizers.SGD(lr=0.01, decay=1e-6, momentum=0.9, nesterov=True)
model.compile(loss='mean_squared_error', optimizer=sgd)
```
* `Adam`  
  An algorithm for first-order gradient-based optimization of stochastic objective functions, based on adaptive estimates of lower-order moments. The method is straightforward to implement, is computationally efficient, has little memory requirements, is invariant to diagonal rescaling of the gradients, and is well suited for problems that are large in terms of data and/or parameters.
  ```python
  keras.optimizers.Adam(learning_rate=0.001, beta_1=0.9, beta_2=0.999, amsgrad=False)
  ```
### Visualization
Keras provides [utility functions](https://keras.io/visualization/) to plot a Keras model (using graphviz).
```python
from keras.utils import plot_model
plot_model(model, to_file='model.png')
```
`plot_model` takes four optional arguments:  
* `show_shapes`: (defaults to False) controls whether output shapes are shown in the graph.
* `show_layer_names`: (defaults to True) controls whether layer names are shown in the graph.
* `expand_nested`: (defaults to False) controls whether to expand nested models into clusters in the graph.
* `dpi`: (defaults to 96) controls image dpi.

## TensorFlow
[TensorFlow](https://www.tensorflow.org) is an end-to-end open source platform for Machine Learning. It has a comprehensive, flexible ecosystem of tools, libraries and community resources that lets researchers push the state-of-the-art in ML and developers easily build and deploy ML powered applications.  
```python
import tensorflow as tf
```

## Predicting House Prices
### Features
* Year of sale
* Age at time of sale
* Distance from city center
* Latitude
* Longitude

### 1. Check Missing Data  
> It's a good practice to check if the data has any missing values. In real world data, this is quite common and must be taken care of before any data pre-processing or model training.
```python
dataset.isna().sum()
```

### 2. Data Normalization  
> We can make it easier for optimization algorithms to find minimas by normalizing the data before training the model.
```python
df = df.iloc[:, 1:]
# [all rows, columns 1 onwards]
df_norm = (df - df.mean())/df.std()
df_norm.head()
```

### 3. Convert Label Value
> Because we are using normalized values for the labels, we will get the predictions back from a trained model in the same distribution. So, we need to convert the predicted values back to the original distribution if we want predicted prices.
```python
y_mean = df['price'].mean()
y_std = df['price'].std()

def convert_label_value(prediction):
    return int(prediction * y_std + y_mean)

print(convert_label_value(n))
```

### 4. Training and Test Sets
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
> We will need to extract just the numeric values for the features and labels as the TensorFlow model will expect just numeric values as input.
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

### 5. Create the Model
> Write a function that returns an untrained model of a certain architecture.
```python
def get_model():
    model = Sequential([
        Dense(10, input_shape=(6,), activation='relu'),
        Dense(20, activation='relu'),
        Dense(5, activation='relu'),
        Dense(1)
    ])
    model.compile(
      loss='mse', # mean squared error
      optimizer='adam'
    )
    return model

get_model().summary()
```

### 6. Model Training
#### EarlyStopping callback
> We can use an `EarlyStopping` callback from Keras to stop the model training if the validation loss stops decreasing for a few epochs.
```python
es_cb = EarlyStopping(monitor='val_loss', patience=5)

model = get_model()
preds_on_untrained = model.predict(x_test)

history = model.fit(
    x_train, y_train,
    validation_data = (x_test, y_test),
    epochs=100,
    callbacks = [es_cb]
)
```
#### Plot Training and Validation Loss
Use the `plot_loss` helper function to take a look at training and validation loss.
```python
plot_loss(history)
```

### 7. Predictions
#### Plot Raw Predictions
Use the `compare_predictions` helper function to compare predictions from the model when it was untrained and when it was trained.
```python
preds_on_trained = model.predict(x_test)
compare_predictions(preds_on_untrained, preds_on_trained, y_test)
```
#### Plot Price Predictions
The plot for price predictions and raw predictions will look the same with just one difference: The x and y axis scale is changed.
```python
price_untrained = [convert_label_value(y) for y in preds_on_untrained]
price_trained = [convert_label_value(y) for y in preds_on_trained]
price_test = [convert_label_value(y) for y in y_test]

compare_predictions(price_untrained, price_trained, price_test)
```