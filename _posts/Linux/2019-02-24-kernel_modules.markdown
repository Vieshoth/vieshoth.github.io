---
layout: post
comments: true
categories: Linux
title: KERNEL MODULES
---
### Generating Modules

A driver program in kernel can be compiled in two ways.
- Along with the kernel image
- Or a seperate binary

### Loading Modules
Any kernel module can be added and removed to the kernel using the following two commands:

#### insmod 
This command is used only to insert the module to the kernel. 
Syntax: 
```
insmod <path/module_name_with_extension>
```
It is mandatory to provide the absolute or relative path with the module name.

#### rmmod 
It only removes module from kernel.
```
rmmod <module_name_with_extension>
```

#### modprobe 
Both inserting and removing a module can be done.
Syntax for adding :
```
modprobe <module_name_without_extension>
```
Syntax for removing:
```
modprobe -r <module_name_without_extension>
```
To use modprobe the driver module should be in the following path

/lib/modules/<kernel_version>/

However by simply placing the module in the **/lib/modules/<kernel_version>/** path, does not work. A command called **depmod** is needed to be entered. This depmode command will creates/updates the necessary configuration files under the **/lib/modules/<kernel_version>/** path in order to make the **modprobe** command to identify and find the placed the module.


