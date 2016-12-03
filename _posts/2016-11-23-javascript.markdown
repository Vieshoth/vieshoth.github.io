---
layout: post
title:  "Javascript basic syntax"
date:   2016-11-23 19:45:31 +0530
categories: linux
author: "Vieshoth"
---

---
layout: post
title: Javascript basic syntax
---

This blog is not for biginners. This site is for those who have experience or knowledge in other language and want quicky learn javascript.

### Creating variable

```javascript
var x = 5;
```

Here is x is the variable name and 5 is its value.

### Creating function

In javascript functions are also called as methods. They can be created by following two sintax.

```javascript
function <function_name>(<function_arguments>){
<function_body>
}
```
```javascript
var <function_name> = function (<function_arguments>){
<function_body>
}
```

### Creating Classes

In javascript classes are called as constructors. The are defined as same as functions. But they can be differentiated by  the way of calling.

For example iam defining a function called fruit

```javascript
function fruit (name){
console.log(name)
}
```

This function can be used as a method or constructor. for a method just call the function name.

fruit("apple");

To use this as a constructor you should use the object creation syntax.

var apple_fruit = new fruit("apple");

But keep in mind functions use 'this' operator can be only used as constructor.

For example
```javascript
function fruit (name){
this.name = name;
}
```

Using the above function as normal method produces undefined results

### Creating Objects

Creating objects is somewhat similar to creating variables.

syntax for defining objects.

```javascript
var <object_name> = {

<property> : <value>

}
```
OR
```javascript
var <object_name> = new <constructor_name>(<arguments>);
```
For more clarification

variable
```javascript
var <variable_name> = <variable_value>

var <array_name> = [array content];

var <object_name> ={Object content};
```
