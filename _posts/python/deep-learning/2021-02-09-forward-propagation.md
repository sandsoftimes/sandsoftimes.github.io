---
layout: post
title: Forward Propagation in Multi-Layer-Perceptron
date: 2021-02-09 20:52:55.000000000 +05:00
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
permalink: "/2021/02/09/forward-propagation-in-multi-layer-perceptron"
---
Generally `Back-Propagation` is the main algorithm to train the neural network but before it, we need to do a forward pass which is known as `Forward Propagation`. Inputs are given through input layer with the weights. Simple linear algebra which includes matrix multiplication is used.

![1](/assets/images/clt/forward-propagation/1.jpeg)

We need to know how a neural network predict. For this purpose we need to understand the flow. Initially you've to identify the `total trainable parameters`. Here in this case we have 4 inputs and 3 hiddens layers. Find the total connections,

![2](/assets/images/clt/forward-propagation/2.jpeg)

This forward pass will be used to check the prediction. In the back the dot product b/w the inputs and weights is taken place with addition with the bias.

```
input*weights+bias
```
Here is the full calculations,

![4](/assets/images/clt/forward-propagation/4.jpeg)

To understand the full flow in one go. I've solved a complete example with all mathematical calculations. You'll get enough idea from it.

![new1](/assets/images/clt/forward-propagation/new1.jpeg)

![new2](/assets/images/clt/forward-propagation/new2.jpeg)

The ouput of first hidden layer will become input for the next hidden layer,

![3](/assets/images/clt/forward-propagation/3.jpeg)

Atlast sigmoid function will be applied on the output obtained from the output layer and we'll have a value in 1x1 matrix.

![new3](/assets/images/clt/forward-propagation/new3.jpeg)

