---
layout: post
title: Introduction to Machine Learning using Scikit Learn
date: 2020-10-30 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Python
- Machine Learning
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2020/10/30/introduction-to-machine-learning-using-scikit-learn"
---
When it comes to machine learning, `Scikit Learn` is the most widely used library. Today, we are going to practice the very basic machine learning model. We are going to use scikit learn to split our data into `train` and `test` subsets. Then we are going to create the `Linear Regression` model and afterwards, we train and test it by using the subsets.

Initially import all the necessary libraries including `pandas`, `numpy`, `matplotlib` and `seaborn`

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

then read the data from the dataset, in this case we are using data from a self-generate csv file with the name 'USA_Housing.csv'

```
USAhousing=pd.read_csv('USA_Housing.csv')
```

Now have a look at the imported dataset,

```
USAhousing.head()
```

Then check some info of the imported dataset,

```
USAhousing.info()
```

After it, apply the `describe()` method to extract some valuable information,

```
USAhousing.describe()
```

Then, specifically extract the columns of the datasets,

```
USAhousing.columns
```

After it, we will visualize the imported data in the form of plots. We are going to use seaborn library for this purpose which we've imported at the start. First we'll look the data in the form of pairplot

```
sns.pairplot(USAhousing)
```

Then visualize the data in the form of distplot,

```
sns.distplot(USAhousing['Price'])
```

Similarly, check heat plot as well for the given data,

```
sns.heatmap(USAhousing.corr())
```

After visualization, we are going to train our first linear regression model. We will need to first split up our data into an X array that contains the features to train on, and a y array with the target variable, in this case the Price column. We will toss out the Address column because it only has text info that the linear regression model can't use.

```
X = USAhousing[['Avg. Area Income', 'Avg. Area House Age', 'Avg. Area Number of Rooms',
               'Avg. Area Number of Bedrooms', 'Area Population']]
y = USAhousing['Price']
```

Now let's split the data into a training set and a testing set. We will train out model on the training set and then use the test set to evaluate the model.

```
from sklearn.model_selection import train_test_split
```

```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4, random_state=101)
```

Now we will create and train the model,

```
from sklearn.linear_model import LinearRegression
```

```
lm = LinearRegression()
```

```
lm.fit(X_train,y_train)
```

Let's evaluate the model by checking out it's coefficients and how we can interpret them.

```
# print the intercept
print(lm.intercept_)
```

```
coeff_df = pd.DataFrame(lm.coef_,X.columns,columns=['Coefficient'])
coeff_df
```

## Interpreting the coefficients:


* Holding all other features fixed, a 1 unit increase in Avg. Area Income is associated with an *increase of $21.52 *.
* Holding all other features fixed, a 1 unit increase in Avg. Area House Age is associated with an *increase of $164883.28 *.
* Holding all other features fixed, a 1 unit increase in Avg. Area Number of Rooms is associated with an *increase of $122368.67 *.
* Holding all other features fixed, a 1 unit increase in Avg. Area Number of Bedrooms is associated with an *increase of $2233.80 *.
* Holding all other features fixed, a 1 unit increase in Area Population is associated with an *increase of $15.15 *.
