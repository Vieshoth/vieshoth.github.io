---
layout: post
title:  "PART-3: SCALA HOF"
date:   2018-12-31 19:45:31 +0530
categories: Bigdata
---

### HOF (HIGHER ORDER FUNCTION)

In the last section we saw how to create a function object.
In this section lets see how to pass a function object as parameter to a function.

In Scala a function which takes another function as a parameter is called Higher Order Function.

Lets define a HOF which takes another function as parameter.

```
scala> def stringOps(s:String, x:String=>String) = {
     | 
     |   if(s != null) x(s)
     |   else s
     | }
stringOps: ()(s: String, x: String => String)String
```

In this stringOps function the second argument is where we pass the function object as parameter.
For that first lets define a function with String as argument as given in stringOps function's second argument.

```
scala> def reverseStr(s:String)={
     | s.reverse
     | }
reverseStr: (s: String)String
```

Now this function can be passed as argument for the stringOps function.

```
scala> stringOps("Spark", reverseStr)
res2: String = krapS
```
You can also pass the function literal instead of the function name as shown below.

```
scala> stringOps("Spark", (s:String)=>s.reverse)
res3: String = krapS
```

Please note that the argument type of the function should be matched with argument type of the HOF.


### Inbuilt Higher Order Function)

There are some inbuilt Higher Order funtion on Collection which worth looking at.
Listed below are the frequently used HOF on collection.
1. Map
2. Filter
3. Foreach
4. Reduce

Lets see one by one.

#### Map




