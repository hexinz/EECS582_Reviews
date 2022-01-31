# [IX: A Protected Dataplane Operating System for High Throughput and Low Latency](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-belay.pdf)

###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
With datacenter applications become more and more complicated, there come the new requirements for the network stacks: high packet rates, microsecond-level responses to remote requests, strong protection models, and elasticity in resource usage. However, high throughput, low latency, strong protection, and resource efficiency are traditionally thought to be a 4-way tradeoff. IX realized separation of management and scheduling functions of the kernal from network processing, which are control plane and dataplane respectively, as well as the untrusted user code by hardware virtualization.

### Summary 
<!-- [Up to 3 sentences] -->

Belay et al. in their paper proposed a dataplane operating system called IX that realized separation of management and scheduling functions of the kernal from network processing, which are control plane and dataplane respectively, as well as the untrusted user code by hardware virtualization. IX also creatively employs run-to-completion, adaptive, bounded batching and a zero-copy API to improve on both latency and throughput. According to the experiments, IX outperforms Linux and state-of-the-art, user-space network greatly in the throughput and the tail latency while having strong protection offered by existing kernels. 


### Key Insights 
<!-- [Up to 2 insights] -->

- The hardware resources in modern servers should be enough to allow for low latency and high packet rates at the samle time for datacenter applications. The reason why pervious designs all failed is that there exist a mismatch between the hardware and the OS.
- The four principles that construct the design of IX are: 
  - Separation and protection of control plane and data plane
  - Run to completion with adaptive batching
  - Native zero-copy API with explicit control flow
  - Flow consistent, synchronization free processing


### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- As suggested by Simon Peter, "the papers differ in how network I/O policy is enforced. Arrakis reaches for utmost performance by relying on hardware to enforce per-application maximum I/O rates and allowed communication peers. IX trades performance for software control over network I/O, thus allowing the precise enforcement of the I/O behavior of a particular network protocol, such as TCP congestion control" [1].
- Batching is traditionally a trade-off between low latency and high thoughput. However, according to the second principle, IX uses adaptive, bounded batching that successfully improved on both latency and throughput.

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
For the connection scalability, under high connection counts, the workload could not fit into the processor's L3 cache. Moreover, "The current IX implementation does not yet exploit IOMMUs or VT-d".

### Summary of Key Results 
<!-- [Up to 3 results] -->

- Belay et al. first evaluated IX against a baseline running the most recent Linux kernel and mTCP. It can be shown that IX achieved "goodput" for different message sizes.
- In the throughput and scalability test, IX achieved 1.9× the throughput of mTCP and 8.8× that of Linux.
- Finally, the throughput-latency curves for the two memcached workloads for Linux and IX showned that IX significantly reduces the unloaded latencies to roughly half.


### Open Questions 
<!-- [Where to go from here?] -->
For the limitation that under high connection counts, the workload could not fit into the processor's L3 cache, authors believed that "further optimizations in the size and access pattern of lwIP’s TCP/IP protocol control block structures can substantially reduce this handicap". Moreover, Belay et al. also planned to add support for interrupts to the IX dataplanes, explore the synergies between IX and networking protocols like DCTCP, ECN, etc.

### Citation: 
[1] https://blog.acolyer.org/2016/06/15/ix-a-protected-dataplane-operating-system-for-high-throughput-and-low-latency/

