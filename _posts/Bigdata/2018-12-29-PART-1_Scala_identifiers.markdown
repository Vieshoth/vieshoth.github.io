---
layout: post
title:  "PART-1: SCALA IDENTIFIERS"
date:   2018-12-29 19:45:31 +0530
categories: Bigdata
---

#### What is Scala
Scala is a 
- jvm based language - Scala project binary can be run directly in the jvm environment
- Functional programming language - Functional programming means avoiding mutability. Scala 	language has provision to avoid mutability.
- Pure OOL (Object Oriented Language) - In Scala everything is object. There is no primitive datatypes in Scala

#### Functional Programing

functional programing literary means avoiding changing the surroundings.
In short this features is called as avoiding mutability.
Mutability means modifying.
However it doesnot mean it is always avoiding mutability. ofcourse it is possible to write a function 
which modifies the sorrounding data. but there should be a clear cut seperation of what is mutabiliy and immutability.
write a seperate function for mutability and imutability.

Basically this a function is used to process some data. This processed data either we can save
the data or return the data.
saving the data means saving it to a file or variale or dB or global datastructure. This is nothing but modifying 
the surrounding.

return - immutability.
non return - mutability.

So Scala is more suitable for distributed application. That is running the same programme in different environment. Since it follows immutability it doesnot change environment. so it is safe.

#### Identifiers

In Scala there are two identifiers. 
They are 
	1. Variable Identifiers
	2. Value Identifiers. 
	
Variable identifiers are defined with the "var" keyword. And it is modifiable.
```
scala> var x = 10
x: Int = 10

scala> x = 20
x: Int = 20

```
On the other the valie identifiers are defined with "val" keyword and 
Value identifiers are not modifiable. 

```
scala> val y = 10
y: Int = 10

scala> y = 20
<console>:12: error: reassignment to val
       y = 20
         ^
```

#### Identifiers data type

It is not required to explicitly give the data type to an identifiers. The Scala will infer the data type
from the given value.

In the below example as you can see it detected the datatype from the assigned value.

```
scala> var x = 10
x: Int = 10

scala> val s = "String"
s: String = String

scala> val d = 10.5
d: Double = 10.5

```

