# [Spectre Attacks: Exploiting Speculative Execution](https://spectreattack.com/spectre.pdf)

###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
The speculative execution is vulnerable to "Spectre attacks", which takes advantage of the speculative execution ability to perform operations that would not appear in the correct program. Moreover, the speculative execution ability is found in Intel, AMD, and ARM, which are being used by billions of devices. Hence, Spectre attacks become a practical and serious threat to the actual systems.

### Summary 
<!-- [Up to 3 sentences] -->

Kocher et al. in their paper implemented and analyzed a class of microarchitectural attacks called "Spectre attacks", which trick the processor to speculatively execute instrction sequences that would not appear in the correct program, to present the security problem of the speculative execution that is now widely-used in m modern processors.


### Key Insights 
<!-- [Up to 2 insights] -->

- Spectre attacks work by inserting a sequence of instructions into the process address space and then tricks CPU to speculatively execute those instructions.
- Spectre attacks are serious mainly because:
  - they can be mounted on ARM-based processors, so it also applies to mobile phones.
  - they only assume that speculatively executed instructions can read from memory that the victim process could access normally. Hence, even a processor prevents speculatively executed instructions from accessing kernel memory, Spectre attacks also work. 
  - they can be mounted in just a few lines of JavaScript. Hence, it is portable and can attack just through the browser.


### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

Two variants of Spectre attacks are presented: 
- Attacker mistrains the CPU’s branch predictor into mispredicting the direction of a branch.
- Attacker chooses a gadget from the victim's address space and mistrains the Branch Target Buffer (BTB) to mispredict a branch from an indirect branch (an indirect branch is one that jumps to an address contained in a register, memory location, or on the stack[1]) instruction to the address of the gadget, resulting in speculative execution of the gadget.


### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
How Spectre sttacks can affect other microarchitectural components are not discussed in detail. Besides, how to prevent the Spectre attacks still remains as a question.


### Summary of Key Results 
<!-- [Up to 3 results] -->

This paper implemented and described the Spectre attacks.
- Attackers mistrain the branch predictor to misdirect the speculative execution to execute at a chosen location.
- By finding some usable gadgets as the victim binary, attackers can execute instructions from any memory location of their choosing.


### Open Questions 
<!-- [Where to go from here?] -->
From a braod view, the Spectre attacks come from the improved performance of critical components like processors. The complex optimizations introduce security risks. Hence, there exist trade-offs between security and performance. Do we have to improve performance at the cost of security? Should we also implement optimization for security?

### Reference
[1] https://blog.acolyer.org/2018/01/16/spectre-attacks-exploiting-speculative-execution/
