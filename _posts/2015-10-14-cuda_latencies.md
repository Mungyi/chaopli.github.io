---
layout: post
title: "Review of CUDA programming"
date: 2015-10-14
---

# Programming strategy in terms of GPU architecture
* The core used for computation is called **Streaming Multiprocessor (SM)** on
  GPU.

* The number of *Warps* are different between the current architecture (Kepler
  and Maxwell) and previous architecture (Fermi).

* The register file size and the maximum number of concurrent warps in SMM are
  the same as in SMX (64k 32-bit registers and 64 warps, respectively), as is
  the maximum number of registers per thread (255). 

* Number of maximum active blocks (per SM) determines the number of active warps
  working concurrently in a SM. The $Occupancy=Active Warps/Maximum Active
  Warps$.

* Potential occupancy limiters:
  * Register usage
  * Shared memory usage
  * Block size
 
 The above resources are shared within a SM. The ideal condition is that we make
 the *Occupancy* equals to 1. The more active blocks the GPU supports the less
 resource could be allocated to each thread. So we should adjust the resources
 usage based on our problem and architectures.

# Programming strategy in terms of hiding latency
* Instruction-Level Parallism: execute independent instructions in a thread
  code.

To be reorganized...
