---
layout: post
title: Multi Layer Perceptron Intuition
date: 2021-02-08 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Python
- Deep Learning
- Multi Layer Perceptron
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2021/02/08/multi-layer-perceptron"
---
As we know that a single perceptron is not able to classify non-linear data, you can check out my blog on this [Perceptron Issue](/2021/02/07/perceptron-issue-for-non-linear-data). So how we can classify non-linear data using `Multi-Layer-Perceptron`. 

We all know that a single-perceptron cannot converge on non-linear data. This means that it cannot draw the Decision Boundaries in the data. This is where multi-layer-percetpron comes into play. Multi-Layer-Perceptron uses smoothing and super-imposition concepts to draw the decision boundaries. The output of one layer of perceptron becomes the input for the next hidden layer and thus your classification results are ore and more accurate. Here is a basic MLP architecture:

![basic mlp network](/assets/images/rletters/deep-learning/mlp-1.jpeg)

## Layers Breakdown:
You can see here, we have multiple layers, each layer with multiple perceptrons. The initial layer labelled as 1 is the input layer, the middle layers with label 2 and 3 are the hidden layers and the layer 4 is called the output layer.

In a MLP-architecture,you've to calculate three things:
* Weight
* Bias
* Output

![mlp-2](/assets/images/rletters/deep-learning/mlp-2.jpeg)

Also at the end we combine the multiple perceptron outputs and pass them through the activation function. While in the case of single perceptron, the output z was passed through the activation function. But here in MLP, there are multiple hidden layers. Keep in mind that you can change the architecture of MLP using 4 methods:

* Increase the nodes in hidden layers
* Increase the nodes in input layer
* Increase the nodes in output layer
* Increase the number of hidden layers

Here you can see the basic training flow and the first two architecture changes.

![mlp-3](/assets/images/rletters/deep-learning/mlp-3.jpeg)

Also the examples of the 3rd and 4th way to change the mlp architecture can be demonstrated by below note snippet,

![mlp-4](/assets/images/rletters/deep-learning/mlp-4.jpeg)

Now, i'm going show some demonstrations of how well MLP performs on a non-linear data. Initially i'm taking a single hidden layer with 2 perceptrons in it. Let's see the results.

![mlp-5](/assets/images/rletters/deep-learning/mlp-5.png)

Let's test it out on a more complex non-linear dataset but we've increased a perceptron in the hidden layer. Here is the demonstration,

![mlp-6](/assets/images/rletters/deep-learning/mlp-6.png)

In the final-example, we are taking the most complex dataset among these. For this we'll use two hidden layers, each with 4 perceptrons in. Let's see how our Neural Network do the classification.

![mlp-7](/assets/images/rletters/deep-learning/mlp-7.png)

So far, this was all about the Multi-Layer-Perceptron(MLP). I hope my explaination will some abstract as well as some practical knowledge of MLP working.  