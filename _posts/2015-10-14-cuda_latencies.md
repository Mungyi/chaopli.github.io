---
layout: post
title: "Review of CUDA programming"
date: 2015-10-14
header-img: "img/cuda.jpg"

---

# Programming strategy in terms of GPU architecture
* A core used for computation is a float processing unit (FPU) in a **Streaming
  Multiprocessor (SM)** on GPU. Each SM are exactly the same on the same GPU.
  SMs on Different GPU have different number of cores.

* *Warp* is a group of threads that run the same operations. The number of
  *Warps* are different between the current architecture (Kepler and Maxwell)
  and previous architecture (Fermi).

* Warps, threads and blocks are abstract structures, which are scheduled onto
  cores by the warp scheduler. Warps are the structures used to map into
  cores. There are some parameters need to be awared by programmer:
  * max number of active warps per SM
  * max number of threads per block
  * max number of blocks per SM

The above parameters are differed from different compute capability.

* The register file size and the maximum number of concurrent warps in SMM are
  the same as in SMX (64k 32-bit registers and 64 warps, respectively), as is
  the maximum number of registers per thread (255). 

* Number of maximum active blocks (per SM) determines the number of active warps
  working concurrently in a SM. The Occupancy=Active Warps/Maximum Active
  Warps.

* Potential occupancy limiters:
  * Register usage
  * Shared memory usage
  * Block size
 
 The above resources are shared within a SM. The ideal condition is that we make
 the *Occupancy* equals to 1. The more active blocks the GPU supports the less
 resource could be allocated to each thread. So we should adjust the resources
 usage based on our problem and architectures.
 
 The size of block is the number of threads assigned in a block. Each SM has a
 maximum number of active block. If the number of threads is too small, to
 achieve the same occupancy, one will probably have to use more blocks. If there
 are no so many SMs available, it will be not full occupancy. For example, assume
 we have a SM supporting 16 active blocks per SM. It has 128 cores in total. We
 can have at most 16 blocks (8 threads in each block).

 The following table shows the comparison between GK107 (Kepler) and GM107
 (Maxwell)

|GPU|GK107|GM107|
|---|-----|-----|
| CUDA Cores|384|640|
| Base Clock|1058 MHz|1020 MHz|
| GPU Boost Clock|N/A|1085 MHz|
| GFLOP/s|812.5|1305.6|
| Compute Capability|3.0|5.0|
| Shared Memory / SM|16KB / 48 KB|64 KB|
| Register File Size / SM|256 KB|256 KB|
| Active Blocks / SM|16|32|
| Memory Clock|5000 MHz|5400 MHz|
| Memory Bandwidth|80 GB/s|86.4 GB/s|
| L2 Cache Size|256 KB|2048 KB|
| TDP|64W|60W|
| Transistors|1.3 Billion|1.87 Billion|
| Die Size|118 mm2|148 mm2|
| Manufactoring Process|28 nm|28 nm|

# Programming strategy in terms of hiding latency
* Instruction-Level Parallism: execute independent instructions in a thread
  code.
* Memory-Level Parallism

To be reorganized...
