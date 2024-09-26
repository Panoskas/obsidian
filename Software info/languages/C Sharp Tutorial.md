
## Print Hello World

```csharp
using System;

namespace HelloWorld
{
  class Program
  {
    static void Main(string[] args)
    {
      Console.WriteLine("Hello World!");    
    }
  }
}
```

**Line 1:** `using System` means that we can use classes from the `System` namespace.

**Line 2:** A blank line. C# ignores white space. However, multiple lines makes the code more readable.

**Line 3:** `namespace` is used to organize your code, and it is a container for classes and other namespaces.

**Line 4:** The curly braces `{}` marks the beginning and the end of a block of code.

**Line 5:** `class` is a container for data and methods, which brings functionality to your program. Every line of code that runs in C# must be inside a class. In our example, we named the class Program.

**Line 7:** Another thing that always appear in a C# program, is the `Main` method. Any code inside its curly brackets `{}` will be executed. You don't have to understand the keywords before and after Main. You will get to know them bit by bit while reading this tutorial.

**Line 9:** `Console` is a class of the `System` namespace, which has a `WriteLine()` method that is used to output/print text. In our example it will output "Hello World!".

## Variables

In C#, there are different **types** of variables (defined with different keywords), for example:

- `int` - stores integers (whole numbers), without decimals, such as 123 or -123
- `double` - stores floating point numbers, with decimals, such as 19.99 or -19.99
- `char` - stores single characters, such as 'a' or 'B'. Char values are surrounded by single quotes
- `string` - stores text, such as "Hello World". String values are surrounded by double quotes
- `bool` - stores values with two states: true or false
**You must initialize a variable before it can be used 
```csharp
bool flag = true;
int value = 0;

if (flag)
{
    value = 10;
    Console.WriteLine("Inside of code block: " + value);
}
Console.WriteLine("Outside of code block: " + value);
```

## Reference data type vs value  data type
Value Types:

- Value types store the actual data values themselves.
- They are typically stored on the stack (for local variables) or inline within an object's memory allocation (for fields in objects).
- When you copy a value type variable to another variable or pass it as an argument to a method, a new copy of the data is created.
- Changes to one variable do not affect other variables that hold the same value type.

Example value types in C# include:

- `int`
- `float`
- `double`
- `char`
- `enum`
- `struct`

Reference Types:

- Reference types store references (pointers) to the memory location where the data is stored.
- They are typically stored on the heap, which allows for dynamic memory allocation.
- When you copy a reference type variable to another variable or pass it as an argument to a method, you're copying the reference, not the actual data. Both variables will point to the same data in memory.
- Changes made to one variable can affect other variables that reference the same object.

Example reference types in C# include:

- `string`
- `object`
- `Arrays
- `Classes
- `Delegates
- `Interfaces

In C#, a delegate is a type that represents a reference to a method. It allows you to treat methods as first-class objects, which means you can pass methods as parameters to other methods, store them in variables, and invoke them dynamically. Delegates are often used to implement callbacks, event handling, and to achieve loose coupling in software design.
## Access modifiers

- `private`: It is an access modifier that restricts the visibility of a member to within the same class. Private members can only be accessed by other members of the same class and are not accessible from outside the class.
- `static`: It is a modifier that indicates that the member belongs to the type itself rather than to an instance of the type. Static members are shared among all instances of the class and can be accessed directly using the class name without creating an instance of the class.
- `public`: Makes the member accessible from any code that can access the containing type.
- `protected`: Allows access to the member within the containing type and its derived types.
- `internal`: Makes the member accessible within the same assembly (project).
- `abstract`: Specifies that a class or a member is incomplete and must be implemented in derived classes.
- `sealed`: Prevents inheritance of a class or overrides of virtual methods.
- `virtual`: Allows a method or property to be overridden in derived classes.
- `override`: Specifies that a method overrides a virtual or abstract method in the base class.
- `readonly`: Specifies that a field can only be assigned a value during initialization or in a constructor and cannot be modified afterward.
- `const`: Defines a constant value that cannot be changed.

## Dependency injection

`Giving an object its instance variables`

Like a computer in order to run u need a GPU, CPU, Ram, Hard drive. So these are its dependencies components. 

Dependency injection is a software design pattern used in object-oriented programming to implement inversion of control (IoC). It allows objects to define their dependencies through constructor parameters or properties, rather than creating or looking up the dependencies themselves. Instead, the dependencies are provided (injected) from the outside, typically by a framework or container.

Here's a simplified explanation of how dependency injection works:

1. Define Dependencies: Identify the dependencies that a class requires to perform its tasks. Dependencies can be other classes, services, data repositories, or any other external resources.
    
2. Configure Dependency Injection Container: Set up a dependency injection container or framework, such as the built-in container in ASP.NET Core or popular third-party containers like Autofac, Unity, or Ninject. The container manages the lifecycle and resolution of dependencies.
    
3. Register Dependencies: Register the dependencies with the container, specifying how they should be created and resolved. This is typically done during the application startup or configuration phase. For example, you might register a specific implementation of an interface to be used when injecting that interface.
    
4. Inject Dependencies: In the classes that require dependencies, define constructor parameters or properties to receive the dependencies. The container will automatically resolve and inject the dependencies when creating instances of the class.
    
5. Resolve Dependencies: When an instance of a class is requested (e.g., by calling a controller method in an MVC application), the dependency injection container resolves the dependencies and provides them to the class.

## Tasks

Tasks, represent asynchronous operations in C#. They are used to execute code concurrently and allow for non-blocking execution. Tasks are typically used when performing operations that may take some time to complete, such as network requests, file I/O, or CPU-intensive computations. By using tasks, you can initiate an operation and continue executing other code while waiting for the task to complete.

Here's an example of a method that returns a `Task`:

```csharp
public async Task<string> DownloadDataAsync(string url)
{
    // Perform asynchronous operations, e.g., download data from a URL
    // Simulating a delay using Task.Delay
    await Task.Delay(2000); // Pauses the method for 2 seconds asynchronously
    
    // Return the downloaded data as a string
    return "Downloaded data";
}

```

In this example, the `DownloadDataAsync` method is declared with a return type of `Task<string>`, indicating that it returns a `Task` that will eventually produce a string result. The `await` keyword is used to asynchronously pause the method and await the completion of the `Task.Delay` operation.

You can later use the `await` keyword when calling this method to asynchronously wait for the task to complete and retrieve the result:

```csharp
string data = await DownloadDataAsync("https://example.com");
// Use the downloaded data

```

The `await` keyword allows the calling code to continue executing other tasks or respond to user input while waiting for the `DownloadDataAsync` task to finish.

## Methods

Methods are fundamental building blocks in C#. They are blocks of code that perform a specific action or a set of actions when called. Methods encapsulate a series of instructions that can be executed multiple times within a program. Methods can have parameters (inputs) and return values (outputs), which allow for flexible and reusable code. Methods can be defined within classes and called by their name followed by parentheses.

## The `this ` keyword

The `this` keyword is used as a modifier on the first parameter of the method `Copy`. This indicates that this method is an extension method, which means it extends the functionality of the `Collection` class.

By using `this Collection collection`, the extension method `Copy` becomes accessible on instances of the `Collection` class. It allows you to call the method directly on a `Collection` object, similar to an instance method.

For example, assuming you have a `Collection` object named `myCollection` and a `CollectionDTO` object named `myCollectionDTO`, you can call the extension method like this:
```csharp
myCollection.Copy(myCollectionDTO);
```
The `this` keyword in the method declaration indicates that the method operates on an instance of the `Collection` class, and within the method body, you can directly access the properties and methods of the `collection` object.
Note that extension methods must be defined in a static class, and the namespace containing the class where the extension method is defined must be imported to use the extension methods in your code.

## Must Know built-in functions

In C#, there are many built-in functions and methods that you can use to perform common operations on various data types. Here are some basic functions that you should be aware of and what they do:

1. **Contains**:
   - **Purpose**: Determines whether a collection (e.g., a string, list, array) contains a specific element.
   - **Usage**: `collection.Contains(element)`

2. **Substring**:
   - **Purpose**: Extracts a portion of a string.
   - **Usage**: `string.Substring(startIndex, length)` or `string.Substring(startIndex)` where `startIndex` is the starting position of the substring and `length` is optional.

3. **Length**:
   - **Purpose**: Returns the number of elements in a collection (e.g., string length, array length).
   - **Usage**: `collection.Length` or `collection.Count` for some collections like lists.

4. **IndexOf**:
   - **Purpose**: Returns the index of the first occurrence of a specified element in a collection (e.g., a string).
   - **Usage**: `collection.IndexOf(element)`.

5. **ToUpper** and **ToLower**:
   - **Purpose**: Converts a string to uppercase or lowercase, respectively.
   - **Usage**: `string.ToUpper()` and `string.ToLower()`.

6. **Replace**:
   - **Purpose**: Replaces all occurrences of a specified substring with another substring in a string.
   - **Usage**: `string.Replace(oldValue, newValue)`.

7. **Split**:
   - **Purpose**: Splits a string into an array of substrings based on a delimiter.
   - **Usage**: `string.Split(delimiters)`.

8. **Concatenate** (for strings):
   - **Purpose**: Combines multiple strings into one.
   - **Usage**: You can use the `+` operator or `string.Concat()` method.

9. **Parse** and **TryParse** (for converting strings to other data types):
   - **Purpose**: Converts a string representation of a value to its equivalent data type.
   - **Usage**: `DataType.Parse(stringValue)` or `DataType.TryParse(stringValue, out result)`.

10. **Math Functions** (e.g., `Math.Max`, `Math.Min`, `Math.Round`):
    - **Purpose**: Perform common mathematical operations.
    - **Usage**: These are static methods in the `System.Math` class.

11. **DateTime Functions** (e.g., `DateTime.Now`, `DateTime.Parse`, `DateTime.AddDays`):
    - **Purpose**: Manipulate and work with date and time values.
    - **Usage**: DateTime methods are part of the `System.DateTime` struct.

12. **Enumerable Functions** (e.g., `Where`, `Select`, `OrderBy`, `GroupBy`):
    - **Purpose**: Perform operations on collections using LINQ (Language Integrated Query).
    - **Usage**: LINQ methods allow you to query and transform collections.

13. **String.Format** and **string interpolation**:
    - **Purpose**: Format strings with placeholders for variable values.
    - **Usage**: `string.Format(format, arg0, arg1, ...)` or string interpolation like ` $"{variable1} is {variable2}"`.

These are just a few of the basic functions available in C#. The .NET framework provides a rich set of libraries and methods for various tasks, and you can also create your own custom functions as needed.

## Declaration

This combines the declaration and initialization of the `_context` field into a single line. The field is declared as `private readonly` and immediately initialized with a new instance of the `EmployeeDBContext` class using the default constructor.
```csharp
private readonly EmployeeDBContext _context = new EmployeeDBContext();
```

## Angle brackets

In .NET, the angle brackets `<>` are used to denote generic type parameters. Generics allow you to define classes, methods, interfaces, and other constructs that can work with different types without specifying the actual type until they are used or instantiated.

## Type Casting

1. **Implicit Casting (Widening Conversion):** This type of casting is done automatically by the compiler when there is no risk of losing information or precision. For example, casting an `int` to a `long`:
```csharp
int number = 10; long bigNumber = number; // Implicit casting from int to long

```

2. **Explicit Casting (Narrowing Conversion):** This type of casting requires an explicit cast operator. It is used when there is a potential loss of information or precision in the conversion. For example, casting a `double` to an `int`:
```csharp
double decimalNumber = 3.14; int integerNumber = (int)decimalNumber; 
// Explicit casting from double to int
```
Casting can also be used with reference types, where it involves converting between different classes or interfaces. In such cases, explicit casting is required, and you can use the `as` or `(type)` syntax to perform the cast.
```csharp
// Casting with reference types
ParentClass parent = new ChildClass();
ChildClass child = (ChildClass)parent; // Explicit casting from ParentClass to ChildClass
```



## TryParse Method
The TryParse() method does several things simultaneously:

- It attempts to parse a string into the given numeric data type.
- If successful, it stores the converted value in an **out parameter**, explained in following section.
- It returns a `bool` to indicate whether the action succeeded or failed.
```csharp
string value = "102";
int result = 0;
if (int.TryParse(value, out result))
{
    Console.WriteLine($"Measurement: {result}");
}
else
{
    Console.WriteLine("Unable to report the measurement.");
}
```
result:`Measurement: 102

## Array Methods

1. **Access Elements:**
    
    - `array[index]`: Access an element at a specific index.
2. **Modify Elements:**
    
    - `array[index] = value`: Modify an element at a specific index.
3. **Get Array Length:**
    
    - `array.Length`: Get the number of elements in the array.
4. **Iteration:**
    
    - `foreach`: Iterate through all elements in the array.
5. **Searching:**
    
    - `Array.IndexOf(array, value)`: Find the index of the first occurrence of a value.
    - `Array.LastIndexOf(array, value)`: Find the index of the last occurrence of a value.
    - `Array.Find(array, predicate)`: Find the first element that matches a condition.
    - `Array.FindIndex(array, predicate)`: Find the index of the first element that matches a condition.
6. **Sorting and Reversing:**
    
    - `Array.Sort(array)`: Sort the elements in ascending order.
    - `Array.Reverse(array)`: Reverse the order of elements.
    - The `Array.Clear()` method allows you to remove the contents of specific elements in your array, and the `Array.Resize()` method adds or removes elements from your array
    `Array.Clear(pallets, 0, 2);`.    
    Here you're using the `Array.Clear()` method to clear the values stored in the elements of the `pallets` array starting at index `0` and clearing `2` elements.
```csharp
string[] pallets = { "B14", "A11", "B12", "A13" };
Console.WriteLine("");

Array.Clear(pallets, 0, 2);
Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

Console.WriteLine("");
Array.Resize(ref pallets, 6);
Console.WriteLine($"Resizing 6 ... count: {pallets.Length}");

pallets[4] = "C01";
pallets[5] = "C02";

foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```
Here, you're calling the `Resize()` method passing in the `pallets` array by reference, using the `ref` keyword. In some cases, methods require you pass arguments by value (the default) or by reference (using the ref keyword). The reasons why this is necessary requires a long and complicated explanation about of how objects are managed in .NET. Unfortunately, that is beyond the scope of this module. When in doubt, you're recommended to look at Intellisense or Microsoft Docs for examples on how to properly call a given method.

In this case, you're resizing the `pallets` array from four elements to `6`. The new elements are added at the end of the current elements. The two new elements will be null until you assign a value to them.
7. **Copying and Cloning:**
    
    - `Array.Copy(sourceArray, destinationArray, length)`: Copy elements from one array to another.
    - `array.Clone()`: Create a shallow copy of the array.
8. **Resizing:**
    
    - Arrays in most languages have a fixed size, so they cannot be resized directly. You would typically create a new array with the desired size and copy elements if you need to "resize" an array.
9. **Manipulating Elements:**
    
    - `Array.Resize(ref array, newSize)`: Change the size of the array (C# specific, may involve copying elements).
10. **Checking for Existence:**
    
    - `Array.Exists(array, predicate)`: Check if any element satisfies a condition.
    - `Array.Contains(array, value)`: Check if a specific value exists in the array.
11. **Filling Arrays:**
    
    - `Array.Fill(array, value)`: Fill the entire array with a specific value (C# specific).
12. **Concatenation:**
    
    - You can concatenate arrays by creating a new array and copying elements from the source arrays.
13. **Conversion:**
    
    - Converting an array to a different data structure (e.g., List, Set) typically requires manual iteration and copying.

## Built-in methods

- `Math.Abs()`—will find the absolute value of a number. Example: `Math.Abs(-5)` returns 5.
- `Math.Sqrt()`—will find the square root of a number. Example: `Math.Sqrt(16)` returns 4.
- `Math.Floor()`—will round the given double or decimal down to the nearest whole number. Example: `Math.Floor(8.65)` returns 8.
- `Math.Min()`—returns the smaller of two numbers. Example: `Math.Min(39, 12)` returns 12.

## Ternary Operators

The _ternary operator_ allows for a compact syntax in the case of binary decisions. Like an `if...else` statement, it evaluates a single condition and executes one expression if the condition is true and the second expression otherwise.

Here’s an example of a ternary operator in action:

```csharp
string color = "blue";
string result = (color == "blue") ? "blue" : "NOT blue"; 
Console.WriteLine(result);
```

In this example, we create a variable `result` and save the outcome of the ternary operator expression. The expression starts with the Boolean expressions `(color == "blue")`, followed by the ternary operator `?`, then the two possible outcomes, separated by a colon `:`. The first outcome, `"blue"` will be saved to `result` if the Boolean expression evaluates to `true`, otherwise it will store the second outcome.


## Constants

If you don't want others (or yourself) to overwrite existing values, you can add the `const` keyword in front of the variable type.

This will declare the variable as "constant", which means unchangeable and read-only:

```csharp
const int myNum = 15;
myNum = 20; // error
```


## Lambda expressions and anonymous functions

You use a _lambda expression_ to create an anonymous function. Use the [lambda declaration operator `=>`](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-operator) to separate the lambda's parameter list from its body. A lambda expression can be of any of the following two forms:
```csharp
(input-parameters) => expression
```

```csharp
(input-parameters) => { <sequence-of-statements> }
```

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

// Filter out even numbers using a lambda expression
List<int> evenNumbers = numbers.Where(num => num % 2 == 0).ToList();

```

## Get user input

You have already learned that `Console.WriteLine()` is used to output (print) values. Now we will use `Console.ReadLine()` to get user input.

In the following example, the user can input his or hers username, which is stored in the variable `userName`. Then we print the value of `userName`:

```csharp
// Type your username and press enter
Console.WriteLine("Enter username:");

// Create a string variable and get user input from the keyboard and store it in the variable
string userName = Console.ReadLine();

// Print the value of the variable (userName), which will display the input value
Console.WriteLine("Username is: " + userName);
```

The `Console.ReadLine()` method returns a `string`. Therefore, you cannot get information from another data type, such as `int`.

```csharp
Console.WriteLine("Enter your age:");
int age = Convert.ToInt32(Console.ReadLine());
Console.WriteLine("Your age is: " + age);
```

## Operators

|   |   |   |   |
|---|---|---|---|
|+|Addition|Adds together two values|x + y|
|   |   |   |   |
|---|---|---|---|
|-|Subtraction|Subtracts one value from another|x - y|
|   |   |   |   |
|---|---|---|---|
|*|Multiplication|Multiplies two values|x * y|
|   |   |   |   |
|---|---|---|---|
|/|Division|Divides one value by another|x / y|
|   |   |   |   |
|---|---|---|---|
|%|Modulus|Returns the division remainder|x % y|
|   |   |   |   |
|---|---|---|---|
|++|Increment|Increases the value of a variable by 1|x++|
|   |   |   |   |
|---|---|---|---|
|--|Decrement|Decreases the value of a variable by 1|x--|


## Interpolation

```csharp
string firstName = "John";
string lastName = "Doe";
string name = $"My full name is: {firstName} {lastName}";
Console.WriteLine(name);
```

## Access Strings

```csharp
string myString = "Hello";
Console.WriteLine(myString[0]);  // Outputs "H"
```

## Escape Characters


|  |    |
|----------|----------|
| \n   | New Line 
| \t    | Tab 
| \b    | Backspace 
| \'    | Single Quote 
| \"    | Double Quote 
| \\    | Backslash


## Short Hand If ... Else

```csharp
variable = (condition) ? expressionTrue :  expressionFalse;
```

```csharp
int time = 20;
string result = (time < 18) ? "Good day." : "Good evening.";
Console.WriteLine(result);
```

**instead of 

```csharp
int time = 20;
if (time < 18) 
{
  Console.WriteLine("Good day.");
} 
else 
{
  Console.WriteLine("Good evening.");
}
```

## Switch Case

he `switch` statement chooses one section of code to execute from a list of possible switch sections. The selected _switch section_ is chosen based on a pattern match with the statement's match expression.

Consider the following code sample that shows the basic structure of `switch` statement:

```csharp
switch (fruit)
{
    case "apple":
    case "tomato"
		Console.WriteLine($"App will display information for apple and tomato that are the same .");
        break;

    case "banana":
        Console.WriteLine($"App will display information for banana.");
        break;

    case "cherry":
        Console.WriteLine($"App will display information for cherry.");
        break;
    default:
	    Console.WriteLine("default fruit");
	    break;
}
```
he match expression (which may also be referred to as the _switch expression_) is the value following the `switch` keyword, in this case `(fruit)`. Each _switch section_ is defined by a _case pattern_. Case patterns are constructed using the keyword `case` followed by a value. The first case pattern in this example is: `case "apple":`. Case patterns are Boolean expressions that evaluate to either `true` or `false`. Each switch section includes a small number of code lines that will be executed if the case pattern is a match for the match expression. In this example, if `fruit` is assigned a value of "apple", the first case pattern will evaluate as `true` and that switch section will be executed.
## Foreach Loop

There is also a `foreach` loop, which is used exclusively to loop through elements in an **array**:
```csharp
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
foreach (string i in cars) 
{
  Console.WriteLine(i);
}
```


## 2D Arrays

```csharp
int[,] numbers = { {1, 4, 2}, {3, 6, 8} };
```

|  |    |
|----------|----------|----------|
| 1   | 4 | 2
| 3    | 6 | 8

## Methods


A **method** is a block of code which only runs when it is called.

You can pass data, known as parameters, into a method.

Methods are used to perform certain actions, and they are also known as **functions**.

Why use methods? To reuse code: define the code once, and use it many times.

```csharp
class Program
{
  static void MyMethod() 
  {
    // code to be executed
  }
}
```

- `MyMethod()` is the name of the method
- `static` means that the method belongs to the Program class and not an object of the Program class. You will learn more about objects and how to access methods through objects later in this tutorial.
- `void` means that this method does not have a return value. You will learn more about return values later in this chapter

### Parameters and Arguments

```csharp
static void MyMethod(string fname) 
{
  Console.WriteLine(fname + " Refsnes");
}

static void Main(string[] args)
{
  MyMethod("Liam");
  MyMethod("Jenny");
  MyMethod("Anja");
}

// Liam Refsnes
// Jenny Refsnes
// Anja Refsnes
```

## Classes and Objects

So, a class is a template for objects, and an object is an instance of a class.

Everything in C# is associated with classes and objects, along with its attributes and methods. For example: in real life, a car is an object. The car has **attributes**, such as weight and color, and **methods**, such as drive and brake.

```csharp
class Car 
{
  string color = "red";
  int maxSpeed = 200;

  static void Main(string[] args)
  {
    Car myObj = new Car();
    Console.WriteLine(myObj.color);
    Console.WriteLine(myObj.maxSpeed);
  }
}
```


**prog2.cs
```csharp
class Car 
{
  public string model;
  public string color;
  public int year;
  public void fullThrottle()
  {
    Console.WriteLine("The car is going as fast as it can!"); 
  }
}
```

**prog.cs
```csharp
class Program
{
  static void Main(string[] args)
  {
    Car Ford = new Car();
    Ford.model = "Mustang";
    Ford.color = "red";
    Ford.year = 1969;

    Car Opel = new Car();
    Opel.model = "Astra";
    Opel.color = "white";
    Opel.year = 2005;

    Console.WriteLine(Ford.model);
    Console.WriteLine(Opel.model);
  }
}
```

## Wrappers

The main idea of a **wrapper** class is to mimic the functionality of another class while hiding the mimicked class’s complexity. **A wrapper is a class that takes an instance of another class (the class being wrapped) as an argument in its constructor, which makes it a primitive class of the one being wrapped**. This means the wrapper has access to the wrapped class’ functionality and is able to expose the desired features or build utility components on top of this wrapped class. In this post, we’ll be using C# for demonstration, but this pattern is viable in all object-oriented languages.


## Constructors

- In C#, constructors are defined as methods with the same name as the class.
- C# constructors do not have a return type and are identified by the absence of a return type declaration.
- C# allows for multiple constructors in a class, and they can have different parameter lists, enabling constructor overloading.
- Constructors in C# can have access modifiers like `public`, `private`, etc., to control their visibility.
```csharp
public class MyClass
{
    private int myNumber;
    private string myString;

    // Parameterless constructor
    public MyClass()
    {
        myNumber = 0;
        myString = "Default";
    }

    // Constructor with parameters
    public MyClass(int number, string text)
    {
        myNumber = number;
        myString = text;
    }

    // Other methods and members of the class...
}
```

In the example above, `MyClass` is a class with two constructors. The first constructor is parameterless, and it initializes the `myNumber` field to 0 and the `myString` field to "Default". The second constructor takes two parameters and assigns them to the respective fields.

Constructors are typically used to set initial values for the fields of an object or perform any necessary setup operations. They are automatically called when an object is created, and you can have multiple constructors in a class with different parameter configurations to provide flexibility when creating instances of the class.

```csharp
MyClass obj1 = new MyClass(); // Calls the parameterless constructor
MyClass obj2 = new MyClass(10, "Hello"); // Calls the constructor with parameters
```
In the above code, `obj1` is created using the parameterless constructor, and `obj2` is created using the constructor with parameters.

### Properties

The meaning of **Encapsulation**, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:

- declare fields/variables as `private`
- provide `public` `get` and `set` methods, through **properties**, to access and update the value of a `private` field

```csharp
class Person
{
  private string name; // field

  public string Name   // property
  {
    get { return name; }   // get method
    set { name = value; }  // set method
  }
}
```

The `Name` property is associated with the `name` field. It is a good practice to use the same name for both the property and the private field, but with an uppercase first letter.

The `get` method returns the value of the variable `name`.

The `set` method assigns a `value` to the `name` variable. The `value` keyword represents the value we assign to the property.

### Inheritance

In C#, it is possible to inherit fields and methods from one class to another. We group the "inheritance concept" into two categories:

- **Derived Class** (child) - the class that inherits from another class
- **Base Class** (parent) - the class being inherited from

To inherit from a class, use the `:` symbol.

In the example below, the `Car` class (child) inherits the fields and methods from the `Vehicle` class (parent):

```csharp
class Vehicle  // base class (parent) 
{
  public string brand = "Ford";  // Vehicle field
  public void honk()             // Vehicle method 
  {                    
    Console.WriteLine("Tuut, tuut!");
  }
}

class Car : Vehicle  // derived class (child)
{
  public string modelName = "Mustang";  // Car field
}

class Program
{
  static void Main(string[] args)
  {
    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (From the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand field (from the Vehicle class) and the value of the modelName from the Car class
    Console.WriteLine(myCar.brand + " " + myCar.modelName);
  }
}
```

### Polymorphism

Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.

Like we specified in the previous chapter; [**Inheritance**](https://www.w3schools.com/cs/cs_inheritance.php) lets us inherit fields and methods from another class. **Polymorphism** uses those methods to perform different tasks. This allows us to perform a single action in different ways.

For example, think of a base class called `Animal` that has a method called `animalSound()`. Derived classes of Animals could be Pigs, Cats, Dogs, Birds - And they also have their own implementation of an animal sound (the pig oinks, and the cat meows, etc.):

```csharp
class Animal  // Base class (parent) 
{
  public virtual void animalSound() 
  {
    Console.WriteLine("The animal makes a sound");
  }
}

class Pig : Animal  // Derived class (child) 
{
  public override void animalSound() 
  {
    Console.WriteLine("The pig says: wee wee");
  }
}

class Dog : Animal  // Derived class (child) 
{
  public override void animalSound() 
  {
    Console.WriteLine("The dog says: bow wow");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object
    Animal myDog = new Dog();  // Create a Dog object

    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}
```

***IMPORTANT!!!***
If we do not use the virtual and override keyword when we print at the end the result will be the parent class WriteLine, because base class overrides the derived class method when they share the 
**same name**

### Abstraction


Data **abstraction** is the process of hiding certain details and showing only essential information to the user.  
Abstraction can be achieved with either **abstract classes** or [**interfaces**](https://www.w3schools.com/cs/cs_interface.php) (which you will learn more about in the next chapter).

The `abstract` keyword is used for classes and methods:

- **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).
  
- **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the derived class (inherited from).

An abstract class can have both abstract and regular methods:

```csharp
// Abstract class
abstract class Animal
{
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep()
  {
    Console.WriteLine("Zzz");
  }
}

// Derived class (inherit from Animal)
class Pig : Animal
{
  public override void animalSound()
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program
{
  static void Main(string[] args)
  {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();  // Call the abstract method
    myPig.sleep();  // Call the regular method
  }
}
```

### Interfaces

Another way to achieve [abstraction](https://www.w3schools.com/cs/cs_abstract.php) in C#, is with interfaces.

In .NET, an interface is a language construct that defines a contract or set of operations that a class must implement. It specifies the members (methods, properties, events) that a class must have, but it does not provide any implementation details. Interfaces act as a blueprint for classes, defining the structure and behavior they should adhere to.

An `interface` is a completely "**abstract class**", which can only contain abstract methods and properties (with empty bodies):
```csharp
// Interface
interface IAnimal 
{
  void animalSound(); // interface method (does not have a body)
}

// Pig "implements" the IAnimal interface
class Pig : IAnimal 
{
  public void animalSound() 
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
  }
}
```

## Data Structures

https://dev.to/adavidoaiei/fundamental-data-structures-and-algorithms-in-c-4ocf

https://learn.microsoft.com/en-us/dotnet/standard/collections/#common-collection-features

https://vinceumo.github.io/devNotes/Dotnet/c-101-cheat-sheet/

### Arrays

An array can store multiple variables of the same type. An array has a fixed size.
```csharp
// Declare a single-dimensional array of length 5 of type int
int[] array1 = new int[5];

// Declare and set array element values
int[] array2 = new int[] { 1, 3, 5, 7, 9 };
```

### Lists

A list represents a strongly typed list of objects that can be accessed by index. It is less performant than an array. It doesn’t have a fixed size.

```csharp
List<string> foods = new List<string>();
```

**foreach can be used in lists also**


![[Pasted image 20230620120835.png]]



## Delegates

A delegate represents some code that will be provided _by someone else, at some future point in time_.

Pretend you work in a warehouse.

Your boss has told you to go to each shelf in the warehouse. Once you arrive at the shelf, call him on the radio, and tell him what's on the shelf. He will then provide instructions on what to do. After completing those instructions, you will move to the next shelf, call him on the radio, etc. Continue until you have visited each shelf.

In C# terms, what you just did is this:

```
public delegate void ShelfAction(Shelf shelf);

public void VisitShelves(List<Shelf> shelves, ShelfAction shelfAction)
{
    foreach(Shelf shelf in shelves)
    {
        shelfAction(shelf);
    }
}
```

`ShelfAction` is a block of code that _will be provided to you by someone else_. You provide it with a parameter - in this case, a `Shelf`, and it performs its logic. It then returns control back to you, to resume processing the next shelf. Note, that a delegate looks _very much_ like a regular method, with two differences - it does not have a method body (just a semicolon at the end!), and it has the `delegate` keyword.

It doesn't **matter** what the code "inside" of the `ShelfAction` is. All you need to know is that it accepts one parameter - a `Shelf`, and it does not have a return value (i.e., `void`).

**THAT** is all a delegate is.

---

When do you use delegates? Let's answer this from two perspectives.

First is "When do I accept a delegate as a parameter?" (i.e., like we did up there 👆). Well - simple. Any time you have a process, that you want to provide an abstraction for, and allow someone to "fill in the blank" on what to do during that process. .... .... Yeah.... not so simple.

Suppose you had two methods:

```
public int AddAges(Person a, Person b)
{
    return a.Age + b.Age;
}
public int SubtractAges(Person a, Person b)
{
    return a.Age - b.Age;
}
```

Those two methods are _really_ similar. Wouldn't it be nice if we could just have **one** method? Maybe something like this?

```
public int CalculateAges(Person a, Person b, CalculationMethod calculation)
{
    // TODO
}
```

That is what delegates do.

```
public delegate int CalculationMethod(int a, int b);
public int CalculateAges(Person a, Person b, CalculationMethod calculation)
{
    return calculation(a.Age, b.Age);
}
```

The next perspective of "When do you use delegates" is "When do you provide an **implementation** for a delegate". The answer to that is much simpler. Any time someone _asks_ for a delegate.

- Your first exposure to delegates is probably the LINQ extension methods, like `Where`, `Select`, `Count`, etc.
    
- You may see "lambda expression" syntax ([docs](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions))
    
- You may see "method group conversion" syntax ([docs](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/conversions#108-method-group-conversions))
    

For simplicity, I'll continue the above example, using both of those syntaxes.

Suppose we have this:

public delegate int CalculationMethod(int a, int b);
public int CalculateAges(Person a, Person b, CalculationMethod calculation)
{
    return calculation(a.Age, b.Age);
}

You can now add the following methods:

public int AddAges(Person a, Person b)
{
    // This uses "method group conversion" to create an instance of the delegate
    return CalculateAges(a, b, AddNumbers);
}
private int AddNumbers(int a, int b)
{
    return a + b;
}

public int SubtractAges(Person a, Person b)
{
    // This uses a "lambda expression" to create an instance of the delegate
    return CalculateAges(a, b, (ageA, ageB) => ageA - ageB);
}

---

Now, I would be **completely** remiss if I didn't mention, that _you (usually) don't need to create your own delegates_

In the above example, I created a delegate:

public delegate int CalculationMethod(int a, int b);

And used it like so:

public int CalculateAges(Person a, Person b, CalculationMethod calculation)
{
    return calculation(a.Age, b.Age);
}

Well, Microsoft has already made some generic delegates for me.

- There is one non-generic `Action` delegate, which does not take a parameter, and does not return a value ([docs](https://learn.microsoft.com/en-us/dotnet/api/system.action))
    
- There are sixteen generic `Action` delegates, which take anywhere from 1 to 16 parameters, and does not return a value ([docs for one of them](https://learn.microsoft.com/en-us/dotnet/api/system.action-1))
    
- There are seventeen generic `Func` delegates, which take anywhere from 0 to 16 parameters, and returns a single value ([docs for one of them](https://learn.microsoft.com/en-us/dotnet/api/system.func-3))
    

So, we can rewrite that example using those built-in delegates:

public int CalculateAges(Person a, Person b, Func<int, int, int> calculation)
{
    return calculation(a.Age, b.Age);
}

In C#, actions, functions, and events are fundamental concepts that play important roles in programming. Let's take a closer look at each of them:

1. **Actions:**
    
    - An `Action` in C# is a delegate type that represents a method that does not return a value.
    - It is essentially a pointer to a method with a specific signature, where the method can take parameters but does not return anything.
    - Actions are commonly used for scenarios where you want to pass a behavior as a parameter to a method or store it in a variable.
    
    Example:
    
    csharpCopy code
    
    `Action<int, int> add = (a, b) => Console.WriteLine(a + b); add(5, 3); // Outputs: 8`
    
2. **Functions:**
    
    - A `Func` is another delegate type in C# that represents a method with a specific return type.
    - Like `Action`, `Func` can also take parameters, but it differs in that it specifies a return type.
    - The last type parameter of `Func` is always the return type.
    
    Example:
    
    csharpCopy code
    
    `Func<int, int, int> add = (a, b) => a + b; int result = add(5, 3); // result is 8`
    
3. **Events:**
    
    - An event in C# is a mechanism for communication between objects. It allows one object (the publisher) to notify other objects (subscribers) when something of interest happens.
    - Events are declared using the `event` keyword and are based on delegates, typically of type `EventHandler` or a custom delegate type.
    - Events follow the publisher-subscriber pattern and are commonly used in GUI programming and other scenarios where objects need to be notified about changes or actions.
    
    Example:
    
    csharpCopy code
    
    `public class EventExample {     public event EventHandler SomethingHappened;      public void DoSomething()     {         // Do something important          // Notify subscribers that something happened         OnSomethingHappened();     }      protected virtual void OnSomethingHappened()     {         SomethingHappened?.Invoke(this, EventArgs.Empty);     } }  // Usage var example = new EventExample(); example.SomethingHappened += (sender, args) => Console.WriteLine("Something happened!"); example.DoSomething(); // Triggers the event`
    

Understanding these concepts is crucial for effective C# programming, as they provide flexibility and enable the creation of modular and extensible code. Actions and functions are useful for passing behavior around, while events facilitate communication between different parts of a program.

## LINQ
Certainly! LINQ (Language Integrated Query) is a set of extensions to the .NET framework that adds query capabilities to C# and VB.NET. LINQ provides a set of standard query operators that operate on sequences, such as arrays, collections, and databases. Here are some of the most commonly used LINQ extension methods:

1. **Filtering:**
   - `Where`: Filters a sequence based on a predicate.
   ```csharp
   var result = collection.Where(item => item.Property > 10);
   ```

2. **Projection:**
   - `Select`: Projects each element of a sequence into a new form.
   ```csharp
   var result = collection.Select(item => item.Property);
   ```

3. **Sorting:**
   - `OrderBy`: Sorts the elements of a sequence in ascending order.
   ```csharp
   var result = collection.OrderBy(item => item.Property);
   ```

   - `OrderByDescending`: Sorts the elements of a sequence in descending order.
   ```csharp
   var result = collection.OrderByDescending(item => item.Property);
   ```

4. **Aggregation:**
   - `Count`: Returns the number of elements in a sequence.
   ```csharp
   var count = collection.Count();
   ```

   - `Sum`: Computes the sum of a sequence of numeric values.
   ```csharp
   var sum = collection.Sum(item => item.Property);
   ```

   - `Average`: Computes the average of a sequence of numeric values.
   ```csharp
   var average = collection.Average(item => item.Property);
   ```

   - `Min`: Returns the minimum value in a sequence.
   ```csharp
   var min = collection.Min(item => item.Property);
   ```

   - `Max`: Returns the maximum value in a sequence.
   ```csharp
   var max = collection.Max(item => item.Property);
   ```

5. **Quantifiers:**
   - `Any`: Determines whether any elements of a sequence satisfy a condition.
   ```csharp
   var any = collection.Any(item => item.Property > 10);
   ```

   - `All`: Determines whether all elements of a sequence satisfy a condition.
   ```csharp
   var all = collection.All(item => item.Property > 10);
   ```

6. **Element Operations:**
   - `First`: Returns the first element of a sequence.
   ```csharp
   var first = collection.First();
   ```

   - `FirstOrDefault`: Returns the first element of a sequence, or a default value if no element is found.
   ```csharp
   var firstOrDefault = collection.FirstOrDefault();
   ```

   - `Single`: Returns the only element of a sequence, or throws an exception if there is not exactly one element.
   ```csharp
   var single = collection.Single();
   ```

   - `SingleOrDefault`: Returns the only element of a sequence, or a default value if no element is found, or throws an exception if there is more than one element.
   ```csharp
   var singleOrDefault = collection.SingleOrDefault();
   ```

   - `ElementAt`: Returns the element at a specified index in a sequence.
   ```csharp
   var element = collection.ElementAt(2);
   ```

7. **Join Operations:**
   - `Join`: Performs an inner join between two sequences based on a key.
   ```csharp
   var result = collection1.Join(collection2, item1 => item1.Key, item2 => item2.Key, (item1, item2) => new { item1, item2 });
   ```

   - `GroupJoin`: Performs a group join between two sequences based on a key.
   ```csharp
   var result = collection1.GroupJoin(collection2, item1 => item1.Key, item2 => item2.Key, (item1, items2) => new { item1, items2 });
   ```

These are just some of the LINQ extension methods. There are additional methods and variations available for more specialized scenarios.

## PLINQ
Certainly! PLINQ provides a set of extension methods to enable parallel execution of LINQ queries. These extension methods are part of the `System.Linq` namespace. Here are some key extension methods for PLINQ:

1. **AsParallel():**
   - Converts a sequential LINQ query to a parallel query.

   ```csharp
   var parallelQuery = sourceCollection.AsParallel();
   ```

2. **WithExecutionMode():**
   - Specifies the execution mode for a PLINQ query (Parallel, Sequential, ForceParallel, ForceSequential).

   ```csharp
   var parallelQuery = sourceCollection.AsParallel().WithExecutionMode(ParallelExecutionMode.ForceParallel);
   ```

3. **WithDegreeOfParallelism():**
   - Specifies the maximum number of concurrently executing tasks for a PLINQ query.

   ```csharp
   var parallelQuery = sourceCollection.AsParallel().WithDegreeOfParallelism(4);
   ```

4. **WithMergeOptions():**
   - Specifies how the results of subtasks are merged in a PLINQ query.

   ```csharp
   var parallelQuery = sourceCollection.AsParallel().WithMergeOptions(ParallelMergeOptions.NotBuffered);
   ```

5. **Where():**
   - Filters elements in a parallel query based on a specified condition.

   ```csharp
   var parallelQuery = sourceCollection.AsParallel().Where(item => item > 50);
   ```

6. **Select():**
   - Projects each element of a parallel query into a new form.

   ```csharp
   var parallelQuery = sourceCollection.AsParallel().Select(item => item * 2);
   ```

7. **ForAll():**
   - Performs an action on each element of a parallel query.

   ```csharp
   sourceCollection.AsParallel().ForAll(item => Console.WriteLine(item));
   ```

These are just a few examples of the extension methods available for PLINQ. Depending on your specific use case, you might also explore additional methods and options provided by PLINQ for better control over parallel query execution.