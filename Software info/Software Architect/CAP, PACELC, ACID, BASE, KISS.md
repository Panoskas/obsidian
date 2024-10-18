1. CAP Theorem:
The CAP theorem, also known as Brewer's theorem, states that in a distributed system, it's impossible to simultaneously guarantee all three of the following properties:

- Consistency (C): All nodes see the same data at the same time.
- Availability (A): Every request receives a response, without guarantee that it contains the most recent version of the information.
- Partition tolerance (P): The system continues to operate despite arbitrary partitioning due to network failures.

In practice, partition tolerance is necessary for distributed systems, so designers usually have to choose between consistency and availability.

2. PACELC Theorem:
PACELC is an extension of the CAP theorem that considers both network partitions and normal operation. It states:

- If there is a partition (P), a distributed system can trade off between availability (A) and consistency (C).
- Else (E), when the system is running normally in the absence of partitions, the system can trade off between latency (L) and consistency (C).

This theorem acknowledges that even when a system is running without partitions, there's still a trade-off between consistency and latency.

3. ACID Properties:
ACID is a set of properties that guarantee reliable processing of database transactions. It stands for:

- Atomicity: Each transaction is treated as a single unit, which either succeeds completely or fails completely.
- Consistency: A transaction can only bring the database from one valid state to another, maintaining database invariants.
- Isolation: Concurrent execution of transactions results in a state that would be obtained if the transactions were executed sequentially.
- Durability: Once a transaction has been committed, it will remain committed even in the case of a system failure.

ACID properties are typically associated with traditional relational databases.

4. BASE Properties:
BASE is used in systems that prioritize availability over consistency. It stands for:

- Basically Available: The system guarantees availability, in terms of the CAP theorem.
- Soft state: The state of the system may change over time, even without input.
- Eventual consistency: The system will become consistent over time, given that the system doesn't receive input during that time.

BASE is often used in large-scale distributed systems where ACID properties are difficult to implement efficiently.

5. KISS Principle

"Keep It Simple, Stupid" (KISS) is a design principle that dates back to 1960 and was first noted by the U.S. Navy. The KISS principle advocates for simplicity in design, stating that systems generally work best when they are kept simple rather than made complicated. This principle is a reminder that simplicity should be a key goal in design, and unnecessary complexity should be avoided.