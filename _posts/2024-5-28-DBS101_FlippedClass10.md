---
Title: DBS101 Flipped Class 10
categories: [DBS101, Flipped_Class10]
tags: [DBS101]
---

# Transaction

In simple terms, a transaction is a group of actions that needs to be completed all at once for it to be considered successful. This is especially important in databases, where a transaction ensures that all the data changes are treated as a single unit.A transaction is delimited by statements (or function calls)
of the form begin transaction and end transaction. 

## Transaction Properties
ACID Properties:

Atomicity: Atomicity ensures that a transaction's operations are either fully completed and correctly reflected in the database, or if any part of the transaction fails, none of its operations are applied to the database at all.

Consistency: Consistency means that when a transaction is executed on its own, without any other concurrent transactions, it maintains the database's integrity and valid state.

Isolation: Isolation ensures that when multiple transactions run concurrently, each transaction is executed as if it were the only one in the system. 

Durability: Durability ensures that once a transaction is successfully completed, its changes to the database are permanent and will persist, even in the event of system failures.

A Simple Transaction Model

Create database 

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 13-51-01.png>)

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 13-51-28.png>)

Create Table

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 13-51-54.png>)

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 13-52-28.png>)

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 13-54-40.png>)

Storage Structure
- Grasping atomicity and durability in transactions necessitates an understanding of data storage and access methods in a database.
- Storage media are categorized based on speed, capacity, and resilience:

  - **Volatile storage:**
    - Does not survive system crashes.
    - Examples include main memory and cache memory.
    - Provides fast access and allows direct access to data items.

  -  Non-volatile storage:
        - Survives system crashes.
        - Examples include magnetic disks, flash storage (online storage), optical media, and magnetic tapes (archival storage).
        - Slower than volatile storage, particularly for random access.
        - Vulnerable to failures that can lead to data loss.
   -  Stable storage:
        - Information is never lost (theoretically).
        - Achieved by replicating data across multiple non-volatile storage media with independent failure modes (usually disks).
        - Updates must be made in a way that guarantees no loss of information.

Transaction Atomicity and Durability

- A transaction may abort, failing to complete successfully, but to ensure atomicity, its effects must be undone.
- The recovery scheme handles aborts, typically by maintaining a log.
- The log records each database modification, including transaction and data item identifiers, old and new values.
- Log-based recovery allows for redoing or undoing modifications to ensure both atomicity and durability.
- A committed transaction transforms the database into a new consistent state that persists despite system failures.
- Committed transactions cannot be undone by aborting; compensating transactions may be necessary to correct any issues.

1. Active:

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 14-08-44.png>)

2. Partially Committed:

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 14-10-44.png>)

3. Failed:

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 14-11-09.png>)

4. Aborted:

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 14-11-44.png>)

5. Committed:

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-20 14-12-07.png>)

If a transaction enters the failed state after the system determines that it can no longer proceed with its normal execution, it must be rolled back and enters the aborted state. At this juncture, the system has two options:

1. It can restart the transaction, but only if the transaction was aborted due to some hardware or software error not caused by the internal logic of the transaction itself. A restarted transaction is treated as a new transaction.

2. Terminate the transaction: If the transaction was aborted due to an error or violation caused by the internal logic of the transaction itself, rather than an external hardware or software error, the system should terminate the transaction instead of restarting it.

Transaction Isolation

- Transaction-processing systems commonly permit multiple transactions to execute concurrently. However, allowing multiple transactions to concurrently update data introduces several challenges regarding data consistency.
- Ensuring consistency despite concurrent transaction execution demands additional effort. It is often simpler to enforce that transactions run serially, meaning one at a time, with each transaction starting only after the previous one has completed.
- Concurrent transactions have the potential to violate the isolation property, which risks compromising database consistency despite each individual transaction being correct.
- Introducing schedules helps identify executions that guarantee isolation and maintain database consistency.
- Database systems manage the interaction of concurrent transactions through concurrency-control schemes, ensuring correct concurrent execution.

Ensuring Consistency with Serializable Schedules:

- Serializable Schedules: Ensure database consistency during concurrent execution.
- Objective: Ensure that concurrent schedules are equivalent to serial schedules.
- Importance: Concurrency-control mechanisms preserve database consistency.
- Database System Role: Ensuring that all executed schedules result in a consistent database state.

Transaction T1: Transfer $50 from account A to B
Sequential execution ensuring consistency

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-21 23-48-39.png>)

Transaction T2: Transfer 10% of balance from A to B
Sequential execution preserving database integrity

![alt text](<../images/DBS101-images/Test_Transaction/Screenshot from 2024-05-21 23-49-18.png>)


Serializability

- A schedule is considered serializable if it is equivalent to some serial schedule of the transactions.
- In simpler terms, a serializable schedule yields the same outcome as if the transactions were executed in a serial order, one after the other.
- The serializability of schedules generated by concurrently executing transactions can be ensured through various mechanisms known as concurrency-control policies.

Serializability is crucial for several reasons:

1. Ensures the isolation property of transactions: Serializability guarantees that even though transactions may execute concurrently, their effects on the database are as if they were executed sequentially, ensuring that each transaction appears to be isolated from others.

2. Concurrent execution of transactions results in a consistent state: By maintaining serializability, the database system ensures that concurrent transactions produce outcomes that are consistent with executing transactions one at a time in a serial order, thereby preserving the integrity and consistency of the database.

3. Equivalent to executing transactions one at a time in a serial order: Serializability allows for efficient concurrent execution while still providing the same result as if transactions were executed sequentially. This ensures that the database remains consistent and reliable even under heavy workload and concurrent access.