In this blog I am going to show how to create and access numpy arrays. All these excercises are done in the Jupyter notebook.
So I prefer the same tool for you too to test these commands.

To install jupiter notebook please visit http://jupyter.org/install.html 

## Introduction to numpy.

Numpy is Python library package for scientific computations. Basic data structure of numpy is an array.

## Creating numpy arrays 

### Creating numpy arrays with python list.

To import numpy as np
```
import numpy as np
```
To find out the numpy's version use numpy's version attribute
```
print(np.__version__)
```
Now lets create numpy array. To do this lets create a python list.
To create a list in python use square brackets
```
my_list = [5,48, 68,-8,2]
```
```
my_list
[5, 48, 68, -8, 2]
```
Now call array function of np and give this list as input to create a numpy array
```
my_np_array = np.array(my_list)
```

print numpy array:
```
my_np_array
```

In numpy array we can perform arithmatic operation element by element.

To simply multiply the elements in numpy we can give this syntax.
```
my_np_array * 5
array([ 25, 240, 340, -40,  10])
```
Now if you do the same operation with python list you will not get this. You will get something like this.
```
my_list * 5

[5,
 48,
 68,
 -8,
 2,
 5,
 48,
 68,
 -8,
 2,
 5,
 48,
 68,
 -8,
 2,
 5,
 48,
 68,
 -8,
 2,
 5,
 48,
 68,
 -8,
 2]
```

It will print my_list array 5 times
 
As I said before numpy performs element by element. with this feature we can add two arrays. 
Lest create another list called my_list1
```
my_list1= [8, 2, 7, 9, -5]
```
Now add this two lists 
```
my_list + my_list1
```
this will simply concatinate
```
[5, 48, 68, -8, 2, 8, 2, 7, 9, -5]
```
Now np array for my_list1
```
my_np_array1 = np.array(my_list1)
```
Then add the two numpy arrays
```
my_np_array + my_np_array1
```
```  
array([13, 50, 75,  1, -3])
```
 
 
### Creating numpy arrays with numpy functions

numpy array can be created with out a python list using a numpy arange method.
For numpy arange syntax visit this link
https://docs.scipy.org/doc/numpy/reference/generated/numpy.arange.html 

To create numpy array
```  
np.arange(10)
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```  
include the start value and exclude the stop value
```  
np.arange(5, 50)
array([ 5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21,
       22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38,
       39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49])
```  
```  
np.arange(5, 50, 5)
array([ 5, 10, 15, 20, 25, 30, 35, 40, 45])
```  
```  
np.arange(50, step=5)
array([ 0,  5, 10, 15, 20, 25, 30, 35, 40, 45])
```  

### Instantiating arrays with one or more integers.

linspace function creates an array evenly or linearly spaced. For more visit:
https://docs.scipy.org/doc/numpy/reference/generated/numpy.linspace.html

To create evenly spaced over a specified interval
```  
np.linspace(0,9,10)
array([ 0.,  1.,  2.,  3.,  4.,  5.,  6.,  7.,  8.,  9.])
```  
```  
np.linspace(0,10,5)
array([  0. ,   2.5,   5. ,   7.5,  10. ])
```  

The third argument is number of samples to be generated.
```  
np.linspace(0,10,5, endpoint=False)
array([ 0.,  2.,  4.,  6.,  8.])
```  

### Creating arrays with zeros
```  
np.zeros(5)
array([ 0.,  0.,  0.,  0.,  0.])
```  

By default the data types for linspace and zeros are floating number. To change that we can assign interger type to 'dtype'
argument.
```  
np.zeros(5, dtype='int64')
array([0, 0, 0, 0, 0])
```  

For more info about numpy dtypes
https://docs.scipy.org/doc/numpy/user/basics.types.html


## Referencing elements within array





 