---
layout: post
title:  "PANDAS DATAFRAME"
date:   2018-03-14 18:00:31 +0530
categories: Python
---


## Introduction 

Installing pandas in Ubuntu
```
pip install pandas
```

Importing panda

```
import pandas as pd
```

## Series

How numpy's ndarray is similar to python's list, in the same way panda's Series is similar Python's dictionary.
```
In [9]: py_dict = {'trichy':300, 'coimbatore':400, 'bangalore': 350}

In [10]: pd_srs = pd.Series(py_dict)

In [11]: pd_srs
Out[11]: 
bangalore     350
coimbatore    400
trichy        300
dtype: int64

In [12]: pd_srs.index
Out[12]: Index(['bangalore', 'coimbatore', 'trichy'], dtype='object')

In [14]: pd_srs.values
Out[14]: array([350, 400, 300])

```
Even a list can be given as an input to Sereis function which will assign numerical index for each element.

```
In [2]: sr = pd.Series([5,3,0,1])

In [3]: sr
Out[3]: 
0    5
1    3
2    0
3    1
dtype: int64

In [4]: 

```
Index are shown on the left and the values are shown on the right. This sr object which we created 
using the Series function as methods which can show the values and seris seperatly.

```

In [4]: sr.values
Out[4]: array([5, 3, 0, 1])

In [5]: sr.index
Out[5]: RangeIndex(start=0, stop=4, step=1)



```


## Data Frame


```
In [2]: import pandas as pd

In [3]: df = pd.DataFrame()

In [4]: df
Out[4]: 
Empty DataFrame
Columns: []
Index: []

```

Series is one dimentional data structure and dataframe is two dimentional data structure.

```
In [6]: py_list = ["chennai" , "bangalore" , "mumbai", "kolkota", "colombo", "dehli"]

In [7]: py_list
Out[7]: ['chennai', 'bangalore', 'mumbai', 'kolkota', 'colombo', 'dehli']

In [8]: sr = pd.Series(py_list)

In [9]: sr
Out[9]: 
0      chennai
1    bangalore
2       mumbai
3      kolkota
4      colombo
5        dehli
dtype: object

In [10]: 

In [10]: 

In [10]: df = pd.DataFrame(py_list)

In [11]: df
Out[11]: 
           0
0    chennai
1  bangalore
2     mumbai
3    kolkota
4    colombo
5      dehli

In [12]: 

```

