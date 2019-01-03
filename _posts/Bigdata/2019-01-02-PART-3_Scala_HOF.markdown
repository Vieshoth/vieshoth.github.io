---
layout: post
title:  "PART-3: SCALA HOF"
date:   2018-12-31 19:45:31 +0530
categories: Bigdata
---

## HOF (HIGHER ORDER FUNCTION)

In the last section we saw how to create a function object.
In this section lets see how to pass a function object as parameter to a function.

In Scala a function which takes another function as a parameter is called Higher Order Function.
















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
NOTE: It is mandatory to mention the datatype for the parameters.

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

One can perform the following operations with functions in Scala
- Assign a value to a function obj
- Assign a function object to another function object 
- Pass a function object as a parameter to a function 
- Return a function object from a function 








