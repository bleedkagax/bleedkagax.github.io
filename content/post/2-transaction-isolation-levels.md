---
title: SQL Transaction Isolation Levels
name: 2-transaction-isolation-levels
date: 2024-10-03
draft: false
tags:
  - Mysql
share: "true"
---

# SQL Transaction Isolation Levels

Transaction isolation levels define the degree to which the operations in one transaction are visible to other concurrent transactions and the types of reads and writes that are allowed.

## Comparison Table

| Isolation Level  | Dirty Read | Non-repeatable Read | Phantom Read |
| ---------------- | ---------- | ------------------- | ------------ |
| READ UNCOMMITTED | Yes        | Yes                 | Yes          |
| READ COMMITTED   | No         | Yes                 | Yes          |
| REPEATABLE READ  | No         | No                  | Yes          |
| SERIALIZABLE     | No         | No                  | No           |

## Explanation of Isolation Levels

### 1. READ UNCOMMITTED

This is the lowest isolation level. Transactions can read data that has been modified by other transactions but not yet committed.

- Allows dirty reads, non-repeatable reads, and phantom reads
- Provides the highest level of concurrency
- Least consistent data state

### 2. READ COMMITTED

This level guarantees that any data read was committed at the moment it was read. It prevents dirty reads.

- Prevents dirty reads
- Allows non-repeatable reads and phantom reads
- Each consistent read sets and reads its own fresh snapshot

### 3. REPEATABLE READ

This level guarantees that any data read cannot change if the transaction reads it again. It prevents non-repeatable reads.

- Prevents dirty reads and non-repeatable reads
- Allows phantom reads
- All consistent reads within the same transaction read the snapshot established by the first read

### 4. SERIALIZABLE

This is the highest isolation level. Transactions are executed as if they were run sequentially.

- Prevents dirty reads, non-repeatable reads, and phantom reads
- Provides the highest level of isolation
- May significantly impact performance due to increased locking

## Phenomena Explained

- **Dirty Read:** A transaction reads data that has not yet been committed.
- **Non-repeatable Read:** A transaction reads the same row twice and gets different data each time.
- **Phantom Read:** A transaction re-executes a query returning a set of rows that satisfy a search condition and finds that the set of rows satisfying the condition has changed due to another recently-committed transaction.

## Key Points to Remember

- As you move from READ UNCOMMITTED to SERIALIZABLE, you gain more consistency and isolation but potentially sacrifice some level of concurrency and performance.
- READ UNCOMMITTED offers the highest concurrency but the least consistency.
- READ COMMITTED prevents dirty reads but still allows non-repeatable and phantom reads.
- REPEATABLE READ prevents both dirty and non-repeatable reads but still allows phantom reads.
- SERIALIZABLE provides the highest isolation, preventing all three phenomena, but may have the highest performance impact.
