---
layout: post
title: Php Basic hello-world
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

