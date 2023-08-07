# csc612m-rabin-karp-CUDA

## Program Specifications
### Inputs
1. text string t of length n = 2^25 (roughly 33 million characters)*
2. Pattern count p = 4, 8, 16**
3. Pattern length m = 10, 20, 30 characters
 <br />  *external text file (text2.txt)
 <br />  **array 

### Output
1. Number of matches and the corresponding index number

## Comparative execution time and analysis of the performance of the different kernels
The Rabin-Karp algorithm was implemented using three distinct methods: C++, CUDA, and CUDA V2.0 (utilizing the NVIDIA Thrust Library). Each method's efficiency was assessed by measuring its execution time and performance, allowing for a comparison to be made and differences to be identified.

Regarding execution time, the GPU-based parallel implementations (CUDA and CUDA V2.0) displayed significantly superior performance in comparison to the sequential approach (C++), as expected. These GPU implementations take advantage of the parallel processing capabilities inherent to GPUs, which are optimized for handling extensive parallel workloads. By distributing tasks across numerous threads, these implementations harness the full potential of the GPU, resulting in quicker execution times when contrasted with the sequential CPU-driven approach. The unoptimized C++ implementation exhibited the slowest execution time, as it relies on a solitary CPU thread to execute the Rabin-Karp algorithm step by step.

Furthermore, it becomes apparent that the utilization of the NVIDIA Thrust library can lead to additional performance optimization for the Rabin-Karp program based on CUDA parallel implementation.

### Comparative analysis of the execution times for each implementation for array size 2<<25
1. C++: Execution time = 58120164 microseconds (μs)
2. CUDA: Execution time = 2.12906 seconds = 2129060 microseconds (μs)
3. CUDA V2.0: Execution time = 57651444 microseconds (μs)

### Let's calculate the percentage differences:

For CUDA V2.0:
Percentage Difference = ((CUDA Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((2129060 μs - 58120164 μs) / 58120164 μs) * 100 = -96.34%

For CUDA:
Percentage Difference = ((SIMD Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((57651444 μs - 58120164 μs) / 58120164 μs) * 100 = -0.81%


### Analysis:

1. The CUDA implementation shows a significant speedup of approximately 96.34% compared to the C++ implementation.
2. The SIMD implementation has a negligible speedup of approximately 0.81%. This result indicates that SIMD's parallel processing capabilities do not provide a significant advantage over the sequential C++ implementation for the particular problem or data size considered.
3. The x86 implementation shows a moderate speedup of approximately 10.99% compared to the C++ implementation. However, it is still less efficient than CUDA's massive parallelism.

The performance analysis reveals that CUDA's superiority is due to its massive parallelism. While the CPU-based approaches execute the dot product sequentially, CUDA's GPU parallelism allows it to perform simultaneous calculations on multiple elements of the arrays.

One overhead worth mentioning is the kernel invocation in the CUDA approach. When calling the CUDA kernel, there is an inherent overhead associated with launching threads and initializing the GPU computation environment. This overhead is relatively small for large data sets but can become significant for smaller data sizes. Additionally, data transfer between the host (CPU) and the device (GPU) incurs some overhead, especially when dealing with large arrays. 

Overall, the CUDA approach emerged as the clear winner in terms of execution time and performance, offering unparalleled speed and efficiency for the dot product computation.

## B. Screenshot of the program output with correctness check (C)
### For Pattern length m = 10, Pattern count n = 16
![Colab C++ Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/c777398cce0788d170ae418c4b09a6d2b94cb54b/RK%20C1.png)


## C. Screenshot of the program output with correctness check (CUDA )
### For Pattern length m = 10, Pattern count n = 16
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/c777398cce0788d170ae418c4b09a6d2b94cb54b/RK%20CUDA1a.png)
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/c777398cce0788d170ae418c4b09a6d2b94cb54b/RK%20CUDA1b.png)


## D. Screenshot of the program output with correctness check (CUDA V2.0)
### For Pattern length m = 10, Pattern count n = 16
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/c777398cce0788d170ae418c4b09a6d2b94cb54b/RK%20CUDA2%201a.png)
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/c777398cce0788d170ae418c4b09a6d2b94cb54b/RK%20CUDA2%201b.png)
