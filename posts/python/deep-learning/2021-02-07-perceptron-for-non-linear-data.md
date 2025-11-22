---
layout: post
title: Perceptron Issue for Non-Linear Data
date: 2021-02-07 20:52:55.000000000 +05:00
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
permalink: "/2021/02/07/perceptron-issue-for-non-linear-data"
---
Perceptron is no doubt the core-component of Deep-Learning. When it comes to single-perceptron. It is best suited for the Linear-Data. Linear-Data means which can be classified into two classes easily by a single-line or classifier. 

For this purpose, showing the classification results using multiple python codes. Initially import all the necessary libraries:

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns 

```
Then making 3-empty datasets using pandas-dataframe.
```

or_data=pd.DataFrame()
and_data=pd.DataFrame()
xor_data=pd.DataFrame()
```

Then fill-in the Dataframes:
```

or_data['input1']=[1,1,0,0]
or_data['input2']=[1,0,1,0]
or_data['output']=[1,1,1,0]
```

Then import the simple perceptron model from sklearn and make 3 instances of it:

```
from sklearn.linear_model import Perceptron
clf1=Perceptron()
clf2=Perceptron()
clf3=Perceptron()
```
Then fit-in the data using our datasets:

```
clf1.fit(and_data.iloc[:,0:2].values,and_data.iloc[:,-1].values)
clf2.fit(or_data.iloc[:,0:2].values,or_data.iloc[:,-1].values)
clf3.fit(xor_data.iloc[:,0:2].values,xor_data.iloc[:,-1].values)
```

If you plot the the clf1 and as it is trained on linearly separable data, it will look like this:

```
plt.plot(x,y)
sns.scatterplot(x='input1',y='input2',data=and_data,hue='output',s=200)
```

<!-- ![A test image](/assets/images/clt/image.png) -->
![Perceptron on linear-data image](/assets/images/clt/perceptron-for-non-linear-data/perceptron-linear-data1.png)

Similarly if you plot the second perceptron classifier instance, which was trained on ```or``` data. It will look like this:

```
plt.plot(x,y)
sns.scatterplot(x='input1',y='input2',hue='output',data=or_data,s=200)
```

![Perceptron on linear-data OR image](/assets/images/clt/perceptron-for-non-linear-data/perceptron-linear-data2.png)
You can also get the idea of it by a visul representation from [PlayGround.Tensorflow](https://playground.tensorflow.org/#activation=sigmoid&batchSize=10&dataset=gauss&regDataset=reg-plane&learningRate=0.01&regularizationRate=0&noise=10&networkShape=&seed=0.71127&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false)

![playgroundtensorflow](/assets/images/clt/perceptron-for-non-linear-data/playgrountensorflow.png)

Now if you apply the same single perceptron model on non-linearly separable data. It will look like this:

![Perceptron-non-linear-issue](/assets/images/clt/perceptron-for-non-linear-data/perceptron-non-linear-data3.png)

![Per-non-linear-issue-2nd-image](/assets/images/clt/perceptron-for-non-linear-data/perceptron-linear-data4.png)

Here you can see that our `Perceptron-Model` doesnot work for non-linear data. This was the issue with the use of single-perceptron.