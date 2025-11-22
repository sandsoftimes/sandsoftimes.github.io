---
layout: post
title: How to Display Error in PHP
date: 2020-10-07 20:52:55.000000000 +05:00
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
permalink: "/2020/10/07/how-to-display-error-in-php"
---
Generally by default, php doesnot show error on the browser. It simply says **page isn't working** instead. Inorder to visualize the error in code in browser. You've to do some basic changes. Initially create a new file with name `display-error.php`. In this file write this php function.

```
echo phpinfo();
```
It will display all the information related to php.
![1](/assets/images/clt/display-error-in-php/1.png)

Now, find the `Loaded Configuration File` and its **path**. In this case, it is `/opt/lampp/etc/php.ini`. Open this file on your terminal and find the keyword **display_errors** it will be set **off** initially. Write **on** infront of it. Then simply restart your apache-server. After the restart, write a php code in any of your file with some syntax error. Go to browser and this time, you'll see the actual error being displayed. I've a code below:
```
<?php
// echo phpinfo();
// echo "Hello";
$num=50K
echo $num*50
?>
```
The above code has a syntax error and will display error on the browser like,
![2](/assets/images/clt/display-error-in-php/2.png)
