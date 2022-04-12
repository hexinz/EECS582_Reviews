# [Dynamo: Amazon’s Highly Available Key-value Store](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
People in Amazon want to solve the reliability problem at massive scale: tens of thousands of servers and network components located in many datacenters around the world where small and large components fail continuously.


### Summary 
<!-- [Up to 3 sentences] -->
DeCandia et al. proposed Dynamo, which is a novel highly available key-value storage system that sacrifices consistency under certain failures to provide an always-reliable experience for Amazon's core services. Dynamo takes advantage of consistent hashing for data partitioning and replicating, object versioning to facilitate consistency, application-assisted conflict resolution (a quorum-like technique and a decentralized replica synchronization protocol) to maintain consistency among replicas during updates as well as a gossip based distributed failure detection and membership protocol. Dynamo also has the flexibility to remove or add storage nodes without manual partitioning or redistribution since it is a complete decentralized system with minimal need for manual administration.

### Key Insights 
<!-- [Up to 2 insights] -->
- Design considerations of Dynamo:
  - Optimistic replication techniques increase availbility but add burden on conflicts resolution.
  - To decide when to perform the process of resolving update conflicts, which usually happens during reads or writes, since users don't want write to be rejected only because data cannot reach all the replicas at a given time, designers push the complexity of conflict resolution to the reads instead.
  - To decide who to perform the process of resolving update conflicts, since application is aware of the data schema, it could tailor the conflict resolution method instead of only using simple policies like "last write wins" in the data store.
- Other design principles of Dynamo:
  - Incremental scalability
  - Symmetry
  - Decentralization
  - Heterogeneity

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->
-  Dynamo introduces a novel API such that by providing the necessary knobs using the three parameters of (N,R,W), users are able to tune parameters based on their needs to customize their storage system to meet their desired performance, durability and consistency SLAs.
-  Dynamo adopts a full membership model where each node is aware of the data hosted by its peers by each node actively gossips the full routing table with other nodes in the system.

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- Dynamo's initial design targets a scale of up to hundreds of storage hosts. Hence it may have scalability limitations problem.

### Summary of Key Results 
<!-- [Up to 3 results] -->
- Dynamo is a novel highly available and scalable key-value storage system that is used for storing state of a number of core services of Amazon’s e-commerce platform.
- Dynamo takes advantage of a series of techniques to achieve availability, performance and handle server failures, data center failures and network partitions as well as allow users to scale up and down according to their current request load.
- Dynamo also has the flexibility for servie owners to customize their storage system by providing the necessary knobs using the three parameters of (N,R,W) to tune the parameters.

### Open Questions 
<!-- [Where to go from here?] -->
In the future, the limitation on scale due to the adoption of a full membership model can be solved by introducing hierarchical extensions to Dynamo. How could we do that in detail?
