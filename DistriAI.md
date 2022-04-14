# [Ray: A Distributed Framework for Emerging AI Applications](https://www.usenix.org/system/files/osdi18-moritz.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Nowadays, AI applications impose more and more new and demanding systems requirements, which adds burden to both performance and flexibility.

### Summary 
<!-- [Up to 3 sentences] -->
Moritz at el. proposed Ray, a distributed system that has a unified interface for both task-parallel and actor-based computations, which are supported by a single dynamic execution engine. Ray also employs a distributed scheduler and a distributed and fault-tolerant store to manage the system’s control state. According to the experiment, Ray achieves 1.8 million tasks per second and has better performance than existing systems over challenging reinforcement learning applications.

### Key Insights 
<!-- [Up to 2 insights] -->
- A framework for RL applications must provide efficient support for training, serving, and simulation. In addition, such a framework should also satisfy the following requirements:
  - Fine-grained, heterogeneous computations.
  - Flexible computation model.
  - Dynamic execution.
- Finally, to achieve high utilization in large clusters, such a framework must handle millions of tasks per. Also, such a framework should enable seamless integration with existing simulators and deep learning frameworks.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->
- Ray’s architecture comprises an application layer implementing the API, and a system layer providing high scalability and fault tolerance.
  - The application layer consists of three types of processes:
    - Driver: A process executing the user program.
    - Worker: A stateless process that executes tasks (remote functions) invoked by a driver or another worker.
    - Actor: A stateful process that executes, when invoked, only the methods it exposes.
  - The The system layer consists of three major components: a global control store, a distributed scheduler, and a distributed object store. All components are horizontally scalable and fault-tolerant.
- Moritz at el. also designed a two-level hierarchical scheduler consisting of a global scheduler and per-node local schedulers that balances locality and latencies, and achieve high scale such that Ray can dynamically schedule millions of tasks per second. 

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- It is mentioned that Ray cannot substitute for serving systems like TensorFlow since Ray could not address model management, testing, and model composition. Also, Ray cannot substitute for generic data-parallel frameworks like Spark since it lacks rich functionality and APIs such as query optimization.

### Summary of Key Results 
<!-- [Up to 3 results] -->
Moritz at el. made the following contributions: 
- Design and build the first distributed framework that unifies training, simulation, and serving—necessary components of emerging RL applications.
- Unify the actor and task-parallel abstractions on top of a dynamic task execution engine.
- Propose a system design principle in which control state is stored in a sharded metadata store and all other system components are stateless and a bottom-up distributed scheduling strategy.

### Open Questions 
<!-- [Where to go from here?] -->
- How Ray can make scheduling decisions without full knowledge of the computation graph?
- How to implementation of garbage collection policies to bound storage costs in the GCS?
