---
layout: post
comments: true
categories: Linux
title: KERNEL MODULES
---

### Loading Modules
Any kernel module can be added and removed to the kernel using the following two commands:

#### insmod 
This command is used only to insert the module to the kernel. 
Syntax: 
```
insmod <path/module_name_with_extension>
```

#### rmmod 
It only removes module from kernel.
Syntax: rmmod <module_name_with_extension>

#### modprobe 
Both inserting and removing a module can be done.
Syntax for adding :
modprobe <module_name_without_extension>
Syntax for removing:
modprobe -r <module_name_without_extension>

To use modprobe the driver module should be in the following path
     /lib/modules/<kernel_version>/


