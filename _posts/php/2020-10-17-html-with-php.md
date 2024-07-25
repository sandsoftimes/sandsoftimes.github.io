---
layout: post
title: HTML with PHP (GET, POST and $_REQUEST)
date: 2020-10-17 20:52:55.000000000 +05:00
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
permalink: "2020/10/17/html-with-php"
---
PHP and HTML are totally different languages. PHP is a server-side language while the HTML is a client-side language. However the interaction between these two is very important. We make the interface in html while and we write the logic in php. The simple example of it is the sign-up boxes. They are made in html, while the username and password we enter in the fields is taken to server via the use of php. So both of them are of equal importance.

Client sends request to the server. There are 2 main types of requests. 

* get request
* post request

In get request, the address is visible in the address bar, while post request is much more secure and the address is not shown in the address bar.

You can also check the working of php by checking out this blog [How PHP Works??](/2020/10/08/how-php-works)

## GET Request Method

One way of getting data in php is **GET** request method. Simply you've to do 4 steps for this purpose,

* Make HTML file
* Make PHP file
* Make input field in HTML file
* Recieve data in PHP file

First of all let's make an html file, name it `login.html`. Create a basic form in this file with two input fields and 1 button. Also keep in mind, you've to write `form method="get"` for the `get` request and `action="./login.php"` for the redirection. At the end of form make a button as well. Here is the code,

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
</head>
<body>
    <form method="get" action="./login.php">
        <input type="text" name="user_name" placeholder="Enter User Name"/>
        <br />
        <br />
        <input type="text" name="user_password" placeholder="Enter User Password"/>
        <br/>
        <br/>
        <button type="submit">Login</button>
    </form>
    
    
</body>
</html>
```

![1](/assets/images/clt/html-with-php/1.png)

Now make the php file with the name `login.php`. Write a simple `echo` with a text in it,

```
<?php
echo "this is a php login file";
?>
```

Now write a username and password on the webpage,

![2](/assets/images/clt/html-with-php/2.png)

Press the **submit** button and you'll get,

![3](/assets/images/clt/html-with-php/3.png)

**GET** request has three characteristics,

* Request is visible in the address bar
* Less secure request 
* Mostly used to get data from the server

As you know you get the information of the **GET** request in the address bar, here is how it looks.

![4](/assets/images/clt/html-with-php/4.png)

You can also print these values using php. Here it is how you do it,

```
<?php
echo "user name is ".$_GET['user_name'];
echo "<br/>";
echo "user password is ".$_GET['user_password'];
?>
```

![5](/assets/images/clt/html-with-php/5.png)

The url portion after `?` represents the values of **GET** request. What if remove the portion after `?` in the url. What will we get? Lets check this,

![6](/assets/images/clt/html-with-php/6.png)

You will get the warning about the undefined array key of `user name` and `user password`,

![7](/assets/images/clt/html-with-php/7.png)

Now how to remove this warning, you simply have to write a single `if` check in order to avoid this warning. 

```
<?php

if($_GET){
    // echo "this is a php login file";
    echo "user name is ".$_GET['user_name'];
    echo "<br/>";
    echo "user password is ".$_GET['user_password'];
}
?>
```
Now if there is nothing after `?`, you'll not get any warning. Instead you'll get a simple white blank page.
The **GET** request information is also available if you `inspect` the page on your browser and go to the payload of the `Network`,

![8](/assets/images/clt/html-with-php/8.png)

P.S, you can check the type of the request by clicking the `Headers` tab.

![9](/assets/images/clt/html-with-php/9.png)

## POST Request Method

Another way of getting data in php is **POST** request method. You also have to do same 4 steps for this type of request,

* Make HTML file
* Make PHP file
* Make input field in HTML file
* Recieve data in PHP file

We are creating two files now, 
* `signup.html`
* `signup.php`

Simply create an html file with a basic form code in it. Keep in mind you've to write `method="post"` in the form tag. Here is a complete code for the `signup.html` file

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sign Up</title>
</head>
<body>
    <form method="post" action="./signup.php">
        <input type="text" placeholder="enter name" name="user_name"/>
        <br>
        <br>
        <input type="text" placeholder="enter password" name="user_password">
        <br>
        <br>
        <input type="text" placeholder="enter email" name="user_email">
        <br>
        <br>
        <button>Sign Up</button>
    </form>
    
</body>
</html>
```
Now create the other file `signup.php`. In this file simply use the if condition with `$_POST` request and simply use the `print_r()` function to print out all the values from the post request. 

```
<?php 
//echo "signup page";
if($_POST){
    print_r($_POST);
}
?>
```

Now go to the **Sign Up** page and fill out the information, 

![10](/assets/images/clt/html-with-php/10.png)

click the **Sign Up** button and here is the information,

![11](/assets/images/clt/html-with-php/11.png)

You can also print out the information separately, 

```
<?php 
echo "signup page";
if($_POST){
    print_r($_POST);
    echo "<br>";
    echo "User Name is: ".$_POST['user_name']."<br>";
    echo "User Password is: ".$_POST['user_password']."<br>";
    echo "User Email is: ".$_POST['user_email']."<br>";
}
?>
```
and here is how it will look,

![12](/assets/images/clt/html-with-php/12.png)
 
Like the **GET** request, you can also check out your request type from the `inspect` tab.

![13](/assets/images/clt/html-with-php/13.png)

also keep in mind as this is **POST** request so no information is given in the url,

![14](/assets/images/clt/html-with-php/14.png)

but the information is present in the `payload` tab in `network` section of page `inspect`

![15](/assets/images/clt/html-with-php/15.png)


## $_REQUEST Method

There is another method of fetching data in php. It is called `$_REQUEST` method. It has an advantage over **GET** and **POST** requests. It can handle both types of requests. For using this method, we will also create two files, one will be html file and the other will be the php file.

Initially write a basic form code in `register.html` file,

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Request</title>
</head>
<body>
    <form action="./register.php" method="get">
        <input type="text" name="user_name" placeholder="enter name">
        <br>
        <br>
        <input type="password" name="user_password" placeholder="enter password">
        <br>
        <br>
        <input type="text" name="user_email" placeholder="enter email">
        <br>
        <br>
        <input type="text" name="user_address" placeholder="enter address">
        <button>Register</button>
    </form>
    
</body>
</html>
```

The form will look like this, 

![16](/assets/images/clt/html-with-php/16.png)

Then go to the `register.php` file and this time write `$_REQUEST` for this new method. It will handle both the **GET** and **POST** requests. Also if you want to forcefully add a new entry to the php file, you can do it aswell like i'm doing it as 

```
$_REQUEST['dummy']='test';
```

Also i'm using foreach loop so that if the number of input field increases, then the foreach loop work on all by itself. Here is the complete code of `register.php` file,

```
<?php
// print_r($_REQUEST);
$_REQUEST['dummy']='test';
if($_REQUEST){
foreach($_REQUEST as $key =>$data){
    echo $key ." is ". $data;
    echo "<br>";
}
}
?>
```
Here you can see i'm sending **GET** request, 

![17](/assets/images/clt/html-with-php/17.png)

And now i'm sending a post request to it,

![18](/assets/images/clt/html-with-php/18.png)