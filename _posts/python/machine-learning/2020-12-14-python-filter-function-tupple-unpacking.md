---
layout: post
title: Filter Function, Dictionaries And Tupple Unpacking in Python
date: 2020-12-14 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Python
- Basics
- Programming
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2020/12/14/python-filter-function-tupple-unpacking"
---
Today, i'm going to introduce you to python's Tupple Unpacking, Lambda function and Filter function. We are also going to discuss some Methods in python. These are widely used when working with python. I'm going to discuss each one by one.

First of all, when it comes to lambda expressions, they are one of the powerful feature in python. They are basically a functions that can be defined in single line, making code more concise and clean. Below is the example of lamba function in python, to double a variable.

```
times2 = lambda var: var * 2
result = times2(6)  # This will give you 12

```

Lambda expressions are commonly used when working with lists and Pandas library. Below is the example, in which we are using the lambda function with the '**map'** funtion to perform operation on every element of a list.

```
seq = [1, 2, 3, 4, 5]
doubled_seq = list(map(lambda num: num * 2, seq))

```

Now talking about '**filter'** function. It is also very handy tool in python. It allows you to filter elements from a list based on a specified condition. Below is the example of filter expression to filter even numbers from a sequence. You can use a lambda expression with filter function.

```
seq = [1, 2, 3, 4, 5]
even_numbers = list(filter(lambda num: num % 2 == 0, seq))

```

This function takes values from the list, applies the provided condition, and returns the values that satisfy it. To obtain a more readable result, wrap the **filter** function with the **list** function.

Lets talk about the Methods and String Manipulation in python. Python strings comes with alot of methods to extract useful information from them. e.g **lower()** method is used to convert a string to lowercase or **upper()** is used to convert a string to uppercase. Similarly **split()** method is used for breaking of s string into substring, based on spaces or other characters. Example is attached below.

```
s = 'hello my name is Sam'
s_lower = s.lower()
s_upper = s.upper()
words = s.split()  # Splits the string into individual words

```

Also, you can use split() method with a specific character as a separator, which can be very handy for a handling hashtags in social media content.

```
tweet = 'Go Sports! #Sports'
hashtags = tweet.split('#')  # Results in ['Go Sports!', 'Sports']

```

Dictionaries and lists are fundamental data structures in Python. With dictionaries, you can access values using keys, retrieve keys, or get a list of key-value pairs. For instance,

```
d = {'k1': 1, 'k2': 2}
keys = d.keys()    # Returns the dictionary keys
items = d.items()  # Returns key-value pairs
values = d.values()  # Returns values associated with keys

```

When working with lists, you can perform various operations, such as adding or removing elements. You can use the `pop()` method to remove elements from the list, and specify the index to remove a specific item.

```
lst = [1, 2, 3]
item = lst.pop()  # Removes and stores the last item, 'item' will be 3
first = lst.pop(0)  # Removes and stores the first item, 'first' will be 1

```

You can also check if an item exists in a list using the `in` operator.

Tuple unpacking is a another powerful technique often used in loops. It allows you to extract elements from tuples within a list quickly. For example, given a list of tuples,

```
x = [(1, 2), (3, 4), (5, 6)]

```

You can use tuple unpacking to access the elements in these tuples,

```
for item in x:
    print(item)

```

This code will print all the tuples in the list. Tuple unpacking can help you work with specific elements within each tuple,

```
for (a, b) in x:
    print(a)  # Prints 1, 3, 5

```

Or,

```
for (a, b) in x:
    print(b)  # Prints 2, 4, 6

```

Tuple unpacking simplifies the process of working with data in lists and enhances code readability.
