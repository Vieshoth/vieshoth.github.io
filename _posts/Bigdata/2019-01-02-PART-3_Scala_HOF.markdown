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

There are some inbuilt Higher Order funtion on Collection which worth mentioning.
Listed below are the frequently used HOF on collection.
1. Map
2. Filter
3. Foreach
4. Reduce

A collection can be a 
- List
- Map
- Vector
- Set
- Array
- ArrayBuffer
- Rdd
- Tuple

By default Scala collections are immutable. If you try to modify an existing collection it will
simply create a new collection.
But Java collections are mutable.

LIST is internally a single linked list.
1. Not contigious
2. Linear collection
3. Random access takes time. To access any element it has to start from first element.
```
scala> val nums = List(4,5,6,7)
nums: List[Int] = List(4, 5, 6, 7)

```

Array is suitable for random access. 
1. because it is suitable for contigious.
2. It is called as Index collection.
3. Its access time is constant.
```
scala> val nums = Array(4,5,6,7)
nums: Array[Int] = Array(4, 5, 6, 7)

```
Collection can be accessed by calling the index with brackets
```
scala> nums(2)
res4: Int = 6

```
And also built in methods and attributes are available which well be handy for while performing some
operations.
```
scala> nums.tail
res5: Array[Int] = Array(5, 6, 7)

scala> nums.init
res6: Array[Int] = Array(4, 5, 6)

```


#### Map









#### Reduce

Collection[A].reduce(f:(A,A)=>A):A

It act on the each element of the collection and returns a sigle element.
It does not return collection.
Some aggregation can be done with this reduce hof.

How "f" is called.

Ex:
```
scala> val num = List(10, 7, 8, 9)
num: List[Int] = List(10, 7, 8, 9)

scala> def sumTotal(a:Int, b:Int) = a+b
sumTotal: (a: Int, b: Int)Int

scala> num.reduce(sumtotal)
<console>:13: error: not found: value sumtotal
       num.reduce(sumtotal)
                  ^

scala> num.reduce(sumTotal)
res1: Int = 34
```

```
scala> num.reduce((a:Int, b:Int) => a+b)
res2: Int = 34

scala> num.reduce((a, b) => a+b)
res3: Int = 34

scala> num.reduce(_+_)
res4: Int = 34

```

How the internal of reduce works?

val num = List(10, 7, 8, 9)

num.reduce((a, b) => a+b)

first parameter "a" is called as accumulator
and second parameter "b" is called as iterator.

a=4,  b=5
a=9,  b=6
a=15,  b=7
a=22

Finally acc is referred from reduce.

```
scala> def maximum(a:Int, b:Int) = if (a > b) a else b
maximum: (a: Int, b: Int)Int

scala> num.reduce(maximum)
res5: Int = 10

```


function nowhere we are specifying the datatype
```
scala> val colors = List("green", "yellow", "red", "blue")
colors: List[String] = List(green, yellow, red, blue)

scala> colors.reduce(sumTotal)
<console>:14: error: type mismatch;
 found   : (Int, Int) => Int
 required: (Any, Any) => Any
       colors.reduce(sumTotal)
                     ^

scala> colors.reduce((a, b) => a+b)
res7: String = greenyellowredblue

```
"+" is method which act upon the object. Here the object is String. So '+' on String object contatenates
the String.


#### SORTBY

Collection[A].sortby(f:(A)=>B):collection[A]

soring is done on the return value of the function.

```
scala> val colors = List("green", "yellow", "red", "blue")
colors: List[String] = List(green, yellow, red, blue)

scala> def getsize(s:String) = s.size
getsize: (s: String)Int

scala> colors.sortBy(getsize)
res8: List[String] = List(red, blue, green, yellow)

scala> colors.map(getsize)
res9: List[Int] = List(5, 6, 3, 4)

scala> 
```


Already existing  HOF.
Type the value with "." and press TAB to see what HOF is available for the object.

```
scala> colors.
!=              filter               maxBy               sortWith        
##              filterNot            min                 sorted          
+               find                 minBy               span            
++              flatMap              mkString            splitAt         
++:             flatten              ne                  startsWith      
+:              fold                 nonEmpty            stringPrefix    
->              foldLeft             notify              sum             
/:              foldRight            notifyAll           synchronized    
:+              forall               orElse              tail            
::              foreach              padTo               tails           
:::             formatted            par                 take            
:\              genericBuilder       partition           takeRight       
==              getClass             patch               takeWhile       
WithFilter      groupBy              permutations        to              
addString       grouped              prefixLength        toArray         
aggregate       hasDefiniteSize      product             toBuffer        
andThen         hashCode             productArity        toIndexedSeq    
apply           head                 productElement      toIterable      
applyOrElse     headOption           productIterator     toIterator      
asInstanceOf    indexOf              productPrefix       toList          
canEqual        indexOfSlice         reduce              toMap           
collect         indexWhere           reduceLeft          toParArray      
collectFirst    indices              reduceLeftOption    toSeq           
combinations    init                 reduceOption        toSet           
companion       inits                reduceRight         toStream        
compose         intersect            reduceRightOption   toString        
contains        isDefinedAt          repr                toTraversable   
containsSlice   isEmpty              reverse             toVector        
copyToArray     isInstanceOf         reverseIterator     transpose       
copyToBuffer    isTraversableAgain   reverseMap          union           
corresponds     iterator             reverse_:::         unzip           
count           last                 runWith             unzip3          
diff            lastIndexOf          sameElements        updated         
distinct        lastIndexOfSlice     scan                view            
drop            lastIndexWhere       scanLeft            wait            
dropRight       lastOption           scanRight           withFilter      
dropWhile       length               segmentLength       zip             
endsWith        lengthCompare        seq                 zipAll          
ensuring        lift                 size                zipWithIndex    
eq              map                  slice               →               
equals          mapConserve          sliding                             
exists          max                  sortBy                              


```










