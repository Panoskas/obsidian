CQRS (Command Query Responsibility Segregation)

**CQRS separates** reads and writes into **different databases**, Commands performs update data, Queries performs read data.

An E-Commerce platform might have high read requests for products listing but fewer writes requests for placing orders.

In **monolithic applications**, a single database typically handles both query and update operations, managing complex joins and **CRUD** tasks. As applications grow more complex, these operations can become unmanageable.

> F**or example,** a query requiring joins across more than **10 tables can lock the database due to latency**, while CRUD operations with complex validations can also cause locks.

To address this, CQRS separates read and write operations into different databases, applying the **“separation of concerns”** principle. This allows using, for instance, a NoSQL database for read operations and a relational database for writes.

Understanding the application’s behavior is crucial. If the application is **read-heavy ( _understand Read : Write ratio non functional requirement_),** the architecture should prioritize optimizing read operations.

## In an Example of E-Commerce Application:

> **Commands** should be actions with task-based operations like “add item into shopping cart” or “checkout order”. So commands can be handle with message broker systems that provide to process commands in async way.
> 
> **Queries** is never modify the database. Queries always return the JSON data with DTO objects. By this way, we can isolate the Commands and Queries.

In order isolate **Commands** and **Queries**, its best practices to separate read and write database with **2 database physically**. By this way, if our application is read-intensive that means reading more than writing, we can define custom data schema to optimized for queries.

**Materialized view pattern** is good example to implement reading databases. Because by this way we can avoid complex joins and mappings with pre defined fine-grained data for query operations.

By this **isolation**, we can even use different database for reading and writing database types like using **no-sql document database** for reading and using relational database for crud operations.

Now we can design our Ordering microservices databases

**Split 2 databases** for **Ordering** microservices  
1 for the **write** database for **relational** concerns  
2 for the **read** database for **querying** concerns

So when user create or update an order, I am going to use relational write database, and when user **query order** or order history, I am going to use no-sql read database. and make consistent them when syncing 2 databases with using message broker system with applying **publish/subscribe pattern.**

Now we can consider **tech stack** of these databases,

[**SQL Server**](https://medium.com/javarevisited/5-best-courses-to-learn-microsoft-sql-server-in-depth-e9f11b73c14a) **(** PostgreSQL / MySQL**)** for relational writing database, and using [**Cassandra**](https://medium.com/javarevisited/5-best-apache-cassandra-courses-for-beginners-and-experienced-ca37195b2fc4) for no-sql read database. Of course we will use Kafka for syncing these 2 database with pub/sub **Kafka** topic exchanges.