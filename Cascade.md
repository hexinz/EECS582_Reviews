# [Just-in-Time Compilation for Verilog](https://cs.stanford.edu/people/eschkufz/docs/asplos_19.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
In reality, there are always tasks that are conceptually straightforward, but due to the latge amount of imput data, we have to parallelize the computation, distribute the data, and handle failures, making originally simple computation complicated.

### Summary 
<!-- [Up to 3 sentences] -->

In purpose of solving the above problem, Google Inc. designed a new abstraction that hides the complex details of parallelization, fault-tolerance, data distributionand load balancing in a library, and thus users only need to specify a map function and a reduce function in order to parallelize a simple computation. The interface as well as the implementation turns out be powerful since it enables automatic parallelization and distribution of large-scale computations, and achieves high performance on large clusters of commodity PCs as well.

### Key Insights 
<!-- [Up to 2 insights] -->
- The MapReduce framework depends on two systems for proper operation. The first is a distributed file system for storing input and output data from MapReduce programs. The second is a scheduling system for managing a cluster of machines.
- To deal with the large amount of data, in the sorting task, if the amount of intermediate data is too large to fit in memory, an external sort is used. 


### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

The MapReduce library first splits input files into M pieces (controlled by users) copies the program as the master. then:
- In the Map phase, each worker is assigned a map task and then the map function takes an input pair and produces a set of intermediate key/value pairs, the MapReduce library then groups together all intermediate value with the same intermediate key and passes the data to the Reduce phase. To be more specific, the intermediate values are buffered and periodically written to the disk, partitioned into R regions by the partitioning function and returns the location of these buffered pairs on the local disk back to the master, who later forwards these locations to the reduce workers.
- In the Reduce phase, each worker is notified by the master about the data location and uses remote procedure calls to read the buffered data from the local disks of the map worker. When a reduce worker has read all intermediate data, it sorts the data by the intermediate keys because typically many different keys map to the same reduce task. The reduce worker iterates over the sorted intermediate data and for each unique intermediate key encountered, it passes the key and the corresponding set of intermediate values to the user’s Reduce function. The reduce function then takes in a intermediate key and a set of values for that key and outputs typically one value. 

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- Upon a master failure, current implementation aborts the MapReduce computation if the master fails. However, although the master failure is unlikely, we still want to figure out a better way to handle master failures.

### Summary of Key Results 
<!-- [Up to 3 results] -->
- The MapReduce framework simplifies parallelizing simple computation over a large amount of data by a map task and a reduce task. 
- The MapReduce framework enables fault tolerance. For worker failure, since the results of a map worker are stored on local disk, if that machine goes down, the master is responsible for scheduling that piece of work on a new worker machine (Completed map tasks are re-executed). 
-  Since network bandwidth is a scarce resource, authors apply the locality optimization, which allows to read data from local disks, and write a single copy of the intermediate data to local disk, saving network bandwidth.

### Open Questions 
<!-- [Where to go from here?] -->
I would like to see more optimization and applications of MapReduce in the future.
