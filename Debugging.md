# [Yesterday, my program worked. Today, it does not. Why?](https://www.st.cs.uni-saarland.de/publications/files/zeller-esec-1999.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Suppose a program can run successfully. However, when changes are applied to the program, it fails. It is usually hard to tell which change is responsible for the failure. 

### Summary 
<!-- [Up to 3 sentences] -->

Zeller proposed a delta debugging prototype, which can efficiently determines the minimal set of failure-inducing changes by looking at the differences.

### Key Insights 
<!-- [Up to 2 insights] -->
- There are three scenarios where linear search is not applicable: 
  - Interference: failures are caused by combination of several changes;
  - Inconsistency: combinations of changes in parallel development may no result in a testable program; 
  - Granularity: a single logical change may affect thousand of lines of code, but only a few may be responsible for the failure.
- In practice, there are several specific properties that allow efficient search algorithms instead of having to test all the 2^n configurations:
  - Monotony: once a change causes a failure, any configuration that includes this change fails as well;
  - Unambiguity: a failure is caused by only one change set and not independently by two disjoint ones;
  - Consistency: every subset of a configuration returns an determinate test result.


### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- The proposed dd+ algorithm can detect arbitrary interferences of changes in linear time; detect individual failure-inducing changes in logarithmic time and handle inconsistencies effectively to support fine-granular changes.
- 

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->

### Summary of Key Results 
<!-- [Up to 3 results] -->
- 
### Open Questions 
<!-- [Where to go from here?] -->


