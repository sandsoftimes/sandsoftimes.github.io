---
layout: post
title: GRU | Gated Recurrent Unit Architecture
date: 2021-04-14 20:52:55.000000000 +05:00
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
permalink: "/2021/04/14/why-rnns-are-needed"
---
Here i've discussed the complete Architecture of Gated Recurrent Unit. This is a type of RNN pretty similar to LSTM but a bit faster from the LSTM. Although it outperforms the LSTM in some problems while there are some cases where you still need to use LSTM's. It is better to test out both techniques to find good results on your problem.

Here is some basic intuition and introduction GRU,

![1](/assets/images/clt/gated-recurrent-unit/1.png)

similary here is some sentences with timestamps along with the Update and Rest gates.

![2](/assets/images/clt/gated-recurrent-unit/2.png)

rest gate working is down below,

![3](/assets/images/clt/gated-recurrent-unit/3.png)

here is some mathematical chart representation,

![4](/assets/images/clt/gated-recurrent-unit/4.png)

a basic neural netwok representation with point-wise addition b/w rest game and previous hidden state/context

![5](/assets/images/clt/gated-recurrent-unit/5.png)

update gate working and final hidden state/context calculation,

![6](/assets/images/clt/gated-recurrent-unit/6.png)