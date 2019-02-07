---
layout: post
title:  "High level spark architecture"
date:   2019-02-06 19:45:31 +0530
categories: Bigdata
---

Spark architecture consists of 5 components
1. Worker
2. Master
3. Driver
4. Executer
5. Tasks

### Cluster Manager
A cluster is distributed computing environment which stores a huge amount data. This cluster is made of a file system 
and a Distributed operating system. This operating system consists of worker deamon and master deamon. The master daemon 
generally referred as
Cluster manager.
Spark runs on top of the following file systems.
- Mesos
- Yarn
- Standalone
- Local

Mesos and Yarn are external Operating system and it does not come along with spark package. Standalone is an operating 
system which resides with spark.

The most widly used file system for spark is HDFS or Hadoop Distributed File System. HDFS consists of Data nodes and Name nodes.

Every worker service conveys its resources avaialable on its system to the master services.

### Driver
It first creates and DAG and then stages and at last tasks.

When we did a put command what internally happems is from my laptop it contacted the master service wich run in the name node.
And it will request the master service to allocate the resource for the file which it wants to save.
Before that the local system(the laptop in this case) will alloca

The master service will have all the information about the Data nodes becuase the worker serices keeps on updating about data node resources to master service.

The master service in return will the information of three data nodes for each block.

