# bartender
A distributed NVRAM-based memory allocator.


# NOTES
1. Malaku
    - Features
        - NVRAM-based memory allocator
        - Support for more familiar C-like malloc/free interface
        - Decrease latency by lazily persisting non-core metadata
        - Post-failure GC for data consistency

1. Hoard
    - [Hoard GitHub](https://github.com/emeryberger/Hoard)
    - Address following issues
        - Contention
        - False Sharing
        - Memory Blowup

1. Fast Cluster Communication
    - [Accelio](https://github.com/accelio/accelio)
    - or write a custom IB/RDMA-based high speed RPC/data transfer library

# TODOs
1. Distributed Memory Management(e.g. maybe CEPH or ZFS or GFS?, consistency, performance)
1. Benchmark tools or methods
1. GitBooks
1. Easy LaTeX editor or transformer

# References
- [1] Bhandari K, Chakrabarti D R, Boehm H. Makalu: fast recoverable allocation of non-volatile memory[J]. Acm Sigplan Notices, 2016, 51(10):677-694.
- [2] Mellanox, http://www.mellanox.com/related-docs/prod_software/RDMA_Aware_Programming_user_manual.pdf
- [3] Berger E D, Mckinley K S, Blumofe R D, et al. Hoard: a scalable memory allocator for multithreaded applications[C]// International Conference on Architectural Support for Programming Languages and Operating Systems. ACM, 2000:117-128.
- [4] Volos H, Tack A J, Swift M M. Mnemosyne:lightweight persistent memory[J]. Acm Sigarch Computer Architecture News, 2011, 47(4):91-104.
- [5] Coburn J, Caulfield A M, Akel A, et al. NV-Heaps: making persistent objects fast and safe with next-generation, non-volatile memories[C]// Sixteenth International Conference on Architectural Support for Programming Languages and Operating Systems. ACM, 2011:105-118.
- [6] Christopher Mitchell, Yifeng Geng, Jinyang Li. Using one-sided RDMA reads to build a fast, CPU-efficient key-value store[C]// Usenix Conference on Technical Conference. USENIX Association, 2013:103-114.
- [7] Kalia A, Kaminsky M, Andersen D G. Using RDMA efficiently for key-value services[C]// ACM Conference on SIGCOMM. ACM, 2014:295-306.
- [8] Megalloc: Fast Distributed Memory Allocator for NVM-Based Cluster