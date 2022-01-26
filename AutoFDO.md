# [AutoFDO: Automatic Feedback-Directed Optimization for Warehouse-Scale Applications](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/45290.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Traditional FDO (feedback-directed optimization) is introduced to guide compiler optimization using information about the code’s runtime behavior. However, the traditional FDO is seldom adopted due to difficulties in maintaining a representative benchmark, storing and accessing logs for loadtesting and overhead of instrumentation under load.


### Summary 
<!-- [Up to 3 sentences] -->

Dehao Chen, David Xinliang Li and Tipp Moseley proposed a new FDO, which is easy to enable.


### Key Insights 
<!-- [Up to 2 insights] -->
- Even without explicitly preplanning, programs tend to have a property called "locality", meaning that programs tend to "cluster references to small subsets of their pages for extended intervals". There are two reaasons. Temporal clustering may caused by "looping and executing within modules with private data" while the spacial clustering is due to "related values being grouped into arrays, sequences, modules, and other data structures".
- The later defined "locality", which is as a "distance" (temporal, spacial and cost) from a processor to an object, is appliable in wide parts of computer systems including operating system, database, hardware architects, etc. 

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- Builders of the Atlas computer system first simulated a large main memory with two main performance problems: translating addresses to locations; and replacing loaded pages. The first problem is caused by additional memory access (page table, then actual memory), but can be solved by using an addressing cache, or Translation Look-aside Buffer (TLB) which copies part of the page table into the CPU. For the replacement algorithm, It was not until 1960s that Belady concluded that the Least-recently used (LRU) policy is the consistently best performer.
- For the thrashing problem occurring during multiprogramming, Peter J. Denning first defined "working set" as "the set of pages used during a fixed-length sampling window in the immediate past", reflecting "the process’s intrinsic memory demand". If the working set does not fit the free space of memory, the program will be defered to a queue. It was observed that programs tend to cluster into relatively small locality sets with long phases, which is later defined as "locality".

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
It was not strictly proved why "locality" happens. Will there be any other reasons?

### Summary of Key Results 
<!-- [Up to 3 results] -->
- The locality principle refers to the observation that programs tend to cluster into relatively small subsets of pages with long phases.
- "Locality" is defined as a "distance" from a processor to an object, taking on several meanings: temporal, spacial and cost.
- The locality principle is applicable to broad parts of computer system, including operating system, database, hardware architects, etc. 

### Open Questions 
<!-- [Where to go from here?] -->
Peter J. Denning mentioned a lot future uses of locality principle. I would like to see more detailed explanation of these applications in the future.


