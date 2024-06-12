---
layout: post
title: php Installation and Initial Working
date: 2020-10-06 20:52:55.000000000 +05:00
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
permalink: "/2020/10/06/php-basic-hello-world"
---
Php is one of the famous server-side scripting language. In common websites, it is used to handle the backend portion. No doubt, many new frameworks are now introduced in the market but still PHP is used in a wide number of websites.
![pngwing](/assets/images/clt/php-hello-world/pngegg.png)

In order to use PHP, you simply have to install the xamp on your system. I'm using linux so i'm attaching a linux installation tutorial of xamp. Here is [XAMP INSTALLATION](https://www.youtube.com/watch?v=R5CUn5wGQGg)

After installation go this directory and create a folder test in it,

```
cd /opt/lampp/htdocs/
mkdir test
cd test
```

In here, you've to create an index.php file in order to visualize the php code on your localhost. So,

```
touch index.php
```

Open up this file and write some basic php code in it like:

```
<?php
$name='SANDSOFTIMES';

$color='green';
echo $name;
echo "SANDSOFTIMES";

?>
<h1><?php echo $name;?></h1>

<h1 style="color:red"><?php echo $name;?></h1>

<h1 style="color:<?php echo $color; ?>"><?php echo $name;?></h1>
```

This code will print the php variables inside the html tags. P.S you've to use `<?php?>` in order to write php code and also `$` is used to declare a variable in php. Also, go to localhost/test/index.php on your browser to view the php code running.

![php first image](/assets/images/clt/php-hello-world/php-first.png)

If you want breakline or you can say go to next line you've to use `"<br />"` in your string or in empty echo.

```
echo "<br />";
```
or
```
echo "What's up <br />";
```
## Variables in PHP
Just like all other programming languages, php also use variables to store any sort of data. The variable is declared by `$` symbol. Also, we don't have to specify any **data-type**. Variables make our life easier. We don't have to do things again and again, below is the example of it, 

```
<?php
echo "matrix <br/>";
echo "maxwell <br/>";
echo "hazel <br/>";
echo "simonn <br/>";

$name="SANDY Soft";

echo $name;
echo "<br>";
echo $name;
echo "<br>";
echo $name;
echo "<br>";

echo 5*3;
echo "<br>";
echo 5*9;
echo "<br>";
echo 5*11;
echo "<br>";

$num=200;
echo "<br>";
echo $num*3;
echo "<br>";
echo $num*9;
echo "<br>";
echo $num*11;
echo "<br>";
echo $num;
echo "<br>";
$name="What is up";
echo $name;
?>
```
Also keep in mind that variables with same names but with different upper and lower case letters are treated separately,

```
<?php
// echo "Hello";
$Name="peter";
echo $Name;
echo "<br>";
$NAME="john";
echo $NAME;
echo "<br>";
$namE="tony";
echo $namE;
echo "<br>";
$a=$b=3;
echo $a;
echo "<br>";
echo $b;
echo "<br>";
?>
```
## Using PHP and HTML Together

You can use both ways,

* Php inside the HTML
* HTML inside the PHP

Below is the attached example of both,

```
<?php
echo "<h1>php with html</h1>";
echo "<h3 style='color:blue'>php with html</h3>";
?>

<!-- HTML in php -->
<?php
$name="SANDY";
$color='blue';
echo "<h1 style='color:orange'>$name</h1>";
?>


<!-- php in HTML -->



<h2 style='color:green'><?php echo "this is h2 tag<br>";?></h2>
<h2 style='color:<?php echo $color;?>'><?php echo "this is h2 tag<br>";?></h2>
<h2>Here <?php echo "this is h2 tag "; echo $name;  ?></h2>
<h2 style='color:<?php echo $color;?>'>Here is another tag <br> <?php echo "<br> and the color is "; echo $color;?></h2>

```

The output of it will look like,

![html-in-png](/assets/images/clt/php-hello-world/html-in-php.png)

## Constants in PHP
In php you can also declare constants just like the variables they are two way to declare constants. The first one is simply by writing the keywords **const** and variable name along with the value assigned to it. The second one is by using the `define()`. Here is the below code for the understanding of both methods,
```  
<?php
// $data="abc";
// const data="peter";
// echo data;
?> 


<!-- First way to declare a variable in php --> 
<?php
$name="bruce";
// $name="tony";
// echo $name;
?> 

<!-- Second way to declare a constant in php -->
<?php
// define("data","peter");
define("data","SandsOfTimes");
echo data;
echo "<br>";
echo $name;
echo "<br>";
define("DATA","EDZIO");
echo DATA;
const __Hello="Mikel";
echo "<br>";
echo __Hello;
?>
```
## Php Datatypes
Just like other programming languages, php also have several datatypes. Some of them are mentioned as follow:
* String
* Integer
* Float
* Boolean
* Null
* Array
* Object
* Recourse

Php has a built in function known as `var_dump`. Use it with the variable name and you can check the variable type from it. Below is a complete code, in which i'm declaring each datatype and then check it using the `var_dump` function of php.

```
<?php

// String

$name="Anil sidhu";
echo var_dump($name);

// Integer

$num=10;
echo "<br>";
echo var_dump($num);

// Float

$numFloat=10.10;
echo "<br>";
echo var_dump($numFloat);

// Bool

$bool=true;
echo "<br>";
echo var_dump($bool);

// Array

$arr=["anil","sam","ali",2];
echo "<br>";
echo var_dump($arr);

// Null

echo "<br>";
$empty=null;
echo var_dump($empty);

// Object

// $user=new className();
echo "<br>";
$connection=ftp_connect("127.0.0.1") or die("local host not found");
echo var_dump($connection);
?>
```
## Comments in php 

In php, you can also do comments for the purpose of better understanding or if you want to comment out the extra portion of the code. There are two types of comments in php as well.
* Single-line comments
* Multi-line comments

There is very little difference b/w the syntax of these two. If you want to do a single-line comment, simply write `//` in the start of the line and if you want to do multi-line comment simple write `/*` at the start and `*/` where you want to end the comment. Both of these types can be demonstrated by the example code written by me below:

```
<!-- Single line comments -->

<?php
$name="Ali";
$name2="Sandsoftime";
define("sandy","what is up");
?>

<!-- Multi line comments -->


<?php
/*
echo $name;
echo "<br>";
echo var_dump(sandy);
*/
?>


<?php
echo "How are you?";
?>
```