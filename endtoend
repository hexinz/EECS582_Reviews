# [END-TO-END ARGUMENTS IN SYSTEM DESIGN](http://web.mit.edu/Saltzer/www/publications/endtoend/endtoend.pdf)

###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
People at that time were obsessed with "layered" systems and tend to implement redundant functions all in low-level or subsystems, thinking that performing functions at lower-level will be more efficient. However, several examples and reasons suggest that it might not be the case. Hence, how those functions should be assigned to layers need further rational principles. 


### Summary 
<!-- [Up to 3 sentences] -->

Saltzer, Reed and Clark in their paper proposed a new design principle to guide function placement in a distributed computer system, called the "end-to-end arguments", which is against the traditional low-level function implementation. They pointed out the potential risks of low-level function implementation, especially in the reliable file transfer system and suggested that end-to-end application level function implementation can be more beneficial. More generally, one should assign functions to proper layers according to the application requirements. 

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

