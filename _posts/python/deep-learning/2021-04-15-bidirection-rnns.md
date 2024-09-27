---
layout: post
title: Bidirectional RNN | LSTM | GRU Implementation
date: 2021-04-15 20:52:55.000000000 +05:00
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
permalink: "/2021/04/15/bidirection-rnns"
---
There are some problems where ordinary RNN architectures fail b/c of uncertainty. The most common example of it is the real-time voice to text recognition, we don't know what the person is going speak next i.e the problem in which we need the future information, we need bidirection rnns for it.

For this purpose, we will use the `Bidirectional` built in wrapper of keras. Initially import the libraries and the wrapper,

```
import tensorflow as tf
from tensorflow.keras.datasets import imdb
from tensorflow.keras.preprocessing.sequence import pad_sequences
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Embedding,Bidirectional,SimpleRNN,LSTM,GRU,Dense
```

load the dataset and do train test split

```
num_words=10000
(x_train,y_train),(x_test,y_test)=imdb.load_data(num_words=num_words)
```

pad the training and testing data

```
maxlen=100
x_train=pad_sequences(x_train,maxlen=maxlen,padding='post',truncating='post')
x_test=pad_sequences(x_test,maxlen=maxlen,padding='post',truncating='post')
```

set the embedding dimensions for future use,

```
embedding_dim=32
```

## Sequential Model for SimpleRNN with Bidirectional Wrapper

Create the sequential model for simpleRNN with all the layers,

```
model=Sequential([
    Embedding(input_dim=num_words,output_dim=embedding_dim,input_length=maxlen),
    Bidirectional(SimpleRNN(5)),
    Dense(1,activation='sigmoid')
])
```

compile the model and check the summary

```
model.compile(optimizer='adam',loss='binary_crossentropy',metrics=['accuracy'])
model.summary()
```

## Sequential Model for GRU with Bidirectional Wrapper

Again make a sequential model for a GRU and wrap it in a bidirectional wrapper

```
mode=Sequential([
    Embedding(input_dim=num_words,output_dim=embedding_dim,input_length=maxlen),
    Bidirectional(GRU(5)),
    Dense(1,activation='sigmoid')
])
```

compile the model and check its summary

```
model.compile(optimizer='adam',loss='binary_crossentropy',metrics=['accuracy'])
model.summary()
```

## Sequential Model for LSTM with Bidirectional Wrapper

One last time make a sequential model for lstm and put it in bidirectional wrapper

```
model=Sequential([
    Embedding(input_dim=num_words,output_dim=embedding_dim,input_length=maxlen),
    Bidirectional(LSTM(5)),
    Dense(1,activation='sigmoid')
])
```

compiler the model and check its summary

```
model.compile(optimizer='adam',loss='binary_crossentropy',metrics=['accuracy'])
model.summary()
```