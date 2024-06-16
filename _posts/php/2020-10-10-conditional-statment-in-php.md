---
layout: post
title: Conditional Statements in PHP  
date: 2020-10-10 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Php
- Web
- Server
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2020/10/10/conditional-statements-in-php"
---
Conditional statements in php are almost similar to **C++**. You write if, else followed by a **small parenthesis** with condition in it and then opening and closing **curly-brackets** in the end. I've solved some basic examples in my IDE. Let me share the explaination and code with you.

## If-Conditions

In the below code, i'm declaring a variable `$age` with a value of `10` in it. Then i'm performing comparison that if this age is less than 18 then execute this block of code.

```
<?php

$age=10;

if ($age<18){
    echo "Display kid content";
}

echo "<br/>";

?>

```

In another example, i've declared a variable `$name` with a string value `SANDY` stored in it. Then i'm performing a check that the string stored in variable `$name` is SANDY then execute the block of code.

```
<?php

$name='SANDY';

if ($name=='SANDY'){
    echo "<h1>Welcome SANDY</h1>";
}

echo 'other';

?>

```

## If-Else Conditions

In case of `if-else` statements. At first, the if statement is check. If it is satisfying the condition, the block of code in it executes and all the remaining `else` statements will be ignored. But in case if the if statment does not satisfy the give statement then the block of code in the `else` statement will be executed. You can visualize the working of `if-else` statements by a diagram given below,
![1](/assets/images/clt/conditional-statments-in-php/1.png)
Also, here is an example of age-check in php,
```
<?php

$age=30;
if($age>18){
    echo "Welcome to website <br>";
}
else{
    echo "You are under-age <br>";
}

>?
```

Similarly in the second example, i'm applying the conditional statment on the variable `$name`,

```
<?php

$name="Peter";
if($name=="SANDY"){
    echo "welcome Back, $name <br>";
}
else{
    echo "$name name not present in our Database <br>";
}

?>
```

## Else-If Conditions
If we want to execute one statment but we want to do multiple checks then we use `elseif` condition. Here in the below code, we want to execute only block of code where `$country=="France"` condition is satisfied.

```
<?php

$country="France";
if($country=="Pakistan"){
    echo "this is an asian country";
}
elseif($country=="France"){
    echo "this is an asian country";    
}
elseif($country=="Germany"){
    echo "this is an european country";
}
elseif($country=="Canada"){
    echo "this is an north american country";
}
else{
    echo "unknown"
}

?>
```

## Switch Statements

**Switch** statments works just like an **if-else statements**, but if you've multiple conditions like ten or twenty checks then it will be better to use switch statements. It helps in getting more organized code. The keyword use for switch statment is `switch` followed by `case "ANYCASE":` and then `default:` at the end. Here is an example code written by me for better understanding. In this example, the **red** case will be executed and we will get the statment **red color is my favourite color** on the browser.  

```
<?php

$favouriteColor="red";
switch ($favouriteColor){
    case "red":
        echo "red color is my favourite color";
        break;
    case "blue":
        echo "blue color is my friends color";
        break;
    case "yellow":
        echo "yellow is my least favourite color";
        break;
    default:
        echo "this color is not matched";
        break;
}

?>
```

## Logical Operators

There are few logical operators in php. They are enlisted below:
* AND
* OR 
* XOR
* NOT

The logical operator `and` is used when both expressions should be satisfied for a block of code to run. 

```
<?php

$a=10;
$b=20;
$c=30;
if($a==10 and $b==20){
    echo "var a has 10 value";
}

?>

```
It can also be written as `&&` in php.

```
<?php

$a=10;
$b=20;
$c=30;
if($a==10 && $b==20){
    echo "var a has 10 value";
}

?>

```

`or` operator is used where only one expression true will start the execution of the block of code.

 ```
<?php

$a=10;
$b=20;
$c=30;
if($a==10 or $b==20){
    echo "condition is true";
}

?>

```

It can also be written as `||` in php code.

 ```
<?php

$a=10;
$b=20;
$c=30;
if($a==10 || $b==20){
    echo "condition is true";
}

?>

```

Next is `xor`. This logical operator return false when both of the expressions are true or false at the same time.

```
<?php

$a=10;
$b=20;
$c=30;
if ($a==50 xor $b==30){
    echo "condition is true";
}

?>
```

The next logical operator is `not`, it is used when certain expression in not true.

```
<?php

$a=10;
$b=20;
$c=30;
if ($a!=10){
    echo "condition is true";
}

?>
```


You can use logical operators for three or more expressions together.

For this purpose, here is an example number 1,

```
<?php

$a=10;
$b=20;
$c=30;
if($a==10 &&  $b==20 && $c==30){
    echo "condition is true";
}

?>

```

Another example is attached below,

```
<?php

$a=10;
$b=20;
$c=30;
if($a==10 ||  $b==20 || $c==30){
    echo "condition is true";
}

?>

```