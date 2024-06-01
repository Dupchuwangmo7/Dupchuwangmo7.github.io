---
Title: DBS101 Flipped Class 11
categories: [DBS101, Flipped_Class11]
tags: [DBS101]
---

# Unit 11: Concurrency Control

## Locks

A lock is a mechanism that allows transactions to gain either read or write access to data, ensuring that conflicts are prevented and data isolation is maintained. Its purpose is to coordinate access to shared resources, preventing multiple transactions from modifying the same data simultaneously, which could lead to data inconsistencies or corruption. By acquiring a lock, a transaction can safely read or modify data without interference from other concurrent transactions, thereby preserving data integrity and ensuring that each transaction operates on a consistent view of the data.

Why lock resources?

- Preventing Conflicts: Locks ensure multiple transactions don't modify the same data item simultaneously, avoiding inconsistencies.
- Mutual Exclusion: Only one transaction holds a lock for modification at a time, serializing access and preventing data corruption.
- Data Integrity: By controlling access, locks safeguard data from being left in an unexpected state due to conflicting modifications.
- Isolation Levels: Locks help enforce the desired level of isolation between concurrent transactions.

Difference Between Lock and Latch in Database

- Locks:

  - Focus: Logical data access control.
  - Scope: Granularity can vary - tables, rows, or even indexes.
  - Duration: Held for the entire transaction duration.
  - Types: Different modes like shared (read) or exclusive (write) for controlling access based on isolation level.
  - Control: Developers and applications can manage locks through transactions.
  - Purpose: Ensure data consistency across concurrent transactions by preventing conflicting modifications.

- Latches:
  - Focus: Memory management and internal synchronization.
  - Scope: Protect specific memory structures like data pages in the buffer pool.
  - Duration: Short-lived, acquired only for the specific operation on the memory structure.
  - Type: Typically offer exclusive access, ensuring data consistency within the memory area.
  - Control: Internal to the database engine, not directly controllable by developers.
  - Purpose: Maintain internal consistency of data in memory during operations like reading, writing, or flushing to disk.

Two main modes of Locks

1. Shared (S) Lock:

   - When a transaction Ti acquires a shared lock on a data item Q, it is allowed to read Q, but not modify or write to it.
   - Multiple transactions can hold shared locks on the same data item simultaneously, allowing concurrent read access.
   - A shared lock prevents any other transaction from acquiring an exclusive lock on the same data item, ensuring read consistency.

2. Exclusive (X) Lock:

   - When a transaction Ti acquires an exclusive lock on a data item Q, it is allowed to both read and write to Q.
   - Only one transaction can hold an exclusive lock on a data item at any given time, ensuring exclusive access.
   - An exclusive lock prevents any other transaction from acquiring a shared or exclusive lock on the same data item, effectively blocking all other access.

The rules governing the compatibility of lock modes are:

- Multiple shared locks are compatible with each other, allowing concurrent read access.
- An exclusive lock is incompatible with any other lock (shared or exclusive) on the same data item.
- A shared lock is compatible with other shared locks but incompatible with an exclusive lock on the same data item.

Locks are granted in databases when no other transaction holds a conflicting lock on the same data item, and there are no earlier pending lock requests for that item. This prevents starvation by considering the pending lock request queue in a fair order, such as arrival time, rather than continuously granting new compatible requests ahead of older ones. Granting locks this way ensures data integrity, prevents conflicts, and avoids indefinitely blocking transactions from acquiring necessary locks.

The two-phase locking protocol is a concurrency control method used in database systems to ensure serializability of transactions. It consists of the following two phases:

- Growing Phase:

      - During this phase, a transaction can acquire (lock) the data items it needs to access.

  It is not allowed to release (unlock) any data item during this phase.

- Shrinking Phase:

  - In this phase, the transaction can only release (unlock) the data items it has locked.
    It is not permitted to acquire any new locks on additional data items.

The key rules of the two-phase locking protocol are:

- After a transaction releases (unlocks) a data item, it can no longer acquire any new locks.
- A transaction cannot acquire a lock after it has released any lock.

Implementation of locking

1. Lock Manager Process:

   - There is a dedicated lock manager process (or component) responsible for handling lock requests, grants, and unlocks from transactions.

2. Lock Table:

   - The lock manager maintains a lock table, which is a data structure that tracks the locks held on various data items.
   - For each data item, there is a linked list of lock records, ordered by the arrival time of the lock requests.

3. Lock Request Handling:

   - When a transaction requests a lock on a data item, the lock manager adds a new lock record to the end of the linked list for that data item.
   - Lock requests are granted if they are compatible with the existing locks held on the data item and if there are no earlier pending lock requests.
   - The order of lock requests in the linked list ensures fairness and prevents starvation.

4. Unlock Handling:

   - When a transaction unlocks (releases) a data item, the lock manager removes the corresponding lock record from the linked list for that data item.
   - Removing a lock record may allow later pending lock requests in the linked list to be granted, as they may now be compatible with the remaining locks.

#### Deadlocks.

A deadlock is a cycle of transactions waiting for locks to
be released by each other.

Two ways of dealing with deadlocks:

1. Deadlock Detection:

- In this approach, the database system allows deadlocks to occur but detects their presence.
- A deadlock detection algorithm is employed to periodically check for the existence of deadlocks among the currently executing transactions.
- If a deadlock is detected, the system must resolve it by aborting (rolling back) one or more of the deadlocked transactions and allowing the remaining transactions to proceed.
- Common deadlock detection algorithms include timeout-based detection, graph-based detection (e.g., wait-for graph), and probe-based detection.

Advantage:

Deadlock detection incurs overhead due to the periodic checking process but allows more concurrency as deadlocks are resolved after they occur.

2. Deadlock Prevention:

- This approach focuses on preventing deadlocks from occurring in the first place, rather than detecting and resolving them after they happen.
- Deadlock prevention techniques impose certain restrictions or rules on how transactions can acquire locks, ensuring that at least one of the necessary conditions for deadlock cannot occur.
- Some common deadlock prevention protocols include:
  - Lock Ordering: Requiring transactions to acquire locks in a specific order to prevent circular wait conditions.
  - Wait-Die or Wound-Wait: Using transaction age or timestamp to decide whether a transaction should wait for a lock or be aborted/restarted.
  - No Preemption: Ensuring that once a transaction acquires a lock, it cannot be preempted or aborted until it completes.

Advantage:
Deadlock prevention protocols limit concurrency and throughput to some extent but provide guaranteed deadlock-free execution.

#### Lock Granularities

In database systems, lock granularity refers to the level or unit at which locks are acquired and managed. The choice of lock granularity can have a significant impact on concurrency, performance, and the potential for deadlocks. Common lock granularities include:

1. Row-level locking:

   - Locks are acquired at the level of individual rows in a table.
   - This provides the finest granularity and maximizes concurrency, as transactions can access different rows concurrently.
   - However, it can lead to increased locking overhead and potentially more deadlocks.

2. Page-level locking:

   - Locks are acquired on database pages, which contain multiple rows.
   - This granularity strikes a balance between concurrency and overhead, as transactions can access different pages concurrently.
   - It is widely used in many database systems due to its reasonable trade-off between concurrency and overhead.

3. Table-level locking:

   - Locks are acquired on entire tables.
   - This is a coarse-grained locking strategy that reduces locking overhead but limits concurrency.
   - Transactions cannot access different parts of the same table concurrently, potentially leading to reduced throughput.

4. Database-level locking:
   - Locks are acquired on the entire database.
   - This is the most coarse-grained locking strategy, providing the least concurrency but also the lowest locking overhead.
   - It is typically used in scenarios where a high level of isolation is required, or when the workload involves mostly batch operations.

The choice of lock granularity depends on various factors, such as the workload characteristics, the level of concurrency required, the acceptable overhead, and the potential for deadlocks. Finer granularities (e.g., row-level) provide higher concurrency but may introduce more overhead and deadlock potential, while coarser granularities (e.g., table-level or database-level) reduce overhead but limit concurrency.

#### Intention Locks

Intention locks are a type of lock used in database systems to support hierarchical or multi-granular locking strategies. They are used in conjunction with other lock types, such as row-level or page-level locks, to ensure consistency and avoid conflicts when locks are acquired at different granularities.

There are typically two types of intention locks:

- Intention-Shared (IS) Lock:

  - An IS lock is acquired by a transaction on a higher-level granularity (e.g., table or page) to indicate its intention to acquire shared (read) locks at a finer granularity within that higher-level granularity.
  - Multiple transactions can hold IS locks on the same higher-level granularity concurrently.

- Intention-Exclusive (IX) Lock:

  - An IX lock is acquired by a transaction on a higher-level granularity (e.g., table or page) to indicate its intention to acquire exclusive (write) locks at a finer granularity within that higher-level granularity.
  - Only one transaction can hold an IX lock on a higher-level granularity at a time


Locking in Practice

![alt text](<../images/DBS101-images/lock_demo/Screenshot from 2024-06-02 01-14-07.png>)

![alt text](<../images/DBS101-images/lock_demo/Screenshot from 2024-06-02 01-16-23.png>)

![alt text](<../images/DBS101-images/lock_demo/Screenshot from 2024-06-02 01-18-01.png>)


SHARE Mode :  Allows read and schema modification
operations but not data modification operations within
the same transaction.

![alt text](<../images/DBS101-images/lock_demo/Screenshot from 2024-06-02 01-19-41.png>)

EXCLUSIVE Mode: Allows full access (read, write,
delete) to the table, blocking all other transactions.

![alt text](<../images/DBS101-images/lock_demo/Screenshot from 2024-06-02 01-20-54.png>)

FOR UPDATE: Acquires an exclusive lock on the selected
rows, allowing modifications on those rows.

![alt text](<../images/DBS101-images/lock_demo/Screenshot from 2024-06-02 01-21-59.png>)


FOR SHARE: Acquires a shared lock on the selected rows,
preventing other transactions from acquiring exclusive
locks but allows updates within the same transaction.

![alt text](<../images/DBS101-images/lock_demo/Screenshot from 2024-06-02 01-24-06.png>)


## Concurrency Control Approaches

There are several approaches used for concurrency control in database systems to ensure the isolation property of transactions and maintain data integrity and consistency in the presence of concurrent access. The main concurrency control approaches are:

1. Lock-Based Concurrency Control:
   - This approach involves the use of locks to regulate access to shared data items.
   - Transactions acquire locks on data items before accessing them, preventing conflicting operations from other transactions.
   - Common locking protocols include Two-Phase Locking (2PL), which enforces a growing and shrinking phase for lock acquisition and release.
   - Variations like multigranular locking and intention locks are used to balance concurrency and overhead.

2. Timestamp-Based Concurrency Control:
   - In this approach, each transaction is assigned a unique timestamp upon its arrival.
   - Conflicts between transactions are resolved based on their timestamps, following either a "wait-die" or "wound-wait" strategy.
   - Transactions with older timestamps are typically given priority over newer transactions in case of conflicts.

3. Optimistic Concurrency Control:
   - This approach assumes that conflicts among transactions are rare and allows transactions to execute without initially acquiring locks.
   - Transactions perform their operations on a private copy of the data.
   - Before committing, a validation phase checks for conflicts with other concurrent transactions.
   - If conflicts are detected, the transaction is aborted and rolled back; otherwise, it can commit its changes.

4. Multi-Version Concurrency Control (MVCC):
   - This approach maintains multiple versions of data items, allowing transactions to access a consistent snapshot of the data.
   - Transactions can read older versions of data without being blocked by writers.
   - Writers create new versions of data items without overwriting the versions being read by other transactions.
   - MVCC is particularly useful in read-intensive workloads and can provide higher concurrency than locking-based approaches.

The choice of concurrency control approach depends on various factors, such as the workload characteristics (read-intensive or write-intensive), the level of concurrency required, the acceptable overhead, and the database system's specific requirements and constraints. Some database systems may combine multiple approaches or employ hybrid strategies to optimize concurrency and performance.

## Snapshot Isolation(SI)

Snapshot Isolation (SI) is a concurrency control technique used in database systems that provides a consistent view of the data to each transaction while avoiding certain types of anomalies and reducing the need for locking.

In Snapshot Isolation, each transaction operates on a consistent snapshot of the database, which is a point-in-time view of the data as it existed at the start of the transaction. This snapshot is created by the database management system (DBMS) and is maintained throughout the transaction's execution.

Here's how Snapshot Isolation works:

1. Transaction Start:
   - When a transaction begins, the DBMS creates a snapshot of the committed data in the database at that point in time.
   - This snapshot includes all data modifications made by transactions that committed before the start of the new transaction.

2. Read Operations:
   - Throughout the transaction, all read operations are performed on the initial snapshot created at the start of the transaction.
   - This ensures that the transaction sees a consistent view of the data, regardless of any concurrent updates made by other transactions.

3. Write Operations:
   - When a transaction needs to modify data (insert, update, or delete), it does so on a temporary copy of the data, separate from the snapshot.
   - These modifications are initially invisible to other transactions.

4. Validation and Commit:
   - Before a transaction can commit, the DBMS validates that no other committed transaction has modified the data that the current transaction intended to change.
   - If the validation succeeds, the transaction's modifications are applied to the database, and the changes become visible to other transactions.
   - If the validation fails due to a conflict, the transaction is typically aborted and rolled back.

Snapshot Isolation provides several benefits:

1. Consistent Reads: Transactions always see a consistent snapshot of the data, eliminating the need for most locking and avoiding certain types of anomalies, such as dirty reads and non-repeatable reads.

2. Reduced Locking Overhead: Since transactions operate on snapshots, the need for locking is reduced, potentially improving concurrency and performance.

3. Avoidance of Certain Anomalies: Snapshot Isolation avoids dirty reads, non-repeatable reads, and lost update anomalies.

However, Snapshot Isolation does not prevent write skew anomalies, where two transactions read the same data and make updates based on their initial reads, leading to an inconsistent state.

Snapshot Isolation is widely used in modern database systems, such as Microsoft SQL Server, Oracle, and PostgreSQL. It strikes a balance between providing a high level of consistency and avoiding excessive locking overhead, making it suitable for many applications that require high concurrency and read-intensive workloads.

## Advanced Concurrency Control Techniques

Advanced concurrency control techniques in database systems aim to improve performance, scalability, and concurrency while ensuring data consistency and integrity. Here are some notable advanced concurrency control techniques:

1. Multiversion Concurrency Control with Snapshot Isolation (MVCC-SI):
   - This technique combines the benefits of Multi-Version Concurrency Control (MVCC) and Snapshot Isolation (SI).
   - Transactions operate on a consistent snapshot of the database, similar to SI, but without the need for validation at commit time.
   - MVCC-SI avoids the write skew anomaly associated with SI by tracking and managing write-write conflicts.

2. Optimistic Concurrency Control (OCC):
   - OCC is an optimistic approach where transactions are allowed to execute without acquiring locks initially.
   - Transactions perform their operations on a private copy of the data.
   - Before committing, a validation phase checks for conflicts with other concurrent transactions.
   - If no conflicts are detected, the transaction can commit its changes; otherwise, it is aborted and rolled back.

3. Partition-Based Concurrency Control:
   - This technique partitions or divides the database into multiple partitions or sub-databases.
   - Concurrency control is applied independently within each partition, reducing contention and improving scalability.
   - Transactions that access data across multiple partitions may require additional coordination or distributed concurrency control mechanisms.

4. Logical Concurrency Control:
   - This approach focuses on controlling concurrency at a logical or semantic level, rather than at the physical data level.
   - Transactions are allowed to execute concurrently as long as their operations are semantically correct and maintain application-level consistency.
   - Logical concurrency control is often used in specific domains or application contexts, such as software configuration management or document editing.

5. Timestamp-Based Concurrency Control with Serialization Graph Testing (SGT):
   - This technique combines timestamp ordering with serialization graph testing to detect and resolve conflicts.
   - Transactions are assigned timestamps, and conflicts are detected by building and analyzing a serialization graph.
   - If the graph indicates a potential cycle (serialization violation), one or more transactions are aborted to resolve the conflict.


These advanced concurrency control techniques aim to improve performance, scalability, and concurrency while maintaining data consistency and integrity. The choice of technique depends on factors such as the workload characteristics, the desired level of consistency, the system's performance requirements, and the trade-offs between concurrency, overhead, and complexity.