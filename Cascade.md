# [Just-in-Time Compilation for Verilog](https://cs.stanford.edu/people/eschkufz/docs/asplos_19.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Compiling FPGA is extremely time consuming.

### Summary 
<!-- [Up to 3 sentences] -->

To solve the problem that compiling FPGA is too slow, VMware researchers embodied the idea of using JIT to hide compilation time to Cascade, thus proposing the first JIT compiler for Verilog - Cascade. Cascade shortens time to execute, enables debugging information, preserves program performance while having no effect on a finalized design. Cascade significantly improves efficiency of producing working hardware designs.


### Key Insights 
<!-- [Up to 2 insights] -->
- The optimization Cascade uses to minimize communication and runtime overhead, and maximize the amount of computation in fast FPGA fabric is shown below:
  - Inline user logic into a single subprogram. A new engine is allocated for the inlined subprogram and inherits state and control from the old engines. At the same time, Cascade creates a new hardware engine which begins the process of compiling the inlined subprogram in the background, thus hiding compilation time to users.
  - Using standard library components will fail in hiding compilation time. To address this, Cascade maintains a small catalog of pre-compiled engines for the modules in its standard library.
  - Cascade overcomes the limit that sending messages between hardware and software per scheduler iteration can greatly hurt performance by relaxing the requirement of direct communication on every scheduler iteration.
  - Placing Cascade in native mode causes it to compile the user’s program exactly as written, which although sacrifices interativity, but achieves full native performance. 


### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- The design principles of Cascade is shown below:
  - Interactivity: Code with IO side effects should run immediately, and a user should be able to modify a running program.
  - Portability: Code written on one platform should run on another with little or no modification.
  - Expressiveness: Unsynthesizable Verilog should remain active after a program has moved to hardware.
  - Performance Users may trade native performance for expressiveness, but not be forced to sacrifice it for interactivity.

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- Cascade is not applicable to timing critical applicaitons since it is unclear how to preserve higher-order program semantics such as QoS guarantees for compilation state in which user logic has not yet been migrated to hardware.
- Supporting non-monotonic language features will violate the property of Cascade, thus will not be considered.

### Summary of Key Results 
<!-- [Up to 3 results] -->
- VMware researchers proposed Cascade, a first JIT compiler for Verilog to improve FPGA compiling efficiency.
- Cascade allows users to test and deploy code in the same environment, ignore the distinction between synthesizable and unsynthesizable Verilog, and enjoy cross-platform portability without greatly changing their code.
- Cascade also enables debugging without hurting performance without changing designs. Thus, cascade shortens compile-test-debug cycle and greately improve efficiency.

### Open Questions 
<!-- [Where to go from here?] -->
How to develop Cascade with dynamic optimization to further improve the produce performance such that user can specialize a program to the input values it encounters at runtime?
