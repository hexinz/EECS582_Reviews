# [The Locality Principle](http://denninginstitute.com/pjd/PUBS/CACMcols/cacmJul05.pdf)
# [The Locality Principle](http://denninginstitute.com/pjd/PUBS/CACMcols/cacmJul05.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
The newly-developed virtual memory (at that time) helped manage memory and provid superier programming environment. However, it also faces the performance issues caused by selection of replacement algorithms, ways compilers grouping codes onto pages and thrashing due to heavy paging for multiprogramming. 

### Summary 
<!-- [Up to 3 sentences] -->

In purpose of solving the thrashing problem, Peter J. Denning in the article defined "working set" to relect program's intrinsic memory demand and proposed a feedback control mechanism that if the working set does not fit the free space of memory, the program request activation will be deferred to a holding queue. He also introduced the term "locality" to describe the observation that programs tend to cluster into small subsets of pages with long phases. Later, he further defined locality as a "distance" from a processor to an object, taking on several meanings: temporal, spacial and cost, which is widely adopted in operating system, database, hardware architects, etc. 

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
- It was not strictly proved why "locality" happens. Will there be any other reasons?

### Summary of Key Results 
<!-- [Up to 3 results] -->
- The locality principle refers to the observation that programs tend to cluster into relatively small subsets of pages with long phases.
- "Locality" is defined as a "distance" from a processor to an object, taking on several meanings: temporal, spacial and cost.
- The locality principle is applicable to broad parts of computer system, including operating system, database, hardware architects, etc. 

### Open Questions 
<!-- [Where to go from here?] -->
- Peter J. Denning mentioned a lot future uses of locality principle. I would like to see more detailed explanation of these applications in the future.


