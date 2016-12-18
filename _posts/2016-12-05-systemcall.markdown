---
layout: post
title:  "Implementing a system call"
date:   2016-11-23 19:45:31 +0530
categories: linux
author: "Vieshoth"
---
This articel is about adding a system call in linux for arm architecture.
So let's start with the question of
#### What is a system call ?

In simple terms System call is serverce form linux kernel that can be used by user space program to talk with the kernel and hardware.

Now lets go throught a practical guide on how to add a new system call in kernel.
