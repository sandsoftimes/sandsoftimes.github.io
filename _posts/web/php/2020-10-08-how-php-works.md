---
layout: post
title: How PHP works??
date: 2020-10-08 20:52:55.000000000 +05:00
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
permalink: "/2020/10/08/how-php-works"
---
I've already written a complete blog on php working. You can check it out by clicking on this link: [PHP Complete Hello World](/2020/10/06/php-basic-hello-world). Today i'll show you the basic working of a php. As we all know that php is a server-side-scripting language. It means that your browser cannot directly understand the php. 

![1](/assets/images/clt/how-php-works/1.png)


The browser can only understand/work with:
* HTML
* CSS
* Javascript

By the above image you can see that your browser performs a http request to the server. The server will have php-code, it will call the **php-interpretor**. The interpretor solve the request and give output in the form of HTML to server. The server then sends back the HTML response to the web-browser/client.

## What about Database?
The databases are also present on web server. Just like the previous requests. This time the web-server request the database for the data. The database returns the result to interpretor. The interpretor convert it into **HTML format** and give it back to web-server. The web-server send the response to the client-browser and we get the results on the browser tab.

You can visualize this request and response procedure by going into the **inspect** section of the browser. Then there is a small sub-section of **network**. Go there, refresh your tab (in this case we've the comments.php file) and you see the requests to the web-server. Here is the demonstration snippet.

![2](/assets/images/clt/how-php-works/2.png)