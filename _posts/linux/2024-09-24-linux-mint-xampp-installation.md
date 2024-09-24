---
layout: post
title: XAMPP Installation in Linux Mint
date: 2024-09-24 00:59:55.000000000 +05:00
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
permalink: "/2024/09/24/linux-mint-xampp-installation"
---
Setting the environment for PHP is very simple in Linux. You just have to run xampp and it will install PHP plus all the requisites for it. First of all download the xampp installer from their offical [website](https://www.apachefriends.org/download_success.html). After the download has finished go to the download directory and run the command,

```
ls -l
```

you'll see the xampp installer has no executition permission so do this,

```
sudo chmod +x xampp-linux-x64-8.2.12-0-installer.run
```

it is now executable, run the installer using this,

```
sudo ./xampp-linux-x64-8.2.12-0-installer.run
```

Simply press forward till last step and it will start the installation,

![1](/assets/images/clt/linux-mint-xampp-install/1.png)

After the installation has finished open up the xampp using this command,

```
sudo /opt/lampp/manager-linux-x64.run
```

Press the start all button to start all the services of xampp. Also to open the dashboard or PHPMyAdmin go to this url,

```
http://localhost/dashboard/
```

Keep in mind, if you want to open MySQl on terminal use this command,

```
sudo  /opt/lampp/bin/mysql -u root
```

