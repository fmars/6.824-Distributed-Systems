*Write down questions and answers we have before reading paper implementation. Basically try to come up with a idea what if we are about to build such a system*


## **How would I design a GFS**


GFS is basically a distrubuted file system, different with distrubuted database, rather than supporting put(), get(), delete() based on a key-value pair, it should support write(), read(), delete(), based on a file. I'm trying to design a GFS mostly inspired by some design principle I recently read in Zippydb, a distribute key-value db in facebook.


(GFS, as Hadoop, is a distributed file system providing transparency which hides how file is stored across servers. Google big table, as HBase, is a distributed database providing transparency which hides how key value pairs are stored and indexed across servers. Goolge big table should build upon GFS. MapReduce, as Hadoop, is a distrubited computing platform providing transparency which hides how data is proccessed across servers. MapReduce should also build upon GFS).


## Topics should be solved to design a GFS system
- Files are stored distributedly. How master node handles namespace and meta data
- How to handle failure in worker/master
- How to handle concurrent read/write request

### 1. Overall design
We assume any file should be able to be stored within a host (should we?). Worker hosts store each individual files. A master node knows which hosts is a file stored.

### 2. Failure 
**Worker failure**

Maintain 3 replicas for each data. When a write happens, it writes to 3 replicas. One replica performs as primary. Primary will return a successful write only when at least two of three replicas executed sucessfully. Master run heart beat check for each host. Synch data if any worker host dies.

**Master failure**

As in MapReduce, since we only have one master node, it unlikey fails. But we still persistently stores meta data. We also provide check point, so it can be easy to recover from a failure.

### 3. Concurrent request
1. A client should only contact master for once. The following requests should directly go to worker hosts. Otherwise master will be the bottleneck.
2. Each file in a worker server maintains a write/read lock. Client write/read reuqest is handled by server with this lock.

## Potential issues?
1. What if a file is larger than one host can store?
2. How to better leverage that most requests are sequential write/read rather than random access?
3. How to handle most requests are appending new data rather than overwrite existing data?


## What are the missed topics?
