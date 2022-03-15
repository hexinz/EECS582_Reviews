# [Bigtable: A Distributed Storage System for Structured Data](https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Users of Bigtable complaints about difficuity in using for applications that have complex, evolving schemas, or those that want strong consistency in the presence of wide-area replication. Spanner has also been motivated by the popularity of Megastore. Many applications at Google (e.g., Gmail, Picasa, Calendar, Android Market, and AppEngine) chose to use Megastore because of its semi-relational data model and synchronous replication, despite its poor write throughput.

### Summary 
<!-- [Up to 3 sentences] -->

Spanner is Google’s scalable, multi-version, globally-distributed, and synchronously-replicated database, which primirily deals with managing cross-datacenter replicated data. The fact that Spanner assigns globally-meaningful commit timestamps to transactions, even though transactions may be distributed, make the API support important features including dynamically controlled replication configurations at a fine grain, external consistenct reads and writes and globally-consistent reads across the database at a timestamp, which also result in support for consistent backups, consistent MapReduce executions and atomic schema updates, all at global scale. Spanner also supports non-blocking reads in the past, and lock-free read-only transactions for performance improvement. 

### Key Insights 
<!-- [Up to 2 insights] -->
-  the linchpin of Spanner’s feature set is TrueTime. Reifying clock uncertainty in the time API makes it possible to build distributed systems with much stronger time semantics. In addition, as the underlying system enforces tighter bounds on clock uncertainty, the overhead of the stronger semantics decreases. Author suggests that we should no longer depend on loosely synchronized clocks and weak time APIs in designing distributed algorithms.


### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- The new TrueTime API and its implementation enables automatical globally-meaningful commit timestamps to transactions even when distributed. The TrueTime exposes clock uncertainty, and the guarantees on Spanner’s timestamps depend on the bounds that the implementation provides: if the uncertainty is large, Spanner slows down to wait out that uncertainty. The TureTime reflects the serialization order and thus the API enables externally consistent (if a transaction T1 commits before another transaction T2 starts, then T1's commit timestamp is smaller than T2's) reads and writes, and globally-consistent reads across the database at a timestamp.
-  Data are stored in tablets, which is not necessarily lexicographically contiguous parition. Therefore, it is possible for a tablet container to colocate multiple buckets (direcotries) that are frequently accessed together. By carefully assigning keys to the data and moving data in the unit of buckets, applications can control the locality, thereby potentially lowering latency.


### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- Spanner doesn't support the full SQL semantics thus has limited applications in Ads databases for example.
- The write operations are still using Paxos for consensus, which provides strong consistency at the cost of increasing latency and troublesome with master failure.

### Summary of Key Results 
<!-- [Up to 3 results] -->
- Spanner stores data in schematized semi-relational tables and version-ed; provides a SQL-based query language; 
- Spanner supports features: 1) replications configuration can be dynamically controlled; 2) externally consistent read/write operations; both are enabled by the globally-assigned timestamps, and supported by the TrueTime API and its implementation;



### Open Questions 
<!-- [Where to go from here?] -->
- How to deal with clock failure or incorrect working of clocks in local machines?
- How is the performance of Spanner for advanced relational DB operations like JOINs?
- How to improve writing performance and timestamp accuracy (sometimes just waiting for TT.after to be true)?

### Reference
[1] http://muratbuffalo.blogspot.com/2013/07/spanner-googles-globally-distributed_4.html
[2] https://souptikji.github.io/blog/2018/03/Spanner
