---
layout: post
title: Customer Churn Prediction using ANN | Keras and Tensorflow | Deep Learning Classification
date: 2021-02-10 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Python
- Deep Learning
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2021/02/10/customer-churn-prediction-using-ANN"
---
The working of a Artificial Neural Network can be observed in multiple ways. One way is to solve a practical use-case on it. The problem we are going to solve today is Customer-Churn problem of a Bank`(will the customer stay or go)`. 

For this purpose, i'm going to use the available dataset on kaggle. Here is the link to [Churn Dataset](https://www.kaggle.com/code/campusx/notebook8ad570467f) and also i'm going to use the notebook provided by kaggle.

Initially we are importing the necessary libraries including numpy and pandas. Then we are obtaining the path to the dataset csv file.

```
# This Python 3 environment comes with many helpful analytics libraries installed
# It is defined by the kaggle/python Docker image: https://github.com/kaggle/docker-python
# For example, here's several helpful packages to load

import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)

# Input data files are available in the read-only "../input/" directory
# For example, running this (by clicking run or pressing Shift+Enter) will list all files under the input directory

import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))

# You can write up to 20GB to the current directory (/kaggle/working/) that gets preserved as output when you create a version using "Save & Run All" 
# You can also write temporary files to /kaggle/temp/, but they won't be saved outside of the current session
```

Now read the data in the form of pandas dataframe,

```
df=pd.read_csv('/kaggle/input/credit-card-customer-churn-prediction/Churn_Modelling.csv')
```

Observe the dataset by using these functions,

```
df.describe()
df.head()
```

Dataset information will be displayed. Also see the un-nessary columns and drop them.e.g **RowNumber,CustomerId and Surname are of no use for us**,

```
df.drop(columns = ['RowNumber','CustomerId','Surname'],inplace=True)
```

Now count the total categorical values in `Geography` and `Gender` column 

```
df['Geography'].value_counts()
```

```
df['Gender'].value_counts()
```

The next step is to get the dummies where possible,

```
df=pd.get_dummies(df,columns=['Geography','Gender'],drop_first=True)
```

You've your dataset in useful form now, perform the initial` train-test-split`.

```
X=df.drop(columns=['Exited'])
y=df['Exited'].values

from sklearn.model_selection import train_test_split
X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.2,random_state=0)
```

Then scale the values using `StandardScaler library`,

```
from sklearn.preprocessing import StandardScaler
scaler=StandardScaler()
X_train_trf=scaler.fit_transform(X_train)
X_test_trf=scaler.transform(X_test)
```

It is now time to make our first Artificial Neural Network, so do necessary importings of tensorflow and keras,

```
import tensorflow
from tensorflow import keras
from tensorflow.keras import Sequential
from tensorflow.keras.layers import Dense
```

Now make a sequential model and add hidden layers to it,

```
model=Sequential()
model.add(Dense(11,activation='relu',input_dim=11))
model.add(Dense(11,activation='relu'))
model.add(Dense(1,activation='sigmoid'))
```

Check the model summary,

```
model.summary()
```

The next step is to add a loss-function to your ANN. Here we are using `binary_crossentropy` with optimizer `Adam`

```
model.compile(loss='binary_crossentropy',optimizer='Adam',metrics=['accuracy'])
```

Fit the model on the training data and validate 20% of the data during training and store it in a variable. This will run for 100 epochs and we will have the perfect weights for hidden layers.

```
history=model.fit(X_train_trf,y_train,epochs=100,validation_split=0.2)
```

Check the weights of hidden layers,

```
model.layers[0].get_weights()
```

```
model.layers[1].get_weights()
```

```
model.layers[2].get_weights()
```

We are going to make predictions from our model now,

```
y_log=model.predict(X_test_trf)
```

As the activation function is sigmoid and relu, so it will give values b/w the range of 0 and 1. We've to use some threshold to obtain the binary values from the results.

```
y_pred=np.where(y_log>0.5,1,0)
```

Check the accuracy of the ANN,

```
from sklearn.metrics import accuracy_score
accuracy_score(y_test,y_pred)
```

history is the object itself. So inorder to access the values use,

```
history.history
```

Now see the overfitting, compare the loss and validation loss.

```
import matplotlib.pyplot as plt

plt.plot(history.history['loss'])
plt.plot(history.history['val_loss'])
```

![1](/assets/images/clt/customer-churn-prediction-using-ann/1.png)

Similarly compare the accuracy and validation accuracy.

```
plt.plot(history.history['accuracy'])
plt.plot(history.history['val_accuracy'])
```

![2](/assets/images/clt/customer-churn-prediction-using-ann/2.png)