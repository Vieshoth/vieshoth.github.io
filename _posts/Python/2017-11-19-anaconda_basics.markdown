---
layout: post
title:  "ANACONDA BASICS"
date:   2017-11-19 19:45:31 +0530
categories: Python
---

## INTRODUCTION

Anaconda is a Python data science platform. It is also a package manager.
Hence one can create customised python environment with anaconda.

To download Anaconda for any OS visit this link
https://www.anaconda.com/download/#linux

The procedure to install anaconda in ubuntu is given in this link
https://docs.anaconda.com/anaconda/install/linux

## CONDA

'conda' is the command-line utility for anaconda.

'conda list' This command will list out all the available package in anaconda.
```
aaa@linux$ conda list
# packages in environment at /home/aaa/anaconda3:
#
_ipyw_jlab_nb_ext_conf    0.1.0            py36he11e457_0  
alabaster                 0.7.10           py36h306e16b_0  
anaconda                  5.0.1            py36hd30a520_1  
anaconda-client           1.6.5            py36h19c0dcd_0  
anaconda-navigator        1.6.9            py36h11ddaaa_0  
anaconda-project          0.8.0            py36h29abdf5_0  
.
.
.
.
.
xlrd                      1.1.0            py36h1db9f0c_1  
xlsxwriter                1.0.2            py36h3de1aca_0  
xlwt                      1.3.0            py36h7b00a1f_0  
xz                        5.2.3                h2bcbf08_1  
yaml                      0.1.7                h96e3832_1  
zeromq                    4.2.2                hb0b69da_1  
zict                      0.1.3            py36h3a3bf81_0  
zlib                      1.2.11               hfbfcf68_1  
aaa@linux$ 

```




conda search "^python$"

conda --help

## CREATING AN ENVIRONMENT

conda create -n my_env python=3

source activate my_env


## DELETING AN ENVIRONMENT

source deactivate

conda info --envs

conda list -n myenv


conda remove --name myenv --all