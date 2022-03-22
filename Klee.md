# [KLEE: Unassisted and Automatic Generation of High-Coverage Tests for Complex Systems Programs](https://llvm.org/pubs/2008-12-OSDI-KLEE.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Two common concerns for finding bugs on real applications are 
- the exponential number of paths through code and 
- the challenges in handling code that interacts with its surrounding environment, such as the operating system, the network, or the user (colloquially: “the environment problem”).

### Summary 
<!-- [Up to 3 sentences] -->

KLEE is a new symbolic execution tool, which uses search heuristics to automatically generate tests to get high coverage and is also capable of dealing with external environment. After using KLEE to check 452 applications with over 530K lines of code, KLEE found 56 serious bugs, including ten in COREUTILS. KLEE works well across a broad range of real applications and achieved coverage of 90% of the code.


### Key Insights 
<!-- [Up to 2 insights] -->

- KLEE optimized constraint solving, which dominates everything else, in following ways: 1) Expression rewriting; 2) Constraint Set Simplification.; 3) Implied Value Concretization; 4) Constraint Independence; and 5) Counter-example Cache.
- The core of KLEE is an interpreter loop which selects a state to run and then symbolically executes a single instruction in the context of that state. The loop will continue until there is no state remains or reaches the maximum execution time.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- KLEE deal with external environment by doing environment modeling by redirecting library calls that access the external environment to *models* that understand the semantics of the desired action and then generate the required constraints. These models are written in normal C code so tht the user can readily customize, extend, or even replace without having to understand the internals of KLEE.

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- Symbolically execution is slow due to interpreter loop and cannot be used for loops. Despite using search heuristics, it is still hard to handle path exposion for a complex program.

### Summary of Key Results 
<!-- [Up to 3 results] -->
- KLEE is a new symbolic execution tool, which uses search heuristics to automatically generate tests to get high coverage and is also capable of dealing with external environment.
- After using KLEE to check 452 applications with over 530K lines of code, KLEE found 56 serious bugs, including ten in COREUTILS. 
- KLEE works well across a broad range of real applications and achieved coverage of 90% of the code.



### Open Questions 
<!-- [Where to go from here?] -->
- Extend KLEE so that it could also be applied to multithreading programs.


