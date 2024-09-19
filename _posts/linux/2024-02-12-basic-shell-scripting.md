---
layout: post
title: Shell Scripting
date: 2024-02-12 20:52:55.000000000 +05:00
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
permalink: "2024/02/12/basic-shell-scripting"
---
Shell scripting is a powerful tool which is widely used to perform different task using the command line. Mainly it is used for the purpose of automation.Shell scripting is a highly flexible tool and it very powerful due to high support of operating system. Mainly it is used by system administrators. They used it for the purpose of system monitoring, account creating and variety of tasks. Developers and DevOps professionals also widely use shell scripting on almost daily basis.

Shell scripting consist of various terminologies. Mainly of which are:

1. Terminal: Establish connection with the server
2. Shell: Interpret shell scripting commands
3. Script: Short program that performs a specific task
4. Shell Script: Script which runs through command-line shell

## Types of Shells:

Different types of shells are used for different tasks. It totally depends upon the nature of application. Shell decides how can we execute programs and which system resources should be access. Some common tpes of shells are below:

1. Bourne shell
2. C shell
3. Bash shell
4. Korn shell
5. Z shell

We are going to look into the bash shell mainly as i'm using linux and bash shell is widely used in it. Let's write some basic hello world shell script by using a hello.sh file.

```
#!/bin/bash
echo "Hello Shell"
```

After it, we have to check the permissions of the hello.sh file so that we can execute this script. For this purpose, we will add execution permission for this `.sh file`

```
chmod +x hello.sh
```

Now, confirm the permissions of the file by,

```
ls -l
```

As the file is now executable, run the file by using,

```
./hello.sh
```

and here you go. A message of "`Hello Shell"` is in front of you.
