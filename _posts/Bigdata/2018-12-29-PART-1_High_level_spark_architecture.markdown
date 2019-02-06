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


The most widly used file system for spark is HDFS or Hadoop File System.

