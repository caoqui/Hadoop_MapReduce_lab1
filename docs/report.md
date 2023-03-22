---
title: "Lab 01: A Gentle Introduction to Hadoop"
author: ["HugeData"]
date: "2023-02-17"
subtitle: "CSC14118 Introduction to Big Data 20KHMT1"
lang: "en"
titlepage: true
titlepage-color: "0B1887"
titlepage-text-color: "FFFFFF"
titlepage-rule-color: "FFFFFF"
titlepage-rule-height: 2
book: true
classoption: oneside
code-block-font-size: \scriptsize
---
# Lab 01: A Gentle Introduction to Hadoop

## Setting up Single-node Hadoop Cluster

## Introduction to MapReduce


## Running a warm-up problem: Word Count

## Bonus

## TEAM HugeData:
MSSV       | FULLNAME             | TASKS           
-----------|----------------------|-----------
20120560   | Cao Đinh Quí         | 1, 2.1.3, write report           
20120089   | Lê Xuân Hoàng        | 1, 2.1.1, 4                
20120130   | Đinh Thị Hoàng Linh  | 1, 2.1.4, 4               
20120397   | Bùi Quang Tùng       | 1, 2.1.2, 3               

### COMPLETION RATE:
SESSION       | RATE                    
-----------|----------------------
1          | 100%       
2          | 100%       
3          | 100%       
4          | ?       

---------------------------------------------------------------
## 1.  Setting up Single-node Hadoop Cluster
### All members finished successfully.
#### The process:
![1.](images/session01/process/1.png)
![2.](images/session01/process/2.png)
![3.](images/session01/process/3.png)
![4.](images/session01/process/4.png)
![5.](images/session01/process/5.png)
![6.](images/session01/process/6.png)
![7.](images/session01/process/7.png)
![8.](images/session01/process/8.png)
![9.](images/session01/process/9.png)
![10.](images/session01/process/10.png)
![11.](images/session01/process/11.png)
![12.](images/session01/process/12.png)
![13.](images/session01/process/13.png)
![14.](images/session01/process/14.png)
![15.](images/session01/process/15.png)
![16.](images/session01/process/16.png)
![17.](images/session01/process/17.png)
![18.](images/session01/process/18.png)
![19.](images/session01/process/19.png)
![20.](images/session01/process/20.png)
![21.](images/session01/process/21.png)
![22.](images/session01/process/22.png)
![23.](images/session01/process/23.png)
![24.](images/session01/process/24.png)
![20120089.](images/session01/process/20120089.png "20120089")
![26.](images/session01/process/26.png)
![27.](images/session01/process/27.png)

#### Result:
![20120560.](images/session01/20120560.png "20120560")
![20120397.](images/session01/20120397.png "20120397")
![20120089.](images/session01/process/20120089.png "20120089")
![20120130.](images/session01/20120130.png "20120130")
_____________________________________________________________
## 2.  Introduction to MapReduce
#### 2.1. How do the input keys-values, the intermediate keys-values, and the output keys-values relate? 
- Input keys-values: The initial data is divided into multiple input keys-values to be fed into MapReduce for processing.
- Intermediate keys-values: Generated from the input keys-values by the Map function. Its key is the result of the Map function's processing, and its value is information to be used in the Reduce function.
- Output keys-values: Generated from intermediate keys-values. The intermediate keys-values are sorted by key and partitioned across reducers. The reducers perform the Reduce function on the groups of intermediate keys-values and generate output keys-values.
- It can be said that input keys-values, intermediate keys-values, and output keys-values are interrelated as the output of one function serves as the input for the next function in the MapReduce process.
#### 2.2 How does MapReduce deal with node failures?
- Redundant storage: MapReduce replicates data across multiple nodes in the cluster to ensure that if one node fails, the data can still be accessed and processed.
- Task tracking: MapReduce tracks completed tasks and tasks that are currently running. If a node fails while running a task, the task can be automatically restarted on another node.
- Job checkpointing: MapReduce periodically stores the intermediate output of a job on disk. If a node fails, the job can be restarted from the last checkpoint instead of starting from scratch, reducing processing time.
- Node monitoring: MapReduce continuously monitors the health of nodes in the cluster through heartbeat. If a node becomes unresponsive or fails, MapReduce can automatically remove it from the cluster and redistribute its tasks to other nodes.
#### 2.3.  What is the meaning and implication of locality? What does it use? 
- The meaning:
    - In MapReduce Hadoop, locality refers to processing data at or near its physical storage location. Locality is an important aspect of the Hadoop MapReduce framework, and it relates to the principle of processing data at or near its physical storage location. By prioritizing locality, Hadoop can reduce network load and improve system performance.
- Use case:
    - Locality aims to reduce the amount of data that needs to be transferred over the network, reduce network load, and improve system performance. Hadoop achieves locality by attempting to schedule tasks on nodes where their input data is stored, which is known as data locality. This is made possible by Hadoop storing data in a distributed manner across a cluster of standard hardware nodes, with each node responsible for processing a portion of the data.
    - When a task is scheduled on a node, the MapReduce framework attempts to read data from the local disk of that node first. Only when the data is not available locally, it is accessed from a remote node. By prioritizing data locality, Hadoop can significantly reduce the amount of data transmitted over the network, which is important for efficiently processing large data sets.
#### 2.4. . Which problem is addressed by introducing a combiner function to the MapReduce model?
- In some cases, the Map tasks return multiple instances of the same <key,value> pair. The Combiner function summarizes these instances into a single <key,value> pair then transfers the result to the Reduce tasks, thus reducing the workload on them and speeding up the whole operation.
_____________________________________________________________
## 3.  Running a warm-up problem: Word Count
#### The process and result: 
![add_check_classpath:](images/session03/add_check_classpath.png)
![add_libary:](images/session03/add_libary.png)
![check_JPS:](images/session03/check_JPS.png)
![check_run:](images/session03/check_run.png)
![copy_to_hd:](images/session03/copy_to_hd.png)
![create_file:](images/session03/create_file.png)
![result:](images/session03/result.png)
![run_1:](images/session03/run_1.png)
![toJar:](images/session03/toJar.png)

_____________________________________________________________
## 4.  Bonus
#### 4.1. Extended Word Count: Unhealthy relationships
- Input:
A D
A B
B C
D B
B E
E C
- Output:
A	pos
B	eq
C	neg
D	eq
E	eq
#### 4.2. Setting up Fully Distributed Mode

_____________________________________________________________
## References
