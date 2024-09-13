---
layout: post
title: Include File Function in PHP
date: 2020-10-16 20:52:55.000000000 +05:00
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
permalink: "2020/10/16/include-file-function-in-php"
---
Include function is one of the most common function. It is used to include files which contain code which are repeatedly used e.g footers, headers e.t.c. In php, there are 4 ways to include a file,

* include
* include_once
* required
* required_once

The `include` and `include_once` function both are almost same. The only difference is while using a loop, we used `include_once`. By this, the function include the file only once in a loop while if we used the `include` in a loop, the file will be included againa and again,

Here is an outlook of `include`,

```
<?php
include("./hello-world1.php");
?>
```

Here is another example of `include_once` in a for loop,

```
<?php
for ($i=0;$i<10;$i++){
    include_once("./hello-world.php");
}
?>
```

Just like the above, `require` and `require_once` are also similar to above two. The only difference between `require` and `include` is that the include function gives **warning** if anything goes wrong (we can hide warning in php) but require function gives **fatal error** in case of error (fatal error cannot be hidden). 

Here is an example code for the `require` function,

```
<?php
require("./hello-world1.php");
?>
```

Below is an example of the `require_once` function,

```
<?php
for($i=0;$i<10;$i++){
    require_once("./hello-world.php");
}
?>
```