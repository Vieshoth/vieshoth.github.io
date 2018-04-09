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

## Data Frame

Dataframe in pandas is a t
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


```
>>> dic = {"MOSI":['CA', '0', 'C7', '8', 'C7', '1', '0'], "MISO":['C4', 'C7', '8', 'C7', 'CA', '1', 'ff']}
>>> dic
{'MOSI': ['CA', '0', 'C7', '8', 'C7', '1', '0'], 'MISO': ['C4', 'C7', '8', 'C7', 'CA', '1', 'ff']}
>>> df = pd.DataFrame(dic)
>>> df
  MISO MOSI
0   C4   CA
1   C7    0
2    8   C7
3   C7    8
4   CA   C7
5    1    1
6   ff    0
>>> 


```

