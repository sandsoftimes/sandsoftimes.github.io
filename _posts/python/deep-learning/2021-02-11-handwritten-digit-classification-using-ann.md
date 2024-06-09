---
layout: post
title: Handwritten Digit Classification using ANN | MNIST Dataset
date: 2021-02-11 20:52:55.000000000 +05:00
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
permalink: "/2021/02/11/handwritten-digit-classification-using-ANN"
---
Today, we are going to build anther Artificial Neural Network for one of the famous dataset known as **MNIST**. It is use to classify digits(0-9). Here is also colab-notebook attached for the code:
[Python-Notebook](https://colab.research.google.com/drive/1SqETl3Zi1EEesdJfEv6_QimB-M-YjKGx?usp=sharing)
![4](/assets/images/clt/handwritten-digit-classification-using-ann/4.png)

Initially we did all the necessary importings,

```
import tensorflow
from tensorflow import keras
from tensorflow.keras import Sequential
from tensorflow.keras.layers import Dense,Flatten
```
Then simply load the dataset using keras, it will automatically do the train and test split.

```
(X_train,y_train),(X_test,y_test)=keras.datasets.mnist.load_data()
```

Visualize the shape of train and test,

```
X_test.shape
````
```
y_test.shape
````
```
X_train.shape
````
```
y_train.shape
````

**y_train** will be the labels array.

Then import plotting library and do some plotting of training data to acutually visualize the digits.

```
import matplotlib.pyplot as plt
plt.imshow(X_train[2])
```

Now scale the data to better calculate the parameters e.g weight and bias.

```
X_train=X_train/255
X_test=X_test/255
```

Lets make our ANN now with keras sequential() model, 

```
model = Sequential()

model.add(Flatten(input_shape=(28,28)))
model.add(Dense(128,activation='relu'))
model.add(Dense(32,activation='relu'))
model.add(Dense(10,activation='softmax'))
```

**Flatten** will convert the 28x28 matrix into single long array.

View the model summary using,

```
model.summary()
````

Add the loss function to our model, 

```
model.compile(loss='sparse_categorical_crossentropy',optimizer='Adam',metrics=['accuracy'])
```

Now fit the model on our training data to calculate the weight and bias,

```
history=model.fit(X_train,y_train,epochs=25,validation_split=0.2)
# history = model.fit(X_train,y_train,epochs=25,validation_split=0.2)
```

The model will run for 25 epochs. It is now time to make some predictions from our model,

```
y_prob=model.predict(X_test)
y_pred = y_prob.argmax(axis=1)
y_pred
```

Inorder to check accuracy of our model **import accuracy_score**

```
from sklearn.metrics import accuracy_score
accuracy_score(y_test,y_pred)
```

Also we will check the overfitting by plotting the loss and validation_loss,

```
plt.plot(history.history['loss'])
plt.plot(history.history['val_loss'])
```
![1](/assets/images/clt/handwritten-digit-classification-using-ann/1.png)

Now compare the accuracy with the validation_accuracy

```
plt.plot(history.history['accuracy'])
plt.plot(history.history['val_accuracy'])
```
![2](/assets/images/clt/handwritten-digit-classification-using-ann/2.png)

Lets test our model on a random value from the testing data,

```
plt.imshow(X_test[9])
```
```
model.predict(X_test[9].reshape(1,28,28)).argmax(axis=1)
```

![3](/assets/images/clt/handwritten-digit-classification-using-ann/3.png)