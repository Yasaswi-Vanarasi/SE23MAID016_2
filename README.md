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
    ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/cd16727d-b28f-4605-82fb-c1106640e47a)
   
    ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/57574f4d-b3e7-4840-96e5-a77dadc1092a)
   
    ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/4a177d3e-577a-4c8c-a100-52a54d15e7ea)

   

3. *Fine-Grain Synchronization*:
	
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/6f5bf49a-44a1-4fb3-b73a-892251e52da3)
   
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/68290b48-9e95-4a40-aff0-df42097c8591)
   
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/94fbb429-db68-4b7d-85a8-7ce2ba68e93e)


5. *Optimistic Synchronization*:
   
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/4d4136fd-822a-41fe-b3fc-ce0e1c773666)
   
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/581fb3ea-1d83-4a68-95ff-2911dcc43bd5)
   
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/e4e057e3-9b13-42fc-a045-5ebdb3c98106)


7. *Lazy Synchronization*:
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/14356cdd-6c3b-4fa3-aa50-f85187572b67)
   
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/a99fe471-ab13-4c0b-a6d2-39c56a74d4e0)
   
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/9d8ab990-6c43-43c9-bda2-df23cc13bad8)



9. *Non-blocking Synchronization*:
   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/86b0146b-bc8d-4d45-95a5-833d673df1ee)

   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/d53e4686-853a-41b5-b810-bbcdae81d7ec)

   ![image](https://github.com/Yasaswi-Vanarasi/SE23MAID016_2/assets/87477849/9557a8ce-3be5-4de4-a6f4-8be50251dc35)

## Conclusion

In this project, we explored the implementation of a concurrent double-linked list data structure with various synchronization techniques. The goal was to evaluate the performance of these techniques under different scenarios, including varying problem sizes, thread counts, and workloads.

Here are some key takeaways from our experiments:

- Coarse-grain synchronization, while easy to implement, often leads to contention, limiting concurrency and performance.

- Fine-grain synchronization provides better concurrency by allowing multiple threads to access different parts of the list simultaneously, but it can be complex to implement correctly.

- Optimistic synchronization, relying on optimistic reading and CAS operations, can offer high concurrency and performance, especially in scenarios with low contention.

- Lazy synchronization, which defers synchronization until conflicts occur, can be efficient when conflicts are infrequent but may suffer in high-contention situations.

- Non-blocking synchronization, using atomic operations and CAS, can provide non-blocking access and high concurrency but requires careful implementation.

The choice of synchronization technique should be based on the specific requirements of your application and the characteristics of your workload. It's important to balance ease of implementation with performance optimization, depending on the use case.
