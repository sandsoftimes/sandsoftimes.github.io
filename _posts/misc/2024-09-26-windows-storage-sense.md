---
layout: post
title: Windows Storage Sense | Get Rid of C-Drive Autofilling
date: 2024-09-26 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Misc
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2024/09/26/windows-storage-sense"
---
I use the Windows operating system mainly for playing video games. Recently i faced this issue of disk space auto filling up whenever the os got updates resulting in lower remaining space in the os drive. Eventually i've to replace the windows with a new one every 2 or 3 years which was a headache.

I did search multiple threads in order to find the solution. Some people said this occur b/c of leftout update files while some were saying the TEMP files as a major cause of this issue. I removed the temp files from the multiple folders `prefetch`, `Temp`, `%temp%` (we used to do it in windows 7) but i got 2 or 3 gigs free. Then i found this built in windows feature by the name of Storage Sense. You simply have to turn it on the moment you install the windows and Vola! it will manage/remove all the roleback update files. Here is a snippet where you can find it also there is a path from system settings,

![1](/assets/images/clt/windows-storage-sense/1.png)