# Concurrent Double-Linked List

## Introduction

This Java program implements a concurrent double-linked list data structure and evaluates its performance using different synchronization techniques. The program tests various problem sizes, thread counts, and workloads to measure the efficiency of the concurrent data structure.

### Synchronization Techniques

1. *Coarse-Grain Synchronization*: The entire list is locked during each operation, allowing only one thread to access the list at a time.

2. *Fine-Grain Synchronization*: Locks are applied at a more granular level, typically per-node or per-section, allowing multiple threads to access different parts of the list simultaneously.

3. *Optimistic Synchronization*: It uses a combination of optimistic reading and CAS (Compare-and-Swap) to perform operations with minimal locking.

4. *Lazy Synchronization*: Operations are initially executed without synchronization, and synchronization is applied only when conflicts are detected.

5. *Non-Blocking Synchronization*: Uses atomic operations and CAS to perform operations without traditional locks, ensuring non-blocking concurrent access.

## Workloads

Three types of workloads are defined:

1. *0C-0I-50D (Workload 1)*
   - 0% Inserts, 0% Reads, 50% Deletes
   - Simulates a workload with mostly delete operations.

2. *50C-25I-25D (Workload 2)*
   - 50% Inserts, 25% Reads, 25% Deletes
   - A mixed workload with a balanced combination of operations.

3. *100C-0I-0D (Workload 3)*
   - 100% Reads, 0% Inserts, 0% Deletes
   - Simulates a workload with only read operations.

## Execution

1. Compile the Java code:
   bash
    javac ConcurrentLinkedListTest.java
   

2. Run the tests using the following command:

   bash
    java ConcurrentLinkedListTest <problemSize> <numThreads> <workload>
   

   Example : 

   bash
    java ConcurrentLinkedListTest 2000 2 "50C-25I-25D"
   

3. The program will execute tests for various problem sizes (2 x 10^3, 2 x 10^4, 2 x 10^5), thread counts (1, 2, 4, 6, 8, 10, 12, 14, 16), and workloads (0C-0I-50D, 50C-25I-25D, 100C-0I-0D).

## Results

The program will print the following results to the console:

- Problem size, thread count, workload, execution time, and throughput for each configuration.

## Graphs of the syncronization technique(Threads vs Throughput):

1. *Coarse-Grain Synchronization*:
   
   

2. *Fine-Grain Synchronization*:
	


3. *Optimistic Synchronization*:
   


4. *Lazy Synchronization*:
   


5. *Non-blocking Synchronization*:
   
   

## Conclusion

In this project, we explored the implementation of a concurrent double-linked list data structure with various synchronization techniques. The goal was to evaluate the performance of these techniques under different scenarios, including varying problem sizes, thread counts, and workloads.

Here are some key takeaways from our experiments:

- Coarse-grain synchronization, while easy to implement, often leads to contention, limiting concurrency and performance.

- Fine-grain synchronization provides better concurrency by allowing multiple threads to access different parts of the list simultaneously, but it can be complex to implement correctly.

- Optimistic synchronization, relying on optimistic reading and CAS operations, can offer high concurrency and performance, especially in scenarios with low contention.

- Lazy synchronization, which defers synchronization until conflicts occur, can be efficient when conflicts are infrequent but may suffer in high-contention situations.

- Non-blocking synchronization, using atomic operations and CAS, can provide non-blocking access and high concurrency but requires careful implementation.

The choice of synchronization technique should be based on the specific requirements of your application and the characteristics of your workload. It's important to balance ease of implementation with performance optimization, depending on the use case.
