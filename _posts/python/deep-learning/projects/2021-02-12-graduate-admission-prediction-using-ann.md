---
layout: post
title: GRADUATE Admission Prediction using ANN
date: 2021-02-12 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Python
- Deep Learning
- Project 
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2021/02/12/graduate-admission-prediction-using-ann"
---

Today we are going to solve a regression problem using an **Artificial Neural Network**. The dataset i'm using contains the information about the students, their GRE score, TOEFL score, CGPA e.t.c. Here click on this [NOTEBOOK](https://www.kaggle.com/code/campusx/gre-admission-prediction) to access the dataset and do predictions on it.

![14](/assets/images/clt/graduation-admission-prediction-using-ann/14.png)

First of all import the `numpy` and `pandas` libraries,

```
import numpy as np
import pandas as pd
```

Next import the dataset we want to work on,

```
df=pd.read_csv('/kaggle/input/graduate-admissions/Admission_Predict_Ver1.1.csv')
```

Have a look at the dataset using the `head()` function,

```
df.head()
```

Here is how it will look like,

![1](/assets/images/clt/graduation-admission-prediction-using-ann/1.png)

Then checkout the shape of dataset,

```
df.shape
```

![2](/assets/images/clt/graduation-admission-prediction-using-ann/2.png)

Then use the info() function to get more details,

```
df.info()
```

![3](/assets/images/clt/graduation-admission-prediction-using-ann/3.png)

Next is, we will check if there are any duplicate rows present or not,

```
df.duplicated().sum()
```

![4](/assets/images/clt/graduation-admission-prediction-using-ann/4.png)

Now drop the `Serial No.` column because it is of no use for us,

```
df.drop(columns=['Serial No.'],inplace=True)
```

![5](/assets/images/clt/graduation-admission-prediction-using-ann/5.png)

Have a look at the dataset,

```
df.head()
```

Here is how it looks like,

![6](/assets/images/clt/graduation-admission-prediction-using-ann/6.png)

Now separate the columns for testing and training data,

```
X=df.iloc[:,0:-1]
y=df.iloc[:,-1]
```
Here is how the features looks like,

![7](/assets/images/clt/graduation-admission-prediction-using-ann/7.png)

Here is a view of target label,

![8](/assets/images/clt/graduation-admission-prediction-using-ann/8.png)

Now import the `train_test_split` and divide the data into 4-parts,

```
from sklearn.model_selection import train_test_split
X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.2,random_state=1)
```

`X_train` will look like this,

![9](/assets/images/clt/graduation-admission-prediction-using-ann/9.png)

Now it is time to scale the values so that the weights can converge in a better way,

```
from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
X_train_scaled=scaler.fit_transform(X_train)
X_test_scaled=scaler.transform(X_test)
```
Scaled values will look like this,

![10](/assets/images/clt/graduation-admission-prediction-using-ann/10.png)

Now it is time to build our **NEURAL NETWORK**. For this purpose import all the necessary libraries,

```
import tensorflow
from tensorflow import keras
from keras import Sequential 
from keras.layers import Dense
```

Create a sequential model and add layers to it,

```
model=Sequential()
model.add(Dense(7,activation='relu',input_dim=7))
model.add(Dense(7,activation='relu'))
model.add(Dense(1,activation='linear'))
```

Check out the model summary,

![11](/assets/images/clt/graduation-admission-prediction-using-ann/11.png)

Then compile the model,

```
model.compile(loss='mean_squared_error',optimizer='Adam')
```

Now fit the model with the training data and provide epochs,

```
history=model.fit(X_train_scaled,y_train,epochs=100,validation_split=0.2)
````

Our model is trained now, it's time to make some predictions now,

```
y_pred=model.predict(X_test_scaled)
```

Calculate the `r2_score` of the predictions,

```
from sklearn.metrics import r2_score
r2_score(y_test,y_pred)
```
Have a look at it,

![12](/assets/images/clt/graduation-admission-prediction-using-ann/12.png)

Now import the plotting libraries and make a plot between `loss` and `validaton_loss` of our model,

```
import matplotlib.pyplot as plt
plt.plot(history.history['loss'])
plt.plot(history.history['val_loss'])
```

Here is the plot,

![13](/assets/images/clt/graduation-admission-prediction-using-ann/13.png)