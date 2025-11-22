---
layout: post
title: Why RNNS are Needed? | RNNs VS ANNs
date: 2021-04-12 20:52:55.000000000 +05:00
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
permalink: "/2021/04/12/why-rnns-are-needed"
---
This question always come to mind. Why RNNS are needed when you have CNNs and ANNs? RNNs stand for Recurrent Neural Networks. It's a type of neural network most suited for Natural Language Processing tasks. They are used to deal with Sequential Data that's why they are better known as sequential models. You may ask what is sequential data. The data in which following the order is must is known as sequential data.

Let me explain you with an example, suppose you've a dataset of textual sentences. Pick one sentense from the dataset, e.g

```
I'll go to school.
```

You cannot write,

* School to go I'll 

or 

*To School go I'll

b/c they don't give us any information. It means sequence is important to us and we call this type of data as Sequential Data. Other examples of Sequential Data are,

* Time Series Data

* Speech

* DNA Sequence 

Now what if we use ANNs or CNN to solve sequential data problems. Assume you've a student dataset with input features,

* iq
* gender
* marks

and you've to predict the placement of student. For an ANN you cannot directly feed the textual data. We must have to vectorize the words. For this purpose we use the simplest method of 1 hot encoding with 12 numbers long vector for each number. It may look like,

```
I'll [1 0 0 0 0 0 0 0 0 0 0 0]

go [0 1 0 0 0 0 0 0 0 0 0 0]

to [0 0 1 0 0 0 0 0 0 0 0 0]

school [0 0 0 1 0 0 0 0 0 0 0 0]
```

Now we've to arrange these vectors vertically and make a vectors stack. 

![1](/assets/images/clt/why-rnns-are-needed/1.png)

You can see for first sentence we'll have 192 trainable parameters only for first hidden layer. Similarly for the next sentence of dataset.

```
How are you?
```

![2](/assets/images/clt/why-rnns-are-needed/2.png)

We will have 3 inputs, while last sentence were passing 4 inputs so its not possible for ANNs to take inputs of different size. In order to solve this we will do zero-padding and will add an extra vector with all zeros in it b/c input size for all inputs should be same. 

Now take an example of large scale datasets, here take a look,

![3](/assets/images/clt/why-rnns-are-needed/3.png)

lets suppose,we have maximum 100 words and minimum 5 words sentences in a dataset but as we are using ANNs so we must have to make input shape same for all sentences, this means we will have 100 vectors for all the sentences even for the small ones with the zero padding. We are using vector with 10000 numbers for a single word so,

```
10000x100=1000000

Now if first hidden layer have 10 neurons then, 

1000000x10=10000000

```

We have a high number of trainable parameters and most of them are with zero vectors which is totally a computational anomly and is inefficient. There are total of four problems in ANNs for sequential data,

* Variable text input make ANNs unsuitable
* Zero Padding will cause unnecessary computations
* Even if we train the ANNs on sequential data, the prediction will still be not good
* ANNs will disregard the sequence information

This last point is the biggest problem because ANNs doesnot have any capability of storing memory so they cannot retain information. Therefore we needed a new architecture for sequence based data and then came the RNNs. There are multiple application of RNNs like,

* Sentiment Analysis
* Ecommerce Customer Behaviour Analysis
* Sentence Completion (Gmail)
* Mobile Phone Text Keywords
* Image Caption Generation
* Translation (Google Translate)
* Question Answer Systems
