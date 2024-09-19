---
layout: post
title: Bubble Sort Algorithm in NASM 16-bit
date: 2020-06-24 20:52:55.000000000 +05:00
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
permalink: "/2020/06/24/bubble-sort-algorithm-in-nasm-16-bit"
---
Bubble sort is a very famous algorithm for sorting numbers. It is commonly used to sort numbers in ascending order. It works totally same here just like the other high level programming languages. Althought coding in 16-bit seems quite difficult but witha a little practice and understanding you can write any code in it. Here is the code,

```
[org 0x0100]

jmp start

data:dw 60,55,45,50

swap:db 0

bubblesort:
    dec cx
    shl cx,1

    mainloop:
        mov si,0
        mov byte[swap],0

        innerloop:
            mov ax,[bx+si]
            cmp ax,[bx+si+2]
            jbe noswap

                mov dx,[bx+si+2]
                mov [bx+si],dx
                mov [bx+si+2],ax
                mov byte[swap],1

                noswap:
                add si,2
                cmp si,cx
                jne innerloop

            cmp byte[swap],1
            je mainloop
            ret ;notice this
```

Here is the initialization and function call,

```
start:
    mov bx,data
    mov cx,4

    ;make a function call
    call bubblesort

    ;data is sorted now!

    mov ax,0x4c00
    int 0x21
```

Before running, write the complete code in a single file.