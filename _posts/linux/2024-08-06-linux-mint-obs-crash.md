---
layout: post
title: OBS (Open Broadcasting Software) Crash Launching Fix in Linux
date: 2024-08-06 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Linux
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2024/08/06/linux-mint-obs-crash"
---

Incase you are using a Linux Operating system and using OBS (Open Broadcasting Software), sometimes this error come which is known by the title of **Not Shutdown Properly Last Time** also known as segmentation fault(on the terminal). In this issue, the obs run and crash on launch. I've tried multiple ways to solve it but none of them was useful until i found this specific solution. 

![5](/assets/images/clt/linux-mint-obs-crash/5.png)

Simply you've to edit a file. Here is the full command to open the file `global.ini`,

```
nano ~/.config/obs-studio/global.ini
```
  
The file will look like this,

![1](/assets/images/clt/linux-mint-obs-crash/1.png)

In here, you've to find a keyword `DockState`, here it is, 

![2](/assets/images/clt/linux-mint-obs-crash/2.png)

It will be a long text in front of `DockState=` as you can see from the above snippet. You simply have to remove everything on the right side of the equal `(=)` sign like this,

![3](/assets/images/clt/linux-mint-obs-crash/3.png)

Now save the file using the shortcut key of `CTRL+O` and exit the prompt using `CTRL+X`. Launch the OBS and it will launch smoothly without an error.

![4](/assets/images/clt/linux-mint-obs-crash/4.png)

For more information, you can also checkout this thread, 

[https://obsproject.com/forum/threads/segmentation-fault.171763/](https://obsproject.com/forum/threads/segmentation-fault.171763/)