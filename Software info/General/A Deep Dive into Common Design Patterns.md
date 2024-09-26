## What is a design pattern?

Design patterns are solutions to complex problems. Design patterns are all about crafting your classes and interfaces in a way that solves a particular design problem. Usually, while designing a system, we encounter some issues, and for those problems, we have a set of design patterns. Design patterns are generally templates that involve classes, interfaces, and the relationships between those classes.

## [](https://dev.to/niharikaa/design-patterns-a-deep-dive-into-common-design-patterns-31b9?ref=dailydev#types-of-design-patterns)Types of design patterns:

### [](https://dev.to/niharikaa/design-patterns-a-deep-dive-into-common-design-patterns-31b9?ref=dailydev#creational-design-patterns)Creational design patterns:

These types of patterns deal with the creation of objects in a way that is compatible with the given situation.  
At the creational level, we can determine how specific parts of our systems can be created independently or composed together, ensuring flexibility and compatibility.  
The list of design patterns that fall under this category are:

- **Singleton:** In this design pattern, we just have only one instance and that instance will be used throughout our application.

**Essentials of singleton design pattern:**

1. **private constructor:** Marking constructor as private is very crucial, as we want to ensure that only one instance of the class is created.
2. **Private Static Instance:** We use private access modifier,because we want to ensure that we only have one instance of the object in the class memory.
3. **Public Static Method (Accessor):** This is a global access point to the single instance. This method basically creates the instance if it doesn't exist else return the same instance if it already exists.

```c#
public class Singleton {
    // Private static instance of the class
    private static Singleton instance;
    private int count;

    // Private constructor to prevent instantiation
    private Singleton() {
        // initialization code
    }

    // Public static method to provide access to the instance
    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }

    // Example method
    public void getCount() {
        System.out.println("The value of count is: " + count);
    }

    public void increaseCount() {
        count++;
    }

    public void decreaseCount() {
        count--;
    }
}

public class Main {
    public static void main(String[] args) {
        // Get the single instance of Singleton
        Singleton singleton = Singleton.getInstance();
        singleton.increaseCount();
        singleton.getCount();  // Output: The value of count is: 1

        // Get the same instance of Singleton
        Singleton anotherSingleton = Singleton.getInstance();
        anotherSingleton.decreaseCount();
        anotherSingleton.getCount();  // Output: The value of count is: 0

        // Both singleton and anotherSingleton refer to the same instance
    }
}

```

- **Builder:** In the Builder pattern, we define a way to create an object step-by-step. This pattern also provides flexibility, allowing different versions of the same object to be created using the same construction process.

**Key essentials of the builder pattern:**

1. **Product:** It is the complex object that is being constructed.
2. **Builder Interface:** Defines the methods to create different parts of the Product. These methods typically return the builder object itself to allow method chaining.
3. **Concrete Builder:**Implements the Builder interface and provides specific implementations for creating parts of the Product.

**Example of builder pattern:**  
This example shows how to use the Builder Design Pattern to make a chocolate spread bread by adding ingredients step by step.

```java
// Product Class
class Bread {
    private String bread;
    private String spread;
    private String chiaSeeds;
    private String pumpkinSeeds;

    public void setBread(String bread) {
        this.bread = bread;
    }

    public void setSpread(String spread) {
        this.spread = spread;
    }

    public void setChiaSeeds(String chiaSeeds) {
        this.chiaSeeds = chiaSeeds;
    }

    public void setPumpkinSeeds(String pumpkinSeeds) {
        this.pumpkinSeeds = pumpkinSeeds;
    }

    @Override
    public String toString() {
        return "Bread with " + spread + ", topped with " + chiaSeeds + " and " + pumpkinSeeds;
    }
}

// Builder Interface
interface BreadBuilder {
    BreadBuilder addBread();
    BreadBuilder addChocolateSpread();
    BreadBuilder addChiaSeeds();
    BreadBuilder addPumpkinSeeds();
    Bread build();
}

// Concrete Builder
class ChocolateBreadBuilder implements BreadBuilder {
    private Bread bread = new Bread();

    @Override
    public BreadBuilder addBread() {
        bread.setBread("Whole grain bread");
        return this;
    }

    @Override
    public BreadBuilder addChocolateSpread() {
        bread.setSpread("Chocolate spread");
        return this;
    }

    @Override
    public BreadBuilder addChiaSeeds() {
        bread.setChiaSeeds("Chia seeds");
        return this;
    }

    @Override
    public BreadBuilder addPumpkinSeeds() {
        bread.setPumpkinSeeds("Pumpkin seeds");
        return this;
    }

    @Override
    public Bread build() {
        return bread;
    }
}

// Client Code
public class Main {
    public static void main(String[] args) {
        // Create a builder and build the chocolate spread bread
        BreadBuilder builder = new ChocolateBreadBuilder();
        Bread myBread = builder.addBread()
                               .addChocolateSpread()
                               .addChiaSeeds()
                               .addPumpkinSeeds()
                               .build();

        // Output the result
        System.out.println(myBread);
    }
}
```

- **Factory Method:** In the Factory Method pattern, we define a way to create objects, but we allow subclasses to decide the specific type of object that will be created.

**Key essentials of factory pattern:**

1. **Product Interface:** Defines the common interface for all products.
2. **Concrete Products**: Implement the Product interface.
3. **Creator:** Declares the factory method.
4. **Concrete Creators:** Implement the factory method to return different concrete products.

```java
// Product Interface
interface Juice {
    void serve();
}

// Concrete Product 1
class OrangeJuice implements Juice {
    @Override
    public void serve() {
        System.out.println("Serving Orange Juice.");
    }
}

// Concrete Product 2
class MangoJuice implements Juice {
    @Override
    public void serve() {
        System.out.println("Serving Mango Juice.");
    }
}

// Creator Abstract Class
abstract class JuiceFactory {
    // Factory method
    public abstract Juice createJuice();
}

// Concrete Creator 1
class OrangeJuiceFactory extends JuiceFactory {
    @Override
    public Juice createJuice() {
        return new OrangeJuice();
    }
}

// Concrete Creator 2
class MangoJuiceFactory extends JuiceFactory {
    @Override
    public Juice createJuice() {
        return new MangoJuice();
    }
}

// Client Code
public class Main {
    public static void main(String[] args) {
        // Create an Orange Juice using its factory
        JuiceFactory orangeJuiceFactory = new OrangeJuiceFactory();
        Juice orangeJuice = orangeJuiceFactory.createJuice();
        orangeJuice.serve();  // Output: Serving Orange Juice.

        // Create a Mango Juice using its factory
        JuiceFactory mangoJuiceFactory = new MangoJuiceFactory();
        Juice mangoJuice = mangoJuiceFactory.createJuice();
        mangoJuice.serve();  // Output: Serving Mango Juice.
    }
}
```

### Structural design patterns

This design patterns mainly focuses on how classes and objects are composed to form larger structures. They focus on the organization and relationships between objects and classes, simplifying the structure, enhancing flexibility, and promoting maintainability.

- **Adapter pattern:** In this pattern, we allow objects with incompatible interfaces to work together. It acts as a bridge between two incompatible interfaces, enabling them to communicate without altering their existing code.

**Key Essentials of the adapter pattern:**

1. **Target Interface:** It is an interface that will solve the problem (bridging the gap between the incompatible interfaces).
2. **Client:** The class or code that interacts with the target interface.
3. **Adaptee:** This is the interface which is not compatible with the current client requirements.
4. **Adapter:** Implements the target interface and contains an instance of the adaptee. It translates requests from the target interface to the adaptee’s interface, making them compatible.

```java
// Target Interface (Menu)
interface Menu {
    void orderDish(String dish);
}

// Adaptee (Chef)
class Chef {
    public void prepareDish(String dishName) {
        System.out.println("Chef is preparing " + dishName + ".");
    }
}

// Adapter (Waiter)
class Waiter implements Menu {
    private Chef chef;

    public Waiter(Chef chef) {
        this.chef = chef;
    }

    @Override
    public void orderDish(String dish) {
        chef.prepareDish(dish);
    }
}

// Client Code
public class Restaurant {
    public static void main(String[] args) {
        Chef chef = new Chef();
        Menu waiter = new Waiter(chef);

        // Customer places an order via the waiter
        waiter.orderDish("Spaghetti Carbonara");  // Output: Chef is preparing Spaghetti Carbonara.
    }
}
```

- **Facade pattern:** Simplifies the interaction with a complex system by providing a unified interface (facade). Instead of directly calling several different methods across various objects, the client interacts with the facade, which internally manages those operations.

**Key essentials of the facade design pattern:**

1. **Facade:** It is an interface that wraps all the complex subsystem interfaces and delegates the complex tasks to the subsystems that actually perform the work.
2. **Subsystem Classes:** These are the classes that acutally perform the work.

**An example of facade design pattern:**  
The example illustrates the Facade Pattern which simplifies the process of washing, drying, and pressing clothes. It hides the complexity of interacting with multiple subsystems behind a single, unified interface.

```java
// Subsystem Classes
class WashingMachine {
    public void wash() {
        System.out.println("Washing clothes.");
    }
}

class Dryer {
    public void dry() {
        System.out.println("Drying clothes.");
    }
}

class Iron {
    public void press() {
        System.out.println("Pressing clothes.");
    }
}

// Facade Class
class LaundryFacade {
    private WashingMachine washingMachine;
    private Dryer dryer;
    private Iron iron;

    public LaundryFacade(WashingMachine washingMachine, Dryer dryer, Iron iron) {
        this.washingMachine = washingMachine;
        this.dryer = dryer;
        this.iron = iron;
    }

    public void doLaundry() {
        System.out.println("Starting the laundry process...");
        washingMachine.wash();
        dryer.dry();
        iron.press();
        System.out.println("Laundry process complete.");
    }
}

// Client Code
public class Main {
    public static void main(String[] args) {
        WashingMachine washingMachine = new WashingMachine();
        Dryer dryer = new Dryer();
        Iron iron = new Iron();

        LaundryFacade laundryFacade = new LaundryFacade(washingMachine, dryer, iron);

        // Use the facade to do the laundry
        laundryFacade.doLaundry();
    }
}
```

### Behavioral design patterns

The patterns that fall under this category mainly deals with communication between objects and how they interact with each other.

- **Iterator pattern:** In the Iterator Pattern, we define a way to sequentially access elements of a collection without needing to use conventional methods, such as for loops or direct indexing. Instead, the pattern provides a standard interface (usually methods like next() and hasNext()) to traverse the collection. This approach abstracts the iteration process, allowing the client to navigate through the collection without needing to understand its internal structure or use traditional iteration methods.

#### [](https://dev.to/niharikaa/design-patterns-a-deep-dive-into-common-design-patterns-31b9?ref=dailydev#key-essentials-of-this-pattern-are)Key essentials of this pattern are:

1. **Iterator Interface:** We define all the methods such as next(), hasNext(), and currentItem().These are used to traverse the collection.
2. **Concrete Iterator:** This is the concrete implementation of the iterator interface.
3. **Aggregate Interface:** In this interface,we define methods to create iterators.All the methods returns an instance of the Iterator.
4. **Concrete Aggregate:** It's just a concrete implementation of the aggregate interface.

**Example of iterator pattern:**  
This example demostrates a simple usecase of iterators a employees object using iterator pattern.

```java
// Iterator Interface
interface Iterator {
    boolean hasNext();
    Object next();
}

// Aggregate Interface 
interface Aggregate {
    Iterator createIterator();
}

// Employee Class
class Employee {
    public String Name;
    public int Age;
    public String Department;
    public int EmployeeId;

    public Employee(String name, int age, String department, int employeeId) {
        this.Name = name;
        this.Age = age;
        this.Department = department;
        this.EmployeeId = employeeId;
    }
}

// Concrete Aggregate
class EmployeeCollection implements Aggregate {
    private Employee[] employees;

    public EmployeeCollection(Employee[] employees) {
        this.employees = employees;
    }

    @Override
    public Iterator createIterator() {
        return new EmployeeIterator(this.employees);
    }
}

// Concrete Iterator
class EmployeeIterator implements Iterator {
    private Employee[] employees;
    private int position = 0;

    public EmployeeIterator(Employee[] employees) {
        this.employees = employees;
    }

    @Override
    public boolean hasNext() {
        return position < employees.length;
    }

    @Override
    public Object next() {
        return hasNext() ? employees[position++].Name : null;
    }
}

// Client Code
public class Main {
    public static void main(String[] args) {
        // Creating employee array
        Employee[] employees = {
            new Employee("John", 28, "Engineering", 101),
            new Employee("Jane", 32, "Marketing", 102),
            new Employee("Tom", 25, "Sales", 103)
        };

        // Creating employee collection and iterator
        EmployeeCollection employeeCollection = new EmployeeCollection(employees);
        Iterator iterator = employeeCollection.createIterator();

        // Iterating through employees
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}
```

- **Strategy pattern:** In this pattern we define a family of algorithms, and at the runtime we choose the algorithm.Instead of implementing a single algorithm directly, the code receives runtime instructions on which algorithm to use from a family of algorithms. This pattern allows the algorithm to vary independently from the clients that use it.

#### [](https://dev.to/niharikaa/design-patterns-a-deep-dive-into-common-design-patterns-31b9?ref=dailydev#key-essentials-of-this-pattern-are)Key essentials of this pattern are:

1.**Strategy Interface:** Defines the common interface for all supported algorithms.  
2.**Concrete Strategies:** Implement the Strategy interface with specific algorithms.  
3.**Context:** Uses a Strategy to execute the algorithm.

**Example of strategy pattern:**  
Imagine we are building an encoding system where we may need to use different encoding algorithms depending on the situation. We will demonstrate this system using the Strategy Pattern.

```java
// Strategy Interface
interface EncoderStrategy {
    void encode(String string);
}

// Concrete Strategy for Base64 Encoding
class Base64Encoder implements EncoderStrategy {
    @Override
    public void encode(String string) {
        // Implement Base64 encoding logic here
        System.out.println("This method uses Base64 encoding algorithm for: " + string);
    }
}

// Concrete Strategy for MD5 Encoding
class MD5Encoder implements EncoderStrategy {
    @Override
    public void encode(String string) {
        // Implement MD5 encoding logic here
        System.out.println("This method uses MD5 encoding algorithm for: " + string);
    }
}

// Context Class
class EncoderContext {
    private EncoderStrategy strategy;

    public void setEncoderMethod(EncoderStrategy strategy) {
        this.strategy = strategy;
    }

    public void encode(String string) {
        strategy.encode(string);
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        EncoderContext context = new EncoderContext();

        // Use Base64 encoding method
        context.setEncoderMethod(new Base64Encoder());
        context.encode("A34937ifdsuhfweiur");

        // Use MD5 encoding method
        context.setEncoderMethod(new MD5Encoder());
        context.encode("89743297dfhksdhWOJO");
    }
}
```

**Explanation:**

1. Firstly, we define the interface for the
2. Next, we create concrete implementations of the interfaces that we have defined.
3. Finally, we use these implementations to observe how a change in the subject also updates its dependents.

- **Observer pattern:** behavioral design pattern that establishes a one-to-many dependency between objects. This means that when one object (the subject) changes its state, all its dependent objects (observers) are notified and updated automatically. This pattern is particularly useful for implementing distributed event-handling systems in event-driven software.

#### [](https://dev.to/niharikaa/design-patterns-a-deep-dive-into-common-design-patterns-31b9?ref=dailydev#key-essentials-of-this-pattern-are)Key essentials of this pattern are:

1. **Subject:** It is an object which holds the state and informs the observers when it updates it's state.
2. **Observer:** An interface or abstract class that defines the update method, which is called when the subject’s state changes.
3. **Concrete Subject:** A class that implements the Subject interface and maintains the state of interest to observers.
4. **Concrete Observer:** A class that implements the Observer interface and updates its state to match the subject’s state.

**Example of observer pattern:**  
In a stock trading application, the stock ticker acts as the subject. Whenever the price of a stock is updated, various observers—such as investors and regulatory bodies—are notified of the change. This allows them to respond to price fluctuations in real-time.

```java
import java.util.ArrayList;
import java.util.List;

// Observer interface
interface Observer {
    void update(String stockSymbol, double stockPrice);
}

// Subject interface
interface Subject {
    void register(Observer o);
    void remove(Observer o);
    void notify();
}

// Concrete Subject
class Stock implements Subject {
    private List<Observer> observers;
    private String stockSymbol;
    private double stockPrice;

    public Stock() {
        observers = new ArrayList<>();
    }

    public void setStock(String stockSymbol, double stockPrice) {
        this.stockSymbol = stockSymbol;
        this.stockPrice = stockPrice;
        notify();
    }

    @Override
    public void register(Observer o) {
        observers.add(o);
    }

    @Override
    public void remove(Observer o) {
        observers.remove(o);
    }

    @Override
    public void notify() {
        for (Observer observer : observers) {
            observer.update(stockSymbol, stockPrice);
        }
    }
}

// Concrete Observer
class StockTrader implements Observer {
    private String traderName;

    public StockTrader(String traderName) {
        this.traderName = traderName;
    }

    @Override
    public void update(String stockSymbol, double stockPrice) {
        System.out.println("Trader " + traderName + " notified. Stock: " + stockSymbol + " is now $" + stockPrice);
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Stock stock = new Stock();

        StockTrader trader1 = new StockTrader("Niharika");
        StockTrader trader2 = new StockTrader("Goulikar");

        stock.register(trader1);
        stock.register(trader2);

        stock.setStock("Niha", 9500.00);
        stock.setStock("Rika", 2800.00);
    }
}
```

**Explanation:**

- Firstly, we define the interface for the subject which is responsible for sending updates. Similarly, we also define an interface for the observer, which is responsible for receiving updates.
- Next, we create concrete implementations of the interfaces that we have defined.
- Finally, we use these implementations to observe how a change in the subject also updates its dependents.