# [Agamotto: How Persistent is your Persistent Memory Application?](https://www.usenix.org/system/files/osdi20-neal.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
It is challenging to write Persistent Memory applications that are both correct and efficient. It is likely that PM applications contain some correctness and performance bugs. However, current bug-detecting tools for PM applications have low bug coverage and rely on developer annotations and need extensive test cases that take long time to finish.

### Summary 
<!-- [Up to 3 sentences] -->

Neal at el. proposed a new generic and extensible system called AGAMOTTO, which uses a state space exploration algorithm and symbolically executes PM system to discover misuse of persistent memory in PM applications. Besides, a new symbolic memory model is introduced to check whether or not PM state has been made persistent. AGAMOTTO has successfully identified 84 new bugs in 5 benchmark PM applications.

### Key Insights 
<!-- [Up to 2 insights] -->
-  PM application bugs can be catagorized into correctness bugs (lead to data corruption), performance problems and application-specific bugs. The missing fences/flush can lead to both correctness and performance problems and accounts for 50/63 bugs; extra fences/flush only leads to performance downgrade and accounts for 6/63 bugs; the rest 7/63 bugs are application-specific bugs.
- AGAMOTTO tracks persistent memory allocations from the system level and tracks Persistent Memory State. Then, AGAMOTTO prioritizes exploring program states that are most likely to modify persistent memory using a PM-aware search algorithm, which is efficient.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->
- AGAMOTTA aims to achieve four high-level design principles:
  - Automation. AGAMOTTO aims to automate in order to reduce user annotation as much as possible. AGAMOTTO could generate basic test cases to explore execution paths in an application.
  - Generality. AGAMOTTO can test any PM application.
  - High Accuracy. AGAMOTTO aims to report no false positives.
  - Extensibility. AGAMOTTO can be easily extended to find application-specific bugs.
 - AGAMOTTO not only provides two built-in Universal Peristency Bug Oracles, which check for bugs automatically based on the patterns that have already been identified, but also allows developers to specify custom, application-specific persistency bug oracles.
  
### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- More bugs could be found and the time spending finding bugs can be optimized.

### Summary of Key Results 
<!-- [Up to 3 results] -->
- AGAMOTTO uses novel state exploration algorithm to symbolically execute PM system to detect bugs in real-life PM applications without user annotation and extensive test suite.
- A new symbolic memory model is introduced to check whether or not PM state has been made persistent.
- AGAMOTTO has successfully identified 84 new bugs in 5 benchmark PM applications and libraries.

### Open Questions 
<!-- [Where to go from here?] -->
- What is the reason why some bugs cannot be detected by AGAMOTTO? How to solve it?

