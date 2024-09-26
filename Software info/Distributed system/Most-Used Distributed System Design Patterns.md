
# Ambassador — Proxy

The ambassador pattern focuses on offloading all the major tasks that are critical to applications other than business logic so that applications can focus only on critical use cases.

It acts as a “go-between” for applications and the services it communicates with, offloading tasks like logging, monitoring or handling retries, and rate limiting.

For Example, K8 uses Envoy as an ambassador to simply communicate between services.

# Circuit Breaker

Imagine a water pipe breaks down the house, the first thing we should do is shut down the main valve to prevent further damage. the circuit breaker pattern works similarly preventing cascading failures in distributed systems.

When service becomes unavailable, the circuit breaker stops requests, allowing it to recover, we use circuit breaker patters to prevent further damage.

> **Closed**:  
> In this state, the circuit breaker allows normal service communication, and requests go through to the service.  
> Circuit breaker monitors the responses from the service for errors **( 4XX , 5XX HTTP Code )**. If the responses are successful **( 200 OK )** with no issues, it remains in the closed state.
> 
> **Open:**  
> When the number of failures reaches a threshold, the circuit breaker switches to the open state (**4XX , 5XX HTTP Code with some threshold count < 30** ), preventing requests from reaching the service and providing a fallback response.  
> (**Threshold Value like 30 failures within 10 seconds**)
> 
> **Half-Open:**  
> Once the timeout or reset interval passes, the circuit breaker goes to the **“Half-Open”** state.  
> It allows a limited number of test requests to pass through to the service to see if the service has **recovered or not**.  
> If the test requests succeed **( 200 OK )** , it means the service has recovered and the circuit breaker goes back to **“Closed” state**.  
> If any of the test requests fails, it means the service has still issues and the circuit breaker goes to **“Open”** state to block further requests.

**_There are several tools and frameworks implementing the circuit breaker pattern. Here are some popular options:_**

1. **Netflix Hystrix:**  
    **Hystrix** is an open-source Java library that provides an implementation of the circuit breaker pattern to handle faults tolerance and latency in distributed systems and micro services architectures.

> Note: Netflix has officially entered maintenance mode, and users are switching to use alternatives like resilience4j or Sentinel.

_Key features of Resilience4j include:_

**Retry:** It allows you to define retry strategies for failed operations, and specify how many times an operation should be retried.  
**Rate Limiter:** This allows you to control the traffic to some parts of your application by limit the rate of requests to a service to prevent overloading them.  
**Fallback:** It allows you to define fallback functions or responses when an operation fails and gracefully shut down and improve user experience.

**2. Resilience4j:**  
**Resilience4j** is a lightweight, easy-to-use library, which offers a powerful circuit breaker implementation inspired by Netflix Hystrix but designed with functional programming approach.

**3.Istio:**  
Istio is a service mesh platform that helps you manage traffic between micro services. It provides a number of features, including:

**Circuit breaker:** A fault tolerance pattern that can route traffic away from unhealthy micro services and automatically retry failed requests.

**4.Sentinel:**  
It is an open-source library that provides monitoring of services and controls the traffic.  
It can be used to implement circuit breaking, rate limiting.  
Sentinel can work in both Java and other languages.

**5.Amazon App Mesh:**  
Amazon App Mesh is a managed service mesh that allows you to monitor and control services running on AWS.  
It provides features like circuit breaking, retries, and more to enhance the reliability of your micro services.


# Sidecar Pattern

Deploys auxiliary components (sidecars) alongside the main service containers to manage cross-cutting concerns like logging, monitoring, and configuration.

The Sidecar concept in Kubernetes is becoming popular. Containers should focus on a single concern and do it well, and the Sidecar pattern supports this by separating core business logic from additional tasks.

> **This pattern involves two containers on a single node. The first is the primary application container with the core logic, and the second is the Sidecar container, which enhances the primary application by running in parallel within the same Pod. They share resources like the filesystem, disk, and network.**

The Sidecar pattern also allows deploying different components of the same application in isolated containers, which is beneficial for sharing common components across a micro service architecture, **such as logging, monitoring, and configuration properties.**

# Leader Selection

In distributed systems, some tasks need a single leader. Leader election algorithms ensure one node is designated as the leader.

In this pattern it ensure that only one node is responsible for a specific task or resource.

If Leader node Fails the remianing nodes elect a new leader. Zookeeper, etcd. use this patterns to manage distributed configurations.

By having a designated leader, we can avoid conflicts and ensure consistent decision making across the distributed system.


# Publisher/Subscriber

This pattern allows services to communicate asynchronously. Publishers send messages without knowledge of subscribers, and subscribers receive messages of interest.

For Example The publisher / subscriber pattern is like news paper delivery service, publishers emits events without knowing how many subscriber receive them, and subscriber listen for events they are interested in.

This pattern allows for better scalability and modularity , for example Google Cloud Pub/Sub enables asynchronous messaging between services, making easier to maintain and scale complex applications.

- The key to this is the fact that Pub/Sub enables the movement of messages between different components of the system without the components being aware of each other’s identity (they are decoupled).
- Pub/Sub provides a framework for exchanging messages between publishers (components that create and send messages) and subscribers (components that receive and consume messages)

> **Benefits:** Decouples message producers and consumers, improves scalability and flexibility.
> 
> **Examples:** Kafka, RabbitMQ, AWS SNS,Google Cloud Pub/Sub.


# Sharding

Divides a dataset into smaller, more manageable pieces (shards) that can be distributed across multiple databases or nodes.

[**Sharding**](https://javarevisited.substack.com/p/the-complete-guide-of-database-sharding) is like dividing a large pizza into smaller slices, making it easier to handle.

Sharding is technique for distributing data across multiple nodes in a system. It improves performance and scalability.

Each Shard contains a subset of the data, reducing the load on any single node.

Database like MongoDB and Cassandra use sharding to handle large amount of data efficiently.

Sharding can also help is achieve better data locality, reducing network latency and speeding up query execution.

There is significant differences between **sharding** and **partitioning** for your reference. We will explain these terms in detail further on.

## Partitioning

Partitioning is a general term for splitting a database along a specific axis to produce multiple smaller databases. You can partition a database:

- **vertically**: i.e., splitting the data, so the smaller databases have the duplicate rows, but different columns
- **horizontally**: i.e., splitting the data, so the smaller databases have the same columns, or the same schema, but different rows

## Sharding

Sharding is a subset of partitioning. Before we explain sharding and what makes it unique, let’s first examine how data scaling works. As your volume of data increases, you may also need to increase the storage capacity of your database. You could perform vertical scaling (add additional CPU, RAM, storage, etc.) or scale horizontally (add more nodes or machines to your server). We could also describe these choices as either scaling up or scaling out

> Types of Sharding:
> 
> **Algorithmic Sharding :** In algorithmic sharding, the client can determine a given partition’s database without any help. In dynamic sharding, a separate locator service tracks the partitions amongst the nodes.

**Dynamic Sharding:** In dynamic sharding, an external **locator service** determines the location of entries. It can be implemented in multiple ways. If the cardinality of partition keys is relatively low, the locator can be assigned per individual key. Otherwise, a single locator can address a range of partition keys.

**Entity Groups :** Store related entities in the same partition to provide additional capabilities within a single partition.

## Use cases

- E-commerce website displaying order / customer / Item information may partition or shard data by country or region, as most queries will retrieve information based on specific locations.
- a stock market analytics firm may partition data by company, or by (company, day) if it wants to perform even granular technical analysis.

> Fetch the stock price between April 2010 till December 2010, we can query Shard 1 and get the data. Additionally, each shard would store the data in a sorted order to improve the query performance. This is illustrated in the below diagram.

**Benefits:** Enhances scalability and performance.

**Challenges:** Adds complexity in query routing and managing shards.

# Bulkhead

Isolates components in a system so that a failure in one component does not cause a system-wide failure.

The Bulkhead Pattern is particularly useful in the following scenarios:

1. **Resource Isolation:** When you need to isolate resources used by consumer backend services to prevent resource contention.
2. **Critical Consumer Isolation:** To shield critical consumers (services) from standard consumers, ensuring the availability and responsiveness of critical services even during peak loads or failures.
3. **Cascading Failure Protection:** To safeguard your application from cascading failures that can occur when issues in one service affect others.

**Related Patterns:**

Bulkhead Pattern can be effectively combined with other cloud design patterns, including:

1. **Circuit Breaker Pattern:** To provide fault tolerance by preventing continuous invocations of a service experiencing issues.
2. **Retry Pattern:** For implementing retry strategies within bulkheads to gracefully handle transient failures.
3. **Throttling Pattern:** To control and limit the rate of incoming requests, preventing a bulkhead from becoming overwhelmed.

**Where we can implement bulkhead ?**

Bulkhead configuration in an API gateway allows you to specify the maximum number of concurrent requests that the API can process.

> **Bulkhead limit for an API at the API level**. Specifies the maximum concurrent request limit for an API, exceeding which the requests are rejected.
> 
> This number does not include the callbacks that an API receives. So, you can separately specify the maximum concurrent callbacks that an API can handle.
> 
> The **503 Service unavailable error code** is sent to the client service when the requests are rejected.
> 
> You can configure the required error code and status phrase using the extended settings. You can customize the required status code and message using the extended settings **pg.bulkhead.statusCode** and **pg.bulkhead.statusMessage** respectively.
> 
> **Bulkhead limit for all APIs (Global policy)**. Specifies the maximum concurrent request limit for all APIs.
> 
> Similar to the API level configuration, you can provide the maximum concurrent callbacks and your choice to retry the rejected requests.
> 
> **When you have configured global-level bulkhead limit for APIs, and if you configure a different bulkhead limit at an API-level, then the limit configured at the global level takes precedence.**
> 
> To override this, you must exclude the required APIs from the **global-policy using filters**. You can apply the required API filters when creating or editing the **bulkhead global policy**. For information about creating global policies and applying API filters
> 
> **Benefits:** Increases resilience and fault tolerance.
> 
> **Examples:** Isolating different services in a microservices architecture.\


# Cache-Aside

This pattern involves explicitly loading data into a cache from the data store and writing data to the data store through the cache.

The cache-aside pattern, also known as lazy loading, involves the application code directly interacting with the cache.

When data is requested, the application first checks the cache. If the data is found, it’s returned to the user. If not, the application retrieves the data from the primary data source, stores it in the cache, and then returns it to the user.

This pattern is suitable for scenarios where the cache contains frequently accessed data, improving response times and reducing load on the primary data source.

## Write-Through and Write-Behind Caching

Write-through caching involves writing data to both the cache and the primary data source simultaneously.

This ensures that the cache and the primary data source remain consistent but may introduce latency due to the dual-write operation.

Write-behind caching, on the other hand, writes data to the cache first and then asynchronously updates the primary data source. While write-behind caching reduces latency, it may increase the risk of data inconsistency in case of system failures or crashes.

## Read-Through and Read-Ahead Caching

Read-through caching involves reading data from the cache. If the data is not found, it’s retrieved from the primary data source, stored in the cache, and returned to the user.

This pattern is suitable for read-heavy workloads where caching frequently accessed data can improve performance.

Read-ahead caching anticipates future data access patterns and preloads data into the cache before it’s requested. This helps reduce latency by ensuring that the required data is readily available when needed.

> **Benefits:** Reduces load on the database, improves read performance.
> 
> **Examples:** Redis, Memcached.