---
layout: post
title:  "PART-1: SCALA BASICS"
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

#### Data type

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
By default int will be inferred for numerical value
By default double will be inferred for decimal value

It is good to know about two more datatypes which are unique to Scala language.
They are "Any" and "Unit".

"Any" is a super datatype and it is the parent datatype of all the other datatype.
And "Unit" is a datatype which is nothing but a void. Which means it does not return anything.

TUPLES - In Scala, a tuple is a group of multiple or different datatypes. Tuples are immutable.

```
scala> val t = (10, "Scala", true)
t: (Int, String, Boolean) = (10,Scala,true)
```

It is useful when returning multiple element of different datatype from the function
```
scala> def person() = {
     | val name = "Peter"
     | val age = 25
     | val height = 5.7
     | (name , age, height)
     | }
person: ()(String, Int, Double)

scala> val x = person()
x: (String, Int, Double) = (Peter,25,5.7)

scala> x._1
res0: String = Peter

```

Tuple is distrubited app used as key, value pair. This is called as two value Tuple.


#### IF ELSE CONDITION

In Scala if condition can used in usual way and also can return value.

Usual way - Mutable
```
scala> val x = 10
x: Int = 10

scala> val y = 20
y: Int = 20

scala> var max = x
max: Int = 10

scala> if (x>y){
     | max = x
     | } else {
     | max = y
     | }

scala> max
res3: Int = 20

```

Returning from the if condition - immutable

```
scala> val x = 10
x: Int = 10

scala> val y = 20
y: Int = 20

scala> var max = x
max: Int = 10

scala> max = if (x>y){
     | x
     | } else {
     | y
     | }
max: Int = 20

```

In both the ways the if else condition can be used.

Here comes the tricky part. Could anyone guess the return type of the below expression.

val msg = if (x==10) "x is 10"

Most people would have guessed as "String". But the answer is "Any"

```
scala> val msg = if (x==10) "x is 10"
msg: Any = x is 10
```
Because in compiler if and else go together. 
Even if the else is not written the compiler will take the return type of else into consideration.
Here since the else part is not available the return of else is UNIT.

So there are two different return type from if and else hence the compiler will go with ANY which the parent type of
string and unit.

For all the block of xpression (whatever inside flower bracket), if the last expression is an assignment 
then the return value is UNIT.
if it is a non assignment then it is return expression.

```
scala> val a = { max = 20 }
a: Unit = ()

```

#### FOR LOOP

syntax for mutability
for (i <- interator){

}

syntax for immutability
val x = for (i <- interator) yield {

non assignment
}


val z = x+ y
here + is not a operator it is a method.
val z = x.+(y)

mutability of for loop

for (i <- 1 to 5){}

for (i <- 1 to 10 by 2 ){}

for (i <- 1.0 to 10.0 by .5 ){}

immutability of for loop

val v = for (i<-1 to 5) yield {
	i+2
}

return value from the for loop is a collection

first character of for loop:

a = Array(Scala, Java, Python)
val c = for (i <- a ){
			a(0)
			}


String

val x = "Helloworld"

x.last
x(x.size -1)



