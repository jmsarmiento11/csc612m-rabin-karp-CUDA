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

Furthermore, it becomes apparent that the utilization of the NVIDIA Thrust library can lead to additional performance optimization for the Rabin-Karp program based on CUDA parallel implementation, depending on given parameters like size or length of text and pattern.

### Comparative analysis of the execution times for each implementation for text size 2<<25, pattern length m = 10, pattern count n = 4
1. C++: Execution time = 736795.73 microseconds (μs)
2. CUDA: Execution time = 1551.64 microseconds (μs)
3. CUDA V2.0: Execution time = 1271.90 microseconds (μs)

### Let's calculate the percentage differences:

#### For CUDA V2.0: <br />
Percentage Difference = ((CUDA V2.0 Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((1271.90 μs - 736795.73 μs) / 736795.73 μs) * 100 = -99.83%

#### For CUDA: <br />
Percentage Difference = ((CUDA Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((1551.64 μs - 736795.73 μs) / 736795.73 μs) * 100 = -99.79%

#### For CUDA V2.0 vs. CUDA: <br />
Percentage Difference = ((CUDA V2.0 Execution Time - CUDA Execution Time) / CUDA Execution Time) * 100 = ((1271.90 μs - 1551.64 μs) / 1551.64 μs) * 100 = -18.00.00%

### Comparative analysis of the execution times for each implementation for text size 2<<25, pattern length m = 20, pattern count n = 16
1. C++: Execution time = 6427887.90 microseconds (μs)
2. CUDA: Execution time = 2240.60 microseconds (μs)
3. CUDA V2.0: Execution time = 2285.56 microseconds (μs)

### Let's calculate the percentage differences:

#### For CUDA V2.0: <br />
Percentage Difference = ((CUDA V2.0 Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((2285.56 μs - 6427887.90 μs) / 6427887.90 μs) * 100 = -99.96%

#### For CUDA: <br />
Percentage Difference = ((CUDA Execution Time - C++ Execution Time) / C++ Execution Time) * 100 = ((2240.60 μs - 6427887.90 μs) / 6427887.90 μs) * 100 = -99.97%

#### For CUDA V2.0 vs. CUDA: <br />
Percentage Difference = ((CUDA V2.0 Execution Time - CUDA Execution Time) / CUDA Execution Time) * 100 = ((2285.56 μs - 2240.60 μs) / 2240.60 μs) * 100 = 2.00%

### Analysis:

1. CUDA V2.0 vs. C++:
   The execution time of the CUDA V2.0 implementation is approximately 99.83-99.96% less than the C++ implementation. This indicates a significant improvement in performance when using CUDA V2.0 compared to the original C++ implementation.

2. CUDA vs. C++:
   The execution time of the CUDA implementation is approximately 99.79-99.97% less than the C++ implementation. Similar to the previous analysis, this result also highlights a substantial improvement in performance by using CUDA compared to the original C++ version.

3. CUDA V2.0 vs. CUDA:
   In the provided comparative analysis, two different scenarios are compared using CUDA V2.0 and the original CUDA version. The comparison is based on the execution time of the algorithms in different conditions.

For the first scenario, where the pattern length (m) is 10, and pattern count (n) is 4, the calculated percentage difference is -18.00%. This implies that CUDA V2.0 performs approximately 18.00% better in terms of execution time compared to the original CUDA version.

In the second scenario, where the pattern length (m) is 20, and pattern count (n) is 16, the calculated percentage difference is 2.00%. This means that CUDA V2.0 shows a minor improvement of 2.00% in execution time compared to the original CUDA version. While this is a smaller improvement, it still indicates enhanced performance.

Overall, the analysis highlights that CUDA V2.0 generally outperforms the original CUDA version in both scenarios, leading to faster execution times for the specified task configurations.

In the context of execution time and overall performance, adopting the CUDA approach integrated with the NVIDIA Thrust library showcases improvements compared to the current implementation based solely on CUDA. This enhancement is particularly noticeable when dealing with smaller pattern counts and lengths within the context of the Rabin-Karp algorithm.

## B. Screenshot of the program output (C++)
### For Pattern length m = 10, Pattern count n = 4
![Colab C++ Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/dd32aedc39d325f4aefc304172b38d549c3bcee5/RK%20C2.png)
![Colab C++ Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/dd32aedc39d325f4aefc304172b38d549c3bcee5/RK%20C2b.png)

### For Pattern length m = 20, Pattern count n = 16
![Colab C++ Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/9a320f26bb5392efb5dc6030faf35f995c524359/RK%20C1.png)
![Colab C++ Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/9a320f26bb5392efb5dc6030faf35f995c524359/RK%20C1b.png)


## C. Screenshot of the program output (CUDA)
### For Pattern length m = 10, Pattern count n = 4
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/dd32aedc39d325f4aefc304172b38d549c3bcee5/RK%20CUDA2%201a.png)
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/dd32aedc39d325f4aefc304172b38d549c3bcee5/RK%20CUDA2%201b.png)

### For Pattern length m = 20, Pattern count n = 16
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/9a320f26bb5392efb5dc6030faf35f995c524359/RK%20CUDA1a.png)
![Colab CUDA Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/9a320f26bb5392efb5dc6030faf35f995c524359/RK%20CUDA1b.png)

## D. Screenshot of the program output (CUDA V2.0)
### For Pattern length m = 10, Pattern count n = 4
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/dd32aedc39d325f4aefc304172b38d549c3bcee5/RK%20CUDA2%202a.png)
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/dd32aedc39d325f4aefc304172b38d549c3bcee5/RK%20CUDA2%202b.png)

### For Pattern length m = 20, Pattern count n = 16
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/9a320f26bb5392efb5dc6030faf35f995c524359/RK%20CUDA2%201a.png)
![Colab CUDA V2.0 Screenshot](https://github.com/jmsarmiento11/csc612m-rabin-karp-CUDA/blob/9a320f26bb5392efb5dc6030faf35f995c524359/RK%20CUDA2%201b.png)
