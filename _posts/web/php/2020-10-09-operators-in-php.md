---
layout: post
title: Complete PHP Operators Toolkit and its Working Manual  
date: 2020-10-09 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Web
- PHP
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2020/10/09/operators-in-php"
---
Lets talk about the operators. Operators are used between the operands to perform any type of operation. Like the other programming languages, php also have a wide variety of operators which are used for multiple purpose. The basic syntax of operators is almost same like the other programming languages. In this blog i'll share the complete details of all types of operators used in php.

Php operators are as follow:

* Arithematic Operator 

* Assignment Operator

* Comparison Operator

* Increment/Decrement Operator

* logical Operator

* String Operator

* Array Operator

Arithematic operators are the most common one. They include **additon, subtraction, multiplication, division e.t.c**. Also there are some comparision operators which perform the comparison. Here is an example of basic arithematic operation of addition,
```
<?php
$a=5;
$b=6;
echo $a+$b;
?>
```
Also below is an another example in which we are using comparison operator `==`. 
```
<?php
$a=10;
$b=10;
echo $a==$b;
?>
```

## Arithematic Operator

Above was the general overview of operations. Now i'm going to perform multiple arithematic operation using php code.
```
<?php
$a=20;
$b=10;
echo $a+$b;
echo "<br>";
echo $a-$b;
echo "<br>";
echo $a/$b;
echo "<br>";
echo $a*$b;
echo "<br>";
echo $a%$b;
echo "<br>";
echo $a**$b;
echo "<br>";

const num1=20;
const num2=30;
echo num1*num2;
echo "<br>";

echo 10*10;
echo "<br>";
?>
```
The output of the above php code will be,
![1](/assets/images/clt/operators-in-php/1.png)

## Assignment Operator

Now we will talk about the assignment operator. It is used to assign values. You can look at the chart below for better understanding.

![](/assets/images/clt/operators-in-php/2.png)

Also i've written an example code, in which i've solved all of the above types,
```
<?php
$a=5;
$b=20;

$a=$b;

$a=$a+$b;
$a+=$b;

$a-=$b;
$a=$a-$b;

$a=$a*$b;
$a*=$b;

$a=$a/$b;
$a/=$b;

$a=$a%$b;
$a%=$b;

$a=$a**$b;
$a**=$b;

echo $a;
?>
```

## Comparison Operator

There are also multiple comparison operators in php. I'm attaching a chart for better understanding.
![3](/assets/images/clt/operators-in-php/3.png)

First if we talk about **Equal** operator. It simply return bool if condition is satisfied. 

```
<!-- Value Comparison  -->

<?php
$a=10;
$b=10;
$c="10";

var_dump($a==$c);
?>
```

Then we've **Identical** operator. It also check whether the type of comparison operands is also same or not.

```
<!-- Type Checking Comparison -->

<?php
$a=10;
$b=10;
$c="10";

var_dump($a===$c);
?>
```

Then we've **Not Equal To**  operator. It return boolean value on the basis of whether condition is satisfied or not.

```
<!-- Not Equal To Operator -->

<?php
$a=10;
$b=10;
$c="10";
$d=5;


var_dump($a!=$d);
?>
```

There is another way to write **Not Equal To** operator.

```
<!-- Second Way of Not Equal To -->

<?php
$a=10;
$b=10;
$c="10";

var_dump($a<>$c);
?>

```

Then we've **Not Identical** operator. It also do comparison and check the type of both operands being compared.

```
<!-- Not Identical Operator-->

<?php
$a=10;
$b=10;
$c="10";

var_dump($a!==$c);
?>
```
The next is **Greater Than** operator. It result boolean value if the `$a is greater than $b`.

```
<!-- Greater Than Operator -->

<?php
$a=10;
$b=10;
$c="10";

var_dump($a>$c);
?>
```

**Less Than** operator is the inverse of **Greater Than** operator.

```
<!-- Less Than Operator -->

<?php
$a=10;
$b=10;
$c="10";

var_dump($a<$c);
?>
```

The final one is the **Spaceship Operator**. Spaceship operator returns -1 if $a is less than c. It will return 0 if $a==$c and it will return 1 if $a<$c;

```
<!-- Spaceship Operator -->

<?php
$a=10;
$b=10;
$c="10";

var_dump($a<=>$c);

/*
Spaceship operator returns -1 if $a is less than c. It will return 0 if $a==$c and it will return 1 if $a<$c;
*/

?>
```

## Increment and Decrement Operators

The increment and decrement operatos can be used in two ways,
* Pre
* Post

An overview chart is attached below,
![4](/assets/images/clt/operators-in-php/4.png)

Example of **Pre-Increment** operator is,

```
<!-- Pre-Increment -->

<?php
$a=10;
echo ++$a;
?>

```

Example of **Post-Increment** operator is,

```
<!-- Post-Increment -->

<?php
$a=10;
echo $a++;
?>
```

Example of **Pre-Decrement** operator is,

```
<!-- Pre-Decrement -->

<?php
$a=10;
echo --$a;
?>
```

Example of **Post-Decrement** operator is,

```
<!-- Post-Decrement -->

<?php
$a=10;
echo $a--;
?>
```

## Strings and String Operators in PHP

Strings is a any combination of words, letters or symbols enclosed in quotations `''`. You can store the string inside a variable or you can print in directly. In alongside the strings, there are two string operators.

* Dot Operator
* Dot Assignment Operator

Initially if we talk about the dot operator, it is used to write variable values with strings or to write multiple string one after another,

```

<?php
$name='SANDY';
$age=22;
echo "My name is " .$name . "<br>";
echo "My age is " .$age;
echo "My name is " .$name. ' and my age is ' .$age;
?>
```

The second dot assignment operator is used to concatenate one string to the other,

```
<?php
$str="Hello How are you? ";
$str1="My name is SANDY";
$str.=$str1;
echo '<br>';
echo $str;
?>
```

