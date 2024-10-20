### Design Good APIs
1. Clear naming
2. Ensure reliability (make the same call multiple times has the same effect as calling it once)
	   **idempotence**
	- POST NO
	- GET YES
	- PUT YES
	- PATCH NO
	- DELETE YES
3. Add Versioning
4. Add Pagination
5. Use clear query string for filtering and sorting API
6. Security is a top priority
7. Keep cross references simples (https://example.com/api/v1/carts/123/items/321) 
	NOT ((https://example.com/api/v1/items?card_id=123&item_id=321)
8. Rate Limiting


## SOLID
SOLID is an acronym that represents a set of five design principles for writing maintainable and scalable software. These principles were introduced by Robert C. Martin and are widely accepted in the object-oriented programming community. The SOLID principles are meant to guide developers in creating more flexible, modular, and understandable code. Here's a brief explanation of each principle:

1. **Single Responsibility Principle (SRP):**
    
    - A class should have only one reason to change, meaning it should have only one responsibility or job.
    - This principle encourages breaking down complex systems into smaller, more manageable components, with each class focused on a specific task.
2. **Open/Closed Principle (OCP):**
    
    - Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.
    - This means that you should be able to add new functionality without altering existing code. This is often achieved through the use of abstract classes, interfaces, and polymorphism.
3. **Liskov Substitution Principle (LSP):**
    
    - Subtypes must be substitutable for their base types without altering the correctness of the program.
    - In other words, if a class is a subtype of another class, it should be able to be used interchangeably with its base class without affecting the behavior of the program.
4. **Interface Segregation Principle (ISP):**
    
    - A class should not be forced to implement interfaces it does not use.
    - Instead of having large, general-purpose interfaces, it's better to have smaller, more specific ones. This helps in preventing classes from implementing methods they don't need.
5. **Dependency Inversion Principle (DIP):**
    
    - High-level modules should not depend on low-level modules. Both should depend on abstractions.
    - Abstractions should not depend on details; details should depend on abstractions.
    - This principle promotes the use of dependency injection and inversion of control to achieve a flexible and decoupled architecture.

By adhering to these SOLID principles, developers aim to create code that is more modular, maintainable, and resilient to changes, fostering good software design practices.
## Gang of Four

The "Gang of Four" patterns refer to the four authors (Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides) of the influential book "Design Patterns: Elements of Reusable Object-Oriented Software," published in 1994. This book categorized 23 design patterns into three main types: Creational, Structural, and Behavioral. Here's a brief overview of each category and the patterns they include:

### Creational Patterns
Creational patterns focus on ways to instantiate objects, ensuring that the creation process is flexible and decoupled from the specific classes that are instantiated.

1. **Abstract Factory**: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
2. **Builder**: Separates the construction of a complex object from its representation, allowing the same construction process to create different representations.
3. **Factory Method**: Defines an interface for creating an object, but lets subclasses alter the type of objects that will be created.
4. **Prototype**: Specifies the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.
5. **Singleton**: Ensures a class has only one instance and provides a global point of access to it.

### Structural Patterns
Structural patterns deal with the composition of classes or objects to form larger structures.

1. **Adapter**: Converts the interface of a class into another interface that clients expect, allowing classes to work together that couldn't otherwise because of incompatible interfaces.
2. **Bridge**: Separates an object’s interface from its implementation, allowing the two to vary independently.
3. **Composite**: Composes objects into tree structures to represent part-whole hierarchies, letting clients treat individual objects and compositions of objects uniformly.
4. **Decorator**: Adds additional responsibilities to an object dynamically.
5. **Facade**: Provides a simplified interface to a complex subsystem.
6. **Flyweight**: Uses sharing to support large numbers of fine-grained objects efficiently.
7. **Proxy**: Provides a surrogate or placeholder for another object to control access to it.

### Behavioral Patterns
Behavioral patterns are concerned with algorithms and the assignment of responsibilities between objects.

1. **Chain of Responsibility**: Passes a request along a chain of handlers, allowing multiple objects the opportunity to handle the request.
2. **Command**: Encapsulates a request as an object, thereby allowing parameterization of clients with queues, requests, and operations.
3. **Interpreter**: Given a language, defines a representation for its grammar along with an interpreter that uses the representation to interpret sentences in the language.
4. **Iterator**: Provides a way to access elements of an aggregate object sequentially without exposing its underlying representation.
5. **Mediator**: Defines an object that encapsulates how a set of objects interact, promoting loose coupling by keeping objects from referring to each other explicitly.
6. **Memento**: Captures and externalizes an object's internal state so that the object can be restored to this state later without violating encapsulation.
7. **Observer**: Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
8. **State**: Allows an object to alter its behavior when its internal state changes.
9. **Strategy**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable.
10. **Template Method**: Defines the skeleton of an algorithm in an operation, deferring some steps to subclasses.
11. **Visitor**: Represents an operation to be performed on the elements of an object structure, allowing you to define a new operation without changing the classes of the elements on which it operates.

These patterns provide solutions to common problems in software design, promoting reusable and maintainable code.
[[A Deep Dive into Common Design Patterns]]

