# [Exokernel: An Operating System Architecture for Application-Level Resource Management](https://pdos.csail.mit.edu/6.828/2016/readings/engler95exokernel.pdf)

###### Hexin Zhang (hexinz@umich.edu)

---

### The Problem
<!-- [A single problem] -->

Traditional operating systems have limited performance, flexibility and functionality of applications since they have fixed the interface between applications and
physical resources. In other words, one could hardly modifies implementations of existing abstractions, adds new abstractions or does any domain-specific optimizations with fixed high-level abstractions.

### Summary 
<!-- [Up to 3 sentences] -->

Dawson R. Engler, M. Frans Kaashoek, and James O’Toole Jr. designed a new operating system architecture called *Exokernel*, which solved the above problems by providing application-level management of physical resources. To securely export hardware resources to applications , exokernel follows the design principle of separting protection from management.

### Key Insights 
<!-- [Up to 2 insights] -->

- Fixed high-level abstractions hurt application performance, hide information from applications, making implementation of own resource management abstractions hard for applications like database, and limit the functionality of applications since they could only use the existing fixed interface.
- Design principles of exokernel include 1) securely expose hardware: avoid resource management except required by protection), 2) expose allocation: allow library operating systemsto requestspecific physical resources, 3) expose names: exokernels should use physical names wherever possible to be efficient. and 4) expose revocation: utilize a visible resource revocation protocol so that library operating systems can perform effective application-level resource management.

### Notable Design Details/Strengths 
<!-- [Up to 2 details/strengths] -->

- To realize application-level management of physical resources, exokernel defines a low-level interface that securely multiplexes available hardware resources. Then, library operating systems, which works above the exokernel interface, implement most of the abstractions at application level so that applications can select libraries or create their own to enhance performance, flexibility and functionality. 
- To realize separating protection from management design principle, exokernel employes three techinques: 1) secure bindings: applications bind to resources securely through library operating systems; 2) visible resource revocation: library operating systems participate in resource revocation protocol and 3) abort protocol: an exokernel can break secure bindings of unsafe applications by force. Secure binding also includes hardware mechanism for applications to directly access hardware resources, software caching for frequently used secure bindings and downloading application code into the kernel. 


### Limitations/Weaknesses 
<!-- [up to 2 weaknesses] -->

- Designing exokernel interfaces is complex (implementation is not).
- The exokernel can be less consistency.



### Summary of Key Results 
<!-- [Up to 3 results] -->

- Due to the simplicity and limited number of exokernel primitives, they are fast and can be implemented efficiently.
- Low-level, secure multiplexing of hardware resources and operating system abstractions at application level can also be implemented efficiently.
- Applications can implement purpose-specific abstractions to enhance flexibility and functionality.

### Open Questions 
<!-- [Where to go from here?] -->

The problem of consistency caused by different development of applications needs to be solved. Also, more detailed design of the low-level interface that communicates with hardware directly is open to discuss.

