# [Yesterday, my program worked. Today, it does not. Why?](https://www.st.cs.uni-saarland.de/publications/files/zeller-esec-1999.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Suppose a program can run successfully. However, when changes are applied to the program, it fails. It is usually hard to tell which change is responsible for the failure. 

### Summary 
<!-- [Up to 3 sentences] -->

Zeller proposed a delta debugging prototype, which can efficiently determines the minimal set of failure-inducing changes by looking at the differences under the assumption of monotony, unambiguity and consistency (sometimes even work for non-monotone or ambiguous configurations). The dd+ algorithm also successfully deal with the three scenarios where linear search is not applciable: interference, inconsistency can granularity. The dd+ algorithm also handle inconsistency to some extent and future work will be focus on automatically avoiding inconsistencies by exploiting domain knowledge.

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

- The automated delta debugging algorithm is at worst linear and can find single failure-inducing change (or a minimal set) even for non-monotone or ambiguous configurations. If ambiguous (multiple failure-inducing changes may occur), for example, automated delta debugging can return one of them and figure out others by re-run the dd algorithm. 
- The delta debugging with unresolved test cases algorithm extends the dd algorithm to handle inconsistency including integration failure, construction failure and execution failure.

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->

The extended dd+ algorithm can only find the minimal set of failure-inducing changes if they can either be applied to the baseline or removed from today’s configuration without causing an inconsistency. If not, the set returned by dd+ may not be minimal.


### Summary of Key Results 
<!-- [Up to 3 results] -->
- The proposed dd+ algorithm can detect arbitrary interferences of changes in linear time; detect individual failure-inducing changes in logarithmic time and handle inconsistencies effectively to support fine-granular changes. 
- The dd+ algorithm can handle inconsistency including integration failure, construction failure and execution failure under the assumption that failure-inducing changes can be either applied to the baseline or removed from today’s configuration without causing an inconsistency.
- Inconsistency can be avoided/reduced by relying on specific knowledge about the nature of the changes.


### Open Questions 
<!-- [Where to go from here?] -->
How to automate the process of avoiding inconsistencies by exploiting domain knowledge?

