---
layout: post
title: Non-Linear Neural Networks | Keras Functional Model
date: 2021-02-15 20:52:55.000000000 +05:00
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
permalink: "/2021/02/15/non-linear-neural-networks"
---
There are some problems which cannot be solved with a sequential model, therefore we need non-sequential model. Sequential model goes on with the assumption of single input and single output. What if you've to predict two things? What if linear topology doesnot solve your problem. 

In order to make non-sequential model, we use keras-functional-api. First of all import the model from keras,

```
from keras.models import Model
```

Then simply create the model but don't run the cell and leave inputs and outputs empty for now,

```
model=Model(inputs=,outputs=)
```

Import all keras-layers,

```
from keras.layers import *
```

Define an input shape for your model,

```
x=Input(shape=(3,))
```

Create hidden layers and output layers for the model,

```
hidden1=Dense(128,activation='relu')(x)
hidden2=Dense(64,activation='relu')(hidden1)
output1=Dense(1,activation='linear')(hidden2)
output2=Dense(1,activation='sigmoid')(hidden2)
```

You can see we've two outputs for the above architecture one with the activation function of sigmoid and other with the linear function. Now go back to the cell which we left where we were creating the model and give the inputs and outputs,

```
model=Model(inputs=x,outputs=[output1,output2])
```

Now check the model summary,

```
model.summary()
```

![2](/assets/images/clt/non-linear-neural-networks/2.png)

At the end plot the model for visual demonstration of model architecture,

```
from keras.utils import plot_model
plot_model(model,show_shapes=True)
```
Here is how it will look,

![1](/assets/images/clt/non-linear-neural-networks/1.png)

Also for better understanding, you can go through this [NOTEBOOK(functional-api-demo.ipynb)](https://colab.research.google.com/drive/1uCHf6hoLR1a-46RznVjqnhVZNechF0fz?usp=sharing#scrollTo=ANFCCwXDDwvf )

## Multi-Input Model

Simply do the imports of Model and Layers,

```
from keras.layers import *
from keras.models import Model
```

Then defined two inputs,

```
inputA=Input(shape=(32,))
inputB=Input(shape=(128,))
```

Define first branch for first input,

```
x=Dense(8,activation="relu")(inputA)
x1=Dense(4,activation="relu")(x)
```

and second branch for second input,

```
y=Dense(64,activation="relu")(inputB)
y1=Dense(32,activation="relu")(y)
y2=Dense(4,activation="relu")(y1)
```

combine output of both branches,

```
combined=concatenate([x1,y2])
```

then apply fully connected layer on combined output,

```
# apply a FC layer and then a regression prediction on the
# combined outputs
z = Dense(2, activation="relu")(combined)
z1 = Dense(1, activation="linear")(z)
```

define the model and its input at the end,

```
# our model will accept the inputs of the two branches and
# then output a single value
model = Model(inputs=[inputA, inputB], outputs=z1)
```

Check the model summary,

```
model.summary()
```

![3](/assets/images/clt/non-linear-neural-networks/3.png)

at the end plot the model,

```
from keras.utils import plot_model
plot_model(model)
```

![4](/assets/images/clt/non-linear-neural-networks/4.png)

You can check out this [NOTEBOOK(functional-api-multiple-input.ipynb)](http://localhost:4000/2021/02/15/non-linear-neural-networks).

## Age Gender Project

Do necessary imports,

```
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
```

download the dataset on your notebook,

```
!kaggle datasets download -d jangedoo/utkface-new
```

unzip the dataset,

```
import zipfile
zip = zipfile.ZipFile("/content/utkface-new.zip",'r')
zip.extractall("/content")
zip.close()
```

import the datagenerator for data-augmentation,

```
import os
import numpy as np
import pandas as pd
from keras.preprocessing.image import ImageDataGenerator
```

define a path for data augmentation folder,

```
folder_path = '/content/utkface_aligned_cropped/UTKFace'
```

define the dataframe format,

```
age=[]
gender=[]
img_path=[]
for file in os.listdir(folder_path):
  age.append(int(file.split('_')[0]))
  gender.append(int(file.split('_')[1]))
  img_path.append(file)  
```

check length of age,

```
len(age)
```

create the dataframe,

```
df=pd.DataFrame({'age':age,'gender':gender,'img':img_path})
```

check the shape of dataframe,

```
df.shape
```

dataframe will look like this,

![5](/assets/images/clt/non-linear-neural-networks/5.png)

check the head,

```
df.head()
```

divide the data into train and test,

```
train_df=df.sample(frac=1,random_state=0).iloc[:20000]
test_df=df.sample(frac=1,random_state=0).iloc[20000:]
```

check the train shape,

```
train_df.shape
```

and the test shape,

```
test_df.shape
```

define the imageGenerator parameters for train and test data,

```
train_datagen = ImageDataGenerator(rescale=1./255,
                                   rotation_range=30,
                                   width_shift_range=0.2,
                                   height_shift_range=0.2,
                                   shear_range=0.2,
                                   zoom_range=0.2,
                                   horizontal_flip=True)

test_datagen = ImageDataGenerator(rescale=1./255)
```

generate the data with generators,

```
train_generator = train_datagen.flow_from_dataframe(train_df,
                                                    directory=folder_path,
                                                    x_col='img',
                                                    y_col=['age','gender'],
                                                    target_size=(200,200),
                                                    class_mode='multi_output')

test_generator = test_datagen.flow_from_dataframe(test_df,
                                                    directory=folder_path,
                                                    x_col='img',
                                                    y_col=['age','gender'],
                                                    target_size=(200,200),
                                                  class_mode='multi_output')
```

![6](/assets/images/clt/non-linear-neural-networks/6.png)

import the resNet50 model,

```
from keras.applications.resnet50 import ResNet50
from keras.layers import *
from keras.models import Model
```

create the instance of resnet50 and define its parameters,

```
resnet = ResNet50(include_top=False, input_shape=(200,200,3))
```

complete the model architecture by adding dense and flatten layers to resNet50,

```
resnet = ResNet50(include_top=False, input_shape=(200,200,3))

resnet.trainable=False

output = resnet.layers[-1].output

flatten = Flatten()(output)

dense1 = Dense(512, activation='relu')(flatten)
dense2 = Dense(512,activation='relu')(flatten)

dense3 = Dense(512,activation='relu')(dense1)
dense4 = Dense(512,activation='relu')(dense2)

output1 = Dense(1,activation='linear',name='age')(dense3)
output2 = Dense(1,activation='sigmoid',name='gender')(dense4)
```

define model with inputs and outputs,

```
model=Model(inputs=resnet.input,outputs=[output1,output2])
```

compile the model,

```
model.compile(optimizer='adam',loss={'age':'mae','gender':'binary_crossentropy'},metrics={'age':'mae','gender':'accuracy'},loss_weights={'age':1,'gender':99})
```

at the end fit the model,

```
model.fit(train_generator, batch_size=32, epochs=10, validation_data=test_generator)
```

![7](/assets/images/clt/non-linear-neural-networks/7.png)

You can check also check the code [NOTEBOOK(age-gender.ipynd)](https://colab.research.google.com/drive/1B2azaSX9g55olY473c7WAMf3E5-717Ge?usp=sharing#scrollTo=Z-K-t3f6Jgyj)