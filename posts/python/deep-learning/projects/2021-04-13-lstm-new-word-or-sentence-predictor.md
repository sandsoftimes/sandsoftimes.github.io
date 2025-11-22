---
layout: post
title: LSTM | Text Generation using Supervised Learning
date: 2021-04-13 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Python
- Deep Learning
- Project
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2021/04/13/lstm-new-word-or-sentence-predictor"
---
LSTM are a pretty good replacement of RNNS's. I'll show the working of LSTM's with a complete project. Our final model will take an input, whether it is a word or a phrase and predict the rest of the sentence by itself. Also you can ask any type of new query from the model and it will answer you. By some tinkering, i've made the model to act as a supervised learning model.

Initially we need to create a dataset, for this purpose i'm using a dummy dataset of sentences, here it is,

```
faqs = """
About the Training
What is the enrollment cost for the Data Analytics Guidance Program (DAGP 2024)?
The program operates on a subscription basis where you pay Rs 899 monthly.
How long is the entire program?
The full duration is 6 months, making the total fee Rs 899 * 6 = Rs 5400 approximately.
What is the curriculum for the training?
We will cover the following topics:
- Basic Python for Analytics
- Key Data Science Libraries
- Data Cleaning Techniques
- Database Management with SQL
- Math Concepts for Data Analytics
- Machine Learning Models
- Real-world ML Projects
- MLOps Overview
- Industry Case Studies
You can view the detailed syllabus here: https://dataschool.co.in/programs/DAGP-2024/curriculum.

Does this program cover NLP and Deep Learning?
No, Deep Learning and NLP are not part of this training.
What if I miss a live session? Will there be a recording?
Yes, all sessions are recorded, so you can access them if you miss one.
Where can I find the schedule?
You can view the program calendar here: https://dataschool.co.in/schedule/DAGP-2024.
How long are the live sessions?
Each session runs for about 1.5 to 2 hours.
What language will the instructor use?
The sessions are conducted in Hinglish.
How will I know about upcoming classes?
We’ll send email notifications before every scheduled session for paid participants.
Can non-technical participants join?
Yes, this course is beginner-friendly.
Can I join the course mid-way?
Yes, you can enroll at any point during the program.
Will I have access to previous lectures if I join late?
Yes, once you pay, you’ll gain access to all past lectures in the dashboard.
Do I need to submit assignments?
No, we provide solutions for self-assessment purposes.
Will the program include case studies?
Yes, we’ll work through real case studies.
How can I contact support?
For inquiries, email us at support@dataschool.co.in.

Payment/Registration Questions
Where should I make the payment?
All payments should be made on our official website: https://dataschool.co.in/payments.
Can I pay the full Rs 5400 in one go?
No, the payments are split into monthly installments.
If I pay mid-month, when is the next payment due?
Your next payment is due 30 days after your first payment date. For example, if you pay on the 10th, your next payment is due on the 10th of the following month.
Is there a refund policy if I don't like the course?
Yes, you have a 7-day refund period after making the payment.
What if I live outside India and can’t make the payment online?
Please email support@dataschool.co.in for assistance.

Post-Registration Queries
How long can I access the paid content?
You can access videos as long as your subscription is active. After completing all payments (totaling Rs 5400), you’ll have access until September 2025.
Why isn't lifetime access available?
Due to the low cost of the course, lifetime access is not offered.
Where can I go for help after a session?
You can fill out a form on your dashboard, and our team will arrange a 1-on-1 doubt-clearing session.
Can I ask questions related to sessions I missed from previous weeks?
Yes, simply select "previous week" in the doubt form.
What if I face payment issues while living abroad?
You can reach out to support@dataschool.co.in for help.

Certificate and Placement Queries
How do I qualify for a certificate?
Two conditions apply:
1. You must pay the full Rs 5400.
2. You need to complete all assessments.
I joined late—how do I pay for previous months?
Once you make your first payment, you will see links in your dashboard to pay for the earlier months.
Does the program offer job placement services?
While we provide placement support, it is not a job guarantee. The assistance includes:
- Sessions on portfolio building
- Soft skills workshops
- Interaction with industry experts
- Guidance on job search strategies.
"""
```

you can check the dataset via variable,

```
faqs
```

now this data is in textual form but we cannot feed or use textual data to our model, so we need to convert it into vectors/numbers so import tokenizer and necessary libraries,

```
import tensorflow as tf
from tensorflow.keras.preprocessing.text import Tokenizer 
```

create a tokenizer instance,

```
tokenizer = Tokenizer()
```

fit the tokenizer on given raw data,

```
tokenizer.fit_on_texts([faqs])
```

you can check the token words along with their index,

```
tokenizer.word_index
```

split the raw data on the basis of new line character `\n` and store all in a list,

```
input_sequences=[]
for sentence in faqs.split('\n'):
  # print(sentence)
  # print(tokenizer.texts_to_sequences([sentence])[0])
  tokenized_sentence=tokenizer.texts_to_sequences([sentence])[0]

  for i in range(1,len(tokenized_sentence)):
    input_sequences.append(tokenized_sentence[:i+1])
```

check for the sentence/sequence for the max length for zero padding of vectors,

```
max_len=max([len(x) for x in input_sequences])
max_len
```

perform the padding,

```
from tensorflow.keras.preprocessing.sequence import pad_sequences
padded_input_sequences=pad_sequences(input_sequences,maxlen=max_len,padding='pre')
padded_input_sequences
```

split the output and output features into x and y so to make a proper dataset,

```
x=padded_input_sequences[:,:-1] #except last colm
# padded_input_sequences[:,-1]
y=padded_input_sequences[:,-1]
```

check the shape of x and y,

```
print(x.shape)
print(y.shape)
```

check the total token words,

```
len(tokenizer.word_index)
```

convert the output scalar y into a vector,

```
from tensorflow.keras.utils import to_categorical
y=to_categorical(y,num_classes=283)
```

check the shape,

```
y.shape
```

now lets make our model, import the necessary libraries,

```
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Embedding,LSTM,Dense
```

create the model,

```
model=Sequential()
model.add(Embedding(283,100,input_length=56))
model.add(LSTM(150))
model.add(Dense(283,activation='softmax'))
```

compile the model,

```
model.compile(loss='categorical_crossentropy',optimizer='adam',metrics=['accuracy'])
```

check the model summary,

```
model.summary()
```

fit the model on x and y,

```
model.fit(x,y,epochs=100)
```

lets take a word, tokenize it, do zero padding and predict the next word from it using the model,

```
import numpy as np
text="mail"

token_text=tokenizer.texts_to_sequences([text])[0]

padded_token_text=pad_sequences([token_text],maxlen=56,padding='pre')
pos=np.argmax(model.predict(padded_token_text))
for word,index in tokenizer.word_index.items():
  if index==pos:
    print(word)
```

inorder to predict a complete sentence, use for loop,

```
import time
import numpy as np
text="NLP and Deep Learning both"

for i in range(10):
  token_text=tokenizer.texts_to_sequences([text])[0]
  padded_token_text=pad_sequences([token_text],maxlen=56,padding='pre')
  pos=np.argmax(model.predict(padded_token_text))

  for word,index in tokenizer.word_index.items():
    if index==pos:
      text=text+ " "+ word
      print(text)
      time.sleep(2)
```
![1](/assets/images/clt/lstm-new-word-or-sentence-predictor/1.png)

another demo is, 

```
import time
import numpy as np
text="total duration of the course"

for i in range(10):
  token_text=tokenizer.texts_to_sequences([text])[0]
  padded_token_text=pad_sequences([token_text],maxlen=56,padding='pre')
  pos=np.argmax(model.predict(padded_token_text))

  for word,index in tokenizer.word_index.items():
    if index==pos:
      text=text+ " "+ word
      print(text)
      time.sleep(2)
```
![2](/assets/images/clt/lstm-new-word-or-sentence-predictor/2.png)