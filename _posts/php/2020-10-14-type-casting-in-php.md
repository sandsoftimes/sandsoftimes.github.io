---
layout: post
title: Type Casting in PHP
date: 2020-10-14 20:52:55.000000000 +05:00
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
permalink: "/2020/10/14/type-casting-in-php"
---
**Type casting is the conversion from one dataype to another.** PHP also allow type casting. We can convert from various datatypes e.g int to float or int to string e.t.c. Here i've solved various examples in which i'm switching between multiple dataypes, 

```
<?php
$a=true;
$a=(string) $a;

$b="300";
$b=(int) $b;

$c=1;
$c= (float) $c;

$d="abc";
$d=(boolean) $d;

$e=10;
$e=(array) $e;

$f=20;
$f=(object) $f;

// $x=["30"];
// $x=(string) $x;
// var_dump($x);
?>
```

Also, keep in mind array to string conversion is directly not allowed in php. You'll get an error like this,

![1](/assets/images/clt/type-casting-in-php/1.png)