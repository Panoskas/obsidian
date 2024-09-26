## Clean Architecture
- Formerly known as Onion, Hexagonal, Ports and Adapters
- Domain Centric approach
- Keeping focus on domain logic

When to Use???
- Practicing DDD
- Focus on domain not infrastructure
- Complex business logic (it is highly testatble)
- Want architecture to help enforce policies rather than relying to developers

Two Approaches to layered architecture
- Traditional N-tier : UI -> Business -> Data Access -> DB
- Clean Architecture :   UI -> Domain (business)
                     Infrastructure -> Domain(business) ->DB

Clean Architecture Rules
1. Model all business rules and entities in the Core Project (Domain)
2. All dependencies flow toward the Core Project 
3. Inner Projects define interfaces; Outer Projects implement them

#### What Belongs in the Core Project???

- Interfaces 
- Aggregates
- Entities -> everything that u store in the DB and have an Id field
- Value Objects -> Things that u compare based on their properties (datetime). Sometimes they will be properties of an entity
- Domain Services
- Domain Exceptions
- Domain Events -> If something happens someone else can know 
- Domain Handlers 
- Specifications
- Validators 
- Enums
- Custom Guards
#### What Belongs in the Use Cases Project???
- Commands
- Queries
- DTOs
- Behaviors
- Command Handlers
- Query Handlers
#### What Belongs In the Infrastructure Project
- Repos
- Api Clients
- DBContext classes
- Cached repos
- File system accessors
- azure storage accessors
- emailing implementations
- sms implementations
- system clock
#### What Belongs in the Web Project
- Api endpoints
- api models
- filters
- model binders
- tag helpers
- view models
- controllers
- views


## GRPC vs REST vs GRAPHQL
In the ever-evolving world of API architectures, it can be challenging to determine which style is the best fit for your specific needs. Two popular contenders that have gained significant traction are GraphQL and gRPC, alongside the well-established REST API. Let’s take a closer look at the advantages and disadvantages of each.

**REST API:**

REST (Representational State Transfer) is a widely adopted architectural style and protocol for designing networked applications. It leverages standard HTTP methods (GET, POST, PUT, DELETE) to manipulate resources. REST APIs offer the following advantages:

- Simplicity and ease of use
- Wide industry support and familiarity
- Statelessness, facilitating scalability
- Caching capabilities

However, REST does have some limitations, including:

- Over-fetching and under-fetching of data
- Potential for tight coupling between client and server
- Multiple round trips to fetch related resources

**GraphQL:**

GraphQL is a query language and runtime that enables clients to request exactly the data they need from the server in a single request. It offers several benefits over REST:

- Efficient data retrieval, eliminating over-fetching and under-fetching
- Strong typing and introspection for increased developer productivity
- Flexible schema evolution and versioning
- Powerful developer tools and client libraries

However, GraphQL also has some considerations:

- Learning curve and increased complexity
- Potential for over-posting of data
- Increased server processing due to complex queries

**gRPC:**

gRPC is a modern, high-performance framework for designing remote procedure call (RPC) APIs. It utilizes the Protocol Buffers data serialization format and supports multiple programming languages. The advantages of gRPC include:

- Efficient data serialization and transmission
- Strongly typed contracts for improved communication
- Built-in support for bidirectional streaming and flow control

On the other hand, gRPC has the following drawbacks:

- Increased complexity due to protocol buffers
- Limited browser compatibility
- Additional setup and configuration

So, when should you use each API architecture? Here are some general recommendations:

- Use REST if wide industry support and simplicity are crucial, and you can tolerate over-fetching and under-fetching of data.
- Choose GraphQL if your application requires flexible data retrieval, strong typing, and efficient queries at the expense of increased complexity.
- Opt for gRPC if you need high-performance communication, bidirectional streaming, and strongly typed contracts, and can handle the additional configuration complexity.

In conclusion, there is no one-size-fits-all solution when it comes to API architectures. Consider your project’s specific requirements, trade-offs, and the strengths of each approach to make an informed decision.