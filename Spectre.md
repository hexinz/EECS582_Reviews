# [Spectre Attacks: Exploiting Speculative Execution](https://spectreattack.com/spectre.pdf)

###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Although lots of system have been designed to use virtualization to divide resources of a modern computer, there are often trade-offs between compatibility and performance, security or functionality and speed, and few have resource isolation or performance guarantees. Most of them only provide best-effort provisioning. 

### Summary 
<!-- [Up to 3 sentences] -->

Barham et al. in their paper proposed Xen, an x86 virtual machine monitor which "allows multiple commodity operating systems to share conventional hardware in a safe and resource managed fashion, but without sacrificing either performance or functionality". They realized it by paravirtualization, which greatly improve performance and simplicity by only making small changes to the guest OS. Finally, Xen can host up to 100 virtual machine instances simultaneously with isolation and little overhead, which outperforms existing solutions.


### Key Insights 
<!-- [Up to 2 insights] -->

- The four design principleps are: 
  - Support for unmodified application binaries is essential, or users will not transition to Xen. Hence we must virtualize all architectural features required by existing standard ABIs.
  - Supporting full multi-application operating systems is important, as this allows complex server configurations to be virtualized within a single guest OS instance.
  - Paravirtualization is necessary to obtain high performance and strong resource isolation on uncooperative machine architectures such as x86.
  - Even on cooperative machine architectures, completely hiding the effects of resource virtualization from guest OSes risks both correctness and performance.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- Xen mainly used paravirtualization to improve performance. Paravirtualization means that the virtual machine abstraction is "similar but not identical to the underlying hardware".
- Compared to Denali's project, which also used paravirtualization, Xen requires no change for the application binary interface (ABI); supports OS level multiplexing to deal with performance isolation; instead of virtualizing 'namespaces' of all machine resources, Xen secures access control by hypervisor: that is, guest OS has direct read access to hardware page tables, but updates are batched and validated by the hypervisor.


### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- The number of different operating systems is limited since Xen has to modify it to be supported.
- Limited operating systems are tested. More tests with different types of operating systems co-working in the virtual space are needed. 

### Summary of Key Results 
<!-- [Up to 3 results] -->

- Xen allows different operating systems co-working on a same server with negligible performance overhead mainly by using paravirtualization.
- Furthermore, Xen multiplexed physical resources at the granularity of an entire operating system to provide performance isolation and utilized hypervisor to secure access control from updates of guest os.
- Finally, Xen can host up to 100 virtual machine instances simultaneously with isolation and little overhead that outperforms other existing solutions.

### Open Questions 
<!-- [Where to go from here?] -->
How data transfer works is not clear and need further illustration. Besides, Xen currently does not support multiprocessor guest OSes. Also, how to address the problem of scaling the number of different operating systems that Xen can support.
