## Basic structure of a Dotnet API 
1. Define the Data Models: Start by defining the data models that represent the entities or objects your API will work with. These models typically map to database tables or external data sources. Consider the properties and relationships between entities. You can use classes or structs to define these models.
    
2. Create the Database Context: Next, create a database context class that extends the `DbContext` class from Entity Framework Core. The database context is responsible for interacting with the database, managing connections, and performing CRUD operations. It should include a `DbSet` property for each data model.
    
3. Build the Data Access Layer: In this step, create a repository or data access layer to encapsulate the logic for accessing and manipulating data. This layer interacts with the database context and provides methods to perform CRUD operations on the data models.
    
4. Define DTOs (Data Transfer Objects): DTOs are objects used to transfer data between different layers or components of your application, such as the API and the client. Create DTOs that represent the data you want to send or receive through the API endpoints. DTOs typically contain a subset of the properties from the data models and are tailored for specific API operations.
    
5. Implement API Controllers: API controllers are responsible for handling incoming HTTP requests, processing the requests, and returning appropriate responses. Create controllers that correspond to the different resources or entities in your application. Each controller should define action methods that handle different HTTP verbs (GET, POST, PUT, DELETE) and perform the necessary operations using the data access layer.
    
6. Implement API Endpoints: Within each controller, define the individual API endpoints that represent specific operations or actions on the resources. These endpoints should be decorated with appropriate attributes, such as `[HttpGet]`, `[HttpPost]`, `[HttpPut]`, or `[HttpDelete]`, to specify the HTTP verb and route configuration.
    
7. Apply Data Validation and Error Handling: Implement data validation to ensure the data received from the client is valid and meets the required criteria. Handle validation errors and other exceptions by returning appropriate HTTP status codes and error messages.
    
8. Test and Refine: Finally, thoroughly test your API endpoints using tools like Postman or automated test frameworks. Make necessary refinements, handle edge cases, and ensure your API behaves as expected.
## Create migrations to the database

1. `add-migration` *Name of Migration*
2. `update-database`

## Repositories

##### **What is Repository?**

A repository is nothing but a class defined for an entity, with all the possible database operations. For example, a repository for an Employee entity will have the basic CRUD operations and any other possible operations related to the Employee entity.
A Repository mediates between the domain and data mapping layers, acting like an in-memory domain object collection. Client objects construct query specifications declaratively and submit them to Repository for satisfaction. Objects can be added to and removed from the Repository, as they can from a simple collection of objects, and the mapping code encapsulated by the Repository will carry out the appropriate operations behind the scenes. **Conceptually, a Repository encapsulates the set of objects persisted in a data store and the operations performed over them, providing a more object-oriented view of the persistence layer.** ==Repository also supports the objective of achieving a clean separation and one-way dependency between the domain and data mapping layers.==

## Concept flow of dotnect core app

The concept flow of a .NET Core app when you have a model, a DTO, a repository, a controller and some services is as follows:

1. **Model**: A model is a class that represents the data of your application. [It is used to interact with the database and contains properties that map to the columns of the database table](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0) [1](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0).
    
2. **DTO**: A Data Transfer Object (DTO) is an object that is used to encapsulate data and send it from one subsystem of an application to another. [DTOs are most commonly used by the Services layer in an N-Tier application to transfer data between itself and the UI layer](https://stackoverflow.com/questions/1051182/what-is-a-data-transfer-object-dto) [2](https://stackoverflow.com/questions/1051182/what-is-a-data-transfer-object-dto).
    
3. **Repository**: A repository is a class that provides an abstraction over the data access layer of your application. [It is responsible for querying the database and returning data in the form of models](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0) [1](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0).
    
4. **Controller**: A controller is a class that handles incoming HTTP requests and returns an HTTP response. [It interacts with the repository to retrieve data and returns it in the form of DTOs](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0) [1](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0).
    
5. **Services**: Services are classes that contain business logic and are responsible for performing operations on data retrieved from the repository. [They interact with the repository to retrieve data in the form of models, perform operations on it, and return it in the form of DTOs](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0) [1](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0).
    

When building an application using these components, you would typically start by creating your models first, followed by your repositories. Once you have your repositories in place, you can create your services which will interact with your repositories to perform operations on your data. [Finally, you would create your controllers which will interact with your services to handle incoming HTTP requests and return HTTP responses in the form of DTOs](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/adding-model?view=aspnetcore-7.0)

## Scopes
In .NET, especially in the context of dependency injection, "singleton," "scoped," and "transient" are three different lifetimes for registering services. These lifetimes dictate how instances of a service are created and managed by the dependency injection container.

1. **Singleton**: When a service is registered as a singleton, only one instance of that service is created and shared throughout the lifetime of the application. Every request for that service will return the same instance. This can be useful for stateless services or services that are expensive to create.
    
2. **Scoped**: Scoped services are created once per request (or once per scope). In a web application, for example, a new instance of a scoped service is created for each HTTP request, and the same instance is used throughout that request. Once the request is completed, the instance is disposed of. Scoped services are typically used for stateful services that are specific to a particular scope, such as a request in a web application.
    
3. **Transient**: Transient services are created each time they are requested. This means that a new instance is created every time the service is needed. Transient services are generally lightweight and stateless, and they are suitable for scenarios where fresh instances are required every time.
    

Here's a quick summary:

- **Singleton**: One instance throughout the application.
- **Scoped**: One instance per request (or per scope).
- **Transient**: New instance every time it's requested.

Choosing the appropriate lifetime for a service depends on its usage and requirements. For example, if a service holds state that should be unique per request, it should be scoped. If a service is stateless and can be shared across the entire application, singleton might be appropriate. If a service is lightweight and stateless but needs to be created fresh every time it's used, transient is the way to go.