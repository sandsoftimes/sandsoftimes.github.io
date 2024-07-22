---
layout: post
title: All About PHP Arrays
date: 2020-10-13 20:52:55.000000000 +05:00
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
permalink: "/2020/10/13/all-about-php-arrays"
---
What if you've 1000 of users and you want to store them in a programming language. One method is to create separate variable for each user but its not possible. The solution is **ARRAYS**. Arrays can store multiple values. You simply have to provide two things.

* Array Name
* Array Size

And you can store any types of values in an array. In some languages like c,c++ you can only store the same datatype in an array. While in php, you can store multiple datatypes in a single array. Lets first begin with the declaration of arrays in php. There are two methods, the first one is with the use of function `array()` while the second ones square brackets `[]` directly. Here is an example code for first method.
```
<?php
$users=array("anil","sam","peter","bruce");
?>
```
While the second method is,

```
<?php
$users=["anil","sam","peter","bruce","john"];
?>
```
In order to print the array, you've to use **indexes**. One way is to pass the index one by one on your own,

```
<?php
$users=["anil","sam","peter","bruce","john"];
echo $users[0]; //array start from zero
echo "<br>";
echo $users[1];
echo "<br>";
echo $users[2];
echo "<br>";
echo $users[3];
echo "<br>";
?>
```

While the more commonly used method is by **loops**.

```
<?php
$users=["anil","sam","peter","bruce","john"];
for ($user=0;$user<count($users);$user++){
    echo "<h1 style='color=blue'>".$users[user]"<h1/>";
    echo "<br>/";
}
?>
```

Here we are using the built-in function of `count()` which will count the total number of entites present in an array.

## For Each Loop with Array

You can use any type of loop with array. Lets talk about the **for-each** loop. Unlike the **for-loop**, in which you've to provide the length of array, here simply provide the array and the loop will run until the last member of the array. Here is an example,

```
<?php
$users=["anil","peter","bruce","tony"];
foreach($users as $x){
    echo $x;
    echo "<br/>";
}
?>
```

The loop will run and print all the entities in `users` array. We can also use the `break` and `continue` statements with this loop. You can see here,

```
<?php
$users=["anil","peter","bruce","tony","sam","bhaskar"];
foreach($users as $x){
    if ($x=="peter"){
        continue;
    }
    echo "<h3>".$x."<h3>";
    if ($x=="bruce"){
        break;
    }
}
?>
```
You can also define the scope of **for-each** loop by using the keyword `endforeach`. Here is an example,

```
<?php
foreach($users as $x):
    echo $x;
    echo "<br>"
endforeach
?>
```
## Associative Array

One of the type of php array is **associative array**. It works on the basis of key-value pair. It don't have the index like normal arrays. Here is a basic dummy look of this array,

![](/assets/images/clt/all-about-php-arrays/3.png)

Also for some testing purpose, i've written a very basic code. Here it is,

```
<?php
$userDetails=[
    "name"=>"sandy",
    "age"=>39,
    "city"=>"lahore",
    "email"=>"ghz@latest.com",
    "state"=>"DAMP"
];

echo $userDetails["name"];
echo $userDetails["age"];
echo $userDetails["city"];
echo $userDetails["state"];
echo $userDetails["email"];
?>
```

You can also use `foreach` loop with associative arrays,

```
<?php
foreach($userDetails as $key => $data){
    echo $key. "is ".$data;
    echo "<br>";
}
?>
```

## Multi Dimensional Array

Nested arrays are also called as **multi dimensional arrays** in php. You can write an array within an array. In order to go through the multi dimensional arrays, you've to use for nested loops as well. Here is an example for the better understanding of how a multi dimensional array look like and how to transverse through it,

```
<?php
$users=[
    [1,"anil","noida","anil@test.com"],
    [2,"sam","delhi","sam@test.com"],
    [3,"peter","handy","peter@test.com"]
];

for($i=0,$i<count(users);$i++){
    for($j=0;j<count($users[i]);$j++){
        echo $users[$i][$j];
    }
}

?>
```
## Display Data From an Array in Table Form

You can create and display data in a very simple way in `HTML`. For this purpose, you've to use specific html tags. Here is an example code,

```
<html>
    <head>
        <table>Table</table>
    </head>
    <body>
        <table>
            <tr>
                <td>S.N.</td>
                <td>Name</td>
                <td>Email</td>
            </tr>

            <tr>
                <td>1</td>
                <td>Ali</td>
                <td>Ali@latest</td>
            </tr>

            <tr>
                <td>2</td>
                <td>Ahmad</td>
                <td>Ahmad@latest</td>
            </tr>
        </table>
    </body>
</html>
```

Let's assume you've a multi-dimensional array in php and you want to display its data in tabular form. You can also do that, you simply have to use **html-tags** and **nested-loop**. Here is an example code,

```
<?php
        $users=[
            [1,"Ali","Ali@latest.com"],
            [2,"Ahmad","Faisal@latest.com"],
            [3,"Faisal","Faisal@latest.com"],
            [4,"Rehman","Rehman@latest.com"],
        ];
        echo "<table border=1>";
        for($i=0;$i<count($users);$i++){
            echo "<tr>";
            for($j=0;$j<count($users[$i]);$j++){
                echo "<td>";
                echo $users[$i][$j];
                echo "</td>";
            }
            echo "</tr>";
        }
        echo "</table>";
?>
```
The output will look like this,

![5](/assets/images/clt/all-about-php-arrays/5.png)

## Multidimensional Associative Array

In multidimensional associative arrays you've both the behaviours of nesting and keys. There will be arrays within array and keys attached to the entries in such type. Here is an example code of this type of Arrays,

```
<?php
$users=[
    ["name"=>"anil","age"=>"29","city"=>"noida"],
    ["name"=>"sam","age"=>"30","city"=>"guargaon"],
    ["name"=>"bhasker","age"=>"32","city"=>"delhi"],
    ["name"=>"peter","age"=>"34","city"=>"noida"],
];

foreach($users as $user){
    foreach($user as $key=>$item){
        echo "$key is $item";
        echo "<br/>";
    }
    echo "<br/>"; echo "<br/>";
}
?>  
```
You can see we've **nesting of arrays** and **keys** attached in the above example. If you run this code on php-server, it will look like this,

![6](/assets/images/clt/all-about-php-arrays/6.png)

## Remove and Add Element in Array

You can also **add** and **remove** elements from an array in php. There are multiple ways for it but most essayist are the use of **php-functions**. In order to do some extra entries in an array, use the `push` function and it will do entries at the end of the array. Similarly, if you want to remove something simply use the `pop` function and the last element of the array  will be removed. What if we want to remove multiple values from a single call? In this case, we will use `splice` function. The splice function takes a numeric value in parameter and removes the last total of that values from the array. Here is a practical code of this,

```
<?php
$users=["anil","sam","bhasker","praveen"];

array_push($users,"peter","bruce","tony");

array_splice($users,-4);
print_r($users);
?>
```

Before splice function call, 

![7](/assets/images/clt/all-about-php-arrays/7.png)

After splice function call,

![8](/assets/images/clt/all-about-php-arrays/8.png)

