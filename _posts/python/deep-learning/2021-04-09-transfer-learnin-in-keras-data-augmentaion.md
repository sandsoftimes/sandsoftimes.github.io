---
layout: post
title: Transfer Learning in Keras | with Data Augmentation
date: 2021-04-09 20:52:55.000000000 +05:00
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
permalink: "/2021/04/09/transfer-learnin-in-keras-data-augmentation"
---
Transfer learning gives a bit different results when done with data-augmentation and without data-augmentation. The accuracy is a bit improved with data augmentation technique. Here i've implemented a code today for transfer learning technique with data-augmentation. You can check my previous without augmentation implementation as well from [here!](/2021/04/10/transfer-learnin-in-keras)

First of all, do necessary importing and download dataset,

```
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!kaggle datasets download -d salader/dogs-vs-cats
```

unzip the dataset,

```
import zipfile
zip_ref = zipfile.ZipFile('/content/dogs-vs-cats.zip', 'r')
zip_ref.extractall('/content')
zip_ref.close()
```

import libraries for the model,

```
import tensorflow
from tensorflow import keras
from keras import Sequential
from keras.layers import Dense,Flatten
from keras.applications.vgg16 import VGG16
```

use the VGG16 convolution base,

```
conv_base = VGG16(
    weights='imagenet',
    include_top = False,
    input_shape=(150,150,3)
)
```

create the rest of the model and connect with the base,

```
model = Sequential()

model.add(conv_base)
model.add(Flatten())
model.add(Dense(256,activation='relu'))
model.add(Dense(1,activation='sigmoid'))
```

freeze the convolution layers training,

```
conv_base.trainable = False
```

import the image generators for the data augmentation,

```
from keras.preprocessing.image import ImageDataGenerator, array_to_img, img_to_array, load_img
```

create the generators and do image augmentation,

```
batch_size = 32

train_datagen = ImageDataGenerator(
        rescale=1./255,
        shear_range=0.2,
        zoom_range=0.2,
        horizontal_flip=True)

test_datagen = ImageDataGenerator(rescale=1./255)

train_generator = train_datagen.flow_from_directory(
        '/content/train',
        target_size=(150, 150),
        batch_size=batch_size,
        class_mode='binary') 

validation_generator = test_datagen.flow_from_directory(
        '/content/test',
        target_size=(150, 150),
        batch_size=batch_size,
        class_mode='binary')
```

compile the model,

```
model.compile(optimizer='adam',loss='binary_crossentropy',metrics=['accuracy'])
```

fit the model and store the history,

```
history = model.fit_generator(
        train_generator,
        epochs=10,
        validation_data=validation_generator)
```

do plotting of accuracy,

```
import matplotlib.pyplot as plt

plt.plot(history.history['accuracy'],color='red',label='train')
plt.plot(history.history['val_accuracy'],color='blue',label='validation')
plt.legend()
plt.show()
```

![1](/assets/images/clt/transfer-learnin-in-keras-data-augmentaion/1.png)

plot the loss,

```
plt.plot(history.history['loss'],color='red',label='train')
plt.plot(history.history['val_loss'],color='blue',label='validation')
plt.legend()
plt.show()
```

![2](/assets/images/clt/transfer-learnin-in-keras-data-augmentaion/2.png)