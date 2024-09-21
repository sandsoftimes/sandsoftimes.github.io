---
layout: post
title: Transfer Learning in Keras | Fine Tuning VS Feature Extraction
date: 2021-04-10 20:52:55.000000000 +05:00
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
permalink: "/2021/04/10/transfer-learnin-in-keras"
---
Transfer learning is also one of the most important topic in Deep-Learning/Machine-Learning. I would say it is like using others pre-trained models for your problem. Deep Learning models are difficult to train because they are data-hungry. By this i mean they require alot of data in order to achieve good performance. Therefore is alot of data you can say labelled-data is required. 

Let's assume the example of a simple cat-dog classifier. We'll need a huge data inorder to make a good classifier. One method is to scrap the data using various data-scrapping techniques but there is still an issue in this case. That data will be unlabelled, you've to assign labels manually and for this purpose labor will be required which is costly. This is the first problem.

Second reason for using the Pre-Trained models is the time. Deep Learning models usually take a huge time to train so people don't prefer long trainings by theirselves. The solution of these two problems is using pre-trained models for your projects. One of the most famous dataset is ImageNet. It is a big dataset of images almost 1.4 million images and there are total of 1000 classes in this dataset. Many models are trained on this dataset. Rather than creating your model and training it on this dataset, you can use those pre-trained models.

There is one problem in using pre-trained models. What if the class you want to classify is not present in the dataset on which model is trained. Here comes the transfer learning. In transfer learning we use the pre-trained models and we re-train a portion of the model on our dataset. Basically in CNN, there are two major parts of the architecture. One is the convolution layer portion while the second one is the fully-connected layer portion. The first portion works for all the problems because it extract the primitive features which is same for all the problems/classification task. While the fully connected portion is used for classification mainly, so we retrain this portion on our required dataset according to the problem.

Transfer learning is done in two ways,

* Feature Extraction Method
* Fine-Tuning Method

In the first method, we only retrain the fully connected layer portion according to our need. While in the Fine-Tuning method, we retrain some of the last convolution layers and fully connected layers. 

## Transfer Learning Feature Extraction without using Data Augmentation

First of all download the dataset in your notebook,

```
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!kaggle datasets download -d salader/dogs-vs-cats
```

Then unzip the dataset,

```
import zipfile
zip_ref = zipfile.ZipFile('/content/dogs-vs-cats.zip', 'r')
zip_ref.extractall('/content')
zip_ref.close()
```

import tensorflow and necessary libraries,

```
import tensorflow
from tensorflow import keras
from keras import Sequential
from keras.layers import Dense,Flatten
from keras.applications.vgg16 import VGG16
```

create a base model,

```
conv_base = VGG16(
    weights='imagenet',
    include_top = False,
    input_shape=(150,150,3)
)
```

check the model summary,

```
conv_base.summary()
```


![1](/assets/images/clt/transfer-learning-in-keras/1.png)

Then create and connect the rest of the model,

```
model = Sequential()

model.add(conv_base)
model.add(Flatten())
model.add(Dense(256,activation='relu'))
model.add(Dense(1,activation='sigmoid'))```
```
check model summary,

```
model.summary()
```

![2](/assets/images/clt/transfer-learning-in-keras/2.png)

change the training parameter for the starting covolution layers,

```
conv_base.trainable=False
```

add the generators to efficiently use the resources,

```
train_ds = keras.utils.image_dataset_from_directory(
    directory = '/content/train',
    labels='inferred',
    label_mode = 'int',
    batch_size=32,
    image_size=(150,150)
)

validation_ds = keras.utils.image_dataset_from_directory(
    directory = '/content/test',
    labels='inferred',
    label_mode = 'int',
    batch_size=32,
    image_size=(150,150)
)
```

normalize the images,

```
def process(image,label):
    image = tensorflow.cast(image/255. ,tensorflow.float32)
    return image,label

train_ds = train_ds.map(process)
validation_ds = validation_ds.map(process)
```

compile the model,

```
model.compile(optimizer='adam',loss='binary_crossentropy',metrics=['accuracy'])
```

store the history in a variable,

```
history = model.fit(train_ds,epochs=10,validation_data=validation_ds)
```

plot the accuracy and validation accuracy using this history variable,

```
import matplotlib.pyplot as plt

plt.plot(history.history['accuracy'],color='red',label='train')
plt.plot(history.history['val_accuracy'],color='blue',label='validation')
plt.legend()
plt.show()
```

![3](/assets/images/clt/transfer-learning-in-keras/3.png)

plot the loss and the validation loss,

```
plt.plot(history.history['loss'],color='red',label='train')
plt.plot(history.history['val_loss'],color='blue',label='validation')
plt.legend()
plt.show()
```

![4](/assets/images/clt/transfer-learning-in-keras/4.png)
