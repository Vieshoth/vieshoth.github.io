---
layout: post
title:  "High level spark architecture"
date:   2019-02-06 19:45:31 +0530
categories: Bigdata
---

Spark architecture consists of 5 components
1. Node Manager
2. Resource Manager or Cluster Manager
3. Driver
4. Executer
5. Tasks

### Cluster Manager or Worker Service
A cluster is distributed computing environment which stores a huge amount data. This cluster is made of a file system 
and a Distributed operating system. This operating system consists of Node Manager and Resource Manager. The Resource Manager 
generally referred as Cluster manager.
Spark runs on top of the following OS.
- Mesos
- Yarn
- Standalone
- Local

Mesos and Yarn are external Operating system and it does not come along with spark package. Standalone is an operating 
system which resides with spark.

The most widly used file system for spark is HDFS or Hadoop Distributed File System. HDFS consists of Data nodes srvices and Name nodes services.

### Name Node
Name Nodes are daemon processes which runs on the Data Nodes. It frequently updates the data nodes's resources to the Reource Manager. The resources are CPUs and Memory.

### Driver
It first creates and DAG and then stages and at last tasks.

### Steps involved in storing a file in cluster.
Lets see a simple example here for better understanding. Lets say we want to save a file called "sample.txt" with the size of 384MB in the cluster. First the driver will divide the file into blocks based on the file system block size. Here lets assume the file system block size is 128MB. Hence the "sample.txt" file is divided into three blocks.

As a next step the user(laptop) will contacts the master service wich runs in the name node for the resources to save this block.
The master service will have all the information about the Data nodes becuase the worker serices keeps on updating about data node resources to master service.
The master service in return will send the information of three data nodes and request to store that block in those data nodes.
Now the user can directly store the B1 block in the data node
By default the replication is 3.
![GitHub Logo](/images/ssl_certificate/page_request.PNG)

Again it will contact Worker serivice and request for resources for the next block B2. So again Worker service will allocate three nodes and request the user to store it in those three nodes. 

Like wise it stores the block B3. Meanwhile all these information gets stored in the name node's ram.





When we did a put command what internally happems is from my laptop it contacts the master service wich run in the name node.
And it will request the master service to allocate the resource for the file which it wants to save.
Before that the local system(the laptop in this case) will allocate



Lets say we have 

### Heading

For this example lets assume we are running YARN Operating System. And in Yarn OS the Master Services is called as Resource Manager (RM) and the Worker Services is called as Node Manager (NM)

Edge node is the last point a user can reach. A cluster can only be access by a Cluster Admin. Edge node is different from Name node but part of cluster. 
Spark submit command is run from Edge node. As soon as we run the Spark submit command the Driver process will run as part of the spark-submit command itself. 
Spark can be run on Yarn OS as client mode or cluster mode.

spark-submit command in spark client mode

The jar file is copied to Edge node
The Driver first creates the DAG.



