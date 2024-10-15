---
title: Operating System Interview
name: 0_operating_system_interview
date: 2024-10-04
draft: false
tags:
  - OperatingSystem
share: "true"
---

## Explain the difference between a process and a thread.

- Process:
  - Independent execution unit
  - Has its own memory space
  - Heavyweight, more resources
  - Isolated from other processes

- Thread:
  - Lightweight unit of execution within a process
  - Shares memory space with other threads in the same process
  - Less resource-intensive
  - Can communicate easily with other threads in the same process

## How do processes and threads communicate

Process communication methods:
- Pipes and named pipes
- Shared memory
- Message queues
- Sockets
- Signals

Thread communication methods:
- Shared memory within the same process
- Mutex and semaphores for synchronization
- Condition variables

## Explain the concept of deadlock and its four necessary conditions.

Deadlock is a situation where a set of processes are blocked because each process is holding a resource and waiting to acquire a resource held by another process.

Four necessary conditions (Coffman conditions):
1. Mutual Exclusion: At least one resource must be held in a non-sharable mode
2. Hold and Wait: A process must be holding at least one resource while waiting to acquire additional resources held by other processes
3. No Preemption: Resources cannot be forcibly taken away from a process; they must be released voluntarily
4. Circular Wait: A circular chain of two or more processes, each waiting for a resource held by the next member in the chain

## What is the purpose of paging in an operating system?

Paging is a memory management scheme that eliminates the need for contiguous allocation of physical memory. It allows the physical address space of a process to be non-contiguous.

Benefits:
- Efficient use of memory
- Supports virtual memory
- Simplifies memory allocation

Paging Overview

```
[Logical Address Space]     [Page Table]     [Physical Address Space]
+------------------+        +----------+     +------------------+
|      Page 0      | -----> | Frame 2  | --> |     Frame 0      |
+------------------+        +----------+     +------------------+
|      Page 1      | -----> | Frame 4  | --> |     Frame 1      |
+------------------+        +----------+     +------------------+
|      Page 2      | -----> | Frame 1  | --> |     Frame 2      |
+------------------+        +----------+     +------------------+
|      Page 3      | -----> | Frame 7  | --> |     Frame 3      |
+------------------+        +----------+     +------------------+
                                             |     Frame 4      |
                                             +------------------+
                                             |     Frame 5      |
                                             +------------------+
                                             |     Frame 6      |
                                             +------------------+
                                             |     Frame 7      |
                                             +------------------+
```

Logical pages are mapped to physical frames through a page table. Note that pages can be stored in non-contiguous frames.

Address Translation

```
[Logical Address]
+----------------+----------------+
|    Page No.    |    Offset      |
+----------------+----------------+
       |                 |
       |                 |
       V                 |
 [Page Table]            |
+----------------+       |
| Frame Number   |       |
+----------------+       |
       |                 |
       |                 |
       V                 V
+----------------+----------------+
|  Frame Number  |    Offset      |
+----------------+----------------+
[Physical Address]
```

Virtual Memory with Paging

```
[Virtual Address Space]   [Physical Memory]   [Disk Storage]
+------------------+      +---------------+   +-------------+
|      Page 0      | ---> |    Frame 0    |   |   Page 3    |
+------------------+      +---------------+   +-------------+
|      Page 1      | ---> |    Frame 2    |   |   Page 5    |
+------------------+      +---------------+   +-------------+
|      Page 2      | ---> |    Frame 1    |   |   Page 6    |
+------------------+      +---------------+   +-------------+
|      Page 3      | --.  |    Frame 3    |   |    ...      |
+------------------+   |  +---------------+   +-------------+
|      Page 4      | ---> |    Frame 4    |
+------------------+      +---------------+
|      Page 5      | --.
+------------------+   |
|      Page 6      | --.
+------------------+
```

 Paging supports virtual memory. Some pages are in physical memory, while others are stored on disk and can be swapped in when needed.

## Explain the difference between preemptive and non-preemptive scheduling.

- Preemptive Scheduling:
  - The CPU can be taken away from a process before it finishes its burst time
  - Better for time-sharing systems
  - Can lead to race conditions if not properly managed

- Non-preemptive Scheduling:
  - Once the CPU has been allocated to a process, the process keeps it until it releases the CPU either by terminating or by switching to the waiting state
  - Simpler to implement
  - Can lead to poor response time for interactive processes

## What is a system call?

A system call is the programmatic way in which a computer program requests a service from the kernel of the operating system. System calls provide an essential interface between a process and the operating system.

Examples of system calls:
- File operations (open, read, write, close)
- Process control (fork, exec, exit)
- Device management
- Information maintenance
- Communication

## Explain the concept of thrashing.

Thrashing is a condition where excessive paging operations are taking place. It occurs when a computer's virtual memory subsystem is in a constant state of paging, rapidly exchanging data in memory for data on disk, to the exclusion of most application-level processing.

Causes:
- Insufficient physical memory
- Poor page replacement algorithms
- Large working sets

## What is the purpose of a semaphore?

A semaphore is a variable or abstract data type used to control access to a common resource by multiple processes in a concurrent system. It's used for process synchronization and to solve critical section problems.

Types:
- Binary Semaphore (mutex): Can have only 0 or 1 as value
- Counting Semaphore: Can have any non-negative value

## What is memory fragmentation, how does it occur, and how is it solved?

Memory fragmentation refers to the condition where memory space is broken into small, unusable blocks, reducing overall memory utilization efficiency.

How it occurs:
- External fragmentation: Frequent allocation and deallocation of memory blocks leaves small, unusable gaps between allocated blocks
- Internal fragmentation: Fixed-size memory allocation schemes may allocate more memory than required, leaving unused space within allocated blocks

Solutions:
- Compaction: Relocating allocated memory blocks to create larger contiguous free spaces
- Paging: Dividing memory into fixed-size pages, eliminating external fragmentation
- Memory pools: Pre-allocating fixed-size memory blocks for specific uses
- Garbage collection: Automatically freeing unused memory and reorganizing remaining objects

## What are virtual memory and physical memory in operating systems?

Virtual memory is an abstraction of physical memory that provides each process with the illusion of having its own large, contiguous address space.

Physical memory refers to the actual RAM(Random-access memory) installed in a computer.

Key points:
- Virtual memory allows programs to use more memory than physically available
- It maps virtual addresses to physical addresses or disk storage
- Enables memory protection between processes
- Simplifies memory management for programmers

## Explain kernel mode and user mode in operating systems

Kernel mode and user mode are privilege levels in which code executes:

Kernel mode:
- Has unrestricted access to hardware and system resources
- Can execute privileged instructions
- Used by the operating system kernel and device drivers

User mode:
- Has limited access to system resources
- Cannot execute privileged instructions directly
- Used by application programs

Switching between modes:
- System calls trigger a switch from user mode to kernel mode
- Return from system calls switches back to user mode
