# [AutoFDO: Automatic Feedback-Directed Optimization for Warehouse-Scale Applications](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/45290.pdf)
###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->
Traditional FDO (feedback-directed optimization) is introduced to guide compiler optimization using information about the code’s runtime behavior. However, the traditional FDO is seldom adopted due to difficulties in maintaining a representative benchmark, storing and accessing logs for loadtesting and overhead of instrumentation when under load. 

### Summary 
<!-- [Up to 3 sentences] -->

Dehao Chen, David Xinliang Li and Tipp Moseley proposed a new FDO, AutoFDO, which, instead of instrumentation, collects production profiles by sampling hardware performance monitors on production machines to compile the next release. It can achieve performance 85% as good as with instrumentation while have less overhead and more stability. It also tolerates stale profile data and can scale and automate for hundreds of production binaries.

### Key Insights 
<!-- [Up to 2 insights] -->
- In the profiling system, the symbolization service, while taking tens of milliseconds before, can only take a few tens of seconds to symbolize all of the samples observed for a single binary, which largely improves performance, client simplicity as well as processes of debugging and manually regenerating profiles for developers.
- In the compiler support, the authors provided 3-steps process of profile annotation as well as sources of profile inaccuracies, including recoverable transformations, unrecoverable benign transformations, and unrecoverable destructive changes.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->
- Profile samples are stored in a database, annotated with job metadata. Profile sampling makes further processing offline using only a little amount of data center resources.
- A batch job queries the databases and symbolizes the raw samples. As stated in the previous section, symbolizing samples can have less overhead than tranditional symbolization service. Finally, the symbolized samples are converted to the compiler’s profile format and submitted to version control.

### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->
Some applications like (like libquantum) do not benefit from AutoFDO or FDO due to lack of tuning and mis-optimization.

### Summary of Key Results 
<!-- [Up to 3 results] -->
- Combined with production automation and scale, AutoFDO has simplified the deployment of FDO to require only adding some compiler flags to enable, little amount of data center resources and negligible overhead. 
- Those advances have led to an 8X increase in customer adoption and doubled the number of cycles covered by FDO.

### Open Questions 
<!-- [Where to go from here?] -->
AutoFDO does not currently support targeted value profiling of the distribution of size, alignment of arguments to memcpy, etc, like the traditional FDO. Also, profile quality and scaling ability can be further improved. There are still a lot to be done.
