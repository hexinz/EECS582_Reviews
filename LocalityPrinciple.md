# [The Locality Principle](http://denninginstitute.com/pjd/PUBS/CACMcols/cacmJul05.pdf)

###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
The newly-developed virtual memory (at that time) assisting to manage memory is extremely helpful with multithreading and multitasking. However, it also faces the performance issues caused by selection of replacement algorithms, ways compilers grouping codes onto pages and thrashing due to heavy paging for multiprogramming. 


### Summary 
<!-- [Up to 3 sentences] -->

Peter J. Denning in the article introduced the locality principle that explicitly helps with the above problems, thus turning the virtual memory into a robust, self-regulating system with optimized performance without user intervention 

### Key Insights 
<!-- [Up to 2 insights] -->

- From the caretaking aspect, implementing functions in the low-level may not be able to completely fulfill the requirements of the upper-level applications, causing potential failures or errors.
- From the performance aspects, performing the function at low-level may cost more. Low-level may have redundant functions for applications that do not need them; also, the low-level subsystems are unaware of the need of higher level, thus cannot do the job efficiently.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

The authors took the file transfer system as an example to illustrate the importance of end-to-end application level function implementation.

- For the file transfer system, the reliability is ensured by the end-to-end application level function realization, e.g. the checksum and retry/commit plan. Simply making the data communication subsystem reliable is not enough and will cause potential error during file transfer, like the transient error inside a host.
- From the performance aspect, since the reliability is entirely ensured by the application layer, spending efforts on any point below application level can be less efficient when designing a reliable file transfer system. One should first try to realize a communication system providing reliability with the little cost, then evaluate the error to get an acceptable retry frequency. 

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->

The paper mainly focuses on the end-to-end argument against the low-level function implementation. However, it is not always true. More applications and conditions should be taken into account to decide whether layers are organized properly. For instance, flow control is end-to-end while congestion control is not. 

### Summary of Key Results 
<!-- [Up to 3 results] -->

- Low-level function implementation may cause potential risks and can be less efficient under certain cases.
- "End-to-end arguments" serve as a new design principle that could improve performance in distributed system design, e.g. reliability file transfer system, delivery guarantees, secure transmission of data, duplicate message suppression, guaranteeing FIFO message delivery and transaction management.


### Open Questions 
<!-- [Where to go from here?] -->

End-to-end arguments are only parts of the rational principles for organizing layered systems. Questions about the proper organization, specific criteria, different applications, are still open to discuss.

