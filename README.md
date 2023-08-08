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

### Comparative analysis of the execution times for each implementation for text size 2<<25, pattern length m = 10, pattern count n = 16
1. C++: Execution time = 461545.967 microseconds (μs)
2. CUDA: Execution time = 425.087 microseconds (μs)
3. CUDA V2.0: Execution time = 278.375 microseconds (μs)

### Let's calculate the percentage differences:

#### For CUDA V2.0: <br />
Percentage Difference = ((CUDA V2.0 Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((278.375 μs - 461545.967 μs) / 461545.967 μs) * 100 = -99.94%

#### For CUDA: <br />
Percentage Difference = ((CUDA Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((425.087 μs - 461545.967 μs) / 461545.967 μs) * 100 = -99.91%

#### For CUDA V2.0 vs. CUDA: <br />
Percentage Difference = ((CUDA V2.0 Execution Time - CUDA Execution Time) / CUDA Execution Time) * 100 = ((278.375 μs - 425.087 μs) / 425.087 μs) * 100 = -34.54%



### Analysis:

1. CUDA V2.0 vs. C++:
   The execution time of the CUDA V2.0 implementation is approximately 99.94% less than the C++ implementation. This indicates a significant improvement in performance when using CUDA V2.0 compared to the original C++ implementation.

2. CUDA vs. C++:
   The execution time of the CUDA implementation is approximately 99.91% less than the C++ implementation. Similar to the previous analysis, this result also highlights a substantial improvement in performance by using CUDA compared to the original C++ version.

3. CUDA V2.0 vs. CUDA:
   The execution time of the CUDA V2.0 implementation is approximately 34.54% less than the regular CUDA implementation. This suggests that CUDA V2.0 provides further optimization over the previous CUDA implementation, resulting in a noticeable reduction in execution time.

The percentage differences indicate that both the CUDA and CUDA V2.0 implementations are highly optimized and offer substantial performance improvements compared to the original C++ implementation. The positive outcomes show the effectiveness of utilizing GPU acceleration through CUDA programming.

Overall, the NVIDIA Thrust library-based CUDA approach emerged as the clear winner in terms of execution time and performance, offering unparalleled speed and efficiency for the Rabin-Karp algorithm.

## B. Screenshot of the program output (C++)
### For Pattern length m = 10, Pattern count n = 16
![Colab C++ Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/4713fa421b1c3134b90e76cd60cceec887d3ff47/RK%20C1.png)
![Colab C++ Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/4713fa421b1c3134b90e76cd60cceec887d3ff47/RK%20C1b.png)


## C. Screenshot of the program output (CUDA)
### For Pattern length m = 10, Pattern count n = 16
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/4713fa421b1c3134b90e76cd60cceec887d3ff47/RK%20CUDA1a.png)
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/4713fa421b1c3134b90e76cd60cceec887d3ff47/RK%20CUDA1b.png)


## D. Screenshot of the program output (CUDA V2.0)
### For Pattern length m = 10, Pattern count n = 16
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/4713fa421b1c3134b90e76cd60cceec887d3ff47/RK%20CUDA2%201a.png)
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/4713fa421b1c3134b90e76cd60cceec887d3ff47/RK%20CUDA2%201b.png)
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/4713fa421b1c3134b90e76cd60cceec887d3ff47/RK%20CUDA2%201c.png)
