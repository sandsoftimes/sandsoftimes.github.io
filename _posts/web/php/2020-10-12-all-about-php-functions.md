---
layout: post
title: PHP Functions, a Complete Guide and Implementation with Examples
date: 2020-10-12 20:52:55.000000000 +05:00
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
permalink: "/2020/10/12/all-about-php-functions"
---
Function are one of the most important component of any programming language. Function is basically a block of code that you want to use repeatidly. Function have two major things.

* Function Declaration
* Function Call

Function is declared initially and later on it is called whenever needed. There are two main types of functions,

* Built-in Functions
* User-defined Functions

Built-in functions are prebuild in language and we use them by giving a simple function call. The most common example of built-in function is `var_dump()`. Secondly the user-defined functions are defined by user himself. The syntax of defining a function in php is very simple. You simple have to write `function` keyword then `function_name` and after it you write small parenthesis `()` and following it comes the pair of curly braces `{}`. 

There are multiple functions if you categorize them on the basis of their functionality. I'm listing some of them,

* Built-in Function
* User-defined Function
* Simple Function
* Returning Value Function
* Anonymous Function
* Parameterize Function
* Variable Function

Now let us see an example of how a user-defined function look like and how it works. Keep in mind that after function declaration, you must have to give a function call inorder to use that function. Also, you can call other functions in a function. But do condition calling else you might get stuck in infinite loop. Here is a simple example of multiple function calls and a function call within a function.

```
<?php

function test(){
    echo "function test";    
}


test(); //function call
test();
test();
test();
?>

<?php
function dummy(){
    echo "<h1>User Details</h1>";
}

function displayUserDetails(){
    dummy();
    echo "Username is SANDY";
    echo "<br/>";
    echo "User age is 27";
    echo "<br/>";
    echo "User email id is sandy@test.com";
    echo "<hr/>";
}

displayUserDetails();
displayUserDetails();
?>
```

## Parameterized Function

Parameterized functions are used where you want to pass some value and perform operations on it. The values are recieved in the variables defined in the `()` of function. Here is a small demonstration of it.

![1](/assets/images/clt/all-about-php-functions/1.png)

I've also written some example code for better understanding.

```
<?php

function sum($a,$b){
    echo $a+$b;
    echo "<br/>";
}

sum(20,50);
sum(100,200);
sum(23,76);

?>
```

Here is another example in which i'm using html within php,

```
<?php

function userData($name,$color){
    echo "<h1 style='color:$color'>$name</h1>";
}

userData('sandy','green');
userData('andy','red');
userData('peter','orange');

?>
```

## Return Statement

The `return` and `echo` might works like same in some cases but they are actually different. `echo` simply displays the output while the `return` return backs the output which can be used for multiple purpose. Here is a basic code of it,

```
?>

<?php
function userName(){
    return "SANDY";
}

echo "<h1>user name is" .userName()."<h1>";

?>
```

## Passing Parameters

In a function, you can also pass parameters. Either you can refer to default parameters or you can send the parameters by yourself. In the below example i'm one parameter from the function call while the other one if define as `default` parameter.

```
<?php
function fruit($name,$color="red"){
    echo "this is $name and it's color is $color";
}

fruit("apple");
?>  
```

I've also written a bit complex example in which i've two parameters both define by default in the function declaration but in the function call i'm also passing the new values for the parameters. Take a look at it,

```
<?php

function displayUser($name='candy',$color="orange"){
    echo "<h1 style='color:$color'>$name<h1>";
}


displayUser('SANDY','blue');

?>
```

## Nested Function

Whenever a function is defined inside another function, it is called as nested function. Keep in mind that for a child function you must have to call parent function first. Else it will not work. You'll get better understanding from the code below,

```
<?php

function test(){
    echo "test function called <br/>";
    
    function apple(){
        echo "apple function called <br/>";
}
}

test();
apple();

?>
```

Also general syntax of it is like this,

![2](/assets/images/clt/all-about-php-functions/2.png)

## Variable Function

Whenever you define a function and store its call in a variable, it is called as Variable Function. Also there is a concept of **callback** function. When you pass a function as a parameter, it is caleld as callback function. Keep in mind that whenever you define a variable function, you simple have to write the function name in the form of string without parenthesis and store in variable. 
The syntax of variable function look like this,

![](/assets/images/clt/all-about-php-functions/3.png)

Here is a complete code for better understanding of both concepts.

```
<?php

function test(){
    echo "test function called";
}


function apple(){

}

$test="test";
$apple="apple";
function main($test){
    echo "main function called";
    $test();
}

main($test);
main($apple);
// echo $test;

?>
```

## Important Built-in Functions:

There are some built-in functions in php which are very useful. `strlen()` function is used to calculate the length of a string stored in a variable.

```
<?php
$str='SANDY';
echo strlen($str);
?>
```

`var_dump()` function is used to check the type of a variable.

```
<?php
$var= "false";
var_dump($var);
?>
```

`date()` function is used to get the date values. You can pass multiple parameters to this function. If you pass the parameter string `"d"`, it will print out current date. 

```
<?php
echo date("d"); 
?>
```

Similarly by passing `"l"` you'll get the current day.

```
<?php
echo date("l"); 
?>
```


By passing `"m"`, you'll get the current month number.

```
<?php
echo date("m"); 
?>
```

Then we've `phpinfo()` function, it'll provide you all the details whether you want `php version`, `inifile location` e.t.c.

```
<?php
echo phpinfo();
?>
```

`is_string()` function will return 1 if the variable passed is string and return nothing is variable is of some other data-type.

```
<?php
$kar="abc";
echo "<br>" .is_string($kar) . "<br>";
?>
```

`is_int()` function will return 1 if the variable passed is integer and return nothing is variable is of some other data-type.

```
<?php
$sar=123;
echo is_int($sar);
?>
```

Then we've `rand()` function. It will generate a random number.

```
<?php
echo rand();
?>
```

`die` and `exit` are used to stop the execution of php. `die` is a bit old while the `exit` is the new one.

```
<?php
echo "before execution";
echo die;
echo "after execution";
?>
```

Also the `exit` look like this,

```
<?php
echo "before executio";
exit;
echo "after execution";
?>
```

Function `substr()` is used to get **sub-string** from a **string**.

```
<?php
$str="code step by step";
echo substr($str,11);
?>
```

The above code will print out the string from the letter 11 and onwards p.s this include the spaces as well. 

Also if you pass parameter `-1` with the string variable. It will print out the last character of the string.

```
<?php
echo substr($str,-1);
?>
```