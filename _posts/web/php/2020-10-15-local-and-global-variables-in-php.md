---
layout: post
title: Local and Global Variables in PHP
date: 2020-10-15 20:52:55.000000000 +05:00
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
permalink: "/2020/10/15/local-and-global-variables-in-php"
---
Variables can be declared **locally** or **globally**. These two words basically defines the scope of a variable. It means the region upto which you can use any declared variable. In php, you can declare the variables both locally and globally. In order to use a global variable you've to use the keyword `global`.

Here is a very basic example for the scope of variables,

```
<?php
$name="anil";
function getName(){
    $name="peter";
    global $name;
    $name="peter";
    echo "local var: $name";
}


getName();
echo "<br/>";
echo $name;
?>
```
Also, you can use the global variables within the nested functions. Keep in mind only the first one globally defined variable will be used within all nested functions. Take a look at it,

```
<?php
$name="anil";
function test(){
    $name="peter";
    echo $name;

    function innerTest(){
        global $name;
        echo $name;
    }
}

test();
echo "<br>/";
innerTest();
echo "<br>/";
echo $name;;
?>
```