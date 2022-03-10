# [Spanner: Google’s Globally-Distributed Database](https://static.googleusercontent.com/media/research.google.com/en//archive/spanner-osdi2012.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Users of Bigtable complaints about difficuity in using for applications that have complex, evolving schemas, or those that want strong consistency in the presence of wide-area replication. Spanner has also been motivated by the popularity of Megastore. Many applications at Google (e.g., Gmail, Picasa, Calendar, Android Market, and AppEngine) chose to use Megastore because of its semi-relational data model and synchronous replication, despite its poor write throughput.

### Summary 
<!-- [Up to 3 sentences] -->

Spanner is Google’s scalable, multi-version, globally-distributed, and synchronously-replicated database, which primirily deals with managing cross-datacenter
replicated data. The fact that Spanner assigns globally-meaningful commit timestamps to transactions, even though transactions may be distributed, make the API support important features including dynamically controlled replication configurations at a fine grain, external consistenct reads and writes and globally-consistent reads across the database at a timestamp, which also result in support for consistent backups, consistent MapReduce executions and atomic schema updates, all at global scale. Spanner also supports non-blocking reads in the past, and lock-free read-only transactions for performance improvement. 

### Key Insights 
<!-- [Up to 2 insights] -->
- Rationale 


### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->
- The new TrueTime API and its implementation enables automatical globally-meaningful commit timestamps to transactions even when distributed. The TrueTime exposes clock uncertainty, and the guarantees on Spanner’s timestamps depend on the bounds that the implementation provides: if the uncertainty is large, Spanner slows down to wait out that uncertainty. The TureTime reflect the serialization order and thus the API enables externally consistent (if a transaction T1 commits before another transaction T2 starts, then T1's commit timestamp is smaller than T2's) reads and writes, and globally-consistent reads across the database at a timestamp.
- There is a strong use of data locality using the concept of buckets. Data are stored in tablets, which are also classified into different “buckets”. Applications can control the locality of data by carefully assigning keys to the data, thereby potentially lowering latency.

Data are stored in tablets, which are also classified into different “buckets”. Applications can control the locality of data by carefully assigning keys to the data. This feature could potentially lower the latency (by choosing closer datacenters for storage);
Dynamic controlled replication configuration might be helpful when the application is trying to change the data location or replication factors during the run.



### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
- Spanner doesn't support the full SQL semantics thus has limited applications in Ads databases for example.
- The write operations are still using Paxos for consensus, which provides strong consistency at the cost of increasing latency and troublesome with master failure.

### Summary of Key Results 
<!-- [Up to 3 results] -->



### Open Questions 
<!-- [Where to go from here?] -->
- How to deal with clock failure or incorrect working of clocks in local machines?
- How is the performance of Spanner for advanced relational DB operations like JOINs?
- How to improve writing performance and timestamp accuracy (sometimes just waiting for TT.after to be true)?

### Reference
[1] http://muratbuffalo.blogspot.com/2013/07/spanner-googles-globally-distributed_4.html
[2] https://souptikji.github.io/blog/2018/03/Spanner

