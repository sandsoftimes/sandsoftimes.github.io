---
layout: post
title: PHP Loops, a Complete Guide and Implementaion with Examples
date: 2020-10-11 20:52:55.000000000 +05:00
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
permalink: "/2020/10/11/all-about-php-loops"
---
Loop are used when ever you want to repeat the same thing in your code. Mostly they are used in these cases,

* Display Series Number
* Display List of Users
* Make Table of Data

Also keep in mind that there are four types of loops in php,

* for
* while
* do while
* forEach

Firstly if we talk about the for-loop. It will take 3-things,

* Starting Statament
* Ending Statment
* Increment/Decrement 

Here is a basic example of `for` loop,

```
<?php

for($start=0;$start<=10;$start++){
    echo $start;
    echo " code step by step <br>";
    echo "SANDY <br>";
}

?>
```

It will print the count **from 0 to 10**. The it will print the string **code step by step**. At the end it will print the string the string **SANDY**. All these printing will be done for ten times.

Here is another code for printing the table of numbers,

```

$table=10;
for($start=1;$start<=10;$start++){
    echo $table*$start ."<br>";
}

?>

```
Below is an example of using `$i` as starter and printing the value of it,

```
<?php

for ($i=0;$i<10;$i++){
    echo "current i value is $i <br>";
}

?>
```

## Break and Continue Statments

If you want to break loop in the middle or any special interval during the execution, we use **break** statment. You can get the idea of it by an example code,

```
<?php

for($i=0;$i<10;$i++){
  if ($i==5){
    break;
}
  echo $i;
  echo "<br>";
}

?>
```

The loop will stop execution when the value of `$i` becomes equal to `5`;

Now the **continue** statements are used when every we want to skip some portion of code to be executed.

```
<?php

for($i=0;$i<10;$i++){
    if($i==3 || $i==7){
        continue;
}
    echo $i;
    echo "<br>";
}

?>
```

Here when the `$i` will be equal to `3` or `7`. The rest of the portion in the code will not be executed.

## Nested Loop

Loop inside a for-loop are called **nested for-loop**. Nested for loops are used where complex logic is required. Forexample, working with **multi-dimensional-arrays**. 

```
<?php

for($i=1;$i<=3;$i++){
    for($j=1;$j<=3;$j++){
        echo "$i   $j <br/>";
}
}

?>
```

## While Loop

Just like the `for` loop, we also have `while` loop in php. The `while` loop syntax is a bit different. You do initial declaration outside, before the loop and it has the increment/decrement statements inside the loop body. Here is a very simple example of it,

```
<?php

$num=10; //initial value

while($num>0){
    echo $num;
    echo "<br/>";
    $num--;
}

?>
```

Also if you want to print values in descending order. Use this code,

```
<?php

$num=10; //initial value

while($num>0){
    echo $num;
    echo "<br/>";
    $num--;
}

?>
```

## Do-While Loop

Do while loop look similar to while loop but it is a bit different. In it, we write logic/code first then we write the stoping condition. So minimum this loop will excute must for the first time. Here is an example of it. Also keep in mind, we use the keyword **do** in this loop,

```
<?php

$num=0;
do{
echo "Current loop value is $num <br/>";
$num++;
}while($num<=10;);

?>


```

## Go-To Statement

Whenever you want to skip some portion of code and jump to some point, we use go to statement. It is written in simple keywords of `goto`. The lines below the goto statments will not be executed. An example of it is,

```
<?php
$x=20;
echo "before condition <br/>";

if($x==20){
    goto jump
}
$name="SANDY <br/>";
echo $name;

jump:
echo "statment is jumped on line number 15";

?>
```
Also you can use it inside a loop. Here the loop will run **5** times and then `goto` statment will be executed,

```
<?php

for($i=0;$i<10;$i++){
    echo "$i <br>";  
    if($i==5){
        goto outsideLoop;
}  
}

outsideLoop:
echo "loop is break";
?>
```

Also keep in mind, if the statement to which you are applying `goto` is above the `goto` call then you'll most likly stuck in an infinite loop. Here is how,

```
<?php

outsideLoop:
echo "loop is break";

for($i=0;$i<10;$i++){
    echo "$i <br>";  
    if($i==5){
        goto outsideLoop;
            }  
                    }

?>
```