# bartender
A high performance distributed guaranteed failure-atomic NVRAM-based memory allocator.

# What is "bartender"?
"bartender" is a distributed NVRAM-based memory allocator, with a traditional C-like memory management interface(malloc/free) and can be deployed on a cluster of host machines connected by InfiniBand or Ethernet
to provide a transparent memory allocation API for the clients.

# Features
- NVRAM-based
  - Guaranteed failure-atomic
  - Failure recovery
  - Transaction
- Distributed clusters
  - Transparent
- Concurrency
  - Cache locality
  - Contention
- Auto defragmentation

# Challenges
- For NVRAM
  1. Memory leak on NVRAM.
  1. Data consistency and its overhead
- For distributed memory allocators
  1. Consistency
  1. Latency and throughput
  1. Locality
  1. Fragmentation
- For concurrent systems
  1. Consistency
  1. Contention
  1. Memory blowup

# Requirements
### For development
- Hardware
  - PC
- Software
  - VirtualBox
  - rustc

### For production
TODO

# Setup
### Single node
- This repository
- rust
- gcc

### Multiple nodes on single machine
TODO

# Usage

```c
#include <bartender.h>

struct btd_config btd_config;
btd_config.single_node = 1;

struct btd_cluster *p_cluster = btd_cluster_create(&btd_config);
const char *s = "123";
char *p_data = btd_malloc(p_cluster, 100);
btd_memcpy(p_data, s, strlen(s));
btd_free(p_data);
```

# Benchmark
- nvm_malloc benchmark https://github.com/IMCG/nvm-malloc/tree/master/benchmark

# Design
TODO


# TODOs
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

1. Distributed Memory Management
  - e.g. maybe CEPH, ZFS or GFS for consistency, performance, fragmentation
1. Benchmark tools or methods
  - nvm_malloc benchmarks
1. IB, NVRAM Emulator
  - Use RAM disk + mmap to emulate NVRAM
  - Use local RAM to emulate remote memory or Ethernet-based RDMA?
1. GitBooks
  - Try GitBooks for our documentation
1. Easy LaTeX editor or transformer
  - maybe pandoc + vim?

1. New programming language with NVM variable support?

# References
- [1] Bhandari K, Chakrabarti D R, Boehm H. Makalu: fast recoverable allocation of non-volatile memory[J]. Acm Sigplan Notices, 2016, 51(10):677-694.
- [2] Mellanox, http://www.mellanox.com/related-docs/prod_software/RDMA_Aware_Programming_user_manual.pdf
- [3] Berger E D, Mckinley K S, Blumofe R D, et al. Hoard: a scalable memory allocator for multithreaded applications[C]// International Conference on Architectural Support for Programming Languages and Operating Systems. ACM, 2000:117-128.
- [4] Volos H, Tack A J, Swift M M. Mnemosyne:lightweight persistent memory[J]. Acm Sigarch Computer Architecture News, 2011, 47(4):91-104.
- [5] Coburn J, Caulfield A M, Akel A, et al. NV-Heaps: making persistent objects fast and safe with next-generation, non-volatile memories[C]// Sixteenth International Conference on Architectural Support for Programming Languages and Operating Systems. ACM, 2011:105-118.
- [6] Christopher Mitchell, Yifeng Geng, Jinyang Li. Using one-sided RDMA reads to build a fast, CPU-efficient key-value store[C]// Usenix Conference on Technical Conference. USENIX Association, 2013:103-114.
- [7] Kalia A, Kaminsky M, Andersen D G. Using RDMA efficiently for key-value services[C]// ACM Conference on SIGCOMM. ACM, 2014:295-306.
- [8] Megalloc: Fast Distributed Memory Allocator for NVM-Based Cluster
- [9] BDWGC, A garbage collector used in Makalu, https://github.com/ivmai/bdwgc.git
- [10] [pmem](http://pmem.io/) pmem, Intel's NVM Programming library
- [11] [pmem valgrind](https://github.com/pmem/valgrind.git) Enhanced Valgrind for Persistent Memory
- [12] [NVL-C](http://ft.ornl.gov/research/nvl-c) A extended C for NVM
