---
layout: post
title:  "ANACONDA BASICS"
date:   2017-11-19 19:45:31 +0530
categories: Python
---

## INTRODUCTION

Anaconda is a Python data science platform. It is also a package manager.
Hence one can create customized python environment with anaconda.

To download Anaconda for any OS visit this link
https://www.anaconda.com/download/#linux

The procedure to install anaconda in ubuntu is given in this link
https://docs.anaconda.com/anaconda/install/linux

## CONDA

'conda' is the command-line utility for anaconda.
Use *conda --help* or *man conda* command gives you more insight about the "conda" command.
Here we will see some important commands to invoke our customized Python environment.

*conda list* is the command which will list out all the available package in anaconda.
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

Use *conda search * to search any kind of package it supports. For example to know more about "numpy" package, 
the command below can be used.

```
conda search "numpy"
```

## CREATING AN ENVIRONMENT

One can create or invoke a Python environment using the command below. 
You can select the Python version as per your requirement.
```
aaa@linux$ conda create -n my_env1 python=3
Fetching package metadata ...........
Solving package specifications: .

Package plan for installation in environment /home/vieshoth/anaconda3/envs/my_env1:

The following NEW packages will be INSTALLED:

    ca-certificates: 2017.08.26-h1d4fec5_0     
    certifi:         2017.7.27.1-py36h8b7b77e_0
    libedit:         3.1-heed3624_0            
    libffi:          3.2.1-hd88cf55_4          
    libgcc-ng:       7.2.0-h7cc24e2_2          
    libstdcxx-ng:    7.2.0-h7a57d05_2          
    ncurses:         6.0-h9df7e31_2            
    openssl:         1.0.2m-h26d622b_1         
    pip:             9.0.1-py36h6c6f9ce_4      
    python:          3.6.3-h1284df2_4          
    readline:        7.0-ha6073c6_4            
    setuptools:      36.5.0-py36he42e2e1_0     
    sqlite:          3.20.1-hb898158_2         
    tk:              8.6.7-hc745277_3          
    wheel:           0.29.0-py36he7f4e38_1     
    xz:              5.2.3-h55aa19d_2          
    zlib:            1.2.11-ha838bed_2         

Proceed ([y]/n)? y

#
# To activate this environment, use:
# > source activate my_env1
#
# To deactivate an active environment, use:
# > source deactivate
#

aaa@linux$ 
```
The above listed packages are installed by default while creating a new environment.
To include any new package which is not in the list, use this command.

```
conda create -n myenv python=3 scipy

```
To install a package in an already created env, use this command.

```
conda install -n myenv scipy
```
Creating the environment alone will not make you to enter in to Python environment. For that you need to activate it. 
Use this command *source activate my_env1* to avtivate. And the output of this will be like shown below.
```
aaa@linux$ source activate my_env1
(my_env1) aaa@linux$ 
```
So this will lead to the Python environment you created.

## KNOW YOUR ENVIRONMENT

To get the environment list in the PC.
```
conda info --envs
```
To know about a particular environment.
```
conda list -n myenv
```

## REMOVING AND DELETING
To come out of the environment
```
source deactivate
```
To delete an environment
```
conda remove --name myenv --all
```

















