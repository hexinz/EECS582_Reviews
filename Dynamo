# [Dynamo: Amazon’s Highly Available Key-value Store](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
People in Google want to store and manage large-scale structured data. Also, multiple projects have a variety of demands for storing and managing data in terms of data size, latency, etc.

### Summary 
<!-- [Up to 3 sentences] -->

Bigtable is a distributed storage system, which built upon GFS to store log and data files and upon a lock service called Chubby, for managing large-scale structured data across thousands of commodity servers. Bigtable provides a simple model which allows clients to dynamically control over data layout and format and reason about the locality properties of data in the underlying storage. Bigtable also achieves flexibility, wide applicability, scalability, high-performance and high availability. 


### Key Insights 
<!-- [Up to 2 insights] -->

- The problem of master replicas consistency in the face of failure is addressed by using the Paxos algorithms. Moreover, master failures will not change the assignment of tablets to tablet servers.
- Clients can prefetch more than one tablet when it reads from METADATA.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

-  The data model of a Bigtable is a sparse, distributed, persistent multi-dimensional sorted map, which is indexed by a row key, column key, and a timestamp; each value in the map is an uninterpreted array of bytes. The Bigtable API provides functions for creating and deleting tables and column families. It also provides functions for changing cluster, table, and column family metadata, such as access control rights. Hence, Bigtable provides simplicity and flexibility for clients.

- The Chubby service consistes of five replicas, and only one of them is the master, which is mainly responsible for:
  - assigning tablets to tablet servers (each row range for a table is called a tablet), 
  - detecting the addition and expiration of tablet servers
  - balancing tablet-server load
  - garbaging collection of files in GFS. 


### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- Bigtable uses different systems and applications: GFS is the low level file storage solution, SSTable is the actually data structure, Chubby is responsible for metadata, cluster management and the stats monitoring. However, usage of multiple system and applications will lead to large overhead and complexity in maintenance.


### Summary of Key Results 
<!-- [Up to 3 results] -->
- Bigtable provides a simple model which allows clients to dynamically control over data layout and format and reason about the locality properties of data in the underlying storage. 
- Bigtable achieves flexibility, wide applicability, scalability, high-performance and high availability. 

### Open Questions 
<!-- [Where to go from here?] -->
How to solve the overhead caused by using multiple different systems and applications?
