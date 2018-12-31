---
layout: post
title:  "PART-2: SCALA FUNCTIONS"
date:   2018-12-31 19:45:31 +0530
categories: Bigdata
---

Scala is functioning progrmming language. And Functions are called as first class citizens because it 
can be used as basic objects.

#### Function Definition

Below I have shown a simple way to create a function.

For Immutable Function
```
scala> def product(x:Int, y:Int):Int = {
     |   x*y
     | }
product: (x: Int, y: Int)Int
```
Here the product function takes two Int parameter and there is ":Int =" sign before the opening bracker.
This specifies this function returns an Int value.
"=" means this funcion return something.

Even if we dont specify the return type explicitly the compiler will infer it from the return statement from the function.

```
scala> def product(x:Int, y:Int) = {
     |   x*y
     | }
product: (x: Int, y: Int)Int
```

For Mutable Function

```
scala> def product(x:Int, y:Int) {
     | x*y
     | }
product: (x: Int, y: Int)Unit

scala> var z = product(10, 20)
z: Unit = ()

scala> z

scala> 
```

This function return Unit datatype that means it returns nothing. So nothing was assigned to the variable z.
It is mandatory to mention the datatype for the parameters.

#### Function objects. 

As we said in the previous post everything in Scala is an object. This confirms that function is also an object in Scala.
For example :
```
scala> var x = 10
x: Int = 10

scala> var y = x
y: Int = 10

```
Here is an Int object called x is created and assigned a value. 
And an Int object called y created from assigning the Int object x.

In similar fashion we can create function object.

#### Creating a function object from the another function.












