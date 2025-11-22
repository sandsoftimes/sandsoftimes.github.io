---
layout: post
title: Softmax Function and Variance in Python
date: 2021-04-16 20:52:55.000000000 +05:00
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
permalink: "/2021/04/16/softmax-and-variance"
---
Softmax function is one of the most widely used activation function in deep learning. Applying it on a data with high variance and cause problems. Therefore we most provide the scaled data with low variance to this activation function. The implementation of softmax is very simple. Here is few lines code showing the implementation of softmax,

First of all import all the necessary libraries,

```
import numpy as np 
import matplotlib.pyplot as plt 
```

then here is the softmax,

```
def softmax(x):
  # Ensure numerical stability by subtracting the max value from each element
  e_x=np.exp(x-np.max(x))
  softmax_values=e_x/e_x.sum(axis=0) # Normalize
  percent_values=softmax_values*100 #convert to percent
  #Format each value to a string with 2 decimal places followed by a percent sign
  formatted_percent_values=[f"{value:.2f}%" for value in percent_values]
  return formatted_percent_values
```

you can check it by apply on any vector of any dimension,

```
softmax(np.array([1,10]))
```

![1](/assets/images/clt/softmax-and-variance/1.png)

also variance is a big problem in deep learning. You've to make sure the vector/scalar passed to softmax function has low variance other wise, the softmax will push the values to both maximum and minimum extremes. Check the variance by using the built in function numpy function `var`

```
np.array([10,20,30,40,50,60,70]).var()
```

![2](/assets/images/clt/softmax-and-variance/2.png)

values close to each other (with less difference) have small variance,

```
np.array([1,2,3,4,5,6,7]).var()
```

![3](/assets/images/clt/softmax-and-variance/3.png)