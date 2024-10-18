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