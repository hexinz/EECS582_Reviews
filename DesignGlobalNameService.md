# [Designing a Global Name Service](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/acrobat-15.pdf)

###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
The author wanted to create a name service such that every individual, organization or facility all over the world can be mapped into a set of labeled properties to 
assist authentication, mail addressing, resource location, etc. The requirements and challenges of that are high availability, large size, long life/continuing evolution, fault isolation and lack of global trust.

### Summary 
<!-- [Up to 3 sentences] -->

Butler W. Lampson in his talk proposed the design of a Global Name Service, which basically employs a hierarchical structure, composed of a tree of directories holding a tree of values. The names are thus also structured such that they can expand and evolve. The hierarchical structure facilitates growth and isolating faults and the provisions and methods are specified to enhance stability, non-deterministic lookup and authentication without global trust.

### Key Insights 
<!-- [Up to 2 insights] -->

- The hierarchical structure is the fundamental method for accommodating growth and isolating faults.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- The proposed global name service has a two-level structure. The client side includes a tree of directories. Each directory has a unique directory identifier (DI) and the leaves of the tree are organized into a tree of values. The client side has the functions of reading, updating, protection, authentication, etc. The administrative level not only sees the directories, but also directory copies (DC) storing on different servers. It enhances updating speed and reliability.
- The name has two parts: the full name of directory name and the value in that directory. The name is not only easy to type just as in a file system but also easy to find since the directory has a unique root that is kept in all servers all over the world. 


### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->

The article mainly focuses on the implementation and structure of the Global Name Service. The application is seldom mentioned. We do not know if it applies to the real-life application and how is the performance. 

### Summary of Key Results 
<!-- [Up to 3 results] -->

- The article suggest a hierarchical design of Global Name Service that addressses the problem of high availability, large size, long life/continuing evolution, and  fault isolation
- Detailed provisions and specifications are introduced to solve the problem of non-deterministic lookup and lack of global trust. 

### Open Questions 
<!-- [Where to go from here?] -->

What other applications the system can have? How is the performance? What are the new challenges the design will face? 
